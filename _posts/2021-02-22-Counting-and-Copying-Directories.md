---
layout: post
title: "Counting and Copying Directories"
date: 2021-02-22 08:00:00 -0600
categories: [Software]
tags: [Microsoft, Performance, Powershell, Robocopy]
---

*Robocopy is still amazing.*

Robocopy is one of the best performing ways to copy, sync, and delete directories in Windows, but it can also be used to count directories. It takes a bit of wrangling to use in Powershell, but the end result is quite amazing.

I found [this function](https://sketchingdev.co.uk/blog/powershell-extract-the-summary-table-from-robocopys-log-file.html) to help parse the output summary of a robocopy job. Kudos to the [SketchingDev](https://twitter.com/sketchingdev).

Example robocopy output:

```
               Total    Copied   Skipped  Mismatch    FAILED    Extras
    Dirs :         3         0         3         0         0         0
   Files :         4         0         4         0         0         0
   Bytes :  19799875         0  19799875         0         0         0
   Times :   0:00:00   0:00:00                       0:00:00   0:00:00
```

I want to parse the total bytes and the SketchingDev's function helped me do just that. The output Powershell object was a little tricky for me to work out because my Powershell skills aren't the greatest, but a bit of trial an error and I was able to extract just the total bytes. And then run it through another function to make it human readable.

*(You could just leave it as human-readable from Robocopy. But I think extracting the total bytes instead is useful for other applications.)*

{% highlight posh %}
function Select-RoboSummary {
    [CmdletBinding()]
    param (
        [parameter(Mandatory=$true,ValueFromPipeline=$true)]
        [string]$log,
        [parameter(Mandatory=$false,ValueFromPipeline=$false)]
        [switch]$separateUnits
    )
    PROCESS
    {
        $cellHeaders = @("Total", "Copied", "Skipped", "Mismatch", "Failed", "Extras")
        $rowTypes    = @("Dirs", "Files", "Bytes")

        # Extract rows
        $rows = $log | Select-String -Pattern "(Dirs|Files|Bytes)\s*:(\s*([0-9]+(\.[0-9]+)?( [a-zA-Z]+)?)+)+" -AllMatches
        if ($rows.Count -eq 0) { throw "Summary table not found" }
        if ($rows.Matches.Count -ne $rowTypes.Count) { throw "Unexpected number of rows/ Expected {0}, found {1}" -f $rowTypes.Count, $rowsMatch.Count }

        # Merge each row with its corresponding row type, with property names of the cell headers
        for($x = 0; $x -lt $rows.Matches.Count; $x++)
        {
            $rowType  = $rowTypes[$x]
            $rowCells = $rows.Matches[$x].Groups[2].Captures | foreach{ $_.ToString().Trim() }
            if ($cellHeaders.Length -ne $rowCells.Count) { throw "Unexpected amount of cells in a row. Expected {0} cells (the amount of headers) but found {1}" -f $cellHeaders.Length,$rowCells.Count }
            $row = New-Object -TypeName PSObject
            $row | Add-Member -Type NoteProperty Type($rowType)

            for($i = 0; $i -lt $rowCells.Count; $i++)
            {
                $header = $cellHeaders[$i]
                $cell   = $rowCells[$i]
                if ($separateUnits -and ($cell -match " ")) { $cell = $cell -split " " }
                $row | Add-Member -Type NoteProperty -Name $header -Value $cell
            }
            $row
        }
    }
}

function Get-NiceFilesize {
    param (
        [parameter(Mandatory=$true)]
        [uint64]$ByteCount
    )

    switch ($bytecount) {
        { $_ -ge 1TB } { "{0:N2} TB" -f ($bytecount / 1TB); break }
        { $_ -ge 1GB } { "{0:N2} GB" -f ($bytecount / 1GB); break }
        { $_ -ge 1MB } { "{0:N2} MB" -f ($bytecount / 1MB); break }
        { $_ -ge 1KB } { "{0:N2} KB" -f ($bytecount / 1KB); break }
        default { "$bytecount Bytes" }
    }
}

# Use Robocopy to calculate the directory size

[string]$output = robocopy dir c:\dummy /L /BYTES /XJ /E /NFL /NDL /NJH /R:0 /MT:64

# Extract just the byte count from the robocopy summary

[uint64]$bytecount = [$output | Select-RoboSummary](2).Total

# Make the Byte count human readable

Get-NiceFilesize $bytecount
{% endhighlight %}

Use the following robocopy command as a template:

```
robocopy [dir] c:\dummy /L /BYTES /XJ /E /NFL /NDL /NJH /R:0 /MT:64

    [dir] - the directory you want to count.
    c:\dummy - a place holder for a non-existent destination directory.
    /L - Don't copy anything. Just List what it would do.
    /BYTES - change the output to bytes instead of human-readable form.
    /XJ - don't follow ntfs junctions.
    /NFL - no file list.
    /NDL - no directory list.
    /NJH - no job header.
    /R:0 - no retries.
    /MT:64 - use 64 threads for performance.
```

The default of /MT (8 threads) would probably have been enough. Also, this might not help with hdds.

This method seems to be faster than `Get-ChildItem` in my informal benchmarks and this method can handle filepaths longer than 260 characters.

*(I already ran across a situation where I needed to upgrade from `[int64]` to `[uint64]` because of an 8TB hard drive.)*

---
layout: post
title: "Powershell, Inline Images, and Outlook"
date: 2020-08-05 08:00:00 -0600
categories: [Powershell]
tags: [email, Outlook, scripting]
---

*For an inline image in an email, use a lowercase "cid:" when specifying the content-id.*

I had a heck of a time trying to get an inline image to show in Outlook when sending an email with Powershell. It should show in other email clients like the iPhone Mail app, but not in Outlook 2016.

I found that using:

```posh
<img src='cid:$($Attachment.ContentId)' />
```

instead of

```posh
<img src='CID:$($Attachment.ContentId)' />
```

fixed the issue.

See the difference? Yeah. Ouch.

```posh
    "CID:" = no work
    "cid:" = works
```

Here is a sanitized version of the script:

```posh
$Attachment = New-Object Net.Mail.Attachment("path\to\image.png") #Change path to image as appropriate
    #next 3 lines particular to including attachment inline...as opposed to as attachment
    $Attachment.ContentDisposition.Inline = $True
    $Attachment.ContentDisposition.DispositionType = "Inline"
    $Attachment.ContentType.MediaType = "image/png"

    $MailMessage = New-Object Net.Mail.MailMessage #Required
    $MailMessage.To.Add("RECIPIENT-EMAIL") #Required
    $MailMessage.From = "SENDER-EMAIL" #Required
    $MailMessage.Subject = "SUBJECT"
    $MailMessage.IsBodyHtml = $True
    $MailMessage.Attachments.Add($Attachment) #Required in order to include image inline
    $MailMessage.Body = "
        <html>
            <body>
                <img src='cid:$($Attachment.ContentId)' />
                <p>BODY OF EMAIL</p>
            </body>
        </html>" #Required

    $SmtpClient = New-Object Net.Mail.SmtpClient("SMTP-SERVER")
    $SmtpClient.Send($MailMessage)
```

I also tried [this StackOverflow answer](https://stackoverflow.com/questions/52837468/embed-images-in-email-and-send-via-powershell) and not using `Net.Mail.Attachment` but it gave me the same error in Outlook. Again, it was because of a capitalized "CID:", using a lowercase "cid:" fixed the issue.

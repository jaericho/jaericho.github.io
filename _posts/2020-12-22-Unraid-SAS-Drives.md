---
layout: post
title: "Unraid and Used SAS Drives"
date: 2020-12-22 08:00:00 -0600
categories: [Software]
tags: [HDD, Linux, LSI SAS2008, SAS, Unraid]
---

I was gifted with many 4TB SAS 7.2k drives, now it's time to put them to work.

I had an interesting issue the other day when building my new Unraid NAS. (Using [this great guide](https://forums.serverbuilds.net/t/guide-nas-killer-4-0-fast-quiet-power-efficient-and-flexible-starting-at-125/667) from [ServerBuilds.net](https://serverbuilds.net))

I'm using a [Rosewill 4412](https://www.rosewill.com/product/rosewill-rsv-l4412-4u-rackmount-server-case-or-chassis-12-sata-sas-hot-swap-drives-5-cooling-fans-included/) with 12 hotswap sata/sas drive bays and two LSI SAS2008 HBA cards flashed with the 20.0.0.7 firmware and in IT mode.

When I plugged the drives in they were recognized by Unraid, but I was getting errors in the logs, and when I tried to attach the drives to the array Unraid would disappear the drive from the list of available drives.

Here were the errors:

```
Dec 20 18:52:01 Tower kernel: print_req_error: protection error, dev sdg, sector 7814036992
Dec 20 18:52:01 Tower kernel: Buffer I/O error on dev sdg, logical block 976754624, async page read
Dec 20 18:52:01 Tower kernel: mpt2sas_cm0: log_info(0x3112043b): originator(PL), code(0x12), sub_code(0x043b)
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 UNKNOWN(0x2003) Result: hostbyte=0x05 driverbyte=0x08
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 Sense Key : 0x5 [current]
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 ASC=0x10 ASCQ=0x3
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 CDB: opcode=0x7f, sa=0x9
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 CDB[00]: 7f 00 00 00 00 00 00 18 00 09 20 00 00 00 00 01
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 CDB[10]: d1 c0 be 00 d1 c0 be 00 00 00 00 00 00 00 00 08
Dec 20 18:52:01 Tower kernel: print_req_error: protection error, dev sdh, sector 7814036992
Dec 20 18:52:01 Tower kernel: mpt2sas_cm0: log_info(0x3112043b): originator(PL), code(0x12), sub_code(0x043b)
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 UNKNOWN(0x2003) Result: hostbyte=0x05 driverbyte=0x08
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 Sense Key : 0x5 [current]
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 ASC=0x10 ASCQ=0x3
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 CDB: opcode=0x7f, sa=0x9
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 CDB[00]: 7f 00 00 00 00 00 00 18 00 09 20 00 00 00 00 01
Dec 20 18:52:01 Tower kernel: sd 7:0:6:0: [sdh] tag#323 CDB[10]: d1 c0 be 00 d1 c0 be 00 00 00 00 00 00 00 00 08
Dec 20 18:52:01 Tower kernel: print_req_error: protection error, dev sdh, sector 7814036992
Dec 20 18:52:01 Tower kernel: Buffer I/O error on dev sdh, logical block 976754624, async page read
Dec 20 18:52:01 Tower kernel: mpt2sas_cm0: log_info(0x3112043b): originator(PL), code(0x12), sub_code(0x043b)
```

To fix this issue, I ended up using Windows to clean the drive of any partitions, create a GPT partition, and format the drive with NTFS. I knew that Unraid would be able to handle importing those partitions, and it would reformat the drives with a new partition scheme and XFS anyways.

```
diskpart
select disk 2
clean
```

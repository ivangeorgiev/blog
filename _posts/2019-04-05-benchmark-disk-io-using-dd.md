---
title: "Benchmark Disk IO Speed Using dd"
date: 2019-04-05
links:
  - title: "Disk Speed Test (Read/Write): HDD, SSD Performance in Linux"
    url: "https://www.shellhacks.com/disk-speed-test-read-write-hdd-ssd-perfomance-linux/"
---



## Measure Disk Write Performance With dd 

Following command writes 1024 blocks of 1 MB size to a file named `tempfile`. The resulting file contains 1 GB of zeroes. After the command finishes, summary statistics are printed. 

```bash
$ sync; dd if=/dev/zero of=tempfile bs=1M count=1024; sync
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 0.750093 s, 1.4 GB/s
```

The `sync` command forces immediate write of all cached data to disk.

## Measure Disk Read Performance With dd

Using the file created from the previous benchmark the following command reads the file and displays statistics.

```bash
$ dd if=tempfile of=/dev/null bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 0.195372 s, 5.5 GB/s
```

## Hints

1. Make sure no other processes are accessing the file. For example if you create the file into a webserver's home folder, the webserver might start processing it which will impact the benchmark.
2. Use as big file as you can for more realistic results.
#Nmap

https://nmap.org/


## **Common Usage:**
`nmap -sC -sV -oA nmap/common 192.x.x.x`

**-sC**
Performs a script scan using the default set of scripts. It is equivalent to --script=default. Some of the scripts in this category are considered intrusive and should not be run against a target network without permission.

**-sV**    
(Version detection) Enables version detection, as discussed above. Alternatively, you can use -A, which enables version detection among other things.

**-oA**    
basename (Output to all formats) As a convenience, you may specify -oA basename to store scan results in normal, XML, and grepable formats at once. They are stored in basename.nmap, basename.xml, and basename.gnmap, respectively. As with most programs, you can prefix the filenames with a directory path, such as ~/nmaplogs/foocorp/ on Unix or c:\hacking\sco on Windows.



## **Aggressive All Ports Scan:**
`nmap -p- -T5 --max-retries 0 -v -oA nmap/common 192.x.x.x`

**-p-**
This option specifies which ports you want to scan and overrides the default. Individual port numbers are OK, as are ranges separated by a hyphen (e.g.  1-1023). The beginning and/or end values of a range may be omitted, causing Nmap to use 1 and 65535, respectively. So
you can specify -p- to scan ports from 1 through 65535. Scanning port zero is allowed if you specify it explicitly. For IP protocol scanning (-sO), this option specifies the protocol numbers you wish to scan for (0–255).


**-T** 
paranoid|sneaky|polite|normal|aggressive|insane (Set a timing template)While the fine-grained timing controls discussed in the previous section are powerful and effective, some people find them confusing. Moreover, choosing the appropriate values can sometimes take more time than the scan you are trying to optimize. Fortunately, Nmap offers a simpler approach, with six timing templates. You can specify them with the -T option and their number (0–5) or their name. The template names are **paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and insane (5)**. The first two are for IDS evasion. Polite mode slows down the scan to use less bandwidth and target machine resources. Normal mode is the default and so -T3 does nothing. Aggressive mode speeds scans up by making the assumption that you are on a reasonably fast and reliable network. Finally insane mode assumes that you are on an extraordinarily fast network or are willing to sacrifice some accuracy for speed.


**--max-retries** 
numtries (Specify the maximum number of port scan probe retransmissions)
When Nmap receives no response to a port scan probe, it could mean the port is filtered. Or maybe the probe or response was simply lost on the network. It is also possible that the target host has rate limiting enabled that temporarily blocked the response. So Nmap tries again by retransmitting the initial probe. If Nmap detects poor network reliability, it may try many more times before giving up on a port. While this benefits accuracy, it also lengthens scan times. When performance is critical, scans may be sped up by limiting the number of retransmissions allowed. You can even specify --max-retries 0 to prevent any retransmissions, though that is only recommended for situations such as informal surveys where occasional missed ports and hosts are acceptable.

The default (with no -T template) is to allow ten retransmissions. If a network seems reliable and the target hosts aren't rate limiting, Nmap usually only does one retransmission. So most target scans aren't even affected by dropping --max-retries to a low value such as three. Such values can substantially speed scans of slow (rate limited) hosts. You usually lose some information when Nmap gives up on ports early, though that may be preferable to letting the --host-timeout expire and losing all information about the target.



## **Nmap Scripts Scan:**
`nmap -p 11211 --script memcached-info`


<iframe width="1270" height="636" src="https://www.youtube.com/embed/M-Uq7YSfZ4I" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
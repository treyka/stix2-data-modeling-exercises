Damballa IMDDOS Botnet STIX 2.0 modeling exercise
=================================================

Tools
-----
* cti-whittler: `https://johnwunder.github.io/cti-whittler/`

Open questions
--------------
* How to represent the random 6-10 bytes of ImagePath - hex(2) at the
  end of the regkey in patterning...
  * ```reg key: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SafePrec<xxx> –
ImagePath - hex(2):43,3a,5c,57,49,4e,44,4f,57,53,5c,73,79,73,74,65,6d,33,32,5c,<xx, xx,
xx, xx, xx, xx, xx, xx, xx, xx, xx>

The <xxx> varies. In the image path, the last ten hex bytes varies depending on the random file
name of dropped file. It ranges from six bytes (files with no extension) to ten bytes (files with
extensions). The first hex bytes when converted to ASCII represents C:\WINDOWS\system32\.
Once the HEXADECIMAL bytes have been converted to reveal the name of the dropped file, it
can be found in the System32 folder of Windows```
  
* How to pattern against a list a la network-traffic protocols to say
  ((tcp OR udp) AND dns)
  * This appears to be the only means of expressing this: ```[(network-traffic:protocols[0] = 'tcp' OR network-traffic:protocols[0] = 'udp') AND network-traffic:protocols[1] = 'dns']```
    * Concise, ain't it?!




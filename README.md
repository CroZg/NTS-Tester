# NTS-Tester
Tool for quick testing of NTS (Network Time Security) servers.<br><br>
Windows(tm) 7+ x64 command-line tool for testing and diagnosing NTP servers that implement the KE (Key Establishment) protocol of the Network Time Security (NTS) authentication mechanism.

# Requirements
Any MS Windows(tm) x64 platform (7, 10, 11, 2019+)

# Usage
```
Usage: nts-tester.exe [OPTIONS] --server <SERVER>

Options:
  -s, --server <SERVER>              NTS-KE server hostname
  -p, --ke-port <KE_PORT>            NTS-KE TCP port [default: 4460]
      --ntp-port <NTP_PORT>          NTP UDP port override (default: 123 or from NTS-KE negotiation)
      --ntp-server <NTP_SERVER>      NTP server address override (default: same as NTS-KE server or from negotiation)
  -n, --count <COUNT>                Number of NTP queries to perform after NTS-KE [default: 1]
      --placeholders <PLACEHOLDERS>  Number of cookie placeholders per NTP request (0-7, default: auto)
  -t, --timeout <TIMEOUT>            Connection timeout in milliseconds [default: 5000]
      --ke-only                      NTS-KE only (skip NTP queries)
  -o, --output <OUTPUT>              Output format [default: text] [possible values: text, json]
  -v, --verbose                      Verbose output (show hex dumps, timing details)
      --dump                         Hex-dump outgoing NTP packets before sending
      --insecure                     Skip TLS certificate verification (DANGEROUS — for testing only)
      --native-certs                 Use the OS native certificate store in addition to bundled root certificates
  -h, --help                         Print help
  -V, --version                      Print version
```
# Example
```
$nts-tester.exe --server nts1.ntp.hr
=== NTS-KE Handshake ===
  Server:      nts1.ntp.hr:4460
  TLS Version: TLSv1_3
  Cipher:      TLS13_AES_256_GCM_SHA384
  ALPN:        ntske/1
  Certificate:
    Subject:   CN=nts1.ntp.hr
    Issuer:    C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication CA DV R36
    Valid:     Mar 18 00:00:00 2026 +00:00 to Oct  2 23:59:59 2026 +00:00
    SANs:      nts1.ntp.hr, www.nts1.ntp.hr
  Protocol:    NTPv4 (0x0000)
  AEAD:        AES-SIV-CMAC-256 (15)
  Cookies:     8 received (104 bytes each)
  Server Neg:  (none)
  Port Neg:    (none)
  Time:        529.5ms

  NTP Target:  nts1.ntp.hr:123 → 161.53.78.69:123

=== NTP Query 1/1 ===
  Server:      nts1.ntp.hr:123 (161.53.78.69:123)
  T1 (Origin):    2026-03-20T13:07:09.939933Z  [3983000829.4036982783]
  T2 (Receive):   2026-03-20T13:07:09.250688Z  [3983000829.1076699274]
  T3 (Transmit):  2026-03-20T13:07:09.251004Z  [3983000829.1078055289]
  T4 (Dest):      2026-03-20T13:07:10.000904Z  [3983000830.3884797]
  Offset:      -719.573ms
  Delay:       60.656ms
  Stratum:     1
  Precision:   -21 (476.8ns)
  Root Delay:  0.000ms
  Root Disp:   0.229ms
  Ref ID:      MRS
  Cookies:     1 refreshed (8 available)
  AEAD:        OK (decryption verified)
  Time:        60.6ms
```
# Author
Marko Jurcevic <ntstimetools@crobiz.com> | Vesco informatika d.o.o. | Zagreb | Croatia 

# License

End User License Agreement

Introduction

This End-User License Agreement ("EULA") is a legal agreement between you (either an individual or a single entity) and Vesco informatika d.o.o. ("Licensor") for the use of NTS Time Tools (NTS Tester in CLI and GUI version, NTS TimeSync) ("Software"). This EULA governs your use of the Software provided by the Licensor. By clicking "I Agree" or installing or using the Software, you agree to be bound by the terms of this EULA.

License Grant

Licensor grants you a revocable, non-exclusive, non-transferable, limited license to download, install, and use the Software solely for your personal, non-commercial purposes strictly in accordance with the terms of this Agreement.

Restrictions on Use

You agree not to, and you will not permit others to:

- Copy, modify, or create derivative works of the Software.
- Distribute, transfer, sublicense, lease, lend, or rent the Software to any third party.
- Reverse engineer, decompile or disassemble the Software, except to the extent expressly permitted by applicable law.
- Remove, alter, or obscure any proprietary notices on the Software.
- Use the Software in any manner that could damage, disable, overburden, or impair the Software.
- Use the Software to create or distribute any malicious software or for any unlawful purpose.

Privacy Notices

The Software does communicate only with servers that are entered by end-user (you), required to perform Software original function. The Software does not communicate with its own server, does not provide automatic updating of the Software; does not implement sending error reports, and does not send any anonymized usage data. 

Jurisdiction

This EULA and any disputes arising out of or in connection with it will be governed by and construed in accordance with the laws of Croatia (EU), without regard to its conflict of laws principles. Any legal actions or proceedings arising out of this EULA shall be brought exclusively in the courts of Zagreb, Croatia.

Intellectual Property & Copyright Infringement

The Software and all rights, title, and interest in and to the Software, including all intellectual property rights therein, are and will remain the exclusive property of the Licensor. You agree to notify the Licensor promptly if you become aware of any infringement of the Licensor’s intellectual property rights in the Software.

Open-Source Notices

Certain components of the Software may be subject to open-source software licenses ("Open-Source Components"), which means any software license approved as open-source licenses by the Open Source Initiative or any substantially similar licenses, including without limitation any license that, as a condition of distribution of the software licensed under such license, requires that the distributor make the software available in source code format. The Software documentation includes copies of the licenses applicable to the Open-Source Components.

To the extent there is conflict between the license terms covering the Open-Source Components and this EULA, the terms of such licenses will apply in lieu of the terms of this EULA. To the extent the terms of the licenses applicable to Open-Source Components prohibit any of the restrictions in this Agreement with respect to such Open-Source Component, such restrictions will not apply to such Open-Source Component. To the extent the terms of the licenses applicable to Open-Source Components require Licensor to make an offer to provide source code in connection with the Product, such offer is hereby made, and you may exercise it by contacting ntstimetools@crobiz.com.


Termination of Licensing

Licensor may terminate this EULA at any time if you fail to comply with any term(s) of this Agreement. Upon termination, you must cease all use of the Software and destroy all copies, full or partial, of the Software.

Warranty Disclaimer

THE SOFTWARE IS PROVIDED “AS IS” AND WITH ALL FAULTS. LICENSOR MAKES NO WARRANTIES, WHETHER EXPRESS, IMPLIED, OR STATUTORY, INCLUDING BUT NOT LIMITED TO THE IMPLIED WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, TITLE, AND NON-INFRINGEMENT. YOU BEAR THE ENTIRE RISK AS TO SELECTING THE SOFTWARE FOR YOUR PURPOSES AND AS TO THE QUALITY AND PERFORMANCE OF THE SOFTWARE.

Limitations of Liability

TO THE MAXIMUM EXTENT PERMITTED BY APPLICABLE LAW, IN NO EVENT SHALL LICENSOR BE LIABLE FOR ANY INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL, OR PUNITIVE DAMAGES, OR ANY LOSS OF PROFITS OR REVENUES, WHETHER INCURRED DIRECTLY OR INDIRECTLY, OR ANY LOSS OF DATA, USE, GOODWILL, OR OTHER INTANGIBLE LOSSES, RESULTING FROM (A) YOUR USE OR INABILITY TO USE THE SOFTWARE; (B) ANY UNAUTHORIZED ACCESS TO OR USE OF OUR SERVERS AND/OR ANY PERSONAL INFORMATION STORED THEREIN; (C) ANY INTERRUPTION OR CESSATION OF TRANSMISSION TO OR FROM THE SOFTWARE; (D) ANY BUGS, VIRUSES, TROJAN HORSES, OR THE LIKE THAT MAY BE TRANSMITTED TO OR THROUGH OUR SOFTWARE BY ANY THIRD PARTY; (E) ANY ERRORS OR OMISSIONS IN ANY CONTENT OR FOR ANY LOSS OR DAMAGE INCURRED AS A RESULT OF YOUR USE OF ANY CONTENT POSTED, EMAILED, TRANSMITTED, OR OTHERWISE MADE AVAILABLE THROUGH THE SOFTWARE; AND/OR (F) THE DEFAMATORY, OFFENSIVE, OR ILLEGAL CONDUCT OF ANY THIRD PARTY.

Limits on Damage Liability

Licensor’s total liability to you for any damages (regardless of the form of action) shall not exceed the amount actually paid by you for the Software.

Control of Software Distribution

You may not distribute or make the Software available over a network where it could be used by multiple devices at the same time. You may not rent, lease, lend, sell, redistribute, or sublicense the Software.

Business Contact Information

If you have any questions about this EULA, please contact us at:

Vesco informatika d.o.o.
Prilaz Ivana Visina 3
ntstimetools@crobiz.com


Updates & Changes

Licensor reserves the right, at its sole discretion, to modify or replace this EULA at any time. If a revision is material, we will provide at least 30 days’ notice prior to any new terms taking effect. By continuing to access or use our Software after those revisions become effective, you agree to be bound by the revised terms.

By clicking "I Agree" or installing or using the Software, you acknowledge that you have read this Agreement, understand it, and agree to be bound by its terms and conditions.

NTS Time Tools - Vesco informatika d.o.o.

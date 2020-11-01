---
description: >-
  John (aka John the Ripper) is a fast password cracker, currently available for
  many flavors of Unix, macOS, Windows, DOS, BeOS, and OpenVMS
---

# John

**Link**: [https://github.com/magnumripper/JohnTheRipper](https://github.com/magnumripper/JohnTheRipper)

## **Simple usage**

**JTR password cracking** 

`john --wordlist=/usr/share/wordlists/rockyou.txt hashes` 

**JTR forced descrypt cracking with wordlist** 

`john --format=descrypt --wordlist /usr/share/wordlists/rockyou.txt hash.txt` 

**JTR forced descrypt brute force cracking** 

`john --format=descrypt hash --show` 

**Display formats:** 

`john --list=formats` 

## **Type and mask:** 

`iron@kali2:/tmp$ sudo john lm.txt --mask=?l?l?l?l --format=lm` 

### **mask** 

Create a mask: 

example: 

```text
root@attackdefense:~# john pdfhash --mask=?d?d?d?d?d?d?d?d?l 
?d = digit 
?l = lower-case ASCII letters 
?u = upper-case ASCII letters 
```

**example with numbers in the middle:** 

```text
root@attackdefense:~# john pdfhash --mask=?d?d?d?d19?d?d?u 
Using default input encoding: UTF-8 
Loaded 1 password hash (PDF [MD5 SHA2 RC4/AES 32/64]) 
Press 'q' or Ctrl-C to abort, almost any other key for status 
01021980D        (/root/encrypted.pdf) 
1g 0:00:00:05 DONE (2019-10-31 10:10) 0.1721g/s 530466p/s 530466c/s 530466C/s 01021980D 
Use the "--show" option to display all of the cracked passwords reliably 
Session completed 
```

A mask may consist of: 

```text
- Static letters. 
- Ranges in [aouei] or [a-z] syntax. Or both, [0-9abcdef] is the same as 
     [0-9a-f]. 
- Placeholders that are just a short form for ranges, like ?l which is 
     100% equivalent to [a-z]. 
- ?l lower-case ASCII letters 
- ?u upper-case ASCII letters 
- ?d digits 
- ?s specials (all printable ASCII characters not in ?l, ?u or ?d) 
- ?a full 'printable' ASCII. Note that for formats that don't recognize case 
     (eg. LM), this only includes lower-case characters which is a tremendous 
     reduction of keyspace for the win. 
- ?B all 8-bit (0x80-0xff) 
- ?b all (0x01-0xff) (the NULL character is currently not supported by core). 
- ?h lower-case HEX digits (0-9, a-f) 
- ?H upper-case HEX digits (0-9, A-F) 
- ?L lower-case non-ASCII letters 
- ?U upper-case non-ASCII letters 
- ?D non-ASCII "digits" 
- ?S non-ASCII "specials" 
- ?A all valid characters in the current code page (including ASCII). Note 
     that for formats that don't recognize case (eg. LM), this only includes 
     lower-case characters which is a tremendous reduction of keyspace. 
- Placeholders that are custom defined, so we can e.g. define ?1 to mean [?u?l] 
  ?1 .. ?9 user-defined place-holder 1 .. 9 
 Placeholders for Hybrid Mask mode: 
  ?w is a placeholder for the original word produced by the parent mode in 
     Hybrid Mask mode. 
  ?W is just like ?w except the original word is case toggled (so PassWord 
     becomes pASSwORD). 
```

## Windows 

`C:\Users\David\Documents\Tools\john-1.9.0-jumbo-1-win64\run>john.exe ..\test.txt --format=raw-MD5` 

## Formats

### Common formats: 

| Type  | John Format  | Hash Example  |
| :--- | :--- | :--- |
| MD5  | raw-md5  | fc16ea469c37da07bac3ddbbdbfb3945  |
| LM  | lm  | 299BD128C1101FD6  |
| NTLM  | nt  | B4B9B02E6F09A9BD760F388B67351E2B  |
| NTLMv1  | netntlm  | netntlm::kNS:338d08f8e26de93300000000000000000000000000000000:9526fb8c23a90751cdd619b6cea564742e1e4bf33006ba41:cb8086049ec4736c  |
| NTLMv2  | netntlmv2  | admin::N46iSNekpT:08ca45b7d7ea58ee:88dcbe4446168966a153a0064958dac6:5c7830315c7830310000000000000b45c67103d07d7b95acd12ffa11230e0000000052920b85f78d013c31cdb3b92f5d765c783030  |
| Cisco Type 5  | Md5crpy  | enable\_secret\_level\_2:$1$WhZT$YYEI3f0wwWJGAXtAayK/Q.  |

### All Formats: 

```text
descrypt, bsdicrypt, md5crypt, md5crypt-long, bcrypt, scrypt, LM, AFS,  
tripcode, AndroidBackup, adxcrypt, agilekeychain, aix-ssha1, aix-ssha256,  
aix-ssha512, andOTP, ansible, argon2, as400-des, as400-ssha1, asa-md5,  
AxCrypt, AzureAD, BestCrypt, bfegg, Bitcoin, BitLocker, bitshares, Bitwarden,  
BKS, Blackberry-ES10, WoWSRP, Blockchain, chap, Clipperz, cloudkeychain,  
dynamic_n, cq, CRC32, sha1crypt, sha256crypt, sha512crypt, Citrix_NS10,  
dahua, dashlane, diskcryptor, Django, django-scrypt, dmd5, dmg, dominosec,  
dominosec8, DPAPImk, dragonfly3-32, dragonfly3-64, dragonfly4-32,  
dragonfly4-64, Drupal7, eCryptfs, eigrp, electrum, EncFS, enpass, EPI,  
EPiServer, ethereum, fde, Fortigate256, Fortigate, FormSpring, FVDE, geli,  
gost, gpg, HAVAL-128-4, HAVAL-256-3, hdaa, hMailServer, hsrp, IKE, ipb2,  
itunes-backup, iwork, KeePass, keychain, keyring, keystore, known_hosts,  
krb4, krb5, krb5asrep, krb5pa-sha1, krb5tgs, krb5-17, krb5-18, krb5-3,  
kwallet, lp, lpcli, leet, lotus5, lotus85, LUKS, MD2, mdc2, MediaWiki,  
monero, money, MongoDB, scram, Mozilla, mscash, mscash2, MSCHAPv2,  
mschapv2-naive, krb5pa-md5, mssql, mssql05, mssql12, multibit, mysqlna,  
mysql-sha1, mysql, net-ah, nethalflm, netlm, netlmv2, net-md5, netntlmv2,  
netntlm, netntlm-naive, net-sha1, nk, notes, md5ns, nsec3, NT, o10glogon,  
o3logon, o5logon, ODF, Office, oldoffice, OpenBSD-SoftRAID, openssl-enc,  
oracle, oracle11, Oracle12C, osc, ospf, Padlock, Palshop, Panama,  
PBKDF2-HMAC-MD4, PBKDF2-HMAC-MD5, PBKDF2-HMAC-SHA1, PBKDF2-HMAC-SHA256,  
PBKDF2-HMAC-SHA512, PDF, PEM, pfx, pgpdisk, pgpsda, pgpwde, phpass, PHPS,  
PHPS2, pix-md5, PKZIP, po, postgres, PST, PuTTY, pwsafe, qnx, RACF,  
RACF-KDFAES, radius, RAdmin, RAKP, rar, RAR5, Raw-SHA512, Raw-Blake2,  
Raw-Keccak, Raw-Keccak-256, Raw-MD4, Raw-MD5, Raw-MD5u, Raw-SHA1,  
Raw-SHA1-AxCrypt, Raw-SHA1-Linkedin, Raw-SHA224, Raw-SHA256, Raw-SHA3,  
Raw-SHA384, ripemd-128, ripemd-160, rsvp, Siemens-S7, Salted-SHA1, SSHA512,  
sapb, sapg, saph, sappse, securezip, 7z, Signal, SIP, skein-256, skein-512,  
skey, SL3, Snefru-128, Snefru-256, LastPass, SNMP, solarwinds, SSH, sspr,  
Stribog-256, Stribog-512, STRIP, SunMD5, SybaseASE, Sybase-PROP, tacacs-plus,  
tcp-md5, telegram, tezos, Tiger, tc_aes_xts, tc_ripemd160, tc_ripemd160boot,  
tc_sha512, tc_whirlpool, vdi, OpenVMS, vmx, VNC, vtp, wbb3, whirlpool,  
whirlpool0, whirlpool1, wpapsk, wpapsk-pmk, xmpp-scram, xsha, xsha512, ZIP,  
ZipMonster, plaintext, has-160, HMAC-MD5, HMAC-SHA1, HMAC-SHA224,  
HMAC-SHA256, HMAC-SHA384, HMAC-SHA512, dummy, crypt 
```

## Cracking examples

### Cracking /etc/shadow

```text
sudo /usr/sbin/unshadow /etc/passwd /etc/shadow > /tmp/crack.password.db 
john /tmp/crack.password.db 
Loaded 2 password hashes with 2 different salts (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x]) 
```

### Cracking pdf protected password

```text
pdf2john encrypted.pdf >> hash 
john hash --mask=?d?d?d?d?d?d?d?d?l 
pdftotext -upw PASSWORD encrypted.pdf 
```

### MD5 wordlist

```text
root@attackdefense:~# for x in $(cat wordlists/100-common-passwords.txt); do echo -n $x | md5sum >> wordlist.txt; done 
root@attackdefense:~# cat wordlist.txt | cut -d' ' -f1 >> new 
root@attackdefense:~# john hash --wordlist=new 
```





## John cheat sheet

[https://countuponsecurity.files.wordpress.com/2016/09/jtr-cheat-sheet.pdf](https://countuponsecurity.files.wordpress.com/2016/09/jtr-cheat-sheet.pdf) 


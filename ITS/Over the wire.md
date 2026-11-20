# Over the wire

## Connecting via ssh

```
	 ssh -p 2220 bandit0@bandit.labs.overthewire.org
```

With password `bandit0`

```
  This machine might hold several wargames.
  If you are playing "somegame", then:

    * USERNAMES are somegame0, somegame1, ...
    * Most LEVELS are stored in /somegame/.
    * PASSWORDS for each level are stored in /etc/somegame_pass/.

  Write-access to homedirectories is disabled. It is advised to create a
  working directory with a hard-to-guess name in /tmp/.  You can use the
  command "mktemp -d" in order to generate a random and hard to guess
  directory in /tmp/.  Read-access to both /tmp/ is disabled and to /proc
  restricted so that users cannot snoop on eachother. Files and directories
  with easily guessable or short names will be periodically deleted! The /tmp
  directory is regularly wiped.
  Please play nice:

    * don't leave orphan processes running
    * don't leave exploit-files laying around
    * don't annoy other players
    * don't post passwords or spoilers
    * again, DONT POST SPOILERS!
      This includes writeups of your solution on your blog or website!
```

```
--[ Tips ]--

  This machine has a 64bit processor and many security-features enabled
  by default, although ASLR has been switched off.  The following
  compiler flags might be interesting:

    -m32                    compile for 32bit
    -fno-stack-protector    disable ProPolice
    -Wl,-z,norelro          disable relro

  In addition, the execstack tool can be used to flag the stack as
  executable on ELF binaries.

  Finally, network-access is limited for most levels by a local
  firewall.
```

```
--[ Tools ]--

 For your convenience we have installed a few useful tools which you can find
 in the following locations:

    * gef (https://github.com/hugsy/gef) in /opt/gef/
    * pwndbg (https://github.com/pwndbg/pwndbg) in /opt/pwndbg/
    * gdbinit (https://github.com/gdbinit/Gdbinit) in /opt/gdbinit/
    * pwntools (https://github.com/Gallopsled/pwntools)
    * radare2 (http://www.radare.org/)
```

## Level 1

`cat readme`

```
The password you are looking for is: 6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR
```

for bandit1

## Level 2

Since the filename is `-` you cannot simply open it. `-` expects a flag.

Therefore write `cat ./-`

`du -` gives result `4` since `-` spans 4 bytes (gives size of file)

resulting password: `PK8fYLZg2hnHSz83plBL1iEPKdD3QToB`

## Level 3

`cat ./--spaces\ in\ this\ filename--`

Spaces are special characters

resulting password: `7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME`

## Level 4

`ls -xa`

```
 -a, --all
Do not ignore hidden files (files with names that start with '.').
```


```bash
 ls -a
 cat ./...Hiding-From-You 
```

`xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq`

## Level 5

Here, use `file` command to try to guess the type of file. Only human readable is ASCII in `-file07`

`6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG`

## Level 6

`ls inhere`

`find . -type f -size 1033c ! -executable`

`pXa26xhMWaC2SvDotA4r9EgZkulOeSBW`

## Level 7

`find / -user bandit7 -group bandit6 -size 33c 2>/dev/null`

`2>/dev/null` hides the many“Permission denied” errors.

`Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3`

## Level 8 

`grep millionth`

`VR1ljMayciFxbnUokuQmJFw6QC9VKtub`

## Level 9

`uniq` only detects adjacent duplicate lines.

`sort data.txt | uniq -u`
Passes sorted lines to uniq -u which prints unique lines that occur once


`EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl`


## Level 10

Elegant solution:
```bash
bandit9@bandit:~$ strings data.txt | grep -n -E "==+ [A-Za-z0-9]"
13:========== the
61:========== password
81:Y========== is
178:========== B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

`strings` print the sequences of printable characters in files
`grep` matches lines that match regex
`-n` prints line numbers
`-E` extended regex

## Level 11

`base64` encodes per standard and `base64 -d` decodes:

```bash
cat data.txt
	VGhlIHBhc3N3b3JkIGlzIHBZZk9ZNkh3VXNEajVyTDlVdnloVTdNQ212OHZONVJvCg==

base64 -d data.txt
	The password is pYfOY6HwUsDj5rL9UvyhU7MCmv8vN5Ro
```

## Level 12

`bandit11@bandit:~$`

https://overthewire.org/wargames/bandit/bandit13.html


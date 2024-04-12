# liblzma and xz version 5.6.0 and 5.6.1 are vulnerable to arbitrary code execution compromise

<span class="text-xs font-semibold">
UPDATE(M03-29-2024 13:43-EDT): This is [CVE-2024-3094](https://nvd.nist.gov/vuln/detail/CVE-2024-3094).
</span>
</br>
</br>
This is a new situation and we are still gathering information. Here is what we know so far:

The [xz/liblzma project](https://github.com/tukaani-project/xz) has released versions 5.6.0 and 5.6.1.
<br><br>
The combination of this and patches made by some distributions to the interactions between liblzma, libsystemd, and sshd have resulted in a situation where an attacker can compromise a system by sending a malicious payload to an sshd server.
<br><br>
We are lucky. This only affects AMD64 Linux systems. Currently, incomplete analysis of the vulnerability suggests that this only targets a specific RSA function used in sshd. The exploit is in the wild. This is also a very new version of xz/liblzma, so it is not widely deployed yet. This is also unlikely to affect anything other than Glibc (because of glibc IFUNC support), so if you use [musl](https://musl.libc.org/) or another libc implementation, you are likely safe.
<br><br>

If you are using a distribution that has not yet released xz 5.6.0 or 5.6.1, you are likely safe.
<br><br>
If you are running Debian sid, Fedora 40, Fedora Rawhide, openSUSE Tumbleweed, or openSUSE MicroOS, run updates now.
<br><br>

Here are the distros where it is likely to be released (according to [repology](https://repology.org/project/xz/versions)):

- Alpine Edge
- Arch
- Cygwin
- Exherbo
- Gentoo
- Homebrew
- KaOS
- MacPorts
- Manjaro Testing
- NixOS Unstable/nixpkgs unstable
- OpenIndiana
- OpenMamba
- OpenMandriva Rolling
- Parabola
- PCLinuxOS
- Pisi Linux
- pkgsrc current
- Ravenports
- Slackware current
- Solus
- Termux
- Wikidata

</br>

If you are using one of these distributions, you should check to see if you are using xz version 5.6.0 or 5.6.1. If you are, you should downgrade to 5.4.6. If you can't downgrade, you should disable public-facing SSH servers until you can downgrade.

At this time, we believe that version 5.4.6 is not vulnerable to this exploit. If you are using a different version, you should check with your distribution's security mailing list to see if you are vulnerable. If you are not already subscribed to your distribution's security mailing list, you should do so now.

Here is how you can tell if you're running the affected version:

```
xz --version
```

Here is what the output on the vulnerable version looks like:

```
$ xz --version
xz (XZ Utils) 5.6.1
liblzma 5.6.1
```

Stay tuned for more information. [Red Hat's security advisory](https://www.redhat.com/en/blog/urgent-security-alert-fedora-41-and-rawhide-users) may be helpful.
</br>
---
</br>
<br>
Special thanks to titanous for pre-vetting this before it went live.

 
Note: configure now enables DCO build by default on FreeBSD and Linux. On Linux this brings in a new default dependency for libnl-genl (for Linux distributions that are too old to have a suitable version of the library, use "configure --disable-dco")
 
**Download ✔ [https://fienislile.blogspot.com/?download=2A0SQj](https://fienislile.blogspot.com/?download=2A0SQj)**


 
Note that OpenVPN 2.5.x is in "Old Stable Support" status (see SupportedVersions). This usually means that we do not provide updated Windows Installers anymore, even for security fixes. Since this release fixes several issues specific to the Windows platform we decided to provide installers anyway. This does not change the support status of 2.5.x branch. We might not provide security updates for issues found in the future. We recommend that everyone switch to the 2.6.x versions of installers as soon as possible.
 
The OpenVPN community project team is proud to release OpenVPN 2.5.6. This is mostly a bugfix release including one security fix ("Disallow multiple deferred authentication plug-ins.", CVE: 2022-0547). The I605 installers include OpenVPN GUI with a bug fix, as well as updated OpenSSL (1.1.1o).
 
The OpenVPN community project team is proud to release OpenVPN 2.5.5. The most notable changes are Windows-related: use of CFG Spectre-mitigations in MSVC builds, bringing back of OpenSSL config loading and several build fixes. More details are available in Changes.rst.
 
The OpenVPN community project team is proud to release OpenVPN 2.5.4. This release include a number of fixes and small improvements. One of the fixes is to password prompting on windows console when stderr redirection is in use - this breaks 2.5.x on Win11/ARM, and might also break on Win11/amd64. Windows executable and libraries are now built natively on Windows using MSVC, not cross-compiled on Linux as with earlier 2.5 releases. Windows installers include updated OpenSSL and new OpenVPN GUI. The latter includes several improvements, the most important of which is the ability to import profiles from URLs where available. Installer version I602 fixes loading of pkcs11 files on Windows. Installer version I603 fixes a bug in the version number as seen by Windows (was 2.5..4, not 2.5.4). Installer I604 fixes some small Windows issues.

The OpenVPN community project team is proud to release OpenVPN 2.5.3. Besides a number of small improvements and bug fixes, this release fixes a possible security issue with OpenSSL config autoloading on Windows (CVE-2021-3606). Updated OpenVPN GUI is also included in Windows installers.
 
The OpenVPN community project team is proud to release OpenVPN 2.5.2. It fixes two related security vulnerabilities (CVE-2020-15078) which under very specific circumstances allow tricking a server using delayed authentication (plugin or management) into returning a PUSH\_REPLY before the AUTH\_FAILED message, which can possibly be used to gather information about a VPN setup. In combination with "--auth-gen-token" or a user-specific token auth solution it can be possible to get access to a VPN with an otherwise-invalid account. OpenVPN 2.5.2 also includes other bug fixes and improvements. Updated OpenSSL and OpenVPN GUI are included in Windows installers.
 
Our MSI installer do not currently support the Windows ARM64 platform. You need to use our NSI-based snapshot installers from here. We recommend using the latest installer that matches one of these patterns:
 
The OpenVPN community project team is proud to release OpenVPN 2.4.12, the final release in the 2.4.x series. This is mostly a bugfix release including one security fix ("Disallow multiple deferred authentication plug-ins.", CVE: 2022-0547).
 
The OpenVPN community project team is proud to release OpenVPN 2.4.11. It fixes two related security vulnerabilities (CVE-2020-15078) which under very specific circumstances allow tricking a server using delayed authentication (plugin or management) into returning a PUSH\_REPLY before the AUTH\_FAILED message, which can possibly be used to gather information about a VPN setup. This release also includes other bug fixes and improvements. The I602 Windows installers fix a possible security issue with OpenSSL config autoloading on Windows (CVE-2021-3606). Updated OpenSSL and OpenVPN GUI are included in Windows installers.
 
Please note that LibreSSL is not a supported crypto backend. We accept patches and we do test on OpenBSD 6.0 which comes with LibreSSL, but if newer versions of LibreSSL break API compatibility we do not take responsibility to fix that.
 
Also note that Windows installers have been built with NSIS version that has been patched against several NSIS installer code execution and privilege escalation problems. Based on our testing, though, older Windows versions such as Windows 7 might not benefit from these fixes. We thus strongly encourage you to always move NSIS installers to a non-user-writeable location before running them.
 
If you find a bug in this release, please file a bug report to our Trac bug tracker. In uncertain cases please contact our developers first, either using the openvpn-devel mailinglist or the developer IRC channel (#openvpn-devel at irc.libera.chat). For generic help take a look at our official documentation, wiki, forums, openvpn-users mailing list and user IRC channel (#openvpn at irc.libera.chat).
 
**Important:** you will need to use the correct installer for your operating system. The Windows 10 installer works on Windows 10 and Windows Server 2016/2019. The Windows 7 installer will work on Windows 7/8/8.1/Server 2012r2. This is because of Microsoft's driver signing requirements are different for kernel-mode devices drivers, which in our case affects OpenVPN's tap driver (tap-windows6).
 
This is primarily a maintenance release with bugfixes and improvements. This release also fixes a security issue (CVE-2020-11810, trac #1272) which allows disrupting service of a freshly connected client that has not yet not negotiated session keys. The vulnerability cannot be used to inject or steal VPN traffic.
 
Also note that Windows installers have been built with NSIS version that has been patched against several NSIS installer code execution and privilege escalation problems. Based on our testing, though, older Windows versions such as Windows 7 might not benefit from these fixes. We thus strongly encourage you to always move NSIS installers to a non-user-writeable location before running them. We are moving to MSI installers in OpenVPN 2.5, but OpenVPN 2.4.x will remain NSIS-only.
 
Compared to OpenVPN 2.3 this is a major update with a large number of new features, improvements and fixes. Some of the major features are AEAD (GCM) cipher and Elliptic Curve DH key exchange support, improved IPv4/IPv6 dual stack support and more seamless connection migration when client's IP address changes (Peer-ID). Also, the new --tls-crypt feature can be used to increase users' connection privacy.
 
OpenVPN GUI bundled with the Windows installer has a large number of new features compared to the one bundled with OpenVPN 2.3. One of major features is the ability to run OpenVPN GUI without administrator privileges. For full details, see the changelog. The new OpenVPN GUI features are documented here.
 
**NOTE:** the GPG key used to sign the release files has been changed since OpenVPN 2.4.0. Instructions for verifying the signatures, as well as the new GPG public key are available here.
 a2f82b0cb4
 

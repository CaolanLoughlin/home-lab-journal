## [21.09.2026] — Setting Up the Home Lab: Windows 11 VM

**Goal:** Install VirtualBox and get a Windows 11 VM running as the first
piece of my home lab.
**What happened:** Install went smoothly, but the display wouldn't extend
past a small fixed resolution — no matter how I resized the window.
**Diagnosis:** Realised Guest Additions hadn't installed properly, which
handles display scaling, shared clipboard, and performance between host
and VM.
**Fix:** Reinstalled Guest Additions manually as Administrator from inside
the VM, then rebooted — resolution scaling worked correctly afterward.
**Takeaway:** Small, "invisible" components like guest drivers can cause
issues that look unrelated on the surface. Good reminder to check the
obvious layer (drivers) before assuming something more complex is wrong.

---

## [21.09.2026] — Adding an Ubuntu VM

**Goal:** Install Ubuntu as a second VM to start getting comfortable with
Linux alongside Windows.
**What happened:** Installation ran slowly, and when I checked back on it
later I was met with a black screen with no visible progress.
**Diagnosis:** Suspected the installer had hung rather than crashed
outright.
**Fix:** Powered off and rebooted the VM — it came up cleanly with a
working login screen on the next boot.
**Takeaway:** Not every "broken-looking" state is actually broken — a
clean reboot is a legitimate first troubleshooting step, and one I used
constantly in kitchens too (reset before you diagnose further).

---

## [21.09.2026] — Networking the Two VMs Together

**Goal:** Get the Windows 11 and Ubuntu VMs talking to each other over
the network, to practice basic connectivity troubleshooting.
**What happened:** Pinging the Windows VM's IP address from Ubuntu
produced no replies — request just hung with no response.
**Diagnosis:** Checked IP configuration on both VMs (ipconfig / ip addr)
— both were correctly on the same bridged network. Suspected Windows
Firewall was blocking the request by default.
**Fix:** Enabled the "File and Printer Sharing (Echo Request - ICMPv4-In)"
inbound rule in Windows Defender Firewall. Re-ran the ping — got full
replies with 0% packet loss. Confirmed the reverse direction
(Windows → Ubuntu) worked too.
**Takeaway:** Windows blocks inbound ping by default as a security
measure — this is exactly the kind of "it's not broken, it's
configured that way" issue that comes up constantly in real IT support.

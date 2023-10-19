# SEB vm escape

***DISCLAIMER: this project hasn't been made for any cheating purposes but rather for being able to run the Safe Exam Browser without it having access to any of your personal data and also being able to run it on computers running LINUX :)***

i've patched 3 Dynamic Link Library to make this possible :

**SafeExamBrowser.SystemComponents.dll**:
contains a class responsible of checking for vm, the following things are checked :

 1. PCI devices including certain string related to emulation
 2. default MAC adress prefix

**SafeExamBrowser.Monitoring.dll :**
it contains a method called ValidateConfiguration that check for any external displays and virtual display, i just modified so it would always validate the configuration

**SafeExamBrowser.Configuration.dll :**
it contains a `TryVerifyCodeSignature` method that calls the function `VerifyCodeSignature` from the `seb_x64.dll`  that is supposed to verify code integrity.
the `TryVerifyCodeSignature` is not called anymore in the patched DLL

## installation

 1. create a standard windows 10 VM
 2.  install SEB normally
 3. navigate to the SEB installation path and locate the dll
 4. replace them
 5. use SEB as you would normally

## Changelog

19/10/23:
- added support for SEB 3.5.0
- you can now open other apps on the guest machine by opening task manager (ctrl + alt + del) and then open the file location of a process in the task manager and navigate around to open whatever you need
- DISCLAIMER : i haven't done a lot of tests with this version if you find any report it

## Recommendations

to make SEB run inside a VM you should rather create a hardened VM by changing what i listed that is used to detect them.
Since you modified the program your school may not be happy about it.
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

## Recommendations

to make SEB run inside a VM you should rather create a hardened VM by changing what i listed that is used to detect them.
Since you modified the program your school may not be happy about it.
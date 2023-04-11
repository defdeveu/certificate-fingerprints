# Fingerprints/digests of the learners' certificates issued by def.dev

This repo holds SHA256 digests of pdf certificates issued in the (printable) format illustrated below.  
(Validation of the 'looney tunes' styled badges does not belong here.)  
(Learners' PII is not present in this public repo.)  

### def.dev certificate hashes
There are two types of hashes involved in your def.dev certificate. The SHA256 hash verifies the authenticity of your PDF certificate -- call it the fingerprint or digest. This repo publicly stores these SHA fingerprints. The FNV hash (part of the voucher) is derived from your (work) email address (in lowercase) which was known to def.dev when you attended a course, the first 4 chars of that hash identifies your personal attendance or your exam -- and so the latter hash serves as a locator of your fingerprint file w/o your name being involved.

### Steps to locate your hash:
* There is a unique voucher code on your certificate. Like on the below illustration it's 'b90ix-m4gk'.
* Actually the left part of the voucher is the code of the learning event, while the part on the right (m4gk) is derived from your email address.
* Please recall the work email address you used while attending the course.
* Pre-2022 we took 4 digits from the MD4 hash of your email, nowadays we use the 4 leading digits of the 32-bit FNV-1a hash of your email.
* Grepping this repo for your (very likely) unique 4 chars code is the shortcut for looking up the fingerprint of your pdf. OR: 
* Identify the folder that corresponds with your course event. Usually the exact matching folder name is indicated on the cert, like 'defdev.2305a.ios-red'. (Mobile course events with different platform specific subevents/tracks are placed to folders ending like 'mobile-blue')
* Alternatively if you take a look at your voucher code shown on the pdf certificate and take the first part of it (the code of the course event, like on the below illustration it's 'b90ix') -- the folder with files containing this event code is the one you are looking for.
* Locate the file where the trailing 4 chars of its name match the unique part of your voucher code shown on your pdf certificate (like on the illustration below it was 'm4gk').
* The name of the sha256 file also indicates the certified achievement (attendance, exam, successful lab work), and the subject of the course, like 'ios-red' means an 'iOS hacking/devsec masterclass'.

### Validation
* Running 'openssl dgst' or 'shasum -a 256' against the pdf should output the same hash/fingerprint/digest as published in the corresponding file.

### Illustrations
![](readme.illustration1.png)

### Notes
* The content of the folders is signed by a defdev representative, see the asice files.
* The '-' in the sha256 files is the missing name of the signed file.
* A reminder regarding the defdev's usual folder naming: '2305' means May 2023 (events of April and June might also have been coded as 2305); blue is the color of the standard devsec courses.
* Find a usable implementation for obtaining the 32-bit FNV-1a hash in https://github.com/schwarzkopfb/fnv1a, or google/prompt for the Excel lambda implementation of it.
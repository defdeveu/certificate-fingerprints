# Fingerprints/digests of the learners' certificates issued by def.dev

This repo holds SHA256 digests of PDF certificates issued in the (printable) format, like the one illustrated below.  
(Validation of the 'looney tunes' styled online badges does not belong here.)  
Learners' PII is not present in this public repo (and actually we don't store such data internally in the long term either). Instead, we use voucher codes to identify our alumni members in case of certificate re-issuance or if validation was requested by an employer or any professional body.

### def.dev certificate hashes
There are two types of hashes involved in your def.dev certificate. The *SHA256* hash verifies the authenticity of your PDF certificate -- call it the fingerprint or digest. This repo publicly stores these SHA fingerprints in folders representing a particular learning event. The *FNV* hash (part of the voucher) is derived from your (work) email address (in lowercase) which was known to def.dev when you attended a course, the first 4 chars of that hash identifies your personal attendance or your exam -- and so the latter hash serves as a locator of your fingerprint file w/o your name being involved.

### Steps to locate your hash:
* In short:
  * Guess the folder matching the YYMM of the course you attended. Also indicated on the certificate above the signature.
  * Locate your SHA fingerprint file by the trailing 4 chars which will match the voucher on your PDF certificate.
* There is a unique voucher code on your certificate. Like on the below illustration it's 'b90ix-m4gk':
  * Actually the left part of the voucher is the code of a learning event, which is an alias to the human-readable identifier of that event, like '2305a.ios-red'. The latter identifier is used in naming the folders holding the actual fingerprints of the certificates issued at/for the particular event. The names of SHA fingerprint files hold the voucher type identifier of a course.
  * While the right-side part of the voucher (m4gk) is derived from your email address. Let's call it the **FNV hash**.
    * Please recall the work email address you used while attending the course.
    * We use the 4 leading digits of the 32-bit FNV-1a hash of your email id. (Pre-2022 it was 4 digits from the MD4 hash of an email address.)
    * In some cases you may have been issued two FNV hashes if two email addresses were used in the company, and it was reasonable to assume that years later you may recall only one of those. 
* Grepping this repo for your (very likely) unique 4 chars code (FNV hash) is the shortcut for looking up the fingerprint of your PDF.
* OR: 
  * Identify the folder that corresponds with your course event. Usually the exact matching folder name is indicated on the cert, like 'defdev.2305a.ios-red'. (Mobile course events with different platform specific subevents/tracks are placed in folders ending like 'mobile-blue')
  * Or. Alternatively if you take a look at your voucher code shown on the PDF certificate and take the first part of it (the code of the course event, like on the below illustration it's 'b90ix') -- the folder with files containing this event code is the one you are looking for.
* Locate the file where the trailing 4 chars of its name match the unique part of your voucher code shown on your pdf certificate (like on the illustration below it was 'm4gk').
* The name of the sha256 file also indicates the certified achievement (attendance, exam, successful lab work), and the subject of the course, like 'ios-red' means an 'iOS hacking/devsec masterclass'.

### Validation
* Running 'openssl dgst' or 'shasum -a 256' against the pdf should output the same hash/fingerprint/digest as published in the corresponding file.

### Illustrations
![](readme.illustration1.png)

### Notes
* The content of the folders is signed by a defdev representative, see the asice files.
* The '-' in the sha256 files is the missing name of the signed file.
* A reminder regarding the defdev's usual folder naming: 
  * defdev.{YYMMx}.{platform|mobile|domain|language}.{color}
  * '2305' means May 2023 (events of April and June might also have been coded as 2305); blue is the color of the standard devsec courses.
* Colors:
  * blue -- advanced trainings (the defdev standard)
  * red -- the lab trainings
* Find a usable implementation for obtaining the 32-bit FNV-1a hash in https://github.com/schwarzkopfb/fnv1a, or google/prompt for the Excel lambda implementation of it.
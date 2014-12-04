Signing a Node-Webkit Mac Application (Tested on 10.9.5)

A. REQUEST CERTIFICATE 
Admin or Member:
1) Open "Keychain Access" on your Mac
2) In the menu bar: "Keychain Access" > "Certificate Assistant" > "Request a Certificate From a Certificate Authority"
3) Ensure "User Email Address" and "Common Name" are present, select "Save to disk" and "Continue".
4) Send the newly created file to your agent

B. GENERATE CERTIFICATE 
Agent (Admin are not allowed to create "Developer ID" certificates - http://stackoverflow.com/a/21695283):
1) Go to https://developer.apple.com/account
2) Sign up and go to "Mac Apps" > "Certificates" > "+"
3) Select "Developer ID" at the bottom of the list and "Continue"
4) Select "Developer ID Application" and "Continue"
5) Select "Continue"
6) Upload the CSR file sent by admin (or dev)
7) Download the certificate
8) Send it to the requester

C. INSTALL CERTIFICATE 
Admin or Member:
1) Add the certificate in your keychain by double-clicking it
2) Copy "User ID" in clipboard

D. SIGN APP
Admin or Member:
1) Go to Terminal in the folder containing your .app
$ app="Your\ App.app"
$ identity="User ID" # (pasted from clipboard)
$ codesign --force --verify --verbose --sign "$identity" "$app/Contents/Frameworks/crash_inspector"
$ codesign --force --verify --verbose --sign "$identity" "$app/Contents/Frameworks/node-webkit Framework.framework"
$ codesign --force --verify --verbose --sign "$identity" "$app/Contents/Frameworks/node-webkit Helper EH.app"
$ codesign --force --verify --verbose --sign "$identity" "$app/Contents/Frameworks/node-webkit Helper NP.app"
$ codesign --force --verify --verbose --sign "$identity" "$app/Contents/Frameworks/node-webkit Helper.app"
$ codesign --force --verify --verbose --sign "$identity" "$app"

E. VERIFY SIGNATURE
Admin or Member:
1) Go to Terminal in the folder containing your .app
2) Ensure spctl accept apps signed with "Developer ID"
$ spctl --list --label "Developer ID"
> 6[Developer ID] P0 allow execute
>   anchor apple generic ... exists
> 7[Developer ID] P0 allow install
>   anchor apple generic ...
$ spctl --enable --rule 6 # matching the rule # above
$ spctl --enable --rule 7 # matching the rule # above
3) And then:
$ codesign --verify --verbose=4 "$app"
...
> $app: valid on disk
> $app: satisfies its Designated Requirement
$ spctl --assess --verbose=4 "$app"
> $app: accepted
> source=Developer ID

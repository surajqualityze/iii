Let me build the full extension. I'll create all the files and package them as a ready-to-install zip.Ran 4 commands, created 3 files, read a fileRan 4 commands, created 3 files, read a fileHere's your extension. To install it:
1. Unzip the downloaded file somewhere permanent (like Documents/ig-follow-checker)
2. Load in Chrome:

Go to chrome://extensions
Enable Developer mode (top-right toggle)
Click Load unpacked → select the unzipped folder

How it works:
The extension has two files working together:

inject.js quietly wraps Instagram's own fetch() calls. When you open the followers/following dialog, Instagram loads the list from its API — the script intercepts that response and reads the follow data.
content.js watches the dialog DOM and stamps each user row with a badge:

🟢 Following back — you and this person follow each other
🔴 Not following back — they follow you but you don't follow back (or vice versa on the following list)



Important notes:

You must be logged into Instagram in that tab for it to work
Open the followers/following dialog as normal — badges appear automatically as each page of users loads (Instagram lazy-loads in batches of ~12)
If a badge doesn't appear, try scrolling slowly inside the dialog to trigger the next batch load

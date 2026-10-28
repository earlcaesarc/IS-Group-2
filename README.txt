ITLOG NI JUNPAUL — SOURCE FILE BUNDLE

FILES INCLUDED
- Code.gs: Google Apps Script backend source.
- Code.gs.txt: same backend in Notepad-friendly format.
- index.html: frontend with the latest report-scroll fix.
- index.html.txt: same frontend in Notepad-friendly format.

CURRENT DEPLOYMENT STATUS
These are the latest available source files from this conversation. They are suitable as source files for the existing Google Apps Script app, but they are NOT yet a complete, working Vercel deployment package.

IMPORTANT COMPATIBILITY ISSUE
The frontend calls google.script.run in multiple places. That API exists only inside the Google Apps Script HTML-service environment and will not work when index.html is hosted directly on Vercel. To use Vercel for the frontend while keeping Apps Script as the backend, the project still needs:
1. A secure Apps Script doPost API dispatcher with an allowlist of permitted actions.
2. A Vercel serverless API bridge that forwards requests to the Apps Script web app.
3. Frontend changes that replace google.script.run calls with requests to the Vercel API.
4. Proper per-user session tokens and role authorization. The existing backend uses Apps Script UserProperties for session state, which is not appropriate for independent website users routed through a shared Vercel backend without adaptation.

DO NOT upload only index.html to Vercel and expect login, inventory, sales, delivery, reports, or image upload to work. The page may load but backend actions will fail until the bridge/session changes are implemented and tested.

FOR THE EXISTING GOOGLE APPS SCRIPT APP
1. Back up the spreadsheet and Apps Script project.
2. Open Apps Script and replace Code.gs with the included Code.gs source.
3. Replace index.html with the included index.html source.
4. Save and deploy a new version only after verifying the code against your current spreadsheet.

NOTE
These files have not been live-tested against your deployed Apps Script project or spreadsheet in this package-generation step. Do not run demo/reset/setup functions against live data unless you have reviewed their behavior and made a backup.

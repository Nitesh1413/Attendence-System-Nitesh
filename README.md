# ClassAttend 2.0

Frontend-only attendance prototype using **HTML + CSS + JavaScript**.

## What changed in 2.0
- Added real local student registration storage using IndexedDB.
- Student ID, name, captured profile image and face descriptor are saved locally.
- Registration is one-time on that browser/device; the student does not create a login every attendance session.
- Verification window is **30 seconds**.
- Teacher side has **no face scanning**. Teacher only displays the class QR and receives the growing attendance list.
- CSV export, PDF export, copy/share of the student URL.
- Duplicate attendance is prevented per session/student.
- Teacher PIN and class setup are stored locally.

## Important frontend-only limitations
1. This is a browser-local prototype. There is no central database/server, so different devices/browsers do not share data.
2. Clearing browser site data removes the local student registry and attendance.
3. The face system uses face-api.js in the browser. Its model files are loaded from a public CDN, so first-use needs internet access.
4. The 30-second step is a verification window, not a cryptographic proof of physical presence.
5. Frontend-only authentication can be bypassed by a technically skilled user. For production attendance, use a backend, secure sessions, server-side records, and stronger liveness/anti-spoofing.

## Run
From this folder, use a local server. For example:

### Python
```bash
python -m http.server 8000
```
Then open:
`http://localhost:8000`

Camera permissions generally require localhost or HTTPS.

## Recommended first flow
1. Open the site and complete Teacher Setup.
2. Students open **Register Student** on the device/browser they will later use.
3. Enter Student ID + name and capture the face once.
4. Teacher opens Teacher Board and displays the QR on the classroom digital board.
5. Student scans the QR and opens the student URL.
6. Student starts the **30-sec verification**.
7. Successful verification creates one attendance row for the current class session.
8. Teacher board auto-refreshes the list.
9. Teacher can export CSV or PDF.

## File structure
- `index.html`
- `css/styles.css`
- `js/app.js`

No backend is included, intentionally.

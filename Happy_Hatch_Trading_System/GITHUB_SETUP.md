# Happy Hatch – GitHub storage setup

The apps now load the Excel data file **from GitHub** and save changes **back to GitHub**.
Every save is one commit (who / when / what), so the full history is tracked and any older version can be recovered.

Repository: `rathikaA87/Projects` · branch `main` · folder `Happy_Hatch_Trading_System/Happy_Hatch_Data/`
(To use a different repo or folder, edit the `GH={...}` block near the top of each of the three `.html` files.)

## 1. Upload (one time)
1. Unzip this package on your computer.
2. Open https://github.com/rathikaA87/Projects/upload/main
3. Drag the whole **Happy_Hatch_Trading_System** folder into the page (the folder itself, so the name is kept).
4. Commit message: `Add Happy Hatch Trading System` → **Commit changes**.

Make sure the repository is **Private** (Settings → General → Danger Zone → Change visibility). The data holds prices, margins and customer details.

## 2. Create an access token (one time per person / computer)
GitHub → your profile picture → **Settings** → **Developer settings** → **Personal access tokens** → **Fine-grained tokens** → **Generate new token**
- Repository access: **Only select repositories** → `Projects`
- Permissions → Repository permissions → **Contents: Read and write** (use **Read-only** for people who only use the View-only app)
- Choose an expiry (e.g. 90 days) and copy the token. Do not share it by chat or e-mail.

## 3. Use the apps
1. Open `Happy_Hatch_Trading_Forms_App.html` (or `_User` / `_ViewOnly`) in any browser.
2. First time: click **GitHub access token…** (or **GitHub settings**), paste the token, enter your name, **Save**.
3. The data loads automatically from GitHub.
4. Work as usual. The header shows **● Unsaved changes**. Click **Save to GitHub** (or Ctrl+S), type a short description, press OK.
5. **Reload from GitHub** fetches the latest version (e.g. after a colleague saved).

If someone else saved while you were working, the app refuses to overwrite their work, tells you, and you can **Export Data** to keep a copy, reload, and re-enter your change.

## 4. Tracking changes on GitHub
- Open the folder → **History** to see every save with author, time and your message.
- Excel files cannot be compared cell-by-cell by GitHub, so each save also writes readable CSV copies of every sheet to `Happy_Hatch_Data/Data_Snapshots_CSV/`.
  Open e.g. `SALES.csv` → **History** → click a commit to see exactly which rows were added, changed or removed.
- Restore an old version: open the commit → open `Happy_Hatch_Trading_Inventory_Data.xlsx` → **Download raw file**, then upload it over the current one (or use **Revert** on the commit).

## 5. Good to know
- Product photos picked in the Products form are committed on the next save (`Product_Photos/<code>.<ext>`). You can also drag photos into that folder on GitHub.
- Photos in a private repo are fetched with your token; if a photo does not show, check the token and the file name.
- A token with write access to `Projects` can change every project in that repository. For tighter control, create a separate private repo just for Happy Hatch (then set `GH.repo` and `GH.dir="Happy_Hatch_Data"`).
- The token is kept in this browser only (never inside the HTML files). **GitHub settings → Remove token** deletes it.
- Opening a local Excel file (old method) still works from the gate / header if you ever need it.

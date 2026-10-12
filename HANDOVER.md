# Miles Tracker: handover guide

This guide covers moving the app to your own GitHub account, putting it on your phone, keeping your data safe, logging spending and exporting reports.

You need a free GitHub account (github.com → Sign up). Send Raymond your **GitHub username**.

---

## 1. Raymond transfers the app repo to you

**Raymond does this:**

1. Open the app's repository on GitHub. Under the repo name, click **Settings**.
2. Scroll to the bottom, to the **Danger Zone**, and click **Transfer**.
3. Under "New owner", choose **Specify an organization or username** and type **your GitHub username**.
4. Type the repository name to confirm, then click **I understand, transfer this repository**.

**You do this:**

5. GitHub emails you a confirmation link. **Accept it within one day**, because the invitation expires after that. Then the repo is yours.
6. Optional: GitHub adds Raymond as a collaborator automatically. If you don't want that, remove him under Settings → Collaborators.

> Notes from GitHub's docs: you must not already have a repo with the same name. The old GitHub Pages web address is **not** redirected, so you have to switch Pages on again (step 2).

## 2. Turn the website on (GitHub Pages)

1. In your copy of the repo, go to **Settings → Pages** (left sidebar, under "Code and automation").
2. Under "Build and deployment" → **Source**, choose **Deploy from a branch**.
3. For the branch, pick **main** and the folder **/ (root)**, then click **Save**.
4. After a minute or two the page shows your address:
   **`https://<your-username>.github.io/<repo-name>/`**
   For example, if the repo is called `miles-tracker`, it is `https://<your-username>.github.io/miles-tracker/`.
   You can rename the repo under Settings → General → Repository name, and the address changes to match.
5. Keep this repo **public**. GitHub Pages on a free account only works for public repos. That's fine: the app file has no personal data in it. Your spending lives on your phone and in your *private* data repo (step 4).

## 3. Add it to your phone

**iPhone:** open your address in **Safari** (not Chrome), tap **Share** (the square with an up arrow), then **Add to Home Screen** → **Add**. From now on, open it from the icon.

**Android:** open your address in **Chrome**, tap the **⋮** menu, then **Add to Home screen** (or **Install app**) → **Add**.

On first launch it walks you through a short setup: your 5 cards (all ticked), optional annual-fee months and optional budgets. It starts **empty**, with no sample data.

Two settings are worth checking once:
- **Cards → UOB Lady's Card → Details**: choose the same bonus category you picked in the UOB TMRW app (the default is Dining). The app counts 6 mpd there, which assumes you keep S$10,000+ in a UOB Lady's Savings Account. If you don't, change the rule's mpd to 4 in the same screen.
- **More → Backup & settings → Value of 1 mile**: the default is 1.5 cents. The app uses it to decide whether Citi Cash Back+ (1.6% cash) or a miles card wins. At 1.5 cents, a card has to earn more than about 1.07 miles per dollar to beat the cash back.

## 4. Keep a backup in your own private repo (optional, recommended)

Your data is stored in the phone's browser. If you clear Safari's website data or change phones, it's gone unless you export it or turn on Sync. Sync saves it to a **private** repo that only you can see.

**a. Create the data repo.** On github.com, click **+ → New repository**. Name it `miles-tracker-data`, choose **Private**, tick **Add a README file**, then click **Create repository**.

**b. Create a token that can only touch that repo.**
1. Click your profile picture → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. Name: `miles tracker phone`. Expiration: for example, 1 year.
3. Resource owner: **you**. Repository access: **Only select repositories** → `miles-tracker-data`.
4. Permissions → Repository permissions → **Contents: Read and write**. Leave everything else alone (Metadata read-only is added automatically).
5. Click **Generate token** and copy it. It starts with `github_pat_`.

**c. Enter it in the app.** Open **More → Sync** and fill in:
- **GitHub token**: paste the token
- **Owner**: your GitHub username
- **Repo**: `miles-tracker-data`
- Leave File path (`data.json`) and Branch (`main`) as they are, then tap **Save**.
Then tap **Upload my phone data** once. After that the app syncs by itself.

The token is stored only on that phone. It's never included in exports or in the synced file. If you lose the phone, revoke the token on GitHub (Fine-grained tokens → Revoke).

## 5. Logging a purchase (about 10 seconds)

1. Tap **＋ Add**.
2. Type the amount and tap a category.
3. Choose **In-store** or **Online / in-app**, and how you pay (Apple/Google Pay, card tap, PayPal…).
4. The **Card ranking** shows the best card and why the others lose (cap reached, not eligible…). Citi Cash Back+ shows its cash back in dollars along with its "≈ miles" equivalent.
5. Tap the card you actually used if it's a different one, then tap the **Save** bar.

Rent, PayNow and cash can be logged too (Paid by → Bank transfer / PayNow / Cash). They count in your spending but earn nothing.

## 6. Reports

- **Spend** tab: the last 12 months (by category, miles per month, averages). Tap a month for its summary: miles earned, cash back, card spend, caps used, spend by card and by category, and every transaction.
- **More → Backup & settings**:
  - **Export CSV**: every transaction with date, merchant, category, amount, card, miles, cash back and best card. Opens in Excel, Numbers or Google Sheets.
  - **Export JSON**: a full backup. **Import JSON** restores it, on this phone or a new one.
- **More → Suggest budgets**: optional. It suggests monthly budgets from your history and Singapore benchmarks, and only applies them if you tap to use them.

## 7. Card rules used (checked 12 Oct 2026)

| Card | Earn | Cap |
|---|---|---|
| UOB Lady's Card | 6 mpd on 1 chosen category (any channel) = 4 mpd card + 2 mpd Lady's Savings bonus (needs S$10k average balance in a UOB Lady's Savings Account); 0.4 mpd otherwise | S$1,000 / calendar month (applies to both parts) |
| DBS Woman's World MC | 4 mpd online / in-app; 0.4 local, 1.2 FCY otherwise | S$1,000 / calendar month |
| HSBC TravelOne | 1.2 mpd local, 2.4 mpd FCY (1.0 / 2.0 if converted to KrisFlyer) | none |
| UOB PRVI Miles | 1.4 mpd local, 2.4 FCY, 3 in IDR/MYR/THB/VND | none |
| Citi Cash Back+ | 1.6% cash back | none |

Banks change these often. Check Cards → Details for each card's sources and exclusions.

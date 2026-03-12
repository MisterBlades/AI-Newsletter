# AMD Finance Newsletter Generator

Automatically generates a weekly AMD finance newsletter PDF using the AMD LLM Gateway, covering:

- **AMD Financials & Earnings** — revenue, margins, segments, guidance
- **Global Gaming Market Trends** — Ryzen demand, Steam data, regional patterns
- **Competitor Analysis** — Intel vs AMD (CPU), Nvidia vs AMD (GPU/AI)

Each run produces a professionally formatted PDF saved to the `newsletters/` folder and pushed to your GitHub repo.

---

## Step 1 — Get an AMD LLM Gateway API Key

1. Open your web browser and go to [https://llm.amd.com/](https://llm.amd.com/)
2. Request an API key
3. Copy the key and keep it somewhere safe — you will need it in Step 5

> **Note:** You must be connected to the AMD internal network or VPN for the script to work.

---

## Step 2 — Create a GitHub Account (if you don't have one)

1. Go to [https://github.com](https://github.com)
2. Click **Sign up** and follow the steps to create a free account
3. Verify your email address

---

## Step 3 — Fork the repo

Forking creates your own personal copy of this project on GitHub.

1. Make sure you are logged in to GitHub
2. Go to [https://github.com/LucasbAMD/AI-Newsletter](https://github.com/LucasbAMD/AI-Newsletter)
3. Click the **Fork** button in the top-right corner of the page
4. On the next screen, click **Create fork**
5. GitHub will create a copy at `https://github.com/YOUR_USERNAME/AI-Newsletter`

---

## Step 4 — Install Git (if you don't have it)

Git is the tool that lets you download code from GitHub to your computer.

1. Go to [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Download and run the installer — click **Next** through all the default options
3. Once installed, continue to the next step

---

## Step 5 — Clone your fork to your computer

This downloads your forked repo to your laptop.

1. Press the **Windows key**, type `cmd`, and press **Enter** to open the Command Prompt
2. Decide where you want to save the project. For example, your Desktop:
```
cd %USERPROFILE%\Desktop
```
3. Type the following command, replacing `YOUR_USERNAME` with your GitHub username:
```
git clone https://github.com/YOUR_USERNAME/AI-Newsletter.git
```
4. Press **Enter** — Git will download the files. You should see a new folder called `AI-Newsletter` on your Desktop (or wherever you chose)
5. Navigate into the folder:
```
cd AI-Newsletter
```

---

## Step 6 — Install Python dependencies

These are the libraries the script needs to run.

1. In the same Command Prompt window, type:
```
pip install openai==1.101.0 gitpython reportlab
```
2. Press **Enter** and wait for it to finish — this may take a minute

---

## Step 7 — Edit the script with your API key and folder path

1. Open File Explorer and navigate to your `AI-Newsletter` folder
2. Right-click `generate_newsletter.py` and open it with **Notepad** (or any text editor)
3. At the very top of the file, find the CONFIG block that looks like this:

```python
# ---------------------------------------------------------------------------
# CONFIG — edit these values before running
# ---------------------------------------------------------------------------
API_KEY   = "PASTE_YOUR_AMD_GATEWAY_KEY_HERE"
REPO_PATH = r"C:\Users\lucasb\AI-Newsletter"
GIT_REMOTE = "origin"
GIT_BRANCH = "main"
```

4. Replace `PASTE_YOUR_AMD_GATEWAY_KEY_HERE` with your AMD LLM Gateway API key (keep the quote marks)
5. Replace the `REPO_PATH` with the actual path to your `AI-Newsletter` folder on your computer.
   - To find your path: open File Explorer, navigate to the `AI-Newsletter` folder, click the address bar at the top — it will show you the full path. Copy and paste it.
   - Example: `r"C:\Users\johndoe\Desktop\AI-Newsletter"`
6. Save the file (Ctrl + S) and close Notepad

> **Important:** Never share your API key with anyone or commit it to GitHub.

---

## Step 8 — Run the script

1. Go back to your Command Prompt window (or open a new one and `cd` back into the `AI-Newsletter` folder)
2. Type:
```
python generate_newsletter.py
```
3. Press **Enter**

The script will take a few minutes to run. You will see log messages appearing. When it finishes you should see:
```
Done. Newsletter published to newsletters\amd_finance_newsletter_YYYY-MM-DD.pdf
```

Your newsletter PDF will be saved in the `newsletters/` folder inside your `AI-Newsletter` folder, and automatically pushed to your GitHub repo.

---

## Viewing your newsletter

1. Go to `https://github.com/YOUR_USERNAME/AI-Newsletter` in your browser
2. Click the `newsletters/` folder
3. Click the PDF file to download and view it

---

## What the newsletter looks like

Each PDF includes:
- AMD red branded masthead with the issue date
- Editor's Note
- AMD Financials & Earnings analysis
- Global Gaming Market Trends
- Competitor Analysis (Intel & Nvidia)
- Key Takeaways summary box
- Auto-generated disclaimer footer

---

## Troubleshooting

**`git` is not recognized**
Git is not installed. Go back to Step 4 and install it, then restart your Command Prompt.

**`pip` is not recognized**
Python is not installed or not on your PATH. Download Python from [https://python.org](https://python.org) — make sure to check **"Add Python to PATH"** during installation.

**`Connection error` when running the script**
You are not connected to the AMD internal network or VPN. Connect and try again.

**`Permission denied` on the CSV**
The newsletter PDF is open in another program. Close it and run the script again.

**`REPO_PATH does not exist`**
The path in your CONFIG block is wrong. Double-check it matches the actual location of your `AI-Newsletter` folder.

# davidjclark.net: how to get it live

This folder holds the entire website.

- `index.html`: the site
- `images/headshot.jpg`: your photo
- `papers/`: PDFs you host yourself (empty for now)
- `CNAME`: tells GitHub the site lives at davidjclark.net
- `.nojekyll`: tells GitHub to serve the files as they are (leave it in)

There are three stages: (A) put the site on GitHub, (B) point the Wix domain at GitHub, and (C) shut down the Wix site. **Don't cancel anything on Wix until stage C.**

---

## Before uploading

1. **Your CV.** Name the PDF `cv.pdf` and put it in this folder, next to `index.html`. The "CV ↗" link in the header points there. The old CV lives on Wix's servers, so it will disappear when the Wix site goes.
2. **PDFs for *The Price of Duty* and *The Demands of Necessity*.** These can wait until later. When you have them, add them to `papers/` and change those two "File" links. Claude can do this for you.

---

## A. Put the site on GitHub (about 10 minutes)

1. Sign in at https://github.com (or create a free account). Note your **username**.
2. Click **+** (top right), then **New repository**. Name it `website`, set it to **Public**, and click **Create repository**.
3. On the new repository page, click **uploading an existing file**.
4. Unzip the package. Select **everything inside** the folder (`index.html`, `CNAME`, `README.md`, `.nojekyll`, `cv.pdf`, and the `images` and `papers` folders) and drag it all onto the page. Click **Commit changes**.
   - `.nojekyll` is a hidden file. On a Mac, press **Cmd+Shift+.** in Finder to show hidden files. If it doesn't upload, nothing breaks.
5. Go to **Settings → Pages**. Under **Build and deployment**, set Source to **Deploy from a branch**, set Branch to **main** and **/ (root)**, then click **Save**.
6. The **Custom domain** box should fill in with `davidjclark.net` on its own. If it doesn't, type it in and save.

The site is now hosted on GitHub. It won't appear at davidjclark.net until you finish stage B.

---

## B. Point davidjclark.net at GitHub (in Wix)

Your domain stays registered with Wix. You're only changing where it points.

1. Go to https://manage.wix.com/account/domains.
2. Click the **⋯ (Domain Actions)** icon next to davidjclark.net and choose **Manage DNS Records**.
3. **A (Host) records.** Delete the existing A records with a blank or `@` host name. These are the ones pointing at Wix. Then click **+ Add Record** four times. Leave Host Name blank each time and enter these values:

   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

4. **CNAME (Aliases) records.** Delete or edit the existing `www` record so that:
   - Host Name: `www`
   - Value: `YOUR-GITHUB-USERNAME.github.io`
5. Click **Save Changes**.

Changes can take anywhere from a few minutes to 48 hours to spread. During that time some visitors may still see the old Wix site.

**If Wix won't let you edit these records** because the domain is "connected" to your Wix site, go to the site's settings, disconnect the domain from the site first, and then try again.

---

## C. Finish up

1. Once https://davidjclark.net shows the new site, go back to GitHub **Settings → Pages** and tick **Enforce HTTPS**. If the box is greyed out, try again in a few hours. GitHub needs time to issue the security certificate.
2. Check that `https://www.davidjclark.net` redirects to `https://davidjclark.net`.
3. Now you can cancel the Wix **site** plan if you want to. Before you do, check whether your domain came free with that plan. If it did, cancelling may stop it from renewing. Make sure the **domain** subscription itself stays active and set to auto-renew.

---

## Updating the site later

On GitHub, click `index.html`, click the pencil icon, edit the text, and click **Commit changes**. The live site updates within a minute or two. Change only the words between the `>` and `<` marks, and leave the tags alone.

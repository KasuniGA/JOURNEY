Forking and applying a compatibility patch for defstudio/telegraph
--------------------------------------------------------------

Goal: use `defstudio/telegraph` with Laravel/Illuminate v13 by installing a fork with a small composer.json change.

Steps (summary):

1. Fork upstream `defstudio/telegraph` on GitHub.
2. Create a new branch on your fork: `compat-illuminate-13`.
3. Apply the supplied patch file `patches/telegraph-compat-illuminate-13.patch` to your fork's repo (see details below).
4. Commit and push the branch, then open a PR upstream if you want to contribute the change.
5. In this project, update `composer.json` to point to your fork (this project already contains a placeholder VCS repository entry). Replace `YOUR_GITHUB_USERNAME` with your account and ensure the fork URL is correct.
6. Run: `composer require defstudio/telegraph:dev-compat-illuminate-13` (or run `composer update defstudio/telegraph`).

How to apply the patch in your fork locally

Clone your fork locally and check out the branch:

```bash
git clone https://github.com/YOUR_GITHUB_USERNAME/telegraph.git
cd telegraph
git checkout -b compat-illuminate-13
```

From the root of your fork, apply the patch included in this repo:

```bash
git apply --index ../path/to/this/project/patches/telegraph-compat-illuminate-13.patch
git commit -m "Allow illuminate v13 in composer.json"
git push origin compat-illuminate-13
```

Notes
- The included patch updates the composer `require` constraints to allow Illuminate v13. Review the patch before committing.
- After pushing the branch, the `composer.json` in this project already contains a `repositories` entry pointing at `https://github.com/YOUR_GITHUB_USERNAME/telegraph`. Replace this URL with your fork URL or edit it to include the branch if you prefer.
- If you prefer to install from a local path while testing, you can use a `path` repository type in `composer.json` instead of `vcs`.

If you'd like I can (A) prepare a ready-made commit/PR on your fork (you must provide repo access), or (B) run the local `composer require` after you push the fork. Which do you prefer?

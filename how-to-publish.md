0) Set the `VERSION` in `src/main.c`
```
#define VERSION "va.b"
```

1) Set a tag for the version
```
git tag va.b

git push --tags
```

2) Edit the new tag on GitHub to make it a release with title and description

3) Calculate and copy the sha256sum for the newly released version from the github generated tarball: https://github.com/alt-romes/programmer-calculator/archive/va.b.tar.gz
```
curl -L https://github.com/alt-romes/programmer-calculator/archive/va.b.tar.gz > va.b

sha256sum va.b
```

5) Update formula in the official homebrew repository:
    `brew bump-formula-pr --version a.b pcalc`

6) Wait until homebrew-core accepts the pr, then test the updated brew formula by running
```
brew update

brew upgrade pcalc
```

8) Clone the AUR repository from https://aur.archlinux.org/packages/programmer-calculator/ (you must be a colaborator)

9) Edit `PKGBUILD`
    - change the version `pkgver` to `a.b`
    - update the sha sum to the one just calculated

10) Edit `.SRCINFO`
    - change the version `pkgver` to `a.b`
    - change in `source` references to previous version to the new version `a.b`
    - change the shasum

11) Push changes to the AUR repo

12) Test the AUR repo (howto?)

Command line instructions

```
Git global setup
git config --global user.name "Sunil Kumar Patro"
git config --global user.email "sisintisunil.patro@thomsonreuters.com"
```

```
Create a new repository
git clone git@git.sami.int.thomsonreuters.com:samba-micro/mobile-e2e.git
cd mobile-e2e
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```

```
Existing folder
cd existing_folder
git init
git remote add origin git@git.sami.int.thomsonreuters.com:samba-micro/mobile-e2e.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

```
Existing Git repository
cd existing_repo
git remote add origin git@git.sami.int.thomsonreuters.com:samba-micro/mobile-e2e.git
git push -u origin --all
git push -u origin --tags
```

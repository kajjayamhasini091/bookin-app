# bookin-app
Demo room-booking web application
1️⃣  Authenticate the CLI with your PAT
gh auth login --with-token
When prompted paste:
Press Enter after pasting the token.
2️⃣  Create the repository on GitHub (public)
gh repo create kajjayamhasini091/bookin-app --description "Demo room‑booking web application" --public --confirm
3️⃣  Clone the repo to the exact folder you requested
$localPath = "C:\Users\hasin\Downloads\room booking"
git clone https://github.com/kajjayamhasini091/bookin-app.git "$localPath"
4️⃣  Change into the folder
Set-Location "$localPath"
5️⃣  Create and push the three branches
git checkout -b main
git push -u origin main
git checkout -b develop
git push -u origin develop
git checkout -b feature/booking-form
"Feature: booking form UI placeholder" | Out-File -Encoding utf8 UI.md
git add UI.md
git commit -m "Add UI placeholder (feature branch)"
git push -u origin feature/booking-form
6️⃣  Add a conflicting change on develop
git checkout develop
"Develop branch: add initial API stub" | Out-File -Encoding utf8 UI.md
git add UI.md
git commit -m "Add UI placeholder (develop branch) – conflict source"
git push
7️⃣  Open a pull request (feature → develop)
gh pr create --title "Merge feature/booking-form into develop"     --head feature/booking-form --base develop
    --body "Demo PR to illustrate conflict resolution."
8️⃣  Resolve the conflict locally
git checkout develop
git merge feature/booking-form --no-ff || $true   # merge will conflict
Resolve by keeping both lines (you can edit differently if you wish)
$resolved = @"
Feature: booking form UI placeholder
Develop branch: add initial API stub
"@
$resolved | Out-File -Encoding utf8 UI.md
git add UI.md
git commit -m "Resolve merge conflict between develop and feature/booking-form"
git push

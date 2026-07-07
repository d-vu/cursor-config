# Set up settings and keyboard mapping for VsCode and Cursor

## 1. Authenticate with GitHub

```
brew install gh
gh auth login
```

## → GitHub.com → HTTPS → login with browser

## 2. Clone the repo

```
git clone https://github.com/d-vu/cursor-config.git ~/cursor-config
```

## 3. Back up machine B's existing config, then symlink

```
cd ~/Library/Application\ Support/Cursor/User


mv settings.json settings.json.bak 2>/dev/null
mv keybindings.json keybindings.json.bak 2>/dev/null
```

```
ln -s ~/cursor-config/settings.json settings.json
ln -s ~/cursor-config/keybindings.json keybindings.json

```

---

# Import and install extensions

```
cd ~/cursor-config && git pull
while read -r ext; do cursor --install-extension "$ext"; done < extensions.txt
```

---

# Alias to sync everything

```
cursor ~/.zshrc
```

```
Add alias cpush='cd ~/cursor-config && cursor --list-extensions > extensions.txt && git add -A && git commit -m "sync $(date +%m/%d-%H:%M)" && git push && cd -'
alias cpull='cd ~/cursor-config && git pull && while read -r ext; do cursor --install-extension "$ext"; done < extensions.txt && cd -'
```

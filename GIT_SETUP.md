# 🔧 Git Setup - Losovanie.sk

## ✅ Lokálny Git repozitár je HOTOVÝ!

Váš projekt je inicializovaný s Git a prvý commit je vytvorený.

## 🚀 Postup nahratia na GitHub:

### Možnosť 1: Vytvorte nový repozitár na GitHub (ODPORÚČANÉ)

1. **Choďte na GitHub**: https://github.com/new

2. **Vytvorte nový repozitár**:
   - Repository name: `losovanie-sk` (alebo `losovac`)
   - Description: `🎲 Moderný online losovač pre spravodlivé žrebovania a súťaže`
   - Visibility: **Public** alebo **Private** (podľa vášho výberu)
   - ❌ **NEVYBERAJTE** "Add a README file"
   - ❌ **NEVYBERAJTE** ".gitignore"
   - ❌ **NEVYBERAJTE** "Choose a license"

3. **Po vytvorení repozitára, spustite tieto príkazy**:

```bash
cd /Users/mariansaray/Desktop/Losovac

# Pridajte remote (zmeňte YOUR_USERNAME za vaše GitHub meno)
git remote add origin https://github.com/YOUR_USERNAME/losovanie-sk.git

# ALEBO ak používate SSH:
# git remote add origin git@github.com:YOUR_USERNAME/losovanie-sk.git

# Premenujte hlavnú vetvu na main (ak je potrebné)
git branch -M main

# Nahrajte kód
git push -u origin main
```

4. **Hotovo!** Váš projekt je na GitHube 🎉

---

### Možnosť 2: Použite GitHub CLI (gh)

Ak máte nainštalované GitHub CLI:

```bash
cd /Users/mariansaray/Desktop/Losovac

# Vytvorte repozitár priamo z terminálu
gh repo create losovanie-sk --public --source=. --remote=origin --push

# Alebo pre private:
# gh repo create losovanie-sk --private --source=. --remote=origin --push
```

---

## 📝 Bežné Git príkazy pre tento projekt:

### Pridanie zmien:
```bash
cd /Users/mariansaray/Desktop/Losovac

# Zobraziť status
git status

# Pridať všetky zmeny
git add .

# Commit
git commit -m "Popis zmien"

# Push na GitHub
git push
```

### Vytvorenie novej vetvy pre development:
```bash
# Vytvorte development vetvu
git checkout -b development

# Práca na development vetve...

# Push development vetvy
git push -u origin development
```

### Pull Request workflow:
```bash
# Vytvorte feature vetvu
git checkout -b feature/nova-funkcia

# Urobte zmeny, commit
git add .
git commit -m "Pridaná nová funkcia"

# Push
git push -u origin feature/nova-funkcia

# Potom na GitHube vytvorte Pull Request do main
```

---

## 🔒 SSH vs HTTPS

### HTTPS (jednoduchšie):
```bash
git remote add origin https://github.com/YOUR_USERNAME/losovanie-sk.git
```
- Výhoda: Rýchle nastavenie
- Nevýhoda: Musíte zadávať heslo pri každom push (alebo použiť token)

### SSH (odporúčané):
```bash
git remote add origin git@github.com:YOUR_USERNAME/losovanie-sk.git
```
- Výhoda: Bezpečnejšie, žiadne heslá
- Nevýhoda: Vyžaduje nastavenie SSH kľúča

#### Nastavenie SSH kľúča:
```bash
# Vygenerujte SSH kľúč (ak ešte nemáte)
ssh-keygen -t ed25519 -C "vas@email.com"

# Skopírujte verejný kľúč
cat ~/.ssh/id_ed25519.pub

# Pridajte ho na GitHub:
# Settings → SSH and GPG keys → New SSH key
```

---

## 📊 .gitignore

Súbor `.gitignore` je už vytvorený a obsahuje:
- Systémové súbory (.DS_Store, Thumbs.db)
- IDE súbory (.vscode, .idea)
- Temporary súbory
- Backup súbory

---

## 🌿 Odporúčaná štruktúra vetiev:

```
main              - Produkčná verzia (www.losovanie.sk)
├── development   - Development verzia
│   ├── feature/nova-funkcia-1
│   ├── feature/nova-funkcia-2
│   └── bugfix/oprava-chyby
└── hotfix        - Naliehavé opravy
```

---

## 🤝 Collaboration

Ak chcete pridať spolupracovníkov:

1. GitHub → Settings → Collaborators
2. Pridajte používateľa
3. Oni klonujú repozitár:
```bash
git clone https://github.com/YOUR_USERNAME/losovanie-sk.git
```

---

## 📦 GitHub Releases

Pre vytvorenie release verzie:

```bash
# Vytvorte tag
git tag -a v1.0.0 -m "Verzia 1.0.0 - Prvé production release"

# Push tag
git push origin v1.0.0
```

Potom na GitHube:
- Releases → Create a new release
- Vyberte tag v1.0.0
- Pridajte release notes
- Publikujte

---

## 🔧 Riešenie problémov

### Remote už existuje:
```bash
git remote remove origin
git remote add origin https://github.com/YOUR_USERNAME/losovanie-sk.git
```

### Konflikt pri push:
```bash
git pull origin main --rebase
git push
```

### Zrušiť posledný commit (lokálne):
```bash
git reset --soft HEAD~1
```

---

## 📞 Ďalšie kroky

Po nahratí na GitHub môžete:

1. ✅ Nastaviť GitHub Pages pre hosting
2. ✅ Pridať GitHub Actions pre CI/CD
3. ✅ Nastaviť branch protection rules
4. ✅ Vytvoriť project board pre task management

---

**Pripravené na push!** 🚀

© 2026 Losovanie.sk | Marián Šaray

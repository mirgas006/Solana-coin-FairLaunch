# Solana FairLaunch

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Solana](https://img.shields.io/badge/Solana-Blockchain-black?logo=solana)](https://solana.com/)
[![Anchor](https://img.shields.io/badge/Anchor-Framework-blue)](https://www.anchor-lang.com/)

**Decentralizované a bezpečné riešenie pre spúšťanie tokenov na sieti Solana.** Tento protokol rieši najväčší problém krypto-investícií: bezpečnosť a dôveru. Developer nemá prístup k vyzbieraným prostriedkom v žiadnej fáze launchu.

---

## 🖼️ Ukážka projektu

<img src="./frontend-preview.png" width="400">
*Ukážka používateľského rozhrania pre nákup a predaj v rámci presale.*

---

## ✨ Kľúčové Funkcionality

* **🔒 Escrow systém:** Všetky SOL investované počas presale sú spravované smart kontraktom (Program Derived Address). Nikto, ani vývojár, ich nemôže vybrať manuálne.
* **⚡ Automatické kótovanie na burze (Raydium):** Po dosiahnutí cieľovej sumy (Hard Cap) môže ktokoľvek zavolať funkciu na uvoľnenie likvidity priamo do Raydium DEX.
* **🛡️ Investor Refund System:** Ak sa nevyzbiera cieľová suma, investori môžu svoje tokeny kedykoľvek predať späť kontraktu za pôvodnú cenu (v SOL).

---

## 🛠️ Technický Stack

### Smart Contract (Backend)
- **Rust** & **Anchor Framework**
- **Solana Web3.js** pre komunikáciu s blockchainom.
- Implementácia logiky pre **PDA (Program Derived Addresses)** na izoláciu prostriedkov.

### Frontend
- **React.js** (Next.js)
- **Tailwind CSS** pre moderný dizajn.
- **@solana/wallet-adapter** pre integráciu s Phantom, Solflare a inými peňaženkami.

---

## ⚙️ Logika Protokolu

1.  **Vytvorenie Presale:** Admin inicializuje kontrakt s parametrami: Soft Cap, Hard Cap, cena tokenu a trvanie.
2.  **Investičná fáza:** Používatelia posielajú SOL a dostávajú presale tokeny. SOL sa hromadí v escrow účte kontraktu.
3.  **Ukončenie:**
    * **Success:** Ak je Hard Cap dosiahnutý, kontrakt odomkne funkciu na vytvorenie Liquidity Poolu na Raydium.
    * **Fail/Refund:** Kým nie je splnený cieľ, používateľ môže vyvolať funkciu `sell_back`, vrátiť tokeny a získať svoje SOL späť.

---

## 🚀 Inštalácia a Spustenie

### Prerekvizity
* Rust & Cargo
* Solana CLI
* Anchor Framework
* Node.js & npm/yarn

### 1. Smart Contract
```bash
# Prechod do priečinka s kontraktom
cd program

# Build kontraktu
anchor build

# Spustenie testov
anchor test

# NODIA Chain : mise en ligne du site

## Fichiers
- `index.html` : le site complet (toutes les pages)
- `nodia-logo.png` : ton logo (512 × 512), déjà intégré dans `index.html`
- `robinhood-chain.svg` : à ajouter toi-même (voir plus bas)

## 1. Remplir la configuration
Ouvre `index.html` dans un éditeur de texte et cherche `var CONFIG`. Remplis :

| Champ | Ce que tu mets |
|---|---|
| `nodia.chainId` | Le Chain ID de NODIA Chain (un nombre) |
| `nodia.rpc` | L'adresse de ton RPC (par défaut https://rpc.nodia.network/) |
| `nodia.explorer` | L'adresse de ton explorer |
| `parent.chainId` | 4663 : à vérifier dans la doc officielle de Robinhood Chain |
| `parent.rpc` / `parent.explorer` | Le RPC et l'explorer publics de Robinhood Chain |
| `token` | L'adresse du token $NODIA sur Robinhood Chain |
| `inbox` | L'adresse de l'Inbox du bridge (rollup NODIA) sur Robinhood Chain |
| `priceUsd` | Le prix à afficher en haut, ou `null` |

Tant qu'un champ est vide, le bouton lié affiche un message clair au lieu de planter.

## 2. Ce qui marche
- **Connect wallet** : une fenêtre de choix s'ouvre, avec **Phantom par défaut** en premier. Les autres wallets installés (MetaMask, Rabby, Coinbase…) sont détectés automatiquement. Le site se reconnecte tout seul au dernier wallet utilisé.
- **Ajouter le réseau** : ajoute NODIA Chain au wallet (il faut `nodia.chainId`).
- **Bridge** : bascule sur Robinhood Chain, affiche le solde, autorise le montant exact puis appelle `depositERC20(montant)` sur l'Inbox. C'est le dépôt standard d'un rollup Arbitrum Orbit dont le gas est un token ERC-20.
- **Explorer** : recherche un bloc, une transaction ou une adresse via ton RPC.
- **Dernier bloc** : mis à jour toutes les 5 secondes depuis ton RPC.
- **Boutons Copier** : RPC, Chain ID, contrat du bridge et exemples de code.

## 3. Logo Robinhood Chain
Le badge du bridge charge `robinhood-chain.svg` s'il est à côté de `index.html` ; sinon il affiche « RH ».
Prends le logo officiel dans le kit média de Robinhood et respecte leurs règles d'utilisation de la marque.

## 4. Héberger
Le site est une simple page statique : dépose les fichiers sur Vercel, Netlify, Cloudflare Pages ou GitHub Pages.
Ton RPC doit autoriser le CORS pour le domaine du site, sinon l'explorer et le compteur de blocs ne pourront pas le lire.

## Important avant le lancement
- Fais auditer les contrats du token et du bridge.
- Teste tout le parcours sur un testnet avant le mainnet.

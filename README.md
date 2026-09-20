# MISS INTELLECT MAN 2026 — site de vote

Prototype prêt à personnaliser, en français, avec le logo fourni.

## Fonctionnalités incluses
- Page d'accueil responsive et identité visuelle dorée/noire.
- Liste des candidates configurable dans `data/candidates.json`.
- Vote gratuit : interface prévue pour 1 vote par personne.
- Vote payant : quantité de votes, numéro et choix Orange Money / MTN Money / Moov Money / Wave.
- API de résultats.
- Architecture prévue pour un prestataire de paiement avec webhook serveur.

## Important pour la mise en production
Le paiement réel n'est PAS activé dans ce prototype. Il faut ouvrir/configurer un compte marchand chez un prestataire de paiement et renseigner ses identifiants uniquement côté serveur. Pour la Côte d'Ivoire, CinetPay documente une intégration API/Checkout et affiche actuellement Orange Money, MTN Money, Wave et Moov Money parmi les moyens de paiement disponibles en Côte d'Ivoire.

Il faut également :
1. Ajouter une vraie base de données.
2. Mettre en place OTP/SMS ou une autre vérification pour limiter le vote gratuit à une personne.
3. Ajouter un rate-limit, anti-bot et journal d'audit.
4. Vérifier côté serveur le statut réel de chaque paiement avant d'ajouter les votes.
5. Ne jamais placer une clé API de paiement dans `public/`.
6. Configurer HTTPS et sauvegardes.
7. Ajouter les vraies photos/noms/numéros des candidates.

## Lancer en local
```bash
npm install
npm start
```
Puis ouvrir `http://localhost:3000`.

Tarif d'exemple actuel dans l'interface : 100 FCFA par vote. Il est modifiable dans `public/app.js`.

## Paiement
La documentation officielle du prestataire choisi doit être suivie pour la création de transaction, la vérification et les webhooks. Ne validez jamais un vote payant à partir d'un simple retour du navigateur.

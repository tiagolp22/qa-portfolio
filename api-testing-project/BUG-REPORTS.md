# Bug reports (simulation réaliste)

> Note: Ce document simule des constats QA professionnels pour entraîner la communication de défauts.

## BUG-API-001 — Message d’erreur non standardisé

- **Titre:** Format d’erreur incomplet sur `POST /register` en cas de payload invalide
- **Sévérité:** Moyenne
- **Priorité:** Moyenne
- **Type:** API Contract / DX

### Étapes de reproduction
1. Envoyer `POST {{baseUrl}}/register`
2. Body JSON: `{ "email": "eve.holt@reqres.in" }`
3. Observer la réponse

### Résultat attendu
- Réponse structurée avec au moins:
  - code métier (`errorCode`)
  - message (`message`)
  - identifiant de corrélation (`traceId`)

### Résultat actuel
- Réponse contient uniquement `error: "Missing password"`

### Impact
- Diagnostic plus difficile côté client et support.
- Logging/monitoring distribués moins efficaces sans `traceId`.

---

## BUG-API-002 — Documentation ambiguë sur les contraintes payload

- **Titre:** Contraintes des champs non explicites dans certains endpoints utilisateurs
- **Sévérité:** Faible
- **Priorité:** Faible
- **Type:** Documentation

### Étapes de reproduction
1. Consulter la documentation endpoint de création/mise à jour d’utilisateur.
2. Rechercher les règles de validation (longueur minimale, format, champs obligatoires détaillés).

### Résultat attendu
- Règles de validation explicites et exemples d’erreurs associés.

### Résultat actuel
- Exemples disponibles, mais contraintes détaillées peu visibles.

### Impact
- Risque d’interprétations différentes entre équipes.
- Plus d’allers-retours QA/Dev/API consumers.

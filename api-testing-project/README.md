# Projet 1 — API Testing (Postman)

Ce projet démontre une approche QA pratique pour tester une API REST publique avec Postman.

## API cible

- Base URL: `https://reqres.in/api`

## Objectifs de test

- Vérifier les scénarios CRUD principaux sur les utilisateurs.
- Valider les réponses HTTP (codes de statut, structure JSON, temps de réponse).
- Couvrir des cas négatifs pour détecter les erreurs et comportements inattendus.

## Structure

```text
api-testing-project/
├── collection.json
├── environment.json
└── README.md
```

## Scénarios couverts

### Scénarios positifs

1. **GET /users?page=2**
   - Statut `200`
   - Présence de `data` (tableau)
   - Chaque utilisateur contient `id` et `email`
2. **POST /users**
   - Statut `201`
   - Réponse contient `id` et `createdAt`
3. **PUT /users/2**
   - Statut `200`
   - Réponse contient `updatedAt`
4. **DELETE /users/2**
   - Statut `204`

### Scénarios négatifs

1. **GET /users/23**
   - Statut attendu `404`
2. **POST /register** (payload incomplet)
   - Statut attendu `400`
   - Message d’erreur attendu: `Missing password`

## Types de validations implémentées

- Vérification du **status code**
- Vérification du **temps de réponse** (< 2000 ms)
- Vérification de **champs clés** dans le JSON (`id`, `email`, `createdAt`, `updatedAt`)
- Validation d’un message d’erreur pour un cas négatif

## Bugs / observations QA (simulation)

- **Observation 1 (mineure)**: la documentation de certains endpoints n’indique pas clairement les limites de payload.
- **Observation 2 (moyenne)**: absence d’un format standard d’erreur détaillée (code interne + trace ID) pour faciliter le debug côté client.

## Exécution

1. Importer `collection.json` dans Postman.
2. Importer `environment.json` puis sélectionner l’environnement.
3. Lancer la collection (Collection Runner) ou Newman.

### Exécution avec Newman (optionnel)

```bash
newman run collection.json -e environment.json
```

## Valeur QA démontrée

Ce projet montre:

- la conception de scénarios de test API orientés risque;
- la validation fonctionnelle + technique d’une API;
- la documentation claire des résultats et limites.

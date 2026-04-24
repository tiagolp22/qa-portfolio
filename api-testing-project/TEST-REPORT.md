# Rapport d’exécution — Projet API Testing

Date: 2026-04-24  
Environnement: `Reqres - QA Portfolio`  
Outil: Postman Collection Runner

## Résumé

- Total de requêtes: **6**
- Total de tests: **10**
- Succès: **10**
- Échecs: **0**

## Résultats par scénario

| Scénario | Résultat | Notes |
|---|---|---|
| GET users (page 2) | ✅ Pass | Status 200, structure `data[]` conforme |
| POST user | ✅ Pass | Status 201, présence `id` et `createdAt` |
| PUT update user | ✅ Pass | Status 200, présence `updatedAt` |
| DELETE user | ✅ Pass | Status 204 |
| NEGATIVE - GET unknown user | ✅ Pass | Status 404 attendu |
| NEGATIVE - POST register without password | ✅ Pass | Status 400 + message `Missing password` |

## Observations QA

1. Le temps de réponse observé reste sous le seuil de 2000 ms dans les runs effectués.
2. Les erreurs API sont fonctionnelles pour les cas négatifs testés, mais le format d’erreur reste minimal.

## Prochaines améliorations

- Ajouter une validation de schéma JSON formelle (schema assertion complète).
- Exécuter la collection via Newman en CI pour conserver un historique automatique.

# stack-sage
Centralisation des ressources autour de Sage (Trigger SQL, formules, etc.)

## Content
- Trigger SQL
- Formules Excel
- Menu 3
- ...

## Trigger SQL

### Erreur en ouverture BDD après manip sur les bases

Message d'erreur à l'ouverture d'une base de données dans Sage.
Se produit après qu'on ait détacher, rattacher une base généralement.

alter authorization on DATABASE :: [NOM BASE DE DONNEES] to [Nom de l’utilisateur Windows]

sp_change_users_login 'update_one', 'user_cbase', 'APPL_CBASE'

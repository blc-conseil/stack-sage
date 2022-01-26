<a href="https://bit.ly/blccommu">Discord entraide sur Sage</a>

# stack-sage
Centralisation des ressources autour de Sage (Trigger SQL, formules, etc.)
## Content
<ul>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#resolution-message-derreur">RESOLUTION MESSAGE ERREUR</a>
<ul>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#alter-authorization">Alter authorization</a>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#change-user-id">Change user ID</a>
</ul>
</li>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#evolution-fonctionnelle">EVOLUTION FONCTIONNELLE</a>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#formules-excel">FORMULES EXCEL</a>
 	<li></li>
</ul>
[Test d'un lien](https://blc-conseil.com)

## Resolution message d'erreur

### Alter authorization

<strong>Périmètre = Tous les logiciels Sage 100 version SQL</strong>

Message d'erreur à l'ouverture d'une base de données dans Sage.
Se produit après qu'on ait détacher, rattacher une base généralement.

alter authorization on DATABASE :: [NOM BASE DE DONNEES] to [Nom de l’utilisateur Windows]

### Change user ID

Périmètre = Tous les logiciels Sage 100 version SQL

Message d'erreur à l'ouverture d'une base de données dans Sage.
Se produit après qu'on ait détacher, rattacher une base généralement.

sp_change_users_login 'update_one', 'user_cbase', 'APPL_CBASE'

## Evolution fonctionnelle


## Formules Excel
Test ajout Baptiste

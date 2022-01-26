<a href="https://bit.ly/blccommu">Discord entraide sur Sage</a>

# stack-sage
Centralisation des ressources autour de Sage (Trigger SQL, formules, etc.)

## Disclaimer
:warning: L'utilisation de ces ressources est de votre entière responsabilité.
Nous vous invitons à tester tous les codes sur des bases de test avant de les déployer sur les bases de prod.
Nous ne pourrons en aucun cas être tenu responsable de quelquonques effets de bord suite à l'utilisation de ces ressources sans les précuations qui s'imposent.

## Content
<ul>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#resolution-message-derreur">RESOLUTION MESSAGE ERREUR</a>
<ul>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#alter-authorization">Alter authorization</a>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#change-user-id">Change user ID</a>
  <li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#liste-des-tables-à-vider-utilisateurs-persistants">Liste des tables à vider utilisateurs persistants</a>
</ul>
</li>
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#evolution-fonctionnelle">EVOLUTION FONCTIONNELLE</a>
<ul>
  <li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#voir-les-user-connectes-sur-une-instance-sql">Voir les user connectés sur SQL</a>
</ul>   
 	<li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#formules-excel">FORMULES EXCEL</a>
 	<li></li>
</ul>

## Resolution message d'erreur

### Alter authorization

***Périmètre = Tous les logiciels Sage 100 version SQL***

Message d'erreur à l'ouverture d'une base de données dans Sage.
Se produit après qu'on ait détacher, rattacher une base généralement.

`alter authorization on DATABASE :: [NOM BASE DE DONNEES] to [Nom de l’utilisateur Windows]`

### Change user ID

***Périmètre = Tous les logiciels Sage 100 version SQL***

Message d'erreur à l'ouverture d'une base de données dans Sage.
Se produit après qu'on ait détacher, rattacher une base généralement.

`sp_change_users_login 'update_one', 'user_cbase', 'APPL_CBASE'`

### Liste des tables à vider utilisateurs persistants

***Périmètre = Tous les logiciels Sage 100 version SQL***

Vider les tables suivantes :
-	cbmessage
-	cbnotification
-	cbregfile
-	cbregmessage
-	cbreguser
-	cbusersession


## Evolution fonctionnelle

### Voir les user connectes sur une instance SQL
Dans le SQL Management studio lancer une nouvelle requête :
`sp_who2`


## Formules Excel
Test ajout Baptiste

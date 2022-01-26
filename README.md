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
  <li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#ajustement-des-cumuls-dans-Sage-100-gestion-commerciale">Ajustement des cumuls en gesco (VBS)</a> 
  <li><a href="https://github.com/blc-conseil/stack-sage/blob/main/README.md#script-redemarrage-instance-sql">Script redémarrage instance sql</a> 
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

Quand il reste des utilisateurs connectés qui vous empêchent d'effectuer des traitements de maintenance (Ou des traitements qui nécessite d'être en mono)

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

## Ajustement des cumuls dans Sage 100 Gestion commerciale
Typiquement le genre de code à prendre avec des "pincettes".
A tester et à re-tester sur des copies de base.

Vous pourrez ensuite l'automatiser avec une tâche planifiée et le fichier VBS ci-dessous

Bien sûr il convient de s'approprier le code en remplaçant les arguments par ses propres valeurs :

```

'Exemple de réajustement des cumuls d'une Base Commerciale Sage 100
    Dim IniFile  
    Dim sPathCbaseD
    CONST GCOTE = """"
    CONST PATH_DEFAULTEXE = "C:\Program Files\GecoMaes\"
    CONST EXECIAL = "GecoMaes.exe"
    CONST PATH_BASES = "C:\Documents and Settings\All Users\Documents\Sage\Gestion commerciale\"
    CONST BASECIAL="Bijou.gcm"
    CONST BASECPTA="Bijou.mae"
   
    Call Connect_Gescom()

SUB Connect_Gescom()
    Dim oSheel
    Dim sExeCute
    Dim i
    Dim sPwd, sUser

    Set oSheel = Wscript.CreateObject("Wscript.Shell")
    sUser = "<Administrateur>"
    sPwd = ""
    
    sExecute = GCOTE & PATH_DEFAULTEXE  & EXECIAL & GCOTE & " " & GCOTE & PATH_BASES  & BASECIAL & GCOTE & " " & GCOTE & PATH_BASES  & BASECPTA & GCOTE & " -u" & sUser & " -p" & sPwd
    oSheel.Run sExecute,9
    Wscript.sleep(6000)
    oSheel.SendKeys("%F")   
    oSheel.SendKeys("u")
    oSheel.SendKeys("c")
for i = 1 to 4
    oSheel.SendKeys("{TAB}")
    oSheel.SendKeys("{+}")
next
    Wscript.sleep(6000)
    oSheel.SendKeys("~")
    Wscript.sleep(10000)
    oSheel.SendKeys("~")
    oSheel.SendKeys("%{F4}")
END SUB

```
## Script redemarrage instance sql
Code à rajouter à vos automatismes pour arrêter et redémarrer une instance SQL

_Remplacer "MSSQLSERVER" par le nom de votre instance_

Arrêt de de l'instance :
`Net stop MSSQLSERVER`

Démarrage de l'instance :
`Net start MSSQLSERVER`

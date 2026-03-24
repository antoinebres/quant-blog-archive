---
layout: post
title: synchronisation-microsoft-azure-active-directory-avec-google-cloud-identity-2
date: 2023-01-29
url_wayback_machine: https://web.archive.org/web/20230129154937/https://www.quantmetry.com/blog/synchronisation-microsoft-azure-active-directory-avec-google-cloud-identity-2/
---
Uncategorized 

15/11/2018 

#  Synchronisation Microsoft Azure Active Directory avec Google Cloud Identity 

[ ](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsynchronisation-microsoft-azure-active-directory-avec-google-cloud-identity-2%2F "Facebook") [ ](http://twitter.com/intent/tweet?text=Synchronisation%20Microsoft%20Azure%20Active%20Directory%20avec%20Google%20Cloud%20Identity&url=https%3A%2F%2Fwww.quantmetry.com%2Fblog%2Fsynchronisation-microsoft-azure-active-directory-avec-google-cloud-identity-2%2F "Twitter")

* * *

Temps de lecture : 14 minutes 

![Quantmetry.com : Synchronisation Microsoft Azure Active Directory avec Google Cloud Identity](https://quantmetry.b-cdn.net/wp-content/uploads/2018/11/aad1.jpg)

####  Introduction 

Le présent article décrit l’automatisation et l’industrialisation de la synchronisation des utilisateurs et groupes d’utilisateurs administrés depuis un annuaire Microsoft ** Azure Active Directory (AD)  ** dans l’univers **Google Cloud Platform (GCP)** via ** Google Cloud Identity  ** . Pour information, GCP n’intègre pas d’annuaire d’identité utilisateur, mais s’appuie sur des composants tiers tel Cloud Identity, G Suite ou Gmail, etc. 

La coordination est **unidirectionnelle** : l’AD Microsoft n’est jamais modifié par Google, les flux sont orientés uniquement depuis Microsoft vers Google. 

Si votre organisation possède déjà un AD sur site (en anglais on-premise), pas d’inquiétude, il est possible d’utiliser l’AD locale de l’entreprise comme référence pour centraliser la gestion de l’ensemble de vos identités. Ceci aussi bien au niveau des solutions sur site que de multiples fournisseurs de solutions d’informatiques dans les nuages (en anglais cloud computing). 

Il existe une solution pour synchroniser automatiquement vos ADs sur-site et dans le nuage sans passer par des exports et fichiers CSV. 

####  Intérêt 

Les avantages de la mise en place de cette solution sont doubles. D’un côté, elle simplifie **l’accès aux outils de l’entreprise pour vos collaborateurs** : chacun possède un **identifiant et un mot de passe unique** pour accéder à l’ensemble des services et applications (nuage et sur site). De l’autre, et c’est le principal bénéfice, cette solution accroît **la sécurité de votre Système d’Information (SI)** . D’une part, la maintenance et l’évolution de votre politique de sécurité d’accès sont facilitées : 

  * **Unification de la stratégie de mots de passe** [1]  . 
  * **Activation** de l’Authentification Multiple (en anglais Multi-Factor Authentication, plus connus sous l’acronyme **MFA** ) **centralisée** . Cette fonctionnalité est également appelée **double authentification** ou encore vérification en **deux étapes** (en anglais Two-Factor Authentication, connus sous l’acronyme **2FA** ). 



D’autre part, la **gestion de la rotation de votre personnel est optimisée** : suite au départ d’un de vos collaborateurs, vous désactivez l’ensemble de ses accès d’une seule action. Ainsi, vous éliminez définitivement le risque lié à l’oubli de suppression d’accès à un ou plusieurs services. 

####  Sous le capeau 

Une image vaut mieux qu’un long discours, ci-dessous, le schéma d’interconnexion des différentes briques logicielles spécifiques à chaque plateforme, aussi bien dans le nuage que sur site. 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/aad1.jpg)

Dans le cas où votre organisation possède déjà un AD sur site, l’utilisation du composant **Azure AD Connect** permet de synchroniser automatiquement votre AD dans le nuage à partir de votre AD locale. Par défaut, cette dernière est exécutée toutes les 30 minutes en mode de traitement par lot (en anglais batch). Pour plus d’information, consulter la documentation Azure  https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-scheduler  . 

Par défaut, la synchronisation est unidirectionnelle, l’AD locale est l’unique référentiel. Dans ce contexte, si un utilisateur modifie son mot de passe depuis la plateforme d’informatique dans les nuages, ce dernier – stocké uniquement dans l’AD du nuage – sera écrasé lors de la prochaine synchronisation. L’option **réécriture du mot de passe** (en anglais **password writeback** ) permet d’éviter ce comportement. L’utilisation de cette option sort du cadre de cet article, pour découvrir les fonctionnalités et les prérequis de cette dernière, consulter la documentation Azure  https://docs.microsoft.com/fr-fr/azure/active-directory/authentication/concept-sspr-writeback  . Pour la configuration, suivez le tutoriel Azure  https://docs.microsoft.com/fr-fr/azure/active-directory/authentication/howto-sspr-writeback#configuring-password-writeback  . 

L’interconnexion entre les écosystèmes Microsoft Azure et Google est assurée côté Azure via l’application d’entreprise G Suite. Un composant **approvisionne** (en anglais **provisionning** ) les utilisateurs et groupes. Un autre assure le rôle de fournisseur d’identité que Google Cloud Identity utilise comme fournisseur d’identité tiers (i.e. **authentification unique** ou en anglais **Single Sign-On** , plus connus sous l’acronyme **SSO** ). 

Lors de l’authentification unique, les échanges au sujet des identités entre les univers Microsoft et Google utilisent le protocole **Security Assertion Markup Language** v2.0, plus connus sous l’acronyme **SAML** . D’après Wikipédia, il s’agit d’un standard informatique définissant un protocole pour échanger des informations liées à la sécurité. Basé sur le langage XML, SAML a été développé par OASIS. Pour plus d’information, consulter  https://fr.wikipedia.org/wiki/Security_assertion_markup_language  . 

####  Périmètre technique 

Pour rappel, le but de cet article est de piloter la gestion des utilisateurs GCP via l’annuaire Azure AD. La configuration des différents services d’informatique dans les nuages de Microsoft et Google à l’exception des utilisateurs et groupes est hors périmètre. 

Les services utilisés sont : 

  * Composant Microsoft Azure AD 
  * Google Cloud Identity 
  * GCP avec les utilisateurs issus de Google Cloud Identity 



Aucun service GCP n’est utilisé, la finalité de la manipulation est d’obtenir le succès d’authentification d’un utilisateur géré depuis Azure AD, mot de passe inclus. Suivant la même logique, le composant GCP Cloud IAM, en charge de la gestion des droits des utilisateurs n’est pas utilisé. 

La démarche vise également à prendre en compte la modification des mots de passe utilisateur de façon homogène : lorsque l’utilisateur modifie son mot de passe depuis la plateforme GCP, celui-ci doit être pris en compte sur l’ensemble des plateformes (i.e. GCP et Azure AD). 

####  Pré-requis 

####  Licences 

#####  Écosystème Microsoft 

A minima, il faut une licence **Azure Active Directory Premium P1** . Sans celle-ci, il n’est pas possible d’activer l’approvisionnement par groupe. 

Pour plus d’information sur les différentes éditions et les tarifs, consulter  https://azure.microsoft.com/fr-fr/pricing/details/active-directory/  . 

Si votre organisation possède déjà un abonnement Office 365, Dynamics CRM Online, Enterprise Mobility Suite ou autres services Microsoft, vous disposez d’accès gratuit à Azure AD. Pour plus d’information, consulter  https://docs.microsoft.com/en-us/office365/securitycompliance/use-your-free-azure-ad-subscription-in-office-365  . 

Il est possible de tester gratuitement la version **Azure Active Directory Premium P2** sans limite de fonctionnalités pendant 30 jours. Pour plus d’information, consulter ce  lien  . Une fois la période d’essai révolue, votre configuration n’est pas perdu, il est possible d’acheter une licence adaptée à vos besoins à posteriori. 

#####  Écosystème Google 

Google Cloud Identity existe en deux versions : Free edition ou Premium. La première version est limitée à 14 jours et pour un nombre d’utilisateurs maximum de 50. Dès lors que cette valeur est franchie, vous devez basculer sur l’édition Premium. Pour plus d’information, consulter  https://support.google.com/cloudidentity/answer/7668528?hl=fr&ref_topic=7385935 

#####  Accès 

Pour configurer la jonction entre les deux plateformes, il faut : 

  * Un **compte administrateur Azure AD**
  * Un **compte super-administrateur G Suite** [2] 



En plus des deux comptes ci-dessus, il faut également un **compte de service** [3]  **“virtuel” super-administrateur G Suite** . Ce dernier est utilisé par Azure Active Directory pour approvisionner les utilisateurs Azure AD dans l’écosystème Google. Au moment de la mise en place de l’interconnexion des deux services, la plateforme Azure prend en charge uniquement des comptes utilisateurs et non des comptes de services, d’où la notion de “virtuel”. 

####  Phase exploratoire : automatisation des tâches répétitives 

Pour faciliter la configuration et l’intégration des plateformes, il est pertinent de créer un jeu de test représentatif des utilisateurs et rôles qui composent les différents membres d’une organisation travaillant sur un SI axé autour de la science des données (en anglais Data Science). Ci-dessous, les utilisateurs et rôles affectés utilisés lors des tests : 

![](https://quantmetry.b-cdn.net/wp-content/uploads/2018/12/ad2-1.jpg)

Pour faciliter l’ajout/modification des utilisateurs et groupes, il convient de créer un fichier CSV. Ci-dessous, les colonnes qui composent ce fichier : 

  * **groups** : le(s) groupe(s) auquel l’utilisateur appartient (séparé par des “|”) 
  * **jobTitle** : la fonction de l’utilisateur dans l’organisation 
  * **firstName** : le prénom de l’utilisateur 
  * **lastName** : le nom de l’utilisateur 



**L’identifiant** et **l’adresse e-mail** sont **générés automatiquement** à partir du prénom et nom de l’utilisateur. 

Pour automatiser la création et suppression des utilisateurs, groupes et rattachement des utilisateurs à leur(s) groupe(s) respectif, il faut créer deux scripts PowerShell. L’automatisation de ces tâches rébarbatives permet un véritable gain de temps et d’énergie. En effet, supprimer, puis recréer une liste d’utilisateurs nécessite beaucoup de “clics” via la console d’administration Azure sans que l’action soit porteuse de valeur ajoutée ! 

Voici un aperçu macro des principales APIs utilisées dans le script d’insertion : 

  * **Authentification auprès d’Azure AD**



Connect-AzureAD -TenantId ![TenantId -Credential](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-f17e7117d9021118f3aefee3412d0743_l3.png) Cred 

  * **Récupérer un utilisateur existant dans l’annuaire Azure AD**



![AADUser = Get-AzureADUser -Filter "UserPrincipalName eq '](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-35fd59e2a89ffddee63223b3903ab262_l3.png) UPN' » 

  * **Créer un nouvel utilisateur dans l’annuaire Azure AD**



New-AzureADGroup -DisplayName ![Group -Description](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-50fba7cb7d39b31c41f304543d812920_l3.png) Description -SecurityEnabled ![true -MailEnabled](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-0e8445ae2f8ed60ed88019c30ad23e0b_l3.png) false -MailNickName 
    
    
    *** QuickLaTeX cannot compile formula:
    GroupMailNickName
    <ul class="font_9">
     	<li><strong>Contraindre les utilisateurs ainsi importés à changer leur mot de passe lors de la première authentification</strong></li>
    </ul>
    
    *** Error message:
    Please use \mathaccent for accents in math mode.
    leading text: ...ontraindre les utilisateurs ainsi importé
    
    

PasswordProfile = New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile   
![PasswordProfile.ForceChangePasswordNextLogin =](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-7975dc567d2175888e220933a731530f_l3.png) true   
![PasswordProfile.Password =](https://quantmetry.b-cdn.net/wp-content/ql-cache/quicklatex.com-fbf9c7a7892675122f053940aff8986d_l3.png) NewUserPassword 

# OC-ASRS-Projet-5-Mettez-en-place-des-services-web-securises
OpenClassrooms : Administrateur Systèmes, Réseaux et Sécurité 2024-2025
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Qu'allez-vous apprendre dans ce projet ?

Votre mission consistera à configurer un serveur prototype qui hébergera les sites du projet EXTRANET en utilisant des technologies de pointe telles que NGINX pour les services web et FTPS pour le transfert de fichiers sécurisé. Vous devrez également configurer les éléments de sécurité, notamment netfilter et Fail2Ban, pour assurer la protection des services web. Ce travail impliquera la création et la configuration de plusieurs environnements virtuels pour simuler les différentes infrastructures réseau et tester l'interaction entre les services. Vous allez également générer un certificat SSL auto-signé pour sécuriser les communications.
 
En quoi ces compétences sont-elles importantes pour votre carrière ?

La mise en place d'un prototype de serveur dans un environnement bancaire est essentielle pour assurer que les nouvelles solutions sont robustes, sécurisées, et prêtes pour une implémentation plus large. Les compétences développées dans ce projet incluent la configuration avancée de serveurs, la mise en œuvre de mesures de sécurité strictes et la gestion de la communication sécurisée. Ce sont des compétences clés pour tout administrateur systèmes et réseaux, particulièrement dans le secteur financier où la sécurité et la fiabilité sont primordiales.

 
Prêt à démarrer votre projet ?

Vous allez réaliser un projet réaliste, présenté sous forme de mission en entreprise. Il se rapproche d'une mission typique effectuée sur le terrain.

Le projet est découpé en trois sections :

    Mission - Présentation, qui présente le contexte de votre mission,
    Mission - Détails, qui présente les détails de la mission, sous forme d’échanges avec les collègues,
    Livrables et Soutenance, qui décrit les livrables à fournir et le déroulement de la soutenance de validation.

Prenez soin de lire le projet en entier avant de commencer, pour comprendre ce qui est attendu de vous.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Mission - Présentation

L'entreprise Rainbow Bank est une banque internationale, située à Paris, qui propose des services financiers innovants pour ses nombreux clients particuliers.

 

Vous êtes administrateur systèmes et réseaux au sein du “Pôle Systèmes et Réseaux”, sous la responsabilité d’Aurélie Fernandez. Ce pôle fait lui-même partie de la DIL (Direction Infrastructure et Logistique) pilotée par Catherine Jettamie, et composée de 70 personnes.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Mission - Détails

Ce matin en arrivant au bureau, vous voyez ce message plein d’enthousiasme d’Aurélie :

 

    Aurélie : “Bonjour ! J’ai une super nouvelle. Catherine est absolument ravie de notre dernier projet, encore bravo à toi. Du coup, elle est en confiance et a décidé de débloquer le budget pour le projet EXTRANET. Elle nous a chargés de monter un prototype opérationnel pour valider l’infrastructure qu’on lui a proposée. Si tout se passe bien, nous pourrons contractualiser ensuite avec le prestataire pour le développement. 

    Tu verras, je t’ai laissé un mail qui récapitule la procédure à suivre. À bientôt !“

 

Ça vous motive dès le matin ! Vous ouvrez donc votre boîte mail :

 

Objet : Projet EXTRANET : brief prototype
De : Aurélie Fernandez
À : Moi

Hello,

Catherine a validé le périmètre que nous avons proposé pour le projet EXTRANET. Voici mon brief pour que tu démarres ton travail sur ce projet.

 

Dans un premier temps, tu vas créer un prototype du serveur qui va héberger les sites. Tu trouveras en pièce jointe le compte rendu de notre réunion de la semaine dernière. Il y a toutes les étapes à suivre dont on avait parlé, et que j’ai étoffées pour te guider sur ce prototype.

 

Je te mets également en pièces jointes les maquettes des arborescences de fichiers des deux vhosts. Pour tester tout ça, tu peux te servir de ton poste de travail, il faudra que tu jongles avec la configuration réseau (tu peux aussi utiliser une seconde VM pour simuler les deux infrastructures réseaux). Attention à ne pas te bannir toi-même !

 

Quelques petits détails concernant les technologies à utiliser, et dont j’aurais besoin qu’on rediscute ensemble pendant notre débriefing :

    Catherine a relevé que NGINX faisait aussi une bonne percée sur le marché des services web. J’aimerais donc que tu fasses une comparaison avec Apache en mettant en place le service web avec NGINX également. Comme ça on pourra discuter des différences que tu auras pu identifier.
    Je n’ai pas encore bien compris la différence entre SFTP et FTPS. Il faudra que tu me réexpliques la prochaine fois qu’on se voit, mais utilise FTPS pour le prototype.

Une fois que tu auras terminé, il faudra que tu m’envoies tes fichiers de configuration (des services web et FTP, ainsi que de netfilter et Fail2Ban) pour que je voie comment fonctionne ton prototype.

 

Très bonne journée à toi,

 

Aurélie Fernandez

Pièces jointes : 

    Arborescence des sources du vhost extranet
    Arborescence des sources du vhost admin
    Compte rendu de réunion Prototype EXTRANET

 

Ça y est, vous avez toutes les informations nécessaires pour vous lancer dans la création de ce prototype. À vous de jouer !
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Livrables et soutenance

    Les fichiers de configuration du service web au format ZIP.
        le fichier de configuration principal ;
        les fichiers de configuration de chaque vhost ;
        les fichiers de configuration des modules supplémentaires ;
        les fichiers pour la génération du certificat SSL auto-signé (fichier CSR de request + clé privée + certificat ou bundle PEM).
    Le fichier de configuration du service FTPau format txt.
    Les fichiers de configuration du filtrage netfilter et de Fail2Ban au format.txt.

Pour faciliter votre passage devant le jury, déposez sur la plateforme, dans un dossier zip nommé “Titre_du_projet_nom_prénom”, tous les livrables du projet comme suit : Nom_Prénom_n° du livrable_nom du livrable_date de démarrage du projet. Cela donnera : 

    Nom_Prénom_1_config_service_web_mmaaaa
    Nom_Prénom_2_config_FTP_mmaaaa
    Nom_Prénom_3_config_filtrage_mmaaaa

Par exemple, le premier livrable peut être nommé comme suit : Dupont_Jean_1_X_012022.

 

Durant la présentation orale, l’évaluateur interprétera le rôle d'Aurélie. La soutenance est structurée de la manière suivante :

    Présentation des livrables (15 minutes) 
        Tests de vos configurations réseau, droits d’accès et sécurité :
            tests des accès aux vhosts (depuis les deux pattes réseaux) ;
            tests des filtres IP ;
            tests des accès FTP et des droits sur les arborescences des sources en fonction des comptes connectés ;
            tests de la réaction aux DDoS et slow connections ;
            tests des réponses dynamiques avec Fail2Ban (tentatives de connexion et accès à des ressources inexistantes).
        Explications des points qu’Aurélie vous a demandé de creuser :
            explication de la différence entre SFTP et FTPS ;
            explication de la différence entre Apache et NGINX sur le périmètre de ce prototype (avantages, inconvénients, différences).

    Discussion (10 minutes) 
        Le mentor, qui joue le rôle de votre responsable, posera des questions sur la méthodologie adoptée et sur les livrables.

    Débriefing (5 minutes)
        À la fin de la soutenance, l'évaluateur arrêtera de jouer le rôle d’Aurélie pour vous permettre de débriefer ensemble.

 

Votre présentation devrait durer 15 minutes (+/- 5 minutes). Puisque le respect des durées des présentations est important en milieu professionnel, les présentations en dessous de 10 minutes ou au-dessus de 20 minutes peuvent être refusées. 

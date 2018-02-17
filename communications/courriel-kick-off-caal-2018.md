Courriels de kick-off de la CAAL 2018
---

## Demande initiale

Objet : Réflexion sur le futur des technologies supportées par la DCOD

Commencer une réflexion sur le futur des technologies et d’organiser cette reflxion à l’intérieur d’un rapport de Veille.

J’aimerais avoir vos commentaires et opinions sur les sujets suivants;
* Quels sont les sujets à suivre dans le cadre de la veille technologique
* Le CAAL actuel (ce qui manque, ce qui doit être changé, quand et comment le publier)
* Le « Domain Driven Design »
* Les pistes de modernisation des applications
* La valeur d’une équipe d’infra applicative dans une organisation
* Infrastructure as Code
* Quel peut-être notre apport en assurance Qualité sur le cycle de développement
* La communauté de pratique des concepteurs en architecture détaillée logicielle (CAD-L)

## Réponses HL

Les sujets à suivre dans le cadre de la veille technologique
---

Si on se base sur l’évolution du marché en général, voici qui évoluent rapidement et qui risquent d’être « disruptive » :

* La voix comme interface utilisateur et les assistants : Avec l’apparition des assistants (Google assistant, Siri, Amazon Alexa) et l’intelligence artificielle, cela redéfinit l’interface homme – machine. Évidemment, on ne s’attend pas à ce qu’on commande une transaction bancaire par la voix dans un futur proche, mais c’est un sujet à suivre
* Effervescence du marché d’infrastructure techno : Avec l’ascension de Kubernetes d’une part et du Serverless computing d’autre part, est-ce que nos choix, incluant le PAAS sont encore valides?  À quoi devrait ressembler notre parc applicatif (d’un point de vue de déploiement)? Quelles sont les solutions pour atténuer les coûts d’exploitation? 
* Démocratisation de l’IA et du « machine learning » : On ne s’attend pas à ce que toutes les applications incluent de l’AI ou du machine learning, mais on doit se préparer à des modèles d’intégration avec des composants qui implémentent les algorithmes.
* Démocratisation des infrastructures : Sans utiliser les infrastructures Amazon AWS pour héberger nos applications, peut-on utiliser cette grosse machinerie pour ce qui est de l’analyse des données (Kinesis Streams, composants d’AI) 

Sinon, pour des sujets plus reliés au mandat de notre équipe :

* Quel est l’impact de la « donation » de JEE à la fondation Eclipse sur nos actifs applicatifs?
* Quel est l’impact de la nouvelle stratégie d’évolution d’Oracle pour les JDK sur nos opérations? Oracle annonce deux nouvelles versions par année, et modifie ses plans de support.
* A-t-on encore besoin des Servlet Container? Dans la version Spring Boot 2, et si on opte pour le « reactor web », le container utilisé par défaut Netty (qui remplace Tomcat), n’est pas un Servlet container. 
* Évolution des paradigmes de programmation
    * On assiste à un retour de la programmation fonctionnelle, propulsée par un autre paradigme : la programmation réactive (reactive programming) 
* Évolution des Framework : 
    * Qu’arrive-t-il avec NodeJS? Peut-on le considérer pour le développement de BFF ou de Services de composition? Y a-t-il des alternatives similaires?
    * Pour les développement des micro-services « light-weight » : Y a-t-il des alternatives à Spring? Qu’arrive-t-il avec DropWizard? Sachant que Spring intègre ou s’inspire de certains composants de DropWizard (dropWizard metrics)
* Évolution des langages
    * Que devons-nous faire avec l’ascension de Kotlin?
    * Est-ce que l’utilisation de TypeScript ou de JavaScript du côté Serveur est à prendre en compte?
* Collecte de métriques
    * L’entreprise a de gros problèmes pour la collecte de métriques : On utilise Dynatrace (et ses tableaux de bord). Sachant que Dynatrace est, à la base, un APM. Il y a d’autres solutions moins couteuses, basées sur l’agrégation des Logs et sur les évènements
    * Sauvegarde de métriques à long terme : À ma connaissance, il n’y a aucune solution pour la rétention des métriques à long terme, ex : pour comparer les tendances avec la même période deux ans plus tôt. 
* Automatisation des tests
    * Peut-on adopter TDD (Test Driven Development). 
    * Quels outils de « mocking » peut-on utiliser pour simuler les appels entre les services?   
    * Comment les tests s’intègrent avec les outils tels que HPQC?

Le CAAL actuel (ce qui manque, ce qui doit être changé, quand et comment le publier)
---

Le CAAL actuel, élaboré en 2015, a commencé par le morceau le plus simple, à savoir le support des interfaces REST pour implémenter des micro-services. Il faut supporter d’autres patrons : CQRS, event-driven, near real-time. 

D’abord, nous devons établir les liens entre ces patrons car il y a du chevauchement.

Ensuite, nous devons établir les liens entre les patrons et les infrastructures existantes. Si on dit qu’on veut supporter de l’event-driven et du near real time, est-ce qu’on peut utiliser des solutions « light-weight » ou doit-on se doter de « clusters » Apache Flink ou Apache Spark.

Le « Domain Driven Design »
---

En 2015, nous avons identifié le Domain Driven Design (DDD) comme un outil important pour la réussite d’une architecture en micro-services (MSA). Le concept de « Bounded Context » combiné avec le « strategic design » offrait un outil pour le découpage des (micro) services afin de délimiter les responsabilités et d’éviter les couplages.

Je vois au moins deux problèmes  :
* On n’a jamais su promouvoir les pratiques DDD auprès des équipes. 
* D’autres équipes sont responsables du découpage des services et elles se basent sur d’autres coffres à outils, ex : BIAN

Les pistes de modernisation des applications
---

Il y a un travail d’analyse qui a été fait par Pivotal (commandité par AcceD) sauf qu’on ne l’a pas récupéré.
Aussi, Pivotal est actuellement en train de faire le même travail du côté du PIC.

Cela étant dit, la modernisation des applications peut avoir plusieurs facettes :
* Modernisation pour supporter la « scalability » horizontale : Actuellement, toutes les applications du PIC doivent être déployées dans une même JVM. Cette modernisation permettra aussi d’adopter des modèles de déploiement plus flexibles 
* Modernisation pour pouvoir supporter des  infrastructures techno. plus légères, c.à.d. containers sur le PAAS 
* Modernisation pour supporter (graduellement) des Frameworks plus modernes, c.à.d. Spring Boot
* Modernisation pour rafraichir l’architecture applicative

Évidemment, ces différentes facettes sont reliées et dépendantes.

La valeur d’une équipe d’infra applicative dans une organisation
---

Il y a une dizaine d’années, on disait que le rôle de cette équipe est d’optimiser les coûts de développement en mettant en place les composants réutilisables et évitant à chaque équipe de refaire le même travail.
Ensuite, on a commencé à dire que le rôle de cette équipe est d’offrir un ensemble d’outils et d’encadrements (des pratiques) pour supporter l’uniformisation du développement.
Je pense que ces rôles sont pertinents, mais avec le changement rapide des technologies, il est important que l’entreprise se dote d’une équipe qui a le mandat (et la responsabilité) d’analyser les tendances et de prévoir les changements à venir. De cette responsabilité découle une autre : celle de prendre les mesures nécessaires pour atténuer l’impact des changements sur le parc applicatif et sur la communauté des développeurs.

Infrastructure as Code
---

C’est un prérequis pour l’automatisation. Il n’est pas acceptable qu’on ait encore des intervenants qui lancent des commandes manuelles sur des infrastructures de production.
D’autant plus qu’on doit assurer une immuabilité des infrastructures. 

Quel peut-être notre apport en assurance Qualité sur le cycle de développement
---

Je pense que la DCOD doit s’assurer que :
* Les outils requis pour le TDD soient inclus dans son coffre à outils
* Les pratiques TDD soient vulgarisées et communiquées à l’ensemble des développeurs.

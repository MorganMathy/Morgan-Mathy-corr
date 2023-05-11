# FEEDBACK APPRENANT 4

---

Hello ! J'ai essayé de te faire un retour pour que tu puisses te remettre de tes émotions après ce parcours de fin de saison 6 !
Tout d'abord, je voulais te dire bravo pour le travail accompli. Ce parcours est loin d'être simple et la compréhension de l'architecture MVC prend du temps et je suis certain qu'avec le temps et de la pratique les notions vont être intégrées.

## Aperçu global :wink:

---

C'est un parcours difficile dans lequel tu as implémenté des fonctionnalités un peu trop rapidement. En effet, elles sont correctement codées mais des erreurs d'inattention provoquant des syntaxes incorrectes les rendent non fonctionnelles. Il manque encore des fondements sur le MVC notamment sur l'héritage, la gestion des erreurs et le routing.

## Points de vigilance

- ### Home Sweet Home (ou pas...)

Attention, à peine le serveur lancé, je me retrouve sur une erreur 500 à l'accueil, SYMPA !
L'erreur 500 est, pour simplifier, un problème dans notre code, notamment sur le front controller (`index.php`).
Quand je vais le voir, la route `'/'` est codée correctement. Seul Hic ! Tu n'as pas de MainController? :confused:
```php
$router->map(
    'GET',
    '/',
    [
        'method' => 'home',
        'controller' => MainController::class // On indique le FQCN de la classe
    ],
    'main-home'
);
```
Il faut que tu codes un MainController avec une méthode `'home'` afin que ton front controller puisse s'y retrouver. :wink:
Attention aussi à bien respecter les nomenclatures des routes précisées dans le `docs/routes.md`.

- ### Syntaxe for the lose
```php 
// VERIFICATION QUE L'UTILISATEUR AIT LES DROITS
        $studentsModel = new Students
```
Tu n'as pas mis de ` ; ` après ton instanciation de Students. De plus, j'en profite pour aussi te dire que ton commentaire n'est pas approprié au code qui est en dessous et donc est inutile. De même, pour instancier une classe il faut lui préciser les paramètres (ou non). Dans ce cas: ` $studentsModel = new Students();`

```php
$retour = $teachersdFromDb->teachers();
```
T'as glissé sur le `d` ? :joy:



- ### J'hérite, OK ! Mais j'hérite de quoi au juste ?

C'est super que tu intègres l'héritage dans ton code, mais il faut comprendre pourquoi on fait ça. Dans ton parcours, tu fais hériter tes controllers du CoreController, mais le problème c'est qu'il n'existe pas.
```php
class TeachersController extends CoreController
```

L'héritage nous permet de faire bénéficier à notre Controller des méthodes que le CoreController possède. Dans notre exercice, il serait intéressant que le CoreController possède des méthodes qui profiteraient à toutes les controllers enfants. Par exemple, celle du rendu d'une vue dans un premier temps.
D'ailleurs, tu utilises la méthode `show()` comme cela: 
```php
     // Afficher le template user list
            $this->show("user/user_list", [
                'errors' => $errorList,
                'users' => $users
            ]);
```
Mais bien évidemment la méthode n'étant pas définie tu ne peux pas faire de rendu de de vues.

De la même manière, tes Models héritent aussi d'un CoreModel, qui leur permet l'utilisation de **méthodes communes**.
Pour info :
[Fiche récap sur l'héritage](https://kourou.oclock.io/ressources/fiche-recap/heritage/)


- ### .htaccess manquant ? :hushed:

Je ne vois pas ton fichier .htaccess de réecriture d'URL. Pour rappel : .htaccess permet de réorienter toutes les requêtes vers ton index.php.
Je t'invite à aller lire cette [fiche récap](https://kourou.oclock.io/ressources/fiche-recap/ressources-apache/#v%c3%a9rifier-que-les-htaccess-sont-interpr%c3%a9t%c3%a9s) afin de bien consolider cette notion et/ou vérifier que tu n'aies pas de problèmes de configuration de ton serveur Apache. :+1:

- ### Naming des Class

Attention à cet aspect qui peut t'induire sur des erreurs. Les class sont par convention nommées au **singulier**.

- ### Garder confiance !

Même si ce parcours a du être challengeant, il peut t'induire une grande remise en question. Alors ne te laisse pas submerger, reprends les notions de bases, des exercices, des challenges.
Si tu prévois de t'orienter sur le back et donc la spé Symfony, il te sera essentiel d'acquérir ces connaissances et de les maîtriser.

## Conclusion et pour la suite...

Je te conseille de revoir de fond en comble le design pattern d'un MVC.
En effet, cela est primordial pour comprendre la **Programmation Orientée Objet (POO)**. :wink:
Je te joins ici [Un super tuto de grafikart](https://grafikart.fr/tutoriels/mvc-model-view-controller-574) qui t'aidera à appréhender la POO, le MVC et le concept de routing.

Toutefois, si tu es perdu après correction et révision, n'hésite pas à demander de l'entraide sur le canal **_#entraide_** du slack de la promo. Cela permet à certains plus expérimentés de pouvoir consolider leurs acquis et à toi de peut être mieux comprendre grâce à d'autres personnes.

Enfin, si tu es en grande difficulté pour cet aspect de la formation, tu peux venir en parler auprès de moi ou d'un formateur. Nous essayerons de trouver une solution pour pouvoir t'aider et surmonter cette difficulté.

Je pense que tu as voulu aller trop vite sur ce parcours et que cela ne reflète pas tes capacités. Il vaut mieux bien réussir une ou deux étapes, que de faire 7 ou 8 étapes sans que rien ne soit fonctionnel.


C'est un parcours difficile que tu as essayé de faire pour le mieux, je t'invite à le retenter en fin de saison ou sur des moments que tu auras de libre.
N'oublie pas que chaque notion peut être dérangeante au début et puis elle se décantera avec la pratique.
Je suis persuadé que tu seras, avec quelques jours de révisions et de reprise de challenges, en mesure de réussir ce parcours!

Je compte sur toi ! :wink:



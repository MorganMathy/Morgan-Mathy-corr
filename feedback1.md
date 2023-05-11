# FEEDBACK APPRENANT 1
***
Hello ! J'ai essayé de te faire un retour pour que tu puisses te remettre de tes émotions après ce parcours de fin de saison 6 !
Tout d'abord, je voulais te dire bravo pour le travail accompli. Ce parcours est loin d'être un des plus simples et la compréhension de l'architecture MVC n'est pas donné à tout le monde du premier coup !

## Aperçu global :wink:
***
C'est un parcours dans l'ensemble bien réussi. Ton backoffice est fonctionnel, les routes sont protégées et ton authentification est implementée. Tu sembles avoir compris le fonctionnement du Model View Controller et le routing via AltoRouter.

## Points de vigilance

- ### Routes non protégées vs. Route inutile ! That is the question :smiling_imp:
 
Attention à la lecture des consignes ! :stuck_out_tongue:
```
        - le _Role_ de chaque utilisateur connecté permet de déterminer à quelles ressources/pages il a accès
        - on a 2 _Roles_ dans ce projet : `admin` et `user`
        - les pages liées aux étudiants sont autorisées aux _Roles_ `admin` et `user`
        - les pages liées aux profs ont des permissions plus précises :
          - ajout, modification et suppression autorisés au _Role_ `admin`
          - liste autorisée aux _Roles_ `admin` et `user`
```

Or, tes ACL de ton CoreController donnent accès à ton utilisateur simple sur des routes qui devraient être réservées aux admins.
Cela permettrait à un étudiant de supprimer un autre étudiant, t'imagines ??? :boom:
Rassure toi, ça n'arrivera pas à Oclock! Quoique... :alien:
```php
            'student_add_get' => ['admin', 'user'],
            'student_add_post' => ['admin', 'user'],
            'student_update_get' => ['admin', 'user'],
            'student_update_get' => ['admin', 'user'],
            'student_delete' => ['admin', 'user'],
```

Aussi, dans ton ACL tu as volontairement commentée la ligne 16 :
```php
            //'main-home' => [],
```
Il est vrai que cette route, qui ne mène qu'à une page d'accueil n'a pas nécessairement besoin d'être protégée. Cependant elle indique à un utilisateur malveillant qu'il est bien tombé sur ton backoffice. :scream: 
Pourquoi ne tout simplement pas la supprimer ? :question: et pourquoi pas router directement ton utilisateur non authentifié vers une page d'authentification ? :sunglasses:

- ### Organisation du code dans une méthode 

Attention à bien effectuer les opérations dans le bon ordre, pour une méthode qui va venir ajouter ou modifier la base de données.
En l'occurence si je prends la méthode _addStudentPost_ de ton _StudentController_, tu instancies un nouvel objet Student, lui affectes des valeurs pour ses paramètres avant même que tu aies validés les données.
La bonne pratique serait de valider les données, si elles sont valides alors permettre la création de cette entité et la sauvegarde en base de données. Mais c'est du détail et ton code est déjà vraiment bien rodé.


- ### .htaccess manquant ? :hushed:

Je ne vois pas ton fichier .htaccess de réecriture d'URL. Pour rappel : .htaccess permet de réorienter toutes les requêtes vers ton index.php. 
Je t'invite à aller lire cette [fiche récap](https://kourou.oclock.io/ressources/fiche-recap/ressources-apache/#v%c3%a9rifier-que-les-htaccess-sont-interpr%c3%a9t%c3%a9s) afin de bien consolider cette notion et/ou vérifier que tu n'aies pas de problèmes de configuration de ton serveur Apache. :+1:


## Bonnes pratiques
- ### snake_case, camelCase, PascalCase, bla bla bla...

C'est plus une question de bonnes pratiques mais j'ai quand même des recommandations pour toi à ce sujet 
Dans la méthode studentUpdatePost de ton StudentController:
```php

        $teacher_id = filter_input(INPUT_POST, 'teacher');

        $studentFromDb->setTeacher_id($teacher_id);
  
```
Même si le [PSR](https://php-fig.org/psr/) n'oblige pas à utiliser le camelCase pour les variables, c'est une convention d'écriture qu'il est préférable d'utiliser et je t'invite à t'y habituer dès maintenant. :grin:

- ### Simplifizing, Factorisizing, Jaipasletempspourçazing

Une autre bonne pratique importante pour ton code est de factoriser ce qui peut l'être, bon OK c'est du bonus, mais ça en jette !
En fait, on pense à toi et plus tard ta pratique professionnelle. 
Car plus tard, que tu sois en entreprise ou en freelance, un des critères importants du code est sa ***MAINTENABILITE***. 

Regarde bien la correction et la manière dont les fichiers sont bien découpés et organisés de façon concise.
Par exemple, au lieu d'avoir toutes mes routes dans le fichier _index.php_ je passe par un require d'un fichier routes.
```php
require __DIR__ . '/../app/routes.php';
```
Désormais, dès lors que je voudrais toucher à un route de mon projet, je n'aurai pas à scroller comme un dingo sur la page index.php qui fera 3000 lignes ! :joy:

- ### Esthétique? Quoi? Non je code moi !

Oui, mais le code propre, c'est du beau code, c'est un code lisible et qui sera lisible et plus accessible quand il faudra s'y replonger. :innocent:
Prends dès maintenant le bon réflexe et commente ton code, pour t'expliquer ce que tu fais, pour expliquer aux autres qui vont le lire. 

Aussi, n'hésite pas à supprimer les retour à la ligne inutile et bien indenter ton code. Cela facilite grandement la relecture.
Il y a des extensions VSCode qui permettent d'automatiser tout ça, et comme quand on code on est fainéant, on aime l'automatisation ! :heart:

Par exemple [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) qui est beaucoup utilisé et son [tutoriel d'installation](https://www.digitalocean.com/community/tutorials/how-to-format-code-with-prettier-in-visual-studio-code-fr). 

## Pour vraiment chercher la petite bête !
- ### Appels à des assets manquants

Eh ! Mon PHP server me crie dessus ! :open_mouth: Il me réclame :
```bash
[Thu May 11 14:54:36 2023] 127.0.0.1:48908 [404]: GET /css/style.css - No such file or directory
```

C'est un appel à un fichier style.css que tu n'as pas. Tu peux supprimer cet appel, un indice c'est dans un de tes partials... :see_no_evil:

# Conclusion
***
C'est vraiment un très bon travail, continues sur cette lancée. Tu as effectué la quasi totalité des consignes avec même des bonus. Tu peux te féliciter! :relaxed:
# FEEDBACK APPRENANT 3

---

Hello ! J'ai essayé de te faire un retour pour que tu puisses te remettre de tes émotions après ce parcours de fin de saison 6 !
Tout d'abord, je voulais te dire bravo pour le travail accompli. Ce parcours est loin d'être un des plus simples et la compréhension de l'architecture MVC n'est pas donné à tout le monde du premier coup !

## Aperçu global :wink:

---

C'est un parcours difficile dans lequel tu as implémenté des fonctionnalités un peu trop rapidement. En effet, elles sont correctement codées mais des erreurs d'inattention les rendent non fonctionnelles. Néanmoins, tu sembles avoir compris le fonctionnement du Model View Controller et le routing via AltoRouter.

## Points de vigilance

- ### Home Sweet Home (ou pas...)

Attention, à peine le serveur lancé, je me retrouve sur une 404 à l'accueil, SYMPA !

```php
$router->map(
    'GET',
    '/home',
    [
        'method' => 'home',
        'controller' => MainController::class // On indique le FQCN de la classe
    ],
    'main-home'
);
```

En général, cette route home se syntaxe `'/'` et non `'/home'`.
Mais tu peux aussi avoir les deux qui dirige vers la même route !

- ### .htaccess manquant ? :hushed:

Je ne vois pas ton fichier .htaccess de réecriture d'URL. Pour rappel : .htaccess permet de réorienter toutes les requêtes vers ton index.php.
Je t'invite à aller lire cette [fiche récap](https://kourou.oclock.io/ressources/fiche-recap/ressources-apache/#v%c3%a9rifier-que-les-htaccess-sont-interpr%c3%a9t%c3%a9s) afin de bien consolider cette notion et/ou vérifier que tu n'aies pas de problèmes de configuration de ton serveur Apache. :+1:

- ### Routing or not Routing, that is the question !

Vigilance! tes routes ne sont pas correctes vis à vis de ce qui était demandé.
Un petit oeil sur ton fichier **_docs/routes.md_** pour avoir les noms exacts !
Par exemple, l'url pour afficher la liste des étudiants aurait dû être `/students` en GET et non `/students_list`

Attention aussi, une erreur s'est glissée car à partir de la liste des profs, quand je clique sur ajouter, j'ajoute un étudiant et non un prof.
Le lien généré par le router n'a sûrement pas le bon nom... :dizzy_face:

- ### Copié-Vautré

Attention également à tes copier/coller. _ON LE FAIT TOUS_ mais il faut le faire bien ! :wink:
Epic FAIL spotted:

```php
public function studentAdd() {
        global $router;
        //$router->generate(...)

        $errorList = [];
        $newTeacher = new Teacher();

        // Le formulaire a été soumis, les données sont envoyées
        if(isset($_POST) && !empty($_POST)) {

            // traitement du formulaire

            // Pour récupérer les différentes valeurs, on va définir des variables
            $firstname = filter_input(INPUT_POST, "firstname", FILTER_SANITIZE_SPECIAL_CHARS);
            $lastname = filter_input(INPUT_POST, "lastname", FILTER_SANITIZE_SPECIAL_CHARS);
            $status = filter_input(INPUT_POST, "status", FILTER_VALIDATE_INT);

                $newStudent->setFirstname($firstname);
                $newStudent->setLastname($lastname);
                $newStudent->setStatus($status);
```

Attends tu me parles d'un prof et ensuite tu me parles d'un étudiant à qui tu mets les données d'un prof ?
:open_mouth: :sweat_smile:
Allez, je te laisserai chercher tes autres erreurs.

Tu peux aussi te servir de intelephense (extension VSCode normalement préinstallée sur ta VM) qui te permettra de retrouver les erreurs dans ton terminal à l'onglet `Problems`.
Pour le code que je t'ai copié, tu as :

```bash
Undefined variable '$newStudent'.
```

- ### Header or not Header ? That is the question...

Au niveau des views, tu as choisi de ne pas faire ce qu'on appelle des **partials**.
Pour rappel, faire des partials permet de ne pas se répéter et donc est considérer comme _DRY_(Don't Repeat Yourself). C'est donc une bonne pratique.
Cela permet aussi d'éviter d'oublier des "_bouts de code_" comme par exemple une navbar.. ?
Regarde tes `student_list.tpl.php` et `teacher_list.tpl.php` il te manque la navbar, ainsi que la div permettant d'intégrer une classe bootstrap afin d'avoir un rendu plus esthétique ! :wink:

D'ailleurs tu ne l'as pas oublié pour ton formulaire d'ajout. Mais tu as oublié de mettre à jour les liens vers les bonnes routes sur ces navbar.
Factoriser ton code permet de le rendre plus **maintenable** et donc, lorsqu'une route change, on aura à modifier le code qu'à un seul endroit au lieu de plusieurs.

Je te conseille de reprendre cette partie de l'exercice avec des partials, pour le header ainsi que le footer. Je te laisserai déterminer les parties communes sur les templates fournis en intégration dans `docs/integration-html-css/`. Dans un premier temps, essaies sans la correction... :wink:

## Et si tu veux aller plus loin

### Appels à des assets manquants

Eh ! Mon PHP server me crie dessus ! :open_mouth: Il me réclame :

```bash
[Thu May 11 14:54:36 2023] 127.0.0.1:48908 [404]: GET /css/style.css - No such file or directory
```

C'est un appel à un fichier style.css que tu n'as pas. Tu peux supprimer cet appel, un indice c'est dans un de tes partials... :see_no_evil:

### Personnalisation de la 404

En te basant sur les templates `docs/integration-html-css/` tu peux personnaliser ta page 404. En effet, la route est correcte et les liens au sein de ton template aussi mais elle est un peu vide...

### Formulaire d'ajout

J'ai pu voir sur ton formulaire d'ajout (celui d'étudiant) un menu déroulant qui renvoyait des valeurs statiques de ta vue.

En effet tu aurais pu dynamiser en envoyant un tableau à ta vue via ton controller StudentController et ta méthode studentsAdd

```php
$this->show("student/student_add", [
            'errors' => $errorList,
            'student' => $newStudent
            // TODO : envoyer un tableau avec la liste des profs
        ]);
```

```html
<select name="teacher" id="teacher" class="form-control">
  <option value="0">-</option>
<!-- TODO : Dynamiser le tableau reçu depuis le controller -->
</select>
```

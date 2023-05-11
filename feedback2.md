# FEEDBACK APPRENANT 2

---

Hello ! J'ai essayé de te faire un retour pour que tu puisses te remettre de tes émotions après ce parcours de fin de saison 6 !
Tout d'abord, je voulais te dire bravo pour le travail accompli. Ce parcours est loin d'être simple et la compréhension de l'architecture MVC prend du temps et je suis certain qu'avec le temps et de la pratique les notions vont être intégrées.

## Aperçu global :wink:

---

C'est un parcours qui semble t'avoir beaucoup destabilisé. Tu as réussi quelques étapes et c'est déjà pas mal !

## Méthodes de listing
- ### Listing des élèves et des profs

Ton code est bien implémenté et fonctionnel, nous pouvons voir la liste des profs et des élèves. Bravo !

## Axes d'amélioration

- ### Les méthodes CRUD en MVC

J'ai vu que tu as essayé d'implémenter une méthode add pour ajouter un nouveau prof. (Etape 4 du parcours)
Cette étape semble t'avoir bloqué. N'hésite pas à **bien lire les consignes JUSQU'À LA FIN**. Tout est écrit ! :smile:
De plus, n'oublie pas aussi d'ajouter un bouton sur ta vue pour qu'on puisse accéder à la route :wink:
Un petit coup de pouce par là !

```html
<a href="<?= $router->generate('route-pour-ajouter-un-prof') ?>"class="btn btn-success float-right">Ajouter</a>
```

Je te conseille de relire et de bien intégrer le fonctionnement d'un MVC. Pour cela, rien de plus simple, direction les fiches récaps !
Pour le MVC c'est [ici](https://kourou.oclock.io/ressources/fiche-recap/architecture-mvc-model-view-controller/)

Enfin, afin de bien comprendre comment fonctionne le CRUD, sa relation avec la base de données et les Models :
Je te conseille de regarder le [replay](#) de l'épisode 2 de la saison 6, qui traite de la méthode insert(), ainsi que relire la [fiche récap sur les objets PHP](https://kourou.oclock.io/ressources/fiche-recap/les-objets-en-php/).

En effet, les objets PHP sont **_essentiels_** pour mieux appréhender la programmation orientée objet ou POO.

- ### Copier/Coller mais pas Copier/Vautrer

Mon second conseil serait de te baser (même si tu ne comprends pas tout :wink:) sur le repo oShop que tu as fait durant cette saison.
Tu peux copier/coller certaines méthodes en prenant garde à bien effectuer les modifications par rapport à tes Models et les paramètres liés.
La compréhension viendra par la réussite de certains objectifs.
[Lien vers oShop](#)

- ### Garder confiance !

Même si ce parcours a du être challengeant, il peut t'induire une grande remise en question. Alors ne te laisse pas submerger, reprends les notions de bases, des exercices, des challenges.
Si tu prévois de t'orienter sur le back et donc la spé Symfony, il te sera essentiel d'acquérir ces connaissances et de les maîtriser.

- ### Ressources

Je te joins ici [Un super tuto de grafikart](https://grafikart.fr/tutoriels/mvc-model-view-controller-574) qui t'aidera à appréhender la POO, le MVC et le concept de routing.

Toutefois, si tu es perdu après correction et révision, n'hésite pas à demander de l'entraide sur le canal **_#entraide_** du slack de la promo. Cela permet à certains plus expérimentés de pouvoir consolider leurs acquis et à toi de peut être mieux comprendre grâce à d'autres personnes.

Enfin, si tu es en grande difficulté pour cet aspect de la formation, tu peux venir en parler auprès de moi ou d'un formateur. Nous essayerons de trouver une solution pour pouvoir t'aider et surmonter cette difficulté.

# Conclusion

---

C'est un parcours difficile que tu as essayé de faire pour le mieux tu as réussi des étapes et c'est déjà un grand pas vers la POO, je t'invite à l'approfondir en fin de saison ou sur des moments que tu auras de libre.
N'oublie pas que chaque notion peut être dérangeante au début et puis elle se décantera avec la pratique.
Je suis persuadé que tu seras, avec quelques jours de révisions et de reprise de challenges, en mesure de réussir ce parcours!

Je compte sur toi ! :wink:

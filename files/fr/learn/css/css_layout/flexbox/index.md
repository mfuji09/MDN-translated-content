---
title: Flexbox
slug: Learn/CSS/CSS_layout/Flexbox
translation_of: Learn/CSS/CSS_layout/Flexbox
original_slug: Apprendre/CSS/CSS_layout/Flexbox
---
{{LearnSidebar}}{{PreviousMenuNext("Apprendre/CSS/CSS_layout/Normal_Flow", "Apprendre/CSS/CSS_layout/Flexbox_skills", "Learn/CSS/CSS_layout")}}

Flexbox est une méthode de mise en page selon un axe principal, permettant de disposer des éléments en ligne ou en colonne. Les éléments se dilatent ou se rétractent pour occuper l'espace disponible. Cet article en explique tous les fondamentaux.

<table class="standard-table">
  <tbody>
    <tr>
      <th scope="row">Prérequis :</th>
      <td>
        Les fondamentaux du HTML (étudiez
        <a href="/fr/Apprendre/HTML/Introduction_%C3%A0_HTML"
          >Introduction au HTML</a
        >) et avoir une idée de la manière dont la CSS fonctionne (étudiez
        <a href="/fr/Apprendre/CSS/Introduction_à_CSS">Introduction aux CSS</a
        >).
      </td>
    </tr>
    <tr>
      <th scope="row">Objectif :</th>
      <td>
        Apprendre à utiliser le système Flexbox pour créer des mises en page
        web.
      </td>
    </tr>
  </tbody>
</table>

## Pourquoi Flexbox ?

Pendant longtemps, les seuls outils de mise en page CSS fiables et compatibles avec les navigateurs, étaient les propriétés concernant les [flotteurs (boîtes flottantes)](/fr/docs/Learn/CSS/CSS_layout/Floats) et le [positionnement](/fr/docs/Learn/CSS/CSS_layout/Positioning). Ces outils sont bien et fonctionnent, mais restent à certains égards plutôt limitatifs et frustrants.

Les simples exigences de mise en page suivantes sont difficiles sinon impossibles à réaliser de manière pratique et souple avec ces outils :

- centrer verticalement un bloc de contenu dans son parent ;
- faire que tous les enfants d'un conteneur occupent tous une même quantité de hauteur/largeur disponible selon l'espace offert ;
- faire que toutes les colonnes dans une disposition multi‑colonnes aient la même hauteur même si leur quantité de contenu diffère.

Comme vous le verrez dans les paragraphes suivants, flexbox facilite considérablement les tâches de mise en page. Approfondissons un peu !

## Voici un exemple simple

Dans cet article, nous allons commenter une série d'exercices pour vous faciliter la compréhension du fonctionnement de flexbox. Pour commencer, faites une copie locale du premier fichier de démarrage — [flexbox0.html](https://github.com/mdn/learning-area/blob/master/css/css-layout/flexbox/flexbox0.html) de notre dépôt GitHub —, chargez‑le dans un navigateur moderne (comme Firefox ou Chrome) et regardez le code dans votre éditeur. Vous pouvez le [voir en direct ici](https://mdn.github.io/learning-area/css/css-layout/flexbox/flexbox0.html) aussi.

Qu'avons‑nous ? un élément {{htmlelement("header")}} avec un en‑tête de haut niveau à l'intérieur, et un élément {{htmlelement("section")}} contenant trois {{htmlelement("article")}}s. Nous allons les utiliser pour créer une disposition vraiment classique sur trois colonnes.

![Échantillon d'utilisation de flexbox](bih741v.png)

## Détermination des éléments à disposer en boîtes flexibles

Pour commencer, sélectionnons les éléments devant être présentés sous forme de boîtes flexibles. Pour ce faire, donnons une valeur spéciale à la propriété  {{cssxref("display")}} du parent de ces éléments à disposer. Dans ce cas, comme cela concerne les éléments {{htmlelement("article")}}, nous affectons la valeur `flex` à l'élément {{htmlelement("section")}} (qui devient un conteneur flex) :

```css
section {
  display: flex;
}
```

Voici le résultat :

![Échantillon d'utilisation de flexbox](flexbox-example2.png)

Ainsi, cette unique déclaration donne tout ce dont nous avons besoin — incroyable, non ? Nous avons ainsi notre disposition en plusieurs colonnes de largeur égale, et toutes de même hauteur. Ceci parce que les valeurs par défaut données aux éléments flex (les enfants du conteneur flex) sont configurés pour résoudre des problèmes courants tels celui-ci. On en reparlera plus tard.

> **Note :** Vous pouvez aussi définir une valeur `inline-flex` pour {{cssxref("display")}} si vous voulez disposer des éléments en ligne sous forme de boîtes modulables.

## Aparté sur le modèle flex

Lorsque les éléments sont disposés en boîtes flexibles, ils sont disposés le long de deux axes :

![Terminologie pour les boîtes modulables](flex_terms.png)

- L'**axe principal** **(main axis)** est l'axe de la direction dans laquelle sont disposés les éléments flex (par exemple, horizontalement sur la page, ou verticalement de haut en bas de la page). Le début et la fin de cet axe sont appelés l'**origine principale** **(main start)** et la **fin principale (main end)**.
- L'**axe croisé** est l'axe perpendiculaire à l'axe principal, c'est-à-dire à la direction dans laquelle sont disposés les éléments flex. Le début et la fin de cet axe sont appelés le début (**cross start**) et la fin (**cross end**) de l'axe croisé.
- L'élément parent dont la propriété est `display: flex` ({{htmlelement("section")}} dans notre exemple) est appelé le **conteneur flex** (**flex container**).
- Les éléments disposés en tant que boîtes flexibles à l'intérieur du conteneur flex sont appelés **éléments flex (flex items)** (les éléments {{htmlelement("article")}}} dans notre exemple).

Gardez cette terminologie en tête en lisant les paragraphes suivants. Vous pouvez toujours vous y référer si vous avez un doute sur la signification des termes utilisés.

## Colonnes ou lignes ?

Flexbox dispose de la propriété {{cssxref("flex-direction")}} pour indiquer la direction de l'axe principal (direction dans laquelle les enfants flexibles sont disposés) — cette propriété est égale par défaut à `row` : ils sont donc disposés en ligne, dans le sens de lecture de la langue par défaut du navigateur (de gauche à droite, dans le cas d'un navigateur français).

Ajoutons la déclaration suivante dans la règle :

```css
flex-direction: column;
```

Cela dispose de nouveau les éléments en colonnes, comme c'était le cas avant l'ajout de la CSS. Avant de poursuivre, enlevez cette déclaration de l'exemple.

> **Note :** Vous pouvez aussi disposer les éléments flex dans la direction inverse avec les valeurs `row-reverse` et `column-reverse`. Expérimentez ces valeurs aussi !

## Enveloppement

Problème : quand votre structure est de largeur ou hauteur fixe, il arrive que les éléments flex débordent du conteneur et brisent cette structure. Voyez l'exemple [flexbox-wrap0.html](https://github.com/mdn/learning-area/blob/master/css/css-layout/flexbox/flexbox-wrap0.html), essayez [directement](https://mdn.github.io/learning-area/css/css-layout/flexbox/flexbox-wrap0.html) (faites une copie locale de ce fichier maintenant si vous voulez suivre cet exemple) :

![Débordement des éléments modulables](flexbox-example3.png)

Ici, nous voyons que les enfants débordent du conteneur. Une façon d'y remédier est d'ajouter la déclaration suivante à votre règle pour `section` :

```css
flex-wrap: wrap;
```

Essayons ; la disposition est bien meilleure avec cet ajout :

![Conditionnement des éléments modulables](flexbox-example4.png)Nous avons maintenant plusieurs lignes — un nombre sensé d'enfants flexibles est placé sur chaque ligne, et le débordement est déplacé vers le bas sur une ligne supplémentaire. La déclaration `flex: 200px` pour les éléments `article` signifie que chacun aura au moins 200px de large ; nous discuterons de cette propriété plus en détail plus tard. Vous noterez aussi que chacun des enfants de la dernière rangée est plus large, de façon à ce que toute la rangée reste remplie.

Mais nous pouvons faire plus ici. Tout d'abord, essayez de changer la valeur de la propriété {{cssxref("flex-direction")}} en `row-reverse` — maintenant vous avez toujours la disposition sur plusieurs lignes, mais elles commencent dans l'angle opposé de la fenêtre du navigateur et se disposent à l'envers.

## Forme abrégée « flex-flow »

Notez maintenant qu'il y a une forme abrégée pour {{cssxref("flex-direction")}} et {{cssxref("flex-wrap")}} — {{cssxref("flex-flow")}}. Ainsi, par exemple, vous pouvez remplacer

```css
flex-direction: row;
flex-wrap: wrap;
```

par

```css
flex-flow: row wrap;
```

## Taille modulable des éléments flex

Revenons maintenant au premier exemple, et examinons comment nous pouvons contrôler la proportion d'éléments flexibles dans l'espace. Lancez votre copie locale de [flexbox0.html](https://github.com/mdn/learning-area/blob/master/css/css-layout/flexbox/flexbox0.html) ou prenez une copie de [flexbox1.html](https://github.com/mdn/learning-area/blob/master/css/css-layout/flexbox/flexbox1.html) comme nouveau point de départ ([voir en direct](https://mdn.github.io/learning-area/css/css-layout/flexbox/flexbox1.html)).

Ajoutez d'abord la règle ci-dessous en fin de la CSS :

```css
article {
  flex: 1;
}
```

Il s'agit d'une valeur de proportion, sans unité, définissant la quantité d'espace disponible que chaque élément flex prendra le long de l'axe principal. Dans ce cas, nous donnons à chaque élément {{htmlelement("article")}}} une valeur de 1, ce qui signifie qu'ils prendront tous une portion égale de l'espace libre après le calcul du remplissage et de la marge. Cette valeur représente une proportion, c'est-à-dire que le fait de donner une valeur de 400 000 simultanément à tous les éléments flex aurait exactement le même effet.

Maintenant ajoutons cette règle en-dessous de la précédente :

```css
article:nth-of-type(3) {
  flex: 2;
}
```

Maintenant, lorsque vous actualisez, vous voyez que le troisième {{htmlelement("article")}} occupe deux fois plus de largeur disponible que chacun des deux autres — il y a maintenant quatre unités de division disponibles au total. Les deux premiers éléments flexibles en occupent chacun un, soit 1/4 de l'espace disponible pour chacun. Le troisième remplit deux unités, soit 2/4 (la moitié) de l'espace disponible.

Vous pouvez également définir une valeur minimale de taille dans la valeur `flex`. Modifiez comme suit vos règles `article` existantes :

```css
article {
  flex: 1 200px;
}

article:nth-of-type(3) {
  flex: 2 200px;
}
```

En gros, cela dit : « Chaque élément flex reçoit d'abord 200px de l'espace disponible quand c'est possible. Ensuite, le reste de l'espace disponible est réparti selon les unités de proportion ». Note : _quand ce n'est pas possible, ce sont les unités de proportions qui sont prises en compte._

Actualisez et vous devriez voir une différence dans la façon dont l'espace est réparti.

![Modulation de la largeur](flexbox-example1.png)

Le véritable intérêt de flexbox apparaît dans sa souplesse et sa réactivité — si vous redimensionnez la fenêtre du navigateur ou ajoutez un autre élément {{htmlelement("article")}}}, la mise en page continue de fonctionner correctement.

## Flex : forme abrégée vs forme longue

{{cssxref("flex")}} est une forme abrégée de propriété qui peut servir à définir trois valeurs différentes :

- une valeur de proportion sans unité, vue ci‑dessus. Elle peut être précisée seule avec la forme longue de la propriété {{cssxref("flex-grow")}} ;
- une deuxième valeur de proportion sans unité — {{cssxref("flex-shrink")}} — intervenant quand les éléments flex débordent du conteneur. Elle indique la quantité de dépassement à retirer de l'extension de chacun des éléments flex pour les empêcher de déborder du conteneur. Il s'agit d'une fonctionnalité avancée de flexbox, et nous n'en parlerons plus dans cet article ;
- une valeur de taille minimale, vue ci‑dessus. Elle peut aussi être précisée seule avec la forme longue de la propriété {{cssxref("flex-basis")}}.

Nous vous déconseillons d'utiliser les propriétés flex sous leur forme longue, sans autre alternative possible (par exemple, pour annuler quelque chose déjà défini). Elles représentent du code supplémentaire, et peuvent être quelque peu déroutantes.

## Alignement horizontal et vertical

Vous pouvez également utiliser les fonctionnalités de flexbox pour aligner les éléments flex le long de l'axe principal ou croisé. Voyons cela avec un nouvel exemple — [flex-align0.html](https://github.com/mdn/learning-area/blob/master/css/css-layout/flexbox/flex-align0.html) ([voir aussi en direct](https://mdn.github.io/learning-area/css/css-layout/flexbox/flex-align0.html)). Nous allons le transformer facilement en une barre souple de boutons. Actuellement, nous avons une barre de menu horizontale avec quelques boutons tassés dans l'angle supérieur gauche.

![Alignement](flexbox-example5.png)

D'abord, faites une copie locale de cet exemple.

Ensuite, ajoutez ce qui suit à la fin de la CSS de l'exemple :

```css
div {
  display: flex;
  align-items: center;
  justify-content: space-around;
}
```

![](flexbox_center_space-around.png)

Actualisez la page et vous verrez que les boutons sont maintenant bien centrés, horizontalement et verticalement. Cette transformation a été opérée grâce à deux nouvelles propriétés.

{{cssxref("align-items")}} fixe là où les éléments flex sont placés sur l'axe perpendiculaire, dit aussi croisé (cross axis).

- Par défaut, la valeur est `stretch`, qui étire tous les éléments flex de manière à emplir le conteneur parent le long de l'axe croisé. Si le parent ne possède pas de dimension définie dans la direction de l'axe croisé, alors tous les éléments flex auront la dimension du plus étiré des éléments. C'est pour cette raison que, dans notre premier exemple, les colonnes ont toutes la même hauteur par défaut.
- Avec la valeur `center`, utilisée dans le code ci-dessus, les éléments gardent leur dimension intrinsèque, tout en étant centrés sur l'axe croisé. C'est la raison pour laquelle, dans l'exemple actuel, les boutons sont centrés verticalement.
- Il y a également des valeurs comme `flex-start` et `flex-end` qui alignent respectivement tous les éléments au début ou à la fin de l'axe croisé. Voyez {{cssxref("align-items")}} pour tous les détails.

Vous pouvez prendre le pas sur le comportement de {{cssxref("align-items")}} pour un élément flex donné en lui appliquant la propriété {{cssxref("align-self")}}. Par exemple, ajoutez ce qui suit aux CSS:

```css
button:first-child {
  align-self: flex-end;
}
```

![](flexbox_first-child_flex-end.png)

Voyez l'effet obtenu, puis supprimez ensuite la règle.

{{cssxref("justify-content")}} fixe où les éléments flex sont placés sur l'axe principal.

- La valeur par défaut est `flex-start`. Tous les éléments sont disposés vers l'origine de l'axe principal.
- Vous utiliserez  `flex-end` pour les disposer vers la fin.
- `center` est aussi une valeur possible pour `justify-content`. Avec elle, les éléments flex sont placés vers le centre de l'axe principal.
- La valeur `space-around`, utilisée plus haut, est pratique — elle distribue régulièrement tous les éléments le long de l'axe principal, en laissant autant d'espace à chaque extrémité qu'entre chacun.
- Une autre valeur, `space-between`, est semblable à `space-around` mais elle ne laisse pas d'espace aux extrémités.

N'hésitez pas à jouer avec ces valeurs pour visualiser leur fonctionnement avant de poursuivre.

## Ordonner les éléments flex

Flexbox dispose aussi d'une fonctionnalité pour modifier l'ordre d'affichage des éléments flex, sans en modifier l'ordre dans la source. C'est une chose impossible à réaliser avec les méthodes classiques de mise en page.

Le code pour ce faire est simple : ajoutez la règle CSS suivante dans l'exemple de code de la barre de boutons :

```css
button:first-child {
  order: 1;
}
```

Actualisez, et vous pouvez voir que le bouton « Smile » a été déplacé en fin de l'axe principal. Voyons en détail comment cela fonctionne :

- par défaut, tous les éléments flex possèdent une valeur {{cssxref("order")}} égale à 0 ;
- les éléments flex avec des valeurs `order` plus élévées apparaîtront plus tard dans l'ordre d'affichage que ceux avec des valeurs plus faibles ;
- les éléments flex avec les mêmes valeurs pour `order` sont affichés dans l'ordre de la source. Ainsi, si vous avez 4 éléments avec des valeurs `order` de 2, 1, 1 et 0, leur ordre d'affichage sera 4e, 2e, 3e et premier.
- Le troisième élément suit le deuxième, car il a la même valeur pour `order` et qu'il est placé après dans le code source.

Vous pouvez donner des valeurs négatives à `order` pour faire en sorte que ces éléments soient affichés avant les éléments d'ordre 0. Par exemple, vous pouvez faire apparaître le bouton « Blush » en tête de l'axe principal avec la règle suivante :

```css
button:last-child {
  order: -1;
}
```

## Boîtes flex imbriquées

Il est possible de créer des mises en page joliment complexes avec flexbox. Il est parfaitement loisible de déclarer un élément flex en tant que conteneur flex, de sorte que ses enfants sont également disposés en tant que boîtes modulables. Regardez [complex-flexbox.html](https://github.com/mdn/learning-area/blob/master/css/css-layout/flexbox/complex-flexbox.html) ([à voir en direct également](https://mdn.github.io/learning-area/css/css-layout/flexbox/complex-flexbox.html)).

![Imbrications avec flexbox](flexbox-example7.png)

Le HTML pour cela est vraiment simple. Voici un élément {{htmlelement("section")}} contenant trois éléments {{htmlelement("article")}}. Le troisième élément {{htmlelement("article")}} contient trois éléments {{htmlelement("div")}}. Le premier élément {{htmlelement("div")}} contient cinq éléments {{htmlelement("button")}}  :

    section - article
              article
              article - div - button
                        div   button
                        div   button
                              button
                              button

Regardez le code utilisé pour cette disposition.

Primo, nous déterminons que les enfants de l'élément {{htmlelement("section")}} seront des boîtes flexibles.

```css
section {
  display: flex;
}
```

Secundo, nous définissons des valeurs flex pour les éléments {{htmlelement("article")}} eux‑mêmes. Remarquez en particulier ici la deuxième règle — nous paramétrons le troisième élément {{htmlelement("article")}} pour que ses enfants soient eux-mêmes disposés en tant qu'éléments flex, mais cette fois‑ci en colonne.

```css
article {
  flex: 1 200px;
}

article:nth-of-type(3) {
  flex: 3 200px;
  display: flex;
  flex-flow: column;
}
```

Tertio, nous sélectionnons le premier élément {{htmlelement("div")}} et lui assignons la valeur `flex:1 100px;` pour qu'il ait effectivement une hauteur minimale de 100px, ensuite nous indiquons que ses enfants (les éléments {{htmlelement("button")}}) doivent être disposés en tant qu'éléments flex dans une ligne enveloppante, centrés dans l'espace disponible comme dans l'exemple des boutons vu plus haut.

```css
article:nth-of-type(3) div:first-child {
  flex:1 100px;
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  justify-content: space-around;
}
```

Enfin, nous définissons un dimensionnement des boutons, et plus précisément nous leur donnons une valeur flex de 1. L'effet obtenu est très intéressant ; vous l'observerez en modifiant la largeur de la fenêtre du navigateur. Les boutons prennent autant d'espace qu'il leur est permis, et sont si possible disposés sur la même ligne ; mais si ce n'est pas possible, ils "descendent" pour créer de nouvelles lignes.

```css
button {
  flex: 1;
  margin: 5px;
  font-size: 18px;
  line-height: 1.5;
}
```

## Compatibilité des navigateurs

La prise en charge de Flexbox est disponible avec la plupart des  navigateurs récents — Firefox, Chrome, Opera, Microsoft Edge et IE 11, les nouvelles versions d'Android/iOS, etc. Mais vous devez être attentif au fait que l'on utilise encore des navigateurs anciens qui ne prennent pas en charge Flexbox (ou le font, mais uniquement pour des versions très anciennes, vraiment dépassées de la spécification).

Pour l'apprentissage et l'expérimentation, cela n'a pas trop d'importance. Mais utiliser flexbox pour un site web réel nécessite de faire des tests et de s'assurer que l'expérience utilisateur est toujours acceptable dans le plus grand nombre de navigateurs possible.

Flexbox est une fonctionnalité plus complexe que les règles CSS courantes. Par exemple, une absence de prise en charge des ombres portées dans les CSS laissera le site utilisable. Mais la non prise en charge des fonctionnalités flexbox risque de casser totalement la mise en page, et de rendre le site inutilisable.

Les stratégies pour contourner les problèmes de compatibilité des navigateurs est discutée dans le module [Tests croisés sur navigateurs](/fr/docs/Learn/Tools_and_testing/Cross_browser_testing).

## Résumé

Notre visite guidée des bases de flexbox est maintenant terminée. Espérons que vous en êtes satisfaits, et que vous saurez jouer avec ses fonctionnalités tout en progressant dans l'apprentissage. Nous allons examiner ensuite un autre aspect important de la mise en page avec les CSS — les grilles CSS.

{{PreviousMenuNext("Apprendre/CSS/CSS_layout/Normal_Flow", "Apprendre/CSS/CSS_layout/Flexbox_skills", "Learn/CSS/CSS_layout")}}

## Dans ce module

- [Introduction to CSS layout](/fr/docs/Learn/CSS/CSS_layout/Introduction)
- [Normal Flow](/fr/docs/Learn/CSS/CSS_layout/Normal_Flow)
- [Flexbox](/fr/docs/Learn/CSS/CSS_layout/Flexbox)
- [Grid](/fr/docs/Learn/CSS/CSS_layout/Grids)
- [Floats](/fr/docs/Learn/CSS/CSS_layout/Floats)
- [Positioning](/fr/docs/Learn/CSS/CSS_layout/Positioning)
- [Multiple-column Layout](/fr/docs/Learn/CSS/CSS_layout/Multiple-column_Layout)
- [Legacy Layout Methods](/fr/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods)
- [Supporting older browsers](/fr/docs/Learn/CSS/CSS_layout/Supporting_Older_Browsers)
- [Fundamental Layout Comprehension Assessment](/fr/docs/Learn/CSS/CSS_layout/Fundamental_Layout_Comprehension)

# S1-TP1 — Refactorer le kata Gilded Rose

Module BC03-FM06 — Analyse de qualité et pratiques de Clean Code | Séance 1 | ORT 4OLEN — 2026-2027

Ce dossier contient le code de départ du TP `S1-TP1`. Le sujet complet est dans le document **S1-TP1 — Sujet étudiant**.

## Contenu

| Élément | Rôle |
|---|---|
| `GildedRose-Refactoring-Kata/<langage>/` | Le code legacy dans votre langage, avec un test de départ et la *fixture* (`texttest_fixture`) |
| `GildedRose-Refactoring-Kata/<langage>/README.md` | Les commandes pour lancer les tests dans ce langage |
| `GildedRose-Refactoring-Kata/GildedRoseRequirements_fr.md` | La spécification, en français |
| `GildedRose-Refactoring-Kata/texttests/` | Outillage *golden master* (TextTest), facultatif |

## Mise en place (5 min, au début de la partie 1)

1. Décompressez l'archive.
2. Copiez le dossier de **votre langage** à l'endroit où vous travaillez, avec la spécification :

   ```bash
   mkdir gilded-rose && cd gilded-rose
   cp -r <chemin>/GildedRose-Refactoring-Kata/<langage>/. .
   cp <chemin>/GildedRose-Refactoring-Kata/GildedRoseRequirements_fr.md .
   ```

3. Initialisez un dépôt Git et enregistrez le code de départ **sans le modifier** :

   ```bash
   git init -b main
   git add .
   git commit -m "chore: code de départ du kata Gilded Rose"
   ```

4. Créez un dépôt **vide** sur GitHub ou GitLab (sans README), puis poussez :

   ```bash
   git remote add origin <url-de-votre-depot>
   git push -u origin main
   ```

5. Créez votre branche de travail :

   ```bash
   git switch -c refactor/gilded-rose
   ```

6. Lancez le test de départ (voir le `README.md` de votre langage). **Il doit échouer** : c'est voulu.

Exemple en PHP (PHP 8.0 ou plus et [Composer](https://getcomposer.org) requis) :

```bash
composer install
composer tests                              # lance PHPUnit
php fixtures/texttest_fixture.php 30        # affiche l'inventaire sur 30 jours
```

En PHP, **trois tests échouent** au départ, et c'est normal :

- `GildedRoseTest::testFoo` attend `"fixme"` : corrigez-le en premier ;
- les deux tests de `ApprovalTest` (bibliothèque ApprovalTests) n'ont pas encore de référence. `testThirtyDays` est un *golden master* tout prêt : **sur le code d'origine, avant tout refactoring**, renommez le fichier `.received.txt` qu'il produit en `.approved.txt`, puis relancez les tests. `testFoo` peut être supprimé.

Bonus PHP, utile pour la séance 2 : `composer phpstan` (analyse statique) et `composer check-cs` (respect du standard PSR-12).

## Rappel des contraintes

- Ne modifiez **ni la classe `Item` ni la propriété `items`**.
- Le comportement doit rester **strictement identique**.
- N'implémentez **pas** « Conjured » dans la PR de refactoring.
- **Pas de refactoring sans tests au vert.**

## Le binôme relecteur

En partie 3, ajoutez le binôme qui vous relira comme collaborateur de votre dépôt (GitHub : *Settings → Collaborators* ; GitLab : *Manage → Members*), pour qu'il puisse commenter votre PR pendant `S1-TD1`.

## Licence

Kata Gilded Rose © Emily Bache, sous licence MIT (voir `GildedRose-Refactoring-Kata/license.txt`).
Source : https://github.com/emilybache/GildedRose-Refactoring-Kata — version du 21/08/2026 (commit `d640790`).

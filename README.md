# Tutoriel sur Git

Comment utiliser les bases de Git ?

## Qu'est-ce que Git ?
Git est un logiciel qui permet de stocker plusieurs versions d'un même contenu.

## Avant tout
Vous devez installer [Git](http://git-scm.com/download).

Pour ce tutoriel, nous allons travailler avec l'arborescence suivante :

```sh
my_dir/file_1
my_dir/file_2
my_dir/dir_1/file_3
my_dir/dir_1/file_4
```

## Commençons
Dans le répertoire que vous souhaitez versionner, il suffit de faire :

```sh
git init
```

## Fonctionnement
Pour utiliser Git, il faut comprendre les bases.

Vos fichiers peuvent être dans plusieurs états :
* modified (modifiés)
* staged (présenté/mis en scène)
* commit (enregistré)

**Modified** : Le fichier est modifié.
**Staged** : Le fichier est marqué en préparation du commit.
**Commit** : Le lot de fichiers mis en staging est enregistré dans Git.

Pour mettre un fichier en état **staged** :
```sh
git add your_file
```

Pour **commit** les fichiers :
```sh
git commit -m "Votre message indiquant les modifications effectuées."
```

## Dans la pratique
### Contexte
On fait un lot de modifications associés au projet **P001**.

On modifie *my_dir/file_1*
```sh
Mes modifications numéro 1
```

Puis *my_dir/dir_1/file_3*
```sh
  Un autre lot de modifications
```

Puis des modifications pour le projet **P002**.

On modifie *my_dir/file_2*
```sh
  Modifications pour le projet P002
```

Puis *my_dir/dir_1/file_4*
```sh
Encore d'autres modifications
```

### On affiche les fichiers modifiés
```sh
git status
```

### On enregistre le tout

```sh
# On enregistre les modifications pour le projet P001
git add file_1 dir_1/file_3
git commit -m "Modification P001"

# On enregistre les modifications pour le projet P002
git add file_2 dir_1/file_4
git commit -m "Modification P0012"
```

## Les différentes versions
L'intérêt d'avoir les versions, c'est de pouvoir se balader dans les versions

### Lister les versions.

```sh
git log

# Ou l'affichage propre sur une ligne
git log --pretty=oneline
```

Avec la seconde ligne on obtient
```sh
2be08f9bcf6637696a5ad4d107e79ddb6cabeda8 Modification P002
a685c9cea3c8ed6a4766998ae68e9afc70a57633 Modification P001
```

Le bloque de chiffres et lettres correspond au *hash* identifiant. Il est unique.
Et à droite, on voit le message des modifications. Les premiers caractères suffisent à l'identifier.

### Afficher les différences entre deux versions
```sh
git diff <VERSION_1>..<VERSION_2>

# Exemple
git diff 2be08f..a685c9
```

Ca vous liste les différences entre ces deux versions.

### Pour revenir à une version précédente
```sh
git reset --hard <VERSION>
```

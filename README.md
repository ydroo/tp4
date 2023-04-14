**Nom :** Maxime Lemoine

**Groupe :** B

**Année :** 2023

**IUT Le Havre - Cours GIT**

---

# Compte-rendu TP4 - Conflits dans GIT
[tp4](https://abderzah.github.io/Introduction-GIT/tp4/)

L'objectif est de savoir comment résoudre des conflits.

## Situations
- lorsqu'il y a des modifications sur le même fichier localement
- modifications sur la même ligne
- pas de synchronisation

## Conséquences
- `git push`
```
From github.com:<utilisateur>/test-conflict
   1094a44..dcb1032  main       -> origin/main
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

- `git pull`
```
error: Pulling is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.
```

## Résoudre
1. déterminer le conflit : `git diff --cc <fichier>`
	- `<<<<<<< HEAD` : indique la ligne locale
	- `=======`      : indique la séparation
	- `>>>>>>`       : indique la ligne distante

2. éditer le fichier
3. remplacer ce qu'il y a entre `<<<<<<<` HEAD' et `>>>>>>` par la version corrigée de la ligne
4. enregistrer le fichier
5. mettre à jour le référenciel local et distant
	- `git status`
	- `git add README.md`
	- `git commit -m "Conflit <fichier> résolu"`
	- `git push`

* * *

## Copie de référenciel et pull request

### Copie référenciel
1. accèder au référenciel github (lien)
2. copier : `fork` > `create new fork` > `create fork`
3. possibilité de copier en local avec `clone`

### Création branche thématique
*depuis le répertoire*
1. créer une branche : `git checkout -b <branche>`
2. vérifier : `git branch`
3. synchroniser local -> distant : `git push origin <branche>` 

### Modifications sur la branche
> obtenir le hash d'une chaine : echo "<chaine>" | shasum
1. faire des modifs
2. synchroniser localement (git status, git add, git commit)
3. synchroniser en distant (git push)

### Proposer des modifications à un utilisateur (pull request)
*Après les étapes précédentes, une option apparait sur github*

1. initier : `compare & pull request`
2. compléter pull request
	- base : `main:<destinataire>`
	- compare : `<branche>`
	- ajouter des commentaires
3. cliquer sur `create pull request`

### Accepter une pull request
1. `github` > `pull resquest`
	- analyer la demander : *conversation*, *commits*, *files changed*
	- accepter : `merge pull request`




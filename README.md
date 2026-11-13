# VMproject

Projet Java (Maven) : créer **notre propre langage assembleur** et **notre propre machine virtuelle**.

## Le principe

1. L'**assembleur** lit un fichier texte (`.asm`) et le traduit en nombres.
2. La **machine virtuelle (VM)** lit ces nombres et les exécute.

```
programme.asm  -->  [Assembleur]  -->  nombres  -->  [VM]  -->  résultat
```

La VM fonctionne avec une **pile** (comme une pile d'assiettes) : `PUSH 5`, `PUSH 7`, `ADD` donne 12.

## Lancer le projet

```
mvn compile
java -cp target/classes VMproject.Main programs/countdown.asm
```

## Les tâches

| Personne | Fichiers | Tâche |
|---|---|---|
| **1** | `pom.xml`, `Main.java`, `Opcode.java`, `SPEC.md` | Chef de projet : prépare le dépôt Git, écrit la liste des instructions, relie l'assembleur et la VM, vérifie que tout marche ensemble. |
| **2** | `VM.java` | Écrit la boucle de la VM et les instructions `PUSH`, `POP`, `ADD`, `SUB`, `MUL`, `DUP`, `PRINT`, `HALT`. |
| **3** | `Stack.java` | Écrit la pile (`push`, `pop`, `peek`) avec les erreurs si elle est pleine ou vide. Puis écrit les instructions `JMP`, `JZ`, `JNZ`, `CALL`, `RET` et les donne à la personne 2. |
| **4** | `LabelScanner.java` | Assembleur, partie 1 : nettoie le texte (commentaires, lignes vides) et trouve la position de chaque label. |
| **5** | `Assembler.java` | Assembleur, partie 2 : transforme chaque ligne en nombres, avec des messages d'erreur clairs. |
| **6** | `Debugger.java`, `BinaryFile.java` | Mode débogage (affiche la pile à chaque étape), sauvegarde et chargement du bytecode, limite de pas contre les boucles infinies. Écrit aussi `LOAD` et `STORE` et les donne à la personne 2. |
| **7** | `programs/`, `src/test/`, `README.md` | Écrit des programmes en assembleur (compte à rebours, somme, factorielle...), écrit les tests, et signale les bugs au bon responsable. |

## Installer le projet sur son PC

1. Installer **JDK**, **Maven** et **Git**.

2. Ouvrir un terminal et taper :
   ```
   git clone https://github.com/imranebiar-jpg/VMproject.git
   cd VMproject
   mvn compile
   ```
3. Si **BUILD SUCCESS** s'affiche, c'est bon. Ouvrir le dossier `VMproject` dans VS Code.

## Chaque jour

```
git pull
```
Travailler sur **ses propres fichiers** seulement, puis :
```
git add .
git commit -m "ce que j'ai fait"
git pull
git push
```
## Règles de l'équipe

1. `git pull` avant de commencer.
2. Modifier **uniquement ses propres fichiers**.
3. `mvn compile` pour vérifier que tout compile.
4. `git add .`, puis `git commit -m "description"`, puis `git pull`, puis `git push`.
5. Ne jamais changer un numéro d'instruction sans prévenir toute l'équipe (voir `SPEC.md`).

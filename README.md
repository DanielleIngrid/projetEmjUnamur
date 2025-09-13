# projetEmjUnamur



\# 🐹 EMJ – Emoji MicroJava DSL



\*\*EMJ\*\* est un \*\*langage spécifique (DSL)\*\* conçu pour programmer des \*\*robots éducatifs\*\* (par ex. Cutebot) en utilisant une \*\*syntaxe à base d’émojis\*\* 🎉.  

Il compile des fichiers `.emj` et `.map` vers du \*\*code MicroPython exécutable\*\* sur microcontrôleurs.



---



\## 🚀 Objectif du projet



\- Permettre de contrôler un robot éducatif avec des \*\*instructions visuelles\*\* (émojis).  

\- Fournir une \*\*infrastructure de compilation\*\* complète :

&nbsp; - Analyse lexicale et syntaxique (\*\*ANTLR4\*\*)

&nbsp; - Vérifications sémantiques (table des symboles, portée, types)

&nbsp; - Génération de code MicroPython

&nbsp; - Gestion des erreurs conviviale

&nbsp; - Tests automatisés (JUnit)



---



\## 🛠️ Stack technique



\- \*\*Java 17\*\*  

\- \*\*Maven\*\* (build \& dépendances)  

\- \*\*ANTLR4\*\* (génération du lexer/parser)  

\- \*\*JUnit 5\*\* (tests unitaires et d’intégration)  

\- \*\*Log4j2\*\* (logging)  



---



\## 📂 Structure du projet



```

emj/

├─ pom.xml                  # Config Maven

├─ src/

│  ├─ main/

│  │  ├─ antlr4/            # Grammaire ANTLR (EMJ.g4)

│  │  ├─ java/be/unamur/... # Code du compilateur

│  │  │   ├─ emj/           # Visiteurs, générateurs de code

│  │  │   ├─ main/          # Main + gestion erreurs + symbol table

│  │  │   └─ exception/     # Exceptions custom

│  │  └─ resources/         # Config (log4j2.xml, messages)

│  └─ test/

│      └─ java/be/unamur/...# Tests unitaires et d’intégration

├─ cubot\_movements.map      # Exemple de programme EMJ

├─ test.map                 # Exemple de map

└─ README.md                # Ce fichier

```



---



\## 🔎 Fonctionnement



1\. \*\*Écriture d’un programme EMJ\*\*  

&nbsp;  Exemple (`test.map`) :

&nbsp;  ```emj

&nbsp;  😀➡️➡️⬅️⬆️⬇️

&nbsp;  ```



&nbsp;  Ici, les émojis représentent des \*\*mouvements du robot\*\*.



2\. \*\*Compilation\*\*  

&nbsp;  ```bash

&nbsp;  mvn clean install

&nbsp;  java -jar target/emj-compiler.jar test.map

&nbsp;  ```



3\. \*\*Sortie MicroPython\*\*  

&nbsp;  Le compilateur génère du code MicroPython, ex. :

&nbsp;  ```python

&nbsp;  robot.forward()

&nbsp;  robot.left()

&nbsp;  robot.up()

&nbsp;  ```



---



\## ✅ Fonctionnalités



\- \*\*Analyse syntaxique\*\* : grammaire ANTLR complète pour la syntaxe EMJ.  

\- \*\*Analyse sémantique\*\* :  

&nbsp; - Déclarations \& portées (`SymbolTable`)  

&nbsp; - Vérification de types  

&nbsp; - Fonctions \& variables (`FunctionSymbol`, `VariableSymbol`)  

\- \*\*Génération de code\*\* : visiteur dédié (`EMJCodeGeneratorVisitor`).  

\- \*\*Gestion des erreurs\*\* :  

&nbsp; - Logs détaillés (`EMJErrorLogger`)  

&nbsp; - Exceptions custom (`EMJErrorException`, `ParsingException`, etc.)  

\- \*\*Tests unitaires\*\* : couverture sur déclarations, expressions, instructions, fonctions, code Cutebot.  



---



\## 🧪 Exécution des tests



```bash

mvn test

```



Les tests valident :

\- la grammaire ANTLR (parsing correct/erreurs attendues)  

\- la sémantique (déclarations, fonctions, instructions, expressions)  

\- la génération MicroPython (via fichiers `.map` de démo)  



---



\## 📸 Exemple d’utilisation pédagogique



\- Le compilateur traduit en \*\*MicroPython\*\*.  

\- Le code s’exécute sur un robot (ex. \*\*Cutebot\*\*) via un microcontrôleur compatible.  



---



\## 👤 Auteur



\*\*Ingrid Goudji\*\*  

\- 📧 \[dgoudji@yahoo.fr](mailto:dgoudji@yahoo.fr)  

\- 💼 \[LinkedIn](https://linkedin.com/in/ingrid-goudji-a9465aa5)  

\- 🐙 \[GitHub](https://github.com/DanielleIngrid)  



---



\## 📄 Licence / usage



Projet académique présenté dans un \*\*portfolio\*\*.  

Le code complet est conservé en privé, mais peut être partagé \*\*en entretien\*\*.




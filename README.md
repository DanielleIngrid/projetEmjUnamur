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

&nbsp;



\### Test pour une map

!\[map](screens/test\_map.jpg)





&nbsp; Traduction en Python:



\# Métadonnées

title = "📢 Carte de jeu"

description = "📢 Exemple de fichier pour un plateau de jeu"



\# Carte : 2 x 4, orientation = LEFT

rows = 2

cols = 4

orientation = "⬅️"  # gauche



\# Plateau de jeu (grille)

grid =  \[

&nbsp;   \["🦹", "🚔", "🚜", "🛣️"],

&nbsp;   \["🌋", "🏘️", "🚧", "🌊"]

]



\# Affichage

print(title)

print(description)

print(f"Dimensions: {rows} x {cols}")

print(f"Orientation: {orientation}")

print("\\nPlateau :")

for row in game\_map:

&nbsp;   print(" ".join(row))







Traduction en java

public class  {

&nbsp;   public static void main(String\[] args) {

&nbsp;       // Métadonnées

&nbsp;       String title = "📢 Carte de jeu";

&nbsp;       String description = "📢 Exemple de fichier pour un plateau de jeu";



&nbsp;       // "🗺️ with 2, 4, ⬅️;"

&nbsp;       int rows = 2, cols = 4;

&nbsp;       String orientation = "⬅️";



&nbsp;       // Grille 2x4 exactement comme ton fichier

&nbsp;       String\[]\[] map = {

&nbsp;           {"🦹", "🚔", "🚜", "🛣️"},

&nbsp;           {"🌋", "🏘️", "🚧", "🌊"}

&nbsp;       };



&nbsp;       // Affichage

&nbsp;       System.out.println(title);

&nbsp;       System.out.println(description);

&nbsp;       System.out.println("Dimensions: " + rows + " x " + cols);

&nbsp;       System.out.println("Orientation: " + orientation);

&nbsp;       System.out.println("\\nPlateau :");

&nbsp;       for (int i = 0; i < rows; i++) {

&nbsp;           for (int j = 0; j < cols; j++) {

&nbsp;               System.out.print(map\[i]\[j] + " ");

&nbsp;           }

&nbsp;           System.out.println();

&nbsp;       }

&nbsp;   }

}





test de fonction

\### Test pour une fonction

!\[fonction](screens/test\_fonction.jpg)



traduction en python



def var\_bowl(var\_0, var\_1):

&nbsp;   return var\_0 + var\_1





def main():

&nbsp;   var\_0 = 10         # \[🐕]

&nbsp;   var\_1 = 7          # \[🐎]

&nbsp;   var\_2 = var\_bowl(2, 5)       # \[🐶] = \[🥣](2,5)

&nbsp;   var\_3 = var\_bowl(var\_0, var\_1)  # \[🌐] = \[🥣](\[🐕],\[🐎])



&nbsp;   return main   # ↩️ 🌀     # ou bien : return var\_3 



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




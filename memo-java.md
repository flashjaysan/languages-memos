# Mémo Java

*par flashjaysan*

## Documentation

La documentation [Java SE](http://docs.oracle.com/javase)

La documentation [Java EE](http://docs.oracle.com/javaee)

## Installation

Si vous souhaitez **exécuter** des applications Java, vous devez installer le [Java Runtime Environment](https://www.java.com/fr/download) (*JRE*). En revanche, si vous souhaitez **développer** des applications Java, vous devez installer le *Java Development Kit* (*JDK*) qui inclut également le *JRE*. Il existe plusieurs versions du *JDK* :

- *Oracle* fournit la [version officielle de Java](https://www.oracle.com/technetwork/java/javase/downloads/index.html) mais depuis la version 11, *Java* est sous une license qui nécessite un abonnement payant si vous développez des applications commerciales.
- [OpenJDK](https://jdk.java.net) est une version libre (license GNU GPL v2) et *open source* du *JRE*.
- [Amazon Corretto](https://aws.amazon.com/fr/corretto) est basé sur *OpenGDK* mais avec un support à long terme (*LTS*).

## Jshell

Comme pour le langage *Python*, *Java* fournit désormais un environnement de test en ligne de commande. Exécutez *Jshell* depuis votre terminal.

```
jshell -v
```

Vous pouvez alors saisir des commandes *Java* pour tester rapidement leur effet.

## IDEs

- *Eclipse Foundation* [Eclipse](https://www.eclipse.org/downloads).
- *JetBrains* [IntelliJ IDEA](https://www.jetbrains.com/idea/download).
- *Microsoft* [Visual Studio Code](https://code.visualstudio.com) (*VS Code*).

## Point d'entrée

Vous devez créer une classe (de préférence publique) comportant une méthode `Main` avec la signature suivante :

```java
public class Program
{
    public static void Main(String[] args)
    {

    }
}
```

## Constantes

Une variable déclarée avec le mot clé `final` ne peut plus être modifiée par la suite.

```java
final int PI = 3.14;
PI = 3.1415; // erreur
```

## Types de base

```java
byte byteValue; // -2^7 à 2^7 - 1 (un octet)
short shortValue; // -2^15 à 2^15 - 1 (deux octets)
int intValue; // -2^31 à 2^31 - 1 (quatre octets)
long longValue; // -2^63 à 2^63 - 1 et suffixe L (huit octets)
float floatValue = 0.1f; // nombre décimal et suffixe f (quatre octets)
double doubleValue = 0.1d; // nombre décimal et suffixe d (huit octets)
boolean booleanValue = true; // true ou false
char charValue = 'a'; // caractère unicode entre guillemets simples
```

Les données de types de base ne sont pas des références. Pour cela, vous devez utiliser les classes *wrapper* associées.

```java
Integer integerOne = new Integer(1);
Integer integerTwo = 2;
Integer integerThree = Integer.valueOf(3);
int intOne = integerOne;
int intTwo = integerTwo.intValue();
```

Vous pouvez convertir un type numérique vers un autre avec l'opérateur de cast.

```java
int intValue = 10;
short shortValue = (short) intValue;
```

La méthode `valueOf` de la classe `String` et des classes *wrapper* pour les types de base (`Byte`, `Short`, `Integer`, `Long`, `Float`, `Double`) permet de convertir une donnée en un autre type. Chacune de ces classes *wrapper* possède une méthode `*primitiveType*Value` qui retourne la valeur du type de base contenue dans l'objet.

```java
Integer integer = Integer.valueOf(5);
int intValue = integer.intValue();
byte byteValue = 5;
String stringByte;
stringByte.valueOf(byteValue);
byte byteValue = Integer.valueOf(stringByte).intValue();
```

## Opérateurs

```java
// opérateurs algébriques
int a = 5;
int b = 3;
int somme = a + b;
int difference = a - b;
int product = a * b;
int division = a / b;
int remainder = a % b;
a += 7; // a = a + 7;
a -= 7; // a = a - 7;
a *= 7; // a = a * 7;
a /= 7; // a = a / 7;
a %= 7; // a = a % 7;
a++; // renvoie l'ancienne valeur de a puis l'augmente de 1
++a; // augmente la valeur de a de 1 et renvoie sa nouvelle valeur
// opérateurs de comparaison
boolean less = a < b;
boolean lessOrEqual = a <= b;
boolean greater = a > b;
boolean greaterOrEqual = a >= b;
boolean equals = a == b;
boolean different = a != b;
// opérateurs logiques
boolean isTrue = true;
boolean isFalse = false;
boolean and = isTrue && isFalse; // ET logique
boolean or = isTrue || isFalse; // OU logique
boolean not = !isTrue; // NON logique
```

## Type String

```java
String stringValue = "Some text."; // caractères unicode entre guillemets doubles
String anotherStringValue = new String("Another text."); // appel du constructeur
```

La méthode `charAt` renvoie le caractère situé à l'indice spécifié.

```java
char charValue = stringValue.chatAt(0); // renvoie le premier caractère de la chaîne
```

La méthode `length` renvoie le nombre de caractères contenus dans la chaîne.

```java
stringValue.length(); // renvoie le nombre de caractères
```

La méthode `toLowerCase` renvoie une chaîne constituée uniquement de minuscules.

```java
String stringValue = "Mickey et Dingo";
System.out.println(stringValue.toLowerCase()); // affiche "mickey et dingo"
```

La méthode `toUpperCase` renvoie une chaîne constituée uniquement de minuscules.

```java
String stringValue = "Mickey et Dingo";
System.out.println(stringValue.toUpperCase()); // affiche "MICKEY ET DINGO"
```

La méthode `equals` indique si deux chaînes sont identiques. N'utilisez pas l'opérateur `==` pour les chaînes.

```java
String stringValue1 = "Mickey et Dingo";
String stringValue2 = "Mickey et Dingo";
stringValue.equals(stringValue2)); // renvoie true
```

La méthode `substring` renvoie une sous-chaîne d'une chaîne.

```java
String stringValue = "Mickey et Dingo";
stringValue.substring(10, 15); // renvoie "Dingo"
```

La méthode `indexOf` renvoie l'indice de la première occurrence d'une sous-chaîne située dans la chaîne en partant du début.

```java
String stringValue = "Mickey et Dingo et Donald";
stringValue.indexOf("et"); // renvoie 7
```

La méthode `lastIndexOf` renvoie l'indice de la premième occurrence d'une sous-chaîne située dans la chaîne en partant de la fin.

```java
String stringValue = "Mickey et Dingo et Donald";
stringValue.lastIndexOf("et"); // renvoie 16
```

## Fonctions mathématiques

La classe `Math` située dans le paquetage `java.lang` (automatiquement importé), fournit de nombreuses méthodes de classe pour les calculs mathématiques.

[`java.lang.Math`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/lang/Math.html)

```java
double angle = Math.PI; // renvoie la valeur de PI en radians
Math.cos(angle); // calcule le cosinus d'un angle en radians
Math.sin(angle); // calcule le sinus d'un angle en radians
Math.random(); // renvoie un nombre compris en 0 et 1
```

## Afficher du texte

```java
System.out.print("Some text."); // affiche le texte
System.out.println("Another text."); // affiche le texte et revient à la ligne
```

## Afficher les types de base ou les objets

Pour les types de base, utilisez simplement `System.out.print` ou `System.out.println`.

```java
int intValue = 10;
double doubleValue = 10.01d;
System.out.print(intValue); // affiche 10
System.out.println(doubleValue); // affiche 10.01 et revient à la ligne
```

Pour les objets, utilisez ces mêmes méthodes mais en redéfinissant la méthode `toString` héritée de la classe `Object`.

```java
public class SomeClass
{
    public int intValue;

    public SomeClass()
    {
        intValue = 99;
    }

    public String toString()
    {
        return Integer.toString(intValue);
    }
}
```

```java
SomeClass someClass = new SomeClass();
System.out.println(someClass); // affiche 99
```

## Récupérer les saisies utilisateur

Commencez par importer la classe `Scanner` du package `java.util`.

```java
import java.util.Scanner;
```

Créez une instance de la classe `Scanner` en lui passant l'entrée standard `System.in`.

```java
Scanner scanner = new Scanner(System.in);
```

Vous pouvez à présent appeler les méthodes de cet objet.

La classe [`Scanner`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/util/Scanner.html)

La méthode `nextLine` renvoie une chaîne saisie depuis la console.

```java
String userInput = scanner.nextLine();
```

Les méthodes `nextInt`, `nextDouble`, etc... à l'exception du type `char` renvoient une donnée saisie depuis la console.

```java
boolean booleanValue = scanner.nextBoolean();
byte byteValue = scanner.nextByte();
short shortValue = scanner.nextShort();
int intValue = scanner.nextInt();
long longValue = scanner.nextLong();
float floatValue = scanner.nextFloat();
double doubleValue = scanner.nextDouble();
```

**Remarque :** Ces méthodes peuvent provoquer une exception si l'utilisateur saisie une chaîne impossible à convertir dans le type attendu. Utilisez la série de méthode `hasNext...` pour vérifier si une saisie utilisateur peut-être convertie dans un type spécifique.

```java
if (scanner.hasNextInt())
{
    int intValue = scanner.nextInt();
}
else
{
    System.out.println("Saisie incorrecte.");
}
```

**Attention !** Une saisie chaîne après une saisie numérique nécessite de vider le tampon. Vous pouvez simplement appeler la méthode `nextLine` deux fois. Le premier appel servira à vider le tampon.

Une fois la saisie utilisateur terminée, vous pouvez fermer l'objet `Scanner` avec la méthode `close`. Vous ne pouvez plus appeler de méthodes `next...` sur l'objet `Scanner` après avoir appelé cette méthode.

```java
scanner.close();
```

## conventions

Les classes sont en `PascalCase`. Les variables et méthodes sont en `camelCase`.

## Structures de contrôle

```java
if (condition1)
{
    // instructions 1
}
else if (condition2)
{
    // instructions 2
}
else
{
    // instructions par défaut
}

switch (expression)
{
    case valeur1:
        // instructions 1
        break;
    case valeur2:
        // instructions 2
        break;
    default:
        // instructions par défaut
}

while (condition)
{
    // instructions
}

do
{
    // instructions
}
while (condition);

for (int i = 0; i < 10; ++i)
{
    // instructions
}
```

## Tableaux

Un tableau ne peut contenir que des éléments de même type.

```java
int[] intArray = {0, 1, 2, 3, 4};
double[] doubleArray = new double[10];
```

**Attention !** La version avec les accolades ne peut pas être utilisée après la déclaration du tableau.

```java
intArray = {1, 2, 3, 4, 5}; // erreur
```

Vous pouvez également placer les crochets après le nom de la variable mais la lecture du type en est plus difficile.

```java
int intArray[] = {0, 1, 2, 3, 4};
```

La propriété `length` (attention, ce n'est pas une méthode) indique le nombre d'éléments d'un tableau.

```java
for (int i = 0; i < intArray.length; ++i)
{
    // instructions
}
```

L'instruction `for` autorise également la construction suivante.

```java
for (int intValue: intArray)
{
    // instructions
}
```

### Afficher un tableau

La méthode `toString` affiche le contenu d'un tableau.

```java
int[] array = {1, 2, 3, 4, 5};
System.out.println(Array.toString(array));
```

### Copier un tableau

Les méthodes statiques `copyOf` de la classe `Array` renvoie une copie d'un tableau.

```java
int[] array = {5, 10, 15, 20};
int[] newArray = Array.copyOf(array, array.length);
```

**Attention !** Cette méthode effectue une copie en surface.

## ArrayList

La classe [`ArrayList`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/util/ArrayList.html), située dans le package `java.util`, permet de créer et de gérer une structure de donnée similaire à un tableau mais dont le nombre d'éléments peut varier.

Pour créer un objet de type `ArrayList`, utilisez le constructeur en précisant le type.

```java
import java.util.ArrayList;
ArrayList<String> stringArrayList = new ArrayList<String>();
```

**Attention !** Vous ne pouvez pas utiliser un type de base. Pour ça, utilisez les classes *wrapper*.

```java
import java.util.ArrayList;
ArrayList<Integer> intArrayList = new ArrayList<Integer>();
```

Utilisez la méthode `add` pour ajouter un élément.

```java
stringArrayList.add("Bonjour.");
intArrayList.add(Integer.valueOf(10));
```

Pour accéder à un élément, utiliser la méthode `get` avec l'indice de l'élément.

```java
String stringValue = stringArrayList.get(0);
int intValue = intArrayList.get(0).intValue();
```

## LinkedList

```java
import java.util.LinkedList;
import java.util.Iterator;
LinkedList<String> stringLinkedList = new LinkedList<String>();
stringLinkedList.add("Bonjour.");
stringLinkedList.add("Hello.");
stringLinkedList.add(1, "Guten tag.");
Iterator<String> i = stringLinkedList.iterator();
while (i.hasNext())
{
    System.out.println(i.next());
}
```

## Quand utiliser un `ListIterator` à la place d'un `Iterator` ?

Si vous avez besoin de revenir à un élément précédent, ou d'obtenir l'index d'un élément, utilisez un `ListIterator`.

```java
import java.util.LinkedList;
import java.util.LisrIterator;
LinkedList<String> stringLinkedList = new LinkedList<String>();
stringLinkedList.add("Bonjour.");
stringLinkedList.add("Hello.");
stringLinkedList.add(1, "Guten tag.");
ListIterator<String> i = stringLinkedList.iterator();
i.next();
i.previous();
i.get();
```

## Parcourir une collection avec une boucle `for`

```java
for (String string : stringLinkedList) {
    System.out.println(string);
}
```

## Classes

```java
public class SomeClass
{
    // déclaraction d'une variable d'instance
    private type nomDeVariable;

    // déclaration d'une variable de classe
    private static type nomDeVariable;

    // déclaration d'une méthode d'instance
    public type nomDeMéthode()
    {
        // instructions
    }

    // déclaration d'une méthode de classe
    public static type nomDeMéthode()
    {
        // instructions
    }

}
```

### Constructeurs

Un constructeur est une méthode qui n'a aucun type de retour et qui porte le même nom que la classe. Lorsque le comiplateur rencontre une classe sans constructeur, il génère automatiquement un constructeur par défaut sans paramètre. Vous pouvez ainsi appeler le constructeur d'une classe n'en possédant pas pour créer un objet de cette classe. En revanche, à partir du moment où vous définissez au moins un constructeur, le compilateur ne génère plus ce constructeur par défaut.

```java
public class SomeClass
{
    public SomeClass() // constructeur par défaut
    {

    }

    public SomeClass(NomDeType nomDeParametre, ...) // constructeur avec paramètres
    {

    }
}
```

Vous pouvez ensuite créer des instances de la classe grâce au mot clé `new`.

```java
SomeClass someClass1 = new SomeClass(); // appel au constructeur par défaut
SomeClass someClass2 = new SomeClass(argument); // appel au constructeur avec paramètres
```

### le mot clé this

Le mot clé `this` permet de faire référence à l'objet courant. Il peut être utilisé pour appeler un membre de l'objet ou une de ses méthodes depuis une autre méthode de cet objet (y compris le constructeur).

```java
public class SomeClass
{
    private int intValue;
    private int otherIntValue;

    public SomeClass(int intValue)
    {
        this.intValue = intValue;
        this.setOtherIntValue();
    }

    private void setOtherIntValue()
    {
        this.otherIntValue = this.intValue;
    }
}
```

Vous pouvez également appeler un autre constructeur depuis un constructeur avec l'appel `this()`. Cependant, cet appel doit être la première instruction du constructeur.

```java
public class SomeClass
{
    private int intValue;

    public SomeClass(int intValue)
    {
        this.intValue = intValue;
    }

    public SomeClass()
    {
        this(0); // appel du premier constructeur avec une valeur par défaut
        // autres instructions
    }
}
```

### Héritage

Une sous-classe peut étendre une classe parent pour lui ajouter des fonctionnalités. Vous pouvez ajouter de nouveaux membres et de nouvelles méthodes. Utilisez le mot clé `extends` pour définir une sous-classe d'une autre classe.
Une sous-classe peut également redéfinir une méthode de sa classe parent (même nom et même paramètres) à condition que la méthode soit déclarée `public` ou `protected` dans la classe parent. Pour un code plus sûr, vous pouvez ajouter une annotation `@Override` pour signaler explicitement au compilateur que vous redéfinissez une méthode dans une sous-classe.
Vous pouvez appeler une méthode de la classe parent avec l'appel `super()` depuis la méthode de la classe enfant. Cependant, cet appel doit être la première instruction de la méthode.
Lors de l'instanciation d'un objet de la sous-classe, si vous n'appelez pas explicitement le constructeur de la classe parent dans le constructeur de la sous-classe, le compilateur ajoute automatiquement un appel au constructeur sans argument de la classe parent. Si la classe parent ne définit que des constructeurs avec au moins un paramètre, une erreur se produit à la compilation.

```java
public class Parent
{
    public Parent()
    {

    }

    protected void someMethod()
    {

    }
}


public class Child extends Parent
{
    public Child()
    {
        super();
        // instructions
    }

    @Override
    public void someMethod()
    {
        super.someMethod();
        // instructions
    }
}
```

### Méthodes finales

Une méthode définie avec le mot clé `final` ne peut être redéfinie dans une sous-classe.

```java
public class Parent
{
    public final void someFinalMethod()
    {

    }
}


public class Child extends Parent
{
    public void someFinalMethod() // erreur
    {

    }
}
```

### Classes finales

Les classes finales n'ont que des méthodes finales. Elles ne peuvent pas posséder de sous-classe.

### Classe abstraite

```java
public class AbstractClass
{
    abstract public type someMethod();
}
```

### Interfaces

```java
public interface SomeInterface
{
    public type someMethod();
}


class ImplementsSomeInterface implements SomeInterface
{
    public type someMethod()
    {
        // instructions
    }
}
```

### Surcharge de méthode

Une classe peut surcharger une méthode définie dans sa propre classe ou une classe parent avec différents arguments (en nombre ou en type)
.

### Surdéfinition de méthode

Une classe enfant peut redéfinir une méthode d'instance (**pas statique**) d'une classe parent si elle possède les mêmes arguments (en nombre et en type). Avant de redéfinir la méthode, placez l'annotation `@Override`. Le type de retour doit être le même que la classe parent ou d'un de ses sous-types. Elle ne peut pas réduire l'éccessibilité de la méthode d'origine.

```java
public class Parent
{
    protected void someMethod()
    {

    }
}


public class Child extends Parent
{
    @Override
    public void someMethod()
    {
        super.someMethod();
        // instructions
    }
}
```




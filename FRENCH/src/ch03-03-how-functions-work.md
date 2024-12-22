<!--
## Functions
-->

## Les fonctions

<!--
Functions are prevalent in Rust code. You’ve already seen one of the most
important functions in the language: the `main` function, which is the entry
point of many programs. You’ve also seen the `fn` keyword, which allows you to
declare new functions.
-->

Les fonctions sont très utilisées dans le code Rust. Vous avez déjà vu l'une des
fonctions les plus importantes du langage : la fonction `main`, qui est le point
d'entrée de beaucoup de programmes. Vous avez aussi vu le mot-clé `fn`, qui vous
permet de déclarer des nouvelles fonctions.

<!--
Rust code uses *snake case* as the conventional style for function and variable
names, in which all letters are lowercase and underscores separate words.
Here’s a program that contains an example function definition:
-->

Le code Rust utilise le *snake case* comme convention de style de nom des
fonctions et des variables, toutes les lettres sont en minuscule et on utilise
des tirets bas pour séparer les mots. Voici un programme qui est un exemple de
définition de fonction :

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/no-listing-16-functions/src/main.rs}}
```
-->

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-16-functions/src/main.rs}}
```

<!--
We define a function in Rust by entering `fn` followed by a function name and a
set of parentheses. The curly brackets tell the compiler where the function
body begins and ends.
-->

Nous définissons une fonction avec Rust en saisissant `fn` suivi par un nom de
fonction ainsi qu'une paire de parenthèses. Les accolades indiquent au
compilateur où le corps de la fonction commence et où il se termine.

<!--
We can call any function we’ve defined by entering its name followed by a set
of parentheses. Because `another_function` is defined in the program, it can be
called from inside the `main` function. Note that we defined `another_function`
*after* the `main` function in the source code; we could have defined it before
as well. Rust doesn’t care where you define your functions, only that they’re
defined somewhere.
-->

Nous pouvons appeler n'importe quelle fonction que nous avons définie en
utilisant son nom, suivi d'une paire de parenthèses. Comme `une_autre_fonction`
est définie dans le programme, elle peut être appelée à l'intérieur de la
fonction `main`. Remarquez que nous avons défini `une_autre_fonction` *après*
la fonction `main` dans le code source ; nous aurions aussi pu la définir avant.
Rust ne se soucie pas de l'endroit où vous définissez vos fonctions, du moment
qu'elles sont bien définies quelque part.

<!--
Let’s start a new binary project named *functions* to explore functions
further. Place the `another_function` example in *src/main.rs* and run it. You
should see the following output:
-->

Créons un nouveau projet de binaire qui s'appellera *functions* afin d'en
apprendre plus sur les fonctions. Ajoutez l'exemple `une_autre_fonction` dans le
*src/main.rs* et exécutez-le. Vous devriez avoir ceci :

<!--
```console
{{#include ../listings-sources/ch03-common-programming-concepts/no-listing-16-functions/output.txt}}
```
-->

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-16-functions/output.txt}}
```

<!--
The lines execute in the order in which they appear in the `main` function.
First, the “Hello, world!” message prints, and then `another_function` is
called and its message is printed.
-->

Les lignes s'exécutent dans l'ordre dans lequel elles apparaissent dans la
fonction `main`. D'abord, le message `Hello, world!` est écrit, et ensuite
`une_autre_fonction` est appelée et son message est affiché.

<!--
### Parameters
-->

### Les paramètres

<!--
We can define functions to have *parameters*, which are special variables that
are part of a function’s signature. When a function has parameters, you can
provide it with concrete values for those parameters. Technically, the concrete
values are called *arguments*, but in casual conversation, people tend to use
the words *parameter* and *argument* interchangeably for either the variables
in a function’s definition or the concrete values passed in when you call a
function.
-->

Nous pouvons définir des fonctions avec des *paramètres*, qui sont des
variables spéciales qui font partie de la signature de la fonction. Quand une
fonction a des paramètres, vous pouvez lui fournir des valeurs concrètes avec
ces paramètres. Techniquement, ces valeurs concrètes sont appelées des
*arguments*, mais dans une conversation courante, on a tendance à
confondre les termes *paramètres* et *arguments* pour désigner soit les
variables dans la définition d'une fonction, soit les valeurs concrètes passées
quand on appelle une fonction.

<!--
In this version of `another_function` we add a parameter:
-->

Dans cette version de `une_autre_fonction`, nous ajoutons un paramètre :

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/no-listing-17-functions-with-parameters/src/main.rs}}
```
-->

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-17-functions-with-parameters/src/main.rs}}
```

<!--
Try running this program; you should get the following output:
-->

En exécutant ce programme, vous devriez obtenir ceci :

<!--
```console
{{#include ../listings-sources/ch03-common-programming-concepts/no-listing-17-functions-with-parameters/output.txt}}
```
-->

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-17-functions-with-parameters/output.txt}}
```

<!--
The declaration of `another_function` has one parameter named `x`. The type of
`x` is specified as `i32`. When we pass `5` in to `another_function`, the
`println!` macro puts `5` where the pair of curly brackets were in the format
string.
-->

La déclaration de `une_autre_fonction` a un paramètre nommé `x`. Le type de
`x` a été déclaré comme `i32`. Quand nous passons `5` à `une_autre_fonction`, la
macro `println!` place `5` là où la paire d'accolades `{}` a été placée dans la
chaîne de formatage.

<!--
In function signatures, you *must* declare the type of each parameter. This is
a deliberate decision in Rust’s design: requiring type annotations in function
definitions means the compiler almost never needs you to use them elsewhere in
the code to figure out what type you mean.
-->

Dans la signature d'une fonction, vous *devez* déclarer le type de chaque
paramètre. C'est un choix délibéré de conception de Rust : exiger l'annotation
de type dans la définition d'une fonction fait en sorte que le compilateur n'a
presque plus besoin que vous les utilisiez autre part pour qu'il comprenne avec
quel type vous souhaitez travailler.

<!--
When defining multiple parameters, separate the parameter declarations with
commas, like this:
-->

Lorsque vous définissez plusieurs paramètres, séparez les paramètres avec des
virgules, comme ceci :

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/no-listing-18-functions-with-multiple-parameters/src/main.rs}}
```
-->

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-18-functions-with-multiple-parameters/src/main.rs}}
```

<!--
This example creates a function named `print_labeled_measurement` with two
parameters. The first parameter is named `value` and is an `i32`. The second is
named `unit_label` and is type `char`. The function then prints text containing
both the `value` and the `unit_label`.
-->

Cet exemple crée la fonction `afficher_mesure_avec_unite` qui a deux paramètres.
Le premier paramètre s'appelle `valeur` et est un `i32`. Le second, `unite`,
est de type `char`. La fonction affiche ensuite le texte qui contient les
valeurs de `valeur` et de `unite`.

<!--
Let’s try running this code. Replace the program currently in your *functions*
project’s *src/main.rs* file with the preceding example and run it using `cargo
run`:
-->

Essayons d'exécuter ce code. Remplacez le programme présent actuellement dans
votre fichier *src/main.rs* de votre projet *functions* par l'exemple précédent
et lancez-le en utilisant `cargo run` :

<!--
```console
{{#include ../listings-sources/ch03-common-programming-concepts/no-listing-18-functions-with-multiple-parameters/output.txt}}
```
-->

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-18-functions-with-multiple-parameters/output.txt}}
```

<!--
Because we called the function with `5` as the value for `value` and `'h'` as
the value for `unit_label`, the program output contains those values.
-->

Comme nous avons appelé la fonction avec la valeur `5` pour `valeur` et `'h'`
pour `unite`, la sortie de ce programme contient ces valeurs.

<!--
### Statements and Expressions
-->

### Instructions et expressions

<!--
Function bodies are made up of a series of statements optionally ending in an
expression. So far, the functions we’ve covered haven’t included an ending
expression, but you have seen an expression as part of a statement. Because
Rust is an expression-based language, this is an important distinction to
understand. Other languages don’t have the same distinctions, so let’s look at
what statements and expressions are and how their differences affect the bodies
of functions.
-->

Les corps de fonctions sont constitués d'une série d'instructions qui se
termine éventuellement par une expression. Jusqu'à présent, les fonctions que
nous avons vu n'avaient pas d'expression à la fin, mais vous avez déjà vu une
expression faire partie d'une instruction. Comme Rust est un langage basé sur
des expressions, il est important de faire la distinction. D'autres langages ne
font pas de telles distinctions, donc penchons-nous sur ce que sont les
instructions et les expressions et comment leurs différences influent sur le
corps des fonctions.

<!--
*Statements* are instructions that perform some action and do not return a
value. *Expressions* evaluate to a resulting value. Let’s look at some examples.
-->

Les *instructions* effectuent des actions et ne retournent aucune valeur.
Les *expressions* sont évaluées pour retourner une valeur comme résultat.
Voyons quelques exemples.

<!--
We’ve actually already used statements and expressions. Creating a variable and
assigning a value to it with the `let` keyword is a statement. In Listing 3-1,
`let y = 6;` is a statement.
-->

Nous avons déjà utilisé des instructions et des expressions. La création d'une
variable en lui assignant une valeur avec le mot-clé `let` est une instruction.
Dans l'encart 3-1, `let y = 6;` est une instruction.

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/listing-03-01/src/main.rs}}
```
-->

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/listing-03-01/src/main.rs}}
```

<!-- markdownlint-disable -->
<!--
<span class="caption">Listing 3-1: A `main` function declaration containing one statement</span>
-->
<!-- markdownlint-restore -->

<span class="caption">Encart 3-1 : une fonction `main` qui contient une
instruction</span>

<!--
Function definitions are also statements; the entire preceding example is a
statement in itself.
-->

La définition d'une fonction est aussi une instruction ; l'intégralité de
l'exemple précédent est une instruction à elle toute seule.

<!--
Statements do not return values. Therefore, you can’t assign a `let` statement
to another variable, as the following code tries to do; you’ll get an error:
-->

Une instruction ne retourne pas de valeur. Ainsi, vous ne pouvez pas assigner
le résultat d'une instruction `let` à une autre variable, comme le code suivant
essaye de le faire, car vous obtiendrez une erreur :

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust,ignore,does_not_compile
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/no-listing-19-statements-vs-expressions/src/main.rs}}
```
-->

```rust,ignore,does_not_compile
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-19-statements-vs-expressions/src/main.rs}}
```

<!--
When you run this program, the error you’ll get looks like this:
-->

Quand vous exécutez ce programme, l'erreur que vous obtenez devrait ressembler à
ceci :

<!--
```console
{{#include ../listings-sources/ch03-common-programming-concepts/no-listing-19-statements-vs-expressions/output.txt}}
```
-->

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-19-statements-vs-expressions/output.txt}}
```

<!--
The `let y = 6` statement does not return a value, so there isn’t anything for
`x` to bind to. This is different from what happens in other languages, such as
C and Ruby, where the assignment returns the value of the assignment. In those
languages, you can write `x = y = 6` and have both `x` and `y` have the value
`6`; that is not the case in Rust.
-->

L'instruction `let y = 6` ne retourne pas de valeur, donc cela ne peut pas
devenir une valeur de `x`. Ceci est différent d'autres langages, comme le C ou
Ruby, où l'assignation retourne la valeur de l'assignation. Dans ces
langages, vous pouvez écrire `x = y = 6` et avoir ainsi `x` et `y` qui ont
chacun la valeur `6` ; cela n'est pas possible avec Rust.

<!--
Expressions evaluate to a value and make up most of the rest of the code that
you’ll write in Rust. Consider a math operation, such as `5 + 6`, which is an
expression that evaluates to the value `11`. Expressions can be part of
statements: in Listing 3-1, the `6` in the statement `let y = 6;` is an
expression that evaluates to the value `6`. Calling a function is an
expression. Calling a macro is an expression. A new scope block created with
curly brackets is an expression, for example:
-->

Les expressions sont calculées en tant que valeur et seront ce que vous écrirez
le plus en Rust (hormis les instructions). Prenez une opération mathématique,
comme `5 + 6`, qui est une expression qui s'évalue à la valeur `11`. Les
expressions peuvent faire partie d'une instruction : dans l'encart 3-1, le `6`
dans l'instruction `let y = 6;` est une expression qui s'évalue à la valeur `6`.
L'appel de fonction est aussi une expression. L'appel de macro est une
expression. Un nouveau bloc de portée que nous créons avec des accolades est
une expression, par exemple :

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/no-listing-20-blocks-are-expressions/src/main.rs}}
```
-->

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-20-blocks-are-expressions/src/main.rs}}
```

<!--
This expression:
-->

L'expression suivante…

<!--
```rust,ignore
{
    let x = 3;
    x + 1
}
```
-->

```rust,ignore
{
    let x = 3;
    x + 1
}
```

<!--
is a block that, in this case, evaluates to `4`. That value gets bound to `y`
as part of the `let` statement. Note that the `x + 1` line doesn’t have a
semicolon at the end, unlike most of the lines you’ve seen so far. Expressions
do not include ending semicolons. If you add a semicolon to the end of an
expression, you turn it into a statement, and it will then not return a value.
Keep this in mind as you explore function return values and expressions next.
-->

… est un bloc qui, dans ce cas, s'évalue à `4`. Cette valeur est assignée à `y`
dans le cadre de l'instruction `let`. Remarquez la ligne `x + 1` ne se termine
pas par un point-virgule, ce qui est différent de la plupart des lignes que
vous avez vues jusque là. Les expressions n'ont pas de point-virgule de fin de
ligne. Si vous ajoutez un point-virgule à la fin de l'expression, vous la
transformez en instruction, et elle ne va donc pas retourner de valeur. Gardez
ceci à l'esprit quand nous aborderons prochainement les valeurs de retour des
fonctions ainsi que les expressions.

<!--
### Functions with Return Values
-->

### Les fonctions qui retournent des valeurs

<!--
Functions can return values to the code that calls them. We don’t name return
values, but we must declare their type after an arrow (`->`). In Rust, the
return value of the function is synonymous with the value of the final
expression in the block of the body of a function. You can return early from a
function by using the `return` keyword and specifying a value, but most
functions return the last expression implicitly. Here’s an example of a
function that returns a value:
-->

Les fonctions peuvent retourner des valeurs au code qui les appelle.
Nous ne nommons pas les valeurs de retour, mais nous devons déclarer
leur type après une flèche (`->`). En Rust, la valeur de retour de la fonction
est la même que la valeur de l'expression finale dans le corps de la fonction.
Vous pouvez sortir prématurément d'une fonction en utilisant le mot-clé `return`
et en précisant la valeur de retour, mais la plupart des fonctions vont
retourner implicitement la dernière expression.
Voici un exemple d'une fonction qui retourne une valeur :

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/no-listing-21-function-return-values/src/main.rs}}
```
-->

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-21-function-return-values/src/main.rs}}
```

<!--
There are no function calls, macros, or even `let` statements in the `five`
function—just the number `5` by itself. That’s a perfectly valid function in
Rust. Note that the function’s return type is specified too, as `-> i32`. Try
running this code; the output should look like this:
-->

Il n'y a pas d'appel de fonction, de macro, ni même d'instruction `let` dans la
fonction `cinq` — uniquement le nombre `5` tout seul. C'est une fonction
parfaitement valide avec Rust. Remarquez que le type de retour de la fonction a
été précisé aussi, avec `-> i32`. Essayez d'exécuter ce code ; le résultat
devrait ressembler à ceci :

<!--
```console
{{#include ../listings-sources/ch03-common-programming-concepts/no-listing-21-function-return-values/output.txt}}
```
-->

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-21-function-return-values/output.txt}}
```

<!--
The `5` in `five` is the function’s return value, which is why the return type
is `i32`. Let’s examine this in more detail. There are two important bits:
first, the line `let x = five();` shows that we’re using the return value of a
function to initialize a variable. Because the function `five` returns a `5`,
that line is the same as the following:
-->

Le `5` dans `cinq` est la valeur de retour de la fonction, ce qui explique le
type de retour de `i32`. Regardons cela plus en détail. Il y a deux éléments
importants : premièrement, la ligne `let x = cinq();` dit que nous utilisons
la valeur de retour de la fonction pour initialiser la variable. Comme la
fonction `cinq` retourne un `5`, cette ligne revient à faire ceci :

<!--
```rust
let x = 5;
```
-->

```rust
let x = 5;
```

<!--
Second, the `five` function has no parameters and defines the type of the
return value, but the body of the function is a lonely `5` with no semicolon
because it’s an expression whose value we want to return.
-->

Deuxièmement, la fonction `cinq` n'a pas de paramètre et déclare le type de
valeur de retour, mais le corps de la fonction est un simple `5` sans
point-virgule car c'est une expression dont nous voulons retourner la valeur.

<!--
Let’s look at another example:
-->

Regardons un autre exemple :

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/no-listing-22-function-parameter-and-return/src/main.rs}}
```
-->

```rust
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-22-function-parameter-and-return/src/main.rs}}
```

<!--
Running this code will print `The value of x is: 6`. But if we place a
semicolon at the end of the line containing `x + 1`, changing it from an
expression to a statement, we’ll get an error.
-->

Exécuter ce code va afficher `La valeur de x est : 6`. Mais si nous ajoutons un
point-virgule à la fin de la ligne qui contient `x + 1`, ce qui la transforme
d'une expression à une instruction, nous obtenons une erreur.

<!--
<span class="filename">Filename: src/main.rs</span>
-->

<span class="filename">Fichier : src/main.rs</span>

<!--
```rust,ignore,does_not_compile
{{#rustdoc_include ../listings-sources/ch03-common-programming-concepts/no-listing-23-statements-dont-return-values/src/main.rs}}
```
-->

```rust,ignore,does_not_compile
{{#rustdoc_include ../listings/ch03-common-programming-concepts/no-listing-23-statements-dont-return-values/src/main.rs}}
```

<!--
Compiling this code produces an error, as follows:
-->

Compiler ce code va produire une erreur, comme ci-dessous :

<!--
```console
{{#include ../listings-sources/ch03-common-programming-concepts/no-listing-23-statements-dont-return-values/output.txt}}
```
-->

```console
{{#include ../listings/ch03-common-programming-concepts/no-listing-23-statements-dont-return-values/output.txt}}
```

<!--
The main error message, “mismatched types,” reveals the core issue with this
code. The definition of the function `plus_one` says that it will return an
`i32`, but statements don’t evaluate to a value, which is expressed by `()`,
the unit type. Therefore, nothing is returned, which contradicts the function
definition and results in an error. In this output, Rust provides a message to
possibly help rectify this issue: it suggests removing the semicolon, which
would fix the error.
-->

Le message d'erreur principal, “mismatched types” *(types inadéquats)* donne le
cœur du problème de ce code. La définition de la fonction `plus_un` dit qu'elle
va retourner un `i32`, mais les instructions ne retournent pas de valeur, ceci
est donc représenté par `()`, le type unité. Par conséquent, rien n'est
retourné, ce qui contredit la définition de la fonction et provoque une erreur.
Rust affiche un message qui peut aider à corriger ce problème : il suggère
d'enlever le point-virgule, ce qui va résoudre notre problème.

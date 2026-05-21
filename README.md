# learn_rust

https://rustlings.rust-lang.org/
https://github.com/rust-lang/rustlings

# Compiler un fichier Rust

```bash
rustc hello.rs
# rustc will produce a hello binary that can be executed.

$ ./hello
Hello World!
```

# Variable

```rust
// Declaration d'un entier immubale, constante ?
let mut age: i32 = 25;
// Declaration d'un flottant, d'une variable
let temperatur: f64 = 24.5;
// Declaration d'un caractere
let grade : char = 'A';
let keyboard = '⌨';
// Declaration d'un booleen
let is_active : bool = false;
// Déclaration d'un tableau d'entier
let array: [i32; 5] = [0, 1, 2, 3, 4];

// Declaration d'une chaine de catactere
let user_name : String = "Bob123".to_string() ;
// Declaration d'un chaine de caractere
let mut name: &str = "Alice";
// Affiche sur la console
println!("Hello {}!", name);

// Conversion d'entier vers flottant
let number: i32 = 5;
let decimal: f64 = number as f64;
// devient 5.0

// Conversion de flottant vers entier
let decimal: f64 = 9.7;
let number: i32 = decimal as i32;
// devient 9 (la partie décimale est tronquée)

// Littéraux de chaîne simples (str) :
let str1 = "hello";
// Chaînes complètes (String) :
let string1: String = "hello".to_string();
let string2: String = String::from("hello");
let string3 = "hello".to_owned();

// Afficher une valeur flottante avec deux décimales : This is rounded: 1.56
println!("This is rounded: {:.2}", num);

// Méthode 1 : Consulter les données (en utilisant &) :
for number in &numbers {
    sum += number;
}
println!("I can use it here: {:?}", numbers);

// Méthode 2 : Prendre les données (sans &) :
for number in numbers {
    sum += number;
}
// println!("Can't use {:?} anymore!", numbers);
// Cela provoquerait une erreur
```

## Chaines de caracteres

len() : Retourne le nombre de caractères dans la chaîne.
chars().nth(index) : Retourne le caractère à l'index spécifié (basé sur 0). Cette méthode retourne un Option<char> — un type Rust spécial qui représente soit une valeur Some (si l'index existe) ou None (s'il n'existe pas). Appeler .unwrap() dessus extrait directement la valeur du caractère.
contains(substring): Vérifie si la chaîne contient la sous-chaîne spécifiée.
starts_with(prefix): Vérifie si la chaîne commence par le préfixe spécifié.
ends_with(suffix): Vérifie si la chaîne se termine par le suffixe spécifié.
to_uppercase(): Convertit la chaîne en majuscules.
to_lowercase(): Convertit la chaîne en minuscules.
trim(): Supprime les espaces blancs au début et à la fin de la chaîne.

## Entrée/Sortie

### Sortie

```rust
    // Positional arguments can be used. Specifying an integer inside `{}`
    // determines which additional argument will be replaced. Arguments start
    // at 0 immediately after the format string.
    println!("{0}, this is {1}. {1}, this is {0}", "Alice", "Bob");

    // As can named arguments.
    println!("{subject} {verb} {object}",
             object="the lazy dog",
             subject="the quick brown fox",
             verb="jumps over");

    // Different formatting can be invoked by specifying the format character
    // after a `:`.
    println!("Base 10:               {}",   69420); // 69420
    println!("Base 2 (binary):       {:b}", 69420); // 10000111100101100
    println!("Base 8 (octal):        {:o}", 69420); // 207454
    println!("Base 16 (hexadecimal): {:x}", 69420); // 10f2c

    // You can right-justify text with a specified width. This will
    // output "    1". (Four white spaces and a "1", for a total width of 5.)
    println!("{number:>5}", number=1);

    // You can pad numbers with extra zeroes,
    println!("{number:0>5}", number=1); // 00001
    // and left-adjust by flipping the sign. This will output "10000".
    println!("{number:0<5}", number=1); // 10000

    // You can use named arguments in the format specifier by appending a `$`.
    println!("{number:0>width$}", number=1, width=5);

	let numbers = [1, 2, 3, 4, 5];
	print!("{:?} ", numbers); // Sortie : [1, 2, 3, 4, 5]

	let arr = [1.12345, 2.23456, 3.34567];
	println!("{:.2?}", arr);// Sortie : [1.12, 2.23, 3.35]
```

### Entrée

```rust
// Import pour utiliser la bibliothèque io
use std::io;
// [...]
// Crée une chaîne vide pour stocker l'entrée
let mut my_var = String::new();
// Lit l'entrée
io::stdin().read_line(&mut my_var).unwrap();
// Parser une valeur pour la stocker en entier
// Le .trim permet de supprimer le \n de l'appuie sur entree
let age: i32 = input.trim().parse().unwrap();
```

# Control et boucle

# if

```rust
let x = 3;

if x < 10 {
	println!("{} is less than 10", x);
} else {
	println!("{} is greater than or equal to 10", x);
}

```

# match

```rust
let day = 3;
let day_name = match day {
	1 => {
		println!("First day of the week!");
		"Monday"
	},
	2 | 3 | 4 | 5 => "Weekday",
	// ... autres cas
	_ => "Invalid day",
};
```

# loop

```rust
let mut x = 0;

loop{
	x++;

	if x >= 100 {
		println!("{} is now over 100 so we break the loop", x);
		break; // Permet de sortir de la boucle
	}
	
	if x % 3 != 0 {
		continue; // The print statment following this if statement will not be printed
	}

	println!("{} is divisible by 3", x);
}
```

```rust
'outer: for i in 1..=3 {
    'inner: for j in 1..=3 {
        if i * j > 5 {
            break 'outer; // Cela interrompra la boucle externe
        }else if i == j {
            continue 'outer; // Cela continuera la boucle externe
        }
		println!("({}, {})", i, j);	
    }
}
```

# while

```rust
let mut x = 0;

while x <= 100 {
	x += 1;

	if x % 3 == 0 {
		println!("{} is divisible by 3", x);
	}
}
```

# For-In Loop

```rust
for x in 1..101 {
	if x % 3 == 0 {
		println!("{} is divisible by 3", x);
	}
}

// Intervalle inversé
for i in (0..5).rev() { } // Valeurs : 4, 3, 2, 1, 0

// Avancer de 2 en 2
for i in (0..10).step_by(2) { } // Valeurs : 0, 2, 4, 6, 8

// Combiner l'inversion et le pas
for i in (0..10).rev().step_by(3) { } // Valeurs : 9, 6, 3, 0

// Itérateur direct
for num in numbers.iter() {} // Valeurs : 1, 2, 3, 4, 5

// Index & Valeur :
for (index, value) in numbers.iter().enumerate() { } // Valeurs : (0,1), (1,2), (2,3), (3,4), (4,5)

for chunk in numbers.chunks(2) { }
// Valeurs : [1,2], [3,4], [5]
```

# Functions in Rust

```rust
fn main(){
	divisible_by_three_between(1,31);
	println!("The square of 12 is {}", square_num(12));
}

fn divisible_by_three_between(min: i32, max_exclusive: i32) {
	for x in min..max_exclusive {
		if x % 3 == 0 {
			println!("{} is divisible by 3", x);
		}
	}
}

fn square_num(n: i32) -> i32 {
	n * n // La derniere instruction sera retourne par la methode
}

fn function_name() -> i32 {
	return 100;
}
//[...]
let number: i32 = function_name();

fn get_coordinates() -> (i32, i32) {
    let x = 10;
    let y = 20;
    (x, y) // Retourne un tuple
}
```

# Tableaux

```rust
// Declarer un tableau
let numbers = [1, 2, 3, 4, 5];
// Recuperer la taille d'un tableau
let length = numbers.len();

let numbers: [i32; 5] = [0; 5];

let numbers = [1, 2, 3, 4, 5];
process_array(&numbers);

// Tableaux de taille fixe :
fn process_array(arr: [i32; 5]) {}

// Une référence est comme un pointeur vers des données au lieu des données elles-mêmes. L'utilisation de & crée une référence. Cela permet de passer un tableau de n'importe quelle taille.
fn process_array(arr: &[i32]) {}

// Acces a un element du tableau
let numbers = [10, 20, 30, 40, 50];
let element = numbers[2];

// Lorsqu'un tableau est une référence, vous pouvez le rendre mutable en utilisant &mut. Cela vous permet de modifier les données d'origine via la référence.
fn process_array(arr: &mut [i32]) {
	arr[0] = 3;
}

// Méthode 1 : Consulter les données (en utilisant &) :
for number in &numbers {
    sum += number;
}
println!("I can use it here: {:?}", numbers);

// Méthode 2 : Prendre les données (sans &) :
for number in numbers {
    sum += number;
}
// println!("Can't use {:?} anymore!", numbers);
// Cela provoquerait une erreur

// Pensez-y de cette façon :
// 1 - Utiliser & c'est comme regarder un album photo : vous pouvez voir toutes les photos, mais l'album reste intact
// 2 - Ne pas utiliser & c'est comme retirer les photos : vous pouvez les utiliser, mais l'album sera vide après
```

```rust
```
```rust
```

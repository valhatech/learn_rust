# learn_rust

[[_TOC_]]

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
```

```rust
```
```rust
```

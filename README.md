# Basic Guessing Games

## Introduction

This documentation provides a comprehensive overview of the guessing game implemented in Rust. The game is a simple interactive program where the player attempts to guess a randomly generated number.

## Rust Book Inspiration

This guessing game is inspired by the Rust programming language book's introductory tutorial. It serves as a practical example for learning basic Rust concepts, such as user input, error handling, random number generation, and pattern matching. Read the tutorial here [Rust Guessing Games](https://doc.rust-lang.org/book/ch02-00-guessing-game-tutorial.html).

## Implementation

The game is implemented in the Rust programming language and consists of a single file. The code uses standard input/output for user interaction and the `rand` crate for random number generation.

```rust
use std::io;
use rand::Rng;
use std::cmp::Ordering;

fn main() {
    // Code...
}
```

## Dependencies

The game relies on the following external crate:

`rand`: Used for generating random numbers.

You can add this dependency to your `Cargo.toml` file:
```toml
[dependencies]
rand = "0.8"
```

## Game Loop

The main game logic is implemented in a loop, allowing the player to make multiple guesses until they correctly identify the secret number.
```rust
let secret_number = rand::thread_rng().gen_range(1..=100);

loop {
    // Code...
}
```

## User Input

The player is prompted to input their guess, and the program reads the input using `stdin`.
```rust
let mut guess = String::new();

io::stdin()
    .read_line(&mut guess)
    .expect("Failed to read line");
```

## Parsing User Input

The user's input is parsed into an unsigned 32-bit integer. If parsing fails, the program continues to the next iteration of the loop.

```rust
let guess: u32 = match guess.trim().parse() {
    Ok(num) => num,
    Err(_) => continue,
};
```

## Guess Comparison

The player's guess is compared to the randomly generated secret number, and the program provides feedback based on the comparison.

```rust
match guess.cmp(&secret_number) {
    Ordering::Less => println!("Too small"),
    Ordering::Greater => println!("Too big"),
    Ordering::Equal => {
        println!("You win!");
        break;
    },
}
```

If the guess is less than the secret number, the program prints "Too small." If it's greater, it prints "Too big." If the guess is equal to the secret number, the player wins, and the game loop exits.

## Conclusion

This guessing game is a beginner-friendly Rust program that incorporates fundamental concepts. It serves as a practical introduction to Rust syntax, user input handling, error management, and external crate usage. Feel free to modify and expand upon this code as you continue to explore Rust programming.

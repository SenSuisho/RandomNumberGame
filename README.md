# RandomNumberGame
RandomNumberGame is a project that utilizes interaction between the user and the console. As the game starts, the program will create a four-digit "code" that the user will attempt to guess. While checking the user's input the porgram will also check for numbers that are a part of the generated code, but not in the correct position. The program will keep track of these values both, "correct" and "misplaced", and will display them to the user. After the twelfth unsuccesful guess, the main game will end as a loss for the user and output the secret code. The game will then prompt the user to either continue playing or terminate the program entirely.
## Components
The program uses functions and constants to control the flow of the game and manage the secret code requirements
```C++
string generate_code();
string get_player_code();
```
These functions handle both the computer code and the player code. **get_player_code** will accept the input of the user and validate it against the constant variable of code length. **generate_code** creates the random function by utilizing a basic random number generating function.
```C++
void print_instructions()
int randint(int);
int randint(int, int);
```
These are helper functions that do basic tasks. With **print_instructions** the program outputs a formatted welcome message and description for the user. The randint functions generate the random integers **generat_code** needs to produce the secret code.
## The Main Method
The main method handles nearly all user interactivity. The majority of the work in the main method is present in the two **for** loops that checks the user's code against the secret code. 
```C++

			for (int i = 0; i < player_code_copy.size(); i++) {
				if (player_code_copy[i] == secret_code_copy[i]) {
					correct_digits++;
					player_code_copy[i] = 'X';
					secret_code_copy[i] = 'Y';
				}
			}
			
			for (int i = 0; i < player_code_copy.size(); i++) {
				for (int j = 0; j < secret_code_copy.size(); j++) {
					if (player_code_copy[i] == secret_code_copy[j]) {
						misplaced_digits++;
						player_code_copy[i] = 'X';
						secret_code_copy[j] = 'Y';
					}

				}
			}
```
The first loop discovers all the correctly placed characters of the code and replaces them so that the second loop does not interact with them. The nested loop is used to check each character of the user's code with the secret code individually in order to find the correct yet misplaced guesses. 
```C++
while ( (!guessed_code) && (num_guesses < MAX_GUESSES) )
```
The **while** loop shown above checks a flag variable to see if the code has been guessed while also checking if the amount of guesses has exceeded the allowed amount(denoted by a constant variable **MAX_GUESSES**). An additional **while** loop checks a basic flag variable(**game_over**) that controls whether the game continues, by simply flipping using a basic "Y/N" option at the end of each round.
## Trial Run Example

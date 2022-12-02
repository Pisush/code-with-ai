# Attempt 1

## ChatGPT Input Prompt 1.0
```
Write a Go program that reads from "input.txt" and solves this puzzle:

The Elves begin to set up camp on the beach. To decide whose tent gets to be closest to the snack storage, a giant Rock Paper Scissors tournament is already in progress.

Rock Paper Scissors is a game between two players. Each game contains many rounds; in each round, the players each simultaneously choose one of Rock, Paper, or Scissors using a hand shape. Then, a winner for that round is selected: Rock defeats Scissors, Scissors defeats Paper, and Paper defeats Rock. If both players choose the same shape, the round instead ends in a draw.

Appreciative of your help yesterday, one Elf gives you an encrypted strategy guide (your puzzle input) that they say will be sure to help you win. "The first column is what your opponent is going to play: A for Rock, B for Paper, and C for Scissors. The second column--" Suddenly, the Elf is called away to help with someone's tent.

The second column, you reason, must be what you should play in response: X for Rock, Y for Paper, and Z for Scissors. Winning every time would be suspicious, so the responses must have been carefully chosen.

The winner of the whole tournament is the player with the highest score. Your total score is the sum of your scores for each round. The score for a single round is the score for the shape you selected (1 for Rock, 2 for Paper, and 3 for Scissors) plus the score for the outcome of the round (0 if you lost, 3 if the round was a draw, and 6 if you won).

Since you can't be sure if the Elf is trying to help you or trick you, you should calculate the score you would get if you were to follow the strategy guide.

For example, suppose you were given the following strategy guide:

A Y
B X
C Z
This strategy guide predicts and recommends the following:

In the first round, your opponent will choose Rock (A), and you should choose Paper (Y). This ends in a win for you with a score of 8 (2 because you chose Paper + 6 because you won).
In the second round, your opponent will choose Paper (B), and you should choose Rock (X). This ends in a loss for you with a score of 1 (1 + 0).
The third round is a draw with both players choosing Scissors, giving you a score of 3 + 3 = 6.
In this example, if you were to follow the strategy guide, you would get a total score of 15 (8 + 1 + 6).

What would your total score be if everything goes exactly according to your strategy guide?
```

## ChatGPT Output 1.0
```
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	// Open the input file.
	file, err := os.Open("input.txt")
	if err != nil {
		fmt.Println(err)
		return
	}
	defer file.Close()

	// Create a new scanner to read the input file.
	scanner := bufio.NewScanner(file)

	// Initialize the total score.
	var score int

	// Read and process each line in the input file.
	for scanner.Scan() {
		line := scanner.Text()

		// Parse the opponent's and your choices.
		opponent := line[0]
		you := line[1]

		// Calculate the score for this round.
		roundScore := 0
		if opponent == you {
			// It's a draw.
			roundScore = 3
		} else if (opponent == 'A' && you == 'Z') || (opponent == 'B' && you == 'Y') || (opponent == 'C' && you == 'X') {
			// You win.
			roundScore = 6
		} else {
			// You lose.
			roundScore = 0
		}

		// Add the score for this round to the total score.
		score += roundScore

		// Add the score for your choice to the total score.
		if you == 'X' {
			score += 1
		} else if you == 'Y' {
			score += 2
		} else if you == 'Z' {
			score += 3
		}
	}

	// Print the total score.
	fmt.Println(score)
}
```

## My Feedback 1.0
Got `0`, unfortunately it's not the right answer.


## ChatGPT Input Prompt 1.1
```
The above code is not correct, please fix it
```

## ChatGPT Output 1.1
```
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	// Open the input file.
	file, err := os.Open("input.txt")
	if err != nil {
		fmt.Println(err)
		return
	}
	defer file.Close()

	// Create a new scanner to read the input file.
	scanner := bufio.NewScanner(file)

	// Initialize the total score.
	var score int

	// Read and process each line in the input file.
	for scanner.Scan() {
		line := scanner.Text()

		// Parse the opponent's and your choices.
		opponent := line[0]
		you := line[1]

		// Calculate the score for this round.
		roundScore := 0
		if opponent == you {
			// It's a draw.
			roundScore = 3
		} else if (opponent == 'A' && you == 'Y') || (opponent == 'B' && you == 'Z') || (opponent == 'C' && you == 'X') {
			// You win.
			roundScore = 6
		} else {
			// You lose.
			roundScore = 0
		}

		// Add the score for this round to the total score.
		score += roundScore

		// Add the score for your choice to the total score.
		if you == 'X' {
			score += 1
		} else if you == 'Y' {
			score += 2
		} else if you == 'Z' {
			score += 3
		}
	}

	// Print the total score.
	fmt.Println(score)
}
```

## My Feedback 1.1
Unfortunately, it was again 0.
Maybe it can rephrase the task better, so it can better understand what to do.


## ChatGPT Input Prompt 1.2
```
Rephrase the code puzzle, so you can solve it better:

The Elves begin to set up camp on the beach. To decide whose tent gets to be closest to the snack storage, a giant Rock Paper Scissors tournament is already in progress.

Rock Paper Scissors is a game between two players. Each game contains many rounds; in each round, the players each simultaneously choose one of Rock, Paper, or Scissors using a hand shape. Then, a winner for that round is selected: Rock defeats Scissors, Scissors defeats Paper, and Paper defeats Rock. If both players choose the same shape, the round instead ends in a draw.

Appreciative of your help yesterday, one Elf gives you an encrypted strategy guide (your puzzle input) that they say will be sure to help you win. "The first column is what your opponent is going to play: A for Rock, B for Paper, and C for Scissors. The second column--" Suddenly, the Elf is called away to help with someone's tent.

The second column, you reason, must be what you should play in response: X for Rock, Y for Paper, and Z for Scissors. Winning every time would be suspicious, so the responses must have been carefully chosen.

The winner of the whole tournament is the player with the highest score. Your total score is the sum of your scores for each round. The score for a single round is the score for the shape you selected (1 for Rock, 2 for Paper, and 3 for Scissors) plus the score for the outcome of the round (0 if you lost, 3 if the round was a draw, and 6 if you won).

Since you can't be sure if the Elf is trying to help you or trick you, you should calculate the score you would get if you were to follow the strategy guide.

For example, suppose you were given the following strategy guide:

A Y
B X
C Z
This strategy guide predicts and recommends the following:

In the first round, your opponent will choose Rock (A), and you should choose Paper (Y). This ends in a win for you with a score of 8 (2 because you chose Paper + 6 because you won).
In the second round, your opponent will choose Paper (B), and you should choose Rock (X). This ends in a loss for you with a score of 1 (1 + 0).
The third round is a draw with both players choosing Scissors, giving you a score of 3 + 3 = 6.
In this example, if you were to follow the strategy guide, you would get a total score of 15 (8 + 1 + 6).

What would your total score be if everything goes exactly according to your strategy guide?
```

## ChatGPT Output 1.2
```
An error occurred. If this issue persists please contact us through our help center at help.openai.com.
```

Retrying:
```
To solve this puzzle, we need to write a Go program that reads a strategy guide from a file and calculates the total score for following that strategy. The strategy guide consists of multiple lines, each representing a round of the Rock Paper Scissors game. The first character on each line represents the opponent's choice and the second character represents your choice.

The program can start by opening the input file and creating a scanner to read its contents. We can then initialize a variable to hold the total score and use a loop to read and process each line in the file.

For each line, we can parse the opponent's and your choices and calculate the score for that round. If the opponent's and your choices are the same, it's a draw and the round score is 3. If your choice defeats the opponent's choice, you win and the round score is 6. Otherwise, you lose and the round score is 0.

We can then add the round score to the total score, and add the score for your choice to the total score as well. Rock is worth 1 point, Paper is worth 2 points, and Scissors is worth 3 points.

After processing all the lines in the file, we can print the total score to the console. This completes the program.

Here is the final version of the Go program that solves the puzzle:


package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	// Open the input file.
	file, err := os.Open("input.txt")
	if err != nil {
		fmt.Println(err)
		return
	}
	defer file.Close()

	// Create a new scanner to read the input file.
	scanner := bufio.NewScanner(file)

	// Initialize the total score.
	var score int

	// Read and process each line in the input file.
	for scanner.Scan() {
		line := scanner.Text()

		// Parse the opponent's and your choices.
		opponent := line[0]
		you := line[1]

		// Calculate the score for this round.
		roundScore := 0
		if opponent == you {
			// It's a draw.
			roundScore = 3
		} else if (opponent == 'A' && you == 'Y') || (opponent == 'B' && you == 'Z') || (opponent == 'C' && you == 'X') {
			// You win.
			roundScore = 6
		} else {
			// You lose.
			roundScore = 0
		}

		// Add the score for this round to the total score.
		score += roundScore

		// Add the score for your choice to the total score.
		if you == 'X' {
			score += 1
		} else if you == 'Y' {
			score += 2
		} else if you == 'Z' {
			score += 3
		}
	}

	// Print the total score.
	fmt.Println(score)
}
```

## My Feedback 1.2
Unfrotunately, it's still 0!

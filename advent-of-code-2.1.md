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

# Attempt 2
ChatGPT has hit the global rate limit, so switching back to DaVinci.

## DaVinci Input Prompt 2.0
```
Write Go code that reads from "input.txt" and solves this code puzzle:

The Elves begin to set up camp on the beach. To decide whose tent gets to be closest to the snack storage, a giant Rock Paper Scissors tournament is already in progress.

Rock Paper Scissors is a game between two players. Each game contains many rounds; in each round, the players each simultaneously choose one of Rock, Paper, or Scissors using a hand shape. Then, a winner for that round is selected: Rock defeats Scissors, Scissors defeats Paper, and Paper defeats Rock. If both players choose the same shape, the round instead ends in a draw.

Appreciative of your help yesterday, one Elf gives you an encrypted strategy guide (your puzzle input) that they say will be sure to help you win. "The first column is what your opponent is going to play: A for Rock, B for Paper, and C for Scissors. The second column--" Suddenly, the Elf is called away to help with someone's tent.

The second column, you reason, must be what you should play in response: X for Rock, Y for Paper, and Z for Scissors. Winning every time would be suspicious, so the responses must have been carefully chosen.

The winner of the whole tournament is the player with the highest score. Your total score is the sum of your scores for each round. The score for a single round is the score for the shape you selected (1 for Rock, 2 for Paper, and 3 for Scissors) plus the score for the outcome of the round (0 if you lost, 3 if the round was a draw, and 6 if you won).

Since you can't be sure if the Elf is trying to help you or trick you, you should calculate the score you would get if you were to follow the strategy guide.

What would your total score be if everything goes exactly according to your strategy guide?
```

## DaVinci Output 2.0

```
package main 

import (
	"bufio"
	"fmt"
	"io"
	"os"
)

func main() {
	// Open file and create a scanner
	file, err := os.Open("input.txt")
	if err != nil {
		fmt.Println(err)
		return
	}
	defer file.Close()

	reader := bufio.NewReader(file)

	// Initialize variables 
	var totalScore int
	var opponentChoice rune
	var yourChoice rune

	// Read each line of the file
	for {
		// Read one line
		choices, _, err := reader.ReadRune()

		// Check if line is empty
		if err == io.EOF {
			break
		}

		// Determine opponent's choice
		if choices == 'A' {
			opponentChoice = 'R'
		} else if choices == 'B' {
			opponentChoice = 'P'
		} else if choices == 'C' {
			opponentChoice = 'S'
		}

		// Determine your choice
		yourChoice, _, err = reader.ReadRune()
		if yourChoice == 'X' {
			yourChoice = 'R'
		} else if yourChoice == 'Y' {
			yourChoice = 'P'
		} else if yourChoice == 'Z' {
			yourChoice = 'S'
		}

		// Calculate score
		if yourChoice == opponentChoice {
			totalScore += 3
		} else if (yourChoice == 'R' && opponentChoice == 'S') || (yourChoice == 'P' && opponentChoice == 'R') || (yourChoice == 'S' && opponentChoice == 'P') {
			totalScore += 6
		}
	}

	// Print total score
	fmt.Println(totalScore)
}
```

## My Feedback 2.0
Again I got a 0.
Trying again to do all the same, just change `Best Of` to be `4` again, instead of the default `1`.
Got `4857`, which is too low.

## DaVinci Input Prompt 2.1
Wrote after the code output, in order to keep the context:
```
The above code did not give the right answer.
Fix the code:
```

## DaVinci Output 2.1
```

package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	file, err := os.Open("input.txt")
	if err != nil {
		fmt.Println("Error opening file:", err)
		return
	}
	defer file.Close()

	// use a scanner to read the file line by line
	scanner := bufio.NewScanner(file)

	totalScore := 0
	for scanner.Scan() {
		// read a line from the input file
		line := scanner.Text()
		// the opponent's move
		opponent := line[0]
		// your move
		you := line[1]
		// determine the score for the round
		score := 0
		if opponent == 'A' {
			// opponent plays rock
			if you == 'X' {
				score = 3
			} else if you == 'Y' {
				score = 6
			} else {
				score = 0
			}
		} else if opponent == 'B' {
			// opponent plays paper
			if you == 'X' {
				score = 0
			} else if you == 'Y' {
				score = 3
			} else {
				score = 6
			}
		} else {
			// opponent plays scissors
			if you == 'X' {
				score = 6
			} else if you == 'Y' {
				score = 0
			} else {
				score = 3
			}
		}
		// add the score for the shape you select to the score
		if you == 'X' {
			score += 1
		} else if you == 'Y' {
			score += 2
		} else {
			score += 3
		}
		// add the score to the total score
		totalScore += score
	}

	fmt.Println("Total Score:", totalScore)
}
```

## My Feedback 2.1
This time I got `12357`, which is too high.

## DaVinci Input Prompt 2.2
Responded in the end, still keeping the context, and still keeping `Best Of` at `4`.
```
The code above generated an answer that was wrong because it was too high, please correct the code.
```

## DaVinci Output 2.2
```
package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	file, err := os.Open("input.txt")
	if err != nil {
		fmt.Println("Error opening file:", err)
		return
	}
	defer file.Close()

	// use a scanner to read the file line by line
	scanner := bufio.NewScanner(file)

	totalScore := 0
	for scanner.Scan() {
		// read a line from the input file
		line := scanner.Text()
		// the opponent's move
		opponent := line[0]
		// your move
		you := line[1]
		// determine the score for the round
		score := 0
		if opponent == 'A' {
			// opponent plays rock
			if you == 'X' {
				score = 3
			} else if you == 'Y' {
				score = 6
			} else {
				score = 0
			}
		} else if opponent == 'B' {
			// opponent plays paper
			if you == 'X' {
				score = 0
			} else if you == 'Y' {
				score = 3
			} else {
				score = 6
			}
		} else {
			// opponent plays scissors
			if you == 'X' {
				score = 6
			} else if you == 'Y' {
				score = 0
			} else {
				score = 3
			}
		}
		// add the score for the shape you select to the score
		if you == 'X' {
			score += 1
		} else if you == 'Y' {
			score += 2
		} else if you == 'Z' {
			score += 3
		}
		// add the score to the total score
		totalScore += score
	}

	fmt.Println("Total Score:", totalScore)
}
```

## My Feedback 2.2
Got `4857`, as last time.



## DaVinci Input Prompt 2.3
Starting over. I've added a line in the beginning, dropped the example, and edited a bit the instruction from the puzzle:

```
Here is a code puzzle:


The Elves begin to set up camp on the beach. To decide whose tent gets to be closest to the snack storage, a giant Rock Paper Scissors tournament is already in progress.

Rock Paper Scissors is a game between two players. Each game contains many rounds; in each round, the players each simultaneously choose one of Rock, Paper, or Scissors using a hand shape. Then, a winner for that round is selected: Rock defeats Scissors, Scissors defeats Paper, and Paper defeats Rock. If both players choose the same shape, the round instead ends in a draw.

Appreciative of your help yesterday, one Elf gives you an encrypted strategy guide (your puzzle input) that they say will be sure to help you win. "The first column is what your opponent is going to play: A for Rock, B for Paper, and C for Scissors. The second column--" Suddenly, the Elf is called away to help with someone's tent.

The second column, you reason, must be what you should play in response: X for Rock, Y for Paper, and Z for Scissors. Winning every time would be suspicious, so the responses must have been carefully chosen.

The winner of the whole tournament is the player with the highest score. Your total score is the sum of your scores for each round. The score for a single round is the score for the shape you selected (1 for Rock, 2 for Paper, and 3 for Scissors) plus the score for the outcome of the round (0 if you lost, 3 if the round was a draw, and 6 if you won).

Since you can't be sure if the Elf is trying to help you or trick you, you should calculate the score you would get if you were to follow the strategy guide.


Write a Go program that reads from "input.txt" and calculates the total score if everything goes exactly according to the strategy guide.
```

## DaVinci Output 2.3
```
package main

import (
	"bufio"
	"fmt"
	"os"
	"strings"
)

func main() {
	file, _ := os.Open("input.txt")
	scanner := bufio.NewScanner(file)
	
	totalScore := 0
	for scanner.Scan() {
		// Get the opponent's choice
		opponentChoice := string(scanner.Text()[0])

		// Get the player's choice
		playerChoice := string(scanner.Text()[1])
		
		// Calculate the score for this round
		var roundScore int
		if opponentChoice == playerChoice {
			// Draw
			roundScore = 3
		} else if (strings.ToLower(opponentChoice) == "r" && strings.ToLower(playerChoice) == "s") || (strings.ToLower(opponentChoice) == "p" && strings.ToLower(playerChoice) == "r") || (strings.ToLower(opponentChoice) == "s" && strings.ToLower(playerChoice) == "p") {
			// Win
			roundScore = 6
		} else {
			// Lose
			roundScore = 0
		}
		
		// Add the score for this round to the total score
		switch strings.ToLower(playerChoice) {
		case "r":
			totalScore += roundScore + 1
		case "p":
			totalScore += roundScore + 2
		case "s":
			totalScore += roundScore + 3
		}
	}
	
	fmt.Println("Total Score:", totalScore)
}
```

## My Feedback 2.3
`Total Score: 0`.


## DaVinci Output 2.4
```
Here is a code puzzle, rephrase it:


The Elves begin to set up camp on the beach. To decide whose tent gets to be closest to the snack storage, a giant Rock Paper Scissors tournament is already in progress.

Rock Paper Scissors is a game between two players. Each game contains many rounds; in each round, the players each simultaneously choose one of Rock, Paper, or Scissors using a hand shape. Then, a winner for that round is selected: Rock defeats Scissors, Scissors defeats Paper, and Paper defeats Rock. If both players choose the same shape, the round instead ends in a draw.

Appreciative of your help yesterday, one Elf gives you an encrypted strategy guide (your puzzle input) that they say will be sure to help you win. "The first column is what your opponent is going to play: A for Rock, B for Paper, and C for Scissors. The second column--" Suddenly, the Elf is called away to help with someone's tent.

The second column, you reason, must be what you should play in response: X for Rock, Y for Paper, and Z for Scissors. Winning every time would be suspicious, so the responses must have been carefully chosen.

The winner of the whole tournament is the player with the highest score. Your total score is the sum of your scores for each round. The score for a single round is the score for the shape you selected (1 for Rock, 2 for Paper, and 3 for Scissors) plus the score for the outcome of the round (0 if you lost, 3 if the round was a draw, and 6 if you won).

Since you can't be sure if the Elf is trying to help you or trick you, you should calculate the score you would get if you were to follow the strategy guide.


Write Go code reading from "input.txt", and calculates the total score:
```

## DaVinci Output 2.4
```
package main

import (
    "fmt"
    "io/ioutil"
    "strconv"
    "strings"
)

func main() {
    // Read from file
    b, err := ioutil.ReadFile("input.txt")
    if err != nil {
        fmt.Print(err)
    }

    // Split lines
    lines := strings.Split(string(b), "\n")

    // Initialize score
    score := 0

    // Iterate over lines
    for _, line := range lines {
        // Split line into opponent selection and strategy
        lineSlice := strings.Split(line, " ")

        // Get opponent selection
        opponentSelection := lineSlice[0]

        // Get strategy
        strategy := lineSlice[1]

        // Determine the score for the shape selected
        shapeScore := 0
        if strategy == "X" {
            shapeScore = 1
        } else if strategy == "Y" {
            shapeScore = 2
        } else if strategy == "Z" {
            shapeScore = 3
        }

        // Determine the score for the outcome of the round
        outcomeScore := 0
        if (opponentSelection == "A" && strategy == "X") || (opponentSelection == "B" && strategy == "Y") || (opponentSelection == "C" && strategy == "Z") {
            outcomeScore = 6
        } else if opponentSelection == strategy {
            outcomeScore = 3
        }

        // Add the scores together
        roundScore, err := strconv.Atoi(fmt.Sprintf("%d", shapeScore+outcomeScore))
        if err != nil {
            fmt.Print(err)
        }
        score += roundScore
    }

    // Print the total score
    fmt.Printf("Total score: %d", score)
}
```

## My Feedback 2.4
`Total score: 14862`.
In 2.1 I already fot the feedback that `12357` is too high, so this won't work either.

## DaVinci Input Prompt 2.5
`The answer generated by this code is too high, correct the code.`

## DaVinci Output 2.5
```
package main

import (
    "fmt"
    "io/ioutil"
    "strconv"
    "strings"
)

func main() {
    // Read from file
    b, err := ioutil.ReadFile("input.txt")
    if err != nil {
        fmt.Print(err)
    }

    // Split lines
    lines := strings.Split(string(b), "\n")

    // Initialize score
    score := 0

    // Iterate over lines
    for _, line := range lines {
        // Split line into opponent selection and strategy
        lineSlice := strings.Split(line, " ")

        // Get opponent selection
        opponentSelection := lineSlice[0]

        // Get strategy
        strategy := lineSlice[1]

        // Determine the score for the shape selected
        shapeScore := 0
        if strategy == "X" {
            shapeScore = 1
        } else if strategy == "Y" {
            shapeScore = 2
        } else if strategy == "Z" {
            shapeScore = 3
        }

        // Determine the score for the outcome of the round
        outcomeScore := 0
        if (opponentSelection == "A" && strategy == "X") || (opponentSelection == "B" && strategy == "Y") || (opponentSelection == "C" && strategy == "Z") {
            outcomeScore = 6
        } else if opponentSelection == strategy {
            outcomeScore = 0
        } else {
            outcomeScore = -3
        }

        // Add the scores together
        roundScore, err := strconv.Atoi(fmt.Sprintf("%d", shapeScore+outcomeScore))
        if err != nil {
            fmt.Print(err)
        }
        score += roundScore
    }

    // Print the total score
    fmt.Printf("Total score: %d", score)
}
```

## DaVinci Input Prompt 2.5
`Total score: 12852`. Too high.


## DaVinci Input Prompt 2.6
Dialed down the `Temprature` from `0.7` to `0.16`.

```
Here is a code puzzle:


The Elves begin to set up camp on the beach. To decide whose tent gets to be closest to the snack storage, a giant Rock Paper Scissors tournament is already in progress.

Rock Paper Scissors is a game between two players. Each game contains many rounds; in each round, the players each simultaneously choose one of Rock, Paper, or Scissors using a hand shape. Then, a winner for that round is selected: Rock defeats Scissors, Scissors defeats Paper, and Paper defeats Rock. If both players choose the same shape, the round instead ends in a draw.

Appreciative of your help yesterday, one Elf gives you an encrypted strategy guide (your puzzle input) that they say will be sure to help you win. "The first column is what your opponent is going to play: A for Rock, B for Paper, and C for Scissors. The second column--" Suddenly, the Elf is called away to help with someone's tent.

The second column, you reason, must be what you should play in response: X for Rock, Y for Paper, and Z for Scissors. Winning every time would be suspicious, so the responses must have been carefully chosen.

The winner of the whole tournament is the player with the highest score. Your total score is the sum of your scores for each round. The score for a single round is the score for the shape you selected (1 for Rock, 2 for Paper, and 3 for Scissors) plus the score for the outcome of the round (0 if you lost, 3 if the round was a draw, and 6 if you won).

Since you can't be sure if the Elf is trying to help you or trick you, you should calculate the score you would get if you were to follow the strategy guide.


Write Go code reading from "input.txt", and calculates the total score.
```
## DaVinci Input Prompt 2.6
```

package main

import (
	"bufio"
	"fmt"
	"os"
)

func main() {
	file, err := os.Open("input.txt")
	if err != nil {
		fmt.Println(err)
		return
	}
	defer file.Close()

	scanner := bufio.NewScanner(file)
	totalScore := 0
	for scanner.Scan() {
		line := scanner.Text()
		opponentMove := line[0]
		yourMove := line[1]
		score := 0
		switch yourMove {
		case 'X':
			if opponentMove == 'A' {
				score = 6
			} else if opponentMove == 'B' {
				score = 1
			} else if opponentMove == 'C' {
				score = 3
			}
		case 'Y':
			if opponentMove == 'A' {
				score = 3
			} else if opponentMove == 'B' {
				score = 6
			} else if opponentMove == 'C' {
				score = 1
			}
		case 'Z':
			if opponentMove == 'A' {
				score = 1
			} else if opponentMove == 'B' {
				score = 3
			} else if opponentMove == 'C' {
				score = 6
			}
		}
		totalScore += score
	}
	fmt.Println("Total score:", totalScore)
}
```

## DaVinci Input Prompt 2.6
This yields 0.

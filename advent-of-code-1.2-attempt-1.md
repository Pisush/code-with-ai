# Attempt 1

## DaVinci Input Prompt 1.0

```
This is a code puzzle:

--- Day 1: Calorie Counting ---
Santa's reindeer typically eat regular reindeer food, but they need a lot of magical energy to deliver presents on Christmas. For that, their favorite snack is a special type of star fruit that only grows deep in the jungle. The Elves have brought you on their annual expedition to the grove where the fruit grows.

To supply enough magical energy, the expedition needs to retrieve a minimum of fifty stars by December 25th. Although the Elves assure you that the grove has plenty of fruit, you decide to grab any fruit you see along the way, just in case.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the Advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants one star. Good luck!

The jungle must be too overgrown and difficult to navigate in vehicles or access from the air; the Elves' expedition traditionally goes on foot. As your boats approach land, the Elves begin taking inventory of their supplies. One important consideration is food - in particular, the number of Calories each Elf is carrying (your puzzle input).

The Elves take turns writing down the number of Calories contained by the various meals, snacks, rations, etc. that they've brought with them, one item per line. Each Elf separates their own inventory from the previous Elf's inventory (if any) by a blank line.

For example, suppose the Elves finish writing their items' Calories and end up with the following list:

1000
2000
3000

4000

5000
6000

7000
8000
9000

10000
This list represents the Calories of the food carried by five Elves:

The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
The second Elf is carrying one food item with 4000 Calories.
The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
The fifth Elf is carrying one food item with 10000 Calories.
In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example above, this is 24000 (carried by the fourth Elf).

Find the Elf carrying the most Calories. How many total Calories is that Elf carrying?

Your puzzle answer was 69883.

The first half of this puzzle is complete! It provides one gold star: *

--- Part Two ---
By the time you calculate the answer to the Elves' question, they've already realized that the Elf carrying the most Calories of food might eventually run out of snacks.

To avoid this unacceptable situation, the Elves would instead like to know the total Calories carried by the top three Elves carrying the most Calories. That way, even if one of those Elves runs out of snacks, they still have two backups.

In the example above, the top three Elves are the fourth Elf (with 24000 Calories), then the third Elf (with 11000 Calories), then the fifth Elf (with 10000 Calories). The sum of the Calories carried by these three elves is 45000.

Find the top three Elves carrying the most Calories. How many Calories are those Elves carrying in total?


Go code that reads my input from "input.txt" and solves this puzzle:
/`/`/`go
```

## DaVinci Output 1.0
```
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	// Open the file
	file, err := os.Open("input.txt")
	if err != nil {
		panic(err)
	}
	defer file.Close()

	// Read the lines
	scanner := bufio.NewScanner(file)

	// Create a slice to hold the calories
	calories := []int{}

	// Iterate through the lines
	for scanner.Scan() {
		// Convert each line to an integer
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			panic(err)
		}
		// Add the calorie to the slice
		calories = append(calories, calorie)
	}

	// Sort the calories from high to low
	sort.Sort(sort.Reverse(sort.IntSlice(calories)))

	// Calculate the total of the top three
	total := 0
	for i := 0; i < 3; i++ {
		total += calories[i]
	}

	// Print the total
	fmt.Println(total)
}
/`/`/`
```

## My Feedback 1.0
This again had a problem with an unimported `strconv`, as in [part 1 attempt 2](https://github.com/Pisush/code-with-ai/blob/main/advent-of-code-1.1-attempt-2.md).

But this time importing did not solve the problem:
```
$ make run
go build -o main .
./main
panic: strconv.Atoi: parsing "": invalid syntax

goroutine 1 [running]:
main.main()
    /home/runner/AoC22-12-1/main.go:30 +0x29a
make: *** [Makefile:3: run] Error 2
exit status 2
```

## DaVinci Input Prompt 1.1
My goal remains to solve it without reading, so I'll report the error and let's see if it's fixed, by just adding this to the end of the prompt:

```
The above is failing with the error:
panic: strconv.Atoi: parsing "": invalid syntax

Correct the code:
```

So now the whole prompt looks like this:

```
This is a code puzzle:

--- Day 1: Calorie Counting ---
Santa's reindeer typically eat regular reindeer food, but they need a lot of magical energy to deliver presents on Christmas. For that, their favorite snack is a special type of star fruit that only grows deep in the jungle. The Elves have brought you on their annual expedition to the grove where the fruit grows.

To supply enough magical energy, the expedition needs to retrieve a minimum of fifty stars by December 25th. Although the Elves assure you that the grove has plenty of fruit, you decide to grab any fruit you see along the way, just in case.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the Advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants one star. Good luck!

The jungle must be too overgrown and difficult to navigate in vehicles or access from the air; the Elves' expedition traditionally goes on foot. As your boats approach land, the Elves begin taking inventory of their supplies. One important consideration is food - in particular, the number of Calories each Elf is carrying (your puzzle input).

The Elves take turns writing down the number of Calories contained by the various meals, snacks, rations, etc. that they've brought with them, one item per line. Each Elf separates their own inventory from the previous Elf's inventory (if any) by a blank line.

For example, suppose the Elves finish writing their items' Calories and end up with the following list:

1000
2000
3000

4000

5000
6000

7000
8000
9000

10000
This list represents the Calories of the food carried by five Elves:

The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
The second Elf is carrying one food item with 4000 Calories.
The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
The fifth Elf is carrying one food item with 10000 Calories.
In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example above, this is 24000 (carried by the fourth Elf).

Find the Elf carrying the most Calories. How many total Calories is that Elf carrying?

Your puzzle answer was 69883.

The first half of this puzzle is complete! It provides one gold star: *

--- Part Two ---
By the time you calculate the answer to the Elves' question, they've already realized that the Elf carrying the most Calories of food might eventually run out of snacks.

To avoid this unacceptable situation, the Elves would instead like to know the total Calories carried by the top three Elves carrying the most Calories. That way, even if one of those Elves runs out of snacks, they still have two backups.

In the example above, the top three Elves are the fourth Elf (with 24000 Calories), then the third Elf (with 11000 Calories), then the fifth Elf (with 10000 Calories). The sum of the Calories carried by these three elves is 45000.

Find the top three Elves carrying the most Calories. How many Calories are those Elves carrying in total?


Go code that reads my input from "input.txt" and solves this puzzle:
/`/`/`go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	// Open the file
	file, err := os.Open("input.txt")
	if err != nil {
		panic(err)
	}
	defer file.Close()

	// Read the lines
	scanner := bufio.NewScanner(file)

	// Create a slice to hold the calories
	calories := []int{}

	// Iterate through the lines
	for scanner.Scan() {
		// Convert each line to an integer
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			panic(err)
		}
		// Add the calorie to the slice
		calories = append(calories, calorie)
	}

	// Sort the calories from high to low
	sort.Sort(sort.Reverse(sort.IntSlice(calories)))

	// Calculate the total of the top three
	total := 0
	for i := 0; i < 3; i++ {
		total += calories[i]
	}

	// Print the total
	fmt.Println(total)
}
/`/`/`

The above is failing with the error:
panic: strconv.Atoi: parsing "": invalid syntax

Correct the code:
```

## DaVinci Output 1.1

```
package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
	"sort"
)

func main() {
	// Open the file
	file, err := os.Open("input.txt")
	if err != nil {
		panic(err)
	}
	defer file.Close()

	// Read the lines
	scanner := bufio.NewScanner(file)

	// Create a slice to hold the calories
	calories := []int{}

	// Iterate through the lines
	for scanner.Scan() {
		// Skip empty lines
		if scanner.Text() == "" {
			continue
		}
		// Convert each line to an integer
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			panic(err)
		}
		// Add the calorie to the slice
		calories = append(calories, calorie)
	}

	// Sort the calories from high to low
	sort.Sort(sort.Reverse(sort.IntSlice(calories)))

	// Calculate the total of the top three
	total := 0
	for i := 0; i < 3; i++ {
		total += calories[i]
	}

	// Print the total
	fmt.Println(total)
}
```

## My Feedback 1.1

First of all - great that it did import `strconv` this time.
And it works!
``` 
$ make run
go build -o main .
./main
185100
```

But unfortunately it's not the right answer:
```
That's not the right answer; your answer is too low. 
If you're stuck, make sure you're using the full input data; 
there are also some general tips on the about page, or you can ask for hints on the subreddit. 
Please wait one minute before trying again. (You guessed 185100.) [Return to Day 1]
```

## DaVinci Input Prompt 1.2

Let's see if I'll get away with just reporting the mistake. So I am adding this at the end of the prompt, which by now looks like a chat:

```
The code did not product the right answer, it was too low.
Correct the code:
```

Now the entire prompt is:
```
This is a code puzzle:

--- Day 1: Calorie Counting ---
Santa's reindeer typically eat regular reindeer food, but they need a lot of magical energy to deliver presents on Christmas. For that, their favorite snack is a special type of star fruit that only grows deep in the jungle. The Elves have brought you on their annual expedition to the grove where the fruit grows.

To supply enough magical energy, the expedition needs to retrieve a minimum of fifty stars by December 25th. Although the Elves assure you that the grove has plenty of fruit, you decide to grab any fruit you see along the way, just in case.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the Advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants one star. Good luck!

The jungle must be too overgrown and difficult to navigate in vehicles or access from the air; the Elves' expedition traditionally goes on foot. As your boats approach land, the Elves begin taking inventory of their supplies. One important consideration is food - in particular, the number of Calories each Elf is carrying (your puzzle input).

The Elves take turns writing down the number of Calories contained by the various meals, snacks, rations, etc. that they've brought with them, one item per line. Each Elf separates their own inventory from the previous Elf's inventory (if any) by a blank line.

For example, suppose the Elves finish writing their items' Calories and end up with the following list:

1000
2000
3000

4000

5000
6000

7000
8000
9000

10000
This list represents the Calories of the food carried by five Elves:

The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
The second Elf is carrying one food item with 4000 Calories.
The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
The fifth Elf is carrying one food item with 10000 Calories.
In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example above, this is 24000 (carried by the fourth Elf).

Find the Elf carrying the most Calories. How many total Calories is that Elf carrying?

Your puzzle answer was 69883.

The first half of this puzzle is complete! It provides one gold star: *

--- Part Two ---
By the time you calculate the answer to the Elves' question, they've already realized that the Elf carrying the most Calories of food might eventually run out of snacks.

To avoid this unacceptable situation, the Elves would instead like to know the total Calories carried by the top three Elves carrying the most Calories. That way, even if one of those Elves runs out of snacks, they still have two backups.

In the example above, the top three Elves are the fourth Elf (with 24000 Calories), then the third Elf (with 11000 Calories), then the fifth Elf (with 10000 Calories). The sum of the Calories carried by these three elves is 45000.

Find the top three Elves carrying the most Calories. How many Calories are those Elves carrying in total?


Go code that reads my input from "input.txt" and solves this puzzle:
/`/`/`go
package main

import (
	"bufio"
	"fmt"
	"os"
	"sort"
)

func main() {
	// Open the file
	file, err := os.Open("input.txt")
	if err != nil {
		panic(err)
	}
	defer file.Close()

	// Read the lines
	scanner := bufio.NewScanner(file)

	// Create a slice to hold the calories
	calories := []int{}

	// Iterate through the lines
	for scanner.Scan() {
		// Convert each line to an integer
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			panic(err)
		}
		// Add the calorie to the slice
		calories = append(calories, calorie)
	}

	// Sort the calories from high to low
	sort.Sort(sort.Reverse(sort.IntSlice(calories)))

	// Calculate the total of the top three
	total := 0
	for i := 0; i < 3; i++ {
		total += calories[i]
	}

	// Print the total
	fmt.Println(total)
}
/`/`/`

The above is failing with the error:
panic: strconv.Atoi: parsing "": invalid syntax

Correct the code:

package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
	"sort"
)

func main() {
	// Open the file
	file, err := os.Open("input.txt")
	if err != nil {
		panic(err)
	}
	defer file.Close()

	// Read the lines
	scanner := bufio.NewScanner(file)

	// Create a slice to hold the calories
	calories := []int{}

	// Iterate through the lines
	for scanner.Scan() {
		// Skip empty lines
		if scanner.Text() == "" {
			continue
		}
		// Convert each line to an integer
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			panic(err)
		}
		// Add the calorie to the slice
		calories = append(calories, calorie)
	}

	// Sort the calories from high to low
	sort.Sort(sort.Reverse(sort.IntSlice(calories)))

	// Calculate the total of the top three
	total := 0
	for i := 0; i < 3; i++ {
		total += calories[i]
	}

	// Print the total
	fmt.Println(total)
}


The code did not product the right answer, it was too low.
Correct the code:
```

## DaVinci Output 1.2
```
package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
	"sort"
)

func main() {
	// Open the file
	file, err := os.Open("input.txt")
	if err != nil {
		panic(err)
	}
	defer file.Close()

	// Read the lines
	scanner := bufio.NewScanner(file)

	// Create a slice to hold the calories
	calories := []int{}

	// Iterate through the lines
	for scanner.Scan() {
		// Skip empty lines
		if scanner.Text() == "" {
			continue
		}
		// Convert each line to an integer
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			panic(err)
		}
		// Add the calorie to the slice
		calories = append(calories, calorie)
	}

	// Sort the calories from high to low
	sort.Slice(calories, func(i, j int) bool {
		return calories[i] > calories[j]
	})

	// Calculate the total of the top three
	total := 0
	for i := 0; i < 3; i++ {
		total += calories[i]
	}

	// Print the total
	fmt.Println(total)
}
```

## My Feedback 1.2

This unfrotunately produced the same number, which we already know is wrong:
```
$ make run
go build -o main .
./main
185100
```


## DaVinci Input Prompt 1.3

Adding this to the end of the file:

```
This code does is not correct.
Write another Go code to solve the puzzle.
```

Won't copy the entire prompt again because it's long and the point is clear.

## DaVinci Output 1.3

```
package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
)

func main() {
	// Open the file
	file, err := os.Open("input.txt")
	if err != nil {
		panic(err)
	}
	defer file.Close()

	// Read the lines
	scanner := bufio.NewScanner(file)

	// Create a variable to store the max Calories
	maxCalories := 0

	// Iterate through the lines
	for scanner.Scan() {
		// Skip empty lines
		if scanner.Text() == "" {
			continue
		}
		// Convert each line to an integer
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			panic(err)
		}
		// Get the max Calories
		if calorie > maxCalories {
			maxCalories = calorie
		}
	}

	// Print the max Calories
	fmt.Println(maxCalories)
}
```

## My Feedback 1.3
It compiles, but the output is even lower than the previous one, which was already too low:
```
$ make run
go build -o main .
./main
69727
```

And indeed it's not the right answer:
```
That's not the right answer; 
your answer is too low. 
If you're stuck, make sure you're using the full input data; 
there are also some general tips on the about page, or you can ask for hints on the subreddit. 
Please wait one minute before trying again. (You guessed 69727.) [Return to Day 1]
```

## DaVinci Input Prompt 1.4

At this point I gave a bit of guidance about the input structure, which is the bare minimum I could do. 
Still trying to not read the exercise.
```
The above code does not solve the puzzle.
Please solve again, taking into consideration that the input file has a newline as a separator.
```

## DaVinci Output 1.4
```

package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
	"sort"
)

func main() {
	// Open the file
	file, err := os.Open("input.txt")
	if err != nil {
		panic(err)
	}
	defer file.Close()

	// Read the lines
	scanner := bufio.NewScanner(file)

	// Create a slice to hold the calories
	calories := []int{}

	// Iterate through the lines
	for scanner.Scan() {
		// Skip empty lines
		line := scanner.Text()
		if line == "" {
			continue
		}
		// Convert each line to an integer
		calorie, err := strconv.Atoi(line)
		if err != nil {
			panic(err)
		}
		// Add the calorie to the slice
		calories = append(calories, calorie)
	}

	// Sort the calories from high to low
	sort.Slice(calories, func(i, j int) bool {
		return calories[i] > calories[j]
	})

	// Calculate the total of the top three
	total := 0
	for i := 0; i < 3; i++ {
		total += calories[i]
	}

	// Print the total
	fmt.Println(total)
}
```

## My Feedback 1.4
Unfortunately, got the same value as before, which I already know is not the answer:
```
$ make run
go build -o main .
./main
185100
```


# Attempt 2


## DaVinci Input Prompt 2.0

```
This is a code puzzle:


Santa's reindeer typically eat regular reindeer food, but they need a lot of magical energy to deliver presents on Christmas. For that, their favorite snack is a special type of star fruit that only grows deep in the jungle. The Elves have brought you on their annual expedition to the grove where the fruit grows.

To supply enough magical energy, the expedition needs to retrieve a minimum of fifty stars by December 25th. Although the Elves assure you that the grove has plenty of fruit, you decide to grab any fruit you see along the way, just in case.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the Advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants one star. Good luck!

The jungle must be too overgrown and difficult to navigate in vehicles or access from the air; the Elves' expedition traditionally goes on foot. As your boats approach land, the Elves begin taking inventory of their supplies. One important consideration is food - in particular, the number of Calories each Elf is carrying (your puzzle input).

The Elves take turns writing down the number of Calories contained by the various meals, snacks, rations, etc. that they've brought with them, one item per line. Each Elf separates their own inventory from the previous Elf's inventory (if any) by a blank line.

For example, suppose the Elves finish writing their items' Calories and end up with the following list:

1000
2000
3000

4000

5000
6000

7000
8000
9000

10000
This list represents the Calories of the food carried by five Elves:

The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
The second Elf is carrying one food item with 4000 Calories.
The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
The fifth Elf is carrying one food item with 10000 Calories.
In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example above, this is 24000 (carried by the fourth Elf).


The Elves would like to know the total Calories carried by the top three Elves carrying the most Calories. That way, even if one of those Elves runs out of snacks, they still have two backups.

In the example above, the top three Elves are the fourth Elf (with 24000 Calories), then the third Elf (with 11000 Calories), then the fifth Elf (with 10000 Calories). The sum of the Calories carried by these three elves is 45000.

Find the top three Elves carrying the most Calories. How many Calories are those Elves carrying in total?


Go code that reads from "input.txt" and solves this puzzle:
/`/`/`go
```

## DaVinci Output 2.0

```
package main

import "fmt"
import "os"
import "bufio"
import "sort"

func main() {
    // Read input from file
    file, err := os.Open("input.txt")
    if err != nil {
        panic(err)
    }
    defer file.Close()

    // Parse input
    scanner := bufio.NewScanner(file)
    calories := []int{}
    for scanner.Scan() {
        var calorie int
        _, err := fmt.Sscanf(scanner.Text(), "%d", &calorie)
        if err != nil {
            continue
        }
        calories = append(calories, calorie)
    }
    sort.Ints(calories)

    // Compute total Calories of top 3 carrying elves
    total := 0
    for i := len(calories) - 1; i > len(calories) - 4; i-- {
        total += calories[i]
    }
    fmt.Println(total)
}
```

## My Feedback 2.1
Unfortunately, again the wrong value. What a tricky exercise!
```
$ make run
./main
185100
```

# Attempt 3

## DaVinci Input Prompt 3.0

Let's try to reuse what works for part 1 of the challenge and just change the last line in the puzzl description, which is the goal statement:

```
This is a code puzzle:

--- Day 1: Calorie Counting ---
Santa's reindeer typically eat regular reindeer food, but they need a lot of magical energy to deliver presents on Christmas. For that, their favorite snack is a special type of star fruit that only grows deep in the jungle. The Elves have brought you on their annual expedition to the grove where the fruit grows.

To supply enough magical energy, the expedition needs to retrieve a minimum of fifty stars by December 25th. Although the Elves assure you that the grove has plenty of fruit, you decide to grab any fruit you see along the way, just in case.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the Advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants one star. Good luck!

The jungle must be too overgrown and difficult to navigate in vehicles or access from the air; the Elves' expedition traditionally goes on foot. As your boats approach land, the Elves begin taking inventory of their supplies. One important consideration is food - in particular, the number of Calories each Elf is carrying (your puzzle input).

The Elves take turns writing down the number of Calories contained by the various meals, snacks, rations, etc. that they've brought with them, one item per line. Each Elf separates their own inventory from the previous Elf's inventory (if any) by a blank line.

For example, suppose the Elves finish writing their items' Calories and end up with the following list:

1000
2000
3000

4000

5000
6000

7000
8000
9000

10000
This list represents the Calories of the food carried by five Elves:

The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
The second Elf is carrying one food item with 4000 Calories.
The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
The fifth Elf is carrying one food item with 10000 Calories.
In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example above, this is 24000 (carried by the fourth Elf).

Find the top three Elves carrying the most Calories. How many Calories are those Elves carrying in total? 


Go code that reads my input from "input.txt" and solves this puzzle:
/`/`/`go
```

## DaVinci Output 3.0
```
// open the input file
file, err := os.Open("input.txt")
if err != nil {
    log.Fatal(err)
}
defer file.Close()

// read the file line by line
scanner := bufio.NewScanner(file)

// keep track of the Elves and calories
elves := make(map[int]int)
maxCalories := 0

// loop through the lines and add the calories to each Elf
for scanner.Scan() {
    line := strings.TrimSpace(scanner.Text())
    if line == "" {
        continue
    }
    calories, err := strconv.Atoi(line)
    if err != nil {
        log.Fatal(err)
    }
    for elf, totalCalories := range elves {
        elves[elf] = totalCalories + calories
        if elves[elf] > maxCalories {
            maxCalories = elves[elf]
        }
    }
    elves[len(elves)] = calories
}

// find the top three Elves carrying the most Calories
topThreeElves := make([]int, 0, 3)
for elf, totalCalories := range elves {
    if totalCalories == maxCalories {
        topThreeElves = append(topThreeElves, elf)
    }
}

totalCalories := 0
for _, elf := range topThreeElves {
    totalCalories += elves[elf]
}
fmt.Println("The top three Elves are carrying", totalCalories, "Calories in total.")
```

## My Feedback 3.0

Interestingly, now only the code that goes into main is generated. 
First run gave an error of missing imports.
```
$ make run
go build -o main .
./main
The top three Elves are carrying 11135643 Calories in total.
```

Still not the right answer:
```
That's not the right answer; your answer is too high. 
If you're stuck, make sure you're using the full input data; 
there are also some general tips on the about page, or you can ask for hints on the subreddit. 
Please wait one minute before trying again. (You guessed 11135643.) [Return to Day 1]
```

# Attempt 4
## DaVinci Input Prompt 4.0

This is an attempt to reuse the solution from part 1, and asking to adjust that code for the second goal:
```
This is a code puzzle:

--- Day 1: Calorie Counting ---
Santa's reindeer typically eat regular reindeer food, but they need a lot of magical energy to deliver presents on Christmas. For that, their favorite snack is a special type of star fruit that only grows deep in the jungle. The Elves have brought you on their annual expedition to the grove where the fruit grows.

To supply enough magical energy, the expedition needs to retrieve a minimum of fifty stars by December 25th. Although the Elves assure you that the grove has plenty of fruit, you decide to grab any fruit you see along the way, just in case.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the Advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants one star. Good luck!

The jungle must be too overgrown and difficult to navigate in vehicles or access from the air; the Elves' expedition traditionally goes on foot. As your boats approach land, the Elves begin taking inventory of their supplies. One important consideration is food - in particular, the number of Calories each Elf is carrying (your puzzle input).

The Elves take turns writing down the number of Calories contained by the various meals, snacks, rations, etc. that they've brought with them, one item per line. Each Elf separates their own inventory from the previous Elf's inventory (if any) by a blank line.

For example, suppose the Elves finish writing their items' Calories and end up with the following list:

1000
2000
3000

4000

5000
6000

7000
8000
9000

10000
This list represents the Calories of the food carried by five Elves:

The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
The second Elf is carrying one food item with 4000 Calories.
The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
The fifth Elf is carrying one food item with 10000 Calories.
In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example above, this is 24000 (carried by the fourth Elf).

Find the Elf carrying the most Calories. How many total Calories is that Elf carrying?


Go code that reads my input from "input.txt" and solves this puzzle:
/`/`/`go
package main

import (
	"bufio"
	"fmt"
	"log"
	"os"
)

func main() {
	file, err := os.Open("input.txt")
	if err != nil {
		log.Fatal(err)
	}
	defer file.Close()

	var maxCalories int
	var currentCalories int
	scanner := bufio.NewScanner(file)
	for scanner.Scan() {
		if scanner.Text() == "" {
			if currentCalories > maxCalories {
				maxCalories = currentCalories
			}
			currentCalories = 0
			continue
		}
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			log.Fatal(err)
		}
		currentCalories += calorie
	}

	if currentCalories > maxCalories {
		maxCalories = currentCalories
	}

	fmt.Printf("The Elf carrying the most Calories is carrying %d Calories.\n", maxCalories)
}
/`/`/`

By the time you calculate the answer to the Elves' question, they've already realized that the Elf carrying the most Calories of food might eventually run out of snacks.

To avoid this unacceptable situation, the Elves would instead like to know the total Calories carried by the top three Elves carrying the most Calories. That way, even if one of those Elves runs out of snacks, they still have two backups.

In the example above, the top three Elves are the fourth Elf (with 24000 Calories), then the third Elf (with 11000 Calories), then the fifth Elf (with 10000 Calories). The sum of the Calories carried by these three elves is 45000.

Adjust the code to  find the top three Elves carrying the most Calories. How many Calories are those Elves carrying in total?
```

## DaVinci Output 4.0

```
package main

import (
	"bufio"
	"fmt"
	"log"
	"os"
	"sort"
)

func main() {
	file, err := os.Open("input.txt")
	if err != nil {
		log.Fatal(err)
	}
	defer file.Close()

	calorieMap := make(map[int]int)
	scanner := bufio.NewScanner(file)
	for scanner.Scan() {
		if scanner.Text() == "" {
			continue
		}
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			log.Fatal(err)
		}
		calorieMap[calorie]++
	}

	sortedCalories := make([]int, 0, len(calorieMap))
	for calorie := range calorieMap {
		sortedCalories = append(sortedCalories, calorie)
	}
	sort.Slice(sortedCalories, func(i, j int) bool { return sortedCalories[i] > sortedCalories[j] })

	var totalCalories int
	for i := 0; i < 3; i++ {
		totalCalories += sortedCalories[i]
	}

	fmt.Printf("The top three Elves carrying the most Calories are carrying %d Calories in total.\n", totalCalories)
}
```

## My Feedback 4.0
```
# make run
go build -o main .
./main
The top three Elves carrying the most Calories are carrying 185100 Calories in total.
```

Not only it's wrong, I am also getting a 5 min timeout:
```
That's not the right answer. If you're stuck, make sure you're using the full input data; there are also some general tips on the about page, or you can ask for hints on the subreddit. Because you have guessed incorrectly 4 times on this puzzle, please wait 5 minutes before trying again. (You guessed 185100.) [Return to Day 1]
```

# Attempt 5

## DaVinci Input Prompt 5.0:
```
Santa's reindeer typically eat regular reindeer food, but they need a lot of magical energy to deliver presents on Christmas. For that, their favorite snack is a special type of star fruit that only grows deep in the jungle. The Elves have brought you on their annual expedition to the grove where the fruit grows.

To supply enough magical energy, the expedition needs to retrieve a minimum of fifty stars by December 25th. Although the Elves assure you that the grove has plenty of fruit, you decide to grab any fruit you see along the way, just in case.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the Advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants one star. Good luck!

The jungle must be too overgrown and difficult to navigate in vehicles or access from the air; the Elves' expedition traditionally goes on foot. As your boats approach land, the Elves begin taking inventory of their supplies. One important consideration is food - in particular, the number of Calories each Elf is carrying (your puzzle input).

The Elves take turns writing down the number of Calories contained by the various meals, snacks, rations, etc. that they've brought with them, one item per line. Each Elf separates their own inventory from the previous Elf's inventory (if any) by a blank line.

For example, suppose the Elves finish writing their items' Calories and end up with the following list:

1000
2000
3000

4000

5000
6000

7000
8000
9000

10000
This list represents the Calories of the food carried by five Elves:

The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
The second Elf is carrying one food item with 4000 Calories.
The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
The fifth Elf is carrying one food item with 10000 Calories.
In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example above, this is 24000 (carried by the fourth Elf).

Find the Elf carrying the most Calories. How many total Calories is that Elf carrying?


Go code that reads my input from "input.txt" and solves this puzzle:
/`/`/`go
package main

import (
	"bufio"
	"fmt"
	"log"
	"os"
)

func main() {
	file, err := os.Open("input.txt")
	if err != nil {
		log.Fatal(err)
	}
	defer file.Close()

	var maxCalories int
	var currentCalories int
	scanner := bufio.NewScanner(file)
	for scanner.Scan() {
		if scanner.Text() == "" {
			if currentCalories > maxCalories {
				maxCalories = currentCalories
			}
			currentCalories = 0
			continue
		}
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			log.Fatal(err)
		}
		currentCalories += calorie
	}

	if currentCalories > maxCalories {
		maxCalories = currentCalories
	}

	fmt.Printf("The Elf carrying the most Calories is carrying %d Calories.\n", maxCalories)
}
/`/`/`

By the time you calculate the answer to the Elves' question, they've already realized that the Elf carrying the most Calories of food might eventually run out of snacks.

To avoid this unacceptable situation, the Elves would instead like to know the total Calories carried by the top three Elves carrying the most Calories. That way, even if one of those Elves runs out of snacks, they still have two backups.

In the example above, the top three Elves are the fourth Elf (with 24000 Calories), then the third Elf (with 11000 Calories), then the fifth Elf (with 10000 Calories). The sum of the Calories carried by these three elves is 45000.

Find the top three Elves carrying the most Calories. How many Calories are those Elves carrying in total?

Adjust the code to output the correct total:
```

## DaVinci Output 5.0:
```
/`/`/`go
package main

import (
	"bufio"
	"fmt"
	"log"
	"os"
	"sort"
)

func main() {
	file, err := os.Open("input.txt")
	if err != nil {
		log.Fatal(err)
	}
	defer file.Close()

	calorieMap := make(map[int]int)
	scanner := bufio.NewScanner(file)
	for scanner.Scan() {
		if scanner.Text() == "" {
			continue
		}
		calorie, err := strconv.Atoi(scanner.Text())
		if err != nil {
			log.Fatal(err)
		}
		calorieMap[calorie]++
	}

	var calories []int
	for calorie := range calorieMap {
		calories = append(calories, calorie)
	}
	sort.Sort(sort.Reverse(sort.IntSlice(calories)))

	var totalCalories int
	for i := 0; i < 3; i++ {
		totalCalories += calories[i]
	}

	fmt.Printf("The top three Elves carrying the most Calories are carrying %d Calories in total.\n", totalCalories)
}
/`/`/`
```

## My Input 5.0:
Still 185100, which is also wrong.

## DaVinci Input Prompt 5.1:
```
--- Day 1: Calorie Counting ---
Santa's reindeer typically eat regular reindeer food, but they need a lot of magical energy to deliver presents on Christmas. For that, their favorite snack is a special type of star fruit that only grows deep in the jungle. The Elves have brought you on their annual expedition to the grove where the fruit grows.

To supply enough magical energy, the expedition needs to retrieve a minimum of fifty stars by December 25th. Although the Elves assure you that the grove has plenty of fruit, you decide to grab any fruit you see along the way, just in case.

Collect stars by solving puzzles. Two puzzles will be made available on each day in the Advent calendar; the second puzzle is unlocked when you complete the first. Each puzzle grants one star. Good luck!

The jungle must be too overgrown and difficult to navigate in vehicles or access from the air; the Elves' expedition traditionally goes on foot. As your boats approach land, the Elves begin taking inventory of their supplies. One important consideration is food - in particular, the number of Calories each Elf is carrying (your puzzle input).

The Elves take turns writing down the number of Calories contained by the various meals, snacks, rations, etc. that they've brought with them, one item per line. Each Elf separates their own inventory from the previous Elf's inventory (if any) by a blank line.

For example, suppose the Elves finish writing their items' Calories and end up with the following list:

1000
2000
3000

4000

5000
6000

7000
8000
9000

10000
This list represents the Calories of the food carried by five Elves:

The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
The second Elf is carrying one food item with 4000 Calories.
The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
The fifth Elf is carrying one food item with 10000 Calories.
In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example 
above, this is 24000 (carried by the fourth Elf).

Find the Elf carrying the most Calories. How many total Calories is that Elf carrying?

Implement a solution in Go, read the calories from a textfile, each empty line means another Elf. Find the Elf carrying the most Calories. How many total Calories is that Elf carrying?



package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
)

func main() {
	// open file
	file, err := os.Open("calories.txt")
	if err != nil {
		fmt.Println(err)
		os.Exit(1)
	}
	defer file.Close()

	// read lines from file
	scanner := bufio.NewScanner(file)
	var caloriesByElf []int
	var calories int
	for scanner.Scan() {
		line := scanner.Text()
		if line == "" {
			caloriesByElf = append(caloriesByElf, calories)
			calories = 0
			continue
		}

		c, err := strconv.Atoi(line)
		if err != nil {
			fmt.Println(err)
			os.Exit(2)
		}
		calories += c
	}
	caloriesByElf = append(caloriesByElf, calories)

	// find elf with most calories
	var maxCalories int
	var maxElf int
	for i, c := range caloriesByElf {
		if c > maxCalories {
			maxCalories = c
			maxElf = i
		}
	}

	fmt.Printf("Elf %d has the most calories with %d\n", maxElf+1, maxCalories)
}

By the time you calculate the answer to the Elves' question, they've already realized that the Elf carrying the most Calories of food might eventually run out of snacks.

To avoid this unacceptable situation, the Elves would instead like to know the total Calories carried by the top three Elves carrying the most Calories. That way, even if one of those Elves runs out of snacks, they still have two backups.

In the example above, the top three Elves are the fourth Elf (with 24000 Calories), then the third Elf (with 11000 Calories), then the fifth Elf (with 10000 Calories). The sum of the Calories carried by these three elves is 45000.

Find the top three Elves carrying the most Calories. How many Calories are those Elves carrying in total?

Adjust the code to output the correct total:
```
And another big change is change the parameter `Best of` to the value `4` (previously: `1`).

## DaVinci Output 5.1:
```
package main

import (
	"bufio"
	"fmt"
	"os"
	"strconv"
)

func main() {
	// open file
	file, err := os.Open("calories.txt")
	if err != nil {
		fmt.Println(err)
		os.Exit(1)
	}
	defer file.Close()

	// read lines from file
	scanner := bufio.NewScanner(file)
	var caloriesByElf []int
	var calories int
	for scanner.Scan() {
		line := scanner.Text()
		if line == "" {
			caloriesByElf = append(caloriesByElf, calories)
			calories = 0
			continue
		}

		c, err := strconv.Atoi(line)
		if err != nil {
			fmt.Println(err)
			os.Exit(2)
		}
		calories += c
	}
	caloriesByElf = append(caloriesByElf, calories)

	// find elf with most calories
	var maxCalories int
	var maxElf int
	for i, c := range caloriesByElf {
		if c > maxCalories {
			maxCalories = c
			maxElf = i
		}
	}

	// find second and third highest calories
	var secondMaxCalories int
	var secondMaxElf int
	var thirdMaxCalories int
	var thirdMaxElf int
	for i, c := range caloriesByElf {
		if c > secondMaxCalories && i != maxElf {
			secondMaxCalories = c
			secondMaxElf = i
		}
	}
	for i, c := range caloriesByElf {
		if c > thirdMaxCalories && i != secondMaxElf && i != maxElf {
			thirdMaxCalories = c
			thirdMaxElf = i
		}
	}

	fmt.Printf("Top three Elves are %d, %d, %d with total calories of %d\n", maxElf+1, secondMaxElf+1, thirdMaxElf+1, maxCalories+secondMaxCalories+thirdMaxCalories)
}
```

## My Feedback 5.1:
Got `207576`. Let's try:
`That's the right answer! You are one gold star closer to collecting enough star fruit.`

Finally!

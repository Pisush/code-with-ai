TL;DR
Tried to solve without reading the exercise at all.

First fed the instructinos to OpenAI's DaVinci. Then to OpenAI'ss Codex. Then executed in Replit.

Did not get the right answer.

Here is the final code: https://replit.com/@pisush/advent-1-go

Please note that anywhere you see ``` /`/`/` ``` - originally this is normal 3 backticks, but for this MD file I had to escape it.

And in more detail -



# Attempt 1


## DaVinci Input Prompt 1

```
This is a coding exercise I need to solve.
How should I instruct Codex to solve it?

---------

Exercise description:

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

---------

Instructions for Codex:
```

## DaVinci Output 1

```
1. Read the exercise description and input data.
2. Parse the data into a data structure (e.g. list)
3. Create a loop to iterate through the list and calculate the total Calories for each Elf.
4. Keep track of the maximum Calories and the Elf associated with it.
5. Print the total Calories and the Elf associated with it.
```

## My Feedback 1

Feels to general, let's try again.



# Attempt 2


## DaVinci Input Prompt 2

```
This is a coding exercise I need to solve.
Write the instructions for Codex so it can solve it.

---------------------------------------------------------------
Exercise description
---------------------------------------------------------------

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

- The first Elf is carrying food with 1000, 2000, and 3000 Calories, a total of 6000 Calories.
- The second Elf is carrying one food item with 4000 Calories.
- The third Elf is carrying food with 5000 and 6000 Calories, a total of 11000 Calories.
- The fourth Elf is carrying food with 7000, 8000, and 9000 Calories, a total of 24000 Calories.
- The fifth Elf is carrying one food item with 10000 Calories.
- In case the Elves get hungry and need extra snacks, they need to know which Elf to ask: they'd like to know how many Calories are being carried by the Elf carrying the most Calories. In the example above, this is 24000 (carried by the fourth Elf).

Find the Elf carrying the most Calories. 
How many total Calories is that Elf carrying?

---------------------------------------------------------------
Instructions for Codex
---------------------------------------------------------------
1.
```

## DaVinci Output 2

```
1. Read the input data, storing each line as an element in a list.
2. Initialize a "calorie_sum" variable to hold the sum of Calories of each Elf.
3. Iterate through the list, adding each element to the "calorie_sum" variable.
4. Initialize a "max_calories" variable to hold the maximum number of Calories carried by any Elf.
5. Compare the current "calorie_sum" to the "max_calories" variable. If the current "calorie_sum" is greater than the "max_calories" variable, set the "max_calories" variable to the current "calorie_sum".
6. After iterating through the list, the "max_calories" variable will hold the maximum number of Calories carried by any Elf.
7. Output the "max_calories" variable.

```

## Codex Input Prompt 2

```
/`/`/`go
/*
findMaxCalories is a function that calculates max calories using the following steps

1. Read the input data, storing each line as an element in a list.
2. Initialize a "calorie_sum" variable to hold the sum of Calories of each Elf.
3. Iterate through the list, adding each element to the "calorie_sum" variable.
4. Initialize a "max_calories" variable to hold the maximum number of Calories carried by any Elf.
5. Compare the current "calorie_sum" to the "max_calories" variable. If the current "calorie_sum" is greater than the "max_calories" variable, set the "max_calories" variable to the current "calorie_sum".
6. After iterating through the list, the "max_calories" variable will hold the maximum number of Calories carried by any Elf.
7. Output the "max_calories" variable.
*/
func findMaxCalories(
```

## Codex Output 2

```
func findMaxCalories(input []string) int {
	calorieSum := 0
	maxCalories := 0
	for _, line := range input {
		calorieSum += getCalories(line)
		if calorieSum > maxCalories {
			maxCalories = calorieSum
		}
	}
	return maxCalories
}
/`/`/`

## Part 2

### Problem Statement

The Elves decide they don't want to visit an infinite number of houses. Instead, each Elf will stop after delivering presents to 50 houses. To make up for it, they decide to deliver presents equal to eleven times their number at each house.

With these changes, what is the new **highest** house number of the house to get at least as many presents as the number in your puzzle input?

### Solution

The solution to this problem is very similar to the solution to Part 1. The only difference is that we need to keep track of the number of houses visited by each Elf.

/`/`/`go
/*
findMaxCalories is a function that calculates max calories using the following steps

1. Read the input data, storing each line as an element in a list.
2. Initialize a "calorie_sum" variable to hold the sum of Calories of each Elf.
3. Iterate through the list, adding each element to the "calorie_sum" variable.
4. Initialize a "max_calories" variable to hold the maximum number of Calories carried by any Elf.
5. Compare the current "calorie_sum" to the "max_calories" variable. If the current "calorie_sum" is greater than the "max_calories" variable, set the "max_calories" variable to the current "calorie_sum".
6. After iterating through the list, the "max_calories" variable will hold the maximum number of Calories carried by any Elf.
7. Output the "max_calories" variable.
*/
func findMaxCalories(input []string) int {
	calorieSum := 0
	maxCalories := 0
	for _, line := range input {
		calorieSum += getCalories(line)
		if calorieSum > maxCalories {
			maxCalories = calorieSum
		}
	}
	return maxCalories
}
/`/`/`

```

## My Feedback 2

* First of all - it's a nice creative touch to add another exercise+solution.
* I took the first part into Replit, but it doesn't work - it uses a func called getCalories() which doesn't exist. 
* I hope to solve the exercise without reading it, so I'm just asking it to implement this function.
* Note that I removed the 3 backticks copying the output into this prompt, to indicate our block of Go code is still open, and I added a very basic description to the function.

## Codex Input Prompt 2.1
```
/`/`/`go
/*
findMaxCalories is a function that calculates max calories using the following steps

1. Read the input data, storing each line as an element in a list.
2. Initialize a "calorie_sum" variable to hold the sum of Calories of each Elf.
3. Iterate through the list, adding each element to the "calorie_sum" variable.
4. Initialize a "max_calories" variable to hold the maximum number of Calories carried by any Elf.
5. Compare the current "calorie_sum" to the "max_calories" variable. If the current "calorie_sum" is greater than the "max_calories" variable, set the "max_calories" variable to the current "calorie_sum".
6. After iterating through the list, the "max_calories" variable will hold the maximum number of Calories carried by any Elf.
7. Output the "max_calories" variable.
*/
func findMaxCalories(input []string) int {
	calorieSum := 0
	maxCalories := 0
	for _, line := range input {
		calorieSum += getCalories(line)
		if calorieSum > maxCalories {
			maxCalories = calorieSum
		}
	}
	return maxCalories
}

/* getCalories is a helper function to findMaxCalories() /*
func getCalories(line
/`/`/`
```

## CODEX Output 2.1
```
func getCalories(line string) int {
	calories, _ := strconv.Atoi(strings.Split(line, " ")[3])
	return calories
}
```

## My Feedback 2.1

I copied the provided input into a file called "input.txt"
And copied the generated code into a same level file called "main.go"
The last remaining bit is to ask the two to communicate.


## CODEX Input Prompt 2.2
```
/`/`/`go
/* use the file "input.txt" as the input to the function findMaxCalories(input []string) int
print the output of the function
*/
func main() {
	fmt.Println(findMaxCalories(
```

## CODEX Output 2.2 
```
fmt.Println(findMaxCalories(readInput("input.txt")))
}
`/`/`/
```

## My Input 2.2 
This is going to fail because readInput() is not a function. So let's ask to implement this one too!

## CODEX Input Prompt 2.3
```
/`/`/`go
/* use the file "input.txt" as the input to the function findMaxCalories(input []string) int
print the output of the function
*/
func main() {
		fmt.Println(findMaxCalories(readInput("input.txt")))
}
  
/*
readInput is a helper function to findMaxCalories()
*/
func readInput(
```

## CODEX Output 2.3
```
func readInput(filename string) []string {
  file, err := os.Open(filename)
	if err != nil {
		log.Fatal(err)
	}
	defer file.Close()

	scanner := bufio.NewScanner(file)
	var input []string
	for scanner.Scan() {
		input = append(input, scanner.Text())
	}

	if err := scanner.Err(); err != nil {
		log.Fatal(err)
	}
	return input
}
/`/`/`  
```

## My Feedback 2.3
Finally import mistakes! It won't auto import and I can't find a setting/button for it, so for now manually importing and trying again.
```
$ make run
go build -o main .
# main
./main.go:24:17: undefined: strconv
./main.go:24:30: undefined: strings
./main.go:29:16: undefined: os
./main.go:31:3: undefined: log
./main.go:35:13: undefined: bufio
./main.go:42:3: undefined: log
make: *** [Makefile:6: main] Error 2
exit status 2
```

Importing manually and re-running:
```
$ make run
go build -o main .
./main
panic: runtime error: index out of range [3] with length 1

goroutine 1 [running]:
main.getCalories({0xc00012800c, 0x4bfc40})
    /home/runner/advent-of-code-day-1/main.go:29 +0x65
main.findMaxCalories({0xc00015c000, 0x8bb, 0x0})
    /home/runner/advent-of-code-day-1/main.go:20 +0x76
main.main()
    /home/runner/advent-of-code-day-1/main.go:13 +0x2a
make: *** [Makefile:3: run] Error 2
exit status 2
```

In L29 changed from:
```calories, _ := strconv.Atoi(strings.Split(line, " ")[3])```
to:
```calories, _ := strconv.Atoi(strings.Split(line, " ")[0])```

And runnning again:
```
$ make run
go build -o main .
./main
11135643 
```

And the Advent of Code out put is:
```That's not the right answer; your answer is too high. 
If you're stuck, make sure you're using the full input data; 
there are also some general tips on the about page, or you can ask for hints on the subreddit.
Please wait one minute before trying again. (You guessed 11135643.) [Return to Day 1]
```

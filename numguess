#!/bin/bash

#numguess: A script to play a simple number guessing game
# Originally authored by Mitch Spradlin
# 2014-1-20

#Let the player exit in a civil manner if they accidentally started it
pass=0
while [[ $pass == 0 ]]
do
	echo -n "Would you like to play the number guessing game? (y/n) "
	read response
	case $response in
		y*)
			pass=1
			;;
		n*)
			pass=1
			echo "Bye!"
			exit 0
			;;
		*)
			echo "I didn't understand that input!"
			pass=0
			;;
		esac
done

#Let the player select a difficulty of game
pass=0
while [[ $pass == 0 ]]
do
	echo
	echo "Which difficulty would you like to play at? (1-3)"
	echo "1: Range 1-100 with 10 guesses"
	echo "2: Range 1-1000 with 10 guesses"
	echo "3: Range 1-10000 with 15 guesses"
	echo -n "Selection: "
	read response
	case $response in
		1)
			top=100
			guesses=10
			pass=1
			;;
		2)
			top=1000
			guesses=10
			pass=1
			;;
		3)
			top=10000
			guesses=15
			pass=1
			;;
		*)
			echo "I didn't understand that input!"
			pass=0
			;;
		esac
done

#The main game loop
echo
echo "Excellent, get ready!"
echo
echo "Thinking of a number..."

#$RANDOM is a built-in bash command that generates a number between 0-32767
randnum=$(($RANDOM * $top / 32767))
echo "Got it!"

try="0"
while [[ $try -lt $guesses ]]
do
	echo "$(($guesses - $try)) guesses left!"
	echo -n "What is your guess? "
	read guess
	if [[ $guess == $randnum ]]
	then
		echo 
		echo "Congratulations!"
		echo "You got it in $try tries!"
		pass=0
		while [[ $pass == 0 ]]
		do
			echo -n "Would you like to play again? (y/n) "
			read again
				case $again in
					y*)
						echo
						#Call itself again
						./$0
						#After that has completed, exit
						exit 0
						;;
					n*)
						echo
						echo "Bye!"
						exit 0
						;;
					*)
						echo
						echo "I didn't understand that input!"
						pass=0
						;;
					esac
		done
	elif [[ $guess -gt $randnum ]]
	then
		echo
		echo "Too high!"
		echo
		try=$(($try + 1)) #Increment the try counter
	else #Then it must be too low
		echo
		echo "Too low!"
		echo
		try=$(($try + 1))
	fi
done

#If we get to here, then the player didn't guess the number in the requisite
# number of tries
echo
echo "Sorry, you didn't guess the number in the correct number of tries!"
echo "The number was: $randnum"
pass=0
while [[ $pass == 0 ]]
do
	echo -n "Would you like to play again? (y/n) "
	read again
		case again in
			y*)
				echo
				#Call itself again
				./$0
				#After that has completed, exit
				exit 0
				;;
			n*)
				echo	
				echo "Bye!"
				exit 0
				;;
			*)
				echo
				echo "I didn't understand that input!"
				pass=0
				;;
			esac
done


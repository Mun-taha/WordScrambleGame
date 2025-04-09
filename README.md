
package com.muntaha.wordscramblegame;

import java.util.*;

public class WordScrambleGame {

    static String[] wordList = {"object", "inheritance", "java", "encapsulation", "abstraction", "polymorphism"};
    static Scanner scanner = new Scanner(System.in);
    static int score = 0;

    public static void main(String[] args) {
        System.out.println("Welcome to the Word Scramble Game!");
        System.out.println("Unscramble the words. Type 'exit' to quit.\n");

        for (String originalWord : wordList) {
            String scrambled = scrambleWord(originalWord);
            System.out.println("Scrambled Word: " + scrambled);

            System.out.print("Your Guess: ");
            String guess = scanner.nextLine().trim().toLowerCase();

            if (guess.equals("exit")) {
                break;
            } else if (guess.equals(originalWord)) {
                System.out.println("Correct!\n");
                score++;
            } else {
                System.out.println("Wrong! The correct word was: " + originalWord + "\n");
            }
        }

        System.out.println("Game Over!");
        System.out.println("Your Final Score: " + score + "/" + wordList.length);
    }

    public static String scrambleWord(String word) {
        List<Character> characters = new ArrayList<>();
        for (char c : word.toCharArray()) {
            characters.add(c);
        }

        Collections.shuffle(characters); // Scramble the characters
        StringBuilder scrambled = new StringBuilder();
        for (char c : characters) {
            scrambled.append(c);
        }

        return scrambled.toString();
    }
}

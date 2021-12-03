# Java-Readability-

package com.company;
import java.util.*;
import java.lang.Math;


public class Main {
    public static void print(String text){
        System.out.println(text);
    }

    public static int countLetters(String text){
        String mtext = text.replaceAll("[^A-Za-z]+", "");
        return mtext.length();
    }

    public static int countWords(String text){
        String[] mtext = text.split(" ");
        return mtext.length;
    }

    public static int countSentences(String text){
        String[] mtext = text.split("[.!?]");
        return mtext.length;
    }

    public static void ColemanLiauIndex(int numberLetters, int numberwords, int numSentences){
        int index;
        double L, S;
        L = (numberLetters * 100)/ numberwords;
        S = (numSentences * 100)/ numberwords;
        if(((int) Math.rint(0.0588*L - 0.296*S -15.8)) > 16)
            index = 17;
        else
            index = (int) Math.rint(0.0588*L - 0.296*S -15.8);
        if(index < 1)
            print("Before Grade 1");
        else if(index > 16)
            print("Grade 16+");
        else
            print("Grade " + index);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String text = "";

        while(args.length != 1 && text == ""){
            if(args.length == 0){
                print("Please provide some text as input");
                text = sc.nextLine();
            }
            else{
                print("Please provide only one input");
                text = sc.nextLine();
            }
        }
        if(text == "")
            text = args[0];


        int numletters = countLetters(text);
        int numwords = countWords(text);
        int numsentences = countSentences(text);


        ColemanLiauIndex(numletters, numwords, numsentences);

    }
}

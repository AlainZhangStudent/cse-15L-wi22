Part 1: Roleplay

Student's Original Post: Hey everyone,
I'm encountering a strange issue with my Java program. It's supposed to read a list of numbers from a file and calculate their average, but it seems like the average is always coming out as zero, even though I know the numbers in the file are valid. 
I've attached a screenshot of the code and the output showing the average as 1. Can anyone help me figure out what's going wrong?

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport5/lab5s1.jpg)

TA's Response: Hey there,
Thanks for reaching out! Could you try adding some print statements in your code to see if the values are being read correctly from the file? Maybe try printing each number as you read it to ensure they're being processed properly. 
You can use System.out.println() for this purpose.
Let me know what you find!

Student's Follow-up Comment: Thanks for the suggestion! I added print statements to check the numbers as they're being read from the file, and it turns out they're all being read right, but returns as the average 0. 
Here's a screenshot of the updated code and the terminal output showing the numbers being read. Any ideas on why this might be happening?

![Image](https://alainzhangstudent.github.io/cse-15L-wi22/labreport5/lab5s2.jpg)

From here we can't really tell much besides that the numbers, in fact, are being read. This is an example of a student
who only provided the symptoms and inputs, but not the bug (code) itself.

TA's Reponse:
You can probably use jdb to debug the sepcific variable, but try using vim to open up the file and go to
the specific line where the average is affected so you won't have to step through everything. Without further
context our hands are tied.

Files needed: ```run.sh file, numbers.txt and Main.java ```
Directory structure: ```run.sh, numbers.txt, and Main.java``` being in the same directory, doesn't matter where so long as 
it can execute and write

Before fixing:
Content of Main.java:
```
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        File file = new File("numbers.txt");
        try {
            Scanner scanner = new Scanner(file);
            double sum = 0;
            int count = 0;
            while (scanner.hasNextDouble()) {
                double num = scanner.nextDouble();
                System.out.println("Read number: " + num); // Added print statement for debugging
                sum += num;
                count++;
            }
            double average = sum / sum; // The error in question HAHAAHA
            System.out.println("Average: " + average);
            scanner.close();
        } catch (FileNotFoundException e) {
            System.out.println("File not found.");
        }
    }
}
```
Content of numbers.txt:```
10
12
38```

Content of run.sh:```
javac Main.java
java Main```

Setup:
After creating a numbers.txt with a number on each new line, use javac Main.java and then java Main to run the program. So like, 
```touch numbers.txt``` -> ```vim numbers.txt``` -> ```i 23 28 32 esc :wq``` -> ```javac Main.java``` -> ```java Main.java```
Running a program like this will trigger the bug.

In order to fix the bug, the average shouldn't be dividing the sum by the sum, but rather the sum by the count in order to get the average. Then, it should return the average and not just 1.

Part 2:
I learned that I genuinely don't like lab. Too much busywork for very little payoff; I feel like homeworks are more valuable than writing lab reports.
Otherwise, I enjoyed the lab activities, and I got to learn more about local hosting as well as the tutors who are very chill. I know they have to do what they gotta do
but I wish they made my life a little easier on the reports. :')

# StudentGradeTracer
import java.util.ArrayList;
import java.util.Scanner;

public class StudentGrades {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Integer> grades = new ArrayList<>();
        String input;

        // Collecting grades
        System.out.println("Enter student grades (type 'done' to finish): ");
        while (true) {
            input = scanner.nextLine();
            if (input.equalsIgnoreCase("done")) {
                break;
            }
            try {
                int grade = Integer.parseInt(input);
                grades.add(grade);
            } catch (NumberFormatException e) {
                System.out.println("Please enter a valid grade or type 'done' to finish.");
            }
        }

        // Check if grades are entered
        if (grades.isEmpty()) {
            System.out.println("No grades entered.");
            return;
        }

        // Converting ArrayList to Array
        int[] gradesArray = new int[grades.size()];
        for (int i = 0; i < grades.size(); i++) {
            gradesArray[i] = grades.get(i);
        }

        // Calculating average, highest, and lowest scores
        double average = calculateAverage(gradesArray);
        int highest = findHighest(gradesArray);
        int lowest = findLowest(gradesArray);

        // Displaying results
        System.out.println("Average grade: " + average);
        System.out.println("Highest grade: " + highest);
        System.out.println("Lowest grade: " + lowest);
    }

    public static double calculateAverage(int[] grades) {
        int sum = 0;
        for (int grade : grades) {
            sum += grade;
        }
        return (double) sum / grades.length;
    }

    public static int findHighest(int[] grades) {
        int highest = grades[0];
        for (int grade : grades) {
            if (grade > highest) {
                highest = grade;
            }
        }
        return highest;
    }

    public static int findLowest(int[] grades) {
        int lowest = grades[0];
        for (int grade : grades) {
            if (grade < lowest) {
                lowest = grade;
            }
        }
        return lowest;
    }
}

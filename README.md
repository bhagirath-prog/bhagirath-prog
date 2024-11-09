#include <stdio.h>

#define MAX_STUDENTS 100

// Function declarations
void addScore(int scores[], int *count);
void displayScores(int scores[], int count);
void calculateAverage(int scores[], int count);
void findHighestAndLowest(int scores[], int count);

int main() {
    int scores[MAX_STUDENTS];
    int count = 0;
    int choice;

    while (1) {
        printf("\nStudent Score Manager\n");
        printf("1. Add a score\n");
        printf("2. Display all scores\n");
        printf("3. Calculate average score\n");
        printf("4. Find highest and lowest score\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addScore(scores, &count);
                break;
            case 2:
                displayScores(scores, count);
                break;
            case 3:
                calculateAverage(scores, count);
                break;
            case 4:
                findHighestAndLowest(scores, count);
                break;
            case 5:
                printf("Exiting the program.\n");
                return 0;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }
}

// Function to add a score
void addScore(int scores[], int *count) {
    if (*count >= MAX_STUDENTS) {
        printf("Maximum number of students reached.\n");
        return;
    }
    printf("Enter the score for student %d: ", *count + 1);
    scanf("%d", &scores[*count]);
    (*count)++;
    printf("Score added successfully.\n");
}

// Function to display all scores
void displayScores(int scores[], int count) {
    if (count == 0) {
        printf("No scores to display.\n");
        return;
    }
    printf("\nScores of students:\n");
    for (int i = 0; i < count; i++) {
        printf("Student %d: %d\n", i + 1, scores[i]);
    }
}

// Function to calculate the average score
void calculateAverage(int scores[], int count) {
    if (count == 0) {
        printf("No scores available to calculate average.\n");
        return;
    }
    int sum = 0;
    for (int i = 0; i < count; i++) {
        sum += scores[i];
    }
    double average = (double)sum / count;
    printf("\nThe average score is: %.2f\n", average);
}

// Function to find the highest and lowest score
void findHighestAndLowest(int scores[], int count) {
    if (count == 0) {
        printf("No scores available to find highest and lowest.\n");
        return;
    }
    int highest = scores[0];
    int lowest = scores[0];
    for (int i = 1; i < count; i++) {
        if (scores[i] > highest) {
            highest = scores[i];
        }
        if (scores[i] < lowest) {
            lowest = scores[i];
        }
    }
    printf("\nThe highest score is: %d\n", highest);
    printf("The lowest score is: %d\n", lowest);
}

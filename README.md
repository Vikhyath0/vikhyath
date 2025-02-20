#include <stdio.h>

#define MAX_MATCHES 100
float calculateAverage(int scores[], int n) {
    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += scores[i];
    }
    return (float)sum / n;
}
void findHighestAndLowest(int scores[], int n, int *highest, int *lowest) {
    *highest = scores[0];
    *lowest = scores[0];

    for (int i = 1; i < n; i++) {
        if (scores[i] > *highest) {
            *highest = scores[i];
        }
        if (scores[i] < *lowest) {
            *lowest = scores[i];
        }
    }
}

int main() {
    int scores[MAX_MATCHES];
    int n;
    printf("Enter the number of matches: ");
    scanf("%d", &n);
    if (n <= 0 || n > MAX_MATCHES) {
        printf("Invalid number of matches.\n");
        return 1;
    }
    printf("Enter the scores for %d matches:\n", n);
    for (int i = 0; i < n; i++) {
        printf("Match %d: ", i + 1);
        scanf("%d", &scores[i]);
    }
    int highest, lowest;
    findHighestAndLowest(scores, n, &highest, &lowest);
    float average = calculateAverage(scores, n);
    printf("\nMatch Scores: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", scores[i]);
    }
    printf("\n");

    printf("Highest score: %d\n", highest);
    printf("Lowest score: %d\n", lowest);
    printf("Average score: %.2f\n", average);

    return 0;
}

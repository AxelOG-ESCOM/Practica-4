#include <stdio.h>
#include <stdlib.h>

int compare(const void *a, const void *b) {
    return (*(int*)a - *(int*)b);
}

int team_chemistry(int *skill, int n) {
    qsort(skill, n, sizeof(int), compare);
    int target_sum = skill[0] + skill[n - 1];
    int total_chemistry = 0;

    for (int i = 0; i < n / 2; i++) {
        if (skill[i] + skill[n - 1 - i] != target_sum) {
            return -1;
        }
        total_chemistry += skill[i] * skill[n - 1 - i];
    }
    return total_chemistry;
}

int main() {
    int skill1[] = {3, 2, 5, 1, 3, 4};
    int skill2[] = {3, 4};
    int skill3[] = {1, 1, 2, 3};

    printf("Resultado 1: %d\n", team_chemistry(skill1, 6));
    printf("Resultado 2: %d\n", team_chemistry(skill2, 2));
    printf("Resultado 3: %d\n", team_chemistry(skill3, 4));

    return 0;
}

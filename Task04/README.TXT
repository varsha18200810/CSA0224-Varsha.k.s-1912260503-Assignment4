#include <stdio.h>

struct account {
    int number;
    float balance;
};

void addInterest(struct account *a, float rate) {
    a->balance += a->balance * rate / 100.0f;
}

int main(void) {
    struct account list[3] = {
        {101, 5000.0f},
        {102, 12000.0f},
        {103, 800.0f}
    };

    struct account *p = list;

    for (int i = 0; i < 3; i++) {
        addInterest(&list[i], 4.0f);
    }

    for (int i = 0; i < 3; i++) {
        printf("%d %.2f\n", p[i].number, p[i].balance);
    }

    return 0;
}

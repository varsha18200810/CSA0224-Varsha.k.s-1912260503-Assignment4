#include <stdio.h>

/* Static local variable retains its value between calls. */
int next_token(void) {
    static int token = 1000;
    return ++token;
}

/* Automatic variable is created again on every call. */
int auto_token(void) {
    int token = 1000;
    return ++token;
}

int main(void) {
    int s1 = next_token();
    int s2 = next_token();
    int s3 = next_token();

    int a1 = auto_token();
    int a2 = auto_token();
    int a3 = auto_token();

    printf("static: %d %d %d\n", s1, s2, s3);
    printf("auto: %d %d %d\n", a1, a2, a3);

    return 0;
}

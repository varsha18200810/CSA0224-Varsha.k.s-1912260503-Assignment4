#include <stdio.h>
#include <string.h>

struct Date {
    int day, month, year;
};

struct BloodPressure {
    int systolic, diastolic;
};

struct Patient {
    char name[50];
    int age;
    char phone[11];  /* 10 digits + '\0' */

    struct BloodPressure bp;
    struct Date visitDate;
};

void addPatient(struct Patient *p, const char *name, int age,
                const char *phone, int sys, int dia,
                struct Date date) {

    snprintf(p->name, sizeof(p->name), "%s", name);

    p->age = age;

    snprintf(p->phone, sizeof(p->phone), "%s", phone);

    p->bp.systolic = sys;
    p->bp.diastolic = dia;

    p->visitDate = date;
}

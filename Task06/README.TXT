#include <stdio.h>
#include <string.h>

#define MAX_ITEMS 50
#define MAX_SALES 100

typedef struct {
    int day, month, year;
} Date;

enum ItemType {
    PACKAGED,
    COOKED,
    COMBO
};

typedef struct {
    Date expiry;
} PackagedInfo;

typedef struct {
    int hour, minute;
} CookedInfo;

typedef struct {
    int componentId[3];
    int quantity[3];
    int count;
} ComboInfo;

typedef struct {
    int id;
    char name[40];
    enum ItemType type;
    int stock;
    float price;

    union {
        PackagedInfo packaged;
        CookedInfo cooked;
        ComboInfo combo;
    } details;

    float revenue;
} Item;

typedef struct {
    int itemId;
    int quantity;
    float amount;
} Sale;

/* Function declarations */

int recordSale(Item *items, int n, int itemId, int qty, Sale *sale);

int isExpiringSoon(const Date *expiry, const Date *today);

void printExpiryWarnings(const Item items[], int n, const Date *today);

void sortByRevenue(Item items[], int n);

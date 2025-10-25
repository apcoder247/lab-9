#include <stdio.h>

int main() {
    int n, i;
    printf("Enter number of elements: ");
    scanf("%d", &n);

    int arr[n];
    int *ptr = arr;

    printf("Enter %d elements:\n", n);
    for (i = 0; i < n; i++)
        scanf("%d", (ptr + i));

    int max = *ptr;
    for (i = 1; i < n; i++) {
        if (*(ptr + i) > max)
            max = *(ptr + i);
    }

    printf("Maximum element = %d\n", max);
    return 0;
}



#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x, y;
    printf("Enter two numbers: ");
    scanf("%d %d", &x, &y);

    swap(&x, &y);

    printf("After swapping: x = %d, y = %d\n", x, y);
    return 0;
}




#include <stdio.h>

struct Student {
    char name[50];
    int roll;
    float marks[3];
    float total, average;
};

int main() {
    struct Student s[5];
    int i, j;

    for (i = 0; i < 5; i++) {
        printf("\nEnter details for student %d:\n", i + 1);
        printf("Name: ");
        scanf("%s", s[i].name);
        printf("Roll number: ");
        scanf("%d", &s[i].roll);
        s[i].total = 0;
        for (j = 0; j < 3; j++) {
            printf("Marks in subject %d: ", j + 1);
            scanf("%f", &s[i].marks[j]);
            s[i].total += s[i].marks[j];
        }
        s[i].average = s[i].total / 3.0;
    }

    printf("\nStudent Results:\n");
    printf("Name\tRoll\tTotal\tAverage\n");
    for (i = 0; i < 5; i++)
        printf("%s\t%d\t%.2f\t%.2f\n", s[i].name, s[i].roll, s[i].total, s[i].average);

    return 0;
}


#include <stdio.h>

struct Address {
    char street[50];
    char city[50];
    int zip;
};

struct Student {
    char name[50];
    int roll;
    struct Address addr;
};

int main() {
    struct Student s;

    printf("Enter student name: ");
    scanf("%s", s.name);
    printf("Enter roll number: ");
    scanf("%d", &s.roll);

    printf("Enter street: ");
    scanf("%s", s.addr.street);
    printf("Enter city: ");
    scanf("%s", s.addr.city);
    printf("Enter zip code: ");
    scanf("%d", &s.addr.zip);

    printf("\n--- Student Details ---\n");
    printf("Name: %s\nRoll No: %d\nAddress: %s, %s - %d\n", s.name, s.roll, s.addr.street, s.addr.city, s.addr.zip);

    return 0;
}




#include <stdio.h>

struct Product {
    int id;
    char name[50];
    float price;
};

int main() {
    int n, i;
    printf("Enter number of products: ");
    scanf("%d", &n);

    struct Product p[n];
    struct Product *ptr = p;

    for (i = 0; i < n; i++) {
        printf("\nEnter details for product %d:\n", i + 1);
        printf("Product ID: ");
        scanf("%d", &(ptr + i)->id);
        printf("Product Name: ");
        scanf("%s", (ptr + i)->name);
        printf("Price: ");
        scanf("%f", &(ptr + i)->price);
    }

    printf("\n--- Product Details ---\n");
    printf("ID\tName\tPrice\n");
    for (i = 0; i < n; i++)
        printf("%d\t%s\t%.2f\n", (ptr + i)->id, (ptr + i)->name, (ptr + i)->price);

    return 0;
}


#include <stdio.h>
#include <string.h>

struct Player {
    char name[50];
    char team[50];
    float average;
};

int main() {
    int n, i, j;
    printf("Enter number of players: ");
    scanf("%d", &n);

    struct Player p[n], temp;

    for (i = 0; i < n; i++) {
        printf("\nEnter details for player %d:\n", i + 1);
        printf("Player Name: ");
        scanf("%s", p[i].name);
        printf("Team Name: ");
        scanf("%s", p[i].team);
        printf("Batting Average: ");
        scanf("%f", &p[i].average);
    }

    // Sorting by batting average (descending)
    for (i = 0; i < n - 1; i++) {
        for (j = i + 1; j < n; j++) {
            if (p[i].average < p[j].average) {
                temp = p[i];
                p[i] = p[j];
                p[j] = temp;
            }
        }
    }

    printf("\n--- Player List (Sorted by Batting Average) ---\n");
    printf("Name\tTeam\tAverage\n");
    for (i = 0; i < n; i++)
        printf("%s\t%s\t%.2f\n", p[i].name, p[i].team, p[i].average);

    return 0;
}




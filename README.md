#include <stdio.h>

struct Vehicle
{
    int id;
    char model[20];
    char type[10];
    float price;
    int available;
};

void search(struct Vehicle v[], int n)
{
    int id, i;

    printf("Enter Vehicle ID: ");
    scanf("%d", &id);

    for(i = 0; i < n; i++)
    {
        if(v[i].id == id)
        {
            printf("Model: %s\n", v[i].model);
            printf("Type: %s\n", v[i].type);
            printf("Price: %.2f\n", v[i].price);

            if(v[i].available == 1)
                printf("Available\n");
            else
                printf("Not Available\n");

            return;
        }
    }

    printf("Vehicle not found\n");
}

void book(struct Vehicle *v)
{
    int days;

    if(v->available == 0)
    {
        printf("Vehicle is not available\n");
    }
    else
    {
        printf("Enter number of days: ");
        scanf("%d", &days);

        printf("Total Amount = %.2f\n", v->price * days);

        v->available = 0;

        printf("Vehicle booked successfully\n");
    }
}

void returnVehicle(struct Vehicle *v)
{
    v->available = 1;
    printf("Vehicle returned successfully\n");
}

int main()
{
    struct Vehicle v[3] =
    {
        {101, "Swift", "Car", 1500, 1},
        {102, "Activa", "Bike", 500, 1},
        {103, "Innova", "Car", 2500, 1}
    };

    int choice, id;

    printf("1. Search Vehicle\n");
    printf("2. Book Vehicle\n");
    printf("3. Return Vehicle\n");

    printf("Enter choice: ");
    scanf("%d", &choice);

    if(choice == 1)
    {
        search(v, 3);
    }
    else if(choice == 2)
    {
        printf("Enter Vehicle ID: ");
        scanf("%d", &id);

        if(id >= 101 && id <= 103)
            book(&v[id - 101]);
        else
            printf("Invalid Vehicle ID\n");
    }
    else if(choice == 3)
    {
        printf("Enter Vehicle ID: ");
        scanf("%d", &id);

        if(id >= 101 && id <= 103)
            returnVehicle(&v[id - 101]);
        else
            printf("Invalid Vehicle ID\n");
    }
    else
    {
        printf("Invalid choice\n");
    }

    return 0;
}
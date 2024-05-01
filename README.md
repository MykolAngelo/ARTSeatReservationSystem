# ARTSeatReservationSystem
include <stdio.h>
#include <stdlib.h>

typedef struct {
    char type[20];
    int seats;
    char seatCategory[20];
    float totalAmount;
} Reservation;

void displaySeatDetails() {

}

float calculateTotalAmount(char type[], int seats, char seatCategory[]) {

}

void displayTransactionDetails(Reservation *reservation, int numReservations) {
    
}

void saveToFile(Reservation *reservation, int numReservations) {
    FILE *file = fopen("transactions.txt", "a");
    if (file == NULL) {
        printf("Error opening file!\n");
        exit(1);
    }

    for (int i = 0; i < numReservations; i++) {
        fprintf(file, "Type: %s, Seats: %d, Seat Category: %s, Total Amount: %.2f\n",
                reservation[i].type, reservation[i].seats, reservation[i].seatCategory, reservation[i].totalAmount);
    }

    fclose(file);
}

int main() {

    Reservation reservations[3];
    int numReservations = 0;

    while (1) {
       
        int choice;
        printf("Welcome to the ART seat reservation system!\n");
        printf("Please select the follow to start your reservation:\n");
        printf("1. Make a reservation\n");
        printf("2. Display seat details\n");
        printf("3. Display transaction details\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1: {
                
                printf("\nEnter reservation details:\n");
                printf("Type (e.g., Adult, Kids): ");
                scanf("%s", reservations[numReservations].type);
                printf("Number of seats: ");
                scanf("%d", &reservations[numReservations].seats);
                printf("Seat category (e.g., hot seat, normal seat): ");
                scanf("%s", reservations[numReservations].seatCategory);

               
                reservations[numReservations].totalAmount =
                    calculateTotalAmount(reservations[numReservations].type,
                                         reservations[numReservations].seats,
                                         reservations[numReservations].seatCategory);
                printf("\nTotal Amount: %.2f\n", reservations[numReservations].totalAmount);

               
                saveToFile(reservations, numReservations + 1);

                
                numReservations++;
                break;
            }
            case 2:
                
                displaySeatDetails();
                break;
            case 3:
                
                displayTransactionDetails(reservations, numReservations);
                break;
            case 4:
                
                printf("Exiting program.\n");
                return 0;
            default:
                printf("Invalid choice. Please enter a valid option.\n");
        }
    }

    return 0;
}

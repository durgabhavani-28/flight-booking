#include <iostream>
#include <vector>
#include <string>
#include <iomanip>
#include <fstream>
#include <limits>

using namespace std;

struct Flight {
    int flightNumber;
    string destination;
    string departureTime;
    int availableSeats;
};

struct Booking {
    string passengerName;
    int flightNumber;
    int seatsBooked;
};

vector<Flight> flights; 
vector<Booking> bookings;

void initializeFlights() {
    Flight flight1 = { 126, "Delhi", "10:00 AM", 50};
    Flight flight2 = { 4001, "Goa", "12:00 PM", 40};
    Flight flight3 = { 108, "Hyderabad", "03:00 PM", 30};
    Flight flight4 = { 306, "Tokyo", "06:00 PM", 20};

    flights.push_back(flight1);
    flights.push_back(flight2);
    flights.push_back(flight3);
    flights.push_back(flight4);
}

void displayFlights() {
    cout << "\nAvailable Flights:\n";
    cout << left << setw(15) << "Flight No" << setw(20) << "Destination"
         << setw(15) << "Departure" << setw(15) << "Seats Available" << endl;

    for (size_t i = 0; i < flights.size(); i++) {
        cout << left << setw(15) << flights[i].flightNumber
             << setw(20) << flights[i].destination
             << setw(15) << flights[i].departureTime
             << setw(15) << flights[i].availableSeats << endl;
    }
}

void bookFlight() {
    string passengerName;
    int flightNumber, seats;

    cin.ignore(numeric_limits<streamsize>::max(), '\n'); 
    cout << "\nEnter your name: ";
    getline(cin, passengerName);

    cout << "Enter flight number to book: ";
    while (!(cin >> flightNumber)) {
        cout << "Invalid input. Please enter a valid flight number: ";
        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
    }

    cout << "Enter number of seats to book: ";
    while (!(cin >> seats) || seats <= 0) {
        cout << "Invalid input. Please enter a valid number of seats: ";
        cin.clear();
        cin.ignore(numeric_limits<streamsize>::max(), '\n');
    }

    for (size_t i = 0; i < flights.size(); i++) {
        if (flights[i].flightNumber == flightNumber) {
            if (flights[i].availableSeats >= seats) {
                flights[i].availableSeats -= seats;
                Booking booking = {passengerName, flightNumber, seats};
                bookings.push_back(booking);
                cout << "Booking successful! " << seats << " seat(s) booked for " << passengerName << ".\n";
                return;
            } else {
                cout << "Not enough seats available!\n";
            }
            return;
        }
    }
    cout << "Flight not found!\n";
}

void displayBookings() {
    if (bookings.empty()) {
        cout << "\nNo bookings yet.\n";
        return;
    }

    cout << "\nBooking Details:\n";
    cout << left << setw(20) << "Passenger Name" << setw(15) << "Flight No"
         << setw(15) << "Seats Booked" << endl;

    for (size_t i = 0; i < bookings.size(); i++) {
        cout << left << setw(20) << bookings[i].passengerName
             << setw(15) << bookings[i].flightNumber
             << setw(15) << bookings[i].seatsBooked << endl;
    }
}

int main() {
    initializeFlights();

    int choice;

    while (true) {
        cout << "\nFlight Booking System\n";
        cout << "1. View Available Flights\n";
        cout << "2. Book a Flight\n";
        cout << "3. View Bookings\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";

        while (!(cin >> choice)) {
            cout << "Invalid input. Please enter a number between 1 and 4: ";
            cin.clear();
            cin.ignore(numeric_limits<streamsize>::max(), '\n');
        }

        switch (choice) {
            case 1:
                displayFlights();
                break;
            case 2:
                bookFlight();
                break;
            case 3:
                displayBookings();
                break;
            case 4:
                cout << "Exiting the system. Goodbye!\n";
                return 0;
            default:
                cout << "Invalid choice! Please try again.\n";
        }
    }
}

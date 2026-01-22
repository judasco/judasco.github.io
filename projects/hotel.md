---
layout: project
type: project
image: img/hotel-square.jpg
title: "Hotel Managemment System"
date: 2025-07-20
published: true
labels:
  - Java
  - Data Structures
  - File I/O
summary: "Hotel Management System is a Java-based hotel booking system that manages room reservations, guest information, and transaction logging using 2D arrays and exception handling."
---

<div class="text-center p-4">
  <img width="400px" src="../img/hotel-room.png" class="img-thumbnail" >
</div>

The Hotel Management System is a command-line application developed in Java that simulates a hotel booking system with 50 rooms across 5 floors. The system manages different room types including Single ($155), Double ($170), Triple ($200), Deluxe ($450), and Handicap-accessible ($220) rooms. Users can book and vacate rooms, view occupancy status, and maintain a complete transaction log that persists to a file.

The system implements robust validation and error handling through a custom `RoomException` class, ensuring data integrity for room numbers (101-510), guest names (minimum 2 characters), and prices ($100-$500). The architecture uses a 2D array to represent the hotel's structure, where rows represent floors and columns represent room positions, making it efficient to track and manage room availability.

For this project, I was responsible for implementing the core Hotel class that manages all booking operations and the Room class that validates and stores guest information. I developed the booking algorithm that filters available rooms by type and validates user selections against business rules (such as Deluxe rooms only on the 5th floor and the Handicap room restricted to room 501). I also implemented the transaction logging system using ArrayList and file I/O to persist booking history.

Here is some code that illustrates the room number validation logic:
```java
private int[] getIndicesFromRoomNumber(int roomNumber) throws RoomException {
    int floor = roomNumber / 100;   // Get the floor number
    int col = (roomNumber % 100) - 1;  // To match zero based array index
    int row;
    
    // Map floor numbers to 2D array row indices
    switch (floor) {
        case 1: row = 0; break;
        case 2: row = 1; break;
        case 3: row = 2; break;
        case 4: row = 3; break;
        case 5: row = 4; break;
        default:   
            throw new RoomException("Invalid floor: must be 1 to 5.");
    }
    
    // Check if the column number is valid (must be 0-9 for rooms 01-10)
    if (col < 0 || col >= 10) {
        throw new RoomException("Invalid room number: must end in 01 to 10.");
    }
    return new int[] {row, col};    
}
```

This project enhanced my understanding of object-oriented design principles, exception handling, and data structure implementation in Java. It also improved my ability to translate real-world business requirements into clean, maintainable code.

Source: <a href="https://github.com/judasco/hotel-management-system">github.com/judasco/hotel-management-system</a>

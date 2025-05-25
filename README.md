# Hotel Management System - WinForms

![.NET](https://img.shields.io/badge/.NET-6.0-blue)
![EF Core](https://img.shields.io/badge/EF_Core-7.0-green)
![WinForms](https://img.shields.io/badge/WinForms-Desktop-lightgrey)
![Twilio](https://img.shields.io/badge/Twilio-SMS_API-orange)
![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)

A comprehensive hotel management solution with modern UI (MetroFramework), EF Core data access, and SMS notifications.

## Key Features

### Reservation Management
- **CRUD Operations**: Full lifecycle management of reservations
- **Dynamic Room Allocation**: 
  ```csharp
  // Example of room availability check
  var availableRooms = context.Rooms
      .Where(r => !context.Reservations.Any(res => 
          res.RoomNumber == r.Number && 
          res.ArrivalTime < departureDate && 
          res.LeavingTime > arrivalDate))
      .ToList();

    Check-In/Out System: With real-time status updates

Guest Services

    Integrated Food Ordering:

        Breakfast ($7), Lunch ($15), Dinner ($15)

        Special dietary requirements tracking

    Room Service Management:

        Cleaning requests

        Towel replacement

        Surprise package delivery

Payment Processing

    Secure Transaction Handling:
    csharp

    // Payment validation example
    public bool ValidatePayment(CardDetails card) {
        return card.Expiry > DateTime.Now && 
               card.CVC.Length == 3 &&
               LuhnCheck(card.Number);
    }

    Multi-Payment Support: Credit/Debit cards

Technology Stack
Component	Technology	Version
Frontend	WinForms	6.0
UI Framework	MetroFramework	1.4.0
ORM	Entity Framework Core	7.0
Database	SQL Server	2019+
SMS Gateway	Twilio API	5.0+
Solution Architecture
Layered Architecture

Presentation Layer (WinForms)
  ↓
Business Logic Layer (Services)
  ↓
Data Access Layer (EF Core)
  ↓
Database (SQL Server)

Core Components

    Reservation Engine:

        Handles booking lifecycle

        Manages room inventory

        Processes cancellations

    Notification Service:
    csharp

public class SmsService {
    public void SendConfirmation(string phone, string message) {
        TwilioClient.Init(accountSid, authToken);
        MessageResource.Create(
            body: message,
            from: new PhoneNumber(twilioNumber),
            to: new PhoneNumber(phone));
    }
}

Reporting Module:

    Occupancy reports

    Revenue analytics

    Guest preference tracking

    Diagram.png
    Getting Started
Prerequisites

    Visual Studio 2022+

    SQL Server Express LocalDB

    Twilio Account (for SMS features)

Installation

    Clone repository:
    bash

git clone https://github.com/MarwaMahmoudSoliman/Hotel_system.git
cd Hotel_system/WinFormsApp3

Configure environment variables:
bash

setx TWILIO_SID "your_sid"
setx TWILIO_AUTH_TOKEN "your_token"

Database setup:
bash

dotnet ef database update --context FRONTEND_RESERVATIONContext

Run application:
bash

    dotnet run

Development Guidelines
Code Standards

    Follow Clean Architecture principles

    Use Repository pattern for data access

    Implement proper DI for services

Testing Approach

    Unit Tests: Business logic

    Integration Tests: Database operations

    UI Tests: WinForms automation

csharp

[Test]
public void Should_Calculate_Correct_Bill() {
    var service = new BillingService();
    var result = service.CalculateTotal(100, 20);
    Assert.AreEqual(120, result);
}

License

MIT License - See LICENSE for details.
Contact

Marwa Mahmoud Soliman

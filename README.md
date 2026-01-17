LOCK-IN Locker Management System
A smart locker management system designed to help users book and manage lockers across multiple locations through both console-based and web interfaces.
Features
•	Multiple Locations: Manage lockers at different locations such as Train station, Shopping Centers, Airports etc.
•	Real-time Booking System: Book, track, and release lockers with unique access codes
•	Multiple Locker Sizes: Small, Medium, and Large lockers with price differing from number of hours chosen
•	User Authentication: Role-based access control (Admin/User)
•	Dual Interface: Console client-server application and web-based dashboard
Tech Stack
•	Backend: Java 17 with Socket Programming
•	Frontend: HTML, CSS, JavaScript
•	Database: MySQL 
•	Build Tool: Maven
•	Data Storage: Object Streams, MySQL
•	Network: TCP Socket Server (Port 8080), HTTP Web Server (Port 8082)

Installation
1.	Clone the repository
git clone https://github.com/predutalexia/Locker-System-Management.git
cd Locker-System-Management

2.	Set up MySQL database 
mysql -u root -p
CREATE DATABASE db;
\q
cd database
mysql -u root -p db < locker_system_database.sql
3.	Configure application properties
src/main/java/com/lockers/db/DB_Connection.java:
private static final String URL = "jdbc:mysql://localhost:8082/db";
private static final String USER = " ";
private static final String PASSWORD = "test ";
4.	Build the project
mvn compile
5.	Run the application
Option A: Demo Mode 
java -cp target/classes com.lockers.LockInApp demo
Option B: Web Interface
java -cp target/classes com.lockers.web.WebServer
6.	Access the application
•	Console Client: Follow terminal prompts after starting client mode
•	Web Interface: Open browser to http://localhost:8082
Default Credentials:
•	Admin: admin / admin123
•	User: user / user123
Usage for users
•	Login with your credentials
•	Browse available lockers by location
•	Book a locker by selecting size and duration
•	Receive a unique access code for your locker
•	View your active and past bookings
•	Release lockers when finished


Usage for administrators
•	Access the Admin Panel for system management
•	View all locations, lockers, and bookings
•	Monitor locker availability across all locations
•	Manage user accounts and system configuration
•	Generate reports on booking statistics
Running Different Modes
Demo Mode (with sample data):
java -cp target/classes com.lockers.LockInApp demo
Server Only:
java -cp target/classes com.lockers.LockInApp server
Console Client:
java -cp target/classes com.lockers.LockInApp client
Web Interface:
java -cp target/classes com.lockers.web.WebServer

Core Components
Models:
•	LockerLocation - Physical location with GPS coordinates
•	Locker - Individual locker with size, status, and pricing
•	Booking - Reservation with time tracking and access codes
•	LockerSize - SMALL, MEDIUM, LARGE
•	LockerStatus - AVAILABLE, OCCUPIED, MAINTENANCE
Services:
•	LocationService - Manage locations and lockers
•	BookingService - Handle booking lifecycle
•	ValidationService - Input and business rule validation
•	DatabaseService - MySQL integration
Network:
•	LockerServer - TCP socket server (port 8080)
•	LockerClient - Console-based client
•	WebServer - HTTP server with REST API (port 8082)
•	
API Endpoints
Authentication
•	POST /api/login - User authentication
Locations
•	GET /api/locations – Get all locker locations
Lockers
•	GET /api/lockers - Get all lockers
•	GET /api/locker_location={id} - Get lockers by location
Bookings
•	POST /api/bookings - Create a new booking
•	GET /api/bookings_username={user} - Get user's bookings
•	GET /api/all-bookings - Get all bookings (admin only)
•	POST /api/release-locker - Release an occupied locker
Testing
Run the unit tests: mvn test
Available test classes:
•	BookingTest - Booking validation and lifecycle
•	LockerTest - Locker operations
•	LockerLocationTest - Location management


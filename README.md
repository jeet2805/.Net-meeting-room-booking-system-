# .Net-meeting-room-booking-system-
it is .net project using 2026 vs code for both frontend backend consisting of various features in readme file 
# Meeting Room Booking System

A comprehensive and feature-rich ASP.NET Core MVC application designed to manage meeting room reservations efficiently. The system provides a seamless experience for users to find and book rooms, while offering administrators powerful tools to manage rooms, approve bookings, and monitor usage.

## 🌟 Key Features

### 1. User Roles & Authentication
- **ASP.NET Core Identity Integration**: Secure user registration, login, and robust password policies.
- **Role-Based Access Control**:
  - **Standard Users**: Can view rooms, make bookings, manage their own reservations, and check in.
  - **Administrators**: Have full access to room management, booking approvals, and system audit logs.

### 2. Room Management
- **CRUD Operations**: Admins can Create, Read, Update, and Delete meeting rooms.
- **Room Metadata**: Track details such as Room Name, Capacity, Amenities (e.g., Projector, Whiteboard, Video Conferencing), and operational Status.
- **Visual Room Layouts**: Redesigned room cards with modern UI principles.

### 3. Advanced Booking System
- **Calendar View**: Interactive calendar integration (FullCalendar) to visualize available and booked slots seamlessly.
- **Smart Booking Policies**:
  - **14-Day Advance Rule**: Users can only book up to 14 days in the future.
  - **No Past Dates**: Automatic validation against past dates.
  - **Same-Day Time Logic**: Start time must be strictly before end time, and users cannot book past time slots for the current day.
  - **Conflict Prevention**: Built-in logic to prevent double bookings for the same time and room.
- **Cancellation & Rescheduling Policies**:
  - Users are restricted from modifying or cancelling a booking within **2 hours** of the meeting start time.
- **One-Click Rebooking**: Easy feature to rebook a previously used room directly from the user's booking history.

### 4. Admin Approval Workflow
- Bookings created by standard users are set to `Pending` by default.
- Admins can review all pending bookings and explicitly **Approve** or **Reject** them through a dedicated dashboard interactively.

### 5. Check-In System & QR Codes
- **QR Code Generation**: A unique QR code is dynamically rendered for every approved booking.
- **Check-In Validation**:
  - Check-in window opens exactly **15 minutes** prior to the start time of the meeting.
  - Users can scan their QR code to automatically mark themselves as "Checked In" and confirm attendance.

### 6. Audit & Activity Logs
- Comprehensive logging of all critical actions performed by users and admins, including:
  - Booking Creations, Reschedules, and Cancellations
  - Admin Booking Approvals and Rejections
  - User Check-Ins
- Dedicated audit log page for administrators to review system activity.

### 7. Interactive Admin Dashboard
- **Key Metrics**: View total rooms, total bookings, and pending bookings at a glance.
- **Data Visualizations**: Integrated charts using Chart.js to display booking distributions (e.g., Bookings per Room and Status distributions).

### 8. Background Jobs
- **Booking Reminder Service**: Hosted background service that can automatically process automated reminders and update booking statuses periodically.

### 9. Modern UI / UX Enhancements
- **Dark & Light Mode**: Built-in toggle for users preferring different theme aesthetics.
- Responsive design tailored to both desktop and mobile layouts.
- Comprehensive UI polish including modern dashboard charts and refined interaction states.

## 🛠️ Technology Stack

- **Framework**: .NET 8 / ASP.NET Core MVC
- **Database**: Entity Framework Core with SQL Server
- **Authentication**: ASP.NET Core Identity
- **Front-end**: HTML5, Vanilla CSS, JavaScript, [Chart.js](https://www.chartjs.org/) (for Admin Dashboard), [FullCalendar](https://fullcalendar.io/) (for Visual Booking Calendar)
- **Utilities**: [QRCoder](https://github.com/codebude/QRCoder) for generating QR Code images.

## 🚀 Setup & Installation

Follow these steps to get the system running locally:

### Prerequisites:
- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- SQL Server (or SQL Server Express)

### Installation:

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd MeetingRoomBookingSystem
   ```

2. **Setup Database Connection**:
   Update `appsettings.json` with your valid SQL Server connection string under `DefaultConnection`.

3. **Apply Database Migrations**:
   Open a terminal in the project directory and run:
   ```bash
   dotnet ef database update
   ```
   *Note: Ensure you have the dotnet-ef tool installed (`dotnet tool install --global dotnet-ef`).*

4. **Run the Application**:
   ```bash
   dotnet run
   ```

5. **Initial Data Seeding**:
   The application uses a `DbInitializer` in `Program.cs`. On first run, it will automatically populate default Roles (Admin) and an initial Admin account if one doesn't exist.

6. **Access the Application**:
   Open your browser and navigate to `https://localhost:5001`.

## 🤝 Contribution Guidelines
Contributions are welcome. Please open an issue first to discuss what you would like to change before issuing a pull request. Make sure to update tests as appropriate.

## 📄 License
This project is licensed under the MIT License.

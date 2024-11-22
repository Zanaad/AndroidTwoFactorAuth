# Two-Factor Authentication (2FA) Android App

This Android application demonstrates a Two-Factor Authentication (2FA) system built with Java and Android Studio. The app includes user signup, email verification via OTP, and login functionalities, ensuring a secure authentication process.

## Features

- **User Signup:** Allows users to register with email, password, and personal details.
- **Email Verification:** Sends a One-Time Password (OTP) to the user's email for verification.
- **Secure Login:** Validates user credentials against a local SQLite database.
- **Password Hashing:** Utilizes BCrypt for secure password storage.
- **Resend OTP:** Allows users to request a new OTP if needed.

## Tech Stack

- **Android Studio**
- **Java**
- **SQLite** (for local database)
- **JavaMail API** (for sending OTP emails)

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Zanaad/AndroidTwoFactorAuth.git
```

### 2. Open in Android Studio

- Open **Android Studio** on your machine.
- Click on **File > Open...** from the top menu.
- Navigate to the folder where you cloned the repository and select it.
- Wait for Android Studio to index the project and download any necessary dependencies.

### 3. Enable Email OTP Functionality

- Open the `OTPSender` class and update the following fields with your Gmail account details:

```java
private static final String senderEmail = "your-email@gmail.com";
private static final String senderPassword = "your-email-app-password";
```
- Make sure the Gmail account has "App Passwords" enabled. Refer to the [Google documentation](https://support.google.com/accounts/answer/185833?hl=en) for generating an app password.

### 4. Run the App

- Connect an Android device or use an emulator.
- Click on **Run > Run 'app'** in Android Studio to build and install the application.

## Application Workflow

### Signup Process:
- Users enter their first name, last name, email, and password.
- The system validates the inputs and sends an OTP to the provided email for verification.

### Email Verification:
- Users enter the OTP received in their email.
- If verified, their account details are securely stored in the SQLite database with a hashed password.

### Login:
- Users log in using their email and password.
- The credentials are validated against the stored details in the database.

## Files Overview

| File/Class          | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `SignupActivity`    | Handles user registration and passes user data to OTP verification.         |
| `VerifyOtpActivity` | Manages OTP verification and account creation upon successful verification. |
| `LoginActivity`     | Handles user login and credential validation.                               |
| `OTPSender`         | Sends OTP emails using the JavaMail API.                                    |
| `DB`                | Manages SQLite database operations like storing and validating user data.   |

## Dependencies
- For password hashing. Add the following to your build.gradle file:
  ```bash
 implementation("de.svenkubiak:jBCrypt:0.4.1")
```
- For sending emails. Add the following to your build.gradle file:
  ```bash
    implementation("com.sun.mail:android-mail:1.6.7")
    implementation("com.sun.mail:android-activation:1.6.7")
```
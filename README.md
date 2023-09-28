# VerifyMeAPP


# User Registration and Verification System Documentation

## Table of Contents
- [Introduction](#introduction)
- [User Registration](#user-registration)
- [Database Structure](#database-structure)
- [Verification Process](#verification-process)
  - [Generating Verification Codes](#generating-verification-codes)
  - [Code Validation and Expiry](#code-validation-and-expiry)
- [User Authentication](#user-authentication)
  - [Device Verification](#device-verification)

## Introduction
This document outlines the logic and database structure for a user registration and verification system. The system will be implemented using the following technologies:
- Front-end: HTML, CSS, JavaScript
- Back-end: PHP, MySQL
- User-friendly URLs for a seamless user experience

## User Registration
The user registration process involves collecting and storing user information, including full name, phone number, and password. The registration process is handled by the `register_client` function, which passes user data to the `validate_client_register` function for database insertion.

## Database Structure
The `users` table will store user data with the following columns:
- `id` (auto-incremental)
- `fullname` (varchar 45)
- `phone` (int 11)
- `ip` (text)
- `status`

The `status` field in the `users` table is initially set to 0, indicating that the user account needs validation.

## Verification Process
### Generating Verification Codes
Verification codes will be generated using the `GenerateVerifyCode()` function. These codes will follow a 5-5-5-5-1 format, consisting of 5 numerical digits followed by a hyphen and a single numerical digit.

### Code Validation and Expiry
- Users will receive the verification code via SMS to the phone number provided during registration.
- The verification code must be entered within 10 minutes to validate the user's account.
- If the user does not receive or see the code within 60 seconds, they can request a new code, starting a new countdown for the code's validity.

## User Authentication
### Device Verification
- User IPs will be recorded in the `ip` column of the `users` table.
- If a user logs in from a different IP address than previously registered, they will be prompted to verify the new device.
- The new IP address will be recorded for future reference.

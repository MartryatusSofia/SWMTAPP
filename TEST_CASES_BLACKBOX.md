# COMPREHENSIVE BLACK-BOX TEST CASES - SWMT APPLICATION
## Sistem Web Menggunakan Teknologi (SWMT)

**Date**: May 25, 2026  
**Testing Method**: Black-Box Testing  
**Test Environment**: Web Browser, Local Server  

---

## TABLE OF CONTENTS
1. [Student Authentication](#1-student-authentication)
2. [Teacher/Admin Authentication](#2-teacheradmin-authentication)
3. [Student Test Registration](#3-student-test-registration)
4. [Test Execution & Progress](#4-test-execution--progress)
5. [Teacher Class Management](#5-teacher-class-management)
6. [Student Registration Management](#6-student-registration-management)
7. [Data Export Features](#7-data-export-features)
8. [Super Admin Features](#8-super-admin-features)
9. [Negative Test Cases](#9-negative-test-cases)

---

## 1. STUDENT AUTHENTICATION

### 1.1 Student Registration Form Display

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-001 | Display student registration page | 1. Navigate to `/student/register`<br>2. Verify page loads | Page displays with form fields: Name, Email, Password, Confirm Password. All fields are empty. Submit button is enabled | |
| ST-002 | Check form validation messages exist | 1. Navigate to student registration page<br>2. Inspect form elements | Form fields have proper HTML5 validation attributes and placeholders | |
| ST-003 | Verify form layout is responsive | 1. Navigate to registration page<br>2. Test on mobile, tablet, desktop views | Layout adapts to screen size; form is readable on all devices | |

### 1.2 Student Registration - Valid Cases

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-004 | Register with valid data | 1. Enter name: "John Doe"<br>2. Enter email: "john@example.com"<br>3. Enter password: "password123"<br>4. Confirm password: "password123"<br>5. Click Submit | User account created successfully. Redirected to student dashboard. Session is active with success message "Akun siswa berhasil dibuat." | |
| ST-005 | Register with different valid emails | 1. Register with "student1@mail.com"<br>2. Logout<br>3. Register with "student2@mail.com" | Both accounts created successfully. Can login with each email | |
| ST-006 | Register with special characters in name | 1. Enter name: "José María O'Neill"<br>2. Enter valid email and password<br>3. Submit | User registered successfully with special characters preserved in name | |
| ST-007 | Register with long but valid name | 1. Enter name: "A" * 255 characters<br>2. Enter valid email and password<br>3. Submit | User registered successfully | |
| ST-008 | Register with minimum password length | 1. Enter password: "abcdef" (6 characters)<br>2. Complete other fields with valid data<br>3. Submit | User registered successfully | |
| ST-009 | Verify user role is set to 'student' | 1. Register new student<br>2. Login<br>3. Check database record | User role is set to 'student' in database | |
| ST-010 | Verify password is hashed | 1. Register student<br>2. Check database<br>3. Compare stored password with plain password | Stored password is hashed, not plain text | |

### 1.3 Student Registration - Password Validation

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-011 | Reject registration with mismatched passwords | 1. Enter name and email<br>2. Enter password: "password123"<br>3. Enter confirm password: "password124"<br>4. Submit | Form returns error message. Account not created | |
| ST-012 | Reject password less than 6 characters | 1. Enter password: "pass" (4 characters)<br>2. Enter confirm password: "pass"<br>3. Submit | Validation error displayed: password must be at least 6 characters | |
| ST-013 | Empty password field | 1. Leave password field empty<br>2. Complete other fields<br>3. Submit | Validation error: password is required | |
| ST-014 | Empty confirm password field | 1. Enter password but leave confirm empty<br>2. Submit | Validation error: password confirmation does not match | |

### 1.4 Student Registration - Email Validation

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-015 | Reject invalid email format | 1. Enter email: "notanemail"<br>2. Complete other fields<br>3. Submit | Validation error: email format is invalid | |
| ST-016 | Reject duplicate email | 1. Register with "test@mail.com"<br>2. Logout<br>3. Try register again with same email | Validation error: email already exists | |
| ST-017 | Reject email exceeding max length | 1. Enter email with 256+ characters<br>2. Submit | Validation error: email exceeds maximum length | |
| ST-018 | Accept email with subdomain | 1. Enter email: "user+tag@subdomain.mail.com"<br>2. Complete other fields<br>3. Submit | Email accepted and user registered | |
| ST-019 | Empty email field | 1. Leave email field empty<br>2. Complete other fields<br>3. Submit | Validation error: email is required | |

### 1.5 Student Registration - Name Validation

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-020 | Empty name field | 1. Leave name field empty<br>2. Complete other fields<br>3. Submit | Validation error: name is required | |
| ST-021 | Reject name exceeding 255 characters | 1. Enter name: "A" * 256<br>2. Submit | Validation error: name exceeds maximum length | |
| ST-022 | Accept name with numbers | 1. Enter name: "Student123"<br>2. Complete other fields<br>3. Submit | User registered successfully | |

### 1.6 Student Login - Valid Cases

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-023 | Login with correct credentials | 1. Navigate to `/student/login`<br>2. Enter registered email<br>3. Enter correct password<br>4. Click Login | Login successful. Redirected to student dashboard with message "Login siswa berhasil." | |
| ST-024 | Login and check session | 1. Login as student<br>2. Check session data | Session is created with student user ID and role | |
| ST-025 | Login with remember-me option | 1. Navigate to login page<br>2. Enter valid credentials<br>3. Check "Remember me"<br>4. Login<br>5. Close browser<br>6. Reopen and visit app | User remains logged in (cookie is set) | |
| ST-026 | Multiple student login/logout cycles | 1. Login as student 1<br>2. Logout<br>3. Login as student 2<br>4. Logout<br>5. Login as student 1 again | Each login and logout works correctly; session switches properly | |

### 1.7 Student Login - Invalid Cases

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-027 | Login with non-existent email | 1. Navigate to login page<br>2. Enter email: "nonexistent@mail.com"<br>3. Enter any password<br>4. Click Login | Error message: "Email atau password siswa tidak valid." | |
| ST-028 | Login with wrong password | 1. Enter registered email<br>2. Enter wrong password<br>3. Click Login | Error message: "Email atau password siswa tidak valid." | |
| ST-029 | Empty email field | 1. Leave email field empty<br>2. Enter password<br>3. Click Login | Validation error: email is required | |
| ST-030 | Empty password field | 1. Enter email<br>2. Leave password field empty<br>3. Click Login | Validation error: password is required | |
| ST-031 | Admin account cannot login as student | 1. Register admin account at `/teacher/register`<br>2. Try login with admin credentials at `/student/login` | Login fails with error message | |

### 1.8 Student Logout

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-032 | Logout successfully | 1. Login as student<br>2. Click logout button<br>3. Navigate to protected page | Session is destroyed. Redirected to home page. Cannot access student dashboard | |
| ST-033 | Session invalidation after logout | 1. Login<br>2. Logout<br>3. Check session data | Session data is cleared. CSRF token is regenerated | |
| ST-034 | Cannot access dashboard after logout | 1. Login<br>2. Note dashboard URL<br>3. Logout<br>4. Manually navigate to dashboard URL | Redirected to login page | |

### 1.9 Student Already Logged In Redirects

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ST-035 | Logged-in student redirected from login page | 1. Login as student<br>2. Navigate to `/student/login` | Redirected to student dashboard | |
| ST-036 | Logged-in student redirected from register page | 1. Login as student<br>2. Navigate to `/student/register` | Redirected to student dashboard | |

---

## 2. TEACHER/ADMIN AUTHENTICATION

### 2.1 Teacher Registration

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TA-001 | Display teacher registration page | 1. Navigate to `/teacher/register` | Page displays with form fields: Name, Email, Password, Confirm Password. All fields empty. Submit button enabled | |
| TA-002 | Register teacher with valid data | 1. Enter name: "Budi Guru"<br>2. Enter email: "budi@mail.com"<br>3. Enter password: "teacher123"<br>4. Confirm password: "teacher123"<br>5. Click Submit | Account created successfully. Redirected to teacher login page with success message. Email pre-filled | |
| TA-003 | Verify teacher role is set to 'admin' | 1. Register new teacher<br>2. Check database record | User role is set to 'admin' | |
| TA-004 | Teacher cannot register with duplicate email | 1. Register teacher with "teacher@mail.com"<br>2. Try register another teacher with same email | Second registration fails with error: email already exists | |
| TA-005 | Teacher registration with special characters | 1. Enter name: "Dr. José García-López"<br>2. Enter valid email and password<br>3. Submit | Teacher registered successfully with special characters | |

### 2.2 Teacher Registration Validation

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TA-006 | Empty name field in registration | 1. Leave name empty<br>2. Enter valid email and password<br>3. Submit | Validation error: name is required | |
| TA-007 | Password mismatch during teacher registration | 1. Enter password: "teacher123"<br>2. Enter confirm: "teacher124"<br>3. Submit | Validation error: password confirmation does not match | |
| TA-008 | Teacher registration email format validation | 1. Enter invalid email: "notanemail"<br>2. Complete other fields<br>3. Submit | Validation error: invalid email format | |
| TA-009 | Minimum password length for teacher | 1. Enter password: "teach" (5 characters)<br>2. Submit | Validation error: password must be at least 6 characters | |

### 2.3 Teacher Login - Valid Cases

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TA-010 | Login teacher with valid credentials | 1. Navigate to `/teacher/login`<br>2. Enter registered email<br>3. Enter correct password<br>4. Click Login | Login successful. Redirected to teacher dashboard | |
| TA-011 | Teacher dashboard accessible after login | 1. Login as teacher<br>2. Navigate to `/teacher/dashboard` | Dashboard loads successfully showing student list and class management | |
| TA-012 | Teacher login with remember-me | 1. Login with valid credentials<br>2. Check "Remember me"<br>3. Close browser<br>4. Reopen app | User remains logged in via cookie | |
| TA-013 | Multiple teacher login/logout cycles | 1. Login teacher 1<br>2. Logout<br>3. Login teacher 2<br>4. Verify each sees only their data | Each teacher can only see their own classes and students | |

### 2.4 Teacher Login - Invalid Cases

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TA-014 | Login with non-existent teacher email | 1. Enter email: "nonexistent@mail.com"<br>2. Enter any password<br>3. Click Login | Error: "Email atau password admin salah." | |
| TA-015 | Login with incorrect password | 1. Enter registered email<br>2. Enter wrong password<br>3. Click Login | Error: "Email atau password admin salah." | |
| TA-016 | Student credentials cannot login as teacher | 1. Register and login as student<br>2. Logout<br>3. Try to login with student email at teacher login | Login fails (role mismatch) | |
| TA-017 | Empty email in teacher login | 1. Leave email field empty<br>2. Enter password<br>3. Click Login | Validation error: email is required | |

### 2.5 Teacher Logout

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TA-018 | Logout successfully as teacher | 1. Login as teacher<br>2. Click logout button<br>3. Try access teacher dashboard | Session destroyed. Redirected away. Cannot access protected pages | |
| TA-019 | Session invalidation after teacher logout | 1. Login as teacher<br>2. Logout<br>3. Check session and token | Session cleared. CSRF token regenerated | |

### 2.6 Google OAuth (Both Students & Teachers)

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| GO-001 | Student Google OAuth redirect | 1. Navigate to `/student/register` or `/student/login`<br>2. Click "Login with Google" button | Redirected to Google OAuth login page | |
| GO-002 | Teacher Google OAuth redirect | 1. Navigate to `/teacher/login`<br>2. Click "Login with Google" button | Redirected to Google OAuth login page | |
| GO-003 | Google OAuth callback handling | 1. Complete Google OAuth flow<br>2. Verify callback to application | User logged in or account created. Redirected to appropriate dashboard | |
| GO-004 | Google OAuth creates user account | 1. New Google user completes OAuth flow | User account created with data from Google (name, email) | |

---

## 3. STUDENT TEST REGISTRATION

### 3.1 Test Registration Form Display

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SR-001 | Display test registration form | 1. Login as student<br>2. Navigate to `/register-test` | Form displays with fields: School, Class Code (optional), Class Name, Student Name, Birth Date | |
| SR-002 | Student not logged in redirected | 1. Navigate to `/register-test` without logging in | Redirected to login page or home page | |
| SR-003 | Form prefills student name from profile | 1. Login as student<br>2. Navigate to registration form | Student name field shows logged-in student's name (if stored) | |

### 3.2 Test Registration - Independent Mode

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SR-004 | Register test without class code | 1. Login as student<br>2. Fill form:<br>   - School: "SDN Jakarta"<br>   - Class Name: "Grade 4A"<br>   - Name: "Andi Wijaya"<br>   - Birth Date: "2018-05-15"<br>3. Leave class code empty<br>4. Submit | Test registration created. No teacher_class_id assigned. Redirected to test start page | |
| SR-005 | Register with independent mode indication | 1. Complete independent registration<br>2. Check database | registration.teacher_class_id is NULL | |

### 3.3 Test Registration - With Class Code

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SR-006 | Register test with valid class code | 1. Teacher creates class (generates code e.g., "ABC123")<br>2. Student fills registration form with this code<br>3. Submit | Test registration created with teacher_class_id linked to the class | |
| SR-007 | Invalid class code rejection | 1. Fill registration form<br>2. Enter non-existent code: "XYZ999"<br>3. Submit | Error message: "Kode kelas tidak ditemukan. Silakan cek kembali kode dari guru." | |
| SR-008 | Case-insensitive class code | 1. Teacher creates class with code "ABC123"<br>2. Student enters code: "abc123" (lowercase)<br>3. Submit | Class code found (case-insensitive). Registration successful | |
| SR-009 | Class code with spaces | 1. Teacher class code: "ABC 123" (with space)<br>2. Student enters: "ABC 123"<br>3. Submit | Code accepted after trimming spaces | |

### 3.4 Test Registration - Data Validation

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SR-010 | Empty school field | 1. Leave school field empty<br>2. Fill other fields<br>3. Submit | Validation error: school is required | |
| SR-011 | Empty class name field | 1. Leave class name empty<br>2. Fill other fields<br>3. Submit | Validation error: class name is required | |
| SR-012 | Empty student name field | 1. Leave student name empty<br>2. Fill other fields<br>3. Submit | Validation error: name is required | |
| SR-013 | Empty birth date field | 1. Leave birth date empty<br>2. Fill other fields<br>3. Submit | Validation error: birth date is required | |
| SR-014 | Invalid birth date format | 1. Enter birth date: "15-05-2018"<br>2. Submit | Validation error or automatic format conversion | |
| SR-015 | Future birth date rejection | 1. Enter birth date: tomorrow's date<br>2. Submit | Validation error: birth date cannot be in the future (if validated) | |
| SR-016 | School name max length | 1. Enter school: "A" * 256 characters<br>2. Submit | Validation error: school name exceeds maximum | |
| SR-017 | Class name max length | 1. Enter class name: "B" * 101 characters<br>2. Submit | Validation error: class name exceeds maximum | |

### 3.5 Test Registration - In-Progress Check

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SR-018 | Resume incomplete test registration | 1. Start test registration but do not complete<br>2. Navigate to `/register-test` again<br>3. Try to create new registration | System redirects to in-progress test with message: "Tes sebelumnya belum selesai." | |
| SR-019 | Cannot start new test while incomplete | 1. Have incomplete test (total_poin is NULL)<br>2. Try to register new test | Redirected to incomplete test | |

### 3.6 Test Registration - Session Handling

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SR-020 | Class code passed through session | 1. Student starts with code flow at `/student/start/with-code`<br>2. Fill registration form without code field<br>3. Submit | Form uses session's pending_class_code value | |

---

## 4. TEST EXECUTION & PROGRESS

### 4.1 Test Start Page

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TE-001 | Display test start page | 1. Login as student<br>2. Register for test<br>3. Navigate to `/test/{registration}` | Test start page displays with test instructions and start button | |
| TE-002 | Test guide page display | 1. Navigate to `/test-guide/{registration}` | Test guide/instructions display explaining the test format | |
| TE-003 | Unauthorized access to other's test | 1. Login as student A<br>2. Get registration ID of student B<br>3. Navigate to `/test/{student_b_registration}` | Access denied or error (depending on implementation) | |

### 4.2 Test Progress Tracking

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TE-004 | Save test progress | 1. Student starts test<br>2. Complete first section<br>3. Submit progress via `/test/{registration}/progress`<br>4. POST with progress data | Progress saved to database:<br>- progress_current_section<br>- progress_current_slide<br>- progress_ui_stage<br>- progress_updated_at | |
| TE-005 | Progress persists after page refresh | 1. Complete progress update<br>2. Refresh page<br>3. Navigate back to test | Saved progress is restored | |
| TE-006 | Progress array storage | 1. Submit progress data with arrays (picked_order, section_results)<br>2. Check database | Arrays are serialized and stored correctly | |
| TE-007 | Invalid progress update | 1. Send malformed progress data<br>2. POST to progress endpoint | Error handled gracefully (no crash) | |

### 4.3 Test Fruit Stage

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TE-008 | Display fruit stage | 1. Student completes test sections<br>2. Navigate to `/test-fruit/{registration}` | Fruit stage/final section displays correctly | |
| TE-009 | Fruit stage logic | 1. Complete fruit stage<br>2. Submit<br>3. Check database | Test results are calculated and stored in test_registrations | |

### 4.4 Test Results

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TE-010 | Display test results page | 1. Complete test<br>2. Navigate to `/test-result/{registration}` | Results page displays:<br>- Total score (total_poin)<br>- Correct answers count (orang_benar, urutan_benar)<br>- Wrong answers count (orang_salah, urutan_salah)<br>- Test completion time (tested_at) | |
| TE-011 | Results calculation accuracy | 1. Student completes test with known answers<br>2. View results | Score calculation is accurate | |
| TE-012 | Results date/time display | 1. Complete test<br>2. View results<br>3. Check tested_at timestamp | tested_at is recorded and displayed correctly | |

### 4.5 PDF Result Export

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TE-013 | Export results as PDF | 1. View test results<br>2. Click "Export PDF" or navigate to `/test-result/{registration}/pdf` | PDF file generated and downloaded successfully | |
| TE-014 | PDF contains all result information | 1. Export results to PDF<br>2. Open PDF file | PDF includes:<br>- Student name<br>- School name<br>- Class information<br>- Birth date<br>- Score breakdown<br>- Test date | |
| TE-015 | PDF filename format | 1. Export PDF<br>2. Check filename | Filename follows format: e.g., "Hasil_Test_Andi_20260525.pdf" | |

---

## 5. TEACHER CLASS MANAGEMENT

### 5.1 Create Teacher Class

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TC-001 | Display create class form | 1. Login as teacher<br>2. Navigate to dashboard<br>3. Locate "Create Class" button | Form displays with Class Name field | |
| TC-002 | Create class with valid name | 1. Login as teacher<br>2. Fill class name: "Grade 5A"<br>3. Submit | Class created successfully. Unique 6-character code generated automatically<br>Success message displays: "Kelas berhasil dibuat. Kode kelas: ABC123" | |
| TC-003 | Verify class code generated | 1. Create class<br>2. Check database<br>3. Check success message | 6-character random code is generated (uppercase letters/numbers) | |
| TC-004 | Class code uniqueness | 1. Create first class (code: "ABC123")<br>2. Create many more classes<br>3. Check no duplicate codes | All class codes are unique | |
| TC-005 | Class code format | 1. Create multiple classes<br>2. Check generated codes | Codes contain only uppercase alphanumeric characters, 6 characters long | |
| TC-006 | Create class with special characters in name | 1. Enter class name: "Grade 5A-B/Advanced"<br>2. Submit | Class created successfully with special characters | |
| TC-007 | Create class with long name | 1. Enter class name: "A" * 255 characters<br>2. Submit | Class created successfully (if within max length) | |

### 5.2 Create Class Validation

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TC-008 | Empty class name field | 1. Leave class name empty<br>2. Submit | Validation error: class name is required | |
| TC-009 | Class name exceeds max length | 1. Enter class name: "A" * 256 characters<br>2. Submit | Validation error: name exceeds maximum length | |

### 5.3 List Teacher Classes

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TC-010 | Display teacher's classes list | 1. Login as teacher<br>2. Navigate to dashboard | Classes list displays all created classes with:<br>- Class name<br>- Class code<br>- Number of students | |
| TC-011 | Pagination for classes | 1. Teacher creates 3+ classes<br>2. View dashboard<br>3. Check pagination | Pagination works (if more than 2 classes) | |
| TC-012 | Search classes by name | 1. Teacher has multiple classes<br>2. Enter search term: "Grade 5"<br>3. Submit search | Only classes matching "Grade 5" display | |
| TC-013 | Search classes by code | 1. Teacher has multiple classes<br>2. Enter search term: class code e.g., "ABC123"<br>3. Submit search | Class with matching code displays | |
| TC-014 | Each teacher sees only own classes | 1. Login as teacher A, create classes<br>2. Logout<br>3. Login as teacher B, create classes<br>4. Each checks their dashboard | Teacher A only sees their classes. Teacher B only sees theirs. No cross-viewing | |

### 5.4 Delete Teacher Class

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TC-015 | Delete class successfully | 1. Login as teacher<br>2. Create a class<br>3. Click delete button on class<br>4. Confirm deletion | Class deleted from database. Removed from list. Success message displays | |
| TC-016 | Authorization check for delete | 1. Login as teacher A<br>2. Get class ID of teacher B<br>3. Send DELETE request to `/teacher/classes/{teacher_b_class}` | Delete fails. Authorization error | |
| TC-017 | Delete class with registered students | 1. Create class<br>2. Students register for this class<br>3. Delete class<br>4. Check student registrations | Students' teacher_class_id becomes NULL (or referential integrity handled) | |

---

## 6. STUDENT REGISTRATION MANAGEMENT

### 6.1 View Student Registrations (Teacher View)

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TR-001 | Teacher views all student registrations | 1. Login as teacher<br>2. Navigate to dashboard<br>3. View registrations list | All students registered (with or without class code) display with:<br>- Student name<br>- School<br>- Class name<br>- Birth date<br>- Test status | |
| TR-002 | Filter registrations by class | 1. Teacher has students in multiple classes<br>2. Select specific class from filter<br>3. View | Only students from selected class display | |
| TR-003 | Search registrations by name | 1. Enter search: student's name<br>2. Submit | Registrations matching name display | |
| TR-004 | Search by school name | 1. Enter search: school name<br>2. Submit | Registrations from that school display | |
| TR-005 | Each teacher sees only their students | 1. Teacher A creates class, students register<br>2. Teacher B has their students<br>3. Each logs in<br>4. Check registrations list | Teacher A sees only their students. Teacher B sees only theirs | |

### 6.2 Edit Student Registration

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TR-006 | Display student edit form | 1. Login as teacher<br>2. Click edit on student<br>3. Navigate to `/teacher/registrations/{registration}/edit` | Form displays with student data pre-filled:<br>- Name<br>- School<br>- Class<br>- Birth date | |
| TR-007 | Edit student information | 1. Open student edit form<br>2. Change name: "Old Name" → "New Name"<br>3. Change school<br>4. Save | Changes saved successfully. Data updated in database | |
| TR-008 | Edit with valid data | 1. Edit student<br>2. Fill all fields with valid data<br>3. Save | Student record updated. Success message displays | |
| TR-009 | Edit validation | 1. Try to save with empty required field<br>2. Submit | Validation error: required field cannot be empty | |

### 6.3 Delete Student Registration

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TR-010 | Delete student registration | 1. Login as teacher<br>2. Locate student<br>3. Click delete<br>4. Confirm deletion | Registration deleted. Removed from list | |
| TR-011 | Authorization for delete | 1. Login as teacher A<br>2. Get student ID registered to teacher B<br>3. Send DELETE request | Delete fails. Authorization error | |
| TR-012 | Delete non-existent registration | 1. Send DELETE to `/teacher/registrations/99999`<br>2. Submit | 404 error or appropriate error message | |

### 6.4 Teacher Profile Management

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| TR-013 | View teacher profile | 1. Login as teacher<br>2. Click on profile option<br>3. Navigate to `/teacher/profile` | Profile page displays with teacher's current information | |
| TR-014 | Edit teacher profile | 1. Navigate to profile page<br>2. Edit name or email<br>3. Save | Profile updated successfully | |
| TR-015 | Profile validation | 1. Try to update with invalid email<br>2. Submit | Validation error: invalid email format | |

---

## 7. DATA EXPORT FEATURES

### 7.1 Teacher PDF Export

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| DE-001 | Generate teacher export PDF | 1. Login as teacher<br>2. Navigate to `/teacher/export-pdf`<br>3. Download PDF | PDF file generated and downloaded | |
| DE-002 | PDF contains teacher's students data | 1. Export PDF as teacher<br>2. Open file<br>3. Check content | PDF includes list of all teacher's students with:<br>- Names<br>- Schools<br>- Classes<br>- Test scores | |
| DE-003 | PDF filename format for teacher | 1. Export PDF<br>2. Check filename | Filename includes teacher's name and date | |
| DE-004 | Only teacher's data in export | 1. Teacher A exports PDF<br>2. Check contents | PDF contains only teacher A's students, not other teachers' | |

### 7.2 Super Admin PDF Export

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| DE-005 | Super admin exports all data PDF | 1. Login as super admin<br>2. Navigate to `/superadmin/export-pdf` | PDF generated and downloaded | |
| DE-006 | Super admin PDF contains all students | 1. Export PDF as super admin<br>2. Open PDF | PDF includes all students from all teachers | |
| DE-007 | PDF filename for super admin | 1. Export PDF<br>2. Check filename | Filename includes "Global" or "Laporan_Global_SWMT_" with date | |

---

## 8. SUPER ADMIN FEATURES

### 8.1 Super Admin Dashboard

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SA-001 | Display super admin dashboard | 1. Login with super admin account<br>2. Navigate to `/superadmin/dashboard` | Dashboard displays with:<br>- Total teachers count<br>- Total classes count<br>- Total students count<br>- List of all registrations | |
| SA-002 | Super admin sees all data | 1. Login as super admin<br>2. Check dashboard | Dashboard shows students from all teachers | |
| SA-003 | Dashboard statistics accuracy | 1. Count teachers, classes, students manually<br>2. Compare with dashboard display | Numbers match actual database records | |

### 8.2 Super Admin Search & Filter

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SA-004 | Search registrations by student name | 1. Enter search term: student name<br>2. Submit | Results show matching students | |
| SA-005 | Search by school name | 1. Enter search term: school name<br>2. Submit | Results show students from that school | |
| SA-006 | Pagination in super admin view | 1. Navigate super admin dashboard<br>2. Check pagination | Multiple pages if more than 15 registrations | |

### 8.3 Super Admin Delete Registration

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SA-007 | Super admin delete any student | 1. Login as super admin<br>2. Locate student<br>3. Click delete<br>4. Confirm | Student deleted successfully. Removed from list | |
| SA-008 | Delete non-existent record | 1. Send DELETE to `/superadmin/registrations/99999` | 404 or appropriate error | |

---

## 9. NEGATIVE TEST CASES

### 9.1 Authentication & Authorization Attacks

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| SEC-001 | SQL Injection in login email | 1. Email field: `" OR "1"="1`<br>2. Click login | Login fails. System not compromised | |
| SEC-002 | XSS attack in name field | 1. Register with name: `<script>alert('xss')</script>`<br>2. View profile | Script not executed. Name displayed as plain text | |
| SEC-003 | CSRF token missing | 1. Disable CSRF middleware (temporarily for test)<br>2. Submit form without token | Request rejected | |
| SEC-004 | Session hijacking prevention | 1. Get another user's session ID<br>2. Try to use it | Session invalid. Cannot access as other user | |
| SEC-005 | Unauthorized access to admin routes | 1. Login as student<br>2. Try to navigate to `/teacher/dashboard` | Access denied. Redirected to unauthorized page | |

### 9.2 Data Validation Edge Cases

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| EDG-001 | Extremely long email | 1. Email field: "a" * 1000 + "@mail.com"<br>2. Submit | Validation error: email exceeds maximum length | |
| EDG-002 | Unicode characters in fields | 1. Name: "中文名字"<br>2. School: "Σχολή Αθήνας" (Greek)<br>3. Submit | Fields accept Unicode correctly (if intended) or validation error | |
| EDG-003 | NULL bytes injection | 1. Name field: "Name%00.txt"<br>2. Submit | NULL byte handled safely | |
| EDG-004 | Negative birth date handling | 1. Birth date: 1900-01-01<br>2. Submit | Handled appropriately (accepted or rejected based on logic) | |

### 9.3 Concurrency & Race Conditions

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| CONC-001 | Simultaneous registration attempts | 1. Two users try to register with same email simultaneously<br>2. Check database | Only one registration succeeds. No duplicate entry | |
| CONC-002 | Simultaneous progress updates | 1. Submit test progress from multiple sources simultaneously | Last update wins (or conflict handled). No data corruption | |
| CONC-003 | Class deletion while student registering | 1. Teacher deletes class<br>2. Simultaneously, student tries to register with that code | Race condition handled. Student either gets error or registers to deleted class | |

### 9.4 File & Resource Handling

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| FILE-001 | Large file upload (if applicable) | 1. Try to upload file > 10MB<br>2. Submit | Upload fails. Error message: file too large | |
| FILE-002 | Invalid file type | 1. Try to upload .exe or .php file<br>2. Submit | Upload rejected | |
| FILE-003 | PDF generation with special characters | 1. Student name with special characters<br>2. Export to PDF | PDF generated correctly with special characters | |

### 9.5 State Management Issues

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| STATE-001 | Refresh during form submission | 1. Fill registration form<br>2. Click submit<br>3. Immediately refresh page | Form submission completes or rolls back. No partial data | |
| STATE-002 | Browser back button after logout | 1. Login<br>2. Logout<br>3. Click browser back button | Cannot access logged-in content. Redirected to login | |
| STATE-003 | Multiple tabs same user | 1. Login in tab 1<br>2. Logout in tab 2<br>3. Try action in tab 1 | Session invalidated. Tab 1 redirects to login | |

### 9.6 Error Handling

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ERR-001 | Database connection failure | 1. Simulate database down<br>2. Try to load dashboard | User-friendly error message. No SQL errors exposed | |
| ERR-002 | Timeout during PDF generation | 1. Generate very large PDF<br>2. Wait for timeout | Graceful timeout. User notified. Not crashing | |
| ERR-003 | Missing required environment variables | 1. Remove Google OAuth credentials<br>2. Try Google login | Graceful error. App doesn't crash | |
| ERR-004 | Invalid registration ID access | 1. Navigate to `/test/999999` (non-existent)<br>2. Load page | 404 error or not found message | |

---

## 10. PERFORMANCE & BOUNDARY TESTS

### 10.1 Load Testing

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| PERF-001 | Multiple concurrent logins | 1. 50 users login simultaneously<br>2. Measure response time | All logins complete within acceptable time. No timeouts | |
| PERF-002 | Dashboard with 1000 registrations | 1. Load teacher dashboard with 1000 student registrations | Page loads and displays pagination. Response time acceptable | |
| PERF-003 | Search with large dataset | 1. Search among 10000 records<br>2. Measure response time | Search completes within 2-3 seconds | |

### 10.2 Data Volume Tests

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| VOL-001 | Maximum students per class | 1. Create class<br>2. Register 10000 students to same class<br>3. Display class page | Page loads. No performance degradation | |
| VOL-002 | Teacher with maximum classes | 1. Teacher creates 500 classes<br>2. Navigate to dashboard | Dashboard loads with pagination | |

### 10.3 Boundary Value Testing

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| BND-001 | Minimum values | 1. Test with all minimum valid values:<br>   - Name: "A" (1 character)<br>   - Email: "a@b" (minimal valid)<br>   - Password: "abcdef" (6 chars)<br>2. Submit | Accepted | |
| BND-002 | Maximum values | 1. Test with all maximum valid values:<br>   - Name: "A" * 255<br>   - Email: "a" * 243 + "@mail.com" (255 chars)<br>   - Password: "A" * 255<br>2. Submit | Accepted | |
| BND-003 | Class code edge cases | 1. Test 6-character codes with all alphanumeric combinations<br>2. Test collision scenarios | All unique. No collisions | |

---

## 11. USER INTERFACE & USABILITY TESTS

### 11.1 Form Usability

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| UI-001 | Tab order in forms | 1. Open registration form<br>2. Press Tab multiple times<br>3. Verify tab order | Tab order is logical (left-to-right, top-to-bottom) | |
| UI-002 | Required field indicators | 1. Open any form<br>2. Check for required field marks | Required fields clearly marked (asterisk or similar) | |
| UI-003 | Error message clarity | 1. Trigger various validation errors<br>2. Check messages | Error messages are clear and actionable. User knows how to fix | |

### 11.2 Responsiveness

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| UI-004 | Mobile view (320px width) | 1. Open app on mobile device<br>2. Navigate pages | All pages render correctly. No horizontal scroll | |
| UI-005 | Tablet view (768px width) | 1. Test on tablet | Layout optimized for tablet. Readable text | |
| UI-006 | Desktop view (1920px width) | 1. Test on 1920px+ screen | Layout uses available space efficiently | |

### 11.3 Accessibility

| Test ID | Test Case | Test Steps | Expected Result | Status |
|---------|-----------|-----------|-----------------|--------|
| ACC-001 | Keyboard navigation | 1. Use only keyboard (no mouse)<br>2. Navigate all pages<br>3. Complete a form | All functions accessible via keyboard | |
| ACC-002 | Color contrast | 1. Check text vs background contrast | Contrast ratio meets WCAG AA standard (4.5:1 for text) | |
| ACC-003 | Alt text for images | 1. Inspect all images<br>2. Check alt attributes | All images have descriptive alt text | |

---

## 12. TEST EXECUTION TRACKING

### Test Execution Summary

| Category | Total Tests | Passed | Failed | Blocked | Notes |
|----------|-------------|--------|--------|---------|-------|
| Student Authentication | 36 | | | | |
| Teacher Authentication | 20 | | | | |
| Test Registration | 20 | | | | |
| Test Execution | 15 | | | | |
| Class Management | 17 | | | | |
| Registration Management | 15 | | | | |
| Data Export | 7 | | | | |
| Super Admin | 8 | | | | |
| Negative Cases | 30 | | | | |
| Performance | 6 | | | | |
| UI/Usability | 9 | | | | |
| **TOTAL** | **183** | | | | |

---

## 13. DEFECT REPORTING TEMPLATE

When a test fails, use this template:

```
DEFECT ID: [DEF-XXX]
TEST ID: [Related test case ID]
SEVERITY: [Critical/High/Medium/Low]
PRIORITY: [P1/P2/P3/P4]

TITLE: [Brief description]

DESCRIPTION:
[What is the defect?]

STEPS TO REPRODUCE:
1. [Step 1]
2. [Step 2]
3. [Step 3]

EXPECTED RESULT:
[What should happen]

ACTUAL RESULT:
[What actually happened]

ENVIRONMENT:
- OS: [Windows/macOS/Linux]
- Browser: [Chrome/Firefox/Safari]
- Version: [Version]
- Server: [Local/Staging/Production]

ATTACHMENTS:
- [Screenshot/Video/Log file if applicable]

ASSIGNED TO:
STATUS: Open/In Progress/Resolved
```

---

## 14. TEST PREREQUISITES & SETUP

### Initial Setup Required:
1. ✓ Database properly migrated with all tables
2. ✓ Environment variables configured (.env file)
3. ✓ Google OAuth credentials (if testing OAuth features)
4. ✓ PDF library configured (DomPDF)
5. ✓ File storage configured
6. ✓ Mail service (if email notifications needed)
7. ✓ Session storage configured

### Test Data Setup:
- Create test user accounts (students, teachers, super admin)
- Pre-populate classes with test data
- Create test registrations with various states

### Browser & Tools:
- Chrome/Firefox/Safari (latest versions)
- Browser DevTools for console errors
- Postman for API testing (optional)
- Database viewer (phpMyAdmin/DBeaver)

---

## 15. TEST SIGN-OFF

| Role | Name | Date | Signature |
|------|------|------|-----------|
| QA Lead | | | |
| Development Lead | | | |
| Project Manager | | | |

---

**Document Version**: 1.0  
**Created Date**: May 25, 2026  
**Last Updated**: May 25, 2026  
**Test Framework**: Black-Box Testing Methodology  
**Total Test Cases**: 183  

---

## NOTES & RECOMMENDATIONS

1. **Test Priority**: Execute critical path tests first (Authentication, Test Registration, Test Execution)
2. **Regression Testing**: When bugs are fixed, run all related test cases
3. **Automation Candidates**: Form submission tests, search filters, pagination
4. **Manual Testing**: UI/UX tests, complex business logic verification
5. **Test Environment**: Use staging environment for comprehensive testing before production
6. **Data Cleanup**: After each test run, clean up test data to maintain database integrity
7. **Performance Baseline**: Establish performance baselines before optimization
8. **Documentation**: Keep detailed logs of all test executions and defects found

---

**END OF TEST CASE DOCUMENT**

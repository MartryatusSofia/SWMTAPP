# TEST CASE EXECUTION FORM - SWMT APPLICATION
## Sistem Web Menggunakan Teknologi

**Tanggal**: 25 Mei 2026  
**Metode Testing**: Black-Box Testing  
**Nama Tester**: ________________________  
**Ttd**: ________________________  

---

## 1️⃣ STUDENT AUTHENTICATION (Autentikasi Siswa)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 1 | Student Register - Valid Data | Navigate to /student/register, fill form with valid data (name, email, password, confirm password), submit | User account created successfully. Redirected to student dashboard. Success message displayed: "Akun siswa berhasil dibuat." | | PASS / FAIL |
| 2 | Student Register - Empty Name | Leave name field empty, complete other fields, submit | Validation error: "name is required" | | PASS / FAIL |
| 3 | Student Register - Empty Email | Leave email field empty, complete other fields, submit | Validation error: "email is required" | | PASS / FAIL |
| 4 | Student Register - Invalid Email | Enter invalid email format (e.g., "notanemail"), complete other fields, submit | Validation error: "email format is invalid" | | PASS / FAIL |
| 5 | Student Register - Empty Password | Complete name and email, leave password empty, submit | Validation error: "password is required" | | PASS / FAIL |
| 6 | Student Register - Password Mismatch | Enter password: "password123", confirm: "password124", submit | Validation error: "password confirmation does not match" | | PASS / FAIL |
| 7 | Student Register - Password Too Short | Enter password: "pass" (4 characters), confirm same, submit | Validation error: "password must be at least 6 characters" | | PASS / FAIL |
| 8 | Student Register - Duplicate Email | Register with email "test@mail.com", logout, try register again with same email | Validation error: "email already exists" | | PASS / FAIL |
| 9 | Student Login - Valid Credentials | Navigate to /student/login, enter registered email and correct password, click login | Login successful. Redirected to student dashboard. Message: "Login siswa berhasil." | | PASS / FAIL |
| 10 | Student Login - Wrong Password | Enter registered email with wrong password, click login | Error message: "Email atau password siswa tidak valid." | | PASS / FAIL |
| 11 | Student Login - Non-existent Email | Enter non-existent email "notexist@mail.com", enter password, click login | Error message: "Email atau password siswa tidak valid." | | PASS / FAIL |
| 12 | Student Logout | Login as student, click logout button | Session destroyed. Redirected away from dashboard. Cannot access protected pages | | PASS / FAIL |

---

## 2️⃣ TEACHER/ADMIN AUTHENTICATION (Autentikasi Guru)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 13 | Teacher Register - Valid Data | Navigate to /teacher/register, fill form with valid name, email, password, confirm password, submit | Account created. Redirected to teacher login page with success message. Email pre-filled | | PASS / FAIL |
| 14 | Teacher Register - Empty Name | Leave name empty, complete other fields, submit | Validation error: "name is required" | | PASS / FAIL |
| 15 | Teacher Register - Password Mismatch | Enter password: "teacher123", confirm: "teacher124", submit | Validation error: "password confirmation does not match" | | PASS / FAIL |
| 16 | Teacher Register - Duplicate Email | Register with "teacher@mail.com", logout, try register with same email again | Validation error: "email already exists" | | PASS / FAIL |
| 17 | Teacher Login - Valid Credentials | Navigate to /teacher/login, enter registered email and correct password, click login | Login successful. Redirected to teacher dashboard | | PASS / FAIL |
| 18 | Teacher Login - Wrong Password | Enter registered email with wrong password, click login | Error message: "Email atau password admin salah." | | PASS / FAIL |
| 19 | Teacher Login - Non-existent Email | Enter non-existent email, enter password, click login | Error message: "Email atau password admin salah." | | PASS / FAIL |
| 20 | Teacher Logout | Login as teacher, click logout button | Session destroyed. Redirected away. Cannot access teacher dashboard | | PASS / FAIL |

---

## 3️⃣ STUDENT TEST REGISTRATION (Pendaftaran Test Siswa)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 21 | Test Reg - Not Logged In | Navigate to /register-test without logging in | Redirected to login page | | PASS / FAIL |
| 22 | Test Reg - Valid Data (No Code) | Login as student, fill: school, class name, name, birth date (leave class code empty), submit | Registration created successfully. No teacher_class_id assigned. Redirected to test start page | | PASS / FAIL |
| 23 | Test Reg - Empty School | Leave school field empty, complete other fields, submit | Validation error: "school is required" | | PASS / FAIL |
| 24 | Test Reg - Empty Class Name | Leave class name empty, complete other fields, submit | Validation error: "class name is required" | | PASS / FAIL |
| 25 | Test Reg - Empty Student Name | Leave name field empty, complete other fields, submit | Validation error: "name is required" | | PASS / FAIL |
| 26 | Test Reg - Empty Birth Date | Leave birth date empty, complete other fields, submit | Validation error: "birth date is required" | | PASS / FAIL |
| 27 | Test Reg - Valid Class Code | Teacher creates class with code (e.g., "ABC123"), student enters this code, submit | Registration created with teacher_class_id linked to the class | | PASS / FAIL |
| 28 | Test Reg - Invalid Class Code | Enter non-existent code "XYZ999", submit | Error message: "Kode kelas tidak ditemukan. Silakan cek kembali kode dari guru." | | PASS / FAIL |

---

## 4️⃣ CLASS MANAGEMENT (Manajemen Kelas Guru)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 29 | Create Class - Valid Data | Login as teacher, fill class name "Grade 5A", submit | Class created. Unique 6-char code auto-generated. Success message: "Kelas berhasil dibuat. Kode kelas: ABC123" | | PASS / FAIL |
| 30 | Create Class - Empty Name | Leave class name empty, submit | Validation error: "class name is required" | | PASS / FAIL |
| 31 | View Classes List | Login as teacher, navigate to dashboard | All teacher's created classes display with name, code, and student count | | PASS / FAIL |
| 32 | Search Classes by Name | Teacher has multiple classes, enter search term "Grade 5", submit | Only classes matching "Grade 5" display in results | | PASS / FAIL |
| 33 | Delete Class | Teacher creates class, clicks delete button, confirms deletion | Class deleted from database and removed from list. Success message displays | | PASS / FAIL |
| 34 | Only Own Classes Visible | Teacher A creates classes, logout. Teacher B creates classes. Each logs in and checks | Teacher A only sees their classes. Teacher B only sees theirs. No cross-viewing | | PASS / FAIL |

---

## 5️⃣ STUDENT REGISTRATION MANAGEMENT (Manajemen Registrasi Siswa)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 35 | View Student Registrations | Teacher logs in, navigates to dashboard, views registrations list | All teacher's student registrations display with: name, school, class, birth date, test status | | PASS / FAIL |
| 36 | Search Student by Name | Teacher has multiple students, enter search term "Andi", submit | Registrations matching "Andi" display in results | | PASS / FAIL |
| 37 | Filter Students by Class | Teacher has students in multiple classes, select specific class from filter dropdown | Only students from selected class display | | PASS / FAIL |
| 38 | Edit Student Registration | Teacher clicks edit on student, changes name from "Old Name" to "New Name", save | Student data updated successfully. Changes reflected in list | | PASS / FAIL |
| 39 | Delete Student Registration | Teacher clicks delete on student, confirms deletion | Student registration deleted from database. Removed from list | | PASS / FAIL |
| 40 | Only Own Students Visible | Teacher A has students, Teacher B has students. Each logs in and checks | Teacher A only sees their students. Teacher B only sees theirs | | PASS / FAIL |

---

## 6️⃣ TEST EXECUTION (Eksekusi Test)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 41 | Display Test Start Page | Login as student, register for test, navigate to /test/{registration} | Test start page displays with instructions and start button | | PASS / FAIL |
| 42 | Save Test Progress | Student starts test, completes first section, submit progress to /test/{registration}/progress | Progress saved: current_section, current_slide, ui_stage, updated_at timestamp recorded | | PASS / FAIL |
| 43 | Resume Test Session | Student completes progress update, page refreshes, navigates back to test | Saved progress is restored. Test continues from where it left off | | PASS / FAIL |
| 44 | Prevent In-Progress Test Override | Student has incomplete test (total_poin is NULL), navigates to /register-test again | Redirected to in-progress test with message: "Tes sebelumnya belum selesai." | | PASS / FAIL |
| 45 | Display Test Results | Student completes test, navigate to /test-result/{registration} | Results page displays: total score, correct answers (orang_benar, urutan_benar), wrong answers (orang_salah, urutan_salah), tested_at timestamp | | PASS / FAIL |
| 46 | Export Results to PDF | View test results, click "Export PDF" or navigate to /test-result/{registration}/pdf | PDF file generated and downloaded successfully with all result information | | PASS / FAIL |

---

## 7️⃣ DATA EXPORT (Ekspor Data)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 47 | Teacher Export PDF | Teacher logs in, navigate to /teacher/export-pdf | PDF file generated and downloaded containing teacher's students data | | PASS / FAIL |
| 48 | Teacher PDF Contains Only Own Data | Teacher A exports PDF, Teacher B exports PDF, check contents | Teacher A's PDF contains only their students. Teacher B's PDF contains only theirs | | PASS / FAIL |
| 49 | Super Admin Export PDF | Super admin logs in, navigate to /superadmin/export-pdf | PDF generated and downloaded containing ALL students data from all teachers | | PASS / FAIL |

---

## 8️⃣ SUPER ADMIN FEATURES (Fitur Super Admin)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 50 | Super Admin Dashboard | Super admin logs in, navigate to /superadmin/dashboard | Dashboard displays: total teachers count, total classes count, total students count, list of all registrations | | PASS / FAIL |
| 51 | Super Admin Sees All Data | Super admin views dashboard, teacher A has 5 students, teacher B has 3 students | Dashboard shows all 8 students from both teachers | | PASS / FAIL |
| 52 | Super Admin Search Students | Super admin enters search term "Andi", submit | Results show all students named "Andi" from all teachers | | PASS / FAIL |
| 53 | Super Admin Delete Any Student | Super admin clicks delete on any student, confirms deletion | Student deleted from database. Removed from list | | PASS / FAIL |

---

## 9️⃣ SECURITY & EDGE CASES (Keamanan & Kasus Khusus)

| No. | Skenario Pengujian | Test Case | Hasil yang Diharapkan | Hasil Pengujian | Kesimpulan |
|-----|-------------------|-----------|----------------------|-----------------|-----------|
| 54 | Student Cannot Access Teacher Routes | Login as student, try navigate to /teacher/dashboard | Access denied. Redirected to unauthorized page or home | | PASS / FAIL |
| 55 | Teacher Cannot Access Super Admin Routes | Login as teacher, try navigate to /superadmin/dashboard | Access denied. Error message: "Anda tidak memiliki akses ke halaman Super Admin." | | PASS / FAIL |
| 56 | SQL Injection in Email | Try email: `" OR "1"="1` in login form, submit | Login fails. System not compromised. SQL error not displayed | | PASS / FAIL |
| 57 | XSS Attack in Name Field | Register with name: `<script>alert('xss')</script>`, check profile | Script not executed. Name displayed as plain text or HTML-encoded | | PASS / FAIL |
| 58 | Concurrent Registration Attempts | Two users try to register with same email simultaneously | Only one registration succeeds. No duplicate email in database | | PASS / FAIL |
| 59 | Invalid Registration ID Access | Navigate to /test/999999 (non-existent registration) | 404 error or "Not found" message. No system error exposed | | PASS / FAIL |

---

## 📊 RINGKASAN PENGUJIAN

### Statistik Pengujian

| Metrik | Nilai |
|--------|-------|
| Total Test Cases | 59 |
| Test Cases PASS | ___ |
| Test Cases FAIL | ___ |
| Test Cases BLOCKED | ___ |
| Success Rate | __% |

### Informasi Pengujian

**Tanggal Pengujian**: ____________________  
**Nama Tester**: ____________________  
**Durasi Pengujian**: ____________________  

### Catatan Defect (Jika Ada)

| No. Defect | Test ID | Severity | Deskripsi | Status |
|-----------|---------|----------|-----------|--------|
| DEF-001 | | | | |
| DEF-002 | | | | |
| DEF-003 | | | | |

### Catatan Umum

_________________________________________________________________

_________________________________________________________________

_________________________________________________________________

### Rekomendasi

_________________________________________________________________

_________________________________________________________________

### Tanda Tangan

**Tester**: ________________________  
**Date**: ________________________  

**QA Lead**: ________________________  
**Date**: ________________________  

---

**END OF TEST EXECUTION FORM**

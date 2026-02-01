                                        MAFFEW HOSPITAL DATABASE

>>>>>>>>>>>THE UNCLEAN DATA SET AFTER CLEANING WITH MICROSOFT EXCEL

patients id full_name gender age state phone

1 Amina Bello Female 29 Lagos 8031234567 2 John Okeke Male 41 Enugu 8039876543 3 Grace Musa Female 35 Abuja 8035551234 4 David Lawal Male 52 Oyo 8037778899 5 Fatima Sule Female 23 Kano 8036667777 6 Peter Obi Male 47 Anambra 8034445555 7 Ngozi Eze Female 31 Imo 8032221111 8 Samuel Dan Male 38 Kaduna 8039990000 9 Ruth James Female 27 Rivers 8031112222 10 Ibrahim Sadiq Male 44 Katsina 8033334444

doctor_id doctor_name specialty years_experience

101 Dr. Adeyemi Cardiology 12 102 Dr. Hassan Neurology 9 103 Dr. Okafor Pediatrics 7 104 Dr. Musa General Medicine 15 105 Dr. Bello Orthopedics 10

appointment_id patient_id doctor_id visit_date diagnosis fee

1001 1 104 1/10/2025 Malaria 15000 1002 2 101 1/11/2025 Hypertension 25000 1003 3 103 1/12/2025 Child Fever 12000 1004 4 105 1/13/2025 Fracture 30000 1005 5 104 1/14/2025 Typhoid 18000 1006 6 102 1/15/2025 Migraine 20000 1007 7 101 1/16/2025 Heart Check 27000 1008 8 104 1/17/2025 Infection 16000 1009 9 103 1/18/2025 Flu 11000 1010 10 105 1/19/2025 Back Pain 22000

>>>>>>>>SQL QUERIES FOR DATA DIGGING

SELECT COUNT(*) AS total_patients FROM patients; 6️⃣ Average patient age SELECT AVG(age) AS avg_age FROM patients;

7️⃣ Total appointment fees collected

SELECT SUM(fee) AS total_revenue FROM appointments;

8️⃣ Number of patients per state

SELECT state, COUNT(*) AS patient_count FROM patients GROUP BY state;

9️⃣ Doctors and number of appointments handled

SELECT d.doctor_name, COUNT(a.appointment_id) AS total_visits FROM doctors d LEFT JOIN appointments a ON d.doctor_id = a.doctor_id GROUP BY d.doctor_name; 🟠 Join Queries (Very Important for Projects)

🔟 Show appointment details with patient & doctor

SELECT p.full_name, d.doctor_name, a.visit_date, a.diagnosis, a.fee FROM appointments a JOIN patients p ON a.patient_id = p.patient_id JOIN doctors d ON a.doctor_id = d.doctor_id;

1️⃣1️⃣ Show only cardiology visits

SELECT p.full_name, d.specialty, a.diagnosis FROM appointments a JOIN doctors d ON a.doctor_id = d.doctor_id JOIN patients p ON a.patient_id = p.patient_id WHERE d.specialty = 'Cardiology';

1️⃣2️⃣ Highest paying appointment

SELECT * FROM appointments WHERE fee = (SELECT MAX(fee) FROM appointments);

1️⃣3️⃣ Patients who visited more than once

SELECT patient_id, COUNT() AS visits FROM appointments GROUP BY patient_id HAVING COUNT() > 1;

1️⃣4️⃣ Doctors earning more than average fee total

SELECT doctor_id, SUM(fee) AS total_fee FROM appointments GROUP BY doctor_id HAVING SUM(fee) >

1️⃣5️⃣ Most visited doctor

SELECT doctor_id, COUNT(*) AS visits FROM appointments GROUP BY doctor_id ORDER BY visits DESC LIMIT 1;

1️⃣6️⃣ Appointments after Jan 15

SELECT * FROM appointments WHERE visit_date > '2025-01-15';

1️⃣7️⃣ Appointments in January

SELECT * FROM appointments WHERE MONTH(visit_date) = 1; (MySQL syntax — tell me if you use SQL Server/PostgreSQL and I’ll adjust.)

1️⃣8️⃣ Update patient phone number

UPDATE patients SET phone = '08030000000' WHERE patient_id = 1;

1️⃣9️⃣ Delete an appointment

DELETE FROM appointments WHERE appointment_id = 1010;

2️⃣0️⃣ Revenue by specialty

SELECT d.specialty, SUM(a.fee) AS revenue FROM appointments a JOIN doctors d ON a.doctor_id = d.doctor_id GROUP BY d.specialty ORDER BY revenue DESC;

>>>>>>>>>>LINK TO POWER BI DASHBOARD FOR PRINCE HOSPITAL

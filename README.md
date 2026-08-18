<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Hospital Management System</title>

<style>

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f2f7f9;
    color: #333;
}

/* HEADER */

header {
    background: #1976d2;
    color: white;
    text-align: center;
    padding: 25px;
}

header h1 {
    margin: 0;
}

/* NAVIGATION */

nav {
    background: white;
    padding: 15px;
    text-align: center;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

nav button {
    padding: 10px 20px;
    margin: 5px;
    border: none;
    background: #1976d2;
    color: white;
    cursor: pointer;
    border-radius: 5px;
}

nav button:hover,
button:hover {
    background: #125ca5;
}

/* MAIN */

main {
    width: 85%;
    margin: 30px auto;
}

section {
    background: white;
    padding: 25px;
    border-radius: 10px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.08);
    margin-bottom: 20px;
}

.hidden {
    display: none;
}

/* CARDS */

.cards {
    display: flex;
    gap: 20px;
}

.card {
    flex: 1;
    padding: 20px;
    background: #e3f2fd;
    text-align: center;
    border-radius: 10px;
}

/* INPUTS */

input,
select {
    padding: 12px;
    margin: 7px 5px;
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 250px;
}

button {
    padding: 12px 20px;
    background: #1976d2;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

/* DOCTORS */

.doctor {
    background: #e3f2fd;
    padding: 15px;
    margin: 10px 0;
    border-radius: 8px;
}

/* LIST */

li {
    padding: 12px;
    margin: 7px;
    background: #f1f1f1;
    border-radius: 5px;
    list-style: none;
}

/* LOGIN */

.login-box {
    width: 400px;
    max-width: 100%;
    margin: auto;
    text-align: center;
}

.login-box input {
    width: 100%;
    margin: 10px 0;
}

.login-box button {
    width: 100%;
    margin-top: 10px;
}

/* PATIENT DASHBOARD */

.dashboard-header {
    background: #1976d2;
    color: white;
    padding: 20px;
    border-radius: 10px;
    margin-bottom: 20px;
}

.dashboard-cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}

.dashboard-card {
    background: #e3f2fd;
    padding: 20px;
    border-radius: 10px;
    text-align: center;
}

.dashboard-card h3 {
    color: #1976d2;
}

/* PROFILE */

.profile {
    background: #f8fbfd;
    padding: 20px;
    border-radius: 10px;
}

/* FOOTER */

footer {
    text-align: center;
    padding: 20px;
    background: #1976d2;
    color: white;
    margin-top: 30px;
}

/* MOBILE */

@media (max-width: 700px) {

    main {
        width: 90%;
    }

    .cards {
        flex-direction: column;
    }

    .dashboard-cards {
        grid-template-columns: 1fr;
    }

    input,
    select {
        width: 100%;
    }

}

</style>
</head>

<body>

<!-- HEADER -->

<header>

    <h1>🏥 Hospital Management System</h1>

    <p>
        Manage patients, doctors and appointments
    </p>

</header>


<!-- NAVIGATION -->

<nav>

    <button onclick="showSection('home')">
        Home
    </button>

    <button onclick="showSection('patients')">
        Patients
    </button>

    <button onclick="showSection('doctors')">
        Doctors
    </button>

    <button onclick="showSection('appointments')">
        Appointments
    </button>

    <button onclick="showSection('patientLogin')">
        🔐 Patient Login
    </button>

</nav>


<main>


<!-- HOME -->

<section id="home">

    <h2>Welcome</h2>

    <p>
        Welcome to the Hospital Management System.
    </p>

    <div class="cards">

        <div class="card">

            <h3>👨‍⚕️ Doctors</h3>

            <p>
                Manage doctor information
            </p>

        </div>


        <div class="card">

            <h3>🧑 Patients</h3>

            <p>
                Register and manage patients
            </p>

        </div>


        <div class="card">

            <h3>📅 Appointments</h3>

            <p>
                Manage appointments
            </p>

        </div>

    </div>

</section>



<!-- PATIENT REGISTRATION -->

<section id="patients" class="hidden">

    <h2>📝 Patient Registration</h2>

    <p>
        Create your personal patient account.
    </p>

    <input
        type="text"
        id="registerName"
        placeholder="Full Name"
    >

    <input
        type="number"
        id="registerAge"
        placeholder="Age"
    >

    <input
        type="text"
        id="registerDisease"
        placeholder="Disease"
    >

    <input
        type="text"
        id="registerUsername"
        placeholder="Create Username"
    >

    <input
        type="password"
        id="registerPassword"
        placeholder="Create Password"
    >

    <br>

    <button onclick="registerPatient()">

        Register Patient

    </button>

    <h3>Registered Patients</h3>

    <ul id="patientList"></ul>

</section>



<!-- DOCTORS -->

<section id="doctors" class="hidden">

    <h2>👨‍⚕️ Doctors</h2>


    <div class="doctor">

        <h3>Dr. Rahul</h3>

        <p>
            ❤️ Cardiologist
        </p>

    </div>


    <div class="doctor">

        <h3>Dr. Priya</h3>

        <p>
            🩺 Dermatologist
        </p>

    </div>


    <div class="doctor">

        <h3>Dr. Arjun</h3>

        <p>
            👨‍⚕️ General Physician
        </p>

    </div>

</section>



<!-- APPOINTMENTS -->

<section id="appointments" class="hidden">

    <h2>📅 Book Appointment</h2>


    <input
        type="text"
        id="appointmentPatient"
        placeholder="Patient Name"
    >


    <select id="appointmentDoctor">

        <option value="">
            Select Doctor
        </option>

        <option value="Dr. Rahul - Cardiologist">
            Dr. Rahul - Cardiologist
        </option>

        <option value="Dr. Priya - Dermatologist">
            Dr. Priya - Dermatologist
        </option>

        <option value="Dr. Arjun - General Physician">
            Dr. Arjun - General Physician
        </option>

    </select>


    <input
        type="date"
        id="appointmentDate"
    >

    <br>


    <button onclick="bookAppointment()">

        Book Appointment

    </button>


    <h3>Appointment List</h3>

    <ul id="appointmentList"></ul>

</section>



<!-- PATIENT LOGIN -->

<section id="patientLogin" class="hidden">

    <div class="login-box">

        <h2>🔐 Patient Login</h2>

        <p>
            Login to access your personal dashboard.
        </p>


        <input
            type="text"
            id="loginUsername"
            placeholder="Username"
        >


        <input
            type="password"
            id="loginPassword"
            placeholder="Password"
        >


        <button onclick="patientLogin()">

            Login

        </button>


        <p>
            New patient?
            <br>
            Go to <b>Patients</b> and register first.
        </p>

    </div>

</section>



<!-- PATIENT DASHBOARD -->

<section id="patientDashboard" class="hidden">

    <div class="dashboard-header">

        <h2>
            👋 Welcome, <span id="dashboardName"></span>
        </h2>

        <p>
            This is your personal patient dashboard.
        </p>

        <button onclick="logout()">

            🚪 Logout

        </button>

    </div>


    <!-- DASHBOARD CARDS -->

    <div class="dashboard-cards">

        <div class="dashboard-card">

            <h3>👤 My Profile</h3>

            <p>
                View personal information
            </p>

        </div>


        <div class="dashboard-card">

            <h3>📅 My Appointments</h3>

            <p>
                View your appointments
            </p>

        </div>


        <div class="dashboard-card">

            <h3>💊 Prescriptions</h3>

            <p>
                View prescriptions
            </p>

        </div>


        <div class="dashboard-card">

            <h3>💰 Bills</h3>

            <p>
                View hospital bills
            </p>

        </div>


        <div class="dashboard-card">

            <h3>🏥 Doctors</h3>

            <p>
                View available doctors
            </p>

        </div>


        <div class="dashboard-card">

            <h3>📋 Medical History</h3>

            <p>
                View medical records
            </p>

        </div>

    </div>


    <br>


    <!-- PROFILE -->

    <div class="profile">

        <h2>👤 My Profile</h2>

        <p>
            <b>Name:</b>
            <span id="profileName"></span>
        </p>

        <p>
            <b>Age:</b>
            <span id="profileAge"></span>
        </p>

        <p>
            <b>Disease:</b>
            <span id="profileDisease"></span>
        </p>

        <p>
            <b>Username:</b>
            <span id="profileUsername"></span>
        </p>

    </div>


    <br>


    <!-- MY APPOINTMENTS -->

    <div class="profile">

        <h2>📅 My Appointments</h2>

        <ul id="myAppointmentList"></ul>

    </div>


    <br>


    <!-- PRESCRIPTIONS -->

    <div class="profile">

        <h2>💊 My Prescriptions</h2>

        <ul>

            <li>
                No prescriptions available.
            </li>

        </ul>

    </div>


    <br>


    <!-- BILLS -->

    <div class="profile">

        <h2>💰 My Bills</h2>

        <ul>

            <li>
                No bills available.
            </li>

        </ul>

    </div>


    <br>


    <!-- MEDICAL HISTORY -->

    <div class="profile">

        <h2>📋 Medical History</h2>

        <ul>

            <li>
                No medical history available.
            </li>

        </ul>

    </div>

</section>


</main>



<!-- FOOTER -->

<footer>

    <p>
        © 2026 Hospital Management System
    </p>

</footer>



<script>


/* =================================
   PATIENT DATA
================================= */

let patients =
    JSON.parse(localStorage.getItem("patients")) || [];

let appointments =
    JSON.parse(localStorage.getItem("appointments")) || [];

let currentPatient =
    JSON.parse(localStorage.getItem("currentPatient")) || null;



/* =================================
   SHOW SECTION
================================= */

function showSection(sectionName) {

    let sections =
        document.querySelectorAll("main section");

    sections.forEach(function(section) {

        section.classList.add("hidden");

    });


    document
        .getElementById(sectionName)
        .classList.remove("hidden");

}



/* =================================
   PATIENT REGISTRATION
================================= */

function registerPatient() {

    let name =
        document.getElementById("registerName").value;

    let age =
        document.getElementById("registerAge").value;

    let disease =
        document.getElementById("registerDisease").value;

    let username =
        document.getElementById("registerUsername").value;

    let password =
        document.getElementById("registerPassword").value;


    if (
        name === "" ||
        age === "" ||
        disease === "" ||
        username === "" ||
        password === ""
    ) {

        alert("Please fill all registration details.");

        return;

    }


    /* Check username */

    let existingPatient =
        patients.find(function(patient) {

            return patient.username === username;

        });


    if (existingPatient) {

        alert("Username already exists. Please choose another.");

        return;

    }


    /* Create patient */

    let newPatient = {

        name: name,
        age: age,
        disease: disease,
        username: username,
        password: password

    };


    patients.push(newPatient);


    localStorage.setItem(
        "patients",
        JSON.stringify(patients)
    );


    alert(
        "Patient registered successfully!\n\n" +
        "Username: " + username
    );


    /* Clear form */

    document.getElementById("registerName").value = "";

    document.getElementById("registerAge").value = "";

    document.getElementById("registerDisease").value = "";

    document.getElementById("registerUsername").value = "";

    document.getElementById("registerPassword").value = "";


    displayPatients();

}



/* =================================
   DISPLAY PATIENTS
================================= */

function displayPatients() {

    let list =
        document.getElementById("patientList");

    list.innerHTML = "";


    patients.forEach(function(patient) {

        let item =
            document.createElement("li");


        item.innerHTML =
            "👤 Name: <b>" +
            patient.name +
            "</b> | Age: <b>" +
            patient.age +
            "</b> | Disease: <b>" +
            patient.disease +
            "</b>";

        list.appendChild(item);

    });

}



/* =================================
   PATIENT LOGIN
================================= */

function patientLogin() {

    let username =
        document.getElementById("loginUsername").value;

    let password =
        document.getElementById("loginPassword").value;


    if (
        username === "" ||
        password === ""
    ) {

        alert("Please enter username and password.");

        return;

    }


    /* Find patient */

    let patient =
        patients.find(function(p) {

            return (
                p.username === username &&
                p.password === password
            );

        });


    if (!patient) {

        alert(
            "Invalid username or password!"
        );

        return;

    }


    /* Save logged-in patient */

    currentPatient = patient;


    localStorage.setItem(
        "currentPatient",
        JSON.stringify(patient)
    );


    alert(
        "Login successful! Welcome " +
        patient.name
    );


    /* Show dashboard */

    showPatientDashboard();

}



/* =================================
   PATIENT DASHBOARD
================================= */

function showPatientDashboard() {

    if (!currentPatient) {

        showSection("patientLogin");

        return;

    }


    showSection("patientDashboard");


    /* Name */

    document.getElementById(
        "dashboardName"
    ).innerText =
        currentPatient.name;


    /* Profile */

    document.getElementById(
        "profileName"
    ).innerText =
        currentPatient.name;


    document.getElementById(
        "profileAge"
    ).innerText =
        currentPatient.age;


    document.getElementById(
        "profileDisease"
    ).innerText =
        currentPatient.disease;


    document.getElementById(
        "profileUsername"
    ).innerText =
        currentPatient.username;


    /* Show appointments */

    displayMyAppointments();

}



/* =================================
   DISPLAY PERSONAL APPOINTMENTS
================================= */

function displayMyAppointments() {

    let list =
        document.getElementById(
            "myAppointmentList"
        );


    list.innerHTML = "";


    if (!currentPatient) {

        return;

    }


    let myAppointments =
        appointments.filter(function(appointment) {

            return (
                appointment.patientUsername ===
                currentPatient.username
            );

        });


    if (myAppointments.length === 0) {

        let item =
            document.createElement("li");

        item.innerText =
            "No appointments booked.";

        list.appendChild(item);

        return;

    }


    myAppointments.forEach(function(appointment) {

        let item =
            document.createElement("li");


        item.innerHTML =
            "📅 <b>Date:</b> " +
            appointment.date +
            " | 👨‍⚕️ <b>Doctor:</b> " +
            appointment.doctor;


        list.appendChild(item);

    });

}



/* =================================
   BOOK APPOINTMENT
================================= */

function bookAppointment() {

    let patient =
        document.getElementById(
            "appointmentPatient"
        ).value;

    let doctor =
        document.getElementById(
            "appointmentDoctor"
        ).value;

    let date =
        document.getElementById(
            "appointmentDate"
        ).value;


    if (
        patient === "" ||
        doctor === "" ||
        date === ""
    ) {

        alert(
            "Please fill all appointment details."
        );

        return;

    }


    /* Find patient */

    let patientAccount =
        patients.find(function(p) {

            return p.name.toLowerCase() ===
                patient.toLowerCase();

        });


    if (!patientAccount) {

        alert(
            "Patient is not registered.\n" +
            "Please register the patient first."
        );

        return;

    }


    let newAppointment = {

        patientName: patient,

        patientUsername:
            patientAccount.username,

        doctor: doctor,

        date: date

    };


    appointments.push(newAppointment);


    localStorage.setItem(
        "appointments",
        JSON.stringify(appointments)
    );


    alert(
        "Appointment booked successfully!"
    );


    document.getElementById(
        "appointmentPatient"
    ).value = "";


    document.getElementById(
        "appointmentDoctor"
    ).value = "";


    document.getElementById(
        "appointmentDate"
    ).value = "";


    displayAppointments();


    /* Update dashboard */

    if (currentPatient) {

        displayMyAppointments();

    }

}



/* =================================
   DISPLAY ALL APPOINTMENTS
================================= */

function displayAppointments() {

    let list =
        document.getElementById(
            "appointmentList"
        );


    list.innerHTML = "";


    appointments.forEach(function(appointment) {

        let item =
            document.createElement("li");


        item.innerHTML =
            "👤 Patient: <b>" +
            appointment.patientName +
            "</b> → 👨‍⚕️ Doctor: <b>" +
            appointment.doctor +
            "</b> | 📅 Date: <b>" +
            appointment.date +
            "</b>";


        list.appendChild(item);

    });

}



/* =================================
   LOGOUT
================================= */

function logout() {

    currentPatient = null;

    localStorage.removeItem(
        "currentPatient"
    );


    alert(
        "You have been logged out."
    );


    showSection("patientLogin");

}



/* =================================
   PAGE LOAD
================================= */

displayPatients();

displayAppointments();


/* Keep patient logged in */

if (currentPatient) {

    showPatientDashboard();

} else {

    showSection("home");

}


</script>

</body>
</html># Hospital-Management-System

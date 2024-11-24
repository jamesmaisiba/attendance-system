// Accessing the DOM elements
const studentNameInput = document.getElementById('studentName');
const attendanceDateInput = document.getElementById('attendanceDate');
const presentBtn = document.getElementById('presentBtn');
const absentBtn = document.getElementById('absentBtn');
const attendanceListDiv = document.getElementById('attendanceList');

let attendanceData = []; // To store attendance data

// Function to add attendance record
function addAttendance(status) {
    const name = studentNameInput.value.trim();
    const date = attendanceDateInput.value.trim();

    if (!name || !date) {
        alert('Please enter both student name and date');
        return;
    }

    // Create attendance entry object
    const attendanceEntry = {
        name,
        date,
        status,
    };

    // Add entry to attendance data
    attendanceData.push(attendanceEntry);

    // Clear input fields
    studentNameInput.value = '';
    attendanceDateInput.value = '';

    // Display updated attendance list
    displayAttendance();
}

// Function to display attendance list
function displayAttendance() {
    attendanceListDiv.innerHTML = ''; // Clear previous attendance list

    attendanceData.forEach(entry => {
        const attendanceItem = document.createElement('div');
        attendanceItem.textContent = `${entry.name} | ${entry.date} | ${entry.status}`;
        attendanceListDiv.appendChild(attendanceItem);
    });
}

// Event listeners for Present and Absent buttons
presentBtn.addEventListener('click', () => addAttendance('Present'));
absentBtn.addEventListener('click', () => addAttendance('Absent'));

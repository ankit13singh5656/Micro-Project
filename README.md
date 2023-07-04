<!DOCTYPE html>
<html>
<head>
  <title>Student Enrollment Form</title>
</head>
<body>
  <h2>Student Enrollment Form</h2>
  <form id="enrollmentForm">
    <label for="rollNo">Roll No:</label>
    <input type="text" id="rollNo" name="rollNo" required><br><br>
    
    <label for="fullName">Full Name:</label>
    <input type="text" id="fullName" name="fullName" required><br><br>
    
    <label for="class">Class:</label>
    <input type="text" id="class" name="class" required><br><br>
    
    <label for="birthDate">Birth Date:</label>
    <input type="text" id="birthDate" name="birthDate" required><br><br>
    
    <label for="address">Address:</label>
    <input type="text" id="address" name="address" required><br><br>
    
    <label for="enrollmentDate">Enrollment Date:</label>
    <input type="text" id="enrollmentDate" name="enrollmentDate" required><br><br>
    
    <button type="button" id="saveBtn" disabled>Save</button>
    <button type="button" id="updateBtn" disabled>Update</button>
    <button type="button" id="resetBtn">Reset</button>
  </form>

  <script src="path/to/jpdb-commons.js"></script>
  <script>
    // JavaScript code for handling form functionality

    // Function to enable or disable buttons and form fields
    function toggleFormElements(enabled) {
      document.getElementById("saveBtn").disabled = !enabled;
      document.getElementById("updateBtn").disabled = !enabled;
      document.getElementById("resetBtn").disabled = false;
      document.getElementById("rollNo").disabled = true;
      document.getElementById("fullName").disabled = !enabled;
      document.getElementById("class").disabled = !enabled;
      document.getElementById("birthDate").disabled = !enabled;
      document.getElementById("address").disabled = !enabled;
      document.getElementById("enrollmentDate").disabled = !enabled;
    }

    // Function to reset the form
    function resetForm() {
      document.getElementById("enrollmentForm").reset();
      document.getElementById("rollNo").disabled = false;
      toggleFormElements(false);
    }

    // Function to handle form submission
    function saveData() {
      // Validate form fields
      const form = document.getElementById("enrollmentForm");
      if (!form.checkValidity()) {
        form.reportValidity();
        return;
      }

      // Get form data
      const rollNo = document.getElementById("rollNo").value;
      const fullName = document.getElementById("fullName").value;
      const studentClass = document.getElementById("class").value;
      const birthDate = document.getElementById("birthDate").value;
      const address = document.getElementById("address").value;
      const enrollmentDate = document.getElementById("enrollmentDate").value;

      // Perform data storage operation (using appropriate database library or API)
      // Replace the following code with the actual implementation to store data in the database
      // Example using JsonPowerDB library
      const jsonData = {
        "rollNo": rollNo,
        "fullName": fullName,
        "class": studentClass,
        "birthDate": birthDate,
        "address": address,
        "enrollmentDate": enrollmentDate
      };
      // Call the appropriate method to save data
      // jpdb.executeCommandAtGivenBaseUrl(dbBaseUrl, "PUT", "SCHOOL-DB", "STUDENT-TABLE", jsonData);

      // Show success message or perform necessary operations after data is saved

      // Reset the form
      resetForm();
    }

    // Event listener for Save button click
    document.getElementById("saveBtn").addEventListener("click", saveData);

    // Event listener for Reset button click
    document.getElementById("resetBtn").addEventListener("click", resetForm);

    // On page load or any control button click
    // Enable/disable form elements and set focus on the first input field
    toggleFormElements(false);
    document.getElementById("rollNo").focus();
  </script>
</body>
</html>

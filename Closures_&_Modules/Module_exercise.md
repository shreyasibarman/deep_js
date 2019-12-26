# Question

In this exercise, you will refactor some code that manages student enrollment records for a workshop, to use the module pattern.

## Instructions

1. Wrap all of the functions in a module factory (ie, function named `defineWorkshop()`). This function should make a return a public API object.

2. The returned public API object should include the following methods:

	- `addStudent(id,name,paid)`
	- `enrollStudent(id)`
	- `printCurrentEnrollment()`
	- `enrollPaidStudents()`
	- `remindUnpaidStudents()`,

3. Move the `currentEnrollment` and `studentRecords` arrays inside the module definition, but as empty arrays.

4. Create an instance of this module by calling `defineWorkshop()`, and name it `deepJS`.

5. Define all the student records by calling `deepJS.addStudent(..)` for each.

6. Define the student enrollments by calling `deepJS.enrollStudent(..)` for each.

7. Change the execution code (the console output steps) to references to `deepJS.*` public API methods.


# Answer

```javascript

function defineWorkshop() {
  var currentEnrollment = [];
  var studentRecords = [];

  var publicAPI = {
    addStudent,
    enrollStudent,
    printCurrentEnrollment,
    enrollPaidStudents,
    remindUnpaidStudents
  };
  return publicAPI;

  function addStudent(id, name, paid) {
    studentRecords.push({ id, name, paid });
  }

  function enrollStudent(id) {
    if (!currentEnrollment.includes(id)) {
      currentEnrollment.push(id);
    }
  }

  function printCurrentEnrollment() {
    printRecords(currentEnrollment);
  }

  function enrollPaidStudents() {
    currentEnrollment = paidStudentsToEnroll();
    printRecords(currentEnrollment);
  }

  function remindUnpaidStudents() {
    remindUnpaid(currentEnrollment);
  }

  function getStudentFromId(studentId) {
    return studentRecords.find(matchId);

    // *************************

    function matchId(record) {
      return record.id === studentId;
    }
  }

  function printRecords(recordIds) {
    var records = recordIds.map(getStudentFromId);

    records.sort(sortByNameAsc);

    records.forEach(printRecord);
  }

  function sortByNameAsc(record1, record2) {
    if (record1.name < record2.name) return -1;
    else if (record1.name > record2.name) return 1;
    else return 0;
  }

  function printRecord(record) {
    console.log(
      `${record.name} (${record.id}): ${record.paid ? "Paid" : "Not Paid"}`
    );
  }

  function paidStudentsToEnroll() {
    var recordsToEnroll = studentRecords.filter(needToEnroll);

    var idsToEnroll = recordsToEnroll.map(getStudentId);

    return [...currentEnrollment, ...idsToEnroll];
  }

  function needToEnroll(record) {
    return record.paid && !currentEnrollment.includes(record.id);
  }

  function getStudentId(record) {
    return record.id;
  }

  function remindUnpaid(recordIds) {
    var unpaidIds = recordIds.filter(notYetPaid);

    printRecords(unpaidIds);
  }

  function notYetPaid(studentId) {
    var record = getStudentFromId(studentId);
    return !record.paid;
  }
}

var deepjs = defineWorkshop();

deepjs.addStudent(313, "Frank", true);
deepjs.addStudent(410, "Suzy", true);
deepjs.addStudent(709, "Brian", false);
deepjs.addStudent(105, "Henry", false);
deepjs.addStudent(502, "Mary", true);
deepjs.addStudent(664, "Bob", false);
deepjs.addStudent(250, "Peter", true);
deepjs.addStudent(375, "Sarah", true);
deepjs.addStudent(867, "Greg", false);

deepjs.enrollStudent(410);
deepjs.enrollStudent(105);
deepjs.enrollStudent(664);
deepjs.enrollStudent(375);

deepjs.printCurrentEnrollment();
console.log(`----`);
deepjs.enrollPaidStudents();
console.log(`----`);
deepjs.remindUnpaidStudents();
```

# Output

```javascript
Bob (664): Not Paid 
Henry (105): Not Paid 
Sarah (375): Paid 
Suzy (410): Paid 
---- 
Bob (664): Not Paid 
Frank (313): Paid 
Henry (105): Not Paid 
Mary (502): Paid 
Peter (250): Paid 
Sarah (375): Paid 
Suzy (410): Paid 
---- 
Bob (664): Not Paid 
Henry (105): Not Paid 
```

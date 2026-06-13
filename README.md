
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Homoeopathy Case Taking Form</title>

<style>
body{
    font-family: Arial, sans-serif;
    background:#f2f5f7;
    margin:0;
    padding:20px;
}

.container{
    max-width:900px;
    margin:auto;
    background:white;
    padding:25px;
    border-radius:12px;
    box-shadow:0 0 10px rgba(0,0,0,0.15);
}

h1{
    text-align:center;
    color:darkgreen;
}

h2{
    background:darkgreen;
    color:white;
    padding:8px;
    border-radius:5px;
}

label{
    font-weight:bold;
}

input, textarea, select{
    width:100%;
    padding:10px;
    margin-top:5px;
    margin-bottom:15px;
    border:1px solid #ccc;
    border-radius:5px;
}

.row{
    display:flex;
    gap:15px;
}

.col{
    flex:1;
}

button{
    background:darkgreen;
    color:white;
    border:none;
    padding:12px 20px;
    border-radius:5px;
    cursor:pointer;
}

button:hover{
    background:green;
}

.footer{
    text-align:center;
    margin-top:20px;
    color:#666;
}
</style>

</head>
<body>

<div class="container">

<h1>Homoeopathy Case Taking Form</h1>

<form>

<h2>Patient Information</h2>

<div class="row">
<div class="col">
<label>Patient Name</label>
<input type="text">
</div>

<div class="col">
<label>Age</label>
<input type="number">
</div>
</div>

<div class="row">
<div class="col">
<label>Gender</label>
<select>
<option>Male</option>
<option>Female</option>
<option>Other</option>
</select>
</div>

<div class="col">
<label>Mobile Number</label>
<input type="tel">
</div>
</div>

<label>Address</label>
<textarea rows="2"></textarea>

<h2>Chief Complaints</h2>

<label>Main Complaint</label>
<textarea rows="3"></textarea>

<label>Duration</label>
<input type="text">

<h2>History of Present Illness</h2>

<textarea rows="4"></textarea>

<h2>Past History</h2>

<textarea rows="3"></textarea>

<h2>Family History</h2>

<textarea rows="3"></textarea>

<h2>Physical Generals</h2>

<label>Appetite</label>
<input type="text">

<label>Thirst</label>
<input type="text">

<label>Food Likes</label>
<input type="text">

<label>Food Dislikes</label>
<input type="text">

<label>Sleep</label>
<input type="text">

<label>Dreams</label>
<input type="text">

<label>Bowel Habit</label>
<input type="text">

<label>Urination</label>
<input type="text">

<label>Thermal Reaction</label>
<select>
<option>Hot Patient</option>
<option>Chilly Patient</option>
<option>Mixed</option>
</select>

<h2>Mental Generals</h2>

<label>Nature & Temperament</label>
<textarea rows="2"></textarea>

<label>Fear</label>
<textarea rows="2"></textarea>

<label>Anxiety</label>
<textarea rows="2"></textarea>

<label>Anger</label>
<textarea rows="2"></textarea>

<label>Memory</label>
<textarea rows="2"></textarea>

<h2>Female History</h2>

<label>Menstrual History</label>
<textarea rows="2"></textarea>

<label>Pregnancy History</label>
<textarea rows="2"></textarea>

<h2>Clinical Examination</h2>

<div class="row">
<div class="col">
<label>Pulse</label>
<input type="text">
</div>

<div class="col">
<label>Blood Pressure</label>
<input type="text">
</div>
</div>

<div class="row">
<div class="col">
<label>Height</label>
<input type="text">
</div>

<div class="col">
<label>Weight</label>
<input type="text">
</div>
</div>

<h2>Diagnosis</h2>
<textarea rows="3"></textarea>

<h2>Prescription</h2>
<textarea rows="3"></textarea>

<h2>Follow Up Date</h2>
<input type="date">

<input type="text" id="name" placeholder="Name">

<input type="text" id="mobile" placeholder="Mobile">

<button type="button" onclick="savePatient()">
Save Patient
</button>

<script>
function savePatient(){

let patient = {
name: document.getElementById("name").value,
mobile: document.getElementById("mobile").value
};

let patients =
JSON.parse(localStorage.getItem("patients"))
|| [];

patients.push(patient);

localStorage.setItem(
"patients",
JSON.stringify(patients)
);

alert("Patient Saved Successfully");

console.log(localStorage.getItem("patients"));
}
</script>

<h2>Search Patient</h2>

<input type="text" id="searchBox"
placeholder="Enter Name or Mobile">

<button onclick="searchPatient()">Search</button>

<div id="result"></div>

<script>
function searchPatient(){

let keyword =
document.getElementById("searchBox")
.value.toLowerCase();

let patients =
JSON.parse(localStorage.getItem("patients"))
|| [];

let output="";

patients.forEach(function(p){

if(
p.name.toLowerCase().includes(keyword)
||
p.mobile.includes(keyword)
){

output += `
<hr>
<b>Name:</b> ${p.name}<br>
<b>Mobile:</b> ${p.mobile}<br>
<b>Complaint:</b> ${p.complaint}<br>
<b>Prescription:</b> ${p.prescription}<br>
<b>Follow Up:</b> ${p.followup}<br>
`;

}

});

document.getElementById("result")
.innerHTML=output;

}
</script>

function addFollowUp(index){

let patients =
JSON.parse(localStorage.getItem("patients"));

let note =
prompt("Enter Follow Up Note");

patients[index].followupnote = note;

localStorage.setItem(
"patients",
JSON.stringify(patients)
);

alert("Follow Up Saved");

}

<button onclick="window.print()">
Print Case Sheet
</button>

function deletePatient(index){

let patients =
JSON.parse(localStorage.getItem("patients"));

if(confirm("Delete Patient?")){

patients.splice(index,1);

localStorage.setItem(
"patients",
JSON.stringify(patients)
);

alert("Deleted");

}

}

<table border="1" width="100%">
<tr>
<th>Name</th>
<th>Mobile</th>
<th>Follow Up</th>
<th>Action</th>
</tr>

<tbody id="patientTable">
</tbody>

</table>

function loadPatients(){

let patients =
JSON.parse(localStorage.getItem("patients"))
|| [];

let html="";

patients.forEach((p,i)=>{

html += `
<tr>
<td>${p.name}</td>
<td>${p.mobile}</td>
<td>${p.followup}</td>
<td>
<button onclick="addFollowUp(${i})">
Follow Up
</button>

<button onclick="deletePatient(${i})">
Delete
</button>
</td>
</tr>
`;

});

document.getElementById("patientTable")
.innerHTML = html;

}

loadPatients();


</form>

<div class="footer">
© Mahashakthi homoeo chikithsalay 
</div>

</div>

</body>
</html>

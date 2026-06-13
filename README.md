<!DOCTYPE html>
<html>
<head>

<title>Homoeopathy Clinic</title>

<style>

body{
font-family:Arial;
background:#f2f2f2;
padding:20px;
}

.container{
background:white;
padding:20px;
border-radius:10px;
}

h1{
color:darkgreen;
}

input,textarea,select{
width:100%;
padding:8px;
margin:5px 0;
}

button{
padding:10px 15px;
margin-top:10px;
cursor:pointer;
}

table{
width:100%;
border-collapse:collapse;
margin-top:20px;
}

th,td{
border:1px solid #ccc;
padding:8px;
text-align:center;
}

</style>

</head>

<body>

<div class="container">

<h1>Homoeopathy Case Taking</h1>

<h3>Patient Information</h3>

<input id="name" placeholder="Patient Name">
<input id="age" placeholder="Age">
<input id="mobile" placeholder="Mobile">

<textarea id="address" placeholder="Address"></textarea>

<h3>Chief Complaint</h3>

<textarea id="complaint" placeholder="Main Complaint"></textarea>

<h3>Mental Symptoms</h3>

<textarea id="mental" placeholder="Anger / Fear / Anxiety"></textarea>

<h3>Past History</h3>

<textarea id="history" placeholder="Past Disease"></textarea>

<h3>Lab Test Report</h3>

<input type="file" id="labReport">

<h3>Remedy Selection</h3>

<input list="remedies" id="remedy">

<datalist id="remedies">

<option value="Aconite">
<option value="Arnica">
<option value="Arsenicum Album">
<option value="Belladonna">
<option value="Bryonia">
<option value="Calcarea Carb">
<option value="Chamomilla">
<option value="China">
<option value="Gelsemium">
<option value="Hepar Sulph">
<option value="Ignatia">
<option value="Lycopodium">
<option value="Merc Sol">
<option value="Natrum Mur">
<option value="Nux Vomica">
<option value="Phosphorus">
<option value="Pulsatilla">
<option value="Rhus Tox">
<option value="Sepia">
<option value="Silicea">
<option value="Sulphur">

</datalist>

<h3>Prescription</h3>

<textarea id="medicine" placeholder="Medicine Instruction"></textarea>

<input type="date" id="followup">

</button> onclick="savePatient()">Save Case</button>

<hr>

<h2>Search Patient</h2>

<input id="search" placeholder="Search name" onkeyup="searchPatient()">

<h2>Patient List</h2>

<table id="table">

<tr>
<th>Name</th>
<th>Age</th>
<th>Mobile</th>
<th>Remedy</th>
<th>View</th>
<th>Print</th>
<th>Delete</th>
</tr>

</table>

</div>

<script>

let patients=JSON.parse(localStorage.getItem("patients")) || [];

function savePatient(){

let p={

name:document.getElementById("name").value,
age:document.getElementById("age").value,
mobile:document.getElementById("mobile").value,
address:document.getElementById("address").value,
complaint:document.getElementById("complaint").value,
mental:document.getElementById("mental").value,
history:document.getElementById("history").value,
remedy:document.getElementById("remedy").value,
medicine:document.getElementById("medicine").value,
followup:document.getElementById("followup").value

};

patients.push(p);

localStorage.setItem("patients",JSON.stringify(patients));

showPatients();

alert("Case Saved");

}

function showPatients(){

let table=document.getElementById("table");

table.innerHTML=`<tr>
<th>Name</th>
<th>Age</th>
<th>Mobile</th>
<th>Remedy</th>
<th>View</th>
<th>Print</th>
<th>Delete</th>
</tr>`;

patients.forEach((p,i)=>{

let row=table.insertRow();

row.insertCell(0).innerHTML=p.name;
row.insertCell(1).innerHTML=p.age;
row.insertCell(2).innerHTML=p.mobile;
row.insertCell(3).innerHTML=p.remedy;

let viewBtn=document.createElement("button");
viewBtn.innerHTML="View";

viewBtn.onclick=function(){

alert(

"Name: "+p.name+
"\nAge: "+p.age+
"\nMobile: "+p.mobile+
"\nAddress: "+p.address+
"\nComplaint: "+p.complaint+
"\nMental: "+p.mental+
"\nPast History: "+p.history+
"\nRemedy: "+p.remedy+
"\nMedicine: "+p.medicine+
"\nFollowUp: "+p.follo

</script>

</body>
</html>

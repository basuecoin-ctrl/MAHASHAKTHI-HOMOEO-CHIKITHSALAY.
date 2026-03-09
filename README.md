
<html>
<head>
<title> Case Taking </title>

<style>

body{
font-family: Arial;
background:#f3f3f3;
padding:20px;
}

h1{
color:darkgreen;
}

h2{
background:#e6ffe6;
padding:5px;
}

input, textarea, select{
width:100%;
padding:8px;
margin:5px 0;
}

button{
padding:10px 15px;
margin-top:10px;
cursor:pointer;
}

.container{
background:white;
padding:20px;
border-radius:10px;
}

</style>

</head>

<body>

<div class="container">

<h1>Homoeopathy Case Taking Form</h1>

<h2>1. Patient Identification</h2>

<input placeholder="Patient Name">
<input placeholder="Age">
<select>
<option>Male</option>
<option>Female</option>
</select>
<input placeholder="Marital Status">
<input placeholder="Occupation">
<input placeholder="Mobile Number">
<textarea placeholder="Address"></textarea>

<h2>2. Chief Complaint</h2>

<textarea placeholder="Main Complaint"></textarea>
<input placeholder="Since When">
<textarea placeholder="Cause of Disease"></textarea>
<textarea placeholder="What makes it worse"></textarea>
<textarea placeholder="What makes it better"></textarea>

<h2>3. History of Present Illness</h2>

<textarea placeholder="How disease started"></textarea>
<textarea placeholder="Progress of disease"></textarea>
<textarea placeholder="Previous treatment"></textarea>

<h2>4. Past History</h2>

<textarea placeholder="Previous diseases"></textarea>
<textarea placeholder="Surgery history"></textarea>

<h2>5. Family History</h2>

<textarea placeholder="Father disease history"></textarea>
<textarea placeholder="Mother disease history"></textarea>

<h2>6. Physical Generals</h2>

<label>Appetite</label>
<select>
<option>Normal</option>
<option>Low</option>
<option>High</option>
</select>

<label>Thirst</label>
<select>
<option>Less</option>
<option>Normal</option>
<option>More</option>
</select>

<label>Sleep</label>
<select>
<option>Good</option>
<option>Disturbed</option>
<option>Insomnia</option>
</select>

<input placeholder="Food Desire (sweet / sour / salt)">
<input placeholder="Food Aversion">

<h2>7. Mental Symptoms</h2>

<textarea placeholder="Anger / Fear / Anxiety"></textarea>
<textarea placeholder="Sadness / Depression"></textarea>
<textarea placeholder="Memory / Concentration"></textarea>

<h2>8. Female History</h2>

<input placeholder="Menstrual Cycle">
<input placeholder="Leucorrhoea">
<input placeholder="Pregnancy History">

<h2>9. Physical Examination</h2>

<input placeholder="Blood Pressure">
<input placeholder="Pulse">
<input placeholder="Weight">
<input placeholder="Temperature">

<h2>10 lab test report</h2>
<input type="file" id="labReport">

<h2>11. Diagnosis</h2>

<textarea placeholder="Clinical Diagnosis"></textarea>

<h2>12. Totality of Symptoms</h2>

<textarea placeholder="Important symptoms for remedy selection"></textarea>

<h2>13. Remedy Selection</h2>

<input list="remedies" id="remedySearch" placeholder="Search Remedy">

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
<option value="hydrophobinum/Lyssinum">
<option value="Thuja Occidentalis">
<option value="Medorrhinum">
<option value="Carbo Vegetabilis">
  
</datalist>

<h3>Prescription</h3>

<textarea id="medicine" placeholder="Medicine Instruction"></textarea>

<input type="date" id="followup">

<button onclick="savePatient()">Save Case</button>

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
"\nFollowUp: "+p.followup

);

}

row.insertCell(4).appendChild(viewBtn);

let printBtn=document.createElement("button");
printBtn.innerHTML="Print";

printBtn.onclick=function(){

let w=window.open();

w.document.write("<h2>Homoeopathy Prescription</h2>");

w.document.write("Name: "+p.name+"<br>");
w.document.write("Age: "+p.age+"<br>");
w.document.write("Mobile: "+p.mobile+"<br>");
w.document.write("Address: "+p.address+"<br><br>");

w.document.write("Complaint: "+p.complaint+"<br>");
w.document.write("Mental: "+p.mental+"<br>");
w.document.write("Past History: "+p.history+"<br><br>");

w.document.write("<b>Remedy:</b> "+p.remedy+"<br>");
w.document.write("<b>Medicine:</b> "+p.medicine+"<br>");
w.document.write("FollowUp: "+p.followup);

w.print();

}

row.insertCell(5).appendChild(printBtn);

let delBtn=document.createElement("button");
delBtn.innerHTML="Delete";

delBtn.onclick=function(){

patients.splice(i,1);

localStorage.setItem("patients",JSON.stringify(patients));

showPatients();

}

row.insertCell(6).appendChild(delBtn);

});

}

function searchPatient(){

let text=document.getElementById("search").value.toLowerCase();

let filtered=patients.filter(p=>p.name.toLowerCase().includes(text));

let table=document.getElementById("table");

table.innerHTML="";

filtered.forEach(p=>{

let row=table.insertRow();

row.insertCell(0).innerHTML=p.name;
row.insertCell(1).innerHTML=p.age;
row.insertCell(2).innerHTML=p.mobile;
row.insertCell(3).innerHTML=p.remedy;

});

}

showPatients();

</script>

</body>
</html>  
  









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

<h2>11. Diagnosis</h2

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
<option value="Thuja Occidentals">
<option value="Medorrhinum">
<option value="Carbo Vegetabillis">

</datalist>
<input placeholder="Potency">
<input placeholder="Dose">

<h2>14. Prescription</h2>

<textarea placeholder="Medicine instruction"></textarea>

<h2>15. Follow Up</h2>

<input type="date">

br>

<button onclick="window.print()">Print Case</button>

</div>

</body>
</html>


function savePatient(){

let p={

name:document.getElementById("name").value,
age:document.getElementById("age").value,
mobile:document.getElementById("mobile").value,
complaint:document.getElementById("complaint").value,
mental:document.getElementById("mental").value,
history:document.getElementById("history").value,
medicine:document.getElementById("medicine").value,
remedy:document.getElementById("remedySearch").value,
followup:document.getElementById("followup").value

};

patients.push(p);

localStorage.setItem("patients",JSON.stringify(patients));

showPatients();

}
row.insertCell(4).innerHTML=p.remedy;
row.insertCell(5).innerHTML=p.medicine;
row.insertCell(6).innerHTML=p.followup;

let viewBtn=document.createElement("button");
viewBtn.innerHTML="View Case";

viewBtn.onclick=function(){

alert(
"Name: "+p.name+
"\nAge: "+p.age+
"\nComplaint: "+p.complaint+
"\nMental: "+p.mental+
"\nPast History: "+p.history+
"\nRemedy: "+p.remedy+
"\nMedicine: "+p.medicine
);

}

row.insertCell(8).appendChild(viewBtn);



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

<h2>10. Diagnosis</h2>

<textarea placeholder="Clinical Diagnosis"></textarea>

<h2>11. Totality of Symptoms</h2>

<textarea placeholder="Important symptoms for remedy selection"></textarea>

<h2>12. Remedy Selection</h2>

<input placeholder="Selected Remedy">
<input placeholder="Potency">
<input placeholder="Dose">

<h2>13. Prescription</h2>

<textarea placeholder="Medicine instruction"></textarea>

<h2>14. Follow Up</h2>

<input type="date">

<br>

<button onclick="window.print()">Print Case</button>

</div>

</body>
</html>

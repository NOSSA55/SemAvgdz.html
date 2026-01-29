<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semester Average Calculator</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid #e0e0e0;
        }
        
        h1 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #7f8c8d;
            font-size: 1.1rem;
        }
        
        .app-container {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 30px;
        }
        
        @media (max-width: 900px) {
            .app-container {
                grid-template-columns: 1fr;
            }
        }
        
        .card {
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            padding: 25px;
            margin-bottom: 25px;
        }
        
        .card h2 {
            color: #3498db;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #f0f0f0;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .card h2 i {
            font-size: 1.4rem;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #2c3e50;
        }
        
        input[type="text"],
        input[type="number"],
        select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: border 0.3s;
        }
        
        input[type="text"]:focus,
        input[type="number"]:focus,
        select:focus {
            border-color: #3498db;
            outline: none;
        }
        
        .checkbox-group {
            display: flex;
            gap: 20px;
            margin-top: 10px;
        }
        
        .checkbox-item {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .checkbox-item input {
            width: auto;
        }
        
        .btn {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 14px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: background-color 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            width: 100%;
        }
        
        .btn:hover {
            background-color: #2980b9;
        }
        
        .btn-secondary {
            background-color: #2ecc71;
        }
        
        .btn-secondary:hover {
            background-color: #27ae60;
        }
        
        .btn-calculate {
            background-color: #9b59b6;
        }
        
        .btn-calculate:hover {
            background-color: #8e44ad;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }
        
        th {
            background-color: #f8f9fa;
            padding: 15px;
            text-align: left;
            border-bottom: 2px solid #e0e0e0;
            color: #2c3e50;
        }
        
        td {
            padding: 15px;
            border-bottom: 1px solid #eee;
        }
        
        tr:hover {
            background-color: #f9f9f9;
        }
        
        .subject-name {
            font-weight: 600;
        }
        
        .coefficient {
            text-align: center;
            font-weight: 600;
            color: #e74c3c;
        }
        
        .average {
            text-align: center;
            font-weight: 600;
        }
        
        .actions {
            display: flex;
            gap: 8px;
        }
        
        .action-btn {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 16px;
            color: #7f8c8d;
            transition: color 0.3s;
        }
        
        .action-btn:hover {
            color: #3498db;
        }
        
        .delete-btn:hover {
            color: #e74c3c;
        }
        
        .result-box {
            text-align: center;
            padding: 25px;
            background-color: #f8f9fa;
            border-radius: 10px;
            margin-top: 20px;
        }
        
        .result-label {
            font-size: 18px;
            color: #7f8c8d;
            margin-bottom: 10px;
        }
        
        .result-value {
            font-size: 42px;
            font-weight: 700;
            color: #2c3e50;
        }
        
        .grade {
            font-size: 20px;
            margin-top: 10px;
            color: #3498db;
            font-weight: 600;
        }
        
        .empty-message {
            text-align: center;
            padding: 40px 20px;
            color: #95a5a6;
            font-style: italic;
        }
        
        .instructions {
            background-color: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }
        
        .instructions h3 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .instructions ul {
            padding-left: 20px;
        }
        
        .instructions li {
            margin-bottom: 8px;
        }
        
        footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            color: #7f8c8d;
            border-top: 1px solid #e0e0e0;
        }
        
        .footer-text {
            font-weight: bold;
            color: #2c3e50;
            margin-top: 5px;
        }
        
        .hidden {
            display: none;
        }
        
        .subject-inputs {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .form-section {
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }
        
        .form-section:last-child {
            border-bottom: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-calculator"></i> Semester Average Calculator</h1>
            <p class="subtitle">Calculate your semester average with TD, TP, and Exam components</p>
        </header>
        
        <div class="app-container">
            <div>
                <div class="card">
                    <h2><i class="fas fa-plus-circle"></i> Add Subject</h2>
                    
                    <form id="subjectForm">
                        <div class="form-group">
                            <label for="subjectName">Subject Name</label>
                            <input type="text" id="subjectName" placeholder="e.g., Mathematics" required>
                        </div>
                        
                        <div class="form-section">
                            <label>Assessment Components</label>
                            <div class="checkbox-group">
                                <div class="checkbox-item">
                                    <input type="checkbox" id="hasTD">
                                    <label for="hasTD" style="display: inline; font-weight: normal;">TD</label>
                                </div>
                                <div class="checkbox-item">
                                    <input type="checkbox" id="hasTP">
                                    <label for="hasTP" style="display: inline; font-weight: normal;">TP</label>
                                </div>
                                <div class="checkbox-item">
                                    <input type="checkbox" id="hasExam" checked>
                                    <label for="hasExam" style="display: inline; font-weight: normal;">Exam</label>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-section">
                            <div class="subject-inputs">
                                <div class="form-group" id="tdGroup">
                                    <label for="tdPoints">TD Points (out of 20)</label>
                                    <input type="number" id="tdPoints" min="0" max="20" step="0.1" placeholder="0-20">
                                </div>
                                
                                <div class="form-group" id="tpGroup">
                                    <label for="tpPoints">TP Points (out of 20)</label>
                                    <input type="number" id="tpPoints" min="0" max="20" step="0.1" placeholder="0-20">
                                </div>
                                
                                <div class="form-group" id="examGroup">
                                    <label for="examPoints">Exam Points (out of 20)</label>
                                    <input type="number" id="examPoints" min="0" max="20" step="0.1" placeholder="0-20" required>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="coefficient">Coefficient</label>
                            <select id="coefficient">
                                <option value="1">1</option>
                                <option value="2">2</option>
                                <option value="3" selected>3</option>
                                <option value="4">4</option>
                                <option value="5">5</option>
                                <option value="6">6</option>
                            </select>
                        </div>
                        
                        <button type="submit" class="btn btn-secondary">
                            <i class="fas fa-plus"></i> Add Subject
                        </button>
                    </form>
                </div>
                
                <div class="card instructions">
                    <h3><i class="fas fa-info-circle"></i> How to Calculate</h3>
                    <ul>
                        <li><strong>Exam only:</strong> Subject average = Exam points</li>
                        <li><strong>TD + Exam:</strong> (TD × 0.4) + (Exam × 0.6)</li>
                        <li><strong>TD + TP + Exam:</strong> ((TD + TP) ÷ 2 × 0.4) + (Exam × 0.6)</li>
                        <li><strong>Overall average:</strong> Sum of (subject average × coefficient) ÷ Sum of coefficients</li>
                    </ul>
                </div>
            </div>
            
            <div>
                <div class="card">
                    <h2><i class="fas fa-list-alt"></i> Subjects</h2>
                    
                    <div id="subjectsTableContainer">
                        <table id="subjectsTable">
                            <thead>
                                <tr>
                                    <th>Subject</th>
                                    <th>Components</th>
                                    <th>Coefficient</th>
                                    <th>Average</th>
                                    <th>Actions</th>
                                </tr>
                            </thead>
                            <tbody id="subjectsTableBody">
                                <!-- Subjects will be added here dynamically -->
                            </tbody>
                        </table>
                        
                        <div id="emptyMessage" class="empty-message">
                            <i class="fas fa-book-open fa-2x" style="margin-bottom: 15px;"></i>
                            <p>No subjects added yet. Add your first subject using the form on the left.</p>
                        </div>
                    </div>
                    
                    <div class="result-box" id="resultContainer">
                        <div class="result-label">Your Semester Average</div>
                        <div class="result-value" id="averageResult">0.00</div>
                        <div class="grade" id="gradeText">Add subjects to calculate</div>
                    </div>
                    
                    <button id="calculateBtn" class="btn btn-calculate" style="margin-top: 20px;">
                        <i class="fas fa-calculator"></i> Calculate Average
                    </button>
                    
                    <button id="clearAllBtn" class="btn" style="margin-top: 10px; background-color: #e74c3c;">
                        <i class="fas fa-trash-alt"></i> Clear All Subjects
                    </button>
                </div>
            </div>
        </div>
        
        <footer>
            <p>Semester Average Calculator</p>
            <p class="footer-text">This website was made by NOSSA 55</p>
        </footer>
    </div>

    <script>
        // DOM elements
        const subjectForm = document.getElementById('subjectForm');
        const subjectsTableBody = document.getElementById('subjectsTableBody');
        const emptyMessage = document.getElementById('emptyMessage');
        const calculateBtn = document.getElementById('calculateBtn');
        const clearAllBtn = document.getElementById('clearAllBtn');
        const averageResult = document.getElementById('averageResult');
        const gradeText = document.getElementById('gradeText');
        const resultContainer = document.getElementById('resultContainer');
        
        // Assessment type checkboxes
        const hasTD = document.getElementById('hasTD');
        const hasTP = document.getElementById('hasTP');
        const hasExam = document.getElementById('hasExam');
        
        // Input groups
        const tdGroup = document.getElementById('tdGroup');
        const tpGroup = document.getElementById('tpGroup');
        const examGroup = document.getElementById('examGroup');
        
        // Initialize subjects array
        let subjects = JSON.parse(localStorage.getItem('semesterSubjects')) || [];
        
        // Toggle input visibility based on checkboxes
        function toggleInputs() {
            tdGroup.classList.toggle('hidden', !hasTD.checked);
            tpGroup.classList.toggle('hidden', !hasTP.checked);
            examGroup.classList.toggle('hidden', !hasExam.checked);
            
            // Update required attribute for exam based on checkbox
            document.getElementById('examPoints').required = hasExam.checked;
        }
        
        // Initialize toggle on page load
        toggleInputs();
        
        // Add event listeners to checkboxes
        hasTD.addEventListener('change', toggleInputs);
        hasTP.addEventListener('change', toggleInputs);
        hasExam.addEventListener('change', toggleInputs);
        
        // Calculate subject average based on assessment types
        function calculateSubjectAverage(subject) {
            let average = 0;
            
            // Case 1: Only exam
            if (!subject.hasTD && !subject.hasTP && subject.hasExam) {
                average = subject.examPoints;
            }
            // Case 2: TD + Exam (no TP)
            else if (subject.hasTD && !subject.hasTP && subject.hasExam) {
                average = (subject.tdPoints * 0.4) + (subject.examPoints * 0.6);
            }
            // Case 3: TP + Exam (no TD)
            else if (!subject.hasTD && subject.hasTP && subject.hasExam) {
                average = (subject.tpPoints * 0.4) + (subject.examPoints * 0.6);
            }
            // Case 4: TD + TP + Exam
            else if (subject.hasTD && subject.hasTP && subject.hasExam) {
                // Updated formula: ((TD + TP) / 2) * 0.4 + exam * 0.6
                const tdTpAverage = (subject.tdPoints + subject.tpPoints) / 2;
                average = (tdTpAverage * 0.4) + (subject.examPoints * 0.6);
            }
            // Case 5: TD + TP only (no exam) - shouldn't happen based on our form, but just in case
            else if (subject.hasTD && subject.hasTP && !subject.hasExam) {
                average = (subject.tdPoints + subject.tpPoints) / 2;
            }
            
            return Math.min(20, Math.max(0, average)); // Ensure average is between 0 and 20
        }
        
        // Format number to 2 decimal places
        function formatNumber(num) {
            return parseFloat(num).toFixed(2);
        }
        
        // Add subject to the table
        function addSubjectToTable(subject, index) {
            // Create table row
            const row = document.createElement('tr');
            
            // Calculate subject average
            const subjectAverage = calculateSubjectAverage(subject);
            
            // Determine which components are included
            let components = [];
            if (subject.hasTD) components.push('TD');
            if (subject.hasTP) components.push('TP');
            if (subject.hasExam) components.push('Exam');
            
            row.innerHTML = `
                <td class="subject-name">${subject.name}</td>
                <td>${components.join(' + ')}</td>
                <td class="coefficient">${subject.coefficient}</td>
                <td class="average">${formatNumber(subjectAverage)}</td>
                <td>
                    <div class="actions">
                        <button class="action-btn edit-btn" data-index="${index}">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="action-btn delete-btn" data-index="${index}">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                </td>
            `;
            
            subjectsTableBody.appendChild(row);
            
            // Show table and hide empty message
            emptyMessage.classList.add('hidden');
        }
        
        // Render all subjects in the table
        function renderSubjects() {
            // Clear table
            subjectsTableBody.innerHTML = '';
            
            if (subjects.length === 0) {
                emptyMessage.classList.remove('hidden');
                resultContainer.classList.add('hidden');
                return;
            }
            
            // Add each subject to the table
            subjects.forEach((subject, index) => {
                addSubjectToTable(subject, index);
            });
            
            resultContainer.classList.remove('hidden');
        }
        
        // Calculate overall average
        function calculateOverallAverage() {
            if (subjects.length === 0) {
                averageResult.textContent = '0.00';
                gradeText.textContent = 'Add subjects to calculate';
                return;
            }
            
            let totalWeightedSum = 0;
            let totalCoefficients = 0;
            
            subjects.forEach(subject => {
                const subjectAverage = calculateSubjectAverage(subject);
                totalWeightedSum += subjectAverage * subject.coefficient;
                totalCoefficients += parseInt(subject.coefficient);
            });
            
            const overallAverage = totalWeightedSum / totalCoefficients;
            averageResult.textContent = formatNumber(overallAverage);
            
            // Determine grade text
            let grade = '';
            if (overallAverage >= 16) {
                grade = 'Excellent!';
                gradeText.style.color = '#27ae60';
            } else if (overallAverage >= 14) {
                grade = 'Very Good';
                gradeText.style.color = '#2ecc71';
            } else if (overallAverage >= 12) {
                grade = 'Good';
                gradeText.style.color = '#3498db';
            } else if (overallAverage >= 10) {
                grade = 'Pass';
                gradeText.style.color = '#f39c12';
            } else {
                grade = 'Needs Improvement';
                gradeText.style.color = '#e74c3c';
            }
            
            gradeText.textContent = grade;
            
            // Save to localStorage
            localStorage.setItem('semesterSubjects', JSON.stringify(subjects));
        }
        
        // Handle form submission
        subjectForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form values
            const subjectName = document.getElementById('subjectName').value;
            const hasTDChecked = hasTD.checked;
            const hasTPChecked = hasTP.checked;
            const hasExamChecked = hasExam.checked;
            const tdPoints = parseFloat(document.getElementById('tdPoints').value) || 0;
            const tpPoints = parseFloat(document.getElementById('tpPoints').value) || 0;
            const examPoints = parseFloat(document.getElementById('examPoints').value) || 0;
            const coefficient = parseInt(document.getElementById('coefficient').value);
            
            // Validate inputs
            if (hasTDChecked && (tdPoints < 0 || tdPoints > 20 || isNaN(tdPoints))) {
                alert('TD points must be between 0 and 20');
                return;
            }
            
            if (hasTPChecked && (tpPoints < 0 || tpPoints > 20 || isNaN(tpPoints))) {
                alert('TP points must be between 0 and 20');
                return;
            }
            
            if (hasExamChecked && (examPoints < 0 || examPoints > 20 || isNaN(examPoints))) {
                alert('Exam points must be between 0 and 20');
                return;
            }
            
            // Create subject object
            const subject = {
                name: subjectName,
                hasTD: hasTDChecked,
                hasTP: hasTPChecked,
                hasExam: hasExamChecked,
                tdPoints: tdPoints,
                tpPoints: tpPoints,
                examPoints: examPoints,
                coefficient: coefficient
            };
            
            // Add to subjects array
            subjects.push(subject);
            
            // Render subjects
            renderSubjects();
            
            // Calculate overall average
            calculateOverallAverage();
            
            // Reset form
            subjectForm.reset();
            hasExam.checked = true;
            toggleInputs();
        });
        
        // Handle edit and delete buttons
        subjectsTableBody.addEventListener('click', function(e) {
            const target = e.target;
            const button = target.closest('button');
            
            if (!button) return;
            
            const index = parseInt(button.getAttribute('data-index'));
            
            if (button.classList.contains('delete-btn')) {
                // Delete subject
                subjects.splice(index, 1);
                renderSubjects();
                calculateOverallAverage();
            } else if (button.classList.contains('edit-btn')) {
                // Edit subject (for simplicity, we'll delete and re-add with form populated)
                const subject = subjects[index];
                
                // Populate form with subject data
                document.getElementById('subjectName').value = subject.name;
                hasTD.checked = subject.hasTD;
                hasTP.checked = subject.hasTP;
                hasExam.checked = subject.hasExam;
                document.getElementById('tdPoints').value = subject.tdPoints;
                document.getElementById('tpPoints').value = subject.tpPoints;
                document.getElementById('examPoints').value = subject.examPoints;
                document.getElementById('coefficient').value = subject.coefficient;
                
                // Toggle inputs
                toggleInputs();
                
                // Remove subject from array
                subjects.splice(index, 1);
                
                // Re-render
                renderSubjects();
                calculateOverallAverage();
            }
        });
        
        // Calculate average button
        calculateBtn.addEventListener('click', calculateOverallAverage);
        
        // Clear all subjects button
        clearAllBtn.addEventListener('click', function() {
            if (confirm('Are you sure you want to clear all subjects?')) {
                subjects = [];
                localStorage.removeItem('semesterSubjects');
                renderSubjects();
                calculateOverallAverage();
            }
        });
        
        // Load subjects from localStorage and render on page load
        document.addEventListener('DOMContentLoaded', function() {
            renderSubjects();
            calculateOverallAverage();
            
            // Add some sample subjects if none exist
            if (subjects.length === 0) {
                const sampleSubjects = [
                    {
                        name: "Mathematics",
                        hasTD: true,
                        hasTP: false,
                        hasExam: true,
                        tdPoints: 16,
                        examPoints: 14,
                        coefficient: 4
                    },
                    {
                        name: "Physics",
                        hasTD: true,
                        hasTP: true,
                        hasExam: true,
                        tdPoints: 15,
                        tpPoints: 17,
                        examPoints: 13,
                        coefficient: 3
                    },
                    {
                        name: "Programming",
                        hasTD: false,
                        hasTP: true,
                        hasExam: true,
                        tdPoints: 0,
                        tpPoints: 18,
                        examPoints: 16,
                        coefficient: 3
                    }
                ];
                
                // Uncomment the line below to load sample subjects by default
                // subjects = sampleSubjects;
            }
        });
    </script>
</body>
</html>

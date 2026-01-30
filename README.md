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
            flex-wrap: wrap;
        }
        
        .checkbox-item {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .checkbox-item input {
            width: auto;
        }
        
        .weighting-group {
            display: flex;
            gap: 20px;
            margin-top: 10px;
        }
        
        .weighting-item {
            display: flex;
            align-items: center;
            gap: 8px;
            background-color: #f8f9fa;
            padding: 10px 15px;
            border-radius: 8px;
            border: 1px solid #e0e0e0;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .weighting-item:hover {
            background-color: #e9ecef;
        }
        
        .weighting-item.selected {
            background-color: #3498db;
            color: white;
            border-color: #3498db;
        }
        
        .weighting-item input {
            display: none;
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

    /* Language Switcher */
.language-switcher {
    position: fixed;
    top: 20px;
    right: 90px;
    z-index: 1001;
}

.language-btn {
    background-color: #34495e;
    color: white;
    border: none;
    border-radius: 50px;
    padding: 8px 15px;
    cursor: pointer;
    font-size: 16px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    transition: all 0.3s ease;
    height: 50px;
}

.language-btn:hover {
    background-color: #2c3e50;
    transform: scale(1.05);
}

/* RTL Support for Arabic */
body[dir="rtl"] .app-container,
body[dir="rtl"] .subject-inputs {
    text-align: right;
}

body[dir="rtl"] .checkbox-group,
body[dir="rtl"] .weighting-group,
body[dir="rtl"] .actions {
    flex-direction: row-reverse;
}

body[dir="rtl"] th,
body[dir="rtl"] td {
    text-align: right;
}

body[dir="rtl"] .coefficient,
body[dir="rtl"] .average {
    text-align: center;
}

body[dir="rtl"] .component-icon {
    margin-right: 0;
    margin-left: 5px;
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
        
        .weighting-info {
            display: inline-block;
            margin-left: 10px;
            font-size: 14px;
            color: #3498db;
            font-weight: 600;
        }
        
        /* Theme Switcher */
        .theme-switcher {
            position: fixed;
            top: 20px;
            right: 20px;
            z-index: 1000;
        }

        .theme-btn {
            background-color: #3498db;
            color: white;
            border: none;
            border-radius: 50px;
            width: 50px;
            height: 50px;
            cursor: pointer;
            font-size: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
            transition: all 0.3s ease;
        }

        .theme-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
        }

        /* Dark Theme Styles */
        body.dark-theme {
            background-color: #121212;
            color: #e0e0e0;
        }

        body.dark-theme .card {
            background-color: #1e1e1e;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        body.dark-theme h1,
        body.dark-theme h2,
        body.dark-theme h3,
        body.dark-theme .subject-name {
            color: #64b5f6;
        }

        body.dark-theme .subtitle {
            color: #b0b0b0;
        }

        body.dark-theme input[type="text"],
        body.dark-theme input[type="number"],
        body.dark-theme select {
            background-color: #2d2d2d;
            border-color: #444;
            color: #e0e0e0;
        }

        body.dark-theme input[type="text"]:focus,
        body.dark-theme input[type="number"]:focus,
        body.dark-theme select:focus {
            border-color: #64b5f6;
        }

        body.dark-theme th {
            background-color: #252525;
            color: #64b5f6;
            border-bottom-color: #444;
        }

        body.dark-theme td {
            border-bottom-color: #444;
        }

        body.dark-theme tr:hover {
            background-color: #252525;
        }

        body.dark-theme .instructions,
        body.dark-theme .result-box {
            background-color: #252525;
        }

        body.dark-theme .empty-message {
            color: #aaa;
        }

        body.dark-theme .action-btn {
            color: #aaa;
        }

        body.dark-theme footer {
            border-top-color: #444;
            color: #aaa;
        }

        body.dark-theme .footer-text {
            color: #64b5f6;
        }
        
        body.dark-theme .weighting-item {
            background-color: #2d2d2d;
            border-color: #444;
        }
        
        body.dark-theme .weighting-item:hover {
            background-color: #3d3d3d;
        }
        
        body.dark-theme .weighting-item.selected {
            background-color: #64b5f6;
            border-color: #64b5f6;
        }
        
        /* Validation styles */
        .error-message {
            color: #e74c3c;
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        .input-error {
            border-color: #e74c3c !important;
        }
        
        .export-buttons {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }
        
        .btn-export {
            background-color: #f39c12;
        }
        
        .btn-export:hover {
            background-color: #e67e22;
        }
        
        .btn-import {
            background-color: #1abc9c;
        }
        
        .btn-import:hover {
            background-color: #16a085;
        }
        
        .component-icon {
            color: #3498db;
            margin-right: 5px;
        }
    </style>
</head>

<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-calculator"></i> Semester Average Calculator</h1>
            <p class="subtitle">Calculate your semester average with multiple weighting schemes</p>
            <header>
    <h1><i class="fas fa-calculator"></i> Semester Average Calculator</h1>
    <p class="subtitle">Calculate your semester average with multiple weighting schemes</p>
    
    <!-- Language Switcher Button -->
    <div class="language-switcher">
        <button id="languageSwitch" class="language-btn">
            <i class="fas fa-language"></i> العربية
        </button>
    </div>
</header>
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
                                    <input type="checkbox" id="hasExam">
                                    <label for="hasExam" style="display: inline; font-weight: normal;">Exam</label>
                                </div>
                            </div>
                            <div class="error-message" id="componentError">Please select at least one component</div>
                        </div>
                        
                        <div class="form-section">
                            <div class="subject-inputs">
                                <div class="form-group" id="tdGroup">
                                    <label for="tdPoints">TD Points (out of 20)</label>
                                    <input type="number" id="tdPoints" min="0" max="20" step="0.1" placeholder="0-20">
                                    <div class="error-message" id="tdError">TD points must be between 0 and 20</div>
                                </div>
                                
                                <div class="form-group" id="tpGroup">
                                    <label for="tpPoints">TP Points (out of 20)</label>
                                    <input type="number" id="tpPoints" min="0" max="20" step="0.1" placeholder="0-20">
                                    <div class="error-message" id="tpError">TP points must be between 0 and 20</div>
                                </div>
                                
                                <div class="form-group" id="examGroup">
                                    <label for="examPoints">Exam Points (out of 20)</label>
                                    <input type="number" id="examPoints" min="0" max="20" step="0.1" placeholder="0-20">
                                    <div class="error-message" id="examError">Exam points must be between 0 and 20</div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="form-section" id="weightingSection">
                            <label for="weightingScheme">Weighting Scheme</label>
                            <div class="weighting-group">
                                <div class="weighting-item" id="weight40">
                                    <input type="radio" id="weight40Radio" name="weighting" value="40-60" checked>
                                    <label for="weight40Radio">40% TD/TP + 60% Exam</label>
                                </div>
                                <div class="weighting-item" id="weight50">
                                    <input type="radio" id="weight50Radio" name="weighting" value="50-50">
                                    <label for="weight50Radio">50% TD/TP + 50% Exam</label>
                                </div>
                            </div>
                            <div class="error-message" id="weightingError">Please select a weighting scheme</div>
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
                        <li><strong>Single component (Exam, TD, or TP only):</strong> Subject average = Component points (100%)</li>
                        <li><strong>TD + Exam or TP + Exam with 40/60:</strong> (TD/TP × 0.4) + (Exam × 0.6)</li>
                        <li><strong>TD + Exam or TP + Exam with 50/50:</strong> (TD/TP × 0.5) + (Exam × 0.5)</li>
                        <li><strong>TD + TP + Exam with 40/60:</strong> ((TD+TP)÷2 × 0.4) + (Exam × 0.6)</li>
                        <li><strong>TD + TP + Exam with 50/50:</strong> ((TD+TP)÷2 × 0.5) + (Exam × 0.5)</li>
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
                                    <th>Weighting</th>
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

    <!-- Theme Switcher -->
    <div class="theme-switcher">
        <button class="theme-btn" id="themeToggle" title="Toggle theme">
            <i class="fas fa-moon"></i>
        </button>
    </div>

    <script>
    // Language Support
const translations = {
    en: {
        // Header
        title: "Semester Average Calculator",
        subtitle: "Calculate your semester average with multiple weighting schemes",
        languageButton: "العربية",
        
        // Form
        addSubject: "Add Subject",
        subjectName: "Subject Name",
        assessmentComponents: "Assessment Components",
        td: "TD",
        tp: "TP",
        exam: "Exam",
        tdPoints: "TD Points (out of 20)",
        tpPoints: "TP Points (out of 20)",
        examPoints: "Exam Points (out of 20)",
        weightingScheme: "Weighting Scheme",
        weighting40: "40% TD/TP + 60% Exam",
        weighting50: "50% TD/TP + 50% Exam",
        coefficient: "Coefficient",
        addSubjectButton: "Add Subject",
        
        // Instructions
        instructionsTitle: "How to Calculate",
        instruction1: "Single component (Exam, TD, or TP only): Subject average = Component points (100%)",
        instruction2: "TD + Exam or TP + Exam with 40/60: (TD/TP × 0.4) + (Exam × 0.6)",
        instruction3: "TD + Exam or TP + Exam with 50/50: (TD/TP × 0.5) + (Exam × 0.5)",
        instruction4: "TD + TP + Exam with 40/60: ((TD+TP)÷2 × 0.4) + (Exam × 0.6)",
        instruction5: "TD + TP + Exam with 50/50: ((TD+TP)÷2 × 0.5) + (Exam × 0.5)",
        instruction6: "Overall average: Sum of (subject average × coefficient) ÷ Sum of coefficients",
        
        // Subjects Table
        subjectsTitle: "Subjects",
        tableSubject: "Subject",
        tableComponents: "Components",
        tableWeighting: "Weighting",
        tableCoefficient: "Coefficient",
        tableAverage: "Average",
        tableActions: "Actions",
        calculateAverage: "Calculate Average",
        clearAll: "Clear All Subjects",
        
        // Results
        semesterAverage: "Your Semester Average",
        addSubjectsToCalculate: "Add subjects to calculate",
        excellent: "Excellent!",
        veryGood: "Very Good",
        good: "Good",
        pass: "Pass",
        needsImprovement: "Needs Improvement",
        
        // Messages
        noSubjects: "No subjects added yet. Add your first subject using the form on the left.",
        confirmClear: "Are you sure you want to clear all subjects?",
        websiteBy: "This website was made by NOSSA 55"
    },
    ar: {
        // Header
        title: "حاسبة معدل الفصل الدراسي",
        subtitle: "احسب معدل فصلك الدراسي بمخططات وزن متعددة",
        languageButton: "English",
        
        // Form
        addSubject: "إضافة مادة",
        subjectName: "اسم المادة",
        assessmentComponents: "مكونات التقييم",
        td: "تمارين",
        tp: "عمل عملي",
        exam: "امتحان",
        tdPoints: "نقاط التمارين (من 20)",
        tpPoints: "نقاط العمل العملي (من 20)",
        examPoints: "نقاط الامتحان (من 20)",
        weightingScheme: "مخطط الوزن",
        weighting40: "40% تمارين/عمل عملي + 60% امتحان",
        weighting50: "50% تمارين/عمل عملي + 50% امتحان",
        coefficient: "المعامل",
        addSubjectButton: "إضافة مادة",
        
        // Instructions
        instructionsTitle: "طريقة الحساب",
        instruction1: "مكون واحد فقط (امتحان، تمارين، أو عمل عملي): متوسط المادة = نقاط المكون (100%)",
        instruction2: "تمارين + امتحان أو عمل عملي + امتحان مع 40/60: (التمارين × 0.4) + (الامتحان × 0.6)",
        instruction3: "تمارين + امتحان أو عمل عملي + امتحان مع 50/50: (التمارين × 0.5) + (الامتحان × 0.5)",
        instruction4: "تمارين + عمل عملي + امتحان مع 40/60: ((التمارين+العمل العملي)÷2 × 0.4) + (الامتحان × 0.6)",
        instruction5: "تمارين + عمل عملي + امتحان مع 50/50: ((التمارين+العمل العملي)÷2 × 0.5) + (الامتحان × 0.5)",
        instruction6: "المعدل العام: مجموع (متوسط المادة × المعامل) ÷ مجموع المعاملات",
        
        // Subjects Table
        subjectsTitle: "المواد",
        tableSubject: "المادة",
        tableComponents: "المكونات",
        tableWeighting: "الوزن",
        tableCoefficient: "المعامل",
        tableAverage: "المتوسط",
        tableActions: "الإجراءات",
        calculateAverage: "حساب المعدل",
        clearAll: "مسح جميع المواد",
        
        // Results
        semesterAverage: "معدل الفصل الدراسي",
        addSubjectsToCalculate: "أضف مواد للحساب",
        excellent: "ممتاز!",
        veryGood: "جيد جداً",
        good: "جيد",
        pass: "ناجح",
        needsImprovement: "بحاجة إلى تحسين",
        
        // Messages
        noSubjects: "لا توجد مواد مضافة بعد. أضف مادتك الأولى باستخدام النموذج على اليسار.",
        confirmClear: "هل أنت متأكد أنك تريد مسح جميع المواد؟",
        websiteBy: "هذا الموقع من صنع NOSSA 55"
    }
};

let currentLang = localStorage.getItem('language') || 'en';

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
        const weightingSection = document.getElementById('weightingSection');
        
        // Weighting scheme selection
        const weight40 = document.getElementById('weight40');
        const weight50 = document.getElementById('weight50');
        const weight40Radio = document.getElementById('weight40Radio');
        const weight50Radio = document.getElementById('weight50Radio');
        
        // Initialize subjects array
        let subjects = JSON.parse(localStorage.getItem('semesterSubjects')) || [];
        
        // Toggle input visibility based on checkboxes
        function toggleInputs() {
            const tdChecked = hasTD.checked;
            const tpChecked = hasTP.checked;
            const examChecked = hasExam.checked;
            
            tdGroup.classList.toggle('hidden', !tdChecked);
            tpGroup.classList.toggle('hidden', !tpChecked);
            examGroup.classList.toggle('hidden', !examChecked);
            
            // Show weighting section only if there's an exam AND at least one of TD or TP
            const showWeighting = examChecked && (tdChecked || tpChecked);
            weightingSection.classList.toggle('hidden', !showWeighting);
            
            // Validate that at least one component is selected
            const componentError = document.getElementById('componentError');
            if (!tdChecked && !tpChecked && !examChecked) {
                componentError.style.display = 'block';
            } else {
                componentError.style.display = 'none';
            }
            
            // Update required attribute for inputs based on checkboxes
            document.getElementById('tdPoints').required = tdChecked;
            document.getElementById('tpPoints').required = tpChecked;
            document.getElementById('examPoints').required = examChecked;
        }
        
        // Initialize toggle on page load
        toggleInputs();
        
        // Add event listeners to checkboxes
        hasTD.addEventListener('change', toggleInputs);
        hasTP.addEventListener('change', toggleInputs);
        hasExam.addEventListener('change', toggleInputs);
        
        // Weighting selection styling
        weight40.addEventListener('click', function() {
            weight40.classList.add('selected');
            weight50.classList.remove('selected');
            weight40Radio.checked = true;
        });
        
        weight50.addEventListener('click', function() {
            weight50.classList.add('selected');
            weight40.classList.remove('selected');
            weight50Radio.checked = true;
        });
        
        // Calculate subject average based on assessment types and weighting scheme
        function calculateSubjectAverage(subject) {
            let average = 0;
            
            // Check if only one component is selected
            const components = [];
            if (subject.hasTD) components.push('TD');
            if (subject.hasTP) components.push('TP');
            if (subject.hasExam) components.push('Exam');
            
            // Case 1: Only one component (100% of that component)
            if (components.length === 1) {
                if (subject.hasTD) average = subject.tdPoints;
                else if (subject.hasTP) average = subject.tpPoints;
                else if (subject.hasExam) average = subject.examPoints;
            }
            // Case 2: Multiple components with weighting scheme
            else {
                // Calculate continuous assessment average (TD and/or TP)
                let continuousAverage = 0;
                let continuousCount = 0;
                
                if (subject.hasTD) {
                    continuousAverage += subject.tdPoints;
                    continuousCount++;
                }
                
                if (subject.hasTP) {
                    continuousAverage += subject.tpPoints;
                    continuousCount++;
                }
                
                if (continuousCount > 0) {
                    continuousAverage = continuousAverage / continuousCount;
                }
                
                // Determine weights based on scheme
                let continuousWeight = 0.4; // Default 40%
                let examWeight = 0.6; // Default 60%
                
                if (subject.weightingScheme === '50-50') {
                    continuousWeight = 0.5;
                    examWeight = 0.5;
                }
                
                // Calculate average based on components present
                if (subject.hasExam && (subject.hasTD || subject.hasTP)) {
                    // TD/TP + Exam
                    average = (continuousAverage * continuousWeight) + (subject.examPoints * examWeight);
                } else if (subject.hasTD && subject.hasTP && !subject.hasExam) {
                    // TD + TP only (no exam) - simple average
                    average = continuousAverage;
                }
            }
            
            return Math.min(20, Math.max(0, average)); // Ensure average is between 0 and 20
        }
        
        // Format number to 2 decimal places
        function formatNumber(num) {
            return parseFloat(num).toFixed(2);
        }
        // Update all text elements with translations
function updateLanguage() {
    const lang = translations[currentLang];
    
    // Update header
    document.querySelector('h1').innerHTML = `<i class="fas fa-calculator"></i> ${lang.title}`;
    document.querySelector('.subtitle').textContent = lang.subtitle;
    
    // Update language button
    document.querySelector('#languageSwitch i').nextSibling.textContent = ` ${lang.languageButton}`;
    
    // Update form
    document.querySelectorAll('.card h2')[0].innerHTML = `<i class="fas fa-plus-circle"></i> ${lang.addSubject}`;
    document.querySelector('label[for="subjectName"]').textContent = lang.subjectName;
    document.querySelectorAll('.form-section label')[0].textContent = lang.assessmentComponents;
    document.querySelector('label[for="hasTD"]').textContent = lang.td;
    document.querySelector('label[for="hasTP"]').textContent = lang.tp;
    document.querySelector('label[for="hasExam"]').textContent = lang.exam;
    document.querySelector('label[for="tdPoints"]').textContent = lang.tdPoints;
    document.querySelector('label[for="tpPoints"]').textContent = lang.tpPoints;
    document.querySelector('label[for="examPoints"]').textContent = lang.examPoints;
    document.querySelector('#weightingSection label').textContent = lang.weightingScheme;
    document.querySelector('label[for="weight40Radio"]').textContent = lang.weighting40;
    document.querySelector('label[for="weight50Radio"]').textContent = lang.weighting50;
    document.querySelector('label[for="coefficient"]').textContent = lang.coefficient;
    document.querySelector('.btn-secondary i').nextSibling.textContent = ` ${lang.addSubjectButton}`;
    
    // Update instructions
    document.querySelector('.instructions h3').innerHTML = `<i class="fas fa-info-circle"></i> ${lang.instructionsTitle}`;
    const instructions = document.querySelectorAll('.instructions li');
    instructions[0].innerHTML = `<strong>${lang.instruction1.split(':')[0]}:</strong> ${lang.instruction1.split(':')[1]}`;
    instructions[1].innerHTML = `<strong>${lang.instruction2.split(':')[0]}:</strong> ${lang.instruction2.split(':')[1]}`;
    instructions[2].innerHTML = `<strong>${lang.instruction3.split(':')[0]}:</strong> ${lang.instruction3.split(':')[1]}`;
    instructions[3].innerHTML = `<strong>${lang.instruction4.split(':')[0]}:</strong> ${lang.instruction4.split(':')[1]}`;
    instructions[4].innerHTML = `<strong>${lang.instruction5.split(':')[0]}:</strong> ${lang.instruction5.split(':')[1]}`;
    instructions[5].innerHTML = `<strong>${lang.instruction6.split(':')[0]}:</strong> ${lang.instruction6.split(':')[1]}`;
    
    // Update subjects table
    document.querySelectorAll('.card h2')[1].innerHTML = `<i class="fas fa-list-alt"></i> ${lang.subjectsTitle}`;
    const tableHeaders = document.querySelectorAll('#subjectsTable th');
    tableHeaders[0].textContent = lang.tableSubject;
    tableHeaders[1].textContent = lang.tableComponents;
    tableHeaders[2].textContent = lang.tableWeighting;
    tableHeaders[3].textContent = lang.tableCoefficient;
    tableHeaders[4].textContent = lang.tableAverage;
    tableHeaders[5].textContent = lang.tableActions;
    
    // Update empty message
    document.querySelector('#emptyMessage p').textContent = lang.noSubjects;
    
    // Update results
    document.querySelector('.result-label').textContent = lang.semesterAverage;
    if (document.getElementById('gradeText').textContent === 'Add subjects to calculate') {
        document.getElementById('gradeText').textContent = lang.addSubjectsToCalculate;
    }
    
    // Update buttons
    document.querySelector('#calculateBtn i').nextSibling.textContent = ` ${lang.calculateAverage}`;
    document.querySelector('#clearAllBtn i').nextSibling.textContent = ` ${lang.clearAll}`;
    
    // Update footer
    document.querySelector('.footer-text').textContent = lang.websiteBy;
    
    // Update placeholders
    document.getElementById('subjectName').placeholder = currentLang === 'en' ? 'e.g., Mathematics' : 'مثال: رياضيات';
    
    // Update direction for Arabic
    if (currentLang === 'ar') {
        document.body.setAttribute('dir', 'rtl');
        document.body.style.textAlign = 'right';
    } else {
        document.body.setAttribute('dir', 'ltr');
        document.body.style.textAlign = 'left';
    }
    
    // Save language preference
    localStorage.setItem('language', currentLang);
    
    // Update grade text if average is already calculated
    if (subjects.length > 0) {
        calculateOverallAverage();
    }
}

        // Get component icons
        function getComponentIcons(components) {
            let icons = '';
            if (components.includes('TD')) icons += '<i class="fas fa-chart-line component-icon" title="TD"></i>';
            if (components.includes('TP')) icons += '<i class="fas fa-flask component-icon" title="TP"></i>';
            if (components.includes('Exam')) icons += '<i class="fas fa-file-alt component-icon" title="Exam"></i>';
            return icons;
        }
        
        // Get weighting text
        function getWeightingText(weightingScheme, hasTD, hasTP, hasExam) {
            const components = [];
            if (hasTD) components.push('TD');
            if (hasTP) components.push('TP');
            
            // Single component
            if (components.length === 0 || !hasExam) {
                return '100%';
            }
            
            // Multiple components with weighting
            if (weightingScheme === '40-60') {
                return '40/60';
            } else {
                return '50/50';
            }
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
            
            // Get component icons
            const componentIcons = getComponentIcons(components);
            
            // Get weighting text
            const weightingText = getWeightingText(subject.weightingScheme, subject.hasTD, subject.hasTP, subject.hasExam);
            
            row.innerHTML = `
                <td class="subject-name">${subject.name}</td>
                <td>${componentIcons} ${components.join(' + ')}</td>
                <td>${weightingText}</td>
                <td class="coefficient">${subject.coefficient}</td>
                <td class="average">${formatNumber(subjectAverage)}</td>
                <td>
                    <div class="actions">
                        <button class="action-btn edit-btn" data-index="${index}" title="Edit subject">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="action-btn delete-btn" data-index="${index}" title="Delete subject">
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
            
            // Determine grade text - UPDATED FOR MULTILANGUAGE
let grade = '';
if (overallAverage >= 16) {
    grade = translations[currentLang].excellent;
    gradeText.style.color = '#27ae60';
} else if (overallAverage >= 14) {
    grade = translations[currentLang].veryGood;
    gradeText.style.color = '#2ecc71';
} else if (overallAverage >= 12) {
    grade = translations[currentLang].good;
    gradeText.style.color = '#3498db';
} else if (overallAverage >= 10) {
    grade = translations[currentLang].pass;
    gradeText.style.color = '#f39c12';
} else {
    grade = translations[currentLang].needsImprovement;
    gradeText.style.color = '#e74c3c';
}
            
            gradeText.textContent = grade;
            
            // Save to localStorage
            localStorage.setItem('semesterSubjects', JSON.stringify(subjects));
        }

                // Validate form inputs
        function validateForm() {
            let isValid = true;
            
            // Clear previous errors
            document.querySelectorAll('.error-message').forEach(el => {
                el.style.display = 'none';
            });
            
            // Check at least one component is selected
            if (!hasTD.checked && !hasTP.checked && !hasExam.checked) {
                document.getElementById('componentError').style.display = 'block';
                isValid = false;
            }
            
            // Validate TD points if TD is checked
            if (hasTD.checked) {
                const tdValue = parseFloat(document.getElementById('tdPoints').value);
                if (isNaN(tdValue) || tdValue < 0 || tdValue > 20) {
                    document.getElementById('tdError').style.display = 'block';
                    isValid = false;
                }
            }
            
            // Validate TP points if TP is checked
            if (hasTP.checked) {
                const tpValue = parseFloat(document.getElementById('tpPoints').value);
                if (isNaN(tpValue) || tpValue < 0 || tpValue > 20) {
                    document.getElementById('tpError').style.display = 'block';
                    isValid = false;
                }
            }
            
            // Validate Exam points if Exam is checked
            if (hasExam.checked) {
                const examValue = parseFloat(document.getElementById('examPoints').value);
                if (isNaN(examValue) || examValue < 0 || examValue > 20) {
                    document.getElementById('examError').style.display = 'block';
                    isValid = false;
                }
            }
            
            return isValid;
        }
        
        // Handle form submission
        subjectForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            if (!validateForm()) {
                return;
            }
            
            // Get form values
            const subjectName = document.getElementById('subjectName').value;
            const hasTDChecked = hasTD.checked;
            const hasTPChecked = hasTP.checked;
            const hasExamChecked = hasExam.checked;
            const tdPoints = parseFloat(document.getElementById('tdPoints').value) || 0;
            const tpPoints = parseFloat(document.getElementById('tpPoints').value) || 0;
            const examPoints = parseFloat(document.getElementById('examPoints').value) || 0;
            const weightingScheme = document.querySelector('input[name="weighting"]:checked').value;
            const coefficient = parseInt(document.getElementById('coefficient').value);
            
            // Create subject object
            const subject = {
                name: subjectName,
                hasTD: hasTDChecked,
                hasTP: hasTPChecked,
                hasExam: hasExamChecked,
                tdPoints: tdPoints,
                tpPoints: tpPoints,
                examPoints: examPoints,
                weightingScheme: weightingScheme,
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
            weight40.classList.add('selected');
            weight50.classList.remove('selected');
            weight40Radio.checked = true;
            toggleInputs();
            
            // Scroll to results
            resultContainer.scrollIntoView({ behavior: 'smooth' });
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
                // Edit subject
                const subject = subjects[index];
                
                // Populate form with subject data
                document.getElementById('subjectName').value = subject.name;
                hasTD.checked = subject.hasTD;
                hasTP.checked = subject.hasTP;
                hasExam.checked = subject.hasExam;
                document.getElementById('tdPoints').value = subject.tdPoints;
                document.getElementById('tpPoints').value = subject.tpPoints;
                document.getElementById('examPoints').value = subject.examPoints;
                
                // Set weighting scheme
                if (subject.weightingScheme === '40-60') {
                    weight40.classList.add('selected');
                    weight50.classList.remove('selected');
                    weight40Radio.checked = true;
                } else {
                    weight50.classList.add('selected');
                    weight40.classList.remove('selected');
                    weight50Radio.checked = true;
                }
                
                document.getElementById('coefficient').value = subject.coefficient;
                
                // Toggle inputs
                toggleInputs();
                
                // Remove subject from array
                subjects.splice(index, 1);
                
                // Re-render
                renderSubjects();
                calculateOverallAverage();
                
                // Scroll to form
                document.getElementById('subjectName').scrollIntoView({ behavior: 'smooth' });
            }
        });
        
        // Calculate average button
        calculateBtn.addEventListener('click', calculateOverallAverage);
        
        // Clear all subjects button
        // Clear all subjects button - UPDATED WITH TRANSLATION
clearAllBtn.addEventListener('click', function() {
    const confirmMessage = currentLang === 'en' ? 
        'Are you sure you want to clear all subjects?' : 
        'هل أنت متأكد أنك تريد مسح جميع المواد؟';
    
    if (subjects.length > 0 && confirm(confirmMessage)) {
        subjects = [];
        localStorage.removeItem('semesterSubjects');
        renderSubjects();
        calculateOverallAverage();
    }
});

// Language switcher
document.getElementById('languageSwitch').addEventListener('click', function() {
    currentLang = currentLang === 'en' ? 'ar' : 'en';
    updateLanguage();
});
        
        // Theme switcher functionality
        const themeToggle = document.getElementById('themeToggle');
        const themeIcon = themeToggle.querySelector('i');

        // Check for saved theme or prefer-color-scheme
        function getPreferredTheme() {
            const savedTheme = localStorage.getItem('theme');
            if (savedTheme) return savedTheme;
            
            // Check for system preference
            if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
                return 'dark';
            }
            return 'light';
        }

        // Set initial theme
        const currentTheme = getPreferredTheme();
        if (currentTheme === 'dark') {
            document.body.classList.add('dark-theme');
            themeIcon.classList.remove('fa-moon');
            themeIcon.classList.add('fa-sun');
        }

        // Toggle theme function
        themeToggle.addEventListener('click', () => {
            document.body.classList.toggle('dark-theme');
            
            if (document.body.classList.contains('dark-theme')) {
                localStorage.setItem('theme', 'dark');
                themeIcon.classList.remove('fa-moon');
                themeIcon.classList.add('fa-sun');
            } else {
                localStorage.setItem('theme', 'light');
                themeIcon.classList.remove('fa-sun');
                themeIcon.classList.add('fa-moon');
            }
        });
        
        // Load subjects from localStorage and render on page load
        // Load subjects from localStorage and render on page load
document.addEventListener('DOMContentLoaded', function() {
    // Set language first
    updateLanguage();
    
    // Then render everything else
    renderSubjects();
    calculateOverallAverage();
    
    // Add some sample subjects if none exist
    if (subjects.length === 0) {
        // Uncomment the line below to load sample subjects by default
        // loadSampleSubjects();
    }
});
        
        // Function to load sample subjects
        function loadSampleSubjects() {
            const sampleSubjects = [
                {
                    name: "Mathematics",
                    hasTD: true,
                    hasTP: false,
                    hasExam: true,
                    tdPoints: 16,
                    tpPoints: 0,
                    examPoints: 14,
                    weightingScheme: "40-60",
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
                    weightingScheme: "50-50",
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
                    weightingScheme: "40-60",
                    coefficient: 3
                },
                {
                    name: "English",
                    hasTD: false,
                    hasTP: false,
                    hasExam: true,
                    tdPoints: 0,
                    tpPoints: 0,
                    examPoints: 15,
                    weightingScheme: "40-60",
                    coefficient: 2
                }
            ];
            
            subjects = sampleSubjects;
            renderSubjects();
            calculateOverallAverage();
        }
    </script>
</body>
</html>


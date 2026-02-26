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
            transition: background-color 0.3s, color 0.3s;
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
            position: relative;
        }
        
        h1 {
            color: #2c3e50;
            margin-bottom: 10px;
            transition: color 0.3s;
        }
        
        .subtitle {
            color: #7f8c8d;
            font-size: 1.1rem;
            transition: color 0.3s;
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
            transition: background-color 0.3s, box-shadow 0.3s;
        }
        
        .card h2 {
            color: #3498db;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #f0f0f0;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: color 0.3s;
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
            transition: color 0.3s;
        }
        
        input[type="text"],
        input[type="number"],
        select,
        textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            transition: border 0.3s, background-color 0.3s, color 0.3s;
        }
        
        input[type="text"]:focus,
        input[type="number"]:focus,
        select:focus,
        textarea:focus {
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
            flex-wrap: wrap;
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
            transition: background-color 0.3s, transform 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            width: 100%;
        }
        
        .btn:hover {
            background-color: #2980b9;
            transform: translateY(-2px);
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
            transition: background-color 0.3s, color 0.3s, border-color 0.3s;
        }
        
        td {
            padding: 15px;
            border-bottom: 1px solid #eee;
            transition: border-color 0.3s;
        }
        
        tr:hover {
            background-color: #f9f9f9;
            transition: background-color 0.3s;
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
            transition: background-color 0.3s;
        }
        
        .result-label {
            font-size: 18px;
            color: #7f8c8d;
            margin-bottom: 10px;
            transition: color 0.3s;
        }
        
        .result-value {
            font-size: 42px;
            font-weight: 700;
            color: #2c3e50;
            transition: color 0.3s;
        }
        
        .grade {
            font-size: 20px;
            margin-top: 10px;
            color: #3498db;
            font-weight: 600;
            transition: color 0.3s;
        }
        
        .empty-message {
            text-align: center;
            padding: 40px 20px;
            color: #95a5a6;
            font-style: italic;
            transition: color 0.3s;
        }
        
        .instructions {
            background-color: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            transition: background-color 0.3s;
        }
        
        .instructions h3 {
            color: #2c3e50;
            margin-bottom: 10px;
            transition: color 0.3s;
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
            transition: color 0.3s, border-color 0.3s;
        }
        
        .footer-text {
            font-weight: bold;
            color: #2c3e50;
            margin-top: 5px;
            transition: color 0.3s;
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
            transition: border-color 0.3s;
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
        body.dark-theme select,
        body.dark-theme textarea {
            background-color: #2d2d2d;
            border-color: #444;
            color: #e0e0e0;
        }

        body.dark-theme input[type="text"]:focus,
        body.dark-theme input[type="number"]:focus,
        body.dark-theme select:focus,
        body.dark-theme textarea:focus {
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
        
        /* Modal Styles for Export/Import */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background-color: white;
            padding: 30px;
            border-radius: 12px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        body.dark-theme .modal-content {
            background-color: #2d2d2d;
            color: #e0e0e0;
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .modal-close {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: #7f8c8d;
        }
        
        .success-message {
            background-color: #d4edda;
            color: #155724;
            padding: 12px;
            border-radius: 8px;
            margin: 15px 0;
            display: none;
        }
        
        body.dark-theme .success-message {
            background-color: #1e4620;
            color: #a3d9b1;
        }
        
        .warning-message {
            background-color: #fff3cd;
            color: #856404;
            padding: 12px;
            border-radius: 8px;
            margin: 15px 0;
        }
        
        body.dark-theme .warning-message {
            background-color: #4d4200;
            color: #ffeaa7;
        }
        
        .subject-count {
            font-weight: bold;
            color: #3498db;
        }
        
        body.dark-theme .subject-count {
            color: #64b5f6;
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
        
        body[dir="rtl"] header {
            text-align: center;
        }
        
        body[dir="rtl"] .instructions ul {
            padding-left: 0;
            padding-right: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
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
                    
                    <div class="export-buttons" style="margin-top: 15px;">
                        <button class="btn btn-export" id="exportBtn">
                            <i class="fas fa-file-export"></i> Export Data
                        </button>
                        <button class="btn btn-import" id="showImportModal">
                            <i class="fas fa-file-import"></i> Import Data
                        </button>
                    </div>
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

    <!-- Export/Import Modal -->
    <div class="modal" id="exportModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2><i class="fas fa-file-export"></i> Export/Import Data</h2>
                <button class="modal-close" id="closeModal">&times;</button>
            </div>
            
            <div class="warning-message">
                <i class="fas fa-exclamation-triangle"></i> Importing data will replace all current subjects! 
                You currently have <span class="subject-count">0</span> subjects.
            </div>
            
            <div class="success-message" id="successMessage">
                <i class="fas fa-check-circle"></i> Data exported successfully!
            </div>
            
            <div class="form-group">
                <label for="exportData">Export Data (JSON)</label>
                <textarea id="exportData" rows="6" readonly placeholder="Your data will appear here..."></textarea>
            </div>
            
            <div class="form-group">
                <label for="importData">Import Data (Paste JSON here)</label>
                <textarea id="importData" rows="6" placeholder='Paste your data here in format: [{"name":"Math","hasTD":true,...}]'></textarea>
            </div>
            
            <div class="export-buttons">
                <button class="btn btn-export" id="copyData">
                    <i class="fas fa-copy"></i> Copy to Clipboard
                </button>
                <button class="btn btn-import" id="importDataBtn">
                    <i class="fas fa-file-import"></i> Import Data
                </button>
            </div>
        </div>
    </div>

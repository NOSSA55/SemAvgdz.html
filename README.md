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

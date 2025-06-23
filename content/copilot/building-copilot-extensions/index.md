<!DOCTYPE.html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>İş Teslim Formu (A4 & Kaydetme Özellikli)</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* A4 Page Sizing and Styles */
        @page {
            size: A4;
            margin: 0;
        }
        body {
            font-family: 'Inter', sans-serif;
            background-color: #e0e0e0; /* Off-page background */
            display: flex;
            justify-content: center;
            padding-top: 2rem;
            padding-bottom: 2rem;
        }
        .container {
            background-color: #ffffff;
            width: 210mm; /* A4 Width */
            min-height: 297mm; /* A4 Height */
            padding: 15mm; /* Margins */
            box-shadow: 0 0 15px rgba(0,0,0,0.2); /* Shadow for paper effect */
            box-sizing: border-box; /* Include padding and border in width */
            display: flex;
            flex-direction: column;
        }
        .content-wrapper {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }
        .header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 25px;
        }
        .fiş-başlık {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            border-radius: 8px;
            font-size: 1.5rem;
            font-weight: bold;
            text-align: center;
        }
        .info-box {
            border: 1px solid #ccc;
            border-radius: 8px;
            padding: 12px;
            margin-bottom: 25px;
        }
        .info-line {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
            font-size: 0.9rem;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 25px;
            font-size: 0.9rem;
        }
        th, td {
            border: 1px solid #ccc;
            padding: 10px;
            text-align: left;
            vertical-align: middle;
            height: 40px; /* Fixed row height */
        }
        th {
            background-color: #f0f0f0;
            font-weight: 600;
        }
        tfoot td {
            font-weight: bold;
            background-color: #f0f0f0;
        }
        .signature-section {
            display: flex;
            justify-content: space-around;
            margin-top: 60px; /* More space for signatures */
            page-break-inside: avoid; /* Prevent breaking at page end */
        }
        .signature-box {
            width: 40%;
            text-align: center;
        }
        .signature-line {
            border-bottom: 1px dashed #888;
            margin-top: 50px;
            margin-bottom: 5px;
        }
        .footer-text {
            font-size: 0.9rem;
            color: #555;
            text-align: center;
        }
        .input-field, .editable-main-input {
            border: none;
            outline: none;
            background-color: transparent;
            width: 100%;
            height: 100%;
        }
        .editable-main-input {
             border-bottom: 1px dashed #aaa;
             padding: 2px 0;
             flex-grow: 1;
        }
        [contenteditable="true"] {
            padding: 2px 4px;
            border-radius: 3px;
        }
        [contenteditable="true"]:hover {
            background-color: #f0f4f8;
        }
        [contenteditable="true"]:focus {
            outline: 1px solid #60a5fa;
            background-color: #e6f2ff;
        }
        .main-button-container {
             margin-top: 1rem;
             page-break-inside: avoid;
        }

        /* Print Styles */
        @media print {
            @page {
                size: A4;
                margin: 20mm 15mm;
            }
            @page {
                @bottom-center {
                    content: "Sayfa " counter(page) " / " counter(pages);
                    font-size: 10pt;
                    color: #666;
                }
            }
            body { background-color: #fff; padding: 0; margin: 0; }
            .container { box-shadow: none; margin: 0; padding: 0; width: 100%; min-height: initial; border: none; }
            .main-button-container, .delete-row-btn, #addRowContainer { 
                display: none; 
            }
            .fiş-başlık, th, tfoot td { 
                -webkit-print-color-adjust: exact; 
                color-adjust: exact; 
            }
           
            /* Remove editing visuals */
            [contenteditable="true"]:hover, [contenteditable="true"]:focus {
                background-color: transparent !important;
                box-shadow: none !important;
                outline: none !important;
            }
            .editable-main-input {
                border-bottom: 1px solid transparent;
            }
            input {
                border: none !important;
                box-shadow: none !important;
            }
            /* Hide date picker icon */
            input[type="date"]::-webkit-inner-spin-button,
            input[type="date"]::-webkit-calendar-picker-indicator {
                display: none;
                -webkit-appearance: none;
            }
        }
    </style>
</head>
<body>
    <div class="container" id="invoiceContainer">
        <div class="content-wrapper">
            <div class="header">
                <div class="company-info text-gray-800 text-left space-y-1">
                    <h1 id="companyName" class="text-2xl font-bold text-blue-800" contenteditable="true">ASLAN HAFRİYAT</h1>
                    <p id="companySubtitle" class="text-xs text-gray-600 italic -mt-1 mb-2" contenteditable="true">Kiralık İş Makineleri- Hafriyat-Nakliye-Altyapı & İnşaat Çözümleri Hizmetleri</p>
                    <p id="contactPerson" class="text-sm font-semibold pt-2" contenteditable="true">İBRAHİM ASLAN</p>
                    <p class="text-sm flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-2 shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" /></svg>
                        <span id="companyPhone" contenteditable="true">0541 315 30 46</span>
                    </p>
                    <p class="text-sm flex items-center">
                         <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-2 shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" /><path stroke-linecap="round" stroke-linejoin="round" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" /></svg>
                        <span id="companyAddress" contenteditable="true">ADRES:DİKBIYIK MAH. ATATÜRK BUL. NO:110 ÇARŞAMBA/SAMSUN</span>
                    </p>
                    <p class="text-sm flex items-center">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 mr-2 shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path stroke-linecap="round" stroke-linejoin="round" d="M21 12a9 9 0 01-9 9m9-9a9 9 0 00-9-9m9 9H3m9 9a9 9 0 01-9-9m9 9V3m0 18a9 9 0 00-9-9m9 9c1.657 0 3-4.03 3-9s-1.343-9-3-9m0 18c-1.657 0-3-4.03-3-9s1.343-9 3-9m-9 9h18" /></svg>
                        <span id="companyWebsite" contenteditable="true">www.aslanhafriyat.com</span>
                    </p>
                </div>
                <div id="invoiceTitle" class="fiş-başlık ml-auto" contenteditable="true">
                    İŞ TESLİM FORMU
                </div>
            </div>

            <div class="info-box">
                <div class="info-line">
                    <span class="font-semibold text-gray-700 mr-2" contenteditable="true">SAYIN:</span> 
                    <input type="text" id="customerName" class="editable-main-input">
                </div>
                 <div class="info-line">
                    <span class="font-semibold text-gray-700 mr-2" contenteditable="true">TELEFON:</span> 
                    <input type="text" id="customerPhone" class="editable-main-input">
                </div>
                 <div class="info-line">
                    <span class="font-semibold text-gray-700 mr-2" contenteditable="true">ADRES:</span> 
                    <input type="text" id="customerAddress" class="editable-main-input">
                </div>
                <div class="info-line">
                    <span class="font-semibold text-gray-700 mr-2" contenteditable="true">TESLİM TARİHİ:</span> 
                    <input type="date" id="deliveryDate" class="editable-main-input w-1/2">
                </div>
            </div>

            <table>
                <thead>
                    <tr>
                        <th class="w-2/12" contenteditable="true">TARİH</th>
                        <th class="w-5/12" contenteditable="true">YAPILAN İŞ</th>
                        <th class="w-2/12" contenteditable="true">SEFER-SAAT</th>
                        <th class="w-2/12" contenteditable="true">TUTARI</th>
                        <th class="w-1/12 text-center"></th> <!-- Column for delete button -->
                    </tr>
                </thead>
                <tbody id="itemRows">
                    <!-- Rows will be dynamically generated by JavaScript -->
                </tbody>
                <tfoot>
                    <tr>
                        <td colspan="3" class="text-right font-bold" contenteditable="true">TOPLAM:</td>
                        <td class="text-right"><input type="text" id="totalAmount" class="input-field font-bold text-right" readonly value="0,00"></td>
                        <td></td> <!-- Empty cell for alignment -->
                    </tr>
                </tfoot>
            </table>
           
            <div id="addRowContainer" class="text-center mt-4">
                 <button id="addRowBtn" class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg shadow-md transition duration-300">
                    Satır Ekle
                </button>
            </div>
           
             <div class="footer-text mt-auto pt-8" id="footerText" contenteditable="true">
                Yukarıda cinsi ve miktarı yazılı malları sağlam ve eksiksiz olarak teslim aldım.
            </div>

            <div class="signature-section">
                <div class="signature-box">
                    <div class="signature-line"></div>
                    <span class="font-semibold" contenteditable="true">TESLİM EDEN</span>
                    <p class="text-sm text-gray-600 mt-1" contenteditable="true">(Adı Soyadı / Kaşe)</p>
                </div>
                <div class="signature-box">
                    <div class="signature-line"></div>
                    <span class="font-semibold" contenteditable="true">TESLİM ALAN</span>
                    <p class="text-sm text-gray-600 mt-1" contenteditable="true">(Adı Soyadı / Kaşe)</p>
                </div>
            </div>
        </div>
       
        <div class="main-button-container text-center flex justify-center items-center space-x-4 mt-4">
            <button id="saveDataBtn" class="bg-green-600 hover:bg-green-700 text-white font-bold py-2 px-4 rounded-lg shadow-md transition duration-300">
                Kaydet
            </button>
            <button id="printBtn" class="bg-gray-600 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded-lg shadow-md transition duration-300">
                Yazdır
            </button>
        </div>
        <p id="saveMessage" class="text-center text-green-600 mt-2 h-4"></p>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const container = document.getElementById('invoiceContainer');
            const itemRowsBody = document.getElementById('itemRows');
            const addRowBtn = document.getElementById('addRowBtn');
            const saveDataBtn = document.getElementById('saveDataBtn');
            const printBtn = document.getElementById('printBtn');
            const saveMessage = document.getElementById('saveMessage');
            const storageKey = 'invoiceData_A4_v25_prepopulated'; // Version updated to reflect new data

            // This is the data you provided, formatted for the form.
            const preloadedData = [
                { date: '2025-05-21', description: 'JBC', quantity: '2 SAAT', amount: '0.00' },
                { date: '2025-05-22', description: '140 PALETLİ', quantity: '10 SAAT', amount: '0.00' },
                { date: '2025-05-22', description: '210 PALETLİ', quantity: '10 SAAT', amount: '0.00' },
                { date: '2025-05-22', description: 'MEZARLIK TOPRAK NAKLİYE', quantity: '25 SEFER', amount: '0.00' },
                { date: '2025-05-23', description: 'JBC', quantity: '5 SAAT', amount: '0.00' },
                { date: '2025-05-23', description: '140 PALETLİ', quantity: '10 SAAT', amount: '0.00' },
                { date: '2025-05-23', description: '210 PALETLİ', quantity: '9 SAAT', amount: '0.00' },
                { date: '2025-05-23', description: 'SAHA İÇİ NAKLİYE', quantity: '25 SEFER', amount: '0.00' },
                { date: '2025-05-23', description: 'MEZARLIK TOPRAK NAKLİYE', quantity: '1 SEFER', amount: '0.00' },
                { date: '2025-05-24', description: '140 PALETLİ', quantity: '10 SAAT', amount: '0.00' },
                { date: '2025-05-24', description: '210 PALETLİ', quantity: '9 SAAT', amount: '0.00' },
                { date: '2025-05-24', description: 'SAHA İÇİ NAKLİYE', quantity: '33 SEFER', amount: '0.00' },
                { date: '2025-05-24', description: 'JBC', quantity: '4 SAAT', amount: '0.00' },
                { date: '2025-05-25', description: 'JBC', quantity: '4 SAAT', amount: '0.00' },
                { date: '2025-05-25', description: 'SAHA İÇİ NAKLİYE', quantity: '24 SEFER', amount: '0.00' },
                { date: '2025-05-25', description: '140 PALETLİ', quantity: '9.5 SAAT', amount: '0.00' },
                { date: '2025-05-25', description: '210 PALETLİ', quantity: '7 SAAT', amount: '0.00' },
                { date: '2025-05-26', description: 'SİLİNDİR + YOL', quantity: '1.5 SAAT', amount: '2500.00' },
                { date: '2025-05-26', description: 'OSB NAKLİYE', quantity: '5 SEFER', amount: '0.00' },
                { date: '2025-05-26', description: 'SAHA İÇİ NAKLİYE', quantity: '5 SEFER', amount: '0.00' },
                { date: '2025-05-26', description: 'JBC', quantity: '2.5 SAAT', amount: '0.00' },
                { date: '2025-05-26', description: '140 PALETLİ', quantity: '4 SAAT', amount: '0.00' },
                { date: '2025-05-26', description: '210 PALETLİ', quantity: '3 SAAT', amount: '0.00' },
                { date: '2025-05-27', description: 'OSB NAKLİYE', quantity: '7 SAAT', amount: '0.00' },
                { date: '2025-05-27', description: '210 PALETLİ', quantity: '3 SAAT', amount: '0.00' },
                { date: '2025-05-28', description: 'OSB NAKLİYE', quantity: '4 SAAT', amount: '0.00' },
                { date: '2025-05-28', description: '210 PALETLİ', quantity: '1.5 SAAT', amount: '0.00' },
                { date: '2025-05-28', description: 'MICIR', quantity: '3 TIR', amount: '0.00' },
                { date: '2025-05-29', description: 'MICIR', quantity: '3 TIR', amount: '0.00' },
                { date: '2025-05-30', description: 'MICIR', quantity: '4 TIR', amount: '0.00' },
                { date: '2025-06-02', description: 'JBC', quantity: '5 SAAT', amount: '0.00' },
                { date: '2025-06-02', description: 'MICIR', quantity: '1 TIR', amount: '0.00' },
                { date: '2025-06-03', description: 'MICIR', quantity: '3 TIR', amount: '0.00' },
                { date: '2025-06-03', description: '140 PALETLİ', quantity: '12 SAAT', amount: '0.00' },
                { date: '2025-06-03', description: 'JBC', quantity: '11 SAAT', amount: '0.00' },
                { date: '2025-06-03', description: 'SAHA İÇİ NAKLİYE', quantity: '30 SEFER', amount: '0.00' },
                { date: '2025-06-04', description: 'LAZER', quantity: '10 SAAT', amount: '0.00' },
                { date: '2025-06-04', description: '140 PALETLİ', quantity: '6 SAAT', amount: '0.00' },
                { date: '2025-06-04', description: 'OSB NAKLİYE', quantity: '3 SEFER', amount: '0.00' },
                { date: '2025-06-04', description: 'JBC', quantity: '6 SAAT', amount: '0.00' },
                { date: '2025-06-04', description: 'MICIR', quantity: '2 TIR', amount: '0.00' },
                { date: '2025-06-05', description: 'OSB NAKLİYE', quantity: '3 SEFER', amount: '0.00' },
                { date: '2025-06-09', description: 'OSB NAKLİYE', quantity: '9 SEFER', amount: '0.00' },
                { date: '2025-06-09', description: '140 PALETLİ', quantity: '4 SAAT', amount: '0.00' },
                { date: '2025-06-10', description: 'SİLİNDİR + YOL', quantity: '2 SAAT', amount: '2500.00' },
            ];

            /**
             * Returns today's date in YYYY-MM-DD format.
             * @returns {string}
             */
            const getTodayDate = () => new Date().toISOString().split('T')[0];

            /**
             * Saves all editable form data to localStorage.
             */
            const saveData = () => {
                const tableRows = [];
                itemRowsBody.querySelectorAll('tr').forEach(row => {
                    tableRows.push({
                        date: row.querySelector('.date-input').value,
                        description: row.querySelector('.description-input').value,
                        quantity: row.querySelector('.quantity-input').value,
                        amount: row.querySelector('.amount-input').value,
                    });
                });

                const dataToSave = {
                    companyName: document.getElementById('companyName').innerHTML,
                    companySubtitle: document.getElementById('companySubtitle').innerHTML,
                    contactPerson: document.getElementById('contactPerson').innerHTML,
                    companyPhone: document.getElementById('companyPhone').innerHTML,
                    companyAddress: document.getElementById('companyAddress').innerHTML,
                    companyWebsite: document.getElementById('companyWebsite').innerHTML,
                    invoiceTitle: document.getElementById('invoiceTitle').innerHTML,
                    customerName: document.getElementById('customerName').value,
                    customerPhone: document.getElementById('customerPhone').value,
                    customerAddress: document.getElementById('customerAddress').value,
                    deliveryDate: document.getElementById('deliveryDate').value,
                    footerText: document.getElementById('footerText').innerHTML,
                    tableHeaders: {
                        date: document.querySelector('th:nth-child(1)').innerHTML,
                        description: document.querySelector('th:nth-child(2)').innerHTML,
                        quantity: document.querySelector('th:nth-child(3)').innerHTML,
                        amount: document.querySelector('th:nth-child(4)').innerHTML
                    },
                    tableRows: tableRows
                };

                local
                

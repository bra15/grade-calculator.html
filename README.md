<!DOCTYPE html>  <html lang="ar" dir="rtl">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>حاسبة النقط الاحترافية</title>  
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>  
    <style>  
        * {  
            margin: 0;  
            padding: 0;  
            box-sizing: border-box;  
        }  body {  
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;  
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);  
        min-height: 100vh;  
        padding: 20px;  
    }  
      
    .container {  
        max-width: 1400px;  
        margin: 0 auto;  
        background: white;  
        border-radius: 20px;  
        box-shadow: 0 20px 40px rgba(0,0,0,0.1);  
        overflow: hidden;  
    }  
      
    .header {  
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);  
        color: white;  
        padding: 30px;  
        text-align: center;  
    }  
      
    .header h1 {  
        font-size: 2.5em;  
        margin-bottom: 10px;  
    }  
      
    .info-section {  
        background: #f8f9fa;  
        padding: 20px;  
        border-bottom: 3px solid #667eea;  
    }  
      
    .info-grid {  
        display: grid;  
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));  
        gap: 15px;  
        margin-bottom: 20px;  
    }  
      
    .info-item {  
        background: white;  
        padding: 15px;  
        border-radius: 10px;  
        box-shadow: 0 2px 5px rgba(0,0,0,0.1);  
        text-align: center;  
    }  
      
    .info-label {  
        font-weight: bold;  
        color: #667eea;  
        margin-bottom: 5px;  
    }  
      
    .info-value {  
        font-size: 1.2em;  
        color: #333;  
    }  
      
    .content {  
        padding: 30px;  
    }  
      
    .grade-table {  
        width: 100%;  
        border-collapse: collapse;  
        margin-bottom: 30px;  
        border-radius: 10px;  
        overflow: hidden;  
        box-shadow: 0 5px 15px rgba(0,0,0,0.1);  
    }  
      
    .grade-table th {  
        background: #343a40;  
        color: white;  
        padding: 12px 6px;  
        text-align: center;  
        font-weight: bold;  
        font-size: 11px;  
        line-height: 1.2;  
    }  
      
    .grade-table td {  
        padding: 10px 6px;  
        text-align: center;  
        border-bottom: 1px solid #dee2e6;  
        font-size: 12px;  
    }  
      
    .grade-table tr:nth-child(even) {  
        background: #f8f9fa;  
    }  
      
    .grade-table tr:hover {  
        background: #e9ecef;  
    }  
      
    .subject-name {  
        font-weight: bold;  
        text-align: right !important;  
        padding-right: 15px !important;  
        background: #e9ecef !important;  
        min-width: 120px;  
    }  
      
    .grade-input {  
        width: 50px;  
        padding: 4px;  
        border: 2px solid #dee2e6;  
        border-radius: 5px;  
        text-align: center;  
        font-size: 11px;  
        transition: all 0.3s;  
    }  
      
    .grade-input:focus {  
        outline: none;  
        border-color: #667eea;  
        box-shadow: 0 0 0 2px rgba(102, 126, 234, 0.1);  
    }  
      
    .grade-input:disabled {  
        background: #f8f9fa;  
        color: #6c757d;  
        border-color: #e9ecef;  
    }  
      
    .average-cell {  
        font-weight: bold;  
        color: #28a745;  
        font-size: 12px;  
        background: #d4edda !important;  
    }  
      
    .coefficient-cell {  
        font-weight: bold;  
        color: #dc3545;  
        background: #f8d7da !important;  
    }  
      
    .final-average-row {  
        background: linear-gradient(135deg, #28a745, #20c997) !important;  
        color: white !important;  
        font-weight: bold;  
    }  
      
    .final-average-row td {  
        background: transparent !important;  
        color: white !important;  
        font-size: 16px;  
    }  
      
    .controls {  
        display: flex;  
        justify-content: center;  
        gap: 15px;  
        margin: 30px 0;  
        flex-wrap: wrap;  
    }  
      
    .btn {  
        padding: 12px 25px;  
        border: none;  
        border-radius: 25px;  
        cursor: pointer;  
        font-size: 16px;  
        font-weight: bold;  
        transition: all 0.3s;  
        text-decoration: none;  
        display: inline-block;  
    }  
      
    .btn-primary {  
        background: linear-gradient(135deg, #667eea, #764ba2);  
        color: white;  
    }  
      
    .btn-success {  
        background: linear-gradient(135deg, #28a745, #20c997);  
        color: white;  
    }  
      
    .btn-warning {  
        background: linear-gradient(135deg, #ffc107, #ff8c00);  
        color: white;  
    }  
      
    .btn:hover {  
        transform: translateY(-2px);  
        box-shadow: 0 5px 15px rgba(0,0,0,0.2);  
    }  
      
    .stats-section {  
        background: #f8f9fa;  
        padding: 20px;  
        border-radius: 15px;  
        margin: 20px 0;  
    }  
      
    .stats-grid {  
        display: grid;  
        grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));  
        gap: 15px;  
    }  
      
    .stat-card {  
        background: white;  
        padding: 20px;  
        border-radius: 10px;  
        text-align: center;  
        box-shadow: 0 2px 10px rgba(0,0,0,0.1);  
    }  
      
    .stat-value {  
        font-size: 2em;  
        font-weight: bold;  
        color: #667eea;  
    }  
      
    .stat-label {  
        color: #666;  
        margin-top: 5px;  
        font-size: 14px;  
    }  
      
    .disabled-cell {  
        background: #f8f9fa !important;  
        color: #6c757d !important;  
    }  
      
    @media (max-width: 768px) {  
        .grade-table {  
            font-size: 10px;  
        }  
          
        .grade-input {  
            width: 45px;  
            padding: 3px;  
            font-size: 10px;  
        }  
          
        .content {  
            padding: 15px;  
        }  
          
        .grade-table th {  
            font-size: 9px;  
            padding: 8px 4px;  
        }  
    }  
</style>

</head>  
<body>  
    <div class="container">  
        <div class="header">  
            <h1>📊 بيان النتائج الدراسية</h1>  
            <p>نظام حساب النقط الاحترافي</p>  
        </div>  <div class="info-section">  
        <div class="info-grid">  
            <div class="info-item">  
                <div class="info-label">المؤسسة</div>  
                <div class="info-value" id="institution">ثا إعدادي مسار دولي</div>  
            </div>  
            <div class="info-item">  
                <div class="info-label">المستوى</div>  
                <div class="info-value" id="level">3APIC-4</div>  
            </div>  
            <div class="info-item">  
                <div class="info-label">عدد التلاميذ</div>  
                <div class="info-value" id="students">40</div>  
            </div>  
            <div class="info-item">  
                <div class="info-label">الفصل</div>  
                <div class="info-value" id="semester">الأول</div>  
            </div>  
        </div>  
    </div>  
      
    <div class="content">  
        <table class="grade-table" id="gradeTable">  
            <thead>  
                <tr>  
                    <th rowspan="2">المادة</th>  
                    <th>الفرض 1</th>  
                    <th>الفرض 2</th>  
                    <th>الفرض 3</th>  
                    <th>الفرض 4</th>  
                    <th>الأنشطة</th>  
                    <th rowspan="2">المعدل</th>  
                    <th rowspan="2">المعامل</th>  
                </tr>  
                <tr id="percentageRow">  
                    <!-- النسب المئوية ستُضاف هنا -->  
                </tr>  
            </thead>  
            <tbody id="gradeBody">  
                <!-- البيانات ستُدرج هنا بواسطة JavaScript -->  
            </tbody>  
        </table>  

        <div class="stats-section">  
            <h3 style="text-align: center; margin-bottom: 20px; color: #667eea;">📈 الإحصائيات العامة</h3>  
            <div class="stats-grid">  
                <div class="stat-card">  
                    <div class="stat-value" id="totalAverage">0.00</div>  
                    <div class="stat-label">المعدل العام</div>  
                </div>  
                <div class="stat-card">  
                    <div class="stat-value" id="passedSubjects">0</div>  
                    <div class="stat-label">المواد المنجزة</div>  
                </div>  
                <div class="stat-card">  
                    <div class="stat-value" id="highestGrade">0.00</div>  
                    <div class="stat-label">أعلى معدل</div>  
                </div>  
                <div class="stat-card">  
                    <div class="stat-value" id="lowestGrade">0.00</div>  
                    <div class="stat-label">أقل معدل</div>  
                </div>  
                <div class="stat-card">  
                    <div class="stat-value" id="totalCoefficient">9</div>  
                    <div class="stat-label">مجموع المعاملات</div>  
                </div>  
                <div class="stat-card">  
                    <div class="stat-value" id="gradeStatus">--</div>  
                    <div class="stat-label">الحالة</div>  
                </div>  
            </div>  
        </div>  

        <div class="controls">  
            <button class="btn btn-primary" onclick="calculateAll()">حساب المعدلات</button>  
            <button class="btn btn-success" onclick="generateExcel()">تحميل إكسل</button>  
            <button class="btn btn-warning" onclick="printReport()">طباعة التقرير</button>  
            <button class="btn btn-primary" onclick="clearAll()">مسح الكل</button>  
        </div>  
    </div>  
</div>  

<script>  
    const subjects = [  
        {  
            name: 'الرياضيات',   
            coefficient: 1,   
            tests: 3,  
            weights: [0.333, 0.333, 0.334, 0, 0], // ثلاث فروض بنسب متساوية  
            labels: ['33.3%', '33.3%', '33.4%', '--', '--']  
        },  
        {  
            name: 'اللغة العربية',   
            coefficient: 1,   
            tests: 2,  
            weights: [0.375, 0.375, 0, 0, 0.25], // فرضان + أنشطة  
            labels: ['37.5%', '37.5%', '--', '--', '25%']  
        },  
        {  
            name: 'الاجتماعيات',   
            coefficient: 1,   
            tests: 2,  
            weights: [0.375, 0.375, 0, 0, 0.25], // فرضان + أنشطة  
            labels: ['37.5%', '37.5%', '--', '--', '25%']  
        },  
        {  
            name: 'التربية الإسلامية',   
            coefficient: 1,   
            tests: 2,  
            weights: [0.375, 0.375, 0, 0, 0.25], // فرضان + أنشطة  
            labels: ['37.5%', '37.5%', '--', '--', '25%']  
        },  
        {  
            name: 'اللغة الإنجليزية',   
            coefficient: 1,   
            tests: 2,  
            weights: [0.375, 0.375, 0, 0, 0.25], // فرضان + أنشطة  
            labels: ['37.5%', '37.5%', '--', '--', '25%']  
        },  
        {  
            name: 'التربية البدنية',   
            coefficient: 1,   
            tests: 3,  
            weights: [0.333, 0.333, 0.334, 0, 0], // ثلاث فروض بنسب متساوية  
            labels: ['33.3%', '33.3%', '33.4%', '--', '--']  
        },  
        {  
            name: 'اللغة الفرنسية',   
            coefficient: 1,   
            tests: 4,  
            weights: [0.2, 0.2, 0.2, 0.2, 0.2], // أربعة فروض + أنشطة  
            labels: ['20%', '20%', '20%', '20%', '20%']  
        },  
        {  
            name: 'علوم الحياة والأرض',   
            coefficient: 1,   
            tests: 2,  
            weights: [0.375, 0.375, 0, 0, 0.25], // فرضان + أنشطة  
            labels: ['37.5%', '37.5%', '--', '--', '25%']  
        },  
        {  
            name: 'الفيزياء والكيمياء',   
            coefficient: 1,   
            tests: 3,  
            weights: [0.25, 0.25, 0.25, 0, 0.25], // ثلاث فروض + أنشطة  
            labels: ['25%', '25%', '25%', '--', '25%']  
        }  
    ];  

    let gradeData = {};  

    function initializeTable() {  
        const tbody = document.getElementById('gradeBody');  
        const percentageRow = document.getElementById('percentageRow');  
          
        tbody.innerHTML = '';  
        percentageRow.innerHTML = '';  

        // Add percentage headers  
        percentageRow.innerHTML = `  
            <th id="p1">--</th>  
            <th id="p2">--</th>  
            <th id="p3">--</th>  
            <th id="p4">--</th>  
            <th id="p5">--</th>  
        `;  

        subjects.forEach((subject, index) => {  
            const row = document.createElement('tr');  
            let cellsHTML = `<td class="subject-name">${subject.name}</td>`;  
              
            // Add grade input cells  
            for (let i = 0; i < 5; i++) {  
                const isDisabled = subject.weights[i] === 0;  
                const cellClass = isDisabled ? 'disabled-cell' : '';  
                cellsHTML += `  
                    <td class="${cellClass}">  
                        <input type="number"   
                            class="grade-input"   
                            min="0" max="20" step="0.01"   
                            ${isDisabled ? 'disabled' : ''}  
                            onchange="updateGrade(${index}, ${i}, this.value)"   
                            placeholder="${isDisabled ? '--' : '0.00'}">  
                    </td>  
                `;  
            }  
              
            cellsHTML += `  
                <td class="average-cell" id="avg-${index}">--</td>  
                <td class="coefficient-cell">${subject.coefficient}</td>  
            `;  
              
            row.innerHTML = cellsHTML;  
            tbody.appendChild(row);  

            // Initialize grade data  
            gradeData[index] = [null, null, null, null, null];  
        });  

        // Add final average row  
        const finalRow = document.createElement('tr');  
        finalRow.className = 'final-average-row';  
        finalRow.innerHTML = `  
            <td colspan="6" style="text-align: center; font-size: 18px;">المعدل العام</td>  
            <td id="finalAverage" style="font-size: 18px;">--</td>  
            <td style="font-size: 18px;">--</td>  
        `;  
        tbody.appendChild(finalRow);  
    }  

    function updateGrade(subjectIndex, gradeIndex, value) {  
        gradeData[subjectIndex][gradeIndex] = value ? parseFloat(value) : null;  
        calculateSubjectAverage(subjectIndex);  
        calculateFinalAverage();  
        updateStats();  
        updatePercentageHeaders(subjectIndex);  
    }  

    function updatePercentageHeaders(activeSubjectIndex) {  
        const subject = subjects[activeSubjectIndex];  
        const labels = subject.labels;  
          
        for (let i = 0; i < 5; i++) {  
            document.getElementById(`p${i+1}`).textContent = labels[i];  
        }  
    }  

    function calculateSubjectAverage(subjectIndex) {  
        const subject = subjects[subjectIndex];  
        const grades = gradeData[subjectIndex];  
        const weights = subject.weights;  
          
        let sum = 0;  
        let totalWeight = 0;  

        for (let i = 0; i < grades.length; i++) {  
            if (grades[i] !== null && weights[i] > 0) {  
                sum += grades[i] * weights[i];  
                totalWeight += weights[i];  
            }  
        }  

        const average = totalWeight > 0 ? (sum / totalWeight).toFixed(2) : '--';  
        document.getElementById(`avg-${subjectIndex}`).textContent = average;  
        return average !== '--' ? parseFloat(average) : null;  
    }  

    function calculateFinalAverage() {  
        let totalWeightedSum = 0;  
        let totalCoefficients = 0;  

        subjects.forEach((subject, index) => {  
            const avg = calculateSubjectAverage(index);  
            if (avg !== null) {  
                totalWeightedSum += avg * subject.coefficient;  
                totalCoefficients += subject.coefficient;  
            }  
        });  

        const finalAvg = totalCoefficients > 0 ? (totalWeightedSum / totalCoefficients).toFixed(2) : '--';  
        document.getElementById('finalAverage').textContent = finalAvg;  
        document.getElementById('totalAverage').textContent = finalAvg;  
    }  

    function updateStats() {  
        let passedCount = 0;  
        let highestGrade = 0;  
        let lowestGrade = 20;  
        let hasGrades = false;  

        subjects.forEach((_, index) => {  
            const avg = calculateSubjectAverage(index);  
            if (avg !== null) {  
                passedCount++;  
                hasGrades = true;  
                if (avg > highestGrade) highestGrade = avg;  
                if (avg < lowestGrade) lowestGrade = avg;  
            }  
        });  

        document.getElementById('passedSubjects').textContent = passedCount;  
        document.getElementById('highestGrade').textContent = hasGrades ? highestGrade.toFixed(2) : '0.00';  
        document.getElementById('lowestGrade').textContent = hasGrades ? lowestGrade.toFixed(2) : '0.00';  

        // Update status  
        const finalAvg = parseFloat(document.getElementById('totalAverage').textContent);  
        let status = '--';  
        if (!isNaN(finalAvg)) {  
            if (finalAvg >= 16) status = 'ممتاز';  
            else if (finalAvg >= 14) status = 'جيد جداً';  
            else if (finalAvg >= 12) status = 'جيد';  
            else if (finalAvg >= 10) status = 'مقبول';  
            else status = 'ضعيف';  
        }  
        document.getElementById('gradeStatus').textContent = status;  
    }  

    function calculateAll() {  
        subjects.forEach((_, index) => {  
            calculateSubjectAverage(index);  
        });  
        calculateFinalAverage();  
        updateStats();  
    }  

    function generateExcel() {  
        const wb = XLSX.utils.book_new();  
          
        // Prepare data for Excel  
        const data = [  
            ['بيان النتائج الدراسية'],  
            [''],  
            ['المؤسسة: ثا إعدادي مسار دولي', 'المستوى: 3APIC-4', 'عدد التلاميذ: 40'],  
            [''],  
            ['المادة', 'الفرض 1', 'الفرض 2', 'الفرض 3', 'الفرض 4', 'الأنشطة', 'المعدل', 'المعامل']  
        ];  

        subjects.forEach((subject, index) => {  
            const grades = gradeData[index];  
            const avg = calculateSubjectAverage(index);  
            const row = [subject.name];  
              
            // Add grades with proper formatting  
            for (let i = 0; i < 5; i++) {  
                if (subject.weights[i] === 0) {  
                    row.push('--');  
                } else {  
                    row.push(grades[i] || '');  
                }  
            }  
              
            row.push(avg || '');  
            row.push(subject.coefficient);  
            data.push(row);  
        });  

        // Add final average  
        const finalAvg = document.getElementById('totalAverage').textContent;  
        data.push(['', '', '', '', '', '', '', '']);  
        data.push(['المعدل العام', '', '', '', '', '', finalAvg, '']);  

        // Add statistics  
        data.push(['', '', '', '', '', '', '', '']);  
        data.push(['الإحصائيات']);  
        data.push(['المعدل العام', finalAvg]);  
        data.push(['المواد المنجزة', document.getElementById('passedSubjects').textContent]);  
        data.push(['أعلى معدل', document.getElementById('highestGrade').textContent]);  
        data.push(['أقل معدل', document.getElementById('lowestGrade').textContent]);  
        data.push(['الحالة', document.getElementById('gradeStatus').textContent]);  

        const ws = XLSX.utils.aoa_to_sheet(data);  
          
        // Set column widths  
        ws['!cols'] = [  
            {wch: 25}, {wch: 12}, {wch: 12}, {wch: 12},   
            {wch: 12}, {wch: 15}, {wch: 12}, {wch: 10}  
        ];  

        XLSX.utils.book_append_sheet(wb, ws, 'بيان النتائج');  
          
        // Generate filename with current date  
        const now = new Date();  
        const filename = `بيان_النتائج_${now.getFullYear()}-${(now.getMonth()+1).toString().padStart(2,'0')}-${now.getDate().toString().padStart(2,'0')}.xlsx`;  
          
        XLSX.writeFile(wb, filename);  
          
        alert('تم تحميل ملف الإكسل بنجاح! ✅');  
    }  

    function printReport() {  
        window.print();  
    }  

    function clearAll() {  
        if (confirm('هل أنت متأكد من مسح جميع البيانات؟')) {  
            // Clear all inputs  
            document.querySelectorAll('.grade-input').forEach(input => {  
                input.value = '';  
            });  
              
            // Reset data  
            gradeData = {};  
            subjects.forEach((_, index) => {  
                gradeData[index] = [null, null, null, null, null];  
            });  
              
            // Reset displays  
            subjects.forEach((_, index) => {  
                document.getElementById(`avg-${index}`).textContent = '--';  
            });  
            document.getElementById('finalAverage').textContent = '--';  
            document.getElementById('totalAverage').textContent = '0.00';  
            document.getElementById('passedSubjects').textContent = '0';  
            document.getElementById('highestGrade').textContent = '0.00';  
            document.getElementById('lowestGrade').textContent = '0.00';  
            document.getElementById('gradeStatus').textContent = '--';  
              
            // Reset percentage headers  
            for (let i = 1; i <= 5; i++) {  
                document.getElementById(`p${i}`).textContent = '--';  
            }  
              
            alert('تم مسح جميع البيانات! ✅');  
        }  
    }  

    // Initialize the table when page loads  
    window.onload = function() {  
        initializeTable();  
    };  

    // Print styles  
    const printStyles = `  
        @media print {  
            body { background: white !important; }  
            .container { box-shadow: none !important; }  
            .controls { display: none !important; }  
            .header { background: #667eea !important; }  
        }  
    `;  
      
    const style = document.createElement('style');  
    style.textContent = printStyles;  
    document.head.appendChild(style);  
</script>

</body>  
</html>  
اعطيني رابط html  بدون تصرفك ولا لف ولا دوران 

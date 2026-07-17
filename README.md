<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>แบบฟอร์มเก็บข้อมูลนักเรียน</title>
    <style>
        /* --- Google Fonts (Prompt) --- */
        @import url('https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600&display=swap');

        /* --- CSS variables for Theme Style --- */
        :root {
            --primary-blue: #1e3c72;
            --secondary-blue: #2a5298;
            --mint-green: #00b4db;
            --light-mint: #00d2ff;
            --bg-gradient: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            --text-dark: #333333;
            --text-muted: #666666;
            --border-color: #e0e0e0;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        /* --- Global Reset & Base --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Prompt', sans-serif;
        }

        body {
            background: #f4f7f6;
            color: var(--text-dark);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 40px 20px;
        }

        /* --- Card Container --- */
        .container {
            background: #ffffff;
            width: 100%;
            max-width: 900px;
            border-radius: 16px;
            box-shadow: var(--shadow);
            overflow: hidden;
            border-top: 8px solid var(--mint-green);
        }

        /* --- Header Section --- */
        .form-header {
            background: var(--bg-gradient);
            color: #ffffff;
            padding: 30px 40px;
            text-align: center;
        }

        .form-header h1 {
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 8px;
            letter-spacing: 0.5px;
        }

        .form-header p {
            font-size: 14px;
            color: rgba(255, 255, 255, 0.8);
            font-weight: 300;
        }

        /* --- Form Wrapper --- */
        form {
            padding: 40px;
        }

        /* --- Section Styling --- */
        fieldset {
            border: none;
            margin-bottom: 35px;
        }

        legend {
            font-size: 18px;
            font-weight: 500;
            color: var(--primary-blue);
            margin-bottom: 20px;
            padding-bottom: 5px;
            border-bottom: 2px solid #eef2f5;
            width: 100%;
            display: flex;
            align-items: center;
        }

        legend::before {
            content: "";
            display: inline-block;
            width: 8px;
            height: 18px;
            background: var(--mint-green);
            margin-right: 10px;
            border-radius: 4px;
        }

        /* --- Form Grid Layout (For Desktop) --- */
        .form-grid {
            display: grid;
            grid-template-columns: repeat(12, 1fr);
            gap: 20px;
        }

        .col-2  { grid-column: span 2; }
        .col-3  { grid-column: span 3; }
        .col-4  { grid-column: span 4; }
        .col-5  { grid-column: span 5; }
        .col-6  { grid-column: span 6; }
        .col-7  { grid-column: span 7; }
        .col-8  { grid-column: span 8; }
        .col-9  { grid-column: span 9; }
        .col-10 { grid-column: span 10; }
        .col-12 { grid-column: span 12; }

        /* --- Component Elements --- */
        .form-group {
            display: flex;
            flex-direction: column;
        }

        label {
            font-size: 14px;
            font-weight: 400;
            color: var(--text-dark);
            margin-bottom: 8px;
        }

        .required::after {
            content: " *";
            color: #ff4d4d;
        }

        /* --- Inputs Styling --- */
        input[type="text"],
        input[type="number"],
        input[type="email"],
        input[type="tel"],
        input[type="date"],
        input[type="url"],
        select,
        textarea {
            width: 100%;
            padding: 12px 16px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            font-size: 14px;
            color: var(--text-dark);
            background-color: #fafafa;
            transition: var(--transition);
            outline: none;
        }

        input:focus, select:focus, textarea:focus {
            border-color: var(--mint-green);
            background-color: #ffffff;
            box-shadow: 0 0 0 3px rgba(0, 180, 219, 0.15);
        }

        textarea {
            resize: vertical;
            min-height: 100px;
        }

        /* --- Color Picker Custom --- */
        input[type="color"] {
            -webkit-appearance: none;
            border: 1px solid var(--border-color);
            width: 100%;
            height: 45px;
            border-radius: 8px;
            cursor: pointer;
            background: none;
            padding: 2px;
        }
        
        input[type="color"]::-webkit-color-swatch-wrapper { padding: 0; }
        input[type="color"]::-webkit-color-swatch { border: none; border-radius: 6px; }

        /* --- File Upload Custom --- */
        input[type="file"] {
            padding: 8px;
            background: #fafafa;
            border: 1px dashed var(--border-color);
            border-radius: 8px;
            cursor: pointer;
        }

        /* --- Inline Choice Group (Radio & Checkbox) --- */
        .choice-group {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            padding-top: 8px;
        }

        .choice-item {
            display: flex;
            align-items: center;
            cursor: pointer;
        }

        .choice-item input {
            margin-right: 8px;
            accent-color: var(--secondary-blue);
            width: 16px;
            height: 16px;
        }

        /* --- Terms and Conditions --- */
        .terms-group {
            margin-top: 10px;
            padding: 15px;
            background: #f8fafb;
            border-radius: 8px;
            border-left: 4px solid var(--primary-blue);
        }

        /* --- Actions Button Container --- */
        .form-actions {
            display: flex;
            justify-content: flex-end;
            gap: 15px;
            margin-top: 40px;
            border-top: 2px solid #eef2f5;
            padding-top: 25px;
        }

        button {
            padding: 12px 30px;
            font-size: 15px;
            font-weight: 500;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
        }

        button[type="submit"] {
            background: var(--bg-gradient);
            color: #ffffff;
            box-shadow: 0 4px 15px rgba(30, 60, 114, 0.2);
        }

        button[type="submit"]:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(30, 60, 114, 0.3);
            opacity: 0.95;
        }

        button[type="reset"] {
            background: #eef2f5;
            color: var(--text-muted);
        }

        button[type="reset"]:hover {
            background: #e0e6ed;
            color: var(--text-dark);
        }

        /* --- Responsive Layout (Mobile Devices) --- */
        @media (max-width: 768px) {
            body { padding: 15px 10px; }
            form { padding: 20px; }
            .form-header { padding: 25px 20px; }
            
            /* ยุบทุกคอลัมน์ให้เต็มหน้าจอเมื่ออยู่บนมือถือ */
            .col-2, .col-3, .col-4, .col-5, .col-6, .col-7, .col-8, .col-9, .col-10, .col-12 {
                grid-column: span 12;
            }
            
            .form-actions {
                flex-direction: column-reverse;
            }
            button { width: 100%; }
        }
    </style>
</head>
<body>

<div class="container">
    <header class="form-header">
        <h1>ระบบลงทะเบียนประวัตินักเรียน</h1>
        <p>กรุณากรอกข้อมูลให้ครบถ้วนและถูกต้องตามความเป็นจริง</p>
    </header>

    <form action="#" method="POST" enctype="multipart/form-data">
        
        <!-- 1. ข้อมูลส่วนตัว -->
        <fieldset>
            <legend>ข้อมูลส่วนตัว</legend>
            <div class="form-grid">
                <div class="form-group col-3">
                    <label for="title" class="required">คำนำหน้า</label>
                    <select id="title" name="title" required>
                        <option value="" disabled selected>เลือกคำนำหน้า</option>
                        <option value="นาย">นาย</option>
                        <option value="นางสาว">นางสาว</option>
                        <option value="เด็กชาย">เด็กชาย</option>
                        <option value="เด็กหญิง">เด็กหญิง</option>
                    </select>
                </div>
                <div class="form-group col-6">
                    <label for="fullname" class="required">ชื่อ-นามสกุล</label>
                    <input type="text" id="fullname" name="fullname" placeholder="สมชาย ใจดี" required>
                </div>
                <div class="form-group col-3">
                    <label for="nickname">ชื่อเล่น</label>
                    <input type="text" id="nickname" name="nickname" placeholder="ต้น">
                </div>
                <div class="form-group col-4">
                    <label for="student_id" class="required">เลขประจำตัวนักเรียน</label>
                    <input type="text" id="student_id" name="student_id" placeholder="พิมพ์ 5 หลัก" pattern="[0-9]{5}" title="กรุณากรอกตัวเลข 5 หลัก" required>
                </div>
                <div class="form-group col-5">
                    <label for="birthdate" class="required">วันเดือนปีเกิด</label>
                    <input type="date" id="birthdate" name="birthdate" required>
                </div>
                <div class="form-group col-3">
                    <label for="age" class="required">อายุ (ปี)</label>
                    <input type="number" id="age" name="age" min="1" max="100" placeholder="ปี" required>
                </div>
            </div>
        </fieldset>

        <!-- 2. ข้อมูลการติดต่อ -->
        <fieldset>
            <legend>ข้อมูลการติดต่อ</legend>
            <div class="form-grid">
                <div class="form-group col-6">
                    <label for="email" class="required">อีเมล</label>
                    <input type="email" id="email" name="email" placeholder="example@school.ac.th" required>
                </div>
                <div class="form-group col-6">
                    <label for="telephone" class="required">เบอร์โทรศัพท์</label>
                    <input type="tel" id="telephone" name="telephone" placeholder="08XXXXXXXX" pattern="[0-9]{10}" title="กรุณากรอกเบอร์โทรศัพท์ 10 หลัก" required>
                </div>
                <div class="form-group col-12">
                    <label for="address" class="required">ที่อยู่ปัจจุบัน</label>
                    <textarea id="address" name="address" placeholder="บ้านเลขที่, ถนน, ตำบล, อำเภอ, จังหวัด..." required></textarea>
                </div>
            </div>
        </fieldset>

        <!-- 3. ข้อมูลส่วนบุคคล -->
        <fieldset>
            <legend>ข้อมูลส่วนบุคคล</legend>
            <div class="form-grid">
                <div class="form-group col-6">
                    <label class="required">เพศ</label>
                    <div class="choice-group">
                        <label class="choice-item"><input type="radio" name="gender" value="ชาย" required> ชาย</label>
                        <label class="choice-item"><input type="radio" name="gender" value="หญิง"> หญิง</label>
                        <label class="choice-item"><input type="radio" name="gender" value="อื่นๆ"> อื่นๆ/ไม่ระบุ</label>
                    </div>
                </div>
                <div class="form-group col-6">
                    <label for="blood_type" class="required">กรุ๊ปเลือด</label>
                    <select id="blood_type" name="blood_type" required>
                        <option value="" disabled selected>เลือกกรุ๊ปเลือด</option>
                        <option value="A">A</option>
                        <option value="B">B</option>
                        <option value="O">O</option>
                        <option value="AB">AB</option>
                    </select>
                </div>
                <div class="form-group col-6">
                    <label for="religion">ศาสนา</label>
                    <select id="religion" name="religion">
                        <option value="พุทธ" selected>พุทธ</option>
                        <option value="คริสต์">คริสต์</option>
                        <option value="อิสลาม">อิสลาม</option>
                        <option value="ฮินดู">ฮินดู</option>
                        <option value="อื่นๆ">อื่นๆ</option>
                    </select>
                </div>
                <div class="form-group col-6">
                    <label for="province" class="required">จังหวัดตามทะเบียนบ้าน</label>
                    <input type="text" id="province" name="province" placeholder="เช่น กรุงเทพมหานคร" required>
                </div>
            </div>
        </fieldset>

        <!-- 4. ความสนใจ -->
        <fieldset>
            <legend>ความสนใจ</legend>
            <div class="form-grid">
                <div class="form-group col-12">
                    <label>งานอดิเรก (เลือกได้มากกว่า 1 ข้อ)</label>
                    <div class="choice-group">
                        <label class="choice-item"><input type="checkbox" name="hobbies" value="อ่านหนังสือ"> อ่านหนังสือ</label>
                        <label class="choice-item"><input type="checkbox" name="hobbies" value="เล่นกีฬา"> เล่นกีฬา</label>
                        <label class="choice-item"><input type="checkbox" name="hobbies" value="ฟังเพลง/เล่นดนตรี"> ฟังเพลง/เล่นดนตรี</label>
                        <label class="choice-item"><input type="checkbox" name="hobbies" value="วาดภาพ/ศิลปะ"> วาดภาพ/ศิลปะ</label>
                        <label class="choice-item"><input type="checkbox" name="hobbies" value="เล่นเกม"> เล่นเกม</label>
                    </div>
                </div>
                <div class="form-group col-4">
                    <label for="favorite_color">สีที่ชอบ</label>
                    <input type="color" id="favorite_color" name="favorite_color" value="#00b4db">
                </div>
                <div class="form-group col-8">
                    <label for="favorite_url">เว็บไซต์ที่เข้าชมบ่อย (URL)</label>
                    <input type="url" id="favorite_url" name="favorite_url" placeholder="https://example.com">
                </div>
            </div>
        </fieldset>

        <!-- 5. ข้อมูลการศึกษา -->
        <fieldset>
            <legend>ข้อมูลการศึกษา</legend>
            <div class="form-grid">
                <div class="form-group col-3">
                    <label for="education_level" class="required">ระดับชั้น</label>
                    <select id="education_level" name="education_level" required>
                        <option value="" disabled selected>เลือกชั้นปี</option>
                        <option value="ม.1">มัธยมศึกษาปีที่ 1</option>
                        <option value="ม.2">มัธยมศึกษาปีที่ 2</option>
                        <option value="ม.3">มัธยมศึกษาปีที่ 3</option>
                        <option value="ม.4">มัธยมศึกษาปีที่ 4</option>
                        <option value="ม.5">มัธยมศึกษาปีที่ 5</option>
                        <option value="ม.6">มัธยมศึกษาปีที่ 6</option>
                    </select>
                </div>
                <div class="form-group col-3">
                    <label for="classroom" class="required">ห้องเรียน</label>
                    <input type="number" id="classroom" name="classroom" min="1" max="15" placeholder="เช่น 1" required>
                </div>
                <div class="form-group col-4">
                    <label for="program" class="required">แผนการเรียน</label>
                    <select id="program" name="program" required>
                        <option value="" disabled selected>เลือกแผนการเรียน</option>
                        <option value="วิทยาศาสตร์-คณิตศาสตร์">วิทยาศาสตร์-คณิตศาสตร์</option>
                        <option value="ศิลป์-คำนวณ">ศิลป์-คำนวณ</option>
                        <option value="ศิลป์-ภาษา">ศิลป์-ภาษา</option>
                        <option value="ทั่วไป">ทั่วไป / อื่นๆ</option>
                    </select>
                </div>
                <div class="form-group col-2">
                    <label for="gpa" class="required">เกรดเฉลี่ย (GPAX)</label>
                    <input type="number" id="gpa" name="gpa" min="0.00" max="4.00" step="0.01" placeholder="4.00" required>
                </div>
            </div>
        </fieldset>

        <!-- 6. การอัปโหลดไฟล์ -->
        <fieldset>
            <legend>การอัปโหลดไฟล์เอกสาร</legend>
            <div class="form-grid">
                <div class="form-group col-6">
                    <label for="avatar_image" class="required">รูปภาพประจำตัวนักเรียน</label>
                    <input type="file" id="avatar_image" name="avatar_image" accept="image/*" required>
                </div>
                <div class="form-group col-6">
                    <label for="document_file">เอกสารเพิ่มเติม (PDF/Image)</label>
                    <input type="file" id="document_file" name="document_file" accept=".pdf,image/*">
                </div>
            </div>
        </fieldset>

        <!-- 7. ความคิดเห็นเพิ่มเติม -->
        <fieldset>
            <legend>ข้อเสนอแนะ</legend>
            <div class="form-grid">
                <div class="form-group col-12">
                    <label for="comments">ความคิดเห็นเพิ่มเติม</label>
                    <textarea id="comments" name="comments" placeholder="ระบุสิ่งที่ต้องการแจ้งให้ทางโรงเรียนทราบเพิ่มเติม..."></textarea>
                </div>
            </div>
        </fieldset>

        <!-- 8. ยืนยันข้อมูล -->
        <div class="choice-group terms-group">
            <label class="choice-item">
                <input type="checkbox" name="agree_terms" id="agree_terms" required>
                <span>ข้าพเจ้ายินยอมและยืนยันว่าข้อมูลข้างต้นทั้งหมดเป็นความจริงทุกประการ</span>
            </label>
        </div>

        <!-- Buttons -->
        <div class="form-actions">
            <button type="reset">ล้างข้อมูล</button>
            <button type="submit">ส่งข้อมูลประวัติ</button>
        </div>

    </form>
</div>

</body>
</html>

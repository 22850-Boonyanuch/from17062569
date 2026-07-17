
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>แบบฟอร์มเก็บข้อมูลนักเรียน</title>
    <style>
        /* --- นำเข้าฟอนต์ Prompt เพื่อความทันสมัยอ่านง่าย --- */
        @import url('https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600&display=swap');

        /* --- กำหนดตัวแปรระบบสี โทนฟ้า-ขาว --- */
        :root {
            --sky-blue-deep: #0076a3;
            --sky-blue-main: #009ee3;
            --sky-blue-light: #e6f6ff;
            --pure-white: #ffffff;
            --soft-white: #f8fafc;
            --text-dark: #2c3e50;
            --text-muted: #7f8c8d;
            --border-color: #d1d5db;
            --shadow-soft: 0 10px 25px rgba(0, 118, 163, 0.08);
            --transition-speed: 0.25s;
        }

        /* --- Global Reset & Base --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Prompt', sans-serif;
        }

        body {
            background-color: #f0f4f8;
            color: var(--text-dark);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 50px 20px;
        }

        /* --- กล่องครอบฟอร์มกึ่งกลางหน้าจอ --- */
        .form-container {
            background-color: var(--pure-white);
            width: 100%;
            max-width: 950px;
            border-radius: 20px;
            box-shadow: var(--shadow-soft);
            overflow: hidden;
            border: 1px solid rgba(0, 158, 227, 0.1);
        }

        /* --- ส่วนหัวของฟอร์ม (Header) --- */
        .form-header {
            background: linear-gradient(135deg, var(--sky-blue-deep) 0%, var(--sky-blue-main) 100%);
            color: var(--pure-white);
            padding: 35px 40px;
            text-align: center;
            position: relative;
        }

        .form-header h1 {
            font-size: 26px;
            font-weight: 600;
            margin-bottom: 8px;
        }

        .form-header p {
            font-size: 14px;
            color: rgba(255, 255, 255, 0.85);
            font-weight: 300;
        }

        /* --- สไตล์ของตัวฟอร์ม --- */
        form {
            padding: 40px;
        }

        /* --- การแบ่งสัดส่วนแต่ละหัวข้อ (Fieldset) --- */
        fieldset {
            border: none;
            margin-bottom: 35px;
        }

        legend {
            font-size: 18px;
            font-weight: 600;
            color: var(--sky-blue-deep);
            margin-bottom: 20px;
            padding-bottom: 8px;
            border-bottom: 2px solid var(--sky-blue-light);
            width: 100%;
            display: flex;
            align-items: center;
        }

        legend::before {
            content: "";
            display: inline-block;
            width: 6px;
            height: 18px;
            background-color: var(--sky-blue-main);
            margin-right: 12px;
            border-radius: 3px;
        }

        /* --- ระบบ Grid Layout สำหรับจัดระเบียบบนคอมพิวเตอร์ --- */
        .form-row {
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

        /* --- การจัดกลุ่มอินพุต --- */
        .form-group {
            display: flex;
            flex-direction: column;
        }

        label {
            font-size: 14.5px;
            font-weight: 500;
            margin-bottom: 8px;
            color: var(--text-dark);
        }

        .required::after {
            content: " *";
            color: #e74c3c;
            font-weight: bold;
        }

        /* --- ตกแต่ง Input Fields ทุกประเภท --- */
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
            background-color: var(--soft-white);
            transition: all var(--transition-speed) ease;
            outline: none;
        }

        /* เอฟเฟกต์ตอนคลิกเลือกช่องกรอกข้อมูล */
        input:focus, select:focus, textarea:focus {
            border-color: var(--sky-blue-main);
            background-color: var(--pure-white);
            box-shadow: 0 0 0 4px rgba(0, 158, 227, 0.12);
        }

        textarea {
            resize: vertical;
            min-height: 110px;
        }

        /* --- Color Picker สไตล์มินิมอล --- */
        input[type="color"] {
            -webkit-appearance: none;
            border: 1px solid var(--border-color);
            width: 100%;
            height: 48px;
            border-radius: 8px;
            cursor: pointer;
            background: none;
            padding: 3px;
        }
        input[type="color"]::-webkit-color-swatch-wrapper { padding: 0; }
        input[type="color"]::-webkit-color-swatch { border: none; border-radius: 6px; }

        /* --- File Upload ช่องอัปโหลดไฟล์แบบโมเดิร์น --- */
        input[type="file"] {
            padding: 9px;
            background-color: var(--soft-white);
            border: 1px dashed var(--border-color);
            border-radius: 8px;
            cursor: pointer;
        }
        input[type="file"]:hover {
            border-color: var(--sky-blue-main);
            background-color: var(--sky-blue-light);
        }

        /* --- การจัดกลุ่มตัวเลือก (Radio & Checkbox) --- */
        .options-flex {
            display: flex;
            flex-wrap: wrap;
            gap: 22px;
            padding-top: 8px;
        }

        .option-item {
            display: flex;
            align-items: center;
            cursor: pointer;
            font-size: 14.5px;
        }

        .option-item input {
            margin-right: 8px;
            accent-color: var(--sky-blue-deep);
            width: 17px;
            height: 17px;
            cursor: pointer;
        }

        /* --- ส่วนกติกาและเงื่อนไข --- */
        .agreement-box {
            background-color: var(--soft-white);
            border: 1px solid #e2e8f0;
            border-left: 5px solid var(--sky-blue-main);
            padding: 18px;
            border-radius: 8px;
            margin-top: 15px;
        }

        /* --- ส่วนปุ่มจัดการฟอร์ม --- */
        .form-buttons {
            display: flex;
            justify-content: flex-end;
            gap: 16px;
            margin-top: 40px;
            border-top: 1px solid #edf2f7;
            padding-top: 25px;
        }

        button {
            padding: 13px 32px;
            font-size: 15.5px;
            font-weight: 500;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: all var(--transition-speed) ease;
        }

        button[type="submit"] {
            background-color: var(--sky-blue-main);
            color: var(--pure-white);
            box-shadow: 0 4px 12px rgba(0, 158, 227, 0.2);
        }

        button[type="submit"]:hover {
            background-color: var(--sky-blue-deep);
            transform: translateY(-1px);
            box-shadow: 0 6px 16px rgba(0, 118, 163, 0.3);
        }

        button[type="reset"] {
            background-color: #edf2f7;
            color: var(--text-muted);
        }

        button[type="reset"]:hover {
            background-color: #e2e8f0;
            color: var(--text-dark);
        }

        /* --- Responsive Design (รองรับการแสดงผลบนสมาร์ตโฟน) --- */
        @media (max-width: 768px) {
            body { padding: 15px 10px; }
            form { padding: 25px 20px; }
            .form-header { padding: 25px 20px; }
            
            /* ยุบทุกคอลัมน์จาก Grid ให้แผ่เต็ม 100% เมื่อเปิดบนมือถือ */
            .col-2, .col-3, .col-4, .col-5, .col-6, .col-7, .col-8, .col-9, .col-10, .col-12 {
                grid-column: span 12;
            }
            
            .form-buttons {
                flex-direction: column-reverse; /* สลับให้ปุ่มส่งอยู่ด้านบนปุ่มล้างข้อมูลเมื่อเป็นแนวตั้ง */
                gap: 12px;
            }
            button { width: 100%; }
        }
    </style>
</head>
<body>

<div class="form-container">
    <header class="form-header">
        <h1>ระบบบันทึกข้อมูลและประวัตินักเรียน</h1>
        <p>กรุณากรอกข้อมูลส่วนบุคคลและการศึกษาให้ครบถ้วนเพื่อประโยชน์ทางการศึกษา</p>
    </header>

    <form action="#" method="POST" enctype="multipart/form-data">
        
        <!-- 1. ข้อมูลส่วนตัว -->
        <fieldset>
            <legend>ข้อมูลส่วนตัว</legend>
            <div class="form-row">
                <div class="form-group col-3">
                    <label for="prefix" class="required">คำนำหน้า</label>
                    <select id="prefix" name="prefix" required>
                        <option value="" disabled selected>เลือก...</option>
                        <option value="นาย">นาย</option>
                        <option value="นางสาว">นางสาว</option>
                        <option value="เด็กชาย">เด็กชาย</option>
                        <option value="เด็กหญิง">เด็กหญิง</option>
                    </select>
                </div>
                <div class="form-group col-6">
                    <label for="fullname" class="required">ชื่อ-นามสกุล</label>
                    <input type="text" id="fullname" name="fullname" placeholder="ภาษาไทย เช่น สมศักดิ์ รักดี" required>
                </div>
                <div class="form-group col-3">
                    <label for="nickname">ชื่อเล่น</label>
                    <input type="text" id="nickname" name="nickname" placeholder="เช่น บอส">
                </div>
                <div class="form-group col-4">
                    <label for="student_code" class="required">เลขประจำตัวนักเรียน</label>
                    <input type="text" id="student_code" name="student_code" placeholder="รหัสตัวเลข 5 หลัก" pattern="[0-9]{5}" title="กรุณากรอกรหัสประจำตัวเป็นตัวเลข 5 หลัก" required>
                </div>
                <div class="form-group col-5">
                    <label for="birthday" class="required">วันเดือนปีเกิด</label>
                    <input type="date" id="birthday" name="birthday" required>
                </div>
                <div class="form-group col-3">
                    <label for="age" class="required">อายุ</label>
                    <input type="number" id="age" name="age" min="1" max="99" placeholder="ปี" required>
                </div>
            </div>
        </fieldset>

        <!-- 2. ข้อมูลการติดต่อ -->
        <fieldset>
            <legend>ข้อมูลการติดต่อ</legend>
            <div class="form-row">
                <div class="form-group col-6">
                    <label for="email" class="required">อีเมล</label>
                    <input type="email" id="email" name="email" placeholder="student@example.com" required>
                </div>
                <div class="form-group col-6">
                    <label for="tel" class="required">เบอร์โทรศัพท์</label>
                    <input type="tel" id="tel" name="tel" placeholder="08XXXXXXXX" pattern="[0-9]{10}" title="กรุณากรอกเบอร์โทรศัพท์เป็นตัวเลข 10 หลัก" required>
                </div>
                <div class="form-group col-12">
                    <label for="address" class="required">ที่อยู่ตามทะเบียนบ้าน</label>
                    <textarea id="address" name="address" placeholder="บ้านเลขที่ หมู่ ซอย ถนน ตำบล อำเภอ..." required></textarea>
                </div>
            </div>
        </fieldset>

        <!-- 3. ข้อมูลส่วนบุคคล -->
        <fieldset>
            <legend>ข้อมูลส่วนบุคคล</legend>
            <div class="form-row">
                <div class="form-group col-6">
                    <label class="required">เพศ</label>
                    <div class="options-flex">
                        <label class="option-item"><input type="radio" name="gender" value="ชาย" required> ชาย</label>
                        <label class="option-item"><input type="radio" name="gender" value="หญิง"> หญิง</label>
                        <label class="option-item"><input type="radio" name="gender" value="ไม่ระบุ"> ไม่ระบุ</label>
                    </div>
                </div>
                <div class="form-group col-6">
                    <label for="blood" class="required">กรุ๊ปเลือด</label>
                    <select id="blood" name="blood" required>
                        <option value="" disabled selected>เลือกหมู่เลือด</option>
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
                        <option value="พราหมณ์-ฮินดู">พราหมณ์-ฮินดู</option>
                        <option value="อื่นๆ">อื่นๆ</option>
                    </select>
                </div>
                <div class="form-group col-6">
                    <label for="province" class="required">จังหวัด</label>
                    <input type="text" id="province" name="province" placeholder="ระบุจังหวัด" required>
                </div>
            </div>
        </fieldset>

        <!-- 4. ความสนใจ -->
        <fieldset>
            <legend>ความสนใจ</legend>
            <div class="form-row">
                <div class="form-group col-12">
                    <label>งานอดิเรก (เลือกได้มากกว่า 1 ข้อ)</label>
                    <div class="options-flex">
                        <label class="option-item"><input type="checkbox" name="hobbies" value="เล่นกีฬา/ออกกำลังกาย"> เล่นกีฬา/ออกกำลังกาย</label>
                        <label class="option-item"><input type="checkbox" name="hobbies" value="อ่านหนังสือ/การ์ตูน"> อ่านหนังสือ/การ์ตูน</label>
                        <label class="option-item"><input type="checkbox" name="hobbies" value="ฟังเพลง/เล่นดนตรี"> ฟังเพลง/เล่นดนตรี</label>
                        <label class="option-item"><input type="checkbox" name="hobbies" value="เล่นเกม/อีสปอร์ต"> เล่นเกม/อีสปอร์ต</label>
                        <label class="option-item"><input type="checkbox" name="hobbies" value="ถ่ายภาพ/ทำคอนเทนต์"> ถ่ายภาพ/ทำคอนเทนต์</label>
                    </div>
                </div>
                <div class="form-group col-4">
                    <label for="fav_color">สีที่ชอบ</label>
                    <input type="color" id="fav_color" name="fav_color" value="#009ee3">
                </div>
                <div class="form-group col-8">
                    <label for="fav_url">เว็บไซต์ที่ชอบ (URL)</label>
                    <input type="url" id="fav_url" name="fav_url" placeholder="https://www.google.com">
                </div>
            </div>
        </fieldset>

        <!-- 5. ข้อมูลการศึกษา -->
        <fieldset>
            <legend>ข้อมูลการศึกษา</legend>
            <div class="form-row">
                <div class="form-group col-4">
                    <label for="class_level" class="required">ระดับชั้น</label>
                    <select id="class_level" name="class_level" required>
                        <option value="" disabled selected>เลือกระดับชั้น</option>
                        <option value="ม.1">มัธยมศึกษาปีที่ 1</option>
                        <option value="ม.2">มัธยมศึกษาปีที่ 2</option>
                        <option value="ม.3">มัธยมศึกษาปีที่ 3</option>
                        <option value="ม.4">มัธยมศึกษาปีที่ 4</option>
                        <option value="ม.5">มัธยมศึกษาปีที่ 5</option>
                        <option value="ม.6">มัธยมศึกษาปีที่ 6</option>
                    </select>
                </div>
                <div class="form-group col-2">
                    <label for="room" class="required">ห้องเรียน</label>
                    <input type="number" id="room" name="room" min="1" max="20" placeholder="เช่น 1" required>
                </div>
                <div class="form-group col-4">
                    <label for="study_plan" class="required">แผนการเรียน</label>
                    <select id="study_plan" name="study_plan" required>
                        <option value="" disabled selected>เลือกแผนการเรียน</option>
                        <option value="วิทย์-คณิต">วิทยาศาสตร์ - คณิตศาสตร์</option>
                        <option value="ศิลป์-คำนวณ">ศิลป์ - คำนวณ</option>
                        <option value="ศิลป์-ภาษา">ศิลป์ - ภาษา</option>
                        <option value="ทั่วไป">ทั่วไป / อื่นๆ</option>
                    </select>
                </div>
                <div class="form-group col-2">
                    <label for="gpax" class="required">เกรดเฉลี่ย</label>
                    <input type="number" id="gpax" name="gpax" min="0.00" max="4.00" step="0.01" placeholder="4.00" required>
                </div>
            </div>
        </fieldset>

        <!-- 6. การอัปโหลดไฟล์ -->
        <fieldset>
            <legend>การอัปโหลดไฟล์</legend>
            <div class="form-row">
                <div class="form-group col-6">
                    <label for="avatar" class="required">รูปภาพประจำตัว</label>
                    <input type="file" id="avatar" name="avatar" accept="image/*" required>
                </div>
                <div class="form-group col-6">
                    <label for="extra_doc">เอกสารเพิ่มเติม (PDF/รูปภาพ)</label>
                    <input type="file" id="extra_doc" name="extra_doc" accept=".pdf, image/*">
                </div>
            </div>
        </fieldset>

        <!-- 7. ความคิดเห็นเพิ่มเติม -->
        <fieldset>
            <legend>ความคิดเห็นเพิ่มเติม</legend>
            <div class="form-row">
                <div class="form-group col-12">
                    <label for="more_info">แสดงความคิดเห็นหรือข้อมูลเพิ่มเติม</label>
                    <textarea id="more_info" name="more_info" placeholder="พิมพ์ข้อความเพิ่มเติมที่นี่..."></textarea>
                </div>
            </div>
        </fieldset>

        <!-- 8. ยืนยันข้อมูล -->
        <div class="agreement-box">
            <label class="option-item">
                <input type="checkbox" name="accept_rules" id="accept_rules" required>
                <span>ข้าพเจ้ายอมรับเงื่อนไขการใช้งาน และยืนยันว่าข้อมูลที่กรอกทั้งหมดเป็นความจริง</span>
            </label>
        </div>

        <!-- ส่วนของปุ่มกด -->
        <div class="form-buttons">
            <button type="reset">ล้างข้อมูล</button>
            <button type="submit">ส่งข้อมูล</button>
        </div>

    </form>
</div>

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Table Status - RMUTT Modern Design</title>
  <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Kanit', sans-serif;
      margin: 0;
      padding: 0;
      background: linear-gradient(145deg, #e0ecf8, #d1dfe8);
      color: #333;
      transition: background 0.5s ease;
    }

    header {
      background-color: #002060;
      color: white;
      padding: 20px 10px;
      text-align: center;
      position: relative;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }

    header img {
      position: absolute;
      top: 50%;
      left: 20px;
      transform: translateY(-50%);
      height: 180px;
    }

    header h1 {
      margin: 0;
      font-size: 3.5rem;
      font-weight: 600;
      text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.3);
    }

    header h2 {
      margin: 5px 0 0;
      font-size: 1.8rem;
      font-weight: 400;
    }

    .grid-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
      grid-gap: 20px;
      margin: 40px auto;
      padding: 20px;
      max-width: 1200px;
      justify-items: center;
    }

    .table {
      width: 140px;
      height: 140px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 20px;
      font-size: 1.5rem;
      font-weight: bold;
      color: white;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      cursor: pointer;
      transition: transform 0.3s, box-shadow 0.4s ease, opacity 0.3s;
      position: relative;
      background-color: #f5f5f5; /* สีพื้นหลังที่ใช้เมื่อไม่มีข้อมูล */
    }

    .table:hover {
      transform: scale(1.15);
      opacity: 0.9;
      box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
    }

    .occupied {
      background: linear-gradient(135deg, #d32f2f, #b71c1c);
    }

    .empty {
      background: linear-gradient(135deg, #388e3c, #1b5e20);
    }

    .cleaning {
      background: linear-gradient(135deg, #fbc02d, #f57f17);
      color: black;
    }

    .status-icon {
      position: absolute;
      top: 10px;
      right: 10px;
      font-size: 1.5rem;
      background: rgba(255, 255, 255, 0.7);
      border-radius: 50%;
      padding: 5px;
    }

    .summary {
      text-align: center;
      margin-top: 40px;
      font-size: 1.6rem;
      color: #333;
    }

    .summary p {
      margin: 10px 0;
    }

    footer {
      background-color: #002060;
      color: white;
      text-align: center;
      padding: 15px 0;
      position: fixed;
      bottom: 0;
      width: 100%;
      box-shadow: 0 -2px 6px rgba(0, 0, 0, 0.2);
    }

    footer p {
      margin: 0;
      font-size: 1.2rem;
    }

    .table-update {
      animation: tableStatusChange 1s ease-in-out;
    }

    @keyframes tableStatusChange {
      0% { opacity: 0.5; }
      100% { opacity: 1; }
    }

    .no-connection {
      color: #f44336; /* สีแดงสำหรับการแจ้งเตือนการเชื่อมต่อ */
      font-size: 1.2rem;
      margin-top: 20px;
      text-align: center;
    }
  </style>
</head>
<body>
  <header>
    <img src="https://www.rmutt.ac.th/wp-content/uploads/2021/02/20210202-logoRMUTT-color-01.png" alt="RMUTT Logo">
    <h1>Table Status</h1>
    <h2>ระบบตรวจสอบสถานะโต๊ะ (RMUTT Modern Design)</h2>
  </header>

  <div id="tableContainer" class="grid-container"></div>

  <div class="summary">
    <h3>สรุปสถานะ:</h3>
    <p>โต๊ะว่าง: <span id="availableCount">0</span></p>
    <p>โต๊ะไม่ว่าง: <span id="occupiedCount">0</span></p>
  </div>

  <div id="noConnection" class="no-connection" style="display: none;">
    ไม่สามารถเชื่อมต่อกับข้อมูลได้
  </div>

  <footer>
    <p>&copy; 2024 RMUTT | ระบบตรวจสอบสถานะโต๊ะ</p>
  </footer>

  <script>
    // รับข้อมูลสถานะโต๊ะจากแหล่งข้อมูลจริง (เช่น API หรือฐานข้อมูล)
    const tableData = {
      1: "occupied",
      2: "empty",
      3: "occupied",
      4: "empty",
      5: "cleaning",
      6: "empty",
      7: "occupied",
      8: "empty",
      9: "cleaning",
      10: "empty"
    };

    // อัปเดตการแสดงผลสถานะโต๊ะ
    function renderTables() {
      const container = document.getElementById("tableContainer");
      container.innerHTML = ""; // ล้างข้อมูลเก่า

      let availableCount = 0;
      let occupiedCount = 0;

      // สร้างบล็อกโต๊ะตามสถานะ
      Object.keys(tableData).forEach((tableId) => {
        const status = tableData[tableId];
        const div = document.createElement("div");
        div.className = `table ${status} table-update`; // เพิ่มสถานะ
        div.textContent = `โต๊ะ ${tableId}`;

        // เพิ่มไอคอนสถานะ
        const icon = document.createElement("div");
        icon.className = "status-icon";
        icon.textContent = status === "empty" ? "✔️" : status === "occupied" ? "❌" : "🧹";
        div.appendChild(icon);

        container.appendChild(div);

        // นับจำนวนโต๊ะแต่ละสถานะ
        if (status === "empty") availableCount++;
        if (status === "occupied") occupiedCount++;
      });

      // แสดงผลสรุปสถานะ
      document.getElementById("availableCount").textContent = availableCount;
      document.getElementById("occupiedCount").textContent = occupiedCount;

      // แสดงข้อความเมื่อไม่มีการเชื่อมต่อ
      document.getElementById("noConnection").style.display = 'none'; // ปิดข้อความนี้ถ้ามีการเชื่อมต่อ
    }

    // เช็คสถานะการเชื่อมต่อกับเซิร์ฟเวอร์ (ตัวอย่างการเชื่อมต่อ API)
    function checkConnection() {
      const isConnected = true;  // เปลี่ยนให้เป็นการเช็คสถานะเชื่อมต่อจริง
      if (!isConnected) {
        document.getElementById("noConnection").style.display = 'block'; // แสดงข้อความถ้าไม่มีการเชื่อมต่อ
        renderTables(); // แสดงสถานะโต๊ะเป็นสีขาวหากไม่มีการเชื่อมต่อ
      } else {
        renderTables(); // อัปเดตสถานะโต๊ะหากเชื่อมต่อ
      }
    }

    // เรียกฟังก์ชันเช็คการเชื่อมต่อ
    checkConnection();
  </script>
</body>
</html>

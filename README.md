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
      background: linear-gradient(145deg, #f0f4f8, #cfd8dc); /* พื้นหลังแบบกราเดีย้น */
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
      top: 10px;
      left: 20px;
      height: 50px;
    }

    header h1 {
      margin: 0;
      font-size: 2.5rem;
      font-weight: 600;
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
    }

    header h2 {
      margin: 5px 0 0;
      font-size: 1.2rem;
      font-weight: 300;
    }

    .grid-container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      grid-gap: 20px;
      margin: 40px auto;
      padding: 20px;
      max-width: 1000px;
      justify-items: center;
    }

    .table {
      width: 120px;
      height: 120px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 15px;
      font-size: 1.3rem;
      font-weight: bold;
      color: white;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      cursor: pointer;
      transition: transform 0.2s, box-shadow 0.3s ease, opacity 0.3s;
    }

    .table:hover {
      transform: scale(1.1);
      opacity: 0.9;
      box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
    }

    .occupied {
      background: #d32f2f; /* สีแดง */
      background: linear-gradient(135deg, #d32f2f, #b71c1c);
    }

    .empty {
      background: #388e3c; /* สีเขียว */
      background: linear-gradient(135deg, #388e3c, #1b5e20);
    }

    .cleaning {
      background: #fbc02d; /* สีเหลือง */
      background: linear-gradient(135deg, #fbc02d, #f57f17);
      color: black;
    }

    .summary {
      text-align: center;
      margin-top: 40px;
      font-size: 1.4rem;
      color: #333;
    }

    .summary p {
      margin: 5px 0;
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
      font-size: 1rem;
    }

    /* เพิ่มแอนิเมชั่นการเปลี่ยนสถานะ */
    .table-update {
      animation: tableStatusChange 1s ease-in-out;
    }

    @keyframes tableStatusChange {
      0% { opacity: 0.5; }
      100% { opacity: 1; }
    }
  </style>
</head>
<body>
  <header>
    <img src="https://upload.wikimedia.org/wikipedia/en/thumb/c/cf/Rajamangala_University_of_Technology_Thanyaburi_Logo.svg/1200px-Rajamangala_University_of_Technology_Thanyaburi_Logo.svg.png" alt="RMUTT Logo">
    <h1>Table Status</h1>
    <h2>ระบบตรวจสอบสถานะโต๊ะ (RMUTT Modern Design)</h2>
  </header>

  <div id="tableContainer" class="grid-container"></div>

  <div class="summary">
    <h3>สรุปสถานะ:</h3>
    <p>โต๊ะว่าง: <span id="availableCount">0</span></p>
    <p>โต๊ะไม่ว่าง: <span id="occupiedCount">0</span></p>
  </div>

  <footer>
    <p>&copy; 2024 RMUTT | ระบบตรวจสอบสถานะโต๊ะ</p>
  </footer>

  <script>
    // จำลองข้อมูลสถานะโต๊ะ
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
        div.className = `table ${status} table-update`;
        div.textContent = `โต๊ะ ${tableId}`;
        container.appendChild(div);

        // นับจำนวนโต๊ะแต่ละสถานะ
        if (status === "empty") availableCount++;
        if (status === "occupied") occupiedCount++;
      });

      // แสดงผลสรุปสถานะ
      document.getElementById("availableCount").textContent = availableCount;
      document.getElementById("occupiedCount").textContent = occupiedCount;
    }

    // เรียกฟังก์ชันเพื่อแสดงผล
    renderTables();

    // จำลองการอัปเดตข้อมูลจากเซิร์ฟเวอร์ทุก 5 วินาที
    setInterval(() => {
      // จำลองการเปลี่ยนสถานะ
      tableData[2] = tableData[2] === "empty" ? "occupied" : "empty";
      tableData[4] = tableData[4] === "empty" ? "occupied" : "empty";

      renderTables();
    }, 5000);
  </script>
</body>
</html>

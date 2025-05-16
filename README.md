<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>صورتجلسه شرکت بهین تهیه غذای برکت</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link href="https://fonts.googleapis.com/css2?family=Vazirmatn :wght@400&display=swap" rel="stylesheet">

  <!-- Manifest PWA -->
  <link rel="manifest" href="manifest.json">
  <meta name="theme-color" content="#8BC34A" />

  <style>
    :root {
      --primary-color: #8BC34A;
      --font-family: 'Vazirmatn', sans-serif;
      --background-color: #fff0f0;
      --text-color: #2d004d;
      --border-radius: 12px;
      --font-size: 14px;

      /* Dark Mode */
      --dark-bg: #1a1a1a;
      --dark-text: #eee;
    }

    body {
      font-family: var(--font-family);
      font-size: var(--font-size);
      background: var(--background-color);
      color: var(--text-color);
      margin: 0;
      padding: 20px;
      transition: all 0.3s ease;
    }

    .dark-mode {
      background: var(--dark-bg);
      color: var(--dark-text);
    }

    .container {
      max-width: 850px;
      margin: auto;
      background: white;
      border-radius: var(--border-radius);
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      padding: 30px;
      border: 4px double var(--primary-color);
    }

    .logo-section {
      text-align: center;
      margin-bottom: 10px;
    }

    .logo-section img {
      max-width: 150px;
      height: auto;
    }

    .header-section {
      text-align: center;
      margin-bottom: 15px;
      font-weight: bold;
    }

    .info-row {
      display: flex;
      gap: 10px;
      margin-bottom: 15px;
      border: 2px solid var(--primary-color);
      border-radius: var(--border-radius);
      padding: 10px;
      background-color: #f0f8e0;
      flex-wrap: wrap;
    }

    .info-row input,
    .info-row select {
      flex: 1;
      padding: 8px;
      border: 2px solid var(--primary-color);
      border-radius: var(--border-radius);
      box-sizing: border-box;
      text-align: center;
    }

    .topic-section {
      width: calc(100% - 20px);
      margin-right: 10px;
      padding: 5px;
      border: 2px solid var(--primary-color);
      border-radius: var(--border-radius);
      margin-bottom: 15px;
      text-align: center;
      resize: none;
      background-color: #f0f8e0;
      font-size: 13px;
    }

    .attendees-section {
      display: flex;
      gap: 10px;
      margin-bottom: 15px;
    }

    .attendees-list {
      flex: 1;
      border: 2px solid var(--primary-color);
      border-radius: var(--border-radius);
    }

    .attendees-input,
    .primary-btn {
      flex: 2;
      padding: 8px;
      border: 2px solid var(--primary-color);
      border-radius: var(--border-radius);
    }

    .entry-row {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-bottom: 15px;
    }

    textarea.autoresize {
      overflow: hidden;
      min-height: 46px;
      max-height: 150px;
    }

    .entry-details {
      display: flex;
      gap: 10px;
    }

    .entry-details input {
      flex: 1;
      padding: 8px;
      border: 2px solid var(--primary-color);
      border-radius: var(--border-radius);
    }

    .action-buttons {
      display: flex;
      gap: 10px;
      justify-content: center;
      margin-top: 20px;
      flex-wrap: wrap;
    }

    .primary-btn {
      background: var(--primary-color);
      color: white;
      border-radius: var(--border-radius);
      cursor: pointer;
      padding: 10px 16px;
      font-weight: bold;
      text-decoration: none;
      text-align: center;
    }

    #previewContent {
      display: none;
      margin-top: 30px;
      padding: 20px;
      background: white;
      border: 2px dashed #8bc34a;
      border-radius: 12px;
    }

    @media print {
      .primary-btn, .attendees-input, #attendeesList, .remove-btn, .action-buttons {
        display: none !important;
      }
      select {
        display: none !important;
      }
      .print-only {
        display: block;
      }
      .info-print {
        border: 2px solid var(--primary-color);
        border-radius: var(--border-radius);
        padding: 8px;
        margin: 0;
        text-align: center;
        background-color: #f0f8e0;
        flex: 1;
        font-size: 13px;
      }
    }
  </style>
</head>
<body>
  <div class="container" id="contentToPrint">
    <div class="logo-section">
      <img src="https://i.imgur.com/gX2NTo6.png " alt="لوگوی شرکت برکت">
    </div>

    <div class="header-section">
      <h2>صورتجلسه شرکت بهین تهیه غذای برکت</h2>
    </div>

    <form id="meetingForm">
      <div class="info-row">
        <div style="display: flex; align-items: center; gap: 5px; flex: 1;">
          <input type="text" id="meetingDate" placeholder="📅 تاریخ جلسه">
          <button type="button" onclick="resetDate()" title="بازنشانی تاریخ" style="background: none; border: none; cursor: pointer;">🔄</button>
        </div>
        <div style="display: flex; align-items: center; gap: 5px; flex: 1;">
          <input type="text" id="meetingTime" placeholder="⏰ ساعت جلسه">
          <button type="button" onclick="resetTime()" title="بازنشانی ساعت" style="background: none; border: none; cursor: pointer;">🔄</button>
        </div>
        <input type="text" id="meetingNumber" placeholder="🔢 شماره جلسه" required>
        <select id="meetingLocation">
          <option value="">📍 مکان جلسه</option>
          <option value="دفتر باغ فیض">دفتر باغ فیض</option>
          <option value="دفتر مرکزی">دفتر مرکزی</option>
          <option value="شعبه مسجد">شعبه مسجد</option>
          <option value="شعبه لبخند">شعبه لبخند</option>
          <option value="شعبه الزهرا سلام الله علیها">شعبه الزهرا سلام الله علیها</option>
          <option value="سرای لبخند">سرای لبخند</option>
        </select>
        <div class="print-only info-print" id="printMeetingLocationField"></div>
      </div>

      <textarea id="topic" class="topic-section" placeholder="🔹 موضوع جلسه" required></textarea>

      <div class="attendees-section">
        <select id="attendeesList" class="attendees-list" multiple>
          <option value="محمد جواد اسماعیلی">محمد جواد اسماعیلی</option>
          <option value="علیرضا اسماعیلی">علیرضا اسماعیلی</option>
          <option value="علیرضا کیایی">علیرضا کیایی</option>
          <option value="علی سلیمی">علی سلیمی</option>
          <option value="کاظم کاظمی">کاظم کاظمی</option>
          <option value="رضا خانی">رضا خانی</option>
          <option value="آقای اخباریه">آقای اخباریه</option>
          <option value="محمدرضا صالحی">محمدرضا صالحی</option>
          <option value="محمد صباغی">محمد صباغی</option>
          <option value="میثم نوری سلطان">میثم نوری سلطان</option>
          <option value="سید طیبی">سید طیبی</option>
          <option value="میلاد بختور">میلاد بختور</option>
        </select>
        <input type="text" id="newAttendee" class="attendees-input" placeholder="➕ افزودن نام جدید">
        <button type="button" class="primary-btn" onclick="addAttendee()">افزودن</button>
      </div>

      <div id="selectedAttendees">
        <h3>حاضرین در جلسه: <span id="selectedAttendeeList" style="font-size: 12px;"></span></h3>
      </div>

      <div id="entries">
        <div class="entry-row" data-entry-id="1">
          <textarea oninput="autoResize(this)" class="autoresize" placeholder="📌 مصوبه ۱"></textarea>
          <div class="entry-details">
            <input type="text" placeholder="👤 مسئول اجرا">
            <input type="text" class="shamsi-date" placeholder="📅 مهلت اجرا">
            <input type="file" onchange="previewFile(this)">
            <div class="file-preview" style="margin-top: 5px;"></div>
            <button type="button" class="remove-btn" onclick="removeEntry(this)">حذف</button>
          </div>
        </div>
      </div>

      <div class="action-buttons">
        <button type="button" class="primary-btn" onclick="addEntry()">+ افزودن مصوبه جدید</button>
        <button type="button" class="primary-btn" onclick="generatePreview()">🔍 پیش‌نمایش</button>
        <button type="button" class="primary-btn" onclick="generatePDF()">📄 دانلود PDF</button>
        <button type="button" class="primary-btn" onclick="sharePDFViaWhatsApp()">📤 اشتراک در واتساپ</button>
        <button type="button" class="primary-btn" onclick="toggleDarkMode()">🌙 حالت تاریک</button>
        <button type="button" class="primary-btn" onclick="saveTemplate()">💾 ذخیره الگو</button>
        <button type="button" class="primary-btn" onclick="loadTemplate()">📁 بارگذاری الگو</button>
        <button type="button" class="primary-btn" onclick="exportJSON()">📥 JSON</button>
        <button type="button" class="primary-btn" onclick="exportCSV()">📥 CSV</button>
        <a href="javascript:window.print()" class="primary-btn">🖨️ پرینت</a>
      </div>
    </form>

    <div id="previewContent"></div>
  </div>

  <!-- html2pdf -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.9.3/html2pdf.bundle.min.js "></script>

  <script>
    function resetDate() {
      const now = new Date();
      const options = { year: 'numeric', month: '2-digit', day: '2-digit' };
      const formattedDate = now.toLocaleDateString('fa-IR', options).replace(/\//g, '-');
      document.getElementById("meetingDate").value = formattedDate;
    }

    function resetTime() {
      const now = new Date();
      const options = { hour: '2-digit', minute: '2-digit', hour12: false };
      const formattedTime = now.toLocaleTimeString('fa-IR', options);
      document.getElementById("meetingTime").value = formattedTime;
    }

    function setCurrentDateTime() {
      resetDate();
      resetTime();
    }

    function addEntry() {
      const count = document.querySelectorAll(".entry-row").length + 1;
      var entryDiv = document.createElement("div");
      entryDiv.classList.add("entry-row");
      entryDiv.setAttribute("data-entry-id", count);
      entryDiv.innerHTML = `
        <textarea oninput="autoResize(this)" class="autoresize" placeholder="📌 مصوبه ${count}"></textarea>
        <div class="entry-details">
          <input type="text" placeholder="👤 مسئول اجرا">
          <input type="text" class="shamsi-date" placeholder="📅 مهلت اجرا">
          <input type="file" onchange="previewFile(this)">
          <div class="file-preview" style="margin-top: 5px;"></div>
          <button type="button" class="remove-btn" onclick="removeEntry(this)">حذف</button>
        </div>
      `;
      document.getElementById("entries").appendChild(entryDiv);
    }

    function removeEntry(button) {
      button.closest('.entry-row').remove();
    }

    function autoResize(textarea) {
      textarea.style.height = "auto";
      textarea.style.height = textarea.scrollHeight + "px";
    }

    function addAttendee() {
      var newName = document.getElementById("newAttendee").value.trim();
      if (newName) {
        var option = document.createElement("option");
        option.text = newName;
        option.value = newName;
        document.getElementById("attendeesList").add(option);
        document.getElementById("newAttendee").value = "";
        updateSelectedAttendees();
      }
    }

    document.getElementById("attendeesList").addEventListener("change", updateSelectedAttendees);

    function updateSelectedAttendees() {
      const selectedList = document.getElementById("attendeesList");
      const names = [];
      for (let i = 0; i < selectedList.options.length; i++) {
        if (selectedList.options[i].selected) names.push(selectedList.options[i].value);
      }
      document.getElementById("selectedAttendeeList").textContent = names.join(', ');
    }

    function updatePrintLocation() {
      const location = document.getElementById("meetingLocation").value;
      const printLocationDiv = document.getElementById("printMeetingLocationField");
      printLocationDiv.textContent = "📍 مکان جلسه: " + location;
    }

    document.getElementById("meetingLocation").addEventListener("change", updatePrintLocation);

    function generatePreview() {
      const form = document.querySelector("#meetingForm").cloneNode(true);
      const preview = document.getElementById("previewContent");
      const buttons = form.querySelectorAll("button, .action-buttons");
      buttons.forEach(btn => btn.remove());
      preview.innerHTML = '';
      preview.appendChild(form);
      preview.style.display = 'block';
      window.scrollTo({ top: preview.offsetTop, behavior: 'smooth' });
    }

    function generatePDF() {
      const element = document.querySelector(".container");
      html2pdf().from(element).save();
    }

    function sharePDFViaWhatsApp() {
      const element = document.querySelector(".container");
      const topic = document.getElementById("topic").value || "صورتجلسه";
      const opt = { filename: `${topic}.pdf`, image: { type: 'jpeg', quality: 0.98 }, jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' } };
      html2pdf().set(opt).from(element).toPdf().output('blob').then(function(pdfBlob) {
        const blobUrl = URL.createObjectURL(pdfBlob);
        const whatsappIntentUrl = `whatsapp://send?text=لطفاً صورتجلسه را مشاهده کنید.%0A${blobUrl}`;
        window.open(whatsappIntentUrl, '_blank');
        const link = document.createElement('a');
        link.href = blobUrl;
        link.download = opt.filename;
        link.click();
        setTimeout(() => URL.revokeObjectURL(blobUrl), 10000);
      });
    }

    function toggleDarkMode() {
      document.body.classList.toggle("dark-mode");
    }

    function saveTemplate() {
      const data = {
        meetingDate: document.getElementById("meetingDate").value,
        meetingTime: document.getElementById("meetingTime").value,
        meetingNumber: document.getElementById("meetingNumber").value,
        meetingLocation: document.getElementById("meetingLocation").value,
        topic: document.getElementById("topic").value,
        attendees: Array.from(document.getElementById("attendeesList").selectedOptions).map(o => o.value),
        entries: Array.from(document.querySelectorAll(".entry-row")).map((el, i) => ({
          text: el.querySelector("textarea").value,
          responsible: el.querySelectorAll("input")[0].value,
          deadline: el.querySelectorAll("input")[1]?.value || "",
        })),
      };
      localStorage.setItem("template", JSON.stringify(data));
      alert("الگو ذخیره شد.");
    }

    function loadTemplate() {
      const saved = localStorage.getItem("template");
      if (!saved) return alert("الگویی وجود ندارد.");
      const data = JSON.parse(saved);
      document.getElementById("meetingDate").value = data.meetingDate;
      document.getElementById("meetingTime").value = data.meetingTime;
      document.getElementById("meetingNumber").value = data.meetingNumber;
      document.getElementById("meetingLocation").value = data.meetingLocation;
      document.getElementById("topic").value = data.topic;
      const list = document.getElementById("attendeesList");
      for (let i = 0; i < list.options.length; i++) {
        list.options[i].selected = data.attendees.includes(list.options[i].value);
      }
      updateSelectedAttendees();
      document.getElementById("entries").innerHTML = '';
      data.entries.forEach((entry, i) => {
        const div = document.createElement("div");
        div.className = "entry-row";
        div.innerHTML = `
          <textarea oninput="autoResize(this)" class="autoresize" placeholder="📌 مصوبه">${entry.text}</textarea>
          <div class="entry-details">
            <input type="text" value="${entry.responsible}" placeholder="👤 مسئول اجرا">
            <input type="text" class="shamsi-date" value="${entry.deadline}" placeholder="📅 مهلت اجرا">
            <input type="file" onchange="previewFile(this)">
            <div class="file-preview" style="margin-top: 5px;"></div>
            <button type="button" class="remove-btn" onclick="removeEntry(this)">حذف</button>
          </div>
        `;
        document.getElementById("entries").appendChild(div);
      });
    }

    function exportJSON() {
      const data = {
        meetingDate: document.getElementById("meetingDate").value,
        meetingTime: document.getElementById("meetingTime").value,
        meetingNumber: document.getElementById("meetingNumber").value,
        meetingLocation: document.getElementById("meetingLocation").value,
        topic: document.getElementById("topic").value,
        attendees: Array.from(document.getElementById("attendeesList").selectedOptions).map(o => o.value),
        entries: Array.from(document.querySelectorAll(".entry-row")).map((el, i) => ({
          text: el.querySelector("textarea").value,
          responsible: el.querySelectorAll("input")[0].value,
          deadline: el.querySelectorAll("input")[1]?.value || "",
        })),
      };
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(data, null, 2));
      const dlAnchorElem = document.createElement('a');
      dlAnchorElem.setAttribute("href", dataStr);
      dlAnchorElem.setAttribute("download", "minutes.json");
      document.body.appendChild(dlAnchorElem);
      dlAnchorElem.click();
      document.body.removeChild(dlAnchorElem);
    }

    function exportCSV() {
      let csv = ['شماره,متون,مسئول,مهلت'].join(',') + "\r\n";
      const rows = document.querySelectorAll(".entry-row");
      rows.forEach((row, i) => {
        const inputs = row.querySelectorAll("input");
        const text = row.querySelector("textarea").value.replace(/,/g, "،");
        const responsible = inputs[0].value.replace(/,/g, "،");
        const deadline = inputs[1]?.value || "";
        csv += [i + 1, `"${text}"`, `"${responsible}"`, `"${deadline}"`].join(",") + "\r\n";
      });
      const csvData = "data:text/csv;charset=utf-8,%EF%BB%BF" + encodeURI(csv);
      const link = document.createElement("a");
      link.setAttribute("href", csvData);
      link.setAttribute("download", "minutes.csv");
      link.click();
    }

    function previewFile(input) {
      const preview = input.nextElementSibling;
      if (input.files && input.files[0]) {
        const reader = new FileReader();
        reader.onload = function(e) {
          preview.innerHTML = `<small>فایل: ${input.files[0].name}</small>`;
        };
        reader.readAsDataURL(input.files[0]);
      }
    }

    function autoSave() {
      setInterval(() => {
        const data = {
          meetingDate: document.getElementById("meetingDate").value,
          meetingTime: document.getElementById("meetingTime").value,
          meetingNumber: document.getElementById("meetingNumber").value,
          meetingLocation: document.getElementById("meetingLocation").value,
          topic: document.getElementById("topic").value,
          attendees: Array.from(document.getElementById("attendeesList").selectedOptions).map(o => o.value),
          entries: Array.from(document.querySelectorAll(".entry-row")).map((el, i) => ({
            text: el.querySelector("textarea").value,
            responsible: el.querySelectorAll("input")[0].value,
            deadline: el.querySelectorAll("input")[1]?.value || "",
          })),
        };
        localStorage.setItem("autosave", JSON.stringify(data));
      }, 10000);
    }

    function autoLoad() {
      const saved = localStorage.getItem("autosave");
      if (!saved) {
        setCurrentDateTime();
        updatePrintLocation();
        setupWhatsAppShare();
        return;
      }
      const data = JSON.parse(saved);
      document.getElementById("meetingDate").value = data.meetingDate;
      document.getElementById("meetingTime").value = data.meetingTime;
      document.getElementById("meetingNumber").value = data.meetingNumber;
      document.getElementById("meetingLocation").value = data.meetingLocation;
      document.getElementById("top

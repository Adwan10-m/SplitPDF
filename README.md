<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>فصل صفحات PDF</title>
</head>
<body>
  <h2>فصل ملف PDF إلى نمطين</h2>
  <input type="file" id="fileInput" accept="application/pdf">
  <button onclick="splitPDF()">فصل الملف</button>
  <br><br>
  <a id="download1" style="display:none;">تحميل النمط الأول</a><br>
  <a id="download2" style="display:none;">تحميل النمط الثاني</a>

  <script src="https://unpkg.com/pdf-lib/dist/pdf-lib.min.js"></script>
  <script>
    async function splitPDF() {
      const fileInput = document.getElementById('fileInput');
      if (!fileInput.files.length) return alert("اختر ملف PDF أولًا");

      const file = fileInput.files[0];
      const arrayBuffer = await file.arrayBuffer();
      const pdfDoc = await PDFLib.PDFDocument.load(arrayBuffer);

      const totalPages = pdfDoc

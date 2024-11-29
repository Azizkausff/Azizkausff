<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>خريطة تفاعلية - مهرجان الأفلام</title>
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
  <style>
    #map {
      height: 600px;
      width: 100%;
      margin: 20px auto;
      border: 2px solid #4caf50;
      border-radius: 8px;
    }
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      text-align: center;
      background: #f4f4f9;
    }
    h1 {
      background: #4caf50;
      color: white;
      padding: 10px;
    }
  </style>
</head>
<body>
  <h1>خريطة تفاعلية - مهرجان الأفلام الطلابية</h1>
  <div id="map"></div>
  <script>
    // إعداد الخريطة
    var map = L.map('map').setView([21.4858, 39.1925], 16); // إحداثيات جامعة الملك عبد العزيز

    // إضافة طبقة خريطة
    L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      maxZoom: 18,
      attribution: '© OpenStreetMap'
    }).addTo(map);

    // إضافة نقاط تفاعلية
    var locations = [
      { name: "قاعة الملك فيصل للمؤتمرات", coords: [21.4875, 39.1925], description: "الموقع الرئيسي للمهرجان" },
      { name: "قاعة 1", coords: [21.4865, 39.1935], description: "جلسات حوارية وورش عمل" },
      { name: "قاعة 2", coords: [21.4855, 39.1920], description: "عرض أفلام وثائقية" },
      { name: "أجنحة الجامعات المشاركة", coords: [21.4858, 39.1915], description: "معرض الجامعات والشركات" }
    ];

    locations.forEach(location => {
      L.marker(location.coords).addTo(map)
        .bindPopup(`<b>${location.name}</b><br>${location.description}`);
    });
  </script>
</body>
</html>

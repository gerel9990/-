<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Personality Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
    }
    .question {
      margin-bottom: 20px;
    }
    .result {
      font-weight: bold;
      margin-top: 20px;
    }
    .error {
      color: red;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>Таны манлайлах хэв маяг юу вэ?</h1>
  <form id="quizForm">
    <div class="question">
      <p>1. Өсөж том болох явцад тань...</p>
      <label><input type="radio" name="q1" value="A"> А. Таны асран хамгаалагчид хүүхэд байхад чинь таны хэрэгцээнд төдийлөн анхаардаггүй байсан.</label><br>
      <label><input type="radio" name="q1" value="B"> Б. Та гэр бүлийнхээ том хүмүүсийг дийлж чаддаг байсан.</label><br>
      <label><input type="radio" name="q1" value="C"> В. Асран хамгаалагчдын тань аль нэг нь давуу эрхтэй байсан.</label><br>
      <label><input type="radio" name="q1" value="D"> Г. Таны асран хамгаалагчдын дунд эрх ашгийн тэнцвэргүй байдал байсан.</label>
    </div>
    <div class="question">
      <p>2. Хүүхэд байхдаа та...</p>
      <label><input type="radio" name="q2" value="A"> А. Насанд хүрсэн хүний үүрэг гүйцэтгэдэг байсан уу? (Жишээ нь: зуны амралтаараа ажил хийх эсвэл дүү нараа харах)</label><br>
      <label><input type="radio" name="q2" value="B"> Б. Асран хамгаалагчдынхаа сэтгэл санааг дэмжигч гол хүн байсан.</label><br>
      <label><input type="radio" name="q2" value="C"> В. Гэр бүлийнхээ хүчтэй хүнийг дуурайх гэж хичээдэг байсан.</label><br>
      <label><input type="radio" name="q2" value="D"> Г. Асран хамгаалагчдынхаа статусын талаар асууснаар магтуулдаг байсан.</label>
    </div>
    <div class="question">
      <p>3. Ажил дээрээ та...</p>
      <label><input type="radio" name="q3" value="A"> А. Бусдын хийх дүргүй зайлсхийдэг ажлыг тогтмол хийдэг.</label><br>
      <label><input type="radio" name="q3" value="B"> Б. Үйл явцаас илүү үр дүнд анхаардаг.</label><br>
      <label><input type="radio" name="q3" value="C"> В. Бусдаас илүү хурдан урагшлаад байгаа мэт санагддаг.</label><br>
      <label><input type="radio" name="q3" value="D"> Г. Удирдах албан тушаалтнуудаас нийтлэг давуу талыг авч үзэх төдийгүй бусад чухал зүйлсийг ч анхаараасай гэж хүлээдэг.</label>
    </div>
    <div class="question">
      <p>4. Ажлын байран дээрээ та...</p>
      <label><input type="radio" name="q4" value="A"> А. Хэрвээ үл тоомсорлуулж, бага цалин авч, шудрага бус байдалтай учирвал өөрийгөө хамгаалж дуугарахад хэцүү байдаг.</label><br>
      <label><input type="radio" name="q4" value="B"> Б. Өөрт хэрэггүй гэж үзсэн хурлуудаас зайлсхийдэг.</label><br>
      <label><input type="radio" name="q4" value="C"> В. Таны хариу үйлдэл, өнгө аяс бусдыг айлгасан гэсэн гомдол, санал авч бусдыг байсан.</label><br>
      <label><input type="radio" name="q4" value="D"> Г. Хуучирч хоцрогдсон зүйлсийг олж хардаг эхний хүн байдаг.</label>
    </div>
    <div class="question">
      <p>5. Хамтран ажиллагсадтайгаа харьцахдаа та...</p>
      <label><input type="radio" name="q5" value="A"> А. Бусдын орхигдуулдаг нарийн зүйлсийг анзаардаг.</label><br>
      <label><input type="radio" name="q5" value="B"> Б. Хэт их ачааллын үед хамт олноосоо холддог.</label><br>
      <label><input type="radio" name="q5" value="C"> В. Албан ёсны удирдлага байхгүй үед таны бодлыг асуудаг эсэх.</label><br>
      <label><input type="radio" name="q5" value="D"> Г. Бусдын гаргасан санаа, хувь нэмрийг заавал үнэлж сайшаадаг.</label>
    </div>
    <div>

      <button type="button" onclick="calculateResult()">Submit</button>
    </div>
  </form>

  <script>
    function calculateResult() {
      const form = document.getElementById('quizForm');
      const answers = new FormData(form);
      const counts = { A: 0, B: 0, C: 0, D: 0 };
      let allAnswered = true;

      for (let i = 1; i <= 5; i++) {
        if (!answers.has('q' + i)) {
          allAnswered = false;
          break;
        }
      }

      if (!allAnswered) {
        alert("Та бүх асуултад хариулна уу."); 
        return;
      }

      for (let value of answers.values()) {
        counts[value]++;
      }

      let result;
      if (counts.A >= 3) result = "Та 'Pleaser' хүн юм.";
      else if (counts.B >= 3) result = "Та 'Charmer' хүн юм.";
      else if (counts.C >= 3) result = "Та 'Commander' хүн юм.";
      else if (counts.D >= 3) result = "Та 'Inspirer' хүн юм.";
      else result = "Таны сонголт тодорхой үр дүн өгөөгүй.";

      const newTab = window.open();
      newTab.document.write('<html><head><title>Quiz Result</title></head><body>');
      newTab.document.write('<h1>Таны манлайлах хэв маяг бол</h1>');
      newTab.document.write('<p>' + result + '</p>');
      newTab.document.write('</body></html>');
      newTab.document.close();
    }
  </script>
</body>
</html>

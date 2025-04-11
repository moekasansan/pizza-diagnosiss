<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>誕生日でわかるピザ診断</title>
  <style>
    body {
      font-family: "Segoe UI", sans-serif;
      background: #fffbe8;
      text-align: center;
      padding: 30px;
    }
    .result-box {
      margin-top: 20px;
      padding: 20px;
      border: 2px dashed #ffa726;
      border-radius: 10px;
      background: #fff3e0;
    }
    input[type="date"] {
      padding: 10px;
      font-size: 16px;
    }
    button {
      padding: 10px 20px;
      background: #ff9800;
      color: white;
      border: none;
      border-radius: 5px;
      margin-top: 10px;
      cursor: pointer;
    }
    .pizza-img {
      width: 280px;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <h1>🍕誕生日でわかる！ピザ診断🍕</h1>
  <p>あなたはどんなピザタイプ？誕生日を入力してチェックしよう！</p>

  <input type="date" id="birthdate">
  <br>
  <button onclick="diagnosePizza()">診断する</button>

  <div id="result" class="result-box" style="display:none;"></div>

  <script>
    const sauces = {
      1: "情熱的なトマトソース",
      2: "繊細なホワイトソース",
      3: "自由なバジルソース",
      4: "パワフルなガーリックソース",
      5: "落ち着いたスモークソース",
      6: "爽やかなレモンクリーム",
      7: "優しいてりやきソース",
      8: "刺激的なチリソース",
      9: "神秘的なトリュフソース",
      10: "知的な和風ソース",
      11: "アーティスティックなジェノベーゼ",
      12: "明るいチーズソース"
    };

    const toppings = [
      "とろけるチーズ（やさしさ）", "ペパロニ（元気）", "トマト（情熱）", "バジル（癒し）",
      "エビ（上品）", "マッシュルーム（控えめ）", "ハム（愛され体質）", "アスパラ（健康志向）",
      "パイナップル（自由人）", "サラミ（冒険家）", "ツナ（落ち着き）", "唐辛子（スパイシー）",
      "ズッキーニ（個性派）", "ナス（クール）", "コーン（親しみ）", "ベーコン（頼れる）",
      "明太子（センス◎）", "オリーブ（ミステリアス）", "スモークチキン（芯が強い）",
      "たまご（安心感）", "アンチョビ（職人気質）", "生ハム（繊細）", "カニカマ（平和主義）",
      "クワトロチーズ（知的）", "イカ（神秘的）", "ホウレン草（真面目）", "サーモン（感性豊か）",
      "シーフードMIX（バランス型）", "ブラックペッパー（刺激好き）", "サルシッチャ（強気）", "モッツァレラ（ナチュラル）"
    ];

    function diagnosePizza() {
      const input = document.getElementById("birthdate").value;
      if (!input) {
        alert("誕生日を入力してください！");
        return;
      }

      const date = new Date(input);
      const month = date.getMonth() + 1;
      const day = date.getDate();

      const sauce = sauces[month];
      const topping = toppings[(day - 1) % toppings.length];

      const resultBox = document.getElementById("result");
      resultBox.innerHTML = 
        <h2>あなたのピザはこれ！</h2>
        <img src="https://upload.wikimedia.org/wikipedia/commons/d/d3/Supreme_pizza.jpg" alt="ピザ画像" class="pizza-img">
        <p><strong>ベースソース：</strong>${sauce}</p>
        <p><strong>トッピング：</strong>${topping}</p>
        <p><strong>あなたの性格：</strong>あなたは ${sauce} のように個性があり、<br>${topping} のような魅力を持つ人です！</p>
      ;
      resultBox.style.display = "block";
    }
  </script>

</body>
</html>

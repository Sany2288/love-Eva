[uhu.html](https://github.com/user-attachments/files/22309147/uhu.html)# love-Eva[Uploadin
DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8">
  <title>Меню з корзиною</title>
  <style>
    body {
      background: url("https://i.ibb.co/ZL1dg8h/cats-hearts.png") repeat;
      background-size: 150px;
      color: white;
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }
    h1, h2 {
      text-align: center;
      margin-top: 20px;
      text-shadow: 2px 2px 5px black;
    }
    .menu {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 20px;
      margin: 30px;
    }
    .item {
      background: rgba(0, 0, 0, 0.7);
      border-radius: 10px;
      padding: 20px;
      width: 200px;
      text-align: center;
      box-shadow: 0 0 10px pink;
      position: relative;
      overflow: visible;
    }
    .item img {
      width: 100%;
      border-radius: 10px;
    }
    .item h3 {
      margin: 10px 0;
    }
    button {
      margin-top: 10px;
      background-color: hotpink;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      transition: 0.3s;
    }
    button:hover {
      background-color: deeppink;
      transform: scale(1.1);
    }
    .cart {
      background: rgba(0, 0, 0, 0.7);
      margin: 20px auto;
      padding: 20px;
      width: 400px;
      border-radius: 10px;
      box-shadow: 0 0 15px pink;
    }
    .cart ul {
      list-style: none;
      padding: 0;
    }
    .cart li {
      padding: 5px 0;
      border-bottom: 1px solid #444;
      display: flex;
      justify-content: space-between;
    }
    .remove-btn {
      background: #ff69b4;
      color: white;
      border: none;
      border-radius: 5px;
      padding: 3px 7px;
      cursor: pointer;
    }
    .remove-btn:hover {
      background: #ff1493;
    }

    /* 🔥 Анімація вилітаючого товару */
    .flying {
      position: absolute;
      width: 50px;
      height: 50px;
      animation: flyUp 1.2s ease-out forwards;
      pointer-events: none;
    }

    @keyframes flyUp {
      0% { opacity: 1; transform: translateY(0) scale(1); }
      50% { opacity: 0.8; transform: translateY(-60px) scale(0.8); }
      100% { opacity: 0; transform: translateY(-120px) scale(0.5); }
    }
  </style>
</head>
<body>
  <h1>🍴 Наше меню</h1>

  <!-- Меню -->
  <div class="menu">
    <div class="item">
      <img src="https://upload.wikimedia.org/wikipedia/commons/2/23/Coca_Cola_Bottle.JPG" alt="Coca Cola">
      <h3>Coca Cola</h3>
      <button onclick="addToCart('Coca Cola', this, 'https://upload.wikimedia.org/wikipedia/commons/2/23/Coca_Cola_Bottle.JPG')">Замовити</button>
    </div>
    <div class="item">
      <img src="https://upload.wikimedia.org/wikipedia/commons/8/82/Chicken_Shawarma_Wrap.jpg" alt="Шаурма">
      <h3>Шаурма</h3>
      <button onclick="addToCart('Шаурма', this, 'https://upload.wikimedia.org/wikipedia/commons/8/82/Chicken_Shawarma_Wrap.jpg')">Замовити</button>
    </div>
    <div class="item">
      <img src="https://upload.wikimedia.org/wikipedia/commons/6/60/Sushi_platter.jpg" alt="Роли">
      <h3>Роли</h3>
      <button onclick="addToCart('Роли', this, 'https://upload.wikimedia.org/wikipedia/commons/6/60/Sushi_platter.jpg')">Замовити</button>
    </div>
    <div class="item">
      <img src="https://upload.wikimedia.org/wikipedia/commons/d/d3/Supreme_pizza.jpg" alt="Піца">
      <h3>Піца</h3>
      <button onclick="addToCart('Піца', this, 'https://upload.wikimedia.org/wikipedia/commons/d/d3/Supreme_pizza.jpg')">Замовити</button>
    </div>
  </div>

  <!-- Корзина -->
  <div class="cart">
    <h2>🛒 Ваша корзина</h2>
    <ul id="cart-list"></ul>
    <p id="empty-text">Корзина порожня</p>
  </div>

  <script>
    let cart = {};

    function addToCart(item, button, imgUrl) {
      const emptyText = document.getElementById("empty-text");
      emptyText.style.display = "none";

      // Якщо товар вже є у корзині → +1
      if (cart[item]) {
        cart[item]++;
      } else {
        cart[item] = 1;
      }
      renderCart();

      // 🚀 Анімація вилітання картинки
      const flyingImg = document.createElement("img");
      flyingImg.src = imgUrl;
      flyingImg.classList.add("flying");
      button.parentElement.appendChild(flyingImg);

      // видаляємо після завершення анімації
      flyingImg.addEventListener("animationend", () => {
        flyingImg.remove();
      });
    }

    function removeFromCart(item) {
      if (cart[item]) {
        cart[item]--;
        if (cart[item] === 0) {
          delete cart[item];
        }
      }
      renderCart();
    }

    function renderCart() {
      const cartList = document.getElementById("cart-list");
      cartList.innerHTML = "";

      const emptyText = document.getElementById("empty-text");

      if (Object.keys(cart).length === 0) {
        emptyText.style.display = "block";
      } else {
        emptyText.style.display = "none";
        for (let item in cart) {
          let li = document.createElement("li");
          li.innerHTML = `${item} ×${cart[item]} 
            <button class="remove-btn" onclick="removeFromCart('${item}')">-</button>`;
          cartList.appendChild(li);
        }
      }
    }
  </script>
</body>
</html>g uhu.html…]()

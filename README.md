<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nairo Fashion</title>
<style>
body {font-family: Arial; margin:0; background:#f5f5f5;}
header {background:#111; color:#fff; padding:15px; display:flex; justify-content:space-between; align-items:center;}
header h1 {margin:0;}
nav a {color:white; margin:0 10px; text-decoration:none;}
.container {padding:20px;}
.products {display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:20px;}
.card {background:#fff; padding:15px; border-radius:10px; box-shadow:0 2px 5px rgba(0,0,0,0.1);} 
.card img {width:100%; border-radius:10px;}
button {padding:10px; border:none; background:black; color:white; cursor:pointer; margin-top:10px; width:100%;}
footer {background:#111; color:#fff; text-align:center; padding:10px; margin-top:20px;}
input {padding:10px; width:100%; margin-bottom:10px;}
.section {display:none;}
.active {display:block;}
</style>
</head>
<body>

<header>
<h1>Nairo Fashion</h1>
<nav>
<a href="#" onclick="showSection('home')">Home</a>
<a href="#" onclick="showSection('cart')">Cart</a>
<a href="#" onclick="showSection('profile')">Profile</a>
<a href="#" onclick="showSection('orders')">Orders</a>
<a href="#" onclick="showSection('login')">Login</a>
</nav>
</header>

<div class="container">

<!-- Home -->
<div id="home" class="section active">
<h2>Shop Now</h2>
<input type="text" id="search" placeholder="Search products..." onkeyup="searchProducts()">
<div class="products" id="productList"></div>
</div>

<!-- Cart -->
<div id="cart" class="section">
<h2>Your Cart</h2>
<ul id="cartItems"></ul>
<button onclick="checkout()">Buy Now</button>
</div>

<!-- Orders -->
<div id="orders" class="section">
<h2>Track Orders</h2>
<p>Your order is on the way 🚚</p>
</div>

<!-- Profile -->
<div id="profile" class="section">
<h2>Customer Profile</h2>
<p>Name: Rohit</p>
<p>Email: example@gmail.com</p>
</div>

<!-- Login -->
<div id="login" class="section">
<h2>Login / Register</h2>
<input type="text" placeholder="Email">
<input type="password" placeholder="Password">
<button>Login</button>
<button>Login with Google</button>
<button>Login with Facebook</button>
</div>

<!-- Support -->
<div id="support" class="section">
<h2>Customer Support</h2>
<a href="https://wa.me/916375527033" target="_blank">
<button>Chat on WhatsApp</button>
</a>
</div>

</div>

<footer>
<p>© 2026 Nairo Fashion</p>
</footer>

<script>
let products = [
{name:"Men Shoes", price:1200, img:"https://via.placeholder.com/200"},
{name:"Women Dress", price:1500, img:"https://via.placeholder.com/200"},
{name:"Kids Wear", price:800, img:"https://via.placeholder.com/200"},
{name:"Leather Belt", price:500, img:"https://via.placeholder.com/200"}
];

let cart = [];

function displayProducts(list) {
let html="";
list.forEach((p,i)=>{
html+=`<div class='card'>
<img src='${p.img}'>
<h3>${p.name}</h3>
<p>₹${p.price}</p>
<button onclick='addToCart(${i})'>Add to Cart</button>
</div>`;
});
document.getElementById("productList").innerHTML=html;
}

function addToCart(i) {
cart.push(products[i]);
alert("Added to cart");
updateCart();
}

function updateCart() {
let html="";
cart.forEach(p=>{
html+=`<li>${p.name} - ₹${p.price}</li>`;
});
document.getElementById("cartItems").innerHTML=html;
}

function checkout() {
alert("Order placed! Payment: Cash on Delivery / Card");
cart=[];
updateCart();
}

function showSection(id) {
document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));
document.getElementById(id).classList.add('active');
}

function searchProducts() {
let value = document.getElementById("search").value.toLowerCase();
let filtered = products.filter(p=>p.name.toLowerCase().includes(value));
displayProducts(filtered);
}

displayProducts(products);
</script>

</body>
</html>

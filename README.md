
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>KS MART</title>
<style>
*{box-sizing:border-box}
body{margin:0;font-family:Arial;background:#f5f5f5;color:#222}
header{background:#111;color:#d4af37;padding:18px;text-align:center}
header h1{margin:0;font-size:30px;letter-spacing:2px}
.search{padding:15px;background:#111}
.search input{width:100%;padding:13px;border:0;border-radius:8px}
nav{display:flex;overflow:auto;background:#222;padding:12px;gap:20px}
nav a{color:#d4af37;text-decoration:none;white-space:nowrap}
.banner{background:#171717;color:#d4af37;text-align:center;padding:35px 15px}
.banner h2{font-size:26px}
button{background:#d4af37;color:#111;border:0;padding:10px 15px;border-radius:6px;font-weight:bold}
.products{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;padding:12px}
.card{background:white;border-radius:10px;padding:10px;text-align:center}
.card img{width:100%;height:130px;object-fit:contain;background:#eee;border-radius:8px}
.card h3{font-size:15px}
.price{font-weight:bold;color:#b8860b}
#cart{background:#111;color:white;padding:18px;margin:12px;border-radius:10px}
footer{background:#111;color:#d4af37;text-align:center;padding:20px}
</style>
</head>
<body>

<header>
<h1>KS MART</h1>
<p>SHOP SMART • SAVE MORE</p>
</header>

<div class="search">
<input id="search" placeholder="Search products..." oninput="showProducts()">
</div>

<nav>
<a href="#">Home</a>
<a href="#products">Products</a>
<a href="#cart">My Cart</a>
<a href="#contact">Contact</a>
</nav>

<div class="banner">
<h2>Welcome to KS MART</h2>
<p>Everything You Need, At One Place</p>
<button onclick="document.getElementById('products').scrollIntoView()">Shop Now</button>
</div>

<h2 style="text-align:center">Our Products</h2>
<div class="products" id="products"></div>

<div id="cart">
<h2>My Cart 🛒</h2>
<div id="cartItems">Your cart is empty</div>
<h3 id="total">Total: ₹0</h3>
<button onclick="checkout()">Place Order</button>
</div>

<footer id="contact">
<h2>KS MART</h2>
<p>Thank you for shopping with us!</p>
</footer>

<script>
const products=[
{name:"Fashion Item",price:499,image:"https://placehold.co/300x200?text=Fashion"},
{name:"Shoes",price:799,image:"https://placehold.co/300x200?text=Shoes"},
{name:"Watch",price:599,image:"https://placehold.co/300x200?text=Watch"},
{name:"Home Product",price:299,image:"https://placehold.co/300x200?text=Home"},
{name:"Beauty Product",price:199,image:"https://placehold.co/300x200?text=Beauty"},
{name:"Electronics",price:999,image:"https://placehold.co/300x200?text=Electronics"}
];

let cart=[];

function showProducts(){
let q=document.getElementById("search").value.toLowerCase();
document.getElementById("products").innerHTML=
products.filter(p=>p.name.toLowerCase().includes(q)).map((p,i)=>`
<div class="card">
<img src="${p.image}" alt="${p.name}">
<h3>${p.name}</h3>
<p class="price">₹${p.price}</p>
<button onclick="addCart('${p.name}')">Add to Cart</button>
</div>`).join("");
}

function addCart(name){
let p=products.find(x=>x.name===name);
cart.push(p);
updateCart();
}

function updateCart(){
let total=cart.reduce((sum,p)=>sum+p.price,0);
document.getElementById("cartItems").innerHTML=
cart.length?cart.map((p,i)=>`
<p>${p.name} - ₹${p.price}
<button onclick="removeCart(${i})">Remove</button></p>`).join(""):"Your cart is empty";
document.getElementById("total").innerText="Total: ₹"+total;
}

function removeCart(i){
cart.splice(i,1);
updateCart();
}

function checkout(){
if(!cart.length){alert("Please add products first");return;}
alert("Order system will be connected in the next step.");
}

showProducts();
</script>
</body>
</html>


<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Librairie en ligne</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <header>
        <h1>Bienvenue à la Librairie en Ligne</h1>
        <p>Découvrez nos livres</p>
    </header>

    <main>
        <section class="book-list">
            <div class="book-card" data-title="Le Petit Prince" data-author="Antoine de Saint-Exupéry">
                <img src="https://via.placeholder.com/150" alt="Le Petit Prince">
                <h3>Le Petit Prince</h3>
                <p>Antoine de Saint-Exupéry</p>
                <button class="btn-add">Ajouter au panier</button>
            </div>

            <div class="book-card" data-title="1984" data-author="George Orwell">
                <img src="https://via.placeholder.com/150" alt="1984">
                <h3>1984</h3>
                <p>George Orwell</p>
                <button class="btn-add">Ajouter au panier</button>
            </div>

            <!-- Ajouter d'autres livres ici -->
        </section>
        
        <section class="cart">
            <h2>Mon Panier</h2>
            <ul id="cart-list">
                <!-- Les livres ajoutés au panier apparaîtront ici -->
            </ul>
        </section>
    </main>

    <footer>
        <p>&copy; 2025 Librairie en Ligne</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Librairie en ligne</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>

    <header>
        <h1>Bienvenue à la Librairie en Ligne</h1>
        <p>Découvrez nos livres</p>
    </header>

    <main>
        <section class="book-list">
            <div class="book-card" data-title="Le Petit Prince" data-author="Antoine de Saint-Exupéry">
                <img src="https://via.placeholder.com/150" alt="Le Petit Prince">
                <h3>Le Petit Prince</h3>
                <p>Antoine de Saint-Exupéry</p>
                <button class="btn-add">Ajouter au panier</button>
            </div>

            <div class="book-card" data-title="1984" data-author="George Orwell">
                <img src="https://via.placeholder.com/150" alt="1984">
                <h3>1984</h3>
                <p>George Orwell</p>
                <button class="btn-add">Ajouter au panier</button>
            </div>

            <!-- Ajouter d'autres livres ici -->
        </section>
        
        <section class="cart">
            <h2>Mon Panier</h2>
            <ul id="cart-list">
                <!-- Les livres ajoutés au panier apparaîtront ici -->
            </ul>
        </section>
    </main>

    <footer>
        <p>&copy; 2025 Librairie en Ligne</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f9;
    color: #333;
    padding: 20px;
}

header {
    text-align: center;
    margin-bottom: 40px;
}

header h1 {
    color: #4CAF50;
}

.book-list {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    margin-bottom: 40px;
}

.book-card {
    background-color: white;
    border: 1px solid #ddd;
    padding: 15px;
    text-align: center;
    width: 200px;
    margin: 10px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.book-card img {
    width: 100%;
    height: auto;
    margin-bottom: 10px;
}

.book-card h3 {
    font-size: 18px;
    color: #333;
}

.book-card p {
    color: #777;
}

.btn-add {
    background-color: #4CAF50;
    color: white;
    border: none;
    padding: 10px;
    width: 100%;
    cursor: pointer;
    border-radius: 4px;
    font-size: 16px;
}

.btn-add:hover {
    background-color: #45a049;
}

.cart {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

footer {
    text-align: center;
    margin-top: 40px;
    color: #777;
}
// Sélection des éléments
const addButtons = document.querySelectorAll('.btn-add');
const cartList = document.getElementById('cart-list');

// Fonction pour ajouter un livre au panier
addButtons.forEach(button => {
    button.addEventListener('click', function () {
        const bookCard = button.closest('.book-card');
        const title = bookCard.dataset.title;
        const author = bookCard.dataset.author;

        const listItem = document.createElement('li');
        listItem.textContent = `${title} de ${author}`;
        cartList.appendChild(listItem);
    });
});





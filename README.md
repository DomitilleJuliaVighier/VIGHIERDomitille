<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Librairie en ligne</title>
    <style>
        /* Styles généraux */
        body {
            font-family: Arial, sans-serif;
            background-color: #FADADD; /* Changer la couleur de fond ici */
            margin: 0;
            padding: 0;
        }

        header {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 1rem;
        }

        #search-bar {
            margin-top: 10px;
            padding: 0.5rem;
            font-size: 1rem;
            width: 80%;
            border: 2px solid #ddd;
            border-radius: 5px;
        }

        /* Liste des livres */
        #book-list {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
            padding: 20px;
        }

        .book {
            background-color: white;
            margin: 10px;
            padding: 15px;
            border-radius: 5px;
            width: 200px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .book img {
            width: 100%;
            height: auto;
            border-radius: 5px;
        }

        .book h3 {
            font-size: 1.2rem;
            color: #333;
        }

        .book p {
            font-size: 0.9rem;
            color: #555;
        }

        .book button {
            background-color: #333;
            color: white;
            border: none;
            padding: 5px 10px;
            margin-top: 10px;
            cursor: pointer;
            border-radius: 5px;
            font-size: 0.9rem;
        }

        .book button:hover {
            background-color: #555;
        }
    </style>
</head>
<body>
    <header>
        <h1>Librairie en ligne</h1>
        <input type="text" id="search-bar" placeholder="Rechercher un livre...">
    </header>

    <div id="book-list"></div>

    <script>
        // Liste des livres avec leurs informations (titre, auteur, description, image de couverture)
        const books = [
            {
                title: 'Le Petit Prince',
                author: 'Antoine de Saint-Exupéry',
                description: 'Un pilote rencontre un enfant qui lui raconte son histoire d\'explorateur.',
                cover: 'assets/cover1.jpg'
            },
            {
                title: '1984',
                author: 'George Orwell',
                description: 'Un roman dystopique sur la surveillance de l\'Etat et la manipulation des masses.',
                cover: 'assets/cover2.jpg'
            },
            {
                title: 'Harry Potter à l\'école des sorciers',
                author: 'J.K. Rowling',
                description: 'L\'histoire de Harry, un jeune sorcier qui découvre qu\'il est spécial.',
                cover: 'assets/cover3.jpg'
            }
        ];

        // Fonction pour afficher les livres
        function displayBooks(filteredBooks) {
            const bookList = document.getElementById('book-list');
            bookList.innerHTML = ''; // Vide la liste actuelle
            filteredBooks.forEach(book => {
                const bookElement = document.createElement('div');
                bookElement.classList.add('book');
                bookElement.innerHTML = `
                    <img src="${book.cover}" alt="Couverture de ${book.title}">
                    <h3>${book.title}</h3>
                    <p>Auteur: ${book.author}</p>
                    <p>${book.description}</p>
                    <button>Ajouter au panier</button>
                `;
                bookList.appendChild(bookElement);
            });
        }

        // Fonction pour filtrer les livres en fonction de la recherche
        document.getElementById('search-bar').addEventListener('input', (event) => {
            const searchTerm = event.target.value.toLowerCase();
            const filteredBooks = books.filter(book =>
                book.title.toLowerCase().includes(searchTerm) || book.author.toLowerCase().includes(searchTerm)
            );
            displayBooks(filteredBooks);
        });

        // Affiche tous les livres au départ
        displayBooks(books);
    </script>
</body>
</html>



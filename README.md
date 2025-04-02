# VIGHIERDomitille
/*
Project Structure:

/online-bookstore
  ├── /client (React frontend)
  ├── /server (Node.js + Express backend)
  ├── package.json
  ├── README.md
*/

// Backend (server/index.js)
const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');

const app = express();
app.use(express.json());
app.use(cors());

mongoose.connect('mongodb://localhost:27017/bookstore', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

const BookSchema = new mongoose.Schema({
  title: String,
  author: String,
  price: Number,
});
const Book = mongoose.model('Book', BookSchema);

app.get('/books', async (req, res) => {
  const books = await Book.find();
  res.json(books);
});

app.post('/books', async (req, res) => {
  const book = new Book(req.body);
  await book.save();
  res.json(book);
});

app.delete('/books/:id', async (req, res) => {
  await Book.findByIdAndDelete(req.params.id);
  res.json({ message: 'Book deleted' });
});

app.listen(5000, () => console.log('Server running on port 5000'));

// Frontend (client/src/App.js)
import React, { useEffect, useState } from 'react';

const App = () => {
  const [books, setBooks] = useState([]);
  const [title, setTitle] = useState('');
  const [author, setAuthor] = useState('');
  const [price, setPrice] = useState('');

  useEffect(() => {
    fetch('http://localhost:5000/books')
      .then(res => res.json())
      .then(data => setBooks(data));
  }, []);

  const addBook = async () => {
    const newBook = { title, author, price: Number(price) };
    const res = await fetch('http://localhost:5000/books', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(newBook),
    });
    const data = await res.json();
    setBooks([...books, data]);
  };

  return (
    <div>
      <h1>Online Bookstore</h1>
      <input placeholder='Title' onChange={(e) => setTitle(e.target.value)} />
      <input placeholder='Author' onChange={(e) => setAuthor(e.target.value)} />
      <input placeholder='Price' type='number' onChange={(e) => setPrice(e.target.value)} />
      <button onClick={addBook}>Add Book</button>
      <ul>
        {books.map(book => (
          <li key={book._id}>{book.title} - {book.author} - ${book.price}</li>
        ))}
      </ul>
    </div>
  );
};


 

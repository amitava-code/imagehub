# 📸 ImageHub

A simple full-stack image-sharing app — upload an image with a caption, and view all posts. Built with **Express + MongoDB** on the backend and **React (Vite)** on the frontend, with image hosting powered by **ImageKit**.

> ⚠️ This project is in early development — the upload form and post feed are still being wired up on the frontend.

---

## ✨ Features

- 🖼️ Upload an image + caption to create a post
- ☁️ Images are stored on **ImageKit** (not on your server's disk)
- 🗂️ Post metadata (image URL + caption) saved in **MongoDB**
- ⚡ Fast, modern frontend powered by **Vite + React 19**
- 🧭 Client-side routing with **React Router**

---

## 🏗️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Node.js, Express 5 |
| Database | MongoDB (via Mongoose) |
| File Uploads | Multer (in-memory storage) |
| Image Hosting | ImageKit |
| Frontend | React 19, Vite, React Router |

---

## 📁 Project Structure

```
imagehub/
├── server.js                   # App entry point — starts the server & DB connection
├── src/
│   ├── app.js                  # Express app & API routes
│   ├── config/
│   │   └── db.js               # MongoDB connection logic
│   ├── models/
│   │   └── post.model.js       # Mongoose schema for a Post
│   └── services/
│       └── storage.service.js  # Uploads image buffers to ImageKit
└── Frontend/
    ├── src/
    │   ├── App.jsx              # Route definitions
    │   ├── main.jsx             # React entry point
    │   └── pages/
    │       └── createPost.jsx   # Create-post form
    └── vite.config.js
```

---

## 🔌 API Reference

### Create a post

```
POST /create-post
Content-Type: multipart/form-data
```

| Field | Type | Description |
|---|---|---|
| `image` | File | The image to upload |
| `caption` | String | A caption for the post |

**Response — `201 Created`**
```json
{
  "message": "Post created Successfully",
  "post": {
    "_id": "...",
    "image": "https://ik.imagekit.io/...",
    "caption": "..."
  }
}
```

### Get all posts

```
GET /posts
```

**Response — `200 OK`**
```json
{
  "message": "Post fetced successfully ",
  "posts": [ { "image": "...", "caption": "..." } ]
}
```

---

## 🚀 Getting Started

### Prerequisites

- Node.js (v18+)
- A MongoDB connection string (local or [MongoDB Atlas](https://www.mongodb.com/atlas))
- An [ImageKit](https://imagekit.io/) account & private API key

### 1. Clone the repo

```bash
git clone https://github.com/amitava-code/imagehub.git
cd imagehub
```

### 2. Backend setup

```bash
npm install
```

Create a `.env` file in the project root:

```env
MONGO_URI=your_mongodb_connection_string
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key
```

Start the server:

```bash
node server.js
```

The API will be running at `http://localhost:3000`.

### 3. Frontend setup

```bash
cd Frontend
npm install
npm run dev
```

The frontend will be running at `http://localhost:5173` (Vite's default port).

---


## 🤝 Contributing

This is a personal/learning project, but feel free to open an issue or PR if you spot something worth improving!



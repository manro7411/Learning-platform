
## 1. Create the main project folder

```bash
mkdir my-learning-platform
cd my-learning-platform
```

---

## 2. Set up the Frontend (React + TypeScript + Vite)

```bash
npm create vite@latest frontend -- --template react-ts
cd frontend
npm install
cd ..
```

---

## 3. Set up the Backend (Node.js + Express + TypeScript)

```bash
mkdir backend
cd backend
npm init -y
npm install express cors
npm install --save-dev typescript ts-node-dev @types/node @types/express
npx tsc --init
```

Create a file `src/index.ts` for backend code:

```ts
// backend/src/index.ts
import express from "express";
import cors from "cors";

const app = express();
app.use(cors());
app.use(express.json());

app.get("/", (req, res) => {
  res.json({ message: "Hello from Backend!" });
});

const PORT = 5000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

Add this to `package.json` in your backend:

```json
"scripts": {
  "dev": "ts-node-dev src/index.ts"
}
```

Run the backend:

```bash
npm run dev
```

---

## 4. Connect Frontend to Backend

* Open `frontend/src/App.tsx` and add:

```tsx
import { useEffect, useState } from 'react';

function App() {
  const [msg, setMsg] = useState('');

  useEffect(() => {
    fetch('http://localhost:5000/')
      .then(res => res.json())
      .then(data => setMsg(data.message));
  }, []);

  return (
    <div>
      <h1>BBL Learn Hub</h1>
      <p>Backend says: {msg}</p>
    </div>
  );
}
export default App;
```

---

## 5. Folder Structure Summary

```
my-learning-platform/
│
├── frontend/   ← React + Vite + TypeScript
│
└── backend/    ← Node.js + Express + TypeScript
```

---

## 6. How to Run the Project

Open 2 terminals:

   `cd backend && npm run dev`
   `cd frontend && npm run dev`
Open your browser at [http://localhost:5173](http://localhost:5173) (frontend)
Backend API will respond at [http://localhost:5000](http://localhost:5000)

---

## 7. (Optional) Add .env for configuration and security**

Frontend: Create `.env` for `BASE_API_URL`, etc.
Backend: Create `.env` for `SECRET`, `DB_URL`, etc.

---

### If you want to add auth, a database, or more features, just let me know!

For example: MongoDB/Firebase integration, more routes, login/quiz pages, etc.

---


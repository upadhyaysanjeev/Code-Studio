# Code-Studio

A collaborative, real-time code editor where multiple users can join a room (via a unique room ID) and code together simultaneously. Code-Studio supports multi-file projects, live presence, chat, collaborative drawing, and in-editor code execution — everything you need for pair-programming, teaching, or group coding sessions.

---

## 🔮 Features

* Real-time collaborative code editing across multiple files and folders
* Create, open, edit, save, delete, and organize files and folders
* Download the entire workspace as a ZIP file
* Unique room generation with shareable room IDs for collaboration
* Broad language support with syntax highlighting and auto-language detection
* Execute code directly from the editor (integrates with code execution backends)
* Instant synchronization of edits across all participants
* Join/leave notifications and user presence list (online/offline)
* Real-time group chat
* Live tooltips showing who is editing which file/line
* Auto-suggestions based on the current programming language
* Customizable editor (font family, font size, themes)
* Collaborative drawing/sketchboard for diagrams and UI brainstorming
* AI Assistant (Copilot) to generate or modify code snippets within files

---

## Live Preview

If a demo is available, replace the placeholder below with your deployment URL.

`https://your-live-preview.example.com`

---

## Tech Stack

Typical stack used for projects like Code-Studio (adapt to your implementation):

* Frontend: React + TypeScript, React Router, Tailwind CSS (or similar)
* Backend: Node.js, Express
* Real-time: Socket.IO (or WebRTC / similar)
* Code Execution: Piston or any code-execution API / sandboxed runner
* Deployment: Vercel / Netlify (frontend), any Node host / Docker (backend)
* Containerization: Docker (optional)

---

## ⚙️ Installation

### Method 1 — Manual (local development)

1. **Fork or clone this repository**

   ```bash
   git clone https://github.com/<your-username>/Code-Studio.git
   cd Code-Studio
   ```

2. **Create `.env` files**

   * In the `client` directory create `.env`:

     ```bash
     VITE_BACKEND_URL=http://localhost:3000
     ```

   * In the `server` directory create `.env`:

     ```bash
     PORT=3000
     ```

3. **Install dependencies**

   ```bash
   # From project root or in each service folder
   cd client
   npm install

   cd ../server
   npm install
   ```

4. **Start development servers**

   ```bash
   # Frontend
   cd client
   npm run dev

   # Backend
   cd ../server
   npm run dev
   ```

5. **Open the app**

   ```
   http://localhost:5173
   ```

---

### Method 2 — Docker (recommended for isolated runs)

1. **Build images locally**

   ```bash
   # From repository root
   docker build -t code-studio-server ./server
   docker build -t code-studio-client ./client
   ```

2. **Run containers**

   ```bash
   docker run -d -p 3000:3000 --name code-studio-server code-studio-server
   docker run -d -p 5173:5173 --name code-studio-client code-studio-client
   ```

3. **Or use docker-compose**

   Create a `docker-compose.yml` in the project root:

   ```yaml
   version: '3.8'
   services:
     server:
       build: ./server
       ports:
         - "3000:3000"
       environment:
         - PORT=3000

     client:
       build: ./client
       ports:
         - "5173:5173"
       environment:
         - VITE_BACKEND_URL=http://server:3000
       depends_on:
         - server
   ```

   Then run:

   ```bash
   docker compose up --build
   ```

---

## 🛠️ Configuration & Notes

* Ensure the code execution backend (Piston or similar) is reachable and sandboxed for security. Never run untrusted code on an exposed host without strict sandboxing.
* If using a third-party code-execution API, store API keys in the server `.env` and never commit secrets to the repo.
* For production deployments, enable HTTPS, configure CORS properly, and consider horizontal scaling for socket servers (use a shared pub/sub such as Redis for socket clustering).

---

## 🔮 Planned / Next-release Features

* Admin roles and permission system (room owners, moderators)
* Persistent projects (save workspaces to user accounts)
* File history and versioning / undo across sessions
* Voice/video calling support for pair-programming
* Better RBAC and organization features for teams

---

## 🤝 Contributing

Contributions are welcome! Please follow these general steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feat/your-feature`
3. Make your changes and add tests where appropriate
4. Commit and push: `git push origin feat/your-feature`
5. Open a pull request describing the change

Refer to `CONTRIBUTING.md` (if present) for repository-specific guidelines.

---

## 📦 License

This project is released under the MIT License. See the `LICENSE` file for details.

---

## 🙏 Acknowledgements

Thanks to the open-source projects and libraries that make implementations like Code-Studio possible, including code execution backends, realtime libraries, and collaborative drawing tools.

---

If you want, I can also:

* produce a `docker-compose.yml` tuned to your repo layout,
* generate `env.example` files for client & server, or
* provide a short CONTRIBUTING.md template.

Which one should I create first?

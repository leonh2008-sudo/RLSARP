// ==============================
// VERCEL READY NEXT.JS PROJECT
// ==============================
// ANLEITUNG:
// 1. Gehe auf https://github.com
// 2. Neues Repository erstellen (z.B. rp-server-website)
// 3. Lade ALLE diese Dateien hoch
// 4. Danach auf https://vercel.com -> Import Project
// 5. Fertig 🚀

// ==============================
// package.json
// ==============================
{
  "name": "rp-server-website",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  },
  "dependencies": {
    "next": "latest",
    "react": "latest",
    "react-dom": "latest",
    "framer-motion": "latest",
    "lucide-react": "latest"
  }
}

// ==============================
// next.config.js
// ==============================
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
};

module.exports = nextConfig;

// ==============================
// app/layout.js
// ==============================
export const metadata = {
  title: "Eclipse RP",
  description: "Moderne Roleplay Server Website",
};

import "./globals.css";

export default function RootLayout({ children }) {
  return (
    <html lang="de">
      <body>{children}</body>
    </html>
  );
}

// ==============================
// app/globals.css
// ==============================
body {
  margin: 0;
  font-family: system-ui, sans-serif;
  background: linear-gradient(135deg, #020617, #0f172a);
  color: white;
}

nav {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  border-bottom: 1px solid #1e293b;
  position: sticky;
  top: 0;
  background: rgba(2,6,23,0.9);
  backdrop-filter: blur(10px);
}

nav a {
  margin-left: 20px;
  text-decoration: none;
  color: #cbd5e1;
  font-weight: 600;
}

nav a:hover {
  color: white;
}

.container {
  max-width: 1100px;
  margin: auto;
  padding: 60px 20px;
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.card {
  background: #0f172a;
  border: 1px solid #1e293b;
  border-radius: 20px;
  padding: 20px;
  transition: 0.2s;
}

.card:hover {
  transform: translateY(-5px);
}

button {
  padding: 12px 22px;
  border-radius: 14px;
  border: none;
  background: #2563eb;
  color: white;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  background: #1d4ed8;
}

footer {
  text-align: center;
  padding: 30px;
  border-top: 1px solid #1e293b;
  color: #94a3b8;
}

// ==============================
// components/Navbar.js
// ==============================
import Link from "next/link";

export default function Navbar() {
  return (
    <nav>
      <h2>Eclipse RP</h2>
      <div>
        <Link href="/">Home</Link>
        <Link href="/server">Server</Link>
        <Link href="/regeln">Regeln</Link>
        <Link href="/community">Community</Link>
      </div>
    </nav>
  );
}

// ==============================
// app/page.js (HOME)
// ==============================
import Navbar from "../components/Navbar";

export default function Home() {
  return (
    <>
      <Navbar />

      <div className="container">
        <h1 style={{fontSize:"48px"}}>Willkommen auf Eclipse RP</h1>
        <p style={{color:"#94a3b8"}}>
          Tauche ein in eine realistische Roleplay Welt mit aktiver Community
          und spannenden Storylines.
        </p>

        <div style={{marginTop:"30px"}}>
          <button>Jetzt beitreten</button>
        </div>
      </div>

      <footer>© {new Date().getFullYear()} Eclipse RP</footer>
    </>
  );
}

// ==============================
// app/server/page.js
// ==============================
import Navbar from "../../components/Navbar";

export default function Server() {
  return (
    <>
      <Navbar />

      <div className="container">
        <h1>Server Informationen</h1>

        <div className="card-grid">
          <div className="card">
            <h3>200 Slots</h3>
            <p>Spiele mit vielen anderen Spielern gleichzeitig.</p>
          </div>

          <div className="card">
            <h3>Eigene Scripts</h3>
            <p>Einzigartige Features, die du sonst nirgendwo findest.</p>
          </div>

          <div className="card">
            <h3>Aktive Admins</h3>
            <p>Unser Team ist täglich für euch da.</p>
          </div>
        </div>
      </div>

      <footer>© {new Date().getFullYear()} Eclipse RP</footer>
    </>
  );
}

// ==============================
// app/regeln/page.js
// ==============================
import Navbar from "../../components/Navbar";

export default function Regeln() {
  const rules = [
    "Respektvoller Umgang mit allen Spielern",
    "Kein Metagaming oder Powergaming",
    "Roleplay steht immer im Vordergrund",
    "Den Anweisungen des Teams ist Folge zu leisten",
  ];

  return (
    <>
      <Navbar />

      <div className="container">
        <h1>Server Regeln</h1>

        <div className="card-grid">
          {rules.map((rule, i) => (
            <div className="card" key={i}>{rule}</div>
          ))}
        </div>
      </div>

      <footer>© {new Date().getFullYear()} Eclipse RP</footer>
    </>
  );
}

// ==============================
// app/community/page.js
// ==============================
import Navbar from "../../components/Navbar";

export default function Community() {
  return (
    <>
      <Navbar />

      <div className="container">
        <h1>Community</h1>

        <div className="card-grid">
          <div className="card">
            <h3>Discord</h3>
            <p>Tritt unserer Community bei!</p>
            <button>Discord öffnen</button>
          </div>

          <div className="card">
            <h3>Support</h3>
            <p>Wir helfen dir jederzeit.</p>
            <button>Support kontaktieren</button>
          </div>
        </div>
      </div>

      <footer>© {new Date().getFullYear()} Eclipse RP</footer>
    </>
  );
}

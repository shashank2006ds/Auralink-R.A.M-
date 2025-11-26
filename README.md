# Auralink-R.A.M-
RNSIT
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Auralink | UniLife Sync Dashboard</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <!-- React & Babel CDN -->
    <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <style>
      :root {
        --bg: #0f172a;
        --bg-soft: #111827;
        --bg-softer: #020617;
        --card: #020617;
        --border: rgba(148, 163, 184, 0.3);
        --accent: #38bdf8;
        --accent-soft: rgba(56, 189, 248, 0.12);
        --accent-strong: rgba(56, 189, 248, 0.3);
        --accent-secondary: #a855f7;
        --text: #f9fafb;
        --muted: #9ca3af;
        --danger: #ef4444;
        --success: #22c55e;
        --warning: #facc15;
      }

      [data-theme="light"] {
        --bg: #f3f4f6;
        --bg-soft: #e5e7eb;
        --bg-softer: #e5e7eb;
        --card: #ffffff;
        --border: rgba(148, 163, 184, 0.4);
        --accent: #2563eb;
        --accent-soft: rgba(37, 99, 235, 0.1);
        --accent-strong: rgba(37, 99, 235, 0.3);
        --accent-secondary: #7c3aed;
        --text: #111827;
        --muted: #6b7280;
      }

      * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }

      body {
        margin: 0;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
          sans-serif;
        background: radial-gradient(circle at top left, #1d283a, var(--bg));
        color: var(--text);
      }

      .app-shell {
        display: flex;
        min-height: 100vh;
      }

      /* Sidebar */
      .sidebar {
        width: 260px;
        background: linear-gradient(to bottom, #020617, #020617, #020617dd);
        border-right: 1px solid var(--border);
        padding: 20px 18px;
        display: flex;
        flex-direction: column;
        position: sticky;
        top: 0;
      }

      .logo {
        display: flex;
        align-items: center;
        gap: 10px;
        margin-bottom: 24px;
      }

      .logo-icon {
        width: 40px;
        height: 40px;
        border-radius: 999px;
        background: radial-gradient(circle at 20% 20%, #38bdf8, #0ea5e9 40%, #020617);
        display: flex;
        align-items: center;
        justify-content: center;
        box-shadow: 0 0 25px rgba(56, 189, 248, 0.55);
        color: white;
        font-weight: 700;
        font-size: 18px;
      }

      .logo-text {
        display: flex;
        flex-direction: column;
      }

      .logo-title {
        font-weight: 700;
        letter-spacing: 0.03em;
        font-size: 18px;
      }

      .logo-subtitle {
        font-size: 11px;
        color: var(--muted);
      }

      .sidebar-section-title {
        font-size: 12px;
        color: var(--muted);
        text-transform: uppercase;
        letter-spacing: 0.08em;
        margin: 12px 6px 4px;
      }

      .nav-list {
        list-style: none;
        margin-top: 6px;
      }

      .nav-item {
        margin-bottom: 4px;
      }

      .nav-button {
        width: 100%;
        border-radius: 999px;
        border: 1px solid transparent;
        padding: 9px 12px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        background: transparent;
        color: var(--muted);
        cursor: pointer;
        font-size: 13px;
        transition: all 0.18s ease-out;
      }

      .nav-button-main {
        border-radius: 14px;
      }

      .nav-button-active {
        background: linear-gradient(to right, var(--accent-soft), transparent);
        border-color: var(--accent-strong);
        color: var(--text);
        box-shadow: 0 0 0 1px rgba(15, 23, 42, 0.9), 0 0 18px rgba(56, 189, 248, 0.3);
      }

      .nav-label-wrap {
        display: flex;
        align-items: center;
        gap: 8px;
      }

      .nav-dot {
        width: 8px;
        height: 8px;
        border-radius: 999px;
        background: var(--accent);
        box-shadow: 0 0 10px rgba(56, 189, 248, 0.9);
      }

      .nav-icon-circle {
        width: 20px;
        height: 20px;
        border-radius: 999px;
        border: 1px solid var(--border);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 11px;
      }

      .nav-pill {
        font-size: 10px;
        padding: 3px 7px;
        border-radius: 999px;
        background: rgba(15, 23, 42, 0.85);
        border: 1px solid var(--border);
        color: var(--muted);
      }

      .nav-pill-primary {
        background: var(--accent-soft);
        color: var(--accent);
        border-color: var(--accent-strong);
      }

      .nav-pill-danger {
        background: rgba(239, 68, 68, 0.15);
        color: var(--danger);
        border-color: rgba(239, 68, 68, 0.4);
      }

      .sidebar-footer {
        margin-top: auto;
        padding-top: 16px;
        border-top: 1px solid rgba(30, 64, 175, 0.6);
      }

      .profile-card {
        border-radius: 14px;
        border: 1px solid var(--border);
        padding: 10px 12px;
        background: radial-gradient(circle at top left, #1f2937, #020617);
      }

      .profile-row {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 8px;
      }

      .profile-avatar {
        width: 28px;
        height: 28px;
        border-radius: 999px;
        background: linear-gradient(135deg, #38bdf8, #a855f7);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 14px;
        font-weight: 700;
      }

      .profile-meta {
        display: flex;
        flex-direction: column;
        font-size: 11px;
      }

      .profile-meta span:first-child {
        font-weight: 500;
      }

      .profile-meta span:last-child {
        color: var(--muted);
        font-size: 10px;
      }

      .badge-soft {
        border-radius: 999px;
        padding: 3px 8px;
        border: 1px solid rgba(148, 163, 184, 0.7);
        font-size: 10px;
        color: var(--muted);
      }

      .text-xs {
        font-size: 11px;
      }

      .mt-2 {
        margin-top: 8px;
      }

      .link {
        border: none;
        background: none;
        padding: 0;
        margin: 0;
        cursor: pointer;
        color: var(--accent);
        font-size: 11px;
        text-decoration: underline;
      }

      /* Main content */
      .main {
        flex: 1;
        padding: 20px;
        max-width: 1120px;
        margin: 0 auto;
      }

      .top-row {
        display: flex;
        justify-content: space-between;
        align-items: center;
        gap: 12px;
        margin-bottom: 16px;
      }

      .top-title-wrap {
        display: flex;
        flex-direction: column;
        gap: 4px;
      }

      .top-eyebrow {
        text-transform: uppercase;
        letter-spacing: 0.18em;
        font-size: 11px;
        color: var(--muted);
      }

      .top-title {
        font-size: 24px;
        font-weight: 700;
        display: flex;
        align-items: center;
        gap: 8px;
      }

      .top-dot {
        width: 8px;
        height: 8px;
        border-radius: 999px;
        background: #22c55e;
        box-shadow: 0 0 12px rgba(34, 197, 94, 0.8);
      }

      .top-subtitle {
        font-size: 12px;
        color: var(--muted);
      }

      .top-actions {
        display: flex;
        align-items: center;
        gap: 8px;
      }

      .btn {
        border-radius: 999px;
        border: 1px solid var(--border);
        background: rgba(15, 23, 42, 0.6);
        color: var(--text);
        padding: 8px 12px;
        font-size: 12px;
        display: inline-flex;
        align-items: center;
        gap: 6px;
        cursor: pointer;
        transition: all 0.18s ease-out;
      }

      .btn:hover {
        border-color: var(--accent-strong);
      }

      .btn-primary {
        background: radial-gradient(circle at top left, var(--accent), var(--accent-secondary));
        border-color: transparent;
        box-shadow: 0 10px 25px rgba(15, 23, 42, 0.8);
      }

      .btn-icon-circle {
        width: 18px;
        height: 18px;
        border-radius: 999px;
        border: 1px solid rgba(15, 23, 42, 0.2);
        background: rgba(15, 23, 42, 0.3);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 11px;
      }

      .theme-toggle {
        position: relative;
        width: 46px;
        height: 22px;
        border-radius: 999px;
        border: 1px solid var(--border);
        background: rgba(15, 23, 42, 0.7);
        display: flex;
        align-items: center;
        padding: 2px;
        cursor: pointer;
      }

      .theme-toggle-knob {
        width: 18px;
        height: 18px;
        border-radius: 999px;
        background: var(--accent);
        transform: translateX(0);
        transition: transform 0.18s ease-out;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 10px;
        color: white;
      }

      .theme-toggle[data-mode="light"] .theme-toggle-knob {
        transform: translateX(22px);
      }

      .theme-toggle-labels {
        position: absolute;
        inset: 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 6px;
        font-size: 10px;
        color: var(--muted);
        pointer-events: none;
      }

      .theme-toggle-labels span {
        opacity: 0.8;
      }

      /* Hero */
      .hero {
        border-radius: 20px;
        border: 1px solid rgba(148, 163, 184, 0.4);
        background:
          radial-gradient(circle at top left, rgba(56, 189, 248, 0.18), transparent 55%),
          radial-gradient(circle at bottom right, rgba(168, 85, 247, 0.22), transparent 55%),
          linear-gradient(135deg, var(--bg-soft), var(--bg-softer));
        padding: 18px 18px;
        margin-bottom: 16px;
        display: grid;
        grid-template-columns: minmax(0, 2.1fr) minmax(0, 1.4fr);
        gap: 16px;
        position: relative;
        overflow: hidden;
      }

      .hero::before {
        content: "";
        position: absolute;
        inset: -80px;
        background: radial-gradient(circle at 20% 0, rgba(56, 189, 248, 0.18), transparent 66%);
        opacity: 0.9;
        pointer-events: none;
      }

      .hero-main {
        position: relative;
        z-index: 1;
      }

      .hero-kicker {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        border-radius: 999px;
        padding: 3px 8px;
        font-size: 10px;
        background: rgba(15, 23, 42, 0.7);
        border: 1px solid rgba(148, 163, 184, 0.6);
        margin-bottom: 8px;
      }

      .hero-kicker span {
        color: var(--accent);
        font-weight: 500;
      }

      .hero-title {
        font-size: 20px;
        font-weight: 700;
        margin-bottom: 4px;
      }

      .hero-subtitle {
        font-size: 12px;
        color: var(--muted);
        max-width: 420px;
      }

      .hero-metrics {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        margin: 14px 0;
      }

      .metric-pill {
        border-radius: 999px;
        padding: 6px 9px;
        font-size: 11px;
        border: 1px solid rgba(148, 163, 184, 0.6);
        background: rgba(15, 23, 42, 0.7);
        display: inline-flex;
        align-items: center;
        gap: 6px;
      }

      .metric-dot {
        width: 8px;
        height: 8px;
        border-radius: 999px;
      }

      .metric-dot.green {
        background: var(--success);
        box-shadow: 0 0 10px rgba(34, 197, 94, 0.9);
      }

      .metric-dot.red {
        background: var(--danger);
        box-shadow: 0 0 10px rgba(239, 68, 68, 0.9);
      }

      .metric-dot.blue {
        background: var(--accent);
        box-shadow: 0 0 10px rgba(56, 189, 248, 0.9);
      }

      .hero-cta-row {
        display: flex;
        gap: 8px;
        margin-top: 6px;
        flex-wrap: wrap;
      }

      .hero-secondary-link {
        font-size: 11px;
        color: var(--muted);
        display: inline-flex;
        align-items: center;
        gap: 5px;
      }

      .hero-secondary-link span {
        text-decoration: underline;
        cursor: pointer;
      }

      .hero-right {
        position: relative;
        z-index: 1;
        display: flex;
        align-items: stretch;
        justify-content: flex-end;
      }

      .sphere {
        width: 140px;
        height: 140px;
        border-radius: 999px;
        background:
          radial-gradient(circle at 20% 10%, #e0f2fe, transparent 55%),
          conic-gradient(from 180deg, #38bdf8, #22c55e, #a855f7, #38bdf8);
        position: relative;
        box-shadow:
          0 0 40px rgba(56, 189, 248, 0.65),
          0 20px 40px rgba(15, 23, 42, 0.95);
        display: flex;
        align-items: center;
        justify-content: center;
        overflow: hidden;
      }

      .sphere-inner {
        width: 110px;
        height: 110px;
        border-radius: 999px;
        border: 1px solid rgba(15, 23, 42, 0.3);
        background: radial-gradient(circle at 30% 20%, #e5f2ff, #0f172a);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 11px;
        color: #e5f2ff;
        text-align: center;
        padding: 12px;
      }

      .sphere-orbit {
        position: absolute;
        inset: 8px;
        border-radius: 999px;
        border: 1px dashed rgba(15, 23, 42, 0.4);
      }

      .sphere-tag {
        position: absolute;
        top: -6px;
        right: -4px;
        border-radius: 999px;
        padding: 4px 8px;
        font-size: 10px;
        background: rgba(15, 23, 42, 0.9);
        border: 1px solid rgba(148, 163, 184, 0.7);
      }

      .sphere-chip {
        position: absolute;
        bottom: 6px;
        left: -8px;
        border-radius: 999px;
        padding: 4px 8px;
        font-size: 10px;
        background: rgba(15, 23, 42, 0.9);
        border: 1px solid rgba(148, 163, 184, 0.7);
      }

      .hero-spark {
        position: absolute;
        width: 9px;
        height: 9px;
        border-radius: 999px;
        background: #38bdf8;
        box-shadow: 0 0 12px rgba(56, 189, 248, 0.88);
      }

      .hero-spark.one {
        top: 6px;
        left: -5px;
      }

      .hero-spark.two {
        bottom: 10px;
        right: 0;
      }

      /* Layout below hero */
      .grid-2 {
        display: grid;
        grid-template-columns: minmax(0, 1.7fr) minmax(0, 1.3fr);
        gap: 14px;
        margin-bottom: 14px;
      }

      .grid-3 {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 12px;
        margin-bottom: 14px;
      }

      @media (max-width: 960px) {
        .app-shell {
          flex-direction: column;
        }

        .sidebar {
          width: 100%;
          flex-direction: row;
          overflow-x: auto;
          position: static;
        }

        .sidebar-section-title,
        .sidebar-footer {
          display: none;
        }

        .nav-button {
          white-space: nowrap;
        }

        .main {
          padding: 14px;
        }

        .hero {
          grid-template-columns: minmax(0, 1fr);
        }

        .grid-2,
        .grid-3 {
          grid-template-columns: minmax(0, 1fr);
        }
      }

      /* Cards */
      .card {
        border-radius: 16px;
        border: 1px solid var(--border);
        background: rgba(15, 23, 42, 0.9);
        padding: 13px 12px;
      }

      [data-theme="light"] .card {
        background: var(--card);
      }

      .card-header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 8px;
      }

      .card-title {
        font-size: 13px;
        font-weight: 600;
        display: flex;
        align-items: center;
        gap: 8px;
      }

      .card-title-icon {
        width: 22px;
        height: 22px;
        border-radius: 999px;
        border: 1px solid var(--border);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 12px;
      }

      .card-sub {
        font-size: 11px;
        color: var(--muted);
      }

      .pill {
        font-size: 10px;
        padding: 3px 7px;
        border-radius: 999px;
        border: 1px solid rgba(148, 163, 184, 0.6);
        background: rgba(15, 23, 42, 0.7);
      }

      .pill.green {
        border-color: rgba(34, 197, 94, 0.6);
        color: #bbf7d0;
        background: rgba(22, 163, 74, 0.12);
      }

      .pill.red {
        border-color: rgba(239, 68, 68, 0.6);
        color: #fecaca;
        background: rgba(220, 38, 38, 0.14);
      }

      .pill.blue {
        border-color: var(--accent-strong);
        color: var(--accent);
        background: var(--accent-soft);
      }

      .pill.amber {
        border-color: rgba(234, 179, 8, 0.7);
        color: #facc15;
        background: rgba(251, 191, 36, 0.10);
      }

      .list {
        list-style: none;
        margin: 0;
        padding: 0;
      }

      .list-item {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 8px;
        padding: 6px 0;
        border-bottom: 1px dashed rgba(148, 163, 184, 0.4);
      }

      .list-item:last-child {
        border-bottom: none;
      }

      .list-main {
        display: flex;
        flex-direction: column;
        gap: 3px;
      }

      .list-title {
        font-size: 12px;
      }

      .list-meta {
        font-size: 11px;
        color: var(--muted);
      }

      .progress-track {
        width: 100%;
        height: 5px;
        border-radius: 999px;
        background: rgba(30, 64, 175, 0.45);
        overflow: hidden;
      }

      .progress-bar {
        height: 100%;
        border-radius: 999px;
        background: linear-gradient(to right, var(--accent), var(--accent-secondary));
      }

      .switch {
        position: relative;
        width: 40px;
        height: 20px;
        border-radius: 999px;
        background: rgba(15, 23, 42, 0.8);
        border: 1px solid var(--border);
        display: flex;
        align-items: center;
        padding: 2px;
        cursor: pointer;
      }

      .switch-knob {
        width: 16px;
        height: 16px;
        border-radius: 999px;
        background: var(--muted);
        transform: translateX(0);
        transition: transform 0.16s ease-out, background 0.16s ease-out;
      }

      .switch[data-on="true"] .switch-knob {
        transform: translateX(18px);
        background: var(--accent);
      }

      /* Inputs */
      .input-row {
        display: flex;
        gap: 6px;
        margin-top: 6px;
      }

      .input {
        flex: 1;
        border-radius: 999px;
        border: 1px solid rgba(148, 163, 184, 0.7);
        background: rgba(15, 23, 42, 0.8);
        padding: 6px 10px;
        font-size: 11px;
        color: var(--text);
      }

      [data-theme="light"] .input {
        background: white;
      }

      .input::placeholder {
        color: var(--muted);
      }

      .chip-row {
        display: flex;
        flex-wrap: wrap;
        gap: 6px;
        margin-top: 6px;
      }

      .chip {
        font-size: 10px;
        padding: 4px 7px;
        border-radius: 999px;
        border: 1px solid rgba(148, 163, 184, 0.6);
        background: rgba(15, 23, 42, 0.7);
      }

      .sos-banner {
        display: flex;
        align-items: center;
        gap: 12px;
        padding: 10px;
        border-radius: 14px;
        background: radial-gradient(circle at left, rgba(239, 68, 68, 0.25), transparent 55%);
        border: 1px solid rgba(248, 113, 113, 0.7);
        margin-top: 6px;
      }

      .sos-button {
        border-radius: 999px;
        border: none;
        padding: 9px 16px;
        font-size: 12px;
        font-weight: 600;
        letter-spacing: 0.03em;
        text-transform: uppercase;
        cursor: pointer;
        background: radial-gradient(circle at top left, #fecaca, #ef4444);
        color: #111827;
        box-shadow: 0 0 22px rgba(248, 113, 113, 0.85);
      }

      .sos-pulse {
        width: 24px;
        height: 24px;
        border-radius: 999px;
        border: 2px solid rgba(248, 113, 113, 0.9);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 12px;
        position: relative;
      }

      .sos-pulse::after {
        content: "";
        position: absolute;
        inset: -3px;
        border-radius: inherit;
        border: 1px solid rgba(248, 113, 113, 0.6);
        opacity: 0.8;
      }

      .toast {
        position: fixed;
        right: 14px;
        bottom: 14px;
        border-radius: 12px;
        padding: 9px 11px;
        background: rgba(15, 23, 42, 0.95);
        border: 1px solid rgba(56, 189, 248, 0.55);
        font-size: 11px;
        color: var(--text);
        display: flex;
        align-items: center;
        gap: 8px;
        z-index: 50;
      }

      .toast-pill {
        width: 18px;
        height: 18px;
        border-radius: 999px;
        border: 1px solid rgba(56, 189, 248, 0.6);
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 11px;
      }
    </style>
  </head>
  <body>
    <div id="root"></div>

    <script type="text/babel">
      const { useState, useEffect } = React;

      const MODULES = [
        "Dashboard",
        "Tasks & Reminders",
        "Bills & Expenses",
        "Grocery Manager",
        "Health Tracker",
        "Document Vault",
        "IoT & Smart Home",
        "Family Mode",
        "Govt. Schemes",
        "SOS & Safety",
      ];

      function App() {
        const [activeModule, setActiveModule] = useState("Dashboard");
        const [theme, setTheme] = useState("dark");

        const [tasks, setTasks] = useState([
          { id: 1, title: "Pay electricity bill", when: "Today, 7:00 PM", tag: "Bills" },
          { id: 2, title: "Family grocery run", when: "Sat, 11:00 AM", tag: "Grocery" },
          { id: 3, title: "Medicine refill", when: "Tomorrow, 6:30 PM", tag: "Health" },
        ]);

        const [newTask, setNewTask] = useState("");

        const [groceries, setGroceries] = useState([
          { id: 1, name: "Milk", qty: "2L" },
          { id: 2, name: "Rice", qty: "5kg" },
          { id: 3, name: "Eggs", qty: "12" },
        ]);
        const [newGrocery, setNewGrocery] = useState("");

        const [bills, setBills] = useState([
          { id: 1, name: "Electricity", due: "Today", amount: "₹1,250", status: "Due" },
          { id: 2, name: "Wi-Fi", due: "3 days", amount: "₹799", status: "Upcoming" },
          { id: 3, name: "DTH", due: "7 days", amount: "₹499", status: "Upcoming" },
        ]);

        const [health, setHealth] = useState({
          steps: 6240,
          goal: 8000,
          waterGlasses: 5,
          sleepHours: 7.2,
        });

        const [iot, setIot] = useState({
          lights: true,
          doorLocked: true,
          acOn: false,
        });

        const [sosAlert, setSosAlert] = useState(null);

        // keep theme on body
        useEffect(() => {
          document.documentElement.setAttribute("data-theme", theme);
        }, [theme]);

        const toggleTheme = () => {
          setTheme((prev) => (prev === "dark" ? "light" : "dark"));
        };

        const addTask = () => {
          if (!newTask.trim()) return;
          setTasks((prev) => [
            { id: Date.now(), title: newTask.trim(), when: "Custom reminder", tag: "Personal" },
            ...prev,
          ]);
          setNewTask("");
        };

        const addGrocery = () => {
          if (!newGrocery.trim()) return;
          setGroceries((prev) => [
            { id: Date.now(), name: newGrocery.trim(), qty: "1x" },
            ...prev,
          ]);
          setNewGrocery("");
        };

        const triggerSOS = () => {
          setSosAlert("SOS triggered: family and emergency contacts notified!");
          setTimeout(() => setSosAlert(null), 3500);
        };

        const completion = Math.min(
          100,
          Math.round(
            ((tasks.length ? 2 : 1) +
              (bills.filter((b) => b.status !== "Due").length ? 1 : 0) +
              (health.steps > 5000 ? 1 : 0)) *
              16
          )
        );

        const renderModule = () => {
          switch (activeModule) {
            case "Dashboard":
              return (
                <Dashboard
                  tasks={tasks}
                  bills={bills}
                  health={health}
                  groceries={groceries}
                  completion={completion}
                  iot={iot}
                  setActiveModule={setActiveModule}
                />
              );
            case "Tasks & Reminders":
              return (
                <TasksModule
                  tasks={tasks}
                  newTask={newTask}
                  setNewTask={setNewTask}
                  addTask={addTask}
                />
              );
            case "Grocery Manager":
              return (
                <GroceryModule
                  groceries={groceries}
                  newGrocery={newGrocery}
                  setNewGrocery={setNewGrocery}
                  addGrocery={addGrocery}
                />
              );
            case "Bills & Expenses":
              return <BillsModule bills={bills} />;
            case "Health Tracker":
              return <HealthModule health={health} setHealth={setHealth} />;
            case "Document Vault":
              return <DocumentModule />;
            case "IoT & Smart Home":
              return <IotModule iot={iot} setIot={setIot} />;
            case "Family Mode":
              return <FamilyModule />;
            case "Govt. Schemes":
              return <GovtModule />;
            case "SOS & Safety":
              return <SosModule triggerSOS={triggerSOS} />;
            default:
              return null;
          }
        };

        const today = new Date();
        const formattedDate = today.toLocaleDateString("en-IN", {
          weekday: "short",
          day: "2-digit",
          month: "short",
        });

        return (
          <>
            <div className="app-shell">
              <aside className="sidebar">
                <div>
                  <div className="logo">
                    <div className="logo-icon">A</div>
                    <div className="logo-text">
                      <span className="logo-title">Auralink</span>
                      <span className="logo-subtitle">UniLife Sync • Home OS</span>
                    </div>
                  </div>

                  <div className="sidebar-section-title">Navigation</div>
                  <ul className="nav-list">
                    {MODULES.map((m) => (
                      <li key={m} className="nav-item">
                        <button
                          className={
                            "nav-button nav-button-main " +
                            (activeModule === m ? "nav-button-active" : "")
                          }
                          onClick={() => setActiveModule(m)}
                        >
                          <span className="nav-label-wrap">
                            <span className="nav-icon-circle">
                              {m === "Dashboard" ? "◎" : m[0]}
                            </span>
                            <span>{m}</span>
                          </span>
                          {m === "Dashboard" && (
                            <span className="nav-pill nav-pill-primary">{formattedDate}</span>
                          )}
                          {m === "SOS & Safety" && (
                            <span className="nav-pill nav-pill-danger">SOS</span>
                          )}
                        </button>
                      </li>
                    ))}
                  </ul>
                </div>

                <div className="sidebar-footer">
                  <div className="profile-card">
                    <div className="profile-row">
                      <div className="profile-row">
                        <div className="profile-avatar">R</div>
                        <div className="profile-meta">
                          <span>R.A.M Household</span>
                          <span>Smart home in sync</span>
                        </div>
                      </div>
                      <span className="badge-soft">Family Space</span>
                    </div>
                    <div className="mt-2 text-xs">
                      Daily automation score: <strong>{completion}%</strong>
                    </div>
                    <button
                      className="link"
                      onClick={() => setActiveModule("Family Mode")}
                      style={{ marginTop: 4 }}
                    >
                      Open family workspace →
                    </button>
                  </div>
                </div>
              </aside>

              <main className="main">
                <div className="top-row">
                  <div className="top-title-wrap">
                    <div className="top-eyebrow">
                      Unified Life & Home • Context-aware Daily OS
                    </div>
                    <div className="top-title">
                      <span>Good to see you, R.A.M</span>
                      <span className="top-dot" />
                    </div>
                    <div className="top-subtitle">
                      One place for tasks, bills, health, docs, IoT and family coordination.
                    </div>
                  </div>

                  <div className="top-actions">
                    <button className="btn">
                      <div className="btn-icon-circle">✦</div>
                      Quick Add
                    </button>
                    <button
                      className="btn btn-primary"
                      onClick={() => setActiveModule("Tasks & Reminders")}
                    >
                      <div className="btn-icon-circle">↗</div>
                      Plan Today
                    </button>
                    <div
                      className="theme-toggle"
                      data-mode={theme}
                      onClick={toggleTheme}
                      title="Toggle light/dark"
                    >
                      <div className="theme-toggle-knob">
                        {theme === "dark" ? "☾" : "☀"}
                      </div>
                      <div className="theme-toggle-labels">
                        <span>☾</span>
                        <span>☀</span>
                      </div>
                    </div>
                  </div>
                </div>

                <Hero completion={completion} />

                {renderModule()}
              </main>
            </div>

            {sosAlert && (
              <div className="toast">
                <div className="toast-pill">!</div>
                <span>{sosAlert}</span>
              </div>
            )}
          </>
        );
      }

      const Hero = ({ completion }) => {
        return (
          <section className="hero">
            <div className="hero-main">
              <div className="hero-kicker">
                <span>Live Sync</span>
                <span style={{ color: "#9ca3af" }}>Bills • Health • Docs • IoT</span>
              </div>
              <h2 className="hero-title">Simplify life, one unified rhythm at a time.</h2>
              <p className="hero-subtitle">
                Auralink keeps your bills, routines, health, documents and home devices in
                one calm, intelligent view. Less app-hopping, more peace of mind.
              </p>

              <div className="hero-metrics">
                <div className="metric-pill">
                  <span className="metric-dot green" />
                  <span>Household flow score</span>
                  <strong>{completion}%</strong>
                </div>
                <div className="metric-pill">
                  <span className="metric-dot.red metric-dot red" />
                  <span>Missed bills this month</span>
                  <strong>0</strong>
                </div>
                <div className="metric-pill">
                  <span className="metric-dot.blue metric-dot blue" />
                  <span>Automation routines</span>
                  <strong>6 active</strong>
                </div>
              </div>

              <div className="hero-cta-row">
                <button className="btn btn-primary">
                  <div className="btn-icon-circle">⚡</div>
                  Start UniLife Sync
                </button>
                <div className="hero-secondary-link">
                  Or
                  <span>preview today&apos;s schedule</span>↗
                </div>
              </div>
            </div>

            <div className="hero-right">
              <div className="sphere">
                <div className="sphere-orbit" />
                <div className="sphere-inner">
                  UniLife Sync orchestrates{" "}
                  <strong>tasks, bills, health & devices</strong> into one calm timeline.
                </div>
                <div className="sphere-tag">AI Copilot · Home</div>
                <div className="sphere-chip">Family mode linked</div>
                <div className="hero-spark one" />
                <div className="hero-spark two" />
              </div>
            </div>
          </section>
        );
      };

      const Dashboard = ({ tasks, bills, health, groceries, completion, iot, setActiveModule }) => {
        const nextBill = bills.find((b) => b.status === "Due") || bills[0];
        const hydrationPercent = Math.min(100, Math.round((health.waterGlasses / 8) * 100));
        const stepsPercent = Math.min(100, Math.round((health.steps / health.goal) * 100));

        return (
          <>
            <section className="grid-2">
              <div className="card">
                <div className="card-header">
                  <div>
                    <div className="card-title">
                      <div className="card-title-icon">📋</div>
                      Today at a glance
                    </div>
                    <div className="card-sub">Your synced responsibilities for the day.</div>
                  </div>
                  <span className="pill blue">{tasks.length} active reminders</span>
                </div>
                <ul className="list">
                  {tasks.slice(0, 3).map((t) => (
                    <li key={t.id} className="list-item">
                      <div className="list-main">
                        <span className="list-title">{t.title}</span>
                        <span className="list-meta">
                          {t.when} • <strong>{t.tag}</strong>
                        </span>
                      </div>
                      <span className="pill.green pill green">In sync</span>
                    </li>
                  ))}
                </ul>
                <button
                  className="link"
                  style={{ marginTop: 4 }}
                  onClick={() => setActiveModule("Tasks & Reminders")}
                >
                  View all tasks →
                </button>
              </div>

              <div className="card">
                <div className="card-header">
                  <div>
                    <div className="card-title">
                      <div className="card-title-icon">🏠</div>
                      Home status
                    </div>
                    <div className="card-sub">Quick snapshot of automation & safety.</div>
                  </div>
                  <span className="pill green">Stable</span>
                </div>
                <ul className="list">
                  <li className="list-item">
                    <div className="list-main">
                      <span className="list-title">Smart devices</span>
                      <span className="list-meta">
                        Lights {iot.lights ? "on" : "off"} • Door{" "}
                        {iot.doorLocked ? "locked" : "unlocked"} • AC{" "}
                        {iot.acOn ? "on" : "off"}
                      </span>
                    </div>
                    <button
                      className="pill"
                      onClick={() => setActiveModule("IoT & Smart Home")}
                    >
                      Manage
                    </button>
                  </li>
                  <li className="list-item">
                    <div className="list-main">
                      <span className="list-title">Next bill</span>
                      <span className="list-meta">
                        {nextBill.name} • {nextBill.amount} • Due: {nextBill.due}
                      </span>
                    </div>
                    <span className="pill.amber pill amber">Remind me</span>
                  </li>
                  <li className="list-item">
                    <div className="list-main">
                      <span className="list-title">Safety & SOS</span>
                      <span className="list-meta">
                        SOS ready • Emergency contacts online
                      </span>
                    </div>
                    <button
                      className="pill.red pill red"
                      onClick={() => setActiveModule("SOS & Safety")}
                    >
                      Open SOS
                    </button>
                  </li>
                </ul>
              </div>
            </section>

            <section className="grid-3">
              <div className="card">
                <div className="card-header">
                  <div>
                    <div className="card-title">
                      <div className="card-title-icon">💳</div>
                      Bills & renewals
                    </div>
                    <div className="card-sub">Stay ahead of monthly payments.</div>
                  </div>
                  <span className="pill">
                    {bills.filter((b) => b.status === "Due").length} due today
                  </span>
                </div>
                <ul className="list">
                  {bills.slice(0, 3).map((b) => (
                    <li key={b.id} className="list-item">
                      <div className="list-main">
                        <span className="list-title">{b.name}</span>
                        <span className="list-meta">
                          {b.amount} • {b.status} in {b.due}
                        </span>
                      </div>
                      <span
                        className={
                          "pill " + (b.status === "Due" ? "red" : "amber")
                        }
                      >
                        {b.status}
                      </span>
                    </li>
                  ))}
                </ul>
              </div>

              <div className="card">
                <div className="card-header">
                  <div>
                    <div className="card-title">
                      <div className="card-title-icon">🫗</div>
                      Health snapshot
                    </div>
                    <div className="card-sub">Tiny nudges for daily well-being.</div>
                  </div>
                  <span className="pill green">On track</span>
                </div>
                <div style={{ fontSize: 12 }}>
                  <div style={{ marginBottom: 4 }}>
                    Steps: <strong>{health.steps.toLocaleString()}</strong> /{" "}
                    {health.goal.toLocaleString()}
                  </div>
                  <div className="progress-track" style={{ marginBottom: 8 }}>
                    <div
                      className="progress-bar"
                      style={{ width: stepsPercent + "%" }}
                    />
                  </div>
                  <div style={{ marginBottom: 4 }}>
                    Hydration: <strong>{health.waterGlasses} glasses</strong> / 8
                  </div>
                  <div className="progress-track" style={{ marginBottom: 8 }}>
                    <div
                      className="progress-bar"
                      style={{ width: hydrationPercent + "%" }}
                    />
                  </div>
                  <div>
                    Sleep last night: <strong>{health.sleepHours} hrs</strong>
                  </div>
                </div>
              </div>

              <div className="card">
                <div className="card-header">
                  <div>
                    <div className="card-title">
                      <div className="card-title-icon">🛒</div>
                      Quick grocery panel
                    </div>
                    <div className="card-sub">Essential items linked to your tasks.</div>
                  </div>
                  <span className="pill blue">{groceries.length} items</span>
                </div>
                <ul className="list">
                  {groceries.slice(0, 3).map((g) => (
                    <li key={g.id} className="list-item">
                      <div className="list-main">
                        <span className="list-title">{g.name}</span>
                        <span className="list-meta">{g.qty}</span>
                      </div>
                      <span className="pill">Ready</span>
                    </li>
                  ))}
                </ul>
              </div>
            </section>

            <section className="card">
              <div className="card-header">
                <div>
                  <div className="card-title">
                    <div className="card-title-icon">📊</div>
                    UniLife Sync timeline
                  </div>
                  <div className="card-sub">
                    Visual cue of how much of your life is currently running on autopilot.
                  </div>
                </div>
                <span className="pill blue">Automation level: {completion}%</span>
              </div>
              <div className="progress-track" style={{ height: 12, marginBottom: 6 }}>
                <div
                  className="progress-bar"
                  style={{ width: completion + "%", borderRadius: 999 }}
                />
              </div>
              <div
                style={{
                  display: "flex",
                  justifyContent: "space-between",
                  fontSize: 11,
                  color: "var(--muted)",
                  marginTop: 2,
                }}
              >
                <span>Manual chaos</span>
                <span>Calm automation</span>
              </div>
            </section>
          </>
        );
      };

      const TasksModule = ({ tasks, newTask, setNewTask, addTask }) => {
        return (
          <section className="card" style={{ marginBottom: 16 }}>
            <div className="card-header">
              <div>
                <div className="card-title">
                  <div className="card-title-icon">📋</div>
                  Tasks & reminders
                </div>
                <div className="card-sub">
                  Plan household chores, bills, and personal routines in one view.
                </div>
              </div>
              <span className="pill blue">{tasks.length} total</span>
            </div>
            <div className="input-row">
              <input
                className="input"
                value={newTask}
                onChange={(e) => setNewTask(e.target.value)}
                placeholder="Add a new reminder — e.g. 'Renew gas connection on Friday'"
                onKeyDown={(e) => e.key === "Enter" && addTask()}
              />
              <button className="btn btn-primary" onClick={addTask}>
                <div className="btn-icon-circle">＋</div>
                Add
              </button>
            </div>
            <ul className="list" style={{ marginTop: 8 }}>
              {tasks.map((t) => (
                <li key={t.id} className="list-item">
                  <div className="list-main">
                    <span className="list-title">{t.title}</span>
                    <span className="list-meta">
                      {t.when} • <strong>{t.tag}</strong>
                    </span>
                  </div>
                  <span className="pill green">On</span>
                </li>
              ))}
            </ul>
          </section>
        );
      };

      const GroceryModule = ({
        groceries,
        newGrocery,
        setNewGrocery,
        addGrocery,
      }) => {
        return (
          <section className="card" style={{ marginBottom: 16 }}>
            <div className="card-header">
              <div>
                <div className="card-title">
                  <div className="card-title-icon">🛒</div>
                  Grocery manager
                </div>
                <div className="card-sub">
                  Link pantry items to reminders and avoid last-minute runs.
                </div>
              </div>
              <span className="pill blue">{groceries.length} tracked items</span>
            </div>
            <div className="input-row">
              <input
                className="input"
                value={newGrocery}
                onChange={(e) => setNewGrocery(e.target.value)}
                placeholder="Add grocery item — e.g. 'Cooking oil 1L'"
                onKeyDown={(e) => e.key === "Enter" && addGrocery()}
              />
              <button className="btn btn-primary" onClick={addGrocery}>
                <div className="btn-icon-circle">＋</div>
                Add
              </button>
            </div>
            <ul className="list" style={{ marginTop: 8 }}>
              {groceries.map((g) => (
                <li key={g.id} className="list-item">
                  <div className="list-main">
                    <span className="list-title">{g.name}</span>
                    <span className="list-meta">{g.qty}</span>
                  </div>
                  <span className="pill">In list</span>
                </li>
              ))}
            </ul>
          </section>
        );
      };

      const BillsModule = ({ bills }) => (
        <section className="card" style={{ marginBottom: 16 }}>
          <div className="card-header">
            <div>
              <div className="card-title">
                <div className="card-title-icon">💳</div>
                Bills & expenses
              </div>
              <div className="card-sub">
                Track utilities, subscriptions and household expenses without juggling
                multiple apps.
              </div>
            </div>
            <span className="pill blue">Unified hub</span>
          </div>
          <ul className="list">
            {bills.map((b) => (
              <li key={b.id} className="list-item">
                <div className="list-main">
                  <span className="list-title">{b.name}</span>
                  <span className="list-meta">
                    {b.amount} • Due in {b.due}
                  </span>
                </div>
                <span className={"pill " + (b.status === "Due" ? "red" : "amber")}>
                  {b.status}
                </span>
              </li>
            ))}
          </ul>
          <div className="chip-row">
            <div className="chip">Electricity</div>
            <div className="chip">Wi-Fi</div>
            <div className="chip">DTH</div>
            <div className="chip">Rent</div>
            <div className="chip">Streaming apps</div>
          </div>
        </section>
      );

      const HealthModule = ({ health, setHealth }) => {
        const stepsPercent = Math.min(100, Math.round((health.steps / health.goal) * 100));
        const hydrationPercent = Math.min(
          100,
          Math.round((health.waterGlasses / 8) * 100)
        );

        const bumpWater = () =>
          setHealth((h) => ({ ...h, waterGlasses: Math.min(8, h.waterGlasses + 1) }));
        const bumpSteps = () =>
          setHealth((h) => ({ ...h, steps: h.steps + 500 }));

        return (
          <section className="card" style={{ marginBottom: 16 }}>
            <div className="card-header">
              <div>
                <div className="card-title">
                  <div className="card-title-icon">🫀</div>
                  Health & well-being tracker
                </div>
                <div className="card-sub">
                  Micro-habits across steps, hydration and sleep — right next to your
                  routine.
                </div>
              </div>
              <span className="pill green">Gentle nudges</span>
            </div>
            <div style={{ fontSize: 12, display: "grid", gap: 8 }}>
              <div>
                <div style={{ marginBottom: 4 }}>
                  Steps:
                  <strong> {health.steps.toLocaleString()}</strong> /{" "}
                  {health.goal.toLocaleString()}
                </div>
                <div className="progress-track">
                  <div
                    className="progress-bar"
                    style={{ width: stepsPercent + "%" }}
                  />
                </div>
                <button className="link" style={{ marginTop: 4 }} onClick={bumpSteps}>
                  +500 steps logged
                </button>
              </div>
              <div>
                <div style={{ marginBottom: 4 }}>
                  Water:
                  <strong> {health.waterGlasses} glasses</strong> / 8
                </div>
                <div className="progress-track">
                  <div
                    className="progress-bar"
                    style={{ width: hydrationPercent + "%" }}
                  />
                </div>
                <button className="link" style={{ marginTop: 4 }} onClick={bumpWater}>
                  +1 glass of water
                </button>
              </div>
              <div>
                Last night&apos;s sleep: <strong>{health.sleepHours} hours</strong>
              </div>
            </div>
          </section>
        );
      };

      const DocumentModule = () => (
        <section className="card" style={{ marginBottom: 16 }}>
          <div className="card-header">
            <div>
              <div className="card-title">
                <div className="card-title-icon">📂</div>
                Document vault
              </div>
              <div className="card-sub">
                Store IDs, policies and bills in a secure digital vault with smart
                expiry reminders.
              </div>
            </div>
            <span className="pill blue">End-to-end encrypted</span>
          </div>
          <ul className="list">
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Aadhaar & PAN cards</span>
                <span className="list-meta">
                  Linked to KYC tasks & bank reminders.
                </span>
              </div>
              <span className="pill">Pinned</span>
            </li>
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Insurance policies</span>
                <span className="list-meta">
                  Auto-renew reminders 30 days before expiry.
                </span>
              </div>
              <span className="pill amber">Expiring in 47 days</span>
            </li>
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">College / office docs</span>
                <span className="list-meta">
                  On-device fallback • Cloud backup enabled.
                </span>
              </div>
              <span className="pill green">Safe</span>
            </li>
          </ul>
        </section>
      );

      const IotModule = ({ iot, setIot }) => (
        <section className="card" style={{ marginBottom: 16 }}>
          <div className="card-header">
            <div>
              <div className="card-title">
                <div className="card-title-icon">🌐</div>
                IoT & Smart home control
              </div>
              <div className="card-sub">
                Control lights, AC and door locks from the same place you manage tasks.
              </div>
            </div>
            <span className="pill blue">ESP32 • Google Home • Alexa</span>
          </div>
          <ul className="list">
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Lights</span>
                <span className="list-meta">
                  Living room & kitchen grouped as &quot;Evening routine&quot;
                </span>
              </div>
              <div
                className="switch"
                data-on={iot.lights}
                onClick={() => setIot((s) => ({ ...s, lights: !s.lights }))}
              >
                <div className="switch-knob" />
              </div>
            </li>
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Door lock</span>
                <span className="list-meta">
                  Auto-lock enabled when everyone leaves home.
                </span>
              </div>
              <div
                className="switch"
                data-on={iot.doorLocked}
                onClick={() => setIot((s) => ({ ...s, doorLocked: !s.doorLocked }))}
              >
                <div className="switch-knob" />
              </div>
            </li>
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">AC</span>
                <span className="list-meta">
                  Linked with heatwave alerts and peak-hour billing.
                </span>
              </div>
              <div
                className="switch"
                data-on={iot.acOn}
                onClick={() => setIot((s) => ({ ...s, acOn: !s.acOn }))}
              >
                <div className="switch-knob" />
              </div>
            </li>
          </ul>
          <div className="chip-row">
            <div className="chip">Routines: Morning</div>
            <div className="chip">Routines: Sleep</div>
            <div className="chip">Presence-based</div>
            <div className="chip">Energy saver</div>
          </div>
        </section>
      );

      const FamilyModule = () => (
        <section className="card" style={{ marginBottom: 16 }}>
          <div className="card-header">
            <div>
              <div className="card-title">
                <div className="card-title-icon">👨‍👩‍👧‍👦</div>
                Family mode
              </div>
              <div className="card-sub">
                Shared boards, chores and safety for everyone living under one roof.
              </div>
            </div>
            <span className="pill green">3 members online</span>
          </div>
          <ul className="list">
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Shared board</span>
                <span className="list-meta">
                  &quot;This week&quot; tasks and announcements in one place.
                </span>
              </div>
              <span className="pill blue">Open</span>
            </li>
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Chore rotation</span>
                <span className="list-meta">
                  Fair rotation for dishes, trash and pet care.
                </span>
              </div>
              <span className="pill">Balanced</span>
            </li>
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Location pings</span>
                <span className="list-meta">
                  Soft check-ins like &quot;Reached college&quot; or &quot;On way home&quot;.
                </span>
              </div>
              <span className="pill green">Healthy</span>
            </li>
          </ul>
        </section>
      );

      const GovtModule = () => (
        <section className="card" style={{ marginBottom: 16 }}>
          <div className="card-header">
            <div>
              <div className="card-title">
                <div className="card-title-icon">🏛️</div>
                Govt. scheme updates
              </div>
              <div className="card-sub">
                Link scholarships, subsidies and welfare schemes to your real household
                data.
              </div>
            </div>
            <span className="pill amber">Context-aware</span>
          </div>
          <ul className="list">
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Electricity subsidy check</span>
                <span className="list-meta">
                  Eligible based on your usage and address details.
                </span>
              </div>
              <span className="pill blue">View</span>
            </li>
            <li className="list-item">
              <div className="list-main">
                <span className="list-title">Education scholarship reminder</span>
                <span className="list-meta">
                  Deadline in 9 days • Docs auto-pulled from vault.
                </span>
              </div>
              <span className="pill amber">Apply</span>
            </li>
          </ul>
        </section>
      );

      const SosModule = ({ triggerSOS }) => (
        <section className="card" style={{ marginBottom: 16 }}>
          <div className="card-header">
            <div>
              <div className="card-title">
                <div className="card-title-icon">🛑</div>
                SOS & emergency safety
              </div>
              <div className="card-sub">
                One tap to notify family, neighbours and emergency services with your
                live context.
              </div>
            </div>
            <span className="pill.red pill red">Always ready</span>
          </div>
          <div className="sos-banner">
            <div className="sos-pulse">!</div>
            <div style={{ fontSize: 12 }}>
              <div>
                SOS is mapped to{" "}
                <strong>family group, trusted neighbours and local helplines</strong>.
              </div>
              <div style={{ color: "var(--muted)", marginTop: 2 }}>
                Trigger only in real emergencies. Auralink will broadcast SMS + push
                alerts with your live status.
              </div>
            </div>
            <button className="sos-button" onClick={triggerSOS}>
              Trigger SOS
            </button>
          </div>
          <div className="chip-row">
            <div className="chip">Long-press power button</div>
            <div className="chip">Geo-tagged</div>
            <div className="chip">Medical notes</div>
          </div>
        </section>
      );

      ReactDOM.createRoot(document.getElementById("root")).render(<App />);
    </script>
  </body>
</html>

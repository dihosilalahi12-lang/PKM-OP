<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kasir Indomaret x One Piece</title>
    <style>
        :root {
            --indomaret-blue: #00529C;
            --indomaret-red: #ED1C24;
            --indomaret-yellow: #FFC20E;
            --bg-dark: #0f172a;
            --card-bg: #1e293b;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, sans-serif;
        }

        body {
            background-color: var(--bg-dark);
            color: #ffffff;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        /* HEADER */
        header {
            background: linear-gradient(135deg, var(--indomaret-blue), #002e59);
            padding: 15px;
            text-align: center;
            border-bottom: 4px solid var(--indomaret-yellow);
            position: relative;
        }

        header h1 {
            font-size: 1.4rem;
            color: #fff;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        /* NAVIGASI MENU (ANDROID FRIENDLY) */
        nav {
            display: flex;
            overflow-x: auto;
            background: #090d16;
            padding: 10px;
            gap: 10px;
            scrollbar-width: none;
        }

        nav::-webkit-scrollbar {
            display: none;
        }

        .nav-btn {
            flex: 0 0 auto;
            background: #1e293b;
            color: #ccc;
            border: 1px solid #334155;
            padding: 8px 14px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }

        .nav-btn.active {
            background: var(--indomaret-yellow);
            color: #000;
            border-color: var(--indomaret-yellow);
            box-shadow: 0 0 10px rgba(255, 194, 14, 0.5);
        }

        /* CONTAINER PANEL */
        main {
            flex: 1;
            padding: 15px;
        }

        .panel {
            display: none;
            background: var(--card-bg);
            border-radius: 12px;
            padding: 15px;
            border: 1px solid #334155;
            position: relative;
            overflow: hidden;
        }

        .panel.active {
            display: block;
        }

        /* KARAKTER & ANIMASI KEKUATAN */
        .char-card {
            display: flex;
            align-items: center;
            gap: 15px;
            background: rgba(15, 23, 42, 0.6);
            padding: 10px;
            border-radius: 10px;
            margin-bottom: 15px;
            position: relative;
            overflow: hidden;
        }

        .char-svg {
            width: 70px;
            height: 70px;
            border-radius: 50%;
            background: #334155;
            z-index: 2;
            flex-shrink: 0;
        }

        .char-desc h2 { font-size: 1.1rem; color: var(--indomaret-yellow); }
        .char-desc p { font-size: 0.8rem; color: #94a3b8; }

        /* 1. ZORO: CONTINUOUS SLASH */
        .slash-effect {
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            pointer-events: none;
            background: linear-gradient(45deg, transparent 45%, #22c55e 50%, transparent 55%);
            animation: zoroSlash 1.2s infinite linear;
            opacity: 0.6;
        }
        @keyframes zoroSlash {
            0% { transform: translate(-30%, -30%) rotate(0deg); }
            100% { transform: translate(30%, 30%) rotate(180deg); }
        }

        /* 2. FRANKY: RADICAL BEAM */
        .beam-effect {
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            pointer-events: none;
            background: radial-gradient(circle, rgba(6, 182, 212, 0.3) 0%, transparent 70%);
            animation: frankyBeam 0.8s infinite alternate;
        }
        @keyframes frankyBeam {
            0% { opacity: 0.2; transform: scale(0.8); }
            100% { opacity: 0.8; transform: scale(1.2); }
        }

        /* 3. SANJI: DIABLE JAMBE FIRE */
        .fire-effect {
            position: absolute;
            bottom: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none;
            background: radial-gradient(circle at bottom, rgba(239, 68, 68, 0.4), transparent 60%);
            animation: sanjiFire 1s infinite alternate ease-in-out;
        }
        @keyframes sanjiFire {
            0% { filter: hue-rotate(0deg); opacity: 0.5; }
            100% { filter: hue

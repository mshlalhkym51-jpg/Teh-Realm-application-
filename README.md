<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>بوابة ذا ريلم | The Realm RP</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;800;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-dark: #09090b;
            --card-bg: #121215;
            --red-primary: #dc2626;
            --red-dark: #991b1b;
            --red-glow: rgba(220, 38, 38, 0.28);
            --border-color: rgba(220, 38, 38, 0.32);
            --text-main: #f4f4f5;
            --text-muted: #a1a1aa;
            --ok-bg: rgba(22, 163, 74, 0.14);
            --ok-border: rgba(34, 197, 94, 0.45);
            --ok-text: #86efac;
            --err-bg: rgba(220, 38, 38, 0.16);
            --err-border: rgba(248, 113, 113, 0.48);
            --err-text: #fca5a5;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Cairo', sans-serif;
        }

        html, body {
            width: 100%;
            max-width: 100%;
            overflow-x: hidden;
            background-color: var(--bg-dark);
            color: var(--text-main);
            background-image:
                radial-gradient(circle at 50% 0%, rgba(220, 38, 38, 0.16) 0%, transparent 55%),
                linear-gradient(rgba(220, 38, 38, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(220, 38, 38, 0.03) 1px, transparent 1px);
            background-size: 100% 100%, 28px 28px, 28px 28px;
            min-height: 100vh;
            line-height: 1.6;
            font-size: 13.5px;
        }

        .red-bg-anim {
            position: fixed;
            inset: 0;
            z-index: 0;
            pointer-events: none;
            overflow: hidden;
        }

        .red-orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(56px);
            opacity: 0.36;
            will-change: transform;
        }

        .red-orb-1 {
            width: 310px;
            height: 310px;
            background: radial-gradient(circle, rgba(220, 38, 38, 0.68) 0%, rgba(153, 27, 27, 0) 70%);
            top: -70px;
            right: -60px;
            animation: floatOrb1 14s ease-in-out infinite alternate;
        }

        .red-orb-2 {
            width: 260px;
            height: 260px;
            background: radial-gradient(circle, rgba(239, 68, 68, 0.52) 0%, rgba(127, 29, 29, 0) 70%);
            bottom: 8%;
            left: -70px;
            animation: floatOrb2 17s ease-in-out infinite alternate;
        }

        .red-orb-3 {
            width: 220px;
            height: 220px;
            background: radial-gradient(circle, rgba(185, 28, 28, 0.56) 0%, rgba(69, 10, 10, 0) 70%);
            top: 40%;
            right: 16%;
            animation: floatOrb3 12s ease-in-out infinite alternate;
        }

        .red-ember {
            position: absolute;
            bottom: -14px;
            border-radius: 50%;
            background: rgba(248, 113, 113, 0.8);
            box-shadow: 0 0 10px rgba(220, 38, 38, 0.9);
            animation: riseEmber linear infinite;
            will-change: transform, opacity;
        }

        @keyframes floatOrb1 {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(-45px, 65px) scale(1.15); }
        }

        @keyframes floatOrb2 {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(55px, -50px) scale(1.12); }
        }

        @keyframes floatOrb3 {
            0% { transform: translate(0, 0) scale(0.95); }
            100% { transform: translate(-35px, -45px) scale(1.1); }
        }

        @keyframes riseEmber {
            0% { transform: translateY(0) translateX(0) scale(0.8); opacity: 0; }
            15% { opacity: 0.85; }
            85% { opacity: 0.65; }
            100% { transform: translateY(-108vh) translateX(22px) scale(1.15); opacity: 0; }
        }

        .top-header {
            position: sticky;
            top: 0;
            z-index: 60;
            width: 100%;
            background: rgba(12, 12, 15, 0.96);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border-color);
            padding: 9px 12px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 8px;
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 8px;
            min-width: 0;
        }

        .menu-btn {
            width: 36px;
            height: 36px;
            flex-shrink: 0;
            border-radius: 9px;
            background: #141418;
            border: 1px solid var(--border-color);
            color: #fff;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 4px;
            cursor: pointer;
        }

        .menu-btn span {
            width: 16px;
            height: 2px;
            background: #fff;
            border-radius: 2px;
            display: block;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
            min-width: 0;
        }

        .logo-box {
            width: 32px;
            height: 32px;
            flex-shrink: 0;
            background: linear-gradient(135deg, var(--red-primary), var(--red-dark));
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 900;
            font-size: 0.85rem;
            color: #fff;
            box-shadow: 0 0 12px var(--red-glow);
        }

        .brand-title {
            min-width: 0;
        }

        .brand-title h1 {
            font-size: 0.9rem;
            font-weight: 900;
            line-height: 1.2;
            color: #fff;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .brand-title span {
            display: block;
            font-size: 0.68rem;
            color: var(--text-muted);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .discord-btn {
            background: var(--red-primary);
            color: #fff;
            text-decoration: none;
            padding: 6px 11px;
            border-radius: 8px;
            font-weight: 800;
            font-size: 0.78rem;
            box-shadow: 0 4px 14px var(--red-glow);
            white-space: nowrap;
            flex-shrink: 0;
        }

        .discord-btn:hover {
            background: #b91c1c;
        }

        .drawer-backdrop {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, 0.75);
            z-index: 90;
            display: none;
        }

        .drawer-backdrop.open {
            display: block;
        }

        .side-drawer {
            position: fixed;
            top: 0;
            left: -285px;
            width: 270px;
            max-width: 84vw;
            height: 100vh;
            background: #101014;
            border-right: 1px solid var(--border-color);
            z-index: 100;
            padding: 15px 13px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            transition: left 0.2s ease;
            box-shadow: 10px 0 30px rgba(0, 0, 0, 0.75);
        }

        .side-drawer.open {
            left: 0;
        }

        .drawer-top {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding-bottom: 10px;
            border-bottom: 1px solid #27272a;
            margin-bottom: 12px;
        }

        .drawer-top strong {
            font-size: 0.9rem;
            color: #fff;
        }

        .close-drawer-btn {
            background: #18181c;
            border: 1px solid #27272a;
            color: #fff;
            width: 26px;
            height: 26px;
            border-radius: 7px;
            cursor: pointer;
            font-weight: 700;
            font-size: 0.8rem;
        }

        .nav-list {
            display: flex;
            flex-direction: column;
            gap: 7px;
        }

        .nav-item-btn {
            width: 100%;
            background: #141418;
            border: 1px solid #27272a;
            color: #e4e4e7;
            padding: 9px 11px;
            border-radius: 9px;
            text-align: right;
            font-size: 0.84rem;
            font-weight: 800;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 6px;
        }

        .nav-item-btn:hover,
        .nav-item-btn.active {
            background: rgba(220, 38, 38, 0.16);
            border-color: var(--red-primary);
            color: #fca5a5;
        }

        .drawer-footer-link {
            display: block;
            text-align: center;
            background: var(--red-primary);
            color: #fff;
            text-decoration: none;
            padding: 9px 12px;
            border-radius: 9px;
            font-weight: 800;
            font-size: 0.82rem;
            margin-top: 12px;
        }

        .container {
            position: relative;
            z-index: 2;
            width: 100%;
            max-width: 720px;
            margin: 0 auto;
            padding: 16px 12px 36px;
        }

        .page-view {
            display: none;
        }

        .page-view.active {
            display: block;
        }

        .home-hero {
            background: linear-gradient(180deg, rgba(220, 38, 38, 0.15) 0%, rgba(18, 18, 21, 0.96) 65%);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 28px 16px;
            text-align: center;
            box-shadow: 0 12px 30px rgba(0, 0, 0, 0.5);
        }

        .pill-badge {
            display: inline-block;
            background: rgba(220, 38, 38, 0.16);
            border: 1px solid var(--border-color);
            color: #fca5a5;
            padding: 3px 11px;
            border-radius: 999px;
            font-size: 0.72rem;
            font-weight: 800;
            margin-bottom: 8px;
        }

        .home-hero h2 {
            font-size: 1.35rem;
            font-weight: 900;
            color: #fff;
            margin-bottom: 8px;
        }

        .home-hero h2 span {
            color: var(--red-primary);
        }

        .home-hero p {
            font-size: 0.82rem;
            color: var(--text-muted);
            max-width: 480px;
            margin: 0 auto 18px;
        }

        .enter-server-btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            background: var(--red-primary);
            color: #fff;
            text-decoration: none;
            padding: 11px 24px;
            border-radius: 11px;
            font-size: 0.9rem;
            font-weight: 900;
            box-shadow: 0 6px 18px var(--red-glow);
        }

        .enter-server-btn:hover {
            background: #b91c1c;
        }

        .portal-banner {
            background: linear-gradient(180deg, rgba(220, 38, 38, 0.14) 0%, rgba(18, 18, 21, 0.96) 65%);
            border: 1px solid var(--border-color);
            border-radius: 14px;
            padding: 14px 13px;
            margin-bottom: 12px;
            text-align: center;
        }

        .portal-banner h2 {
            font-size: 1.15rem;
            font-weight: 900;
            margin-bottom: 4px;
            color: #fff;
        }

        .portal-banner h2 span {
            color: var(--red-primary);
        }

        .portal-banner p {
            font-size: 0.78rem;
            color: var(--text-muted);
        }

        .form-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 14px;
            padding: 14px 13px;
            box-shadow: 0 10px 26px rgba(0, 0, 0, 0.45);
        }

        .field-group {
            display: flex;
            flex-direction: column;
            gap: 4px;
            margin-bottom: 10px;
            min-width: 0;
        }

        .field-group label {
            font-size: 0.78rem;
            font-weight: 800;
            color: #f4f4f5;
        }

        .field-hint {
            font-size: 0.68rem;
            color: var(--text-muted);
        }

        .field-input,
        .field-textarea,
        .field-select {
            width: 100%;
            max-width: 100%;
            background: #09090b;
            border: 1px solid #27272a;
            color: #fff;
            padding: 8px 10px;
            border-radius: 9px;
            font-size: 0.82rem;
            outline: none;
        }

        .field-input:focus,
        .field-textarea:focus,
        .field-select:focus {
            border-color: var(--red-primary);
        }

        .field-textarea {
            min-height: 76px;
            resize: vertical;
        }

        .oath-box {
            background: rgba(220, 38, 38, 0.08);
            border: 1px solid rgba(220, 38, 38, 0.35);
            border-radius: 10px;
            padding: 10px 11px;
            margin-bottom: 11px;
        }

        .oath-title {
            font-size: 0.78rem;
            font-weight: 900;
            color: #fca5a5;
            margin-bottom: 6px;
        }

        .oath-options {
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .oath-option {
            display: flex;
            align-items: center;
            gap: 7px;
            background: #09090b;
            border: 1px solid #27272a;
            padding: 7px 10px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.78rem;
            font-weight: 700;
            color: #f4f4f5;
        }

        .oath-option input {
            accent-color: var(--red-primary);
            cursor: pointer;
        }

        .submit-btn {
            width: 100%;
            background: var(--red-primary);
            color: #fff;
            border: none;
            padding: 10px 16px;
            border-radius: 10px;
            font-size: 0.86rem;
            font-weight: 900;
            cursor: pointer;
            box-shadow: 0 5px 16px var(--red-glow);
        }

        .submit-btn:hover:not(:disabled) {
            background: #b91c1c;
        }

        .submit-btn:disabled {
            opacity: 0.65;
            cursor: not-allowed;
        }

        .status-box {
            margin-top: 10px;
            padding: 9px 11px;
            border-radius: 9px;
            font-size: 0.78rem;
            font-weight: 800;
            display: none;
            word-wrap: break-word;
        }

        .status-box.ok {
            display: block;
            background: var(--ok-bg);
            border: 1px solid var(--ok-border);
            color: var(--ok-text);
        }

        .status-box.err {
            display: block;
            background: var(--err-bg);
            border: 1px solid var(--err-border);
            color: var(--err-text);
        }

        footer {
            text-align: center;
            margin-top: 24px;
            padding-top: 10px;
            border-top: 1px solid #27272a;
            color: var(--text-muted);
            font-size: 0.72rem;
        }

        footer span {
            color: var(--red-primary);
            font-weight: 700;
        }
    </style>
</head>
<body>

    <div class="red-bg-anim" aria-hidden="true">
        <div class="red-orb red-orb-1"></div>
        <div class="red-orb red-orb-2"></div>
        <div class="red-orb red-orb-3"></div>
        <span class="red-ember" style="right: 8%; width: 4px; height: 4px; animation-duration: 9s; animation-delay: 0s;"></span>
        <span class="red-ember" style="right: 22%; width: 6px; height: 6px; animation-duration: 12s; animation-delay: -3s;"></span>
        <span class="red-ember" style="right: 36%; width: 3px; height: 3px; animation-duration: 8.5s; animation-delay: -5s;"></span>
        <span class="red-ember" style="right: 52%; width: 5px; height: 5px; animation-duration: 11s; animation-delay: -2s;"></span>
        <span class="red-ember" style="right: 68%; width: 4px; height: 4px; animation-duration: 10s; animation-delay: -6s;"></span>
        <span class="red-ember" style="right: 82%; width: 6px; height: 6px; animation-duration: 13s; animation-delay: -4s;"></span>
        <span class="red-ember" style="right: 91%; width: 3px; height: 3px; animation-duration: 9.5s; animation-delay: -7s;"></span>
    </div>

    <header class="top-header">
        <div class="header-left">
            <button type="button" class="menu-btn" id="menuToggleBtn" aria-label="القائمة" onclick="setDrawerOpen(true)">
                <span></span>
                <span></span>
                <span></span>
            </button>
            <div class="brand" onclick="switchTab('home')">
                <div class="logo-box">TR</div>
                <div class="brand-title">
                    <h1>THE REALM</h1>
                    <span>ذا ريلم • The Realm RP</span>
                </div>
            </div>
        </div>
        <a href="https://discord.gg/re-1" target="_blank" rel="noopener noreferrer" class="discord-btn">دخول السيرفر</a>
    </header>

    <div class="drawer-backdrop" id="drawerBackdrop" onclick="setDrawerOpen(false)"></div>
    <aside class="side-drawer" id="sideDrawer">
        <div>
            <div class="drawer-top">
                <strong>قائمة ذا ريلم</strong>
                <button type="button" class="close-drawer-btn" onclick="setDrawerOpen(false)">✕</button>
            </div>
            <nav class="nav-list">
                <button type="button" class="nav-item-btn active" data-tab="home" onclick="switchTab('home')">
                    <span>الرئيسية</span>
                    <span>←</span>
                </button>
                <button type="button" class="nav-item-btn" data-tab="admin" onclick="switchTab('admin')">
                    <span>تقديم الإدارة</span>
                    <span>←</span>
                </button>
                <button type="button" class="nav-item-btn" data-tab="mod" onclick="switchTab('mod')">
                    <span>تقديم الرقابة</span>
                    <span>←</span>
                </button>
                <button type="button" class="nav-item-btn" data-tab="dev" onclick="switchTab('dev')">
                    <span>تقديم المطورين</span>
                    <span>←</span>
                </button>
                <button type="button" class="nav-item-btn" data-tab="bugs" onclick="switchTab('bugs')">
                    <span>إبلاغ عن مشكلة بالموقع</span>
                    <span>←</span>
                </button>
            </nav>
        </div>
        <a href="https://discord.gg/re-1" target="_blank" rel="noopener noreferrer" class="drawer-footer-link">دخول السيرفر</a>
    </aside>

    <div class="container">

        <section id="tab-home" class="page-view active">
            <div class="home-hero">
                <div class="pill-badge">مرحباً بك في ذا ريلم</div>
                <h2>سيرفر <span>The Realm RP</span></h2>
                <p>افتح القائمة من الشرطات الثلاث للوصول إلى التقديمات والبلاغات.</p>
                <a href="https://discord.gg/re-1" target="_blank" rel="noopener noreferrer" class="enter-server-btn">دخول السيرفر</a>
            </div>
        </section>

        <section id="tab-admin" class="page-view">
            <div class="portal-banner">
                <div class="pill-badge">نموذج رسمي • ذا ريلم</div>
                <h2>تقديم <span>الإدارة</span></h2>
                <p>املأ البيانات التالية بدقة ليتم إرسال طلبك مباشرة إلى روم تقديمات الإدارة.</p>
            </div>

            <form class="form-card" onsubmit="submitStaffApp(event, 'admin', 'تقديم الإدارة')">
                <div class="field-group">
                    <label for="admin-name">الاسم</label>
                    <input type="text" id="admin-name" class="field-input" placeholder="اكتب اسمك هنا" required>
                </div>
                <div class="field-group">
                    <label for="admin-discord">يوزرك بالديسكورد</label>
                    <input type="text" id="admin-discord" class="field-input" placeholder="مثال: username أو @username" required>
                </div>
                <div class="field-group">
                    <label for="admin-age">العمر</label>
                    <input type="number" id="admin-age" class="field-input" min="12" max="99" placeholder="اكتب عمرك هنا" required>
                </div>
                <div class="field-group">
                    <label for="admin-exp">خبراتك السابقة</label>
                    <textarea id="admin-exp" class="field-textarea" placeholder="اذكر خبراتك الإدارية أو الرقابية السابقة..." required></textarea>
                </div>
                <div class="oath-box">
                    <div class="oath-title">هل تقسم بالالتزام بقوانين السيرفر والعدل وعدم استغلال الصلاحيات؟</div>
                    <div class="oath-options">
                        <label class="oath-option">
                            <input type="radio" name="admin-oath" value="إي" required>
                            <span>إي</span>
                        </label>
                        <label class="oath-option">
                            <input type="radio" name="admin-oath" value="لا">
                            <span>لا</span>
                        </label>
                    </div>
                </div>
                <button type="submit" class="submit-btn">إرسال التقديم</button>
                <div id="status-admin" class="status-box"></div>
            </form>
        </section>

        <section id="tab-mod" class="page-view">
            <div class="portal-banner">
                <div class="pill-badge">نموذج رسمي • ذا ريلم</div>
                <h2>تقديم <span>الرقابة</span></h2>
                <p>املأ البيانات التالية بدقة ليتم إرسال طلبك مباشرة إلى روم تقديمات الرقابة.</p>
            </div>

            <form class="form-card" onsubmit="submitStaffApp(event, 'mod', 'تقديم الرقابة')">
                <div class="field-group">
                    <label for="mod-name">الاسم</label>
                    <input type="text" id="mod-name" class="field-input" placeholder="اكتب اسمك هنا" required>
                </div>
                <div class="field-group">
                    <label for="mod-discord">يوزرك بالديسكورد</label>
                    <input type="text" id="mod-discord" class="field-input" placeholder="مثال: username أو @username" required>
                </div>
                <div class="field-group">
                    <label for="mod-age">العمر</label>
                    <input type="number" id="mod-age" class="field-input" min="12" max="99" placeholder="اكتب عمرك هنا" required>
                </div>
                <div class="field-group">
                    <label for="mod-exp">خبراتك السابقة</label>
                    <textarea id="mod-exp" class="field-textarea" placeholder="اذكر خبراتك في الرقابة ومتابعة المخالفات والسيناريوهات..." required></textarea>
                </div>
                <div class="oath-box">
                    <div class="oath-title">هل تقسم بالالتزام بقوانين السيرفر والعدل وعدم استغلال الصلاحيات؟</div>
                    <div class="oath-options">
                        <label class="oath-option">
                            <input type="radio" name="mod-oath" value="إي" required>
                            <span>إي</span>
                        </label>
                        <label class="oath-option">
                            <input type="radio" name="mod-oath" value="لا">
                            <span>لا</span>
                        </label>
                    </div>
                </div>
                <button type="submit" class="submit-btn">إرسال التقديم</button>
                <div id="status-mod" class="status-box"></div>
            </form>
        </section>

        <section id="tab-dev" class="page-view">
            <div class="portal-banner">
                <div class="pill-badge">نموذج رسمي • ذا ريلم</div>
                <h2>تقديم <span>المطورين</span></h2>
                <p>املأ البيانات التالية بدقة ليتم إرسال طلبك مباشرة إلى روم تقديمات المطورين.</p>
            </div>

            <form class="form-card" onsubmit="submitStaffApp(event, 'dev', 'تقديم المطورين')">
                <div class="field-group">
                    <label for="dev-name">الاسم</label>
                    <input type="text" id="dev-name" class="field-input" placeholder="اكتب اسمك هنا" required>
                </div>
                <div class="field-group">
                    <label for="dev-discord">يوزرك بالديسكورد</label>
                    <input type="text" id="dev-discord" class="field-input" placeholder="مثال: username أو @username" required>
                </div>
                <div class="field-group">
                    <label for="dev-age">العمر</label>
                    <input type="number" id="dev-age" class="field-input" min="12" max="99" placeholder="اكتب عمرك هنا" required>
                </div>
                <div class="field-group">
                    <label for="dev-exp">خبراتك السابقة</label>
                    <textarea id="dev-exp" class="field-textarea" placeholder="اذكر خبراتك البرمجية أو التقنية وأعمالك السابقة..." required></textarea>
                </div>
                <div class="oath-box">
                    <div class="oath-title">هل تقسم بالالتزام بقوانين السيرفر والعدل وعدم استغلال الصلاحيات؟</div>
                    <div class="oath-options">
                        <label class="oath-option">
                            <input type="radio" name="dev-oath" value="إي" required>
                            <span>إي</span>
                        </label>
                        <label class="oath-option">
                            <input type="radio" name="dev-oath" value="لا">
                            <span>لا</span>
                        </label>
                    </div>
                </div>
                <button type="submit" class="submit-btn">إرسال التقديم</button>
                <div id="status-dev" class="status-box"></div>
            </form>
        </section>

        <section id="tab-bugs" class="page-view">
            <div class="portal-banner">
                <div class="pill-badge">الدعم التقني • ذا ريلم</div>
                <h2>إبلاغ عن <span>مشكلة بالموقع</span></h2>
                <p>أبلغ عن أي مشكلة في الموقع أو خطأ برمجي ليتم إرساله مباشرة إلى روم البلاغات التقنية.</p>
            </div>

            <form class="form-card" onsubmit="submitBugReport(event)">
                <div class="field-group">
                    <label for="bug-discord">يوزرك بالديسكورد</label>
                    <input type="text" id="bug-discord" class="field-input" placeholder="مثال: username أو @username" required>
                </div>
                <div class="field-group">
                    <label for="bug-type">نوع المشكلة</label>
                    <select id="bug-type" class="field-select" required>
                        <option value="خطأ برمجي (Bug)">خطأ برمجي (Bug)</option>
                        <option value="مشكلة في الأزرار أو التنقل">مشكلة في الأزرار أو التنقل</option>
                        <option value="مشكلة في عرض الجوال أو التصميم">مشكلة في عرض الجوال أو التصميم</option>
                        <option value="مشكلة في إرسال النماذج / الويب هوك">مشكلة في إرسال النماذج / الويب هوك</option>
                        <option value="مشكلة أخرى في الموقع">مشكلة أخرى في الموقع</option>
                    </select>
                </div>
                <div class="field-group">
                    <label for="bug-desc">وصف المشكلة أو الخطأ البرمجي</label>
                    <textarea id="bug-desc" class="field-textarea" placeholder="اشرح المشكلة بالتفصيل وأين ظهرت..." required></textarea>
                    <span class="field-hint">اكتب الخطوات التي أدت إلى المشكلة ليسهل إصلاحها بسرعة.</span>
                </div>
                <button type="submit" class="submit-btn">إرسال البلاغ</button>
                <div id="status-bugs" class="status-box"></div>
            </form>
        </section>

        <footer>
            بوابة التقديم والبلاغات الرسمية لسيرفر <span>ذا ريلم (The Realm RP)</span> &copy; 2026
        </footer>
    </div>

    <script>
        const WEBHOOKS = {
            admin: "https://discord.com/api/webhooks/1574149764444987464/d0tFRfp_mHaHeA0_EBiWk3Frf1Y-KRTk1WiykieiSxcvdVlTz-URSO8s0GRf_ddS-wqq",
            mod: "https://discord.com/api/webhooks/1574149868320985169/L50kLDTivr_EsMropPKG-KcoPP13ZU34Lmcay7oVj5E4u2SS40gBzS634Gj9i3i2FY_U",
            dev: "https://discord.com/api/webhooks/1574149562354892913/I409SMaDuq65XJj7mR3-nriHx8LsGf6SYYDZWm-mLznti9avi87-NwU-pxFsVvdoyspP",
            bugs: "https://discord.com/api/webhooks/1574149964786044938/d4GVSOTe6TQGTqTYh4z-9zMjX8IHzz9NIoaZZW9E6T8RQcRwr21Zvwxs9mzitJHkgLcZ"
        };

        function setDrawerOpen(open) {
            var drawer = document.getElementById('sideDrawer');
            var backdrop = document.getElementById('drawerBackdrop');
            if (drawer) drawer.classList.toggle('open', open);
            if (backdrop) backdrop.classList.toggle('open', open);
        }

        function switchTab(tabName) {
            var views = document.querySelectorAll('.page-view');
            var btns = document.querySelectorAll('.nav-item-btn');

            for (var i = 0; i < views.length; i++) {
                views[i].classList.remove('active');
            }
            var target = document.getElementById('tab-' + tabName);
            if (target) target.classList.add('active');

            for (var j = 0; j < btns.length; j++) {
                btns[j].classList.toggle('active', btns[j].getAttribute('data-tab') === tabName);
            }

            setDrawerOpen(false);
            try {
                window.scrollTo({ top: 0, behavior: 'smooth' });
            } catch (e) {
                window.scrollTo(0, 0);
            }
        }

        function showStatus(id, type, message) {
            var box = document.getElementById(id);
            if (!box) return;
            box.className = 'status-box ' + type;
            box.textContent = message;
        }

        async function postToWebhook(url, payload) {
            var res = await fetch(url, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            });
            if (!res.ok) {
                throw new Error('HTTP ' + res.status);
            }
        }

        async function submitStaffApp(event, key, roleTitle) {
            event.preventDefault();
            var form = event.target;
            var btn = form.querySelector('button[type="submit"]');
            var statusId = 'status-' + key;

            var nameVal = document.getElementById(key + '-name').value.trim();
            var discordVal = document.getElementById(key + '-discord').value.trim();
            var ageVal = document.getElementById(key + '-age').value.trim();
            var expVal = document.getElementById(key + '-exp').value.trim();
            var oathChecked = form.querySelector('input[name="' + key + '-oath"]:checked');

            if (!nameVal || !discordVal || !ageVal || !expVal || !oathChecked) {
                showStatus(statusId, 'err', 'يرجى تعبئة جميع الحقول واختيار إي أو لا على القسم.');
                return;
            }

            var oathVal = oathChecked.value;
            if (oathVal !== 'إي') {
                showStatus(statusId, 'err', 'يجب اختيار "إي" لإرسال التقديم.');
                return;
            }

            btn.disabled = true;
            btn.textContent = 'جاري الإرسال...';

            var payload = {
                embeds: [{
                    title: '📥 ' + roleTitle + ' — ذا ريلم',
                    color: 0xdc2626,
                    fields: [
                        { name: 'الاسم', value: nameVal, inline: true },
                        { name: 'يوزر الديسكورد', value: discordVal, inline: true },
                        { name: 'العمر', value: ageVal + ' سنة', inline: true },
                        { name: 'القسم', value: oathVal, inline: false },
                        { name: 'الخبرات السابقة', value: expVal.slice(0, 1024), inline: false },
                        {
                            name: 'قرار الإدارة',
                            value: '⏳ قيد المراجعة\n✅ قبول المتقدم   |   ❌ رفض المتقدم',
                            inline: false
                        }
                    ],
                    footer: {
                        text: 'The Realm RP • نظام التقديمات الرسمي'
                    },
                    timestamp: new Date().toISOString()
                }]
            };

            try {
                await postToWebhook(WEBHOOKS[key], payload);
                showStatus(statusId, 'ok', 'تم إرسال تقديمك بنجاح إلى الروم المخصص، وبانتظار مراجعة وقرار الإدارة (قبول / رفض).');
                form.reset();
            } catch (err) {
                showStatus(statusId, 'err', 'تعذر الإرسال حالياً، تأكد من الاتصال بالإنترنت ثم حاول مرة أخرى.');
            } finally {
                btn.disabled = false;
                btn.textContent = 'إرسال التقديم';
            }
        }

        async function submitBugReport(event) {
            event.preventDefault();
            var form = event.target;
            var btn = form.querySelector('button[type="submit"]');
            var statusId = 'status-bugs';

            var discordVal = document.getElementById('bug-discord').value.trim();
            var typeVal = document.getElementById('bug-type').value;
            var descVal = document.getElementById('bug-desc').value.trim();

            if (!discordVal || !typeVal || !descVal) {
                showStatus(statusId, 'err', 'يرجى تعبئة يوزر الديسكورد ونوع المشكلة ووصفها.');
                return;
            }

            btn.disabled = true;
            btn.textContent = 'جاري إرسال البلاغ...';

            var payload = {
                embeds: [{
                    title: '🛠️ بلاغ مشكلة / خطأ برمجي بالموقع',
                    color: 0xef4444,
                    fields: [
                        { name: 'يوزر الديسكورد', value: discordVal, inline: true },
                        { name: 'نوع المشكلة', value: typeVal, inline: true },
                        { name: 'وصف المشكلة / الخطأ', value: descVal.slice(0, 1024), inline: false }
                    ],
                    footer: {
                        text: 'The Realm RP • نظام البلاغات التقنية'
                    },
                    timestamp: new Date().toISOString()
                }]
            };

            try {
                await postToWebhook(WEBHOOKS.bugs, payload);
                showStatus(statusId, 'ok', 'تم إرسال بلاغك التقني بنجاح إلى روم المشاكل.');
                form.reset();
            } catch (err) {
                showStatus(statusId, 'err', 'تعذر إرسال البلاغ حالياً، حاول مرة أخرى.');
            } finally {
                btn.disabled = false;
                btn.textContent = 'إرسال البلاغ';
            }
        }
    </script>
</body>
</html>

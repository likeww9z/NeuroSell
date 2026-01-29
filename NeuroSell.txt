<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NeuroCell — Образовательная платформа</title>
    <style>
        /* --- СТИЛИ (CSS) --- */
        :root {
            --primary: #4a90e2;
            --accent: #2ecc71;
            --bg: #f4f7f6;
            --text: #2d3436;
            --white: #ffffff;
            --gray: #dfe6e9;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            background-color: var(--bg);
            color: var(--text);
            scroll-behavior: smooth;
        }

        /* Шапка */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 5%;
            background: var(--white);
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .logo-group { display: flex; gap: 20px; align-items: center; }
        .logo { font-weight: bold; font-size: 1.5rem; color: var(--primary); }
        .school-logo { font-size: 0.9rem; color: #636e72; border-left: 1px solid #ccc; padding-left: 15px; }

        /* Навигация */
        nav button {
            background: var(--primary);
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: 0.3s;
        }

        /* Главный экран */
        .page { display: none; padding: 40px 5%; min-height: 80vh; }
        .active-page { display: block; }

        .hero {
            text-align: center;
            padding: 100px 20px;
        }

        .hero h1 { font-size: 3.5rem; margin-bottom: 20px; color: var(--text); }
        .hero p { font-size: 1.2rem; max-width: 700px; margin: 0 auto 40px; }

        .btn-group { display: flex; justify-content: center; gap: 15px; flex-wrap: wrap; }
        .btn {
            padding: 15px 35px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 600;
            transition: 0.3s;
            cursor: pointer;
            border: none;
        }

        .btn-main { background: var(--primary); color: white; }
        .btn-sub { background: var(--white); border: 2px solid var(--primary); color: var(--primary); }

        /* Страница курса */
        .course-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .block-card {
            background: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.05);
            transition: 0.3s;
            position: relative;
        }

        .block-card.locked { opacity: 0.6; filter: grayscale(1); pointer-events: none; }
        .block-card.completed { border-top: 5px solid var(--accent); }
        
        .progress-circle {
            font-size: 0.8rem;
            color: var(--accent);
            font-weight: bold;
        }

        /* Футер */
        footer {
            background: #2d3436;
            color: white;
            padding: 40px 5%;
            margin-top: 50px;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .footer-grid a { color: var(--primary); text-decoration: none; }

    </style>
</head>
<body>

    <header>
        <div class="logo-group">
            <div class="logo" onclick="showPage('home')" style="cursor:pointer">NeuroCell</div>
            <div class="school-logo">Школьный проект</div>
        </div>
        <nav>
            <button onclick="alert('Окно входа в разработке')">Войти</button>
        </nav>
    </header>

    <main id="home" class="page active-page">
        <section class="hero">
            <h1>NeuroCell</h1>
            <p>Образовательный курс о манипулятивном маркетинге. Узнай, как бренды влияют на твой выбор, и научись защищать свои границы.</p>
            <div class="btn-group">
                <button class="btn btn-main" onclick="showPage('course')">Начать курс</button>
                <button class="btn btn-sub" onclick="showPage('booklet')">Образовательный буклет</button>
                <button class="btn btn-sub" onclick="showPage('about')">О проекте</button>
            </div>
        </section>
    </main>

    <main id="course" class="page">
        <h2>Обучающие блоки</h2>
        <p>Пройдите блоки последовательно, чтобы завершить курс.</p>
        
        <div class="course-grid">
            <div class="block-card" id="b1">
                <span class="progress-circle" id="p1">0% выполнено</span>
                <h3>1. Основы манипуляций</h3>
                <p>Видеоурок, презентация и вводный тест.</p>
                <button class="btn-main" style="padding: 5px 15px; border-radius: 5px;" onclick="completeBlock(1)">Сдать тест</button>
            </div>

            <div class="block-card locked" id="b2">
                <span class="progress-circle" id="p2">Закрыто</span>
                <h3>2. Эмоциональные триггеры</h3>
                <p>Как реклама использует страх и радость.</p>
                <button class="btn-main" style="padding: 5px 15px; border-radius: 5px;" onclick="completeBlock(2)">Сдать тест</button>
            </div>

            <div class="block-card locked" id="b3">
                <span class="progress-circle">Закрыто</span>
                <h3>3. Дефицит и срочность</h3>
                <p>«Осталось всего 2 товара!» — правда или ложь?</p>
                <button class="btn-main" style="padding: 5px 15px; border-radius: 5px;" onclick="completeBlock(3)">Сдать тест</button>
            </div>
        </div>
    </main>

    <main id="booklet" class="page">
        <h2>Образовательный буклет</h2>
        <div style="background: #eee; height: 400px; display: flex; align-items: center; justify-content: center; border-radius: 15px; margin: 20px 0;">
            <p>[ Здесь будет предпросмотр вашего PDF буклета ]</p>
        </div>
        <button class="btn btn-main">Скачать буклет (PDF)</button>
    </main>

    <main id="about" class="page">
        <h2>О проекте NeuroCell</h2>
        <p>NeuroCell — это инициатива, направленная на развитие медиаграмотности у молодежи.</p>
        <p>Мы верим, что понимание механизмов маркетинга делает потребителя свободным.</p>
        <h3>Создатели</h3>
        <p>Команда студентов и энтузиастов психологии.</p>
    </main>

    <footer>
        <div class="footer-grid">
            <div>
                <h4>NeuroCell</h4>
                <p>Твой гид в мире маркетинга.</p>
            </div>
            <div>
                <h4>Помощь</h4>
                <a href="#">Написать боту</a><br>
                <a href="#">FAQ</a>
            </div>
            <div>
                <h4>Контакты</h4>
                <p>Email: hello@neurocell.site</p>
            </div>
        </div>
    </footer>

    <script>
        // Функция переключения страниц
        function showPage(pageId) {
            // Скрываем все страницы
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active-page');
            });
            // Показываем нужную
            document.getElementById(pageId).classList.add('active-page');
            window.scrollTo(0,0);
        }

        // Логика прохождения курса
        function completeBlock(num) {
            const currentBlock = document.getElementById('b' + num);
            const progressText = document.getElementById('p' + num);
            const nextBlock = document.getElementById('b' + (num + 1));

            // Отмечаем текущий как выполненный
            currentBlock.classList.add('completed');
            progressText.innerText = "100% выполнено ✅";
            
            // Разблокируем следующий
            if(nextBlock) {
                nextBlock.classList.remove('locked');
                const nextProgress = nextBlock.querySelector('.progress-circle');
                if(nextProgress) nextProgress.innerText = "Доступно";
                alert("Блок " + num + " завершен! Следующий этап открыт.");
            } else {
                alert("Поздравляем! Вы прошли все доступные блоки курса!");
            }
        }
    </script>
</body>
</html>

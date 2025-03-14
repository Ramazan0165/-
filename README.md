<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Карманный доктор</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            max-width: 500px;
            width: 100%;
            text-align: center;
        }
        h1 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }
        .button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            margin: 0.5rem;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s ease;
        }
        .button:hover {
            background-color: #0056b3;
        }
        .response {
            margin-top: 1.5rem;
            text-align: left;
            background: #f9f9f9;
            padding: 1rem;
            border-radius: 5px;
            border: 1px solid #ddd;
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 id="greeting">Привет, я твой карманный доктор! Чем могу помочь?</h1>
        <button id="startButton" class="button">Я заболел! 🤒</button>
        
        <div id="symptomsSection" class="hidden">
            <h2>Какие симптомы?</h2>
            <button id="stomachButton" class="button">Болит живот 😬</button>
            <button id="headacheButton" class="button">Болит голова 🤕</button>
            <button id="nauseaButton" class="button">Тошнит 🤢</button>
            <button id="cutButton" class="button">Ссадина или порез 🔪</button>
            <button id="throatButton" class="button">Болит горло 🤭</button>
        </div>

        <div id="responseSection" class="hidden response"></div>

        <div id="thanksSection" class="hidden">
            <button id="thanksButton" class="button">Спасибо! 😊</button>
        </div>
    </div>

    <script>
        // Элементы DOM
        const greeting = document.getElementById('greeting');
        const startButton = document.getElementById('startButton');
        const symptomsSection = document.getElementById('symptomsSection');
        const responseSection = document.getElementById('responseSection');
        const thanksSection = document.getElementById('thanksSection');
        const thanksButton = document.getElementById('thanksButton');

        // Обработчики кнопок
        startButton.addEventListener('click', () => {
            symptomsSection.classList.remove('hidden');
            startButton.classList.add('hidden');
        });

        const handleSymptomClick = (response) => {
            responseSection.innerHTML = `<p>${response}</p>`;
            responseSection.classList.remove('hidden');
            symptomsSection.classList.add('hidden');
            thanksSection.classList.remove('hidden');
        };

        document.getElementById('stomachButton').addEventListener('click', () => {
            const response = `
                Вот несколько методов быстрого облегчения боли в животе:<br><br>
                ☑️1. Теплый компресс: Приложите теплую грелку или компресс к животу, чтобы расслабить мышцы и уменьшить спазмы.<br>
                ☑️2. Изменение положения: Попробуйте лечь на бок с поджатыми коленями или принять позу эмбриона, чтобы уменьшить дискомфорт.<br>
                ☑️3. Медикаменты: Используйте безрецептурные препараты, такие как анальгетики (например, Но-шпа, Тримедат, Необутин).<br>
                ☑️4. Имбирный чай: Пейте имбирный чай или настой, который может помочь при тошноте и болях.<br>
                ☑️5. Легкая диета: Употребляйте легкие продукты, такие как бананы, рис, яблочное пюре и тосты (BRAT-диета), чтобы успокоить желудок.<br>
                ☑️6. Гидратация: Пейте воду или электролитные растворы, чтобы избежать обезвоживания.<br>
                ☑️7. Дыхательные упражнения: Глубокое дыхание может помочь расслабить тело и уменьшить напряжение в животе.<br><br>
                ‼️Если боль не проходит или усиливается, обязательно обратитесь к врачу.
            `;
            handleSymptomClick(response);
        });

        document.getElementById('headacheButton').addEventListener('click', () => {
            const response = `
                Некоторые методы быстрого лечения головной боли:<br><br>
                ☑️1. Отдых в тихом и тёмном месте. Часто свет и шум усиливают головную боль.<br>
                ☑️2. Применение холодного компресса. Холод помогает уменьшить воспаление и сузить кровеносные сосуды, что может облегчить боль.<br>
                ☑️3. Приём обезболивающих средств. Безрецептурные препараты, например, парацетамол или аспирин, анальгин, снижают болевые ощущения и воспаление. Важно соблюдать дозировку, указанную в инструкции.<br>
                ☑️4. Соблюдение питьевого режима. Обезвоживание может быть причиной головной боли, и восстановление водного баланса часто помогает облегчить состояние.<br>
                ☑️5. Техники релаксации. Глубокое дыхание, медитация или прогрессивная мышечная релаксация помогают снизить стресс и напряжение, что может способствовать уменьшению головной боли.<br>
                ☑️6. Массаж головы и шеи. Лёгкий массаж головы, шеи и плеч поможет расслабить напряжённые мышцы. Он улучшает кровообращение и уменьшает напряжение, что способствует облегчению боли.<br><br>
                ‼️Если в течение часа боль не проходит, беспокоят сопутствующие симптомы (тошнота, головокружение, снижение чувствительности в отдельных частях тела), нужно вызывать врача.
            `;
            handleSymptomClick(response);
        });

        document.getElementById('nauseaButton').addEventListener('click', () => {
            const response = `
                Вот несколько методов быстрого облегчения тошноты:<br><br>
                ☑️1. Глубокое дыхание: Медленно вдыхайте через нос и выдыхайте через рот, чтобы успокоить организм.<br>
                ☑️2. Имбирь: Пейте имбирный чай или жуйте кусочек свежего имбиря.<br>
                ☑️3. Мятный чай: Мята может помочь успокоить желудок.<br>
                ☑️4. Лимон: Понюхайте лимон или выпейте немного лимонного сока.<br>
                ☑️5. Положение тела: Лягте на бок или сядьте с прямой спиной, избегая наклона вперед.<br>
                ☑️6. Легкая пища: Употребляйте сухие крекеры или тосты.<br>
                ☑️7. Гидратация: Пейте воду маленькими глотками.<br>
                ☑️8. Медикаменты: Драмина, Колофорт, Линекс форте, Церукал.<br><br>
                ‼️Если тошнота не проходит, обратитесь к врачу.
            `;
            handleSymptomClick(response);
        });

        document.getElementById('cutButton').addEventListener('click', () => {
            const response = `
                Вот краткие методы лечения порезов и ссадин:<br><br>
                ☑️1. Остановка кровотечения: Нажмите на рану чистой тканью или бинтом.<br>
                ☑️2. Очистка раны: Промойте рану под проточной водой, удаляя грязь и остатки.<br>
                ☑️3. Антисептик: Нанесите антисептический раствор (например, перекись водорода или хлоргексидин).<br>
                ☑️4. Закрытие раны: При необходимости наложите стерильный бинт или пластырь.<br>
                ☑️5. Контроль за состоянием: Следите за признаками инфекции (покраснение, отек, гной).<br>
                ☑️6. Обезболивание: При необходимости принимайте обезболивающие средства.<br>
                ☑️7. Замена повязки: Меняйте повязку ежедневно или по мере загрязнения.<br><br>
                ‼️Если рана глубокая или не заживает, обратитесь к врачу.
            `;
            handleSymptomClick(response);
        });

        document.getElementById('throatButton').addEventListener('click', () => {
            const response = `
                Вот несколько методов лечения боли в горле:<br><br>
                ☑️1. Полоскание:<br>
                   • Полоскайте горло теплой соленой водой (1/2 чайной ложки соли на стакан воды).<br>
                   • Используйте антисептические растворы для полоскания.<br>
                ☑️2. Гидратация:<br>
                   • Пейте много жидкости, включая воду, чаи и бульоны.<br>
                   • Теплые напитки с медом и лимоном могут облегчить боль.<br>
                ☑️3. Увлажнение воздуха:<br>
                   • Используйте увлажнитель воздуха, чтобы предотвратить пересушивание слизистых оболочек.<br>
                ☑️4. Лекарственные средства:<br>
                   • Принимайте безрецептурные обезболивающие (ибупрофен, парацетамол).<br>
                   • Используйте пастилки для горла или спреи с антисептиками.<br>
                ☑️5. Отдых:<br>
                   • Дайте голосу отдохнуть и избегайте напряжения голосовых связок.<br>
                ☑️6. Избегание раздражителей:<br>
                   • Избегайте курения, алкоголя и острой пищи, которые могут усугубить боль.<br>
                ☑️7. Теплые компрессы:<br>
                   • Применяйте теплые компрессы на шею для облегчения дискомфорта.<br><br>
                ‼️Если боль в горле сохраняется более нескольких дней, сопровождается высокой температурой, затруднением дыхания или глотания, обратитесь к врачу.
            `;
            handleSymptomClick(response);
        });

        thanksButton.addEventListener('click', () => {
            responseSection.classList.add('hidden');
            thanksSection.classList.add('hidden');
            greeting.textContent = "Всегда пожалуйста! 😉 Будет нужна помощь — обращайтесь! А пока выздоравливайте! 😘";
        });
    </script>
</body>
</html>

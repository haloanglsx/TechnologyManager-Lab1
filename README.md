

### 1. **Клас Technology та його успадкування**
   - **Базовий клас (`Technology`)**:
     - Це абстрактний базовий клас, який представляє загальну технологію з такими атрибутами, як `name` (назва) та `type` (тип).
     - Він містить віртуальні функції, такі як `serialize()` та `display()`, які можна перевизначити у похідних класах.
     - Клас є абстрактним, оскільки має чисто віртуальну функцію (`serialize()`), тобто ви не можете створити об'єкт безпосередньо з класу `Technology`.

   - **Похідні класи (`FrontendTechnology` та `BackendTechnology`)**:
     - Ці класи успадковують `Technology` і представляють конкретні типи технологій.
     - `FrontendTechnology` додає атрибут `framework` (фреймворк), а `BackendTechnology` додає атрибут `language` (мова).
     - Вони перевизначають методи `serialize()` та `display()` для надання конкретної реалізації, залежно від типу технології.

### 2. **Клас TechnologyManager**
   - **Призначення**:
     - Клас `TechnologyManager` відповідає за керування колекцією об'єктів `Technology`.
     - Він забезпечує функціонал, такий як додавання, редагування, відображення, збереження та завантаження цих технологій.

   - **Атрибути**:
     - Основний атрибут – це `technologies`, вектор вказівників на об'єкти `Technology`. Це дозволяє зберігати будь-який тип технології (Frontend або Backend) в одній колекції.

   - **Основні методи**:
     - `addTechnology()`: Додає нову технологію до колекції. Метод запитує у користувача тип (Frontend/Backend) і, залежно від типу, створює відповідний об'єкт (`FrontendTechnology` або `BackendTechnology`).
     - `editTechnology(int index)`: Редагує існуючу технологію за її індексом у колекції. Метод видаляє старий об'єкт і замінює його новим.
     - `displayAll()`: Проходиться по вектору `technologies` та викликає метод `display()` для кожного об'єкта, виводячи його деталі на екран.
     - `deleteTechnology(int index)`: Видаляє технологію з колекції та звільняє пам'ять.
     - `saveToFile()`: Серіалізує дані технологій і записує їх у файл, що дозволяє користувачу зберігати свій прогрес.
     - `loadFromFile()`: Читає дані з файлу та відновлює об'єкти технологій, переповнюючи вектор `technologies`.

### 3. **Основна програма (main.cpp)**
   - **Призначення**:
     - Функція `main()` є точкою входу до програми. Вона взаємодіє з користувачем, надаючи меню для виконання різних операцій, таких як додавання, редагування, відображення та збереження/завантаження технологій.

   - **Робочий процес**:
     - Програма починається зі створення об'єкта класу `TechnologyManager`.
     - Вона представляє користувачу меню вибору дій (наприклад, додавання технології, відображення всіх технологій, збереження у файл).
     - Залежно від вибору користувача, викликається відповідний метод об'єкта `TechnologyManager`.
     - Якщо користувач вирішує додати технологію, програма переконується, що введений тип є коректним (Frontend або Backend). Якщо введено некоректний тип, програма продовжує запитувати правильний тип, доки не отримає вірну відповідь.
     - Програма працює в циклі, дозволяючи користувачу виконувати кілька операцій, доки він не вирішить завершити роботу.

### 4. **Управління пам'яттю**
   - **Динамічне виділення**:
     - Технології динамічно виділяються за допомогою `new` при додаванні до менеджера. Це забезпечує гнучкість у роботі з різними типами технологій.
   - **Деструктор (`~TechnologyManager()`)**:
     - Клас `TechnologyManager` має деструктор, який гарантує, що всі динамічно виділені об'єкти `Technology` будуть належним чином видалені при знищенні менеджера, запобігаючи витокам пам'яті.

### 5. **Обробка помилок та валідація введення**
   - Програма перевіряє правильність введення типу (Frontend/Backend) під час додавання технології. Це важливо для забезпечення створення правильних об'єктів.
   - Методи `editTechnology` та `deleteTechnology` включають перевірку меж, щоб запобігти виходу за межі вектора `technologies`.

### 6. **Робота з файлами (File I/O)**
   - **Збереження**: Метод `saveToFile` записує серіалізовані дані технологій у файл, що дозволяє зберігати дані між запусками програми.
   - **Завантаження**: Метод `loadFromFile` читає дані з файлу та відтворює об'єкти технологій у менеджері, дозволяючи користувачу продовжити роботу з того місця, де він зупинився.

### Підсумок:
Програма призначена для керування колекцією технологій, які класифікуються на типи Frontend та Backend, надаючи користувачу можливість взаємодіяти з цією колекцією через низку операцій. Використання успадкування та поліморфізму дозволяє програмі безшовно працювати з різними типами технологій, тоді як клас `TechnologyManager` інкапсулює логіку керування цією колекцією. Управління пам'яттю забезпечується через динамічне виділення та обережне видалення, що гарантує ефективну роботу програми без витоків пам'яті..

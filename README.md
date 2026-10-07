# Introducing

# Как сдавать лабораторную работу через GitHub

Весь процесс сдачи лабораторной работы проходит через **GitHub**.

Для каждого студента заранее создан отдельный репозиторий.

Общий процесс:

```text
Получить репозиторий
        ↓
Клонировать репозиторий
        ↓
Создать свою ветку
        ↓
Сделать лабораторную работу
        ↓
Добавить изменения в Git
        ↓
Сделать commit
        ↓
Отправить ветку на GitHub
        ↓
Создать Pull Request
        ↓
Проверка работы
        ↓
 ┌───────────────┐
 │               │
Правки нужны    Всё хорошо
 │               │
 ↓               ↓
Исправить       PR принят
 │
 ↓
Сделать commit
 │
 ↓
PR автоматически обновится
````

---

# 1. Что нужно установить

Для работы понадобится:

* **Git**
* аккаунт на **GitHub**
* IDE, например Rider / Visual Studio / VS Code

Проверить, установлен ли Git:

```bash
git --version
```

Если команда выводит версию Git, всё готово.

Например:

```text
git version 2.51.0
```

---

# 2. Получить ссылку на свой репозиторий

Преподаватель выдаёт каждому студенту ссылку на его репозиторий.

Например:

```text
https://github.com/teacher/student-repository.git
```

Откройте репозиторий в браузере и убедитесь, что это **ваш** репозиторий.

---

# 3. Клонировать репозиторий

Перейдите в папку, где хотите хранить лабораторные работы.

Например:

```bash
cd ~/Projects
```

Склонируйте репозиторий:

```bash
git clone https://github.com/teacher/student-repository.git
```

Перейдите в папку проекта:

```bash
cd student-repository
```

Проверить, что всё получилось:

```bash
git status
```

Должно быть примерно:

```text
On branch main
nothing to commit, working tree clean
```

---

# 4. Настроить Git

Если Git используется впервые, необходимо указать имя и email.

```bash
git config --global user.name "Your Name"
```

```bash
git config --global user.email "your@email.com"
```

Проверить настройки:

```bash
git config --global --list
```

---

# 5. Основная ветка

В репозитории есть основная ветка:

```text
main
```

**Не делайте лабораторную работу напрямую в `main`.**

Для каждой лабораторной необходимо создавать отдельную ветку.

Например:

```text
main
 ├── lab1
 ├── lab2
 └── lab3
```

Это позволяет проверять каждую лабораторную отдельно.

---

# 6. Создать ветку для лабораторной

Перед созданием ветки убедитесь, что вы находитесь в `main`:

```bash
git checkout main
```

Получите последние изменения с GitHub:

```bash
git pull
```

Теперь создайте ветку для лабораторной.

Например, для первой лабораторной:

```bash
git checkout -b lab1
```

Проверить текущую ветку:

```bash
git branch
```

Вы должны увидеть:

```text
* lab1
  main
```

Звёздочка `*` показывает текущую ветку.

---

# 7. Сделать лабораторную работу

Теперь можно выполнять лабораторную работу.

Создавайте файлы, изменяйте код, запускайте программу и проверяйте её работу.

Например:

```text
student-repository/
├── src/
│   ├── Program.cs
│   ├── User.cs
│   └── ...
├── tests/
└── README.md
```

Все изменения выполняются в ветке:

```text
lab1
```

---

# 8. Проверить изменения

После выполнения части работы можно посмотреть, какие файлы изменились:

```bash
git status
```

Например:

```text
Changes not staged for commit:

    modified:   Program.cs

Untracked files:

    User.cs
```

Также можно посмотреть конкретные изменения:

```bash
git diff
```

---

# 9. Добавить изменения в Git

Когда изменения готовы к сохранению:

```bash
git add .
```

Команда `git add .` добавляет все изменения текущей папки.

После этого снова можно проверить статус:

```bash
git status
```

Файлы должны появиться в разделе:

```text
Changes to be committed
```

---

# 10. Сделать commit

Теперь необходимо сохранить изменения в Git.

```bash
git commit -m "Implement lab 1"
```

Например:

```bash
git commit -m "Implement interfaces and records"
```

Хорошее сообщение commit должно коротко описывать, что было сделано.

### Хорошо

```text
Implement user repository
```

```text
Add validation
```

```text
Fix route calculation
```

### Плохо

```text
changes
```

```text
123
```

```text
asdf
```

---

# 11. Отправить ветку на GitHub

После commit изменения пока находятся только на вашем компьютере.

Нужно отправить ветку на GitHub:

```bash
git push -u origin lab1
```

После этого ветка появится на GitHub.

При следующих изменениях достаточно:

```bash
git push
```

---

# 12. Создать Pull Request

После отправки ветки на GitHub откройте свой репозиторий.

GitHub обычно покажет кнопку:

**Compare & pull request**

Нажмите её.

Если кнопки нет:

1. Откройте вкладку **Pull requests**
2. Нажмите **New pull request**
3. Выберите:

```text
base: main
compare: lab1
```

То есть:

```text
lab1 → main
```

---

# 13. Оформить Pull Request

В названии Pull Request укажите лабораторную работу.

Например:

```text
Lab 1
```

Или:

```text
Lab 1 — OOP
```

В описании можно кратко написать, что было сделано.

Например:

```text
Implemented the first laboratory work.

Completed:
- interfaces
- record classes
- validation
- tests
```

После этого нажмите:

**Create pull request**

---

# 14. Что происходит после создания PR

После создания Pull Request преподаватель получает работу на проверку.

Преподаватель может:

### Вариант 1 — работа принята

Если всё хорошо, преподаватель принимает Pull Request.

```text
Student
   ↓
Pull Request
   ↓
Code Review
   ↓
Approved
```

Лабораторная работа сдана.

---

### Вариант 2 — нужны исправления

Если в работе есть ошибки, преподаватель оставляет комментарии и просит внести исправления.

Например:

```text
Please fix the validation in User.cs.
```

или:

```text
The class violates SRP.
Please refactor it.
```

**Не нужно создавать новый Pull Request.**

Работайте дальше в той же ветке.

---

# 15. Как исправить замечания преподавателя

Предположим, преподаватель оставил замечание:

```text
Fix validation in User.cs
```

Исправьте код локально.

После этого:

```bash
git status
```

Добавьте изменения:

```bash
git add .
```

Сделайте новый commit:

```bash
git commit -m "Fix validation"
```

И отправьте его:

```bash
git push
```

### Важно

Pull Request обновится **автоматически**.

Создавать новый PR не нужно.

Получится:

```text
Commit 1
   ↓
Pull Request
   ↓
Review
   ↓
Fix
   ↓
Commit 2
   ↓
git push
   ↓
Тот же Pull Request обновился
   ↓
Review
```

---

# 16. Если преподаватель оставил несколько замечаний

Исправьте все замечания.

Например:

```text
❌ Fix validation
❌ Rename class
❌ Add tests
```

После исправления:

```bash
git add .
```

```bash
git commit -m "Fix review comments"
```

```bash
git push
```

После этого напишите преподавателю, что замечания исправлены.

---

# 17. Полный процесс от начала до конца

## Первый раз

```bash
git clone <URL-репозитория>
```

```bash
cd <repository>
```

```bash
git checkout main
```

```bash
git pull
```

```bash
git checkout -b lab1
```

После выполнения лабораторной:

```bash
git status
```

```bash
git add .
```

```bash
git commit -m "Implement lab 1"
```

```bash
git push -u origin lab1
```

После этого создаётся Pull Request:

```text
lab1 → main
```

---

# 18. Если преподаватель отправил на исправления

Исправляем код:

```bash
git add .
```

```bash
git commit -m "Fix review comments"
```

```bash
git push
```

**Новый Pull Request создавать не нужно.**

---

# 19. Следующая лабораторная

После того как первая лабораторная принята, для следующей создаётся новая ветка.

Сначала переключаемся на `main`:

```bash
git checkout main
```

Получаем последние изменения:

```bash
git pull
```

Создаём новую ветку:

```bash
git checkout -b lab2
```

Делаем лабораторную и отправляем:

```bash
git add .
```

```bash
git commit -m "Implement lab 2"
```

```bash
git push -u origin lab2
```

Создаём новый Pull Request:

```text
lab2 → main
```

---

# 20. Полезные команды Git

| Команда                   | Что делает                                 |
| ------------------------- | ------------------------------------------ |
| `git status`              | Показывает состояние репозитория           |
| `git branch`              | Показывает ветки                           |
| `git checkout main`       | Переключается на `main`                    |
| `git checkout -b lab1`    | Создаёт новую ветку и переключается на неё |
| `git add .`               | Добавляет изменения в commit               |
| `git commit -m "message"` | Создаёт commit                             |
| `git push`                | Отправляет изменения на GitHub             |
| `git pull`                | Получает изменения с GitHub                |
| `git diff`                | Показывает изменения в файлах              |
| `git log`                 | Показывает историю commit                  |

---

# 21. Самый частый сценарий

В большинстве случаев вам понадобится всего несколько команд.

### Начало новой лабораторной

```bash
git checkout main
git pull
git checkout -b lab2
```

### После выполнения работы

```bash
git add .
git commit -m "Implement lab 2"
git push -u origin lab2
```

### Если пришли правки

```bash
git add .
git commit -m "Fix review comments"
git push
```

---

# 22. Важные правила

### 1. Не работайте напрямую в `main`

Для каждой лабораторной создавайте отдельную ветку:

```text
lab1
lab2
lab3
...
```

### 2. Не создавайте новый PR после исправлений

Если преподаватель отправил работу на правки:

```text
❌ Новый PR
```

Нужно:

```text
Исправить → commit → push
```

Существующий PR обновится автоматически.

### 3. Перед новой лабораторной обновляйте `main`

Всегда:

```bash
git checkout main
git pull
```

и только после этого:

```bash
git checkout -b labN
```

### 4. Проверяйте код перед созданием PR

Перед сдачей убедитесь, что:

* проект собирается;
* программа запускается;
* тесты проходят;
* нет лишних файлов;
* нет паролей, токенов и других секретов;
* лабораторная соответствует заданию.

### 5. Commit должен описывать изменения

Например:

```text
Implement lab 3
```

```text
Add unit tests
```

```text
Fix validation
```

---

# 23. Что считается сдачей лабораторной

Лабораторная считается отправленной на проверку, когда:

1. Лабораторная выполнена.
2. Изменения находятся в отдельной ветке.
3. Ветка отправлена на GitHub.
4. Создан Pull Request из вашей ветки в `main`.

То есть итоговый вид должен быть:

```text
main
  ↑
  │
  │ Pull Request
  │
lab1
  │
  ├── commit
  ├── commit
  └── commit
```

После проверки преподавателем:

```text
Approved → лабораторная принята
```

или:

```text
Changes requested → исправить замечания и сделать push
```

---

# 24. Главное, что нужно запомнить

```text
1. clone
      ↓
2. checkout main
      ↓
3. git pull
      ↓
4. checkout -b labN
      ↓
5. Сделать лабораторную
      ↓
6. git add .
      ↓
7. git commit
      ↓
8. git push
      ↓
9. Создать Pull Request
      ↓
10. Review преподавателя
      ↓
   ┌───────────────┐
   ↓               ↓
Правки           Approved
   ↓
Исправить
   ↓
commit + push
   ↓
Повторное ревью
```

**Ваша основная задача — работать в своей ветке и поддерживать Pull Request актуальным до момента его принятия.**

```

# Документація з лінтингу

## Обраний лінтер та причини вибору
Для цього проєкту було обрано **ESLint** у поєднанні з **Prettier**.

### Чому саме ESLint?
- Виявляє помилки та потенційні проблеми в коді.
- Допомагає підтримувати єдиний стиль коду.
- Інтегрується з більшістю редакторів коду.
- Можливість налаштування під конкретні вимоги проєкту.

### Чому використовується Prettier?
- Відповідає за форматування коду, щоб уникнути стилістичних помилок.
- Автоматично виправляє відступи, лапки, коми тощо.
- Допомагає уникнути конфліктів форматування в командній розробці.

## Базові правила та їх пояснення

### Налаштування ESLint
У файлі `.eslintrc.json` визначені наступні правила:
```json
{
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:prettier/recommended"
  ],
  "rules": {
    "prettier/prettier": "warn",
    "no-unused-vars": "warn",
    "react/prop-types": "off",
    "eqeqeq": "error"
  }
}
```

- **"prettier/prettier": "warn"** – підсвічує помилки форматування, але не виправляє їх автоматично.
- **"no-unused-vars": "warn"** – попереджає про невикористані змінні.
- **"react/prop-types": "off"** – вимикає обов’язкову перевірку `prop-types`.
- **"eqeqeq": "error"** – вимагає використання `===` замість `==`.

### Налаштування Prettier
Файл `.prettierrc.json`:
```json
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5",
  "printWidth": 80,
  "arrowParens": "always"
}
```
- **"semi": true** – додає `;` у кінці рядків.
- **"singleQuote": true** – використовує `'` замість `"`.
- **"tabWidth": 2** – відступ у 2 пробіли.
- **"trailingComma": "es5"** – додає коми в кінці об'єктів і масивів.
- **"printWidth": 80** – максимальна довжина рядка – 80 символів.
- **"arrowParens": "always"** – завжди додає `()` у стрілочних функціях.

## Інструкція з запуску лінтера

1. **Встановіть залежності** (якщо ще не встановлено):
   ```sh
   npm install eslint prettier eslint-plugin-prettier eslint-config-prettier eslint-plugin-react --save-dev
   ```

2. **Запуск ESLint для перевірки коду:**
   ```sh
   npx eslint .
   ```

3. **Запуск Prettier для перевірки форматування:**
   ```sh
   npx prettier --check .
   ```

4. **Запуск ESLint з автоматичним виправленням:**
   ```sh
   npx eslint . --fix
   ```

5. **Запуск Prettier для автоматичного форматування:**
   ```sh
   npx prettier --write .
   ```

6. **Додавання лінтерів у `package.json` для зручності:**
   ```json
   "scripts": {
     "lint": "eslint .",
     "lint:fix": "eslint . --fix",
     "format": "prettier --write .",
     "format:check": "prettier --check ."
   }
   ```

Тепер можна запускати лінтер простішими командами:
```sh
npm run lint
npm run lint:fix
npm run format
npm run format:check
```


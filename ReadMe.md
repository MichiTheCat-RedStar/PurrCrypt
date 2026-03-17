[![Telegram](https://img.shields.io/badge/Telegram-@TeaTechnology-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/TeaTechnology)
[![GitHub](https://img.shields.io/badge/GitHub-MichiTheCat--RedStar-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/MichiTheCat-RedStar)
[![Itch.io](https://img.shields.io/badge/Itch.io-michi--the--cat-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://michi-the-cat.itch.io)

# PurrCrypt

PurrCrypt is a playful Python module that encodes text into a cat‑like language using only the characters `R` and `r` (prefixed by `Pu`).  
It provides two modes:

- **Simple encoding/decoding** – direct mapping of bits to `R` (1) and `r` (0).
- **Key‑based encryption/decryption** – each bit is randomly flipped based on a seed, making the output reversible only with the correct key.

## Functions

### `purr_encode(*text: str) -> str`
Converts the given text into a `Pu...` string by replacing each `1` bit with `R` and each `0` bit with `r`.  
Multiple arguments are joined with spaces.

### `purr_decode(text: str) -> str`
Reverses `purr_encode`. Expects a string starting with `Pu` followed only by `R`/`r`.  
Raises `ValueError` for invalid input.

### `purr_encrypt(*text: str, key=42) -> str`
Similar to `purr_encode`, but uses the given `key` to seed Python’s random generator.  
For every bit:
- If the original bit is `1`, a random choice decides whether to output `R` or `r`.
- If the original bit is `0`, the opposite random mapping is applied.

This makes the output unpredictable without the key.

### `purr_decrypt(text: str, key=42) -> str`
Reverses `purr_encrypt` using the same key.  
It reads the `R`/`r` sequence and, based on the same random decisions, reconstructs the original bits.

## Example

```python
>>> import PurrCrypt

>>> encoded = PurrCrypt.purr_encode("Meow")
>>> print(encoded)
PuRrRrRrrRrRRrRrRrRrRrRrrRrrRrRRrRrrRrRrRr

>>> decoded = PurrCrypt.purr_decode(encoded)
>>> print(decoded)
Meow

>>> encrypted = PurrCrypt.purr_encrypt("Hello", key=123)
>>> print(encrypted)
PuRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRr

>>> decrypted = PurrCrypt.purr_decrypt(encrypted, key=123)
>>> print(decrypted)
Hello
```

## Notes

- The encoding/decoding functions are deterministic and always produce the same output for a given input.
- The encryption/decryption functions use `random.seed(key)` and `round(random())` to generate a deterministic but pseudo‑random bit flip.  
  The same key must be used for both encryption and decryption.
- Only characters `R` and `r` are allowed after the initial `Pu`. Any other character raises a `ValueError`.
- The module works with any UTF‑8 text.

---

# PurrCrypt (Русское описание)

PurrCrypt — это игровой модуль на Python, который преобразует текст в «кошачий» язык, используя только символы `R` и `r` (с префиксом `Pu`).  
Предусмотрено два режима:

- **Простое кодирование/декодирование** – прямая замена битов: `1` → `R`, `0` → `r`.
- **Шифрование/дешифрование с ключом** – каждый бит случайно инвертируется в зависимости от seed’а, что делает результат обратимым только при наличии правильного ключа.

## Функции

### `purr_encode(*text: str) -> str`
Преобразует переданный текст в строку вида `Pu...`, заменяя каждый бит `1` на `R`, а `0` на `r`.  
Несколько аргументов объединяются через пробел.

### `purr_decode(text: str) -> str`
Выполняет обратное преобразование для `purr_encode`. Ожидает строку, начинающуюся с `Pu`, за которой следуют только символы `R`/`r`.  
При неверном формате возбуждает исключение `ValueError`.

### `purr_encrypt(*text: str, key=42) -> str`
Работает аналогично `purr_encode`, но использует переданный `key` для инициализации генератора случайных чисел.  
Для каждого бита:
- Если исходный бит равен `1`, случайным образом выбирается, вывести `R` или `r`.
- Если исходный бит равен `0`, применяется противоположное случайное отображение.

Без знания ключа восстановить исходный текст практически невозможно.

### `purr_decrypt(text: str, key=42) -> str`
Восстанавливает текст, зашифрованный с помощью `purr_encrypt` с тем же ключом.  
Анализирует последовательность `R`/`r` и, используя ту же последовательность случайных решений, воссоздаёт исходные биты.

## Пример

```python
>>> import PurrCrypt

>>> encoded = PurrCrypt.purr_encode("Мяу")
>>> print(encoded)
PuRrRrRrrRrRRrRrRrRrRrRrrRrrRrRRrRrrRrRrRr

>>> decoded = PurrCrypt.purr_decode(encoded)
>>> print(decoded)
Мяу

>>> encrypted = PurrCrypt.purr_encrypt("Привет", key=123)
>>> print(encrypted)
PuRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRrRr

>>> decrypted = PurrCrypt.purr_decrypt(encrypted, key=123)
>>> print(decrypted)
Привет
```

## Примечания

- Функции простого кодирования/декодирования детерминированы и всегда дают одинаковый результат для одних и тех же входных данных.
- Функции шифрования/дешифрования используют `random.seed(key)` и `round(random())` для создания детерминированного псевдослучайного потока.  
  Один и тот же ключ должен применяться как при шифровании, так и при дешифровании.
- После начального `Pu` допускаются только символы `R` и `r`. Любой другой символ вызывает исключение `ValueError`.
- Модуль работает с любым текстом в кодировке UTF‑8.

## Лицензия

Этот проект распространяется под лицензией MIT. Подробности см. в файле [LICENSE](LICENSE).
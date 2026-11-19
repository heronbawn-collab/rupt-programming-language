# Rupt

## Русский

Rupt — современный язык программирования с собственным интерпретатором, написанным на C.  
Философия: простота для новичка, мощь для реальных приложений.

### Принципы

- Собственный лексер, парсер и AST.
- Динамическая типизация с опциональными аннотациями.
- Интерпретатор с REPL и запуском файлов.
- Модульная архитектура: compiler / runtime / std / bricks.
- Расширяемость: Bricks, native-модули, JIT-ready дизайн.

### Установка (Windows)

#### Вариант 1: установщик

1. Скачайте installer/installer.exe.
2. Запустите установщик.
3. Перезапустите терминал.

Установщик копирует файлы в %LOCALAPPDATA%\Rupt и добавляет bin в PATH.

#### Вариант 2: вручную

1. Скопируйте rupt.exe и brick.exe в папку, например C:\Rupt\bin.
2. Скопируйте папки std, registry, bricks рядом.
3. Добавьте C:\Rupt\bin в PATH.

Проверка:

```text
rupt program.rupt
```

### Запуск

Все .rupt файлы должны начинаться со слова rupt.

```text
rupt program.rupt
rupt run program.rupt
rupt
```

### Синтаксис

```rupt
rupt
name = "Rupt"
print("Hello {name}")

fn add(a, b):
    return a + b

class User:
    fn __init__(self, name):
        self.name = name

    fn greet(self):
        print("Hello", self.name)
```

### Типы данных

- Int, Float, Bool, String, None
- List, Tuple, Set, Map
- Function, Class, Instance, Module, Range

### Управляющие конструкции

- if / elif / else
- for / while
- break / continue / pass
- try / except / finally / raise

### Функции

  - позиционные, именованные, значения по умолчанию
  - variadic (*args, **kwargs)
  - замыкания, рекурсия, lambda
  - visible(...) — вывод (как print).
  - toilet() — полная остановка программы.
  - встроенные: print, visible, toilet, len, range, int, float, str, bool, list, input, sum, min, max, sorted, reversed, enumerate, zip, all, any, abs, time_now, sleep_ms, file_read, file_write, file_append, file_delete, file_exists, sound_beep, sound_play, ceil, floor, round, pow, sqrt, exp, log, log10, sin, cos, tan, asin, acos, atan, sinh, cosh, tanh, deg2rad, rad2deg, clamp, map_range, lerp, sign, is_even, is_odd, gcd, lcm, min2, max2, chr, ord, hex, oct, bin, divmod, repr, ascii, slice, complex, dict, frozenset, issubclass, isinstance, bytes, bytearray, memoryview, format, type, callable, object

### Коллекции

- List: индексация, срезы, comprehensions
- Map: ключ-значение
- Set: уникальные элементы
- Tuple: неизменяемые наборы

### Модули

```rupt
rupt
import math
from math import sqrt
```

Поиск модулей: текущая директория, std/, bricks/<name>/.

### Стандартная библиотека

Модули: math, os, json, random, time, path, sys, string, collections, regex, datetime, terminal, environment, logging, files, network, http, crypto, hash, threading, process, subprocess, async, itertools, functools.

### Графика и звук

- `gfx_init(w, h)` — создать холст.
- `gfx_clear()` — очистить холст.
- `gfx_color("#RRGGBB")` — установить цвет в формате HEX.
- `gfx_pixel(x, y)` — точка.
- `gfx_line(x1, y1, x2, y2)` — отрезок.
- `gfx_rect(x, y, w, h)` / `gfx_fill_rect(x, y, w, h)` — прямоугольник / залитый прямоугольник.
- `gfx_circle(x, y, r)` / `gfx_fill_circle(x, y, r)` — окружность / залитый круг.
- `gfx_show()` — отрисовать холст в терминале.
- `gfx_save("file.ppm")` — сохранить холст в PPM.
- `gfx_close()` — освободить холст.
- `sound_beep(freq, ms)` — звуковой сигнал.
- `kill(pid)` — полная остановка процесса по PID (возвращает true/false).

- `http_get(url)` — GET запрос, возвращает {status, body}.
- `http_post(url, data)` — POST запрос с телом.
- `http_post_json(url, data)` — POST запрос с JSON телом.
- `json_parse(str)` — разбор JSON строки в Map.
- `json_stringify(obj)` — сериализация Map/List в JSON строку.
- `url_encode(str)` — URL кодирование.
- `url_decode(str)` — URL декодирование.
- `html_escape(str)` — экранирование HTML.
- `html_unescape(str)` — декодирование HTML.
- `base64_encode(list)` — Base64 кодирование списка байт.
- `base64_decode(str)` — Base64 декодирование в список байт.
- `uuid()` — генерация UUID v4.
- `md5(text)` — MD5 хеш (шестнадцатеричная строка).
- `sha1(text)` — SHA1 хеш.
- `sha256(text)` — SHA256 хеш.
- `url_parse(url)` — разбор URL на части.
- `html_strip_tags(html)` — удаление HTML тегов.
- `base64url_encode(list)` — Base64URL кодирование.
- `base64url_decode(str)` — Base64URL декодирование.
- `hmac_sha256(key, msg)` — HMAC-SHA256.
- `pbkdf2(password, salt, iterations)` — PBKDF2 с HMAC-SHA256.
- `jwt_encode(header, payload, secret)` — JWT кодирование.
- `jwt_decode(token)` — JWT декодирование.

### Файлы

- `file_read(path)` — прочитать файл в строку.
- `file_write(path, text)` — записать файл.
- `file_append(path, text)` — дописать в файл.
- `file_delete(path)` — удалить файл.
- `file_exists(path)` — проверить существование файла.

### Bricks (пакеты)

```text
brick install <name>
brick remove <name>
brick update <name>
brick list
brick search <name>
brick publish
brick info <name>
```

Пакеты хранятся в bricks/, реестр — в registry/.  
Пример brick: rupt_timer.

Доступные Bricks: rupt_timer, rupt_math, rupt_strings, rupt_lists, rupt_maps, rupt_random, rupt_files, rupt_json, rupt_http, rupt_os, rupt_path, rupt_crypto, rupt_hash, rupt_regex, rupt_datetime, rupt_collections, rupt_itertools, rupt_functools, rupt_logging, rupt_terminal, rupt_network, rupt_process, rupt_testing, rupt_async.

### Ошибки

Профессиональный вывод: тип ошибки, файл, строка, колонка, stack trace, подсказки.

### Развитие языка

Rupt развивается благодаря контрибьюторам. Любой вклад (код, документация, тесты, идеи) помогает языку расти.

### Сборка

```text
build.bat
```

## English

Rupt is a modern programming language with a C-based interpreter.  
Philosophy: simple for beginners, powerful for real applications.

### Principles

- Custom lexer, parser, and AST.
- Dynamic typing with optional annotations.
- Interpreter with REPL and file execution.
- Modular architecture: compiler / runtime / std / bricks.
- Extensible: Bricks, native modules, JIT-ready design.

### Installation (Windows)

#### Option 1: installer

1. Download installer/installer.exe.
2. Run the installer.
3. Restart the terminal.

The installer copies files to %LOCALAPPDATA%\Rupt and adds bin to PATH.

#### Option 2: manual

1. Copy rupt.exe and brick.exe to a folder, e.g. C:\Rupt\bin.
2. Copy std, registry, bricks folders next to it.
3. Add C:\Rupt\bin to PATH.

Check:

```text
rupt program.rupt
```

### Run

All .rupt files must start with the word rupt.

```text
rupt program.rupt
rupt run program.rupt
rupt
```

### Syntax

```rupt
rupt
name = "Rupt"
print("Hello {name}")

fn add(a, b):
    return a + b

class User:
    fn __init__(self, name):
        self.name = name

    fn greet(self):
        print("Hello", self.name)
```

### Data Types

- Int, Float, Bool, String, None
- List, Tuple, Set, Map
- Function, Class, Instance, Module, Range

### Control Flow

- if / elif / else
- for / while
- break / continue / pass
- try / except / finally / raise

### Functions

  - positional, keyword, default arguments
  - variadic (*args, **kwargs)
  - closures, recursion, lambda
  - visible(...) — output (like print).
  - toilet() — full program stop.
  - builtins: print, visible, toilet, len, range, int, float, str, bool, list, input, sum, min, max, sorted, reversed, enumerate, zip, all, any, abs, time_now, sleep_ms, file_read, file_write, file_append, file_delete, file_exists, sound_beep, sound_play, ceil, floor, round, pow, sqrt, exp, log, log10, sin, cos, tan, asin, acos, atan, sinh, cosh, tanh, deg2rad, rad2deg, clamp, map_range, lerp, sign, is_even, is_odd, gcd, lcm, min2, max2, chr, ord, hex, oct, bin, divmod, repr, ascii, slice, complex, dict, frozenset, issubclass, isinstance, bytes, bytearray, memoryview, format, type, callable, object, http_get, http_post, http_post_json, json_parse, json_stringify, url_encode, url_decode, html_escape, html_unescape, base64_encode, base64_decode, uuid, md5, sha1, sha256, url_parse, html_strip_tags, base64url_encode, base64url_decode, hmac_sha256, pbkdf2, jwt_encode, jwt_decode, kill

### Collections

- List: indexing, slicing, comprehensions
- Map: key-value
- Set: unique elements
- Tuple: immutable collections

### Modules

```rupt
rupt
import math
from math import sqrt
```

Module search: current directory, std/, bricks/<name>/.

### Standard Library

Modules: math, os, json, random, time, path, sys, string, collections, regex, datetime, terminal, environment, logging, files, network, http, crypto, hash, threading, process, subprocess, async, itertools, functools.

### Graphics and Sound

- `gfx_init(w, h)` — create canvas.
- `gfx_clear()` — clear canvas.
- `gfx_color("#RRGGBB")` — set color in HEX format.
- `gfx_pixel(x, y)` — pixel.
- `gfx_line(x1, y1, x2, y2)` — line segment.
- `gfx_rect(x, y, w, h)` / `gfx_fill_rect(x, y, w, h)` — rectangle / filled rectangle.
- `gfx_circle(x, y, r)` / `gfx_fill_circle(x, y, r)` — circle / filled circle.
- `gfx_show()` — render canvas to terminal.
- `gfx_save("file.ppm")` — save canvas to PPM.
- `gfx_close()` — free canvas.
- `sound_beep(freq, ms)` — beep sound.
- `sound_play("file")` — play sound (via Beep).

### Web and Networking

- `http_get(url)` — GET request, returns {status, body}.
- `http_post(url, data)` — POST request with body.
- `http_post_json(url, data)` — POST request with JSON body.
- `json_parse(str)` — parse JSON string to Map.
- `json_stringify(obj)` — serialize Map/List to JSON string.
- `url_encode(str)` — URL encoding.
- `url_decode(str)` — URL decoding.
- `html_escape(str)` — HTML escaping.
- `html_unescape(str)` — HTML unescaping.
- `base64_encode(list)` — Base64 encode list of bytes.
- `base64_decode(str)` — Base64 decode to list of bytes.
- `uuid()` — generate UUID v4.
- `md5(text)` — MD5 hash (hex string).
- `sha1(text)` — SHA1 hash.
- `sha256(text)` — SHA256 hash.
- `url_parse(url)` — parse URL into parts.
- `html_strip_tags(html)` — strip HTML tags.
- `base64url_encode(list)` — Base64URL encode.
- `base64url_decode(str)` — Base64URL decode.
- `hmac_sha256(key, msg)` — HMAC-SHA256.
- `pbkdf2(password, salt, iterations)` — PBKDF2 with HMAC-SHA256.
- `jwt_encode(header, payload, secret)` — JWT encode.
- `jwt_decode(token)` — JWT decode.

### Files

- `file_read(path)` — read file into string.
- `file_write(path, text)` — write file.
- `file_append(path, text)` — append to file.
- `file_delete(path)` — delete file.
- `file_exists(path)` — check if file exists.

### Process

- `kill(pid)` — terminate process by PID, returns true/false.

### Bricks (Packages)

```text
brick install <name>
brick remove <name>
brick update <name>
brick list
brick search <name>
brick publish
brick info <name>
```

Packages live in bricks/, registry in registry/.  
Example brick: rupt_timer.

Available Bricks: rupt_timer, rupt_math, rupt_strings, rupt_lists, rupt_maps, rupt_random, rupt_files, rupt_json, rupt_http, rupt_os, rupt_path, rupt_crypto, rupt_hash, rupt_regex, rupt_datetime, rupt_collections, rupt_itertools, rupt_functools, rupt_logging, rupt_terminal, rupt_network, rupt_process, rupt_testing, rupt_async.

### Errors

Professional output: error type, file, line, column, stack trace, suggestions.

### Language Development

Rupt grows thanks to contributors. Any contribution (code, docs, tests, ideas) helps the language evolve.

### Build

```text
build.bat
```


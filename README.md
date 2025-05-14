# 🎥 PHP Video Downloader & Converter CLI

Это CLI-приложение на PHP предназначено для скачивания видео с URL-адреса (например, с YouTube) с помощью [`yt-dlp`](https://github.com/yt-dlp/yt-dlp) и перекодирования его в `.mp4` с использованием кодека `H.264` (видео) и `AAC` (аудио), если это необходимо.

## 📦 Требования

Перед использованием убедитесь, что на вашей системе установлены следующие компоненты:

* PHP 8.1 или новее с поддержкой `CLI`
* [`yt-dlp`](https://github.com/yt-dlp/yt-dlp)
* [`ffmpeg`](https://ffmpeg.org/)
* `ffprobe` (обычно входит в состав `ffmpeg`)
* Unix-подобная система (Linux, macOS) — **скрипт не тестировался на Windows**

## 🛠 Установка

### 1. Установите зависимости:

#### PHP

Убедитесь, что PHP доступен в командной строке:

```bash
php -v
```

Если не установлен — установите его через пакетный менеджер вашей системы:

```bash
# Ubuntu/Debian
sudo apt install php-cli

# macOS (через Homebrew)
brew install php
```

#### yt-dlp

```bash
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

#### ffmpeg (и ffprobe)

```bash
# Ubuntu/Debian
sudo apt install ffmpeg

# macOS
brew install ffmpeg
```

### 2. Скачайте скрипт

Скопируйте содержимое файла в файл `video-dl`, например:

```bash
nano ~/bin/video-downloader
# вставьте код из скрипта, сохраните
```

Или скачайте файл из репозитория (если загружен в GitHub):

```bash
wget https://raw.githubusercontent.com/yourusername/video-dl/main/video-dl -O ~/bin/video-downloader
```

### 3. Сделайте файл исполняемым

```bash
chmod +x ~/bin/video-downloader
```

### 4. Сделайте скрипт доступным в любой точке системы

Выберите один из двух способов:

#### ✅ **Вариант 1 (рекомендуется): Установить в `/usr/local/bin`**

Подходит, если у вас есть root-доступ и вы хотите запускать скрипт как системную команду.

1. Переместите файл:

   ```bash
   sudo mv video-downloader /usr/local/bin/video-downloader
   ```

2. Сделайте его исполняемым:

   ```bash
   sudo chmod +x /usr/local/bin/video-downloader
   ```

Теперь вы можете вызывать скрипт из любого места:

```bash
video-downloader
```

#### 🏠 **Вариант 2: Установить в `~/bin` (для одного пользователя)**

Подходит, если вы не хотите (или не можете) использовать `sudo`.

1. Создайте папку `~/bin`, если она не существует:

   ```bash
   mkdir -p ~/bin
   ```

2. Переместите скрипт в эту папку:

   ```bash
   mv video-downloader ~/bin/video-downloader
   chmod +x ~/bin/video-downloader
   ```

3. Добавьте `~/bin` в переменную окружения `$PATH`, если он ещё не добавлен.
   Откройте `.bashrc`, `.zshrc` или `.profile` (в зависимости от используемой оболочки) и добавьте:

   ```bash
   export PATH="$HOME/bin:$PATH"
   ```

4. Примените изменения:

   ```bash
   source ~/.bashrc  # или соответствующий файл
   ```

Теперь вы тоже можете запускать скрипт как:

```bash
video-downloader
```

Перезапустите терминал или выполните:

```bash
source ~/.bashrc  # или ваш профиль
```

## 🚀 Использование

Запустите скрипт из терминала:

```bash
video-downloader
```

Вы увидите приглашение:

```
Введите URL для скачивания:
```

Вставьте URL видео. Скрипт:

1. Скачает видео с помощью `yt-dlp` в папку `~/Downloads/Videos`.
2. Определит MIME-тип и кодеки видео/аудио.
3. Если видео не в формате `.mp4` с кодеком `h264`, перекодирует его с помощью `ffmpeg`.
4. Удалит исходный файл после успешной перекодировки.

## 📁 Куда сохраняются файлы?

По умолчанию, все видео сохраняются в директорию:

```
~/Downloads/Videos
```

Если директория не существует — она будет создана автоматически.

## ✅ Поддерживаемые сайты

Благодаря `yt-dlp`, поддерживается множество сайтов, включая:

* YouTube
* Vimeo
* Facebook
* TikTok
* И сотни других

Полный список поддерживаемых сайтов можно найти [здесь](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md).

## 🛡 Безопасность

Скрипт экранирует аргументы командной строки и работает только с локальными путями, минимизируя риск инъекций. Однако **используйте его только с доверенными URL-ами**.

## 📜 Лицензия

MIT — свободно используйте, распространяйте и изменяйте.

---

Конечно! Вот точный перевод README.md на английский язык, соблюдая оригинальную структуру и формат:

---

# 🎥 PHP Video Downloader & Converter CLI

This is a PHP-based CLI application designed to download videos from a given URL (e.g., YouTube) using [`yt-dlp`](https://github.com/yt-dlp/yt-dlp) and convert them to `.mp4` format using the `H.264` video codec and `AAC` audio codec if necessary.

## 📦 Requirements

Before using the script, make sure the following components are installed on your system:

* PHP 8.1 or newer with CLI support
* [`yt-dlp`](https://github.com/yt-dlp/yt-dlp)
* [`ffmpeg`](https://ffmpeg.org/)
* `ffprobe` (usually bundled with `ffmpeg`)
* A Unix-like system (Linux, macOS) — **the script has not been tested on Windows**

## 🛠 Installation

### 1. Install dependencies:

#### PHP

Ensure that PHP is available in the command line:

```bash
php -v
```

If not installed, install it using your system’s package manager:

```bash
# Ubuntu/Debian
sudo apt install php-cli

# macOS (via Homebrew)
brew install php
```

#### yt-dlp

```bash
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

#### ffmpeg (and ffprobe)

```bash
# Ubuntu/Debian
sudo apt install ffmpeg

# macOS
brew install ffmpeg
```

### 2. Download the script

Copy the contents into a file called `video-dl`, for example:

```bash
nano ~/bin/video-downloader
# paste the script code and save
```

Or download the file from a repository (if uploaded to GitHub):

```bash
wget https://raw.githubusercontent.com/yourusername/video-dl/main/video-dl -O ~/bin/video-downloader
```

### 3. Make the file executable

```bash
chmod +x ~/bin/video-downloader
```

### 4. Make the script available system-wide

Choose one of the following two methods:

#### ✅ **Option 1 (recommended): Install to `/usr/local/bin`**

Use this if you have root access and want the script to behave like a system-wide command.

1. Move the file:

   ```bash
   sudo mv video-downloader /usr/local/bin/video-downloader
   ```

2. Make it executable:

   ```bash
   sudo chmod +x /usr/local/bin/video-downloader
   ```

Now you can run the script from anywhere:

```bash
video-downloader
```

#### 🏠 **Option 2: Install to `~/bin` (per-user setup)**

Use this if you don’t want (or can’t) use `sudo`.

1. Create the `~/bin` directory if it doesn’t exist:

   ```bash
   mkdir -p ~/bin
   ```

2. Move the script into this directory:

   ```bash
   mv video-downloader ~/bin/video-downloader
   chmod +x ~/bin/video-ddownloader
   ```

3. Add `~/bin` to your `$PATH` if it’s not already included.
   Open `.bashrc`, `.zshrc`, or `.profile` (depending on your shell) and add:

   ```bash
   export PATH="$HOME/bin:$PATH"
   ```

4. Apply the changes:

   ```bash
   source ~/.bashrc  # or the appropriate file
   ```

Now you can also run the script like this:

```bash
video-downloader
```

Restart the terminal or run:

```bash
source ~/.bashrc  # or your corresponding profile
```

## 🚀 Usage

Run the script from the terminal:

```bash
video-downloader
```

You’ll see a prompt:

```
Enter URL to download:
```

Paste the video URL. The script will:

1. Download the video using `yt-dlp` into `~/Downloads/Videos`
2. Detect the file’s MIME type and codecs
3. Convert the video using `ffmpeg` if it’s not already in `.mp4` format with the `h264` codec
4. Remove the original file after successful conversion

## 📁 Where are files saved?

By default, all videos are saved in:

```
~/Downloads/Videos
```

If the directory doesn’t exist, it will be created automatically.

## ✅ Supported websites

Thanks to `yt-dlp`, many sites are supported, including:

* YouTube
* Vimeo
* Facebook
* TikTok
* And hundreds more

Full list of supported sites is available [here](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md).

## 🛡 Security

The script escapes command-line arguments and works only with local paths, minimizing injection risks. However, **only use trusted URLs**.

## 📜 License

MIT — free to use, modify, and distribute.

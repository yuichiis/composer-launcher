# Multi-Platform Composer Wrapper for rindow/phpvenv

A set of seamless wrapper scripts (`composer.bat`, `composer.ps1`, `composer.sh`) designed to locate and execute `composer.phar` across multiple operating systems. 

These scripts natively integrate with **[rindow/phpvenv](https://github.com/rindow/phpvenv)** virtual environments by dynamically reading environment variables set inside isolated PHP configurations.

## Features

- **rindow/phpvenv Compatibility**: Automatically detects dynamically set environment variables (such as `COMPOSER_HOME`) when `php` is wrapped by virtual environment configurations.
- **Smart Resolution Fallback**: Searches for `composer.phar` in a defined order across Windows and Linux environments.
- **Cross-Platform**: Provides identical execution logic for Windows Command Prompt, PowerShell, and Linux/macOS Bash shell.
- **Transparent Argument Passing**: Forwards all command-line arguments directly to `composer.phar`.

## Resolution Order

The scripts search for `composer.phar` in the following order:

1. **Virtual Environment / Explicit Path**: Path specified inside `COMPOSER_HOME` (dynamically retrieved via `php -r "echo getenv('COMPOSER_HOME');"`).
2. **Default Composer Path**:
   - **Windows**: `%APPDATA%\Composer\composer.phar`
   - **Linux/macOS**: `$HOME/.config/composer/composer.phar`
3. **Local Directory**: `composer.phar` located in the same directory as the wrapper script.

---

## Files Included

- `composer.bat` — For Windows Command Prompt (`cmd.exe`).
- `composer.ps1` — For Windows PowerShell.
- `composer.sh` — For Linux, macOS, and WSL Bash environments.

---

## Installation & Usage

### 1. Download or Clone
Clone this repository or download the files into a directory included in your system's `PATH`, or place them directly inside your project directory.

```bash
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)

```

### 2. Set Up `composer.phar`

Place `composer.phar` into your global Composer home directory or in the same folder alongside these scripts.

### 3. Execution

#### **Windows (Command Prompt)**

```cmd
composer install

```

#### **Windows (PowerShell)**

```powershell
.\composer.ps1 install

```

*Note: If `composer.bat` is in your PATH, running `composer install` works seamlessly in PowerShell as well.*

#### **Linux / macOS (Bash)**

Grant execution permission to `composer.sh` before running:

```bash
chmod +x composer.sh
./composer.sh install

```

---

## License

This project is licensed under the [MIT License](https://www.google.com/search?q=LICENSE).


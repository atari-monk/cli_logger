# Project Documentation: Logger Utility

### 1. **Project Overview**

This project provides a flexible logging utility for Python applications, supporting both console and file logging. The logger is configurable, allowing for different logging levels and file rotation for long-running applications. It uses the `logging` module and provides a convenient setup function for configuring loggers with custom settings. The utility also supports log file rotation to prevent files from growing too large.

### 2. **Installation**

To install and use this logging utility in your Python project:

1. Ensure you have Python 3.x installed.
2. Clone or download the project files.
3. Import `setup_logger` and `LoggerConfig` from the `logger.py` file into your application.

```bash
git clone https://github.com/atari-monk/cli_logger.git
```

### 3. **Usage**

To use the logger in your Python project, follow these steps:

1. Import the necessary components from `logger.py`.
2. Configure the logger by passing custom settings to the `setup_logger` function.
3. Use the logger instance to log messages at various severity levels (DEBUG, INFO, WARNING, ERROR, CRITICAL).

#### Example Usage:

```python
import logging
from logger import setup_logger, LoggerConfig

# Custom configuration for the logger
custom_config = {
    LoggerConfig.MAIN_LEVEL: logging.DEBUG,
    LoggerConfig.CONSOLE_LEVEL: logging.DEBUG,
    LoggerConfig.FILE_LEVEL: logging.DEBUG,
    LoggerConfig.LOG_TO_FILE_FLAG: True,
    LoggerConfig.LOG_FILE_PATH: 'logs/my_project.log',
    LoggerConfig.USE_ROTATING_FILE: True,
    LoggerConfig.MAX_BYTES: 5 * 1024 * 1024,  # 5 MB
    LoggerConfig.BACKUP_COUNT: 5,
}

# Setup logger with the custom configuration
logger = setup_logger('my_project_logger', custom_config)

# Log messages with various severity levels
logger.debug("This is a debug message.")
logger.info("This is an informational message.")
logger.warning("This is a warning message.")
logger.error("This is an error message.")
logger.critical("This is a critical error message.")

# Example of an exception logging
try:
    result = 10 / 0
except ZeroDivisionError as e:
    logger.exception("An exception occurred: %s", e)
```

### 4. **Features**

-   **Flexible Logging Levels:** Supports different levels of logging (DEBUG, INFO, WARNING, ERROR, CRITICAL) for both console and file outputs.
-   **Log Rotation:** Automatically rotates log files when they exceed a specified size (`MAX_BYTES`), keeping a defined number of backup files (`BACKUP_COUNT`).
-   **Custom Configuration:** Allows for easy customization of log file paths, logging levels, and whether to log to a file or just the console.
-   **Exception Logging:** Can log exceptions with full stack traces using `logger.exception()`.

### 5. **File Structure**

The project consists of the following files:

-   `logger.py`: Contains the main logging utility, including functions for setting up the logger and configuring the loggers with custom settings.
-   `usage_example.py`: Provides a sample usage of the logger, demonstrating how to configure and log messages at different levels.

### 6. **Configuration**

The logger can be customized using a dictionary with various configuration options. Here's a breakdown of the available configuration options:

-   **LoggerConfig.MAIN_LEVEL**: The main logging level (e.g., `logging.DEBUG`, `logging.INFO`).
-   **LoggerConfig.CONSOLE_LEVEL**: The logging level for console output.
-   **LoggerConfig.FILE_LEVEL**: The logging level for file output.
-   **LoggerConfig.LOG_TO_FILE_FLAG**: Boolean flag to determine whether to log to a file.
-   **LoggerConfig.LOG_FILE_PATH**: Path to the log file (e.g., `'logs/my_project.log'`).
-   **LoggerConfig.USE_ROTATING_FILE**: Boolean flag to enable log file rotation.
-   **LoggerConfig.MAX_BYTES**: Maximum size for the log file before rotation (in bytes).
-   **LoggerConfig.BACKUP_COUNT**: Number of backup log files to keep.

### 7. **API Documentation**

The logging API is built around Python’s standard `logging` module, but with extended customization options for file logging and log rotation. Key functions include:

-   `setup_logger(name: str, config: Optional[dict] = None)`: Initializes and returns a logger with the specified name and configuration.
-   `get_default_config()`: Returns the default configuration for the logger.
-   `validate_config(config: dict)`: Validates the configuration dictionary.
-   `add_console_handler(logger: logging.Logger, formatter: logging.Formatter, config: dict)`: Adds a console handler to the logger.
-   `add_file_handler(logger: logging.Logger, formatter: logging.Formatter, config: dict)`: Adds a file handler to the logger.
-   `setup_rotating_file_handler(config: dict)`: Configures and returns a rotating file handler.
-   `setup_standard_file_handler(config: dict)`: Configures and returns a standard file handler.

### 8. **Contributing**

Contributions are welcome! If you want to contribute to the project:

1. Fork the repository.
2. Create a new branch for your changes.
3. Write tests for any new features.
4. Submit a pull request with a clear description of your changes.

### 9. **Testing**

To test the logger, simply run the `usage_example.py` script and verify that logs are written to the console and the specified log file. Check that the log file rotates after reaching the size limit.

### 10. **Changelog**

-   **v1.0.0** - Initial release with logging functionality, including file rotation and customizable configuration.
-   **v1.1.0** - Added exception logging support (`logger.exception()`).

### 11. **License**

This project is licensed under the MIT License.

### 12. **Contact/Author**

For any questions or issues, feel free to open an issue or contact the author at `atari.monk1@gmail.com`.

---

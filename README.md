# fd-open

A shell script that uses `fd` and `fzf` to incrementally search for a target file or directory and open it with a specified program.

## Dependencies

This script depends on the following tools. Please install them beforehand.

*   [fd](https://github.com/sharkdp/fd)
*   [fzf](https://github.com/junegunn/fzf)

## Installation

1.  Download the `fd-open` script from this repository.
2.  Grant execute permission to the downloaded `fd-open` file.
    ```sh
    chmod +x fd-open
    ```
3.  Move `fd-open` to a directory in your PATH, such as `~/.local/bin`.
    ```sh
    mv fd-open ~/.local/bin/
    ```

## Usage

The basic syntax is `fd-open <program> <pattern>`.

**Examples:**

Open a directory whose name contains `my-project` with `zed`.
```sh
fd-open zed my-project
```

Open a file whose name contains `main.c` with `vim`.
```sh
FDO_FD_OPTIONS='-t f' fd-open vim main.c
```

[![asciicast](https://asciinema.org/a/WSAQPCCDQPWqaTdcaojtiblf7.svg)](https://asciinema.org/a/WSAQPCCDQPWqaTdcaojtiblf7)

### `FDO_FD_OPTIONS` Environment Variable

You can specify options to pass to the `fd` command using the `FDO_FD_OPTIONS` environment variable.
By default, it is set to `-t d` (search for directories only).

If you want to search for files only, specify `-t f`.

```sh
FDO_FD_OPTIONS='-t f' fd-open nvim config.toml
```

### Alias Configuration

Since typing the options every time can be a hassle, it is useful to define aliases in your shell's configuration file (e.g., `.bashrc` or `.zshrc`).

```sh
# Basic alias
alias f="fd-open"

# Alias for file search
alias ff="FDO_FD_OPTIONS='-t f' fd-open"
```

This allows you to run commands more concisely:

```sh
# Open a directory with Zed
f zed my-project

# Open a file with Vim
ff vim my-file.txt
```

## License

This project is licensed under the [MIT License](LICENSE).

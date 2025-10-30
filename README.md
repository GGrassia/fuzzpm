# Fuzzpm

A fuzzy search, minimal package browser for APT systems.

## Features

- Fast and beautiful fuzzy search for Debian/Ubuntu packages
- Interactive package browsing with fzf
- Direct package installation and removal
- Automatic cache management
- Keyboard shortcuts for common operations
- Optional preview of package details

## Installation

### From Package (Recommended)

1. Download the latest .deb package from the releases page, install the deb from the package manager. Alternatively:
2. Install with:
   ```bash
   sudo dpkg -i fuzzpm.deb
   sudo apt install -f  # Fix any dependencies if needed
   ```

### From Source

1. Clone this repository:
   ```bash
   git clone https://github.com/GGrassia/fuzzpm.git
   cd fuzzpm
   ```

2. Build the package:
   ```bash
   dpkg-deb --build .
   ```

3. Install the package:
   ```bash
   sudo dpkg -i ../fuzzpm.deb
   sudo apt install -f  # Fix any dependencies if needed
   ```

## Dependencies

- fzf (required)
- apt (required)
- bat (optional, for better preview formatting)

Install dependencies with:
```bash
sudo apt install fzf apt bat
```

## Usage

### Basic Usage

Simply run:
```bash
sudo fpm
```

This will open an interactive package browser where you can:

- Search for packages using fuzzy search
- Preview package details
- Install or remove packages

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| Enter | Install selected package |
| Ctrl-U | Uninstall selected package |
| Ctrl-H | Show package details in pager |
| Ctrl-C | Exit |

### Command Line Options

```bash
fpm [OPTIONS]
```

Options:
- `-h, --help`: Show help message
- `-r, --refresh`: Refresh package cache (requires sudo)
- `-c, --config`: Open configuration file

## Cache Management

Fuzzpm maintains a cache of packages at `/var/cache/fuzzpm/packages.txt` for faster searching. The cache is automatically:

- Updated when you install or remove packages
- Created during initial installation
- Updated when running `sudo fpm --refresh`

If the cache is missing, fpm will prompt you to run `sudo fpm --refresh`.

## Configuration

Configuration is stored in `~/.config/fuzzpm/config`. Currently, this file is a placeholder for future configuration options.

## How It Works

1. **Cache Generation**: Fuzzpm generates a package list using `apt-cache search .`
2. **Fuzzy Search**: Uses fzf to provide fast, interactive fuzzy searching
3. **Package Operations**: Directly calls apt install/remove with sudo privileges
4. **Automatic Updates**: The APT hook automatically updates the cache when packages are installed or removed

## Troubleshooting

### Cache Issues

If you encounter cache-related issues:
1. Refresh the cache: `sudo fpm --refresh`
2. Or manually regenerate: `sudo apt update && sudo fpm --refresh`

### Permission Issues

Make sure you have sudo privileges for package operations.

### FZF Issues

Ensure fzf is properly installed and configured:
```bash
sudo apt install fzf
```

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Author

Created by Giulio Grassia

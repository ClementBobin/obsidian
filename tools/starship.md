# Starship Prompt

Starship is a minimal, blazing-fast, and infinitely customizable prompt for any shell. It provides a modern, feature-packed prompt with a minimalistic design to enhance your terminal experience.

- **Project Homepage**: [Starship: Cross-Shell Prompt](https://starship.rs/)
    
- **Documentation**: [Configuration | Starship](https://starship.rs/config/)
    

---

## 🔧 Installation

### For Linux

To install Starship on your Linux system, follow these steps:

1. **Install Starship**: Run the following command to install the latest version of Starship:
    
    ```bash
    curl -sS https://starship.rs/install.sh | sh
    ```
    
2. **Configure your shell**: After installation, add the following line to the end of your shell configuration file:
    
    - For **Bash** (`~/.bashrc`):
        
        ```bash
        eval "$(starship init bash)"
        ```
        
    - For **Zsh** (`~/.zshrc`):
        
        ```bash
        eval "$(starship init zsh)"
        ```
        
3. **Apply the configuration**: After adding the configuration to your shell's config file, restart the shell or run:
    
    ```bash
    source ~/.bashrc  # for bash # or source ~/.zshrc   # for zsh
    ```
    

---

## 🛠️ Configuration

You can customize Starship's appearance and functionality via the configuration file. Here's how to start:

1. **Create a configuration file**: The configuration file is located at `~/.config/starship.toml`. If it doesn't exist, you can create it.
    
2. **Customize Prompt Settings**: Starship provides a wide range of customization options, from changing colors to adding new modules. The [official documentation](https://starship.rs/config/) provides detailed guidance on how to customize your prompt.
    

---

## 🏆 Key Features

- **Minimal and Fast**: Starship is designed to be fast and lightweight, without compromising on functionality.
    
- **Cross-Shell Support**: Works with various shells, including Bash, Zsh, Fish, and others.
    
- **Highly Customizable**: Personalize your prompt with custom settings, colors, and modules.
    
- **Extensive Module System**: Modules for displaying useful information such as Git status, system info, and more.
    
- **Unicode Support**: Fully supports Unicode characters for a rich and modern terminal experience.
    

---

## 🔗 Related

- **[Oh-My-Zsh](https://github.com/ohmyzsh/ohmyzsh)**: A framework for managing Zsh configurations, with several themes and plugins.
    
- **[Powerlevel10k](https://github.com/romkatv/powerlevel10k)**: A Zsh theme that offers a high degree of customization and fast performance.
    
- **[Fish Shell](https://fishshell.com/)**: A user-friendly shell with a focus on discoverability and ease of use.
    

---

## 🔍 Explore More

- **Zsh Configuration**: Learn how to configure and optimize Zsh for your environment.
    
- **Bash Prompt Customization**: A guide to customizing Bash prompts.
    

---

## 🏷️ Tags

#starship #shell #linux #bash #zsh #terminal #customization #prompt

---

## 📚 Resources

- **Starship Documentation**: Official guide to installation, configuration, and advanced customization options.
    
- **Starship Configuration Examples**: A collection of examples to get started with configuring your prompt.
    
- **[GitHub Repository](https://github.com/starship/starship)**: Source code and contributions for Starship.
    
- **Terminal Color Codes**: A handy reference for customizing colors in Starship.
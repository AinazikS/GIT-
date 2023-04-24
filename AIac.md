# Install brew command

> Run terminal and then first, issue an update command-



```
sudo apt update
```
```
sudo apt-get install build-essential
```

> Run Homebrew installation script

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> To run the brew command after installation, we need to add it to our system path…

```
(echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/user/.bashrc
```
```
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```
> To ensure everything is working correctly to use brew, we can run its command-

```
brew doctor
```
# Installation of AIac by Firefly

```
brew install gofireflyio/aiac/aiac
```
# EXPORT API key


```
export OPENAI_API_KEY=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
```

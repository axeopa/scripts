# base config for linux mint workstation

## install packages
```
sudo add-apt-repository -y ppa:slgobinath/safeeyes

sudo apt-get update
sudo apt-get install -y \
clipit \
flameshot \
git \
gitg \
htop \
safeeyes \
silversearcher-ag \
terminator \
tig \
tree

cp -rf .themes ~/.themes

echo "PS1='\[\033[1;36m\]\u\[\033[1;31m\]@\[\033[1;32m\]\h:\[\033[1;35m\]\w\[\033[1;31m\]$\[\033[0m\]'" >> ~/.bashrc
```


## vs code 

### install vs code
[code doc](https://code.visualstudio.com/docs/setup/linux)


### plugins install

press **Ctrl+Shift+X**

```
ext install ms-python.python
ext install VisualStudioExptTeam.vscodeintellicode
ext install CoenraadS.bracket-pair-colorizer
ext install yzhang.markdown-all-in-one
ext install ms-azuretools.vscode-docker
ext install streetsidesoftware.code-spell-checker
ext install eamodio.gitlens
ext install donjayamanne.githistory
ext install esbenp.prettier-vscode
ext install FallenMax.mithril-emmet
ext install pnp.polacode
ext install 4ops.terraform
ext install ms-kubernetes-tools.vscode-kubernetes-tools
ext install redhat.vscode-yaml
```

## terminator config

```
cat terminator.conf > ~/.config/terminator/config
```

## install neovim

```
sudo apt-get install neovim

curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

[ -d ~/.config/nvim/ ] || mkdir ~/.config/nvim/
cp init.vim ~/.config/nvim/init.vim

nvim +PlugInstall +qall
```


## install terminal themes

```
cd ~/coding/
git clone https://github.com/chriskempson/base16-xfce4-terminal
cd base16-xfce4-terminal
./convert2themes
sudo cp themes/*.theme /usr/share/xfce4/terminal/colorschemes/
rm -rf ~/coding/base16-xfce4-terminal
```

## k8s stuff

```
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version --client
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

curl -o aws-iam-authenticator https://amazon-eks.s3.us-west-2.amazonaws.com/1.16.8/2020-04-16/bin/linux/amd64/aws-iam-authenticator
chmod +x ./aws-iam-authenticator
sudo mv aws-iam-authenticator /usr/bin/
```
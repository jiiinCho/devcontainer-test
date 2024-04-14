ARG VARIANT="18-bookworm"
FROM mcr.microsoft.com/devcontainers/typescript-node:1-${VARIANT}

# Configure apt
# ENV DEBIAN_FRONTEND=noninteractive

# Installing additional OS Packages
RUN apt-get update \
    && apt-get -y install --no-install-recommends 
#     curl \
#     git-core \
#     gnupg \
#     linuxbrew-wrapper \
#     locales \
#     zsh \
#     wget \
#     tree \
#     jq \
#     fonts-powerline \
#     # set up locale
#     && locale-gen en_US.UTF-8 && fc-cache -vf

# ENV DEBIAN_FRONTEND=dialog
# ENV SHELL=/bin/zsh

# Use Yarn 2
RUN yarn set version berry

# ARG USER="node"
# ARG GROUP="node"

# USER ${USER}

# # Make variables available in Shell Env
# ENV USER=${USER}
# ENV GROUP=${GROUP}

# # Install Oh-my-ZSH
# RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true

# # Install powerlevel10k
# RUN git clone https://github.com/romkatv/powerlevel10k.git /home/${USER}/.oh-my-zsh/custom/themes/powerlevel10k

# ADD --chown=${USER}:${GROUP} .zshrc /home/${USER}

# # Configure Linuxbrew
# RUN brew update || true
# # Install handy plugins
# RUN brew install zsh-autosuggestions zsh-syntax-highlighting

# # Restore cache ownership
# RUN sudo chown -R ${USER}:${GROUP} ~/.cache

# Set the working directory
WORKDIR /workspaces

# Copy package.json and yarn.lock to the working directory
COPY package.json yarn.lock ./

# Install dependencies
RUN yarn install

# Copy the rest of the application code
COPY . .

# Set the command to run the development server
# CMD ["yarn", "dev"]
# Padronizando mensagens de commit do Git

## Configurações:

- ### [Commitlint](https://github.com/conventional-changelog/commitlint)
  Instalação:
  ```bash
    # For Windows:
    npm install --save-dev @commitlint/config-conventional @commitlint/cli

    # Configure commitlint to use conventional config
    echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
  ```
  Para fazer o lint de commits antes de serem criados, você pode usar o hook `commit-msg` do Husky:

  !!! - ⚠️ Antes de continuar, inicie o repositório local em seu projeto. `git init`
    
    ```bash
      # Install Husky v6
      npm install husky --save-dev
      # or
      yarn add husky --dev

      # Activate hooks
      npx husky install
      # or
      yarn husky install
    ```
  Adicionando hook:
  ```sh
    npx husky add .husky/commit-msg

    # adicinar os commandos abaixo no arquivo .husky/commit-msg
      #!/bin/sh
      . "$(dirname "$0")/_/husky.sh"

      npx commitlint --edit $1
  ```
- ### [Commitizen](https://github.com/commitizen/cz-cli)
  Instalação:
  ```bash
    npm install --save-dev commitizen
  ```
  Em seguida, inicialize seu projeto para usar o adaptador cz-conventional-changelog digitando:
  ```bash
    #npm
    npx commitizen init cz-conventional-changelog --save-dev --save-exact

    #yarn
    yarn commitizen init cz-conventional-changelog --yarn --dev --exact
  ```
  Agora, basta usar o comando `cz` para gerar o changelog:
  ```json
    //package.json

    "scripts": {
      "commit": "git-cz"
    }

---
Feito com ❤️ por [@brhcastro](https://linkedin.com/in/brhcastro).
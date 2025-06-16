# Gerenciamento de versões Node

## O que é o NVM?

O **NVM**, ou _Node Version Manager_, é um script de linha de comando que permite que você instale, gerencie e alterne entre múltiplas versões do Node.js em uma única máquina.

Imagine este cenário:

* O **Projeto A** é um sistema legado que só funciona com a versão **Node.js 14 LTS**.
* O **Projeto B** é um novo projeto que você está iniciando e quer usar todos os recursos da versão mais recente, a **Node.js 20 LTS**.

Sem o NVM, você teria que desinstalar uma versão para instalar a outra toda vez que fosse trocar de projeto. Com o NVM, essa troca é feita com um único comando no terminal.

***

#### Por que usar o NVM?

* **Flexibilidade:** Alterne entre versões do Node.js com um comando simples, sem precisar de privilégios de administrador.
* **Isolamento:** As versões são instaladas em um diretório específico do seu usuário, evitando conflitos com a versão de Node.js do sistema (se houver).
* **Compatibilidade de Projetos:** Garanta que cada projeto rode com a versão exata do Node.js para a qual foi desenvolvido, evitando o clássico "mas na minha máquina funciona".
* **Facilidade para Testes:** Teste a compatibilidade da sua biblioteca ou aplicação em diferentes versões do Node.js de forma rápida e eficiente.

***

#### Instalação

O processo de instalação varia um pouco entre os sistemas operacionais.

**Linux e macOS**

Para ambientes baseados em Unix, como Linux e macOS, a forma mais comum é usar um script de instalação via `curl` ou `wget`. Abra seu terminal e execute:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

_Observação: É uma boa prática verificar o site oficial do NVM para a versão mais recente do script de instalação._

Após a instalação, feche e reabra seu terminal para que as alterações tenham efeito.

**Windows**

No Windows, o projeto recomendado é o **nvm-windows**. Ele não é o mesmo NVM, mas cumpre o mesmo propósito.

1. Vá para a [página de releases do nvm-windows no GitHub](https://github.com/coreybutler/nvm-windows/releases).
2. Baixe o instalador mais recente (ex: `nvm-setup.zip`).
3. Extraia o arquivo e execute o instalador.

O instalador cuidará de tudo para você. Após a instalação, abra um novo terminal (Prompt de Comando ou PowerShell).

***

#### Comandos Essenciais do NVM

Aqui estão os comandos que você mais usará no seu dia a dia.

*   **Listar todas as versões remotas disponíveis para instalação:**

    ```bash
    nvm ls-remote
    ```
*   **Instalar uma versão específica do Node.js:**

    ```bash
    nvm install 20.14.0
    ```
*   **Instalar a versão LTS (Long Term Support) mais recente:**

    ```bash
    nvm install --lts
    ```
*   **Listar todas as versões que você já tem instaladas:**

    ```bash
    nvm ls
    ```

    O resultado mostrará as versões instaladas e indicará com uma seta `->` qual está em uso no momento.
*   **Alternar para uma versão instalada:**\
    Este é o comando principal! Para começar a usar uma versão em seu terminal atual:

    ```bash
    nvm use 20.14.0
    ```
*   **Definir uma versão padrão para novos terminais:**

    ```bash
    nvm alias default 20.14.0
    ```

***

#### Automatizando a Versão por Projeto com `.nvmrc`

Uma das melhores práticas ao trabalhar com NVM é criar um arquivo chamado `.nvmrc` na raiz do seu projeto. Dentro desse arquivo, você escreve apenas a versão do Node.js que o projeto deve usar.

**Exemplo de arquivo `.nvmrc`:**

```
20.14.0
```

Com esse arquivo na pasta do seu projeto, sempre que você entrar no diretório pelo terminal, pode simplesmente digitar:

```bash
nvm use
```

O NVM irá ler o arquivo `.nvmrc` e automaticamente mudará para a versão especificada. Isso garante que toda a equipe use a mesma versão do Node.js, tornando o ambiente de desenvolvimento consistente para todos.

***

#### Snippet de Código para Ilustrar

Vamos supor que queremos usar o `fetch` nativo do Node.js, que foi estabilizado a partir da versão 18.

```javascript
// app.js
// Este script usa a API fetch, que é estável no Node.js v18+

async function getPosts() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts/1');
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    const post = await response.json();
    console.log('Post encontrado:', post);
  } catch (error) {
    console.error('Falha ao buscar post:', error);
  }
}

getPosts();
```

**Como testar a importância do NVM com este código:**

1.  **Use uma versão antiga:**

    ```bash
    nvm use 16.0.0
    node app.js 
    # Provavelmente resultará em um erro: "ReferenceError: fetch is not defined"
    ```
2.  **Use a versão correta:**

    ```bash
    nvm use 20.14.0 # ou qualquer versão >= 18
    node app.js
    # O código será executado com sucesso e exibirá o post.
    ```

Este exemplo prático demonstra por que forçar uma versão específica do Node.js é crucial para a estabilidade de um projeto.

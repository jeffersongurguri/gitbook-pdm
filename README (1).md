# 1. Introdução

Para começarmos com o pé direito, convidamos vocês a se familiarizarem com algumas tecnologias e conceitos fundamentais que encontraremos frequentemente em nosso caminho. A leitura destas definições rápidas ajudará a construir uma base sólida para os nossos próximos passos.



## React

ReactJS, uma **biblioteca** JavaScript do Facebook (hoje Meta), revoluciona a criação de interfaces de usuário (UI) dinâmicas para web e mobile. Sua popularidade explodiu desde o lançamento em 2013, figurando entre as ferramentas de front-end mais adotadas mundialmente.

A chave do React está em sua abordagem baseada em "componentes": a interface é construída a partir de peças menores e reutilizáveis, tornando o código inerentemente mais modular, simples de gerenciar e otimizado em performance.

A influência do ReactJS se estende significativamente para além do ecossistema JavaScript, moldando a forma como interfaces de usuário (UI) são concebidas e desenvolvidas em diversas tecnologias e plataformas. Seus conceitos e padrões arquiteturais provaram ser tão eficazes que foram adotados e adaptados em outras linguagens e frameworks.



**Componentes: A Essência do React**

No cerne do React, encontramos os componentes. Cada componente representa um bloco de código autocontido, responsável por gerenciar sua própria estrutura (HTML), lógica (JavaScript) e apresentação visual (CSS). A abordagem baseada em componentes simplifica significativamente a reutilização de código e facilita a manutenção de aplicações extensas e complexas.

**Virtual DOM: O Motor da Eficiência**

Uma das características distintivas que conferiram ao React sua notável eficiência é a implementação do Virtual DOM. Em vez de manipular diretamente o DOM do navegador – uma operação dispendiosa em termos de performance –, o React mantém uma representação do DOM na memória. Quando o estado de um componente se altera, o React compara essa nova representação virtual com a anterior e aplica as modificações necessárias apenas nos elementos correspondentes do DOM real.

**Fluxo de Dados Unidirecional: Previsibilidade e Depuração Facilitada**

O React emprega um modelo de fluxo de dados unidirecional. Isso implica que os dados e o estado da aplicação seguem um único sentido, o que torna o código mais previsível e simplifica o processo de depuração. Essa arquitetura é particularmente vantajosa em aplicações com uma lógica de estado intrincada.

**JSX: Sintaxe Intuitiva para a Interface do Usuário**

O React utiliza JSX, uma extensão de sintaxe que permite escrever a estrutura da interface do usuário de maneira similar ao HTML, diretamente dentro do código JavaScript. Essa característica melhora a legibilidade e a compreensão do código.

**Flexibilidade e um Ecossistema Rico**

O React se destaca por sua flexibilidade, não impondo diretrizes rígidas sobre a estrutura da sua aplicação ou as tecnologias a serem utilizadas em conjunto. Essa adaptabilidade permite uma integração fluida com diversas bibliotecas e frameworks. Adicionalmente, o ecossistema do React é vasto e vibrante, contando com uma grande comunidade de desenvolvedores e uma vasta gama de bibliotecas e ferramentas disponíveis. É importante lembrar que, embora esses conceitos possam parecer complexos agora, eles serão detalhadamente explorados ao longo deste material, capacitando você a utilizar o React com confiança.

Para saber mais: [https://react.dev/](https://react.dev/)

## Vite

**Vite** é uma ferramenta de build para frontend que visa proporcionar uma experiência de desenvolvimento **rápida e eficiente** para aplicações web modernas. Criado por Evan You (o mesmo criador do Vue.js), o Vite se destaca por seu **servidor de desenvolvimento instantâneo** e **Hot Module Replacement (HMR) extremamente veloz**, independentemente do tamanho da aplicação.

Por que é usar vite com react?

* desenvolvimento ágil.
* fácil de configurar
* amigável para desenvolvedores

Para saber mais: [https://vite.dev/](https://vite.dev/)

## React Native

React Native é uma biblioteca JavaScript desenvolvida pelo Facebook que permite criar aplicativos móveis multiplataforma. Isso significa que você pode escrever seu código uma vez e usá-lo em dispositivos iOS e Android. Não é necessário aprender duas linguagens de programação diferentes.

### Por que escolher React Native?

1. Eficiência de Desenvolvimento: O React Native é conhecido por sua eficiência. Ele permite que você desenvolva aplicativos mais rapidamente em comparação com a abordagem tradicional de desenvolvimento nativo.
2. Reutilização de Código: Como mencionado, você pode reutilizar grande parte do seu código em diferentes plataformas, economizando tempo e esforço.
3. Comunidade Ativa: React Native tem uma comunidade grande e ativa de desenvolvedores. Isso significa que há uma tonelada de recursos, bibliotecas e soluções disponíveis para ajudar você em sua jornada.
4. Performance: Embora não seja tão rápido quanto o desenvolvimento nativo em termos de desempenho puro, o React Native oferece um desempenho muito bom para a maioria dos aplicativos, e a diferença geralmente não é perceptível para os usuários.

### Como Funciona o React Native?

React Native funciona com componentes. Em vez de criar interfaces de usuário usando ferramentas de criação visual, você cria seu aplicativo dividindo-o em pequenos componentes reutilizáveis. Cada componente tem sua própria lógica e estilo.

A biblioteca React Native cuida de traduzir esses componentes em elementos nativos do iOS e Android, garantindo que seu aplicativo pareça e funcione como um aplicativo nativo, apesar de ser construído com JavaScript.

### Já ouvi falar de React, mas não de React Native

React e React Native são tecnologias relacionadas que compartilham princípios fundamentais, mas são destinadas a diferentes plataformas de desenvolvimento.

**React** (também chamado de React.js ou ReactJS) é uma biblioteca JavaScript criada pelo Facebook para construir interfaces de usuário para aplicações web. O React introduziu:

* Um modelo declarativo para definir interfaces
* Componentes reutilizáveis
* O Virtual DOM para renderização eficiente
* O fluxo de dados unidirecional
* JSX como sintaxe para misturar marcação com lógica

**React Native** é um framework baseado no React, mas focado na criação de aplicativos móveis nativos para iOS e Android. O React Native aplica a filosofia do React ao desenvolvimento móvel.

### Princípios Compartilhados

1. **Arquitetura baseada em componentes** - Ambos usam componentes como blocos de construção fundamentais
2. **Fluxo de dados unidirecional** - Props fluem de componentes pais para filhos
3. **Virtual DOM** - React usa Virtual DOM para web; React Native usa "shadow nodes" para se comunicar com APIs nativas
4. **Sintaxe JSX** - Ambos utilizam JSX para definir a estrutura da interface
5. **Ciclo de vida dos componentes** - Ambos seguem padrões similares para gerenciar o ciclo de vida dos componentes
6. **Hooks** - Ambos suportam Hooks (useState, useEffect, etc.) para gerenciamento de estado e efeitos

Na prática, se você conhece React, já tem uma grande vantagem para aprender React Native, pois a lógica de como construir componentes, gerenciar estados e trabalhar com props é praticamente idêntica. A principal adaptação está no uso de componentes específicos para mobile e nas diferenças de estilização.

Um desenvolvedor React pode transferir muitos conceitos e habilidades para o React Native, tornando a curva de aprendizado mais suave para quem já trabalha com a biblioteca web.

Para saber mais: [https://reactnative.dev/](https://reactnative.dev/)

## Expo

Expo é um conjunto de ferramentas, bibliotecas e serviços construídos em torno do React Native que permite desenvolver, compilar, implantar e iterar rapidamente em aplicativos iOS, Android e web, tudo a partir de uma única base de código JavaScript/TypeScript.

Para saber mais: [https://expo.dev/](https://expo.dev/)

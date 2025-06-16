# Resumo - RN

## Apostila React Native

Esta apostila serve como um guia de referência rápida para os **fundamentos do React Native**. Ela foi criada inicialmente para estudantes do curso React Native Bootcamp da Zero To Mastery, mas está sendo compartilhada com todos os desenvolvedores que desejam aprender e relembrar informações e conceitos chave do React Native.

Se você está começando a aprender React Native, você fez uma ótima escolha para se tornar um **Desenvolvedor Mobile**.

### Sumário

1. Configuração
2. Componentes Essenciais
3. Estilização
4. Layout Flexbox
5. Estado e Props
6. Manipulação de Eventos
7. Listas
8. Navegação
9. Rede
10. Código Específico da Plataforma
11. Animações
12. Hooks
13. Bibliotecas de Terceiros
14. Depuração
15. Comandos Úteis
16. TypeScript no React Native
17. Testes
18. Acessibilidade
19. Permissões
20. APIs de Dispositivo
21. Armazenamento Offline
22. Otimização de Desempenho
23. Internacionalização (i18n)
24. Tratamento de Erros
25. Melhores Práticas

***

### 1. Configuração

O **Expo CLI** oferece uma maneira conveniente de iniciar projetos React Native.

*   **Instalar Expo CLI**:

    ```bash
    npm install -g expo-cli
    ```
*   **Criar um Novo Projeto**:

    ```bash
    expo init MyApp
    cd MyApp
    npm start
    ```

### 2. Componentes Essenciais

React Native oferece um conjunto de **componentes essenciais** para a construção de interfaces de usuário.

* **Componentes Básicos**:
  * **View**: O componente fundamental para construir UI, **similar a uma `div` em HTML**.
  * **Text**: Usado para exibir texto.
  * **Image**: Exibe imagens.
  * **ScrollView**: Um **contêiner rolável** para views.
  * **TextInput**: Para campos de entrada de texto.
  * **TouchableOpacity**: Para envolver componentes e torná-los **sensíveis ao toque**.
*   **Exemplo**:

    ```javascript
    import React from 'react';
    import { View, Text, Image } from 'react-native';

    const App = () => (
      <View>
        <Text>Hello, World!</Text>
        <Image source={{ uri: 'https://example.com/image.png' }} style={{ width: 100, height: 100 }} />
      </View>
    );

    export default App;
    ```

### 3. Estilização

React Native usa **objetos JavaScript para estilização**, similar a estilos inline em HTML, mas com uma sintaxe semelhante a CSS.

*   **Exemplo**:

    ```javascript
    const styles = {
      container: {
        flex: 1,
        backgroundColor: '#fff',
        alignItems: 'center',
        justifyContent: 'center',
      },
    };

    <View style={styles.container}>
      <Text style={{ color: 'blue', fontSize: 20 }}>Styled Text</Text>
    </View>
    ```
* **Unidades**: Todas as unidades são **pixels independentes de densidade (dp)**.
* **Nomes de Propriedade**: Use **camelCase** (ex: `backgroundColor`).

### 4. Layout Flexbox

React Native utiliza **Flexbox para layout**, oferecendo uma maneira poderosa de organizar componentes.

* **Propriedades Comuns do Flexbox**:
  * **flexDirection**: Determina o **eixo principal** (`'row'` ou `'column'`).
  * **justifyContent**: Alinha os filhos ao longo do **eixo principal**.
  * **alignItems**: Alinha os filhos ao longo do **eixo secundário**.
  * **flex**: Determina como um componente cresce ou encolhe.
*   **Exemplo**:

    ```javascript
    <View style={{ flex: 1, flexDirection: 'row' }}>
      <View style={{ flex: 1, backgroundColor: 'red' }} />
      <View style={{ flex: 2, backgroundColor: 'green' }} />
      <View style={{ flex: 3, backgroundColor: 'blue' }} />
    </View>
    ```

### 5. Estado e Props

*   **Props**:

    * **Props (propriedades) são entradas para componentes**, permitindo que os dados sejam passados do componente pai para o filho.

    ```javascript
    const Greeting = (props) => (
      <Text>Hello, {props.name}!</Text>
    );

    <Greeting name="Alice" />
    ```
*   **Estado (State)**:

    * **O estado permite que os componentes criem e gerenciem seus próprios dados**.

    ```javascript
    import React, { useState } from 'react';
    import { View, Text, Button } from 'react-native';

    const Counter = () => {
      const [count, setCount] = useState(0);
      return (
        <View>
          <Text>You clicked {count} times</Text>
          <Button onPress={() => setCount(count + 1)} title="Click me" />
        </View>
      );
    };
    ```

### 6. Manipulação de Eventos

Eventos são manipulados usando **funções de callback passadas como props**.

*   **Exemplo**:

    ```javascript
    <Button onPress={() => { alert('Button pressed!'); }} title="Press Me" />
    ```
* **Manipuladores de Eventos Comuns**:
  * **onPress**: Acionado quando um componente é pressionado.
  * **onChangeText**: Usado com `TextInput` para lidar com **mudanças de texto**.
  * **onSubmitEditing**: Acionado quando o usuário **envia a entrada de texto**.

### 7. Listas

*   **FlatList**:

    * A maneira **ideal de renderizar listas de dados roláveis**. Possui várias propriedades ajustáveis para **renderização mais eficiente**.

    ```javascript
    import { FlatList, Text } from 'react-native';

    <FlatList
      data={[{ key: 'Alice' }, { key: 'Bob' }]}
      renderItem={({ item }) => <Text>{item.key}</Text>}
    />
    ```
*   **SectionList**:

    * Para **renderizar seções com cabeçalhos**.

    ```javascript
    import { SectionList, Text } from 'react-native';

    <SectionList
      sections={[
        { title: 'A', data: ['Alice', 'Alan'] },
        { title: 'B', data: ['Bob', 'Bill'] },
      ]}
      renderItem={({ item }) => <Text>{item}</Text>}
      renderSectionHeader={({ section }) => <Text>{section.title}</Text>}
    />
    ```

### 8. Navegação

**React Navigation** é a biblioteca padrão para lidar com a navegação em aplicativos React Native. É recomendado utilizar o **native stack navigator para uma experiência nativa completa e benefícios de desempenho**.

*   **Instalação**:

    ```bash
    npm install @react-navigation/native
    npm install @react-navigation/native-stack expo install react-native-screens react-native-safe-area-context
    ```
*   **Exemplo**:

    ```javascript
    import * as React from 'react';
    import { Button, View, Text } from 'react-native';
    import { NavigationContainer } from '@react-navigation/native';
    import { createNativeStackNavigator } from '@react-navigation/native-stack';

    function HomeScreen({ navigation }) {
      return (
        <Button
          title="Go to Details"
          onPress={() => navigation.navigate('Details')}
        />
      );
    }

    function DetailsScreen() {
      return (
        <View>
          <Text>Details Screen</Text>
        </View>
      );
    }

    const Stack = createNativeStackNavigator();

    export default function App() {
      return (
        <NavigationContainer>
          <Stack.Navigator initialRouteName="Home">
            <Stack.Screen name="Home" component={HomeScreen} />
            <Stack.Screen name="Details" component={DetailsScreen} />
          </Stack.Navigator>
        </NavigationContainer>
      );
    }
    ```

### 9. Rede

Use a **API `fetch` ou bibliotecas como `axios`** para requisições de rede.

*   **Exemplo com Fetch**:

    ```javascript
    import React, { useEffect, useState } from 'react';
    import { FlatList, Text } from 'react-native';

    const FetchExample = () => {
      const [data, setData] = useState([]);

      useEffect(() => {
        fetch('https://example.com/data')
          .then((response) => response.json())
          .then((json) => setData(json.items))
          .catch((error) => console.error(error));
      }, []);

      return (
        <FlatList
          data={data}
          renderItem={({ item }) => <Text>{item.name}</Text>}
          keyExtractor={(item) => item.id.toString()}
        />
      );
    };
    ```

### 10. Código Específico da Plataforma

Use o **módulo `Platform` para renderizar código condicionalmente com base na plataforma**.

*   **Exemplo**:

    ```javascript
    import { Platform, Text } from 'react-native';

    const instructions = Platform.select({
      ios: 'Press Cmd+R to reload',
      android: 'Double tap R on your keyboard to reload',
    });

    <Text>{instructions}</Text>
    ```
* **Platform.OS**: Retorna `'ios'`, `'android'` ou `'web'`.

### 11. Animações

React Native oferece a **API `Animated` para criar animações**.

*   **Exemplo**:

    ```javascript
    import React, { useRef, useEffect } from 'react';
    import { Animated, Text } from 'react-native';

    const FadeInView = (props) => {
      const fadeAnim = useRef(new Animated.Value(0)).current; // Initial opacity value

      useEffect(() => {
        Animated.timing(fadeAnim, {
          toValue: 1, // Fade to opacity 1
          duration: 1000,
          useNativeDriver: true,
        }).start();
      }, [fadeAnim]);

      return (
        <Animated.View style={{ opacity: fadeAnim }}>
          {props.children}
        </Animated.View>
      );
    };

    <FadeInView>
      <Text>Fading in</Text>
    </FadeInView>;
    ```

### 12. Hooks

React Native suporta **React Hooks para gerenciamento de estado e ciclo de vida**.

*   **useState**:

    ```javascript
    import React, { useState } from 'react';
    const [value, setValue] = useState(initialValue);
    ```
*   **useEffect**:

    ```javascript
    import React, { useEffect } from 'react';
    useEffect(() => {
      // Perform side effects here
      return () => {
        // Cleanup if necessary
      };
    }, [dependencies]);
    ```

### 13. Bibliotecas de Terceiros

Instale bibliotecas adicionais usando `npm` ou `yarn`.

*   **Exemplo: Usando Axios**:

    ```bash
    npm install axios
    ```

    ```javascript
    import axios from 'axios';
    axios.get('https://example.com/data')
      .then((response) => {
        // Handle success
      })
      .catch((error) => {
        // Handle error
      });
    ```

### 14. Depuração

* **Registro (Logging)**: Use `console.log()` para depuração.
* **Menu do Desenvolvedor**: Agite seu dispositivo ou pressione **`Ctrl + M` (ou `Cmd + M` no Mac)** para abrir o menu do desenvolvedor.
* **Ferramentas de Depuração**: Use o **React Native Debugger ou Chrome DevTools**.

### 15. Comandos Úteis

*   **Iniciar o Servidor de Desenvolvimento**:

    ```bash
    npm start
    ```
*   **Executar no Emulador Android**:

    ```bash
    npm run android
    ```
*   **Executar no Simulador iOS**:

    ```bash
    npm run ios
    ```
*   **Compilar APK (Android)**:

    ```bash
    expo build:android
    ```
*   **Compilar IPA (iOS)**:

    ```bash
    expo build:ios
    ```

### 16. TypeScript no React Native

TypeScript adiciona **tipagem estática opcional ao JavaScript**, o que pode ajudar a **detectar erros precocemente e melhorar a qualidade do código**.

* **Configuração**:
  *   Para adicionar TypeScript a um projeto React Native:

      ```bash
      npx react-native init MyApp --template react-native-template-typescript
      ```
  *   Se você tiver um projeto existente:

      ```bash
      npm install --save-dev typescript @types/react @types/react-native
      ```
*   **Exemplo**:

    ```javascript
    import React from 'react';
    import { Text, View } from 'react-native';

    interface Props {
      name: string;
    }

    const Greeting: React.FC<Props> = ({ name }) => (
      <View>
        <Text>Hello, {name}!</Text>
      </View>
    );

    export default Greeting;
    ```

### 17. Testes

Testar garante que seu aplicativo funcione como esperado e reduz bugs.

* **Jest**:
  * React Native vem com **Jest, um framework de testes JavaScript**.
  *   **Instalação**:

      ```bash
      npm install --save-dev jest @testing-library/react-native react-test-renderer
      ```
  *   **Exemplo de Teste**:

      ```javascript
      import React from 'react';
      import renderer from 'react-test-renderer';
      import App from '../App';

      test('renders correctly', () => {
        const tree = renderer.create(<App />).toJSON();
        expect(tree).toMatchSnapshot();
      });
      ```
* **Testing Library**:
  * Para **testar componentes com interações do usuário**.
  *   **Exemplo**:

      ```javascript
      import React from 'react';
      import { render, fireEvent } from '@testing-library/react-native';
      import MyButton from '../MyButton';

      test('Button presses correctly', () => {
        const onPressMock = jest.fn();
        const { getByText } = render(
          <MyButton onPress={onPressMock} title="Press me" />
        );
        fireEvent.press(getByText('Press me'));
        expect(onPressMock).toHaveBeenCalled();
      });
      ```

### 18. Acessibilidade

Tornar seu aplicativo acessível garante que ele possa ser usado pelo maior número possível de pessoas.

* **Props de Acessibilidade**:
  * **accessible**: Marca um componente como acessível.
  * **accessibilityLabel**: Fornece um rótulo legível para leitores de tela.
  * **accessibilityHint**: Fornece informações adicionais sobre um componente.
*   **Exemplo**:

    ```javascript
    <TouchableOpacity
      accessible={true}
      accessibilityLabel="Play Button"
      accessibilityHint="Plays the current track"
      onPress={handlePlay}
    >
      <Text>Play</Text>
    </TouchableOpacity>
    ```

### 19. Permissões

Para acessar certos recursos do dispositivo, você pode precisar **solicitar permissões**.

* **Usando `PermissionsAndroid` (Android)**:
  *   **Exemplo**:

      ```javascript
      import { PermissionsAndroid } from 'react-native';

      async function requestCameraPermission() {
        try {
          const granted = await PermissionsAndroid.request(
            PermissionsAndroid.PERMISSIONS.CAMERA,
            {
              title: 'Camera Permission',
              message: 'This app needs access to your camera',
              buttonNeutral: 'Ask Me Later',
              buttonNegative: 'Cancel',
              buttonPositive: 'OK',
            }
          );
          if (granted === PermissionsAndroid.RESULTS.GRANTED) {
            console.log('You can use the camera');
          } else {
            console.log('Camera permission denied');
          }
        } catch (err) {
          console.warn(err);
        }
      }
      ```
* **Usando `react-native-permissions` (Multiplataforma)**:
  *   **Instalação**:

      ```bash
      npm install react-native-permission
      ```
  *   **Exemplo**:

      ```javascript
      import { check, request, PERMISSIONS, RESULTS } from 'react-native-permissions';

      async function checkCameraPermission() {
        const result = await check(PERMISSIONS.ANDROID.CAMERA);
        switch (result) {
          case RESULTS.GRANTED:
            console.log('Camera permission granted');
            break;
          case RESULTS.DENIED:
            const requestResult = await request(PERMISSIONS.ANDROID.CAMERA);
            if (requestResult === RESULTS.GRANTED) {
              console.log('Camera permission granted');
            }
            break;
          // Handle other cases
        }
      }
      ```

### 20. APIs de Dispositivo

React Native fornece **acesso a várias APIs de dispositivo**.

*   **Geolocalização**:

    ```javascript
    import Geolocation from '@react-native-community/geolocation';
    Geolocation.getCurrentPosition(
      (position) => {
        console.log(position);
      },
      (error) => {
        console.log(error);
      },
      { enableHighAccuracy: true, timeout: 20000, maximumAge: 1000 }
    );
    ```
*   **Camera Roll**:

    ```javascript
    import { CameraRoll } from '@react-native-community/cameraroll';
    CameraRoll.getPhotos({
      first: 20,
      assetType: 'Photos',
    })
      .then((r) => {
        this.setState({ photos: r.edges });
      })
      .catch((err) => {
        console.log(err);
      });
    ```
*   **Clipboard**:

    ```javascript
    import { Clipboard } from 'react-native';
    Clipboard.setString('Hello World');
    Clipboard.getString().then((content) => {
      console.log(content);
    });
    ```

### 21. Armazenamento Offline

* **AsyncStorage**:
  * AsyncStorage é um **sistema de armazenamento de chave-valor simples, não criptografado, assíncrono e persistente**.
  *   **Instalação**:

      ```bash
      npm install @react-native-async-storage/async-storage
      ```
  *   **Exemplo**:

      ```javascript
      import AsyncStorage from '@react-native-async-storage/async-storage';

      const storeData = async (value) => {
        try {
          await AsyncStorage.setItem('@storage_Key', value);
        } catch (e) {
          // saving error
        }
      };

      const getData = async () => {
        try {
          const value = await AsyncStorage.getItem('@storage_Key');
          if (value !== null) {
            // value previously stored
          }
        } catch (e) {
          // error reading value
        }
      };
      ```

### 22. Otimização de Desempenho

Otimizar o desempenho garante que seu aplicativo funcione sem problemas.

*   **Usar `PureComponent` ou `React.memo`**: **Previne re-renderizações desnecessárias**.

    ```javascript
    import React from 'react';
    const MyComponent = React.memo(({ prop1, prop2 }) => {
      // Component code
    });
    ```
* **Evitar Funções Anônimas em `render`**: Passe funções definidas fora de `render` para componentes filhos.
*   **Usar `useCallback` e `useMemo`**: **Otimiza funções e computações caras**.

    ```javascript
    const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
    const memoizedCallback = useCallback(() => {
      doSomething(a, b);
    }, [a, b]);
    ```

### 23. Internacionalização (i18n)

Suporte a **vários idiomas** em seu aplicativo.

* **Usando `react-native-i18n`**:
  *   **Instalação**:

      ```bash
      npm install react-native-i18n
      ```
  *   **Exemplo**:

      ```javascript
      import I18n from 'react-native-i18n';
      I18n.fallbacks = true;
      I18n.translations = {
        en: { welcome: 'Welcome' },
        fr: { welcome: 'Bienvenue' },
      };
      <Text>{I18n.t('welcome')}</Text>
      ```
* **Usando `react-native-localize` e `i18n-js` (Abordagem moderna)**:
  *   **Instalação**:

      ```bash
      npm install react-native-localize i18n-js
      ```
  *   **Exemplo**:

      ```javascript
      import * as RNLocalize from 'react-native-localize';
      import i18n from 'i18n-js';

      const locales = RNLocalize.getLocales();
      if (Array.isArray(locales)) {
        i18n.locale = locales.languageTag;
      }
      i18n.fallbacks = true;
      i18n.translations = {
        en: { welcome: 'Welcome' },
        fr: { welcome: 'Bienvenue' },
      };
      <Text>{i18n.t('welcome')}</Text>
      ```

### 24. Tratamento de Erros

Lidar com erros de forma graciosa melhora a experiência do usuário.

*   **Limites de Erro (Error Boundaries)**:

    * **Captura erros de JavaScript em componentes**.

    ```javascript
    import React from 'react';
    import { View, Text } from 'react-native';

    class ErrorBoundary extends React.Component {
      state = { hasError: false };

      componentDidCatch(error, info) {
        // Log error
        this.setState({ hasError: true });
      }

      render() {
        if (this.state.hasError) {
          return <Text>Something went wrong.</Text>;
        }
        return this.props.children;
      }
    }

    <ErrorBoundary>
      <MyComponent />
    </ErrorBoundary>;
    ```
*   **Blocos Try-Catch**: Use blocos `try-catch` em **funções assíncronas**.

    ```javascript
    try {
      const response = await fetchData();
    } catch (error) {
      console.error(error);
    }
    ```

### 25. Melhores Práticas

Seguir as melhores práticas ajuda a manter a qualidade do código.

*   **Estrutura de Diretórios**: Organize seus arquivos logicamente.

    ```
    - src/
      - components/
      - screens/
      - navigation/
      - services/
      - assets/
    ```
*   **Linting e Formatação**: Use **ESLint e Prettier**.

    ```bash
    npm install --save-dev eslint prettier eslint-config-prettier eslint-plugin-prettier
    ```
* **Escrever Componentes Reutilizáveis**: Crie componentes que possam ser reutilizados em todo o seu aplicativo.
* **Comentar e Documentar Seu Código**: Use comentários e documentação para explicar lógicas complexas.
*   **Usar PropTypes ou TypeScript**: Garanta que as props do componente sejam usadas corretamente.

    ```javascript
    import PropTypes from 'prop-types';
    MyComponent.propTypes = {
      name: PropTypes.string.isRequired,
    };
    ```

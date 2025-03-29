

1. Fundamentos do React
- [ ] [[1.1 JSX, JavaScript XML]] É uma extensão de sintaxe do JavaScript usada para criar componentes React. Entenda como misturar HTML e JavaScript.
- [ ] [[1.2 Componentes e Props]] Aprenda a criar componentes reutilizáveis e a passar dados para eles usando props.
- [ ] [[1.3 Estado e Ciclo de Vida]] Explore como gerenciar estados locais nos componentes e os métodos do ciclo de vida, como componentDidMount e componentWillUnmount.
- [ ]  [[1.4 Eventos no React]] Manipule eventos como cliques e envios de formulários de maneira declarativa.
- [ ] [[1.5 Hooks]] Com foco em useState (para gerenciar estados) e useEffect (para efeitos colaterais como chamadas de API).

2. Introdução ao Redux
- [ ] [[2.1 O que e Redux]] É uma biblioteca para gerenciamento de estado previsível. Saiba quando e por que usá-la.
- [ ] [[2.2 State Management]] Entenda os problemas que surgem ao gerenciar estados em aplicativos grandes.
- [ ] [[2.3 Principios]] Conheça os três pilares do Redux:
- [ ] [[2.4 Single Source of Truth]] O estado da aplicação é mantido em uma única Store.
- [ ] [[2.5 State is Read-Only]] O estado é somente leitura.
- [ ] [[2.6 Changes are Made with Pure Reducers]] Mudanças são feitas por Reducers puros.

3. Configurando o Redux
- [ ] [[3.1 Instalacao]] Use npm install redux react-redux para configurar.
- [ ] [[3.2 Criando a Store]] Inicialize o estado principal com o método createStore.
- [ ] [[3.3 Actions e Reducers]] Defina ações para descrever mudanças e reducers para implementá-las.
- [ ] [[3.4 Provider]] Envolva a aplicação com `<Provider>` para fornecer acesso ao estado Redux.

4. Uso do Estado no Redux
- [ ] [[4.1 useSelector]] Para extrair partes específicas do estado global.
- [ ] [[4.2 useDispatch]] Para enviar ações e atualizar o estado.
- [ ] [[4.3 Estrutura de Projeto]] Organize as pastas: actions/, reducers/ e components/ para manter o código limpo.

5. Middleware no Redux
- [ ] [[5.1 O que e Middleware]] Ferramentas intermediárias que permitem manipular ações antes de elas atingirem os reducers.
- [ ] [[5.2 Redux Thunk]] Permite lidar com chamadas assíncronas (como APIs).
- [ ] [[5.3 Redux Saga]] Um middleware avançado para lidar com fluxos de trabalho complexos.

6. Ferramentas de Debugging
- [ ] [[6.1 Redux DevTools]] Uma extensão de navegador poderosa para inspecionar mudanças de estado, ações despachadas e mais.
- [ ] [[6.2 Configuracao DevTools]] Inclua o DevTools durante a criação da Store no Redux.

7. Padrões Avançados
- [ ] [[7.1 Normalizacao]] Estruture o estado para evitar duplicações.
- [ ] [[7.2 CombineReducers]] Divida reducers grandes em partes menores para organizar o código.
- [ ] [[7.3 Memoization]] Use o reselect para otimizar seleções de estado e evitar renders desnecessários.

8. Testes
- [ ] [[8.1 Testes Unitarios]] Crie testes para verificar o comportamento de actions e reducers.
- [ ] [[8.2 Testes de Integracao]] Valide se componentes conectados ao Redux funcionam como esperado.







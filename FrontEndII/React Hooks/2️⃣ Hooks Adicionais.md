##  <span style="color:rgb(255,255,0)">1.1 Uso do hook useContext para acessar o contexto</span>

O hook useContext no React é usado para acessar o contexto disponibilizado pelo Context API, que é uma forma eficiente de compartilhar dados entre componentes sem a necessidade de passar "props" manualmente por cada nível da árvore de componentes.

Criação do Contexto: Primeiro, você cria um contexto com React.createContext(). Esse contexto atuará como um "armazém" para os dados que você quer compartilhar.

```
import React, { createContext } from "react";

const MeuContexto = createContext();
```

Provedor do Contexto (Provider): O contexto tem um componente especial chamado Provider, que envolve os componentes onde os dados estarão acessíveis. Ele também permite definir o valor que será compartilhado.

```
function App() {
    return (
        <MeuContexto.Provider value={{ nome: "Diego" }}>
            <MeuComponente />
        </MeuContexto.Provider>
    );
}
```

Uso do useContext: Nos componentes que precisam acessar o valor do contexto, você utiliza o hook useContext, passando o contexto criado como argumento.

```
import React, { useContext } from "react";

function MeuComponente() {
    const contexto = useContext(MeuContexto);

    return <h1>Olá, {contexto.nome}!</h1>;
}
```

Vantagens
Evita "prop drilling" (passar propriedades de forma desnecessária por vários níveis).
Simples e direto para acessar informações globais dentro da aplicação.


## 1.2 Introdução ao hook useReducer para gerenciamento de estado complexo

O hook useReducer no React é uma ótima alternativa ao uso do useState quando você precisa gerenciar estados mais complexos ou interdependentes. Ele funciona de forma semelhante a um "mini Redux" integrado, fornecendo uma maneira estruturada de atualizar o estado com base em ações.

Como funciona o useReducer?

- Estado inicial: Você define o estado inicial, que pode ser um valor simples ou um objeto complexo.
- Reducer: É uma função pura que recebe dois argumentos: o estado atual e uma ação. Ela retorna o novo estado com base na lógica definida.
- Dispatch: É a função que você usa para disparar uma ação e "informar" ao reducer que uma atualização de estado precisa ocorrer.
- useReducer: Este hook combina o estado inicial, o reducer e retorna o estado atualizado junto com a função dispatch.

Aqui está um exemplo básico:

```
import React, { useReducer } from "react";

// 1. Define o estado inicial
const estadoInicial = { contador: 0 };

// 2. Cria a função reducer
function reducer(estado, acao) {
    switch (acao.tipo) {
        case "incrementar":
            return { contador: estado.contador + 1 };
        case "decrementar":
            return { contador: estado.contador - 1 };
        case "resetar":
            return { contador: 0 };
        default:
            throw new Error("Ação não reconhecida!");
    }
}

export default function Contador() {
    // 3. Usa o useReducer
    const [estado, dispatch] = useReducer(reducer, estadoInicial);

    return (
        <div>
            <h1>Contador: {estado.contador}</h1>
            {/* 4. Dispara ações */}
            <button onClick={() => dispatch({ tipo: "incrementar" })}>
                Incrementar
            </button>
            <button onClick={() => dispatch({ tipo: "decrementar" })}>
                Decrementar
            </button>
            <button onClick={() => dispatch({ tipo: "resetar" })}>
                Resetar
            </button>
        </div>
    );
}
```

Vantagens do useReducer

- Ideal para lógica de estado mais complexa, onde várias partes do estado dependem umas das outras.
- Garante que o estado seja atualizado de forma previsível, já que o reducer é uma função pura (sem efeitos colaterais).
- Ajuda a organizar o código e separar a lógica de atualização do estado da interface do usuário.


## 1.3 Uso do hook useCallback para memorização de funções

O hook useCallback no React é usado para memorizar funções e evitar que elas sejam recriadas em cada renderização do componente. Ele é particularmente útil em situações onde a recriação desnecessária de uma função pode causar problemas de desempenho ou renderizações desnecessárias de componentes filhos.

Como funciona o useCallback?

- O useCallback aceita dois argumentos:
- A função a ser memorizada.
- Um array de dependências que determina quando a função deve ser recriada.
- Ele retorna a versão "memorizada" da função, garantindo que ela seja a mesma entre renderizações, a menos que uma das dependências mude.

Aqui está um exemplo simples para ilustrar seu uso:

```
import React, { useState, useCallback } from "react";
import List from "./List";

export default function App() {
    const [contador, setContador] = useState(0);
    const [valor, setValor] = useState("");

    // Função memorizada com useCallback
    const adicionarNaLista = useCallback((item) => {
        console.log(`Adicionando ${item}`);
    }, []); // Sem dependências, então nunca será recriada

    return (
        <div>
            <h1>Contador: {contador}</h1>
            <button onClick={() => setContador(contador + 1)}>Incrementar</button>
            
            <input
                value={valor}
                onChange={(e) => setValor(e.target.value)}
                placeholder="Digite algo"
            />
            <List adicionarNaLista={adicionarNaLista} />
        </div>
    );
}

// Componente List
function List({ adicionarNaLista }) {
    const itens = ["Item 1", "Item 2", "Item 3"];

    return (
        <ul>
            {itens.map((item) => (
                <li key={item} onClick={() => adicionarNaLista(item)}>
                    {item}
                </li>
            ))}
        </ul>
    );
}
```

Por que usar o useCallback?
- Evitar renderizações desnecessárias:
- Componentes filhos que recebem funções como props podem ser otimizados com React.memo, que verifica se as props mudaram. O useCallback impede que novas instâncias da função sejam criadas, ajudando na comparação de props.
- Melhorar desempenho:
- Em componentes com estados complexos ou muitos re-renderizadores, o useCallback reduz o trabalho ao evitar a criação contínua de funções.

Nota Importante:
- Nem sempre necessário: Use o useCallback apenas quando a função estiver sendo passada para componentes filhos otimizados com React.memo ou quando houver impacto real no desempenho.
- Dependências corretas: Certifique-se de incluir todas as dependências que a função utiliza no array de dependências, para evitar comportamentos inesperados.



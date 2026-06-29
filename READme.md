# AtividadeGrafosLinkedIn — LinkedIn Analyzer

Projeto prático da disciplina de Grafos: motor de recomendações para uma rede de conexões profissionais.

A rede é modelada como um **grafo não-direcionado e ponderado**:
- **Vértices** = perfis dos usuários
- **Arestas** = conexões de amizade ou trabalho (bidirecionais)
- **Pesos** = afinidade entre as pessoas (1 = muita proximidade, 5+ = pouca)

## Integrantes

| Nome | RGM |
|---|---|
| Daniel | _preencher_ |
| Carlos | _preencher_ |
| Roberio | _preencher_ |
| Jezreel de Andrade | _preencher_ |

**Vídeo da apresentação:** _colocar link do YouTube aqui_

## Estrutura do projeto

```
AtividadeGrafosLinkedIn/
├── trabalhografos/
│   └── src/
│       ├── modelo/          ← código do professor (grafo)
│       │   ├── Vertice.java
│       │   ├── Aresta.java
│       │   ├── Grafo.java
│       │   └── ResultadoRota.java
│       ├── analyzer/        ← lógica da atividade
│       │   ├── LinkedInAnalyzer.java
│       │   ├── SugestaoConexao.java
│       │   └── ResultadoCaminho.java
│       └── app/
│           ├── Main.java
│           └── RedeFactory.java
├── run.sh
├── run.bat
├── READme.md
└── .gitignore
```

## Como executar

Requer **JDK 16+** (não funciona com Java 8). O código do professor usa text blocks e `Stream.toList()`.

Na **raiz do repositório** (`AtividadeGrafosLinkedIn/`):

**Git Bash / Linux / macOS:**

```bash
chmod +x run.sh
./run.sh
```

**Windows (CMD ou duplo clique):**

```bat
run.bat
```

**Manualmente (Git Bash):**

```bash
mkdir -p out
javac -encoding UTF-8 -d out $(find trabalhografos/src -name "*.java")
java -cp out app.Main
```

## Modo interativo

1. **Entrar como usuário** — escolhe um dos perfis
2. **Ver amigos** — conexões diretas com peso de afinidade
3. **Ver sugestões** — amigos de amigos, ordenados por amigos em comum
4. **Grau de separação** — BFS: menor número de passos
5. **Rota de maior afinidade** — Dijkstra: menor custo (maior proximidade)

## Exemplo da demo (login como Ana)

| Consulta | Resultado |
|---|---|
| Conexões diretas | Bruno (afinidade: 1), Carlos (2), Daniela (8) |
| Top sugestão | Eduardo — 2 amigos em comum |
| BFS → Fernanda | 2 passos: Ana → Daniela → Fernanda |
| Dijkstra → Fernanda | custo 3: Ana → Bruno → Eduardo → Fernanda |

## Divisão do desenvolvimento

| Integrante | Responsabilidade |
|---|---|
| Carlos | Modelo de dados (`Vertice`, `Aresta`, `RedeFactory`, DTOs) |
| Roberio | `LinkedInAnalyzer` — sugestões e BFS |
| Jezreel | `Main`, scripts de execução e integração |
| Daniel | Apresentação e demonstração |

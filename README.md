# IsKahoot - Jogo Concorrente e Distribuído 🎮

Projeto desenvolvido para a unidade curricular de **Programação Concorrente e Distribuída (PCD)**.  
O **IsKahoot** é uma versão adaptada e distribuída do popular jogo *Kahoot!*, focada na aplicação de conceitos avançados de concorrência e coordenação de threads em Java.

---

## 📌 Características do Projeto

- **Arquitetura Cliente-Servidor:** Comunicação via Sockets Java e troca de objetos serializados.
- **Modos de Jogo:**
    - **Perguntas Individuais:** Avaliadas com atribuição de pontos bónus para as primeiras respostas recebidas (utilizando uma versão personalizada de `CountDownLatch`).
    - **Perguntas de Equipa:** Avaliadas apenas após a receção das respostas de todos os membros da equipa ou quando o tempo expira (utilizando uma `Barreira` com variáveis condicionais).
- **Interface Gráfica (GUI):** Interface Java Swing/AWT para os jogadores visualizarem as perguntas, opções, cronómetros e placares de desempenho.
- **Interface de Texto (TUI) no Servidor:** Gestão de jogos e criação dinâmica de sessões.
- **Ficheiro de Perguntas:** Leitura e processamento de ficheiros JSON com suporte à biblioteca **Gson**.

---

## 📁 Estrutura do Repositório

````text
Kahoot/
├── src/
│   └── kahoot/
│       ├── cliente/       # Interface gráfica e lógica do jogador
│       ├── mensagens/     # Classes de mensagens para comunicação Sockets
│       └── servidor/      # Servidor, gestão de estado (GameState) e coordenação
├── perguntas.json         # Base de dados de perguntas em formato JSON
├── .gitignore             # Ficheiros ignorados pelo Git
└── README.md              # Documentação do projeto
````
---

## 🚀 Como Executar

### 1. Pré-requisitos
- **Java JDK 17** ou superior instalado.
- Biblioteca **Gson** (necessária para a leitura do ficheiro `perguntas.json`).

### 2. Iniciar o Servidor
O servidor é iniciado sem argumentos e abre a interface de linha de comandos (TUI):
````bash
java -cp bin:gson.jar kahoot.servidor.Servidor
````
Na TUI do servidor, pode criar um novo jogo especificando os parâmetros:
````bash
new <num_equipas> <num_jogadores_por_equipa> <num_perguntas>
````
### 3. Iniciar um Cliente (Jogador)
Cada cliente liga-se ao servidor passando como argumentos o endereço IP, porto, código do jogo, código da equipa e nome do utilizador:
````bash
java -cp bin kahoot.cliente.Cliente


# 📄 Documentação do Sistema de Gestão de Campeonato Esportivo

## 📌 Visão Geral

Este sistema permite gerenciar **jogadores**, **times** e **campeonatos esportivos**. As funcionalidades incluem:
- Cadastro de jogadores
- Criação de campeonatos
- Adição de times aos campeonatos
- Associação de jogadores a times
- Agendamento e realização de confrontos
- Listagem de dados
- Remoção de jogadores de times

---

## 📦 Estrutura de Classes

### 1. `class Jogador`

Representa um jogador com atributos imutáveis: **nome**, **idade** e **posição**.

#### Atributos:
- `self.info`: tupla com (nome, idade, posição)

#### Propriedades:
- `nome`: retorna `self.info[0]`
- `idade`: retorna `self.info[1]`
- `posicao`: retorna `self.info[2]`

#### Métodos:
- `__str__`: retorna uma representação amigável do jogador

---

### 2. `class Time`

Representa um time contendo jogadores.

#### Atributos:
- `nome`: nome do time
- `jogadores`: lista de objetos `Jogador`

#### Métodos:
- `adicionar_jogador(jogador)`: adiciona jogador ao time
- `remover_jogador_por_nome(nome_jogador)`: remove jogador pelo nome
- `remover_jogador()`: remove o último jogador da lista (estilo pilha)
- `listar_jogadores()`: retorna lista de strings representando os jogadores

---

### 3. `class Campeonato`

Representa um campeonato com seus times e confrontos agendados.

#### Atributos:
- `nome`: nome do campeonato
- `times`: dicionário `{nome_time: objeto_time}`
- `fila_confrontos`: fila de confrontos usando `collections.deque`

#### Métodos:
- `adicionar_time(time)`: adiciona um time ao campeonato
- `listar_times()`: retorna nomes dos times cadastrados
- `agendar_confronto(nome_time1, nome_time2)`: insere confronto na fila
- `realizar_proximo_confronto()`: remove e mostra o próximo confronto da fila

---

### 4. `class SistemaCampeonato`

Classe principal que gerencia toda a interação do usuário com o sistema.

#### Atributos:
- `jogadores_cadastrados`: dicionário `{nome: objeto_jogador}`
- `campeonatos`: dicionário `{nome_campeonato: objeto_campeonato}`

#### Métodos:
- `cadastrar_jogador()`: solicita dados do usuário e cadastra um novo jogador
- `criar_campeonato()`: cria um novo campeonato
- `adicionar_time_campeonato()`: cria e adiciona um time a um campeonato existente, incluindo a escolha de jogadores
- `listar_jogadores_time()`: exibe os jogadores de um time em um campeonato
- `agendar_confronto()`: agenda confronto entre dois times
- `realizar_confronto()`: realiza (remove e mostra) o próximo confronto
- `listar_campeonatos()`: mostra todos os campeonatos criados
- `remover_jogador_time()`: remove um jogador específico de um time
- `menu()`: exibe o menu principal e permite navegar pelo sistema via console

---

## 🎮 Lógica de Execução

O sistema roda a partir do `if __name__ == "__main__"` e executa `sistema.menu()`, que oferece um menu interativo com as seguintes opções:

```
1. Cadastrar jogador
2. Criar campeonato
3. Adicionar time ao campeonato
4. Listar jogadores de um time
5. Agendar confronto
6. Realizar próximo confronto
7. Listar campeonatos
8. Remover jogador de um time
0. Sair
```

---

## 🛠️ Estruturas de Dados Usadas

- **Tupla** (`Jogador.info`) — usada para garantir imutabilidade dos dados do jogador.
- **Lista** (`Time.jogadores`) — usada para armazenar e manipular os jogadores em um time.
- **Dicionário** (`Campeonato.times`, `SistemaCampeonato.jogadores_cadastrados`, `SistemaCampeonato.campeonatos`) — usado para acessos rápidos via chave.
- **Deque** (`Campeonato.fila_confrontos`) — fila eficiente para os confrontos, respeitando ordem FIFO.

---

## 💡 Sugestões de Melhoria

1. **Salvar/Carregar dados em arquivos** (JSON ou pickle) para manter os cadastros entre execuções.
2. **Adicionar placar aos confrontos** e armazenamento de resultados.
3. **Interface gráfica (GUI)** ou versão web.
4. **Validação de dados mais robusta** (por exemplo, evitar idades negativas).
5. **Separar entrada de dados da lógica de negócios** para facilitar testes automatizados.

caue rocha RA:1988978
pedro guedes RA:2014778

📝 Documentação do Sistema de Gestão de Campeonato Esportivo
💡 Visão Geral
Esse projeto implementa um sistema de campeonatos esportivos onde é possível cadastrar jogadores, montar times, adicionar esses times a campeonatos, agendar confrontos e realizar partidas simuladas.
Ele usa conceitos básicos de programação orientada a objetos em Python, como classes, métodos e encapsulamento, e também estruturas de dados como listas, dicionários, tuplas e fila (deque).

🧱 Estrutura de Classes
🔹 Classe Jogador
Representa um jogador de futebol (ou outro esporte).
Os dados de nome, idade e posição são guardados em uma tupla, pois são considerados imutáveis após o cadastro.

__init__(nome, idade, posicao): Cria o jogador e guarda suas informações.

@property nome / idade / posicao: Propriedades para acessar os dados individuais.

__str__(): Retorna a representação do jogador como string, por ex: João, 22 anos, atacante.

🔹 Classe Time
Um time pode ter vários jogadores.

__init__(nome): Inicializa o time com um nome e uma lista de jogadores vazia.

adicionar_jogador(jogador): Adiciona um jogador ao time.

remover_jogador_por_nome(nome): Remove um jogador pelo nome.

remover_jogador(): Remove o último jogador da lista (comportamento de pilha/LIFO).

listar_jogadores(): Retorna uma lista dos jogadores no time (em forma de string).

🔹 Classe Campeonato
Representa um campeonato com vários times e confrontos agendados.

__init__(nome): Cria um campeonato com nome, dicionário de times e uma fila de confrontos.

adicionar_time(time): Adiciona um time ao campeonato.

listar_times(): Retorna os nomes dos times cadastrados.

agendar_confronto(time1, time2): Adiciona um confronto entre dois times na fila.

realizar_proximo_confronto(): Retira o próximo confronto da fila e o realiza (simbolicamente, só mostra na tela).

🔹 Classe SistemaCampeonato
Essa é a classe que faz a interface com o usuário. Ela conecta jogadores, times e campeonatos, simulando um sistema de menu.

Atributos:
jogadores_cadastrados: Dicionário para armazenar os jogadores únicos por nome.

campeonatos: Dicionário para armazenar os campeonatos criados.

Métodos principais:
cadastrar_jogador(): Pergunta dados via input e cria um jogador, evitando duplicatas.

criar_campeonato(): Cria um campeonato com nome fornecido pelo usuário.

adicionar_time_campeonato(): Cria um time, adiciona jogadores existentes a ele, e insere no campeonato.

listar_jogadores_time(): Mostra os jogadores de um time específico.

agendar_confronto(): Agenda uma partida entre dois times já cadastrados no campeonato.

realizar_confronto(): Retira o próximo confronto da fila e mostra que ele foi realizado.

listar_campeonatos(): Mostra todos os campeonatos criados até agora.

remover_jogador_time(): Remove um jogador específico de um time dentro de um campeonato.

menu(): Menu de opções para o usuário interagir com o sistema.

📦 Execução
Quando o script é executado diretamente (if __name__ == "__main__":), ele inicializa o sistema e exibe um menu interativo em loop, onde o usuário pode:

Cadastrar jogadores

Criar campeonatos

Adicionar times com jogadores

Ver os jogadores de um time

Agendar confrontos

Realizar confrontos

Listar campeonatos

Remover jogadores dos times

Sair do sistema

📌 Extras e Detalhes Técnicos
Imutabilidade dos dados do jogador: foi usada uma tupla para evitar alterações acidentais nas informações de um jogador após ser criado.

Fila com collections.deque: usada para garantir que os confrontos sejam realizados na ordem em que foram agendados (FIFO).

Tratamento de erros: simples e direto, principalmente na conversão de idade e verificação de existência de jogadores/times.

💭 Sugestões Futuras
Permitir salvar os dados em arquivos (usando JSON ou pickle).

Adicionar pontuação e registrar resultados dos confrontos.

Criar uma interface gráfica simples (com Tkinter, por exemplo).

Adicionar autenticação para administradores e controle de acesso.

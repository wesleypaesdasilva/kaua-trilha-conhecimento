Aqui está o documento formatado em Markdown:

---

# 🎯 Missão DevOps 02: Investigação de Redes e Processos no Linux

Parabéns por ter matado a primeira missão no peito e colocado o Nginx para rodar! Você já sabe como subir um serviço básico. Mas no dia a dia de DevOps e SRE, as coisas quebram. Portas ficam ocupadas, processos travam e gargalos de rede acontecem.

Sua segunda missão é focar em **observabilidade e troubleshooting**. Você vai aprender a rastrear o que está rodando na sua máquina e como o Linux gerencia a comunicação de rede.

---

## 🏢 O Cenário

O time de segurança da empresa desconfia que existem processos desnecessários rodando no servidor e quer um relatório de como o Nginx está se comunicando. Além disso, precisamos simular um problema clássico do dia a dia: **descobrir quem está ocupando uma porta quando um serviço se recusa a subir.**

---

## 🚀 Fase 1: Investigando a Árvore de Processos

> Tudo o que roda no Linux é um processo. Vamos aprender a rastreá-los.

1. **Listagem Geral** — Use o comando `ps` com as flags necessárias para listar todos os processos que estão rodando na máquina neste exato momento.

2. **Caçando o Nginx** — Filtre a listagem anterior (usando o bom e velho `| grep`) para encontrar apenas os processos do Nginx.

3. **Quem é o Dono?** — Repare na saída do comando. Você vai notar que existe um processo **master** (geralmente rodando como `root`) e processos **worker** (rodando com um usuário limitado, como `www-data` ou `nginx`). Descubra o **PID** (Process ID) do processo master do Nginx.

4. **Consumo de Recursos** — Use uma ferramenta interativa no terminal (como `top` ou `htop`) para monitorar o consumo de **CPU** e **Memória** desse processo em tempo real.

---

## 🌐 Fase 2: Mapeamento de Redes e Portas

> Agora que sabemos quem está rodando, precisamos ver como ele conversa com o mundo.

1. **Quem está ouvindo?** — Use uma ferramenta de estatísticas de rede (como `ss` ou `netstat`) com as flags certas para listar todas as portas TCP que estão em modo de escuta (`LISTEN`) no seu sistema.

2. **Conectando os Pontos** — Descubra o comando exato que mostra não apenas a porta (no caso, a `80`), mas também o **nome do processo** e o **PID** que está amarrado a ela.

3. **Auditoria de Conexão** — Do seu celular ou de outra máquina, acesse o site novamente. Enquanto a página carrega ou atualiza, rode o comando de rede no Linux para tentar ver a conexão estabelecida (`ESTABLISHED`) entre o IP do seu celular e a porta `80` do servidor.

---

## 💥 Fase 3: Simulação de Incidente (A Porta Ocupada)

> Dois corpos não ocupam o mesmo lugar no espaço, e dois serviços não ocupam a mesma porta no Linux.

1. **O Clone** — Tente instalar ou subir um segundo servidor web (como o Apache) ou configure um script simples para tentar escutar na mesma porta `80`. Veja o erro acontecer no log do sistema.

2. **Forçando a Queda** — Em vez de usar o delicado `systemctl stop`, imagine que o Nginx travou totalmente e não responde. Use o comando `kill` (ou `killall`) enviando o sinal correto (`SIGKILL` ou `-9`) diretamente para o **PID master** do Nginx que você descobriu na Fase 1.

3. **A Confirmação** — Rode o comando de portas novamente e confirme que a porta `80` foi finalmente liberada após a "morte" do processo.

---

## 🛡️ Fase 4: Automação com Sinais e Logs

> DevOps precisa saber onde olhar quando o sistema reclama.

1. **Rastro de Sangue (Logs)** — Onde o Linux guarda os logs de erro do sistema? Descubra o caminho do arquivo principal de logs (geralmente `/var/log/syslog` ou através do `journalctl`) e use o comando `tail -f` para monitorar as mensagens em tempo real enquanto você inicia e para o Nginx.

2. **Recarga Suave (Reload)** — Imagine que você alterou o HTML ou a configuração do Nginx, mas **não quer derrubar o site** para os usuários atuais. Descubra qual sinal do `kill` (ou flag do `nginx`) permite recarregar as configurações sem matar o processo principal.

---

## 📝 O que eu espero que você me entregue

Mande no meu privado:

- **O comando exato** (com as flags) que você usou para descobrir qual PID estava usando a porta `80`.
- **Uma breve explicação** de qual é a diferença entre matar um processo com um sinal padrão e usar o `-9` (`SIGKILL`).
- **O comando** que você usou para acompanhar os logs do sistema em tempo real.

---

> Essa base de processos e redes vai te salvar muito no futuro quando estivermos mexendo com containers e clusters. **Mão na massa!**

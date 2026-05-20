# 🎯 Missão DevOps: Operação Servidor Web Vivo

Bem-vindo ao mundo Linux e DevOps! Para começar com o pé direito, você não vai apenas decorar comandos isolados. Você vai resolver um **problema real**, do tipo que enfrentamos todos os dias no mercado: preparar um servidor, colocar uma aplicação no ar e garantir que ela continue funcionando, aconteça o que acontecer.

Siga os passos abaixo, pesquise os comandos necessários e documente o seu progresso. Boa sorte!

---

## 🏢 O Cenário

Uma empresa fictícia precisa colocar uma **página de avisos institucional** no ar urgentemente em um servidor Linux local. Sua missão como profissional de infraestrutura/DevOps é:

- Preparar o sistema
- Instalar o servidor web
- Customizar a página com o conteúdo do time de design
- Garantir que o serviço seja **resiliente a falhas e reinicializações**

---

## 🚀 Fase 1: Reconhecimento e Preparação do Terreno

> Antes de construir, precisamos saber onde estamos pisando e garantir que as ferramentas estejam atualizadas.

### 1.1 Atualize o Sistema

Abra o seu terminal e execute a atualização da lista de pacotes e dos programas do seu Linux para garantir que tudo esteja na versão mais recente e segura.

### 1.2 Crie seu Espaço de Trabalho

Na sua pasta de usuário (Home), crie um diretório chamado `workspace`. Dentro dele, crie uma pasta chamada `projeto-web`.

### 1.3 Descubra sua Identidade na Rede

Use o terminal para descobrir o **endereço IP local** (IP privado) da sua máquina Linux. Anote esse IP — você vai precisar dele logo mais.

---

## 🌐 Fase 2: Instalação e Configuração do Servidor

> Hora de transformar sua máquina comum em um servidor de verdade.

### 2.1 Instale o Nginx

Descubra qual é o gerenciador de pacotes da sua distribuição Linux e instale o servidor web **Nginx**.

### 2.2 Valide o Status

Verifique via terminal se o serviço do Nginx foi iniciado corretamente e está **ativo (running)**.

### 2.3 Primeiro Teste de Acesso

Abra o navegador no seu celular ou em outro computador conectado na **mesma rede Wi-Fi** que o seu Linux. Digite o endereço IP do seu Linux na barra de navegação.

✅ Se tudo estiver certo, você verá a **página padrão de boas-vindas do Nginx**.

---

## ✍️ Fase 3: A Entrada do "Dev" (Manipulação e Permissões)

> O servidor padrão está funcionando, mas a empresa precisa exibir o conteúdo dela, não o do Nginx.

### 3.1 Crie a Página

Entre na pasta `workspace/projeto-web` que você criou na Fase 1. Use um editor de texto de terminal (como `nano` ou `vim`) e crie um arquivo chamado `index.html`.

### 3.2 Escreva o Conteúdo

Dentro desse arquivo, coloque uma estrutura HTML simples com o conteúdo institucional desejado.

### 3.3 O Desafio das Permissões

O Nginx lê os arquivos que ficam no diretório padrão do sistema, geralmente em `/var/www/html/`. Você precisa **mover ou copiar** o seu `index.html` para lá.

> ⚠️ **Atenção:** Você provavelmente vai receber um erro de **"Permissão Negada"**. Descubra por que isso acontece e como usar privilégios de superusuário (`sudo`) ou alterar o dono/permissões do diretório para resolver isso.

### 3.4 Valide a Alteração

Atualize a página no navegador do seu celular/outro dispositivo.

✅ Se o seu texto aparecer, você concluiu esta etapa com sucesso!

---

## 🛡️ Fase 4: O Toque DevOps/SRE (Automação e Resiliência)

> Um bom profissional de DevOps não deixa as coisas funcionando "por sorte". Precisamos garantir que o sistema sobreviva a problemas.

### 4.1 Sobrevivendo ao Reboot

Se o computador for reiniciado ou faltar energia, o servidor web precisa **voltar sozinho** sem intervenção humana. Configure o serviço do Nginx para iniciar automaticamente junto com a inicialização do sistema.

### 4.2 Simulação de Incidente

1. Vá ao terminal e **force a parada** do serviço do Nginx.
2. Tente acessar a página pelo navegador e confirme que ela caiu (**Erro de conexão**).
3. **Inicie o serviço novamente** e valide que o site voltou a funcionar.

---

## 📝 Entregáveis

Quando terminar, mande uma mensagem com:

| # | Entregável |
|---|-----------|
| 1 | O **comando** que você usou para descobrir o IP da sua máquina |
| 2 | Como você resolveu o problema de **"Permissão Negada"** na Fase 3 |
| 3 | Uma **foto ou print** da tela do seu celular acessando a sua página customizada através do IP do Linux |
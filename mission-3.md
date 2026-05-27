# 🎯 Missão DevOps 03: Arquitetura, Cálculo e Desenho de Redes

Você já dominou como um servidor web roda localmente e como investigar processos e portas no Linux. Agora, imagine que sua infraestrutura precisa crescer. Você não terá apenas uma máquina, mas sim dezenas delas que precisam conversar de forma organizada e segura.

Sua terceira missão é puramente de **Planejamento e Arquitetura de Redes**. Você vai calcular o endereçamento de uma empresa e desenhar a topologia dessa rede antes de qualquer implementação.

---

## 🏢 O Cenário

Uma startup está migrando a infraestrutura dela para um ambiente corporativo. Eles receberam o bloco de IP principal `192.168.0.0/22` e precisam que você divida essa rede (**Subnetting**) para atender a três departamentos distintos:

| Departamento | IPs necessários |
|---|---|
| Diretoria / Administrativo | Pelo menos 50 IPs utilizáveis |
| Desenvolvimento (Devs) | Pelo menos 200 IPs utilizáveis |
| Produção (Servidores / Banco de Dados) | Pelo menos 500 IPs utilizáveis |

Sua missão é fazer o **cálculo exato** dessas sub-redes para evitar desperdício de IPs e desenhar o fluxo de comunicação entre elas.

---

## 🚀 Fase 1: Desvendando o CIDR (Cálculo de Máscaras)

> Para não faltar IP e nem desperdiçar o bloco da empresa, você precisa calcular o tamanho de cada sub-rede usando a lógica de blocos CIDR.

**1. Entendendo o Bloco Pai**

O bloco principal é `192.168.0.0/22`. Responda:

- Quantos IPs totais existem dentro de uma máscara `/22`?
- Qual é a máscara de rede correspondente em formato decimal (ex: `255.255.X.X`)?

**2. Divisão das Sub-redes (Subnetting)**

Baseado na necessidade de cada departamento, defina a máscara ideal (`/X`) para cada um de modo que cubra a quantidade de IPs necessários com a **menor sobra possível**:

- Qual bloco CIDR usar para a **Produção** (500 IPs)?
- Qual bloco CIDR usar para o **Desenvolvimento** (200 IPs)?
- Qual bloco CIDR usar para a **Diretoria** (50 IPs)?

**3. Mapeamento de IP Útil**

Para cada uma das 3 sub-redes calculadas, identifique:

- O **IP de Rede** (Network IP)
- O **Primeiro IP utilizável** e o **Último IP utilizável** (para colocar nas máquinas)
- O **IP de Broadcast**

---

## 🗺️ Fase 2: O Desenho da Topologia (Arquitetura)

> Um bom DevOps precisa saber documentar e visualizar a rede de forma clara.

**1. Escolha sua Ferramenta**

Use uma ferramenta de desenho técnico ou diagramação livre, como **Draw.io**, **Excalidraw** ou **Lucidchart**.

**2. Monte o Diagrama**

O seu desenho precisa conter visualmente:

- O **Roteador Principal (Gateway)** que recebe a internet
- Um **Firewall** ou switch central gerenciando o tráfego
- Três **zonas isoladas** representando cada sub-rede calculada na Fase 1
- Dentro de cada sub-rede, pelo menos **um elemento de exemplo** — ex: um notebook na Diretoria, um PC na área de Devs, e um Servidor + Banco de Dados na Produção — com o **bloco CIDR** anotado em cada zona

---

## 🔒 Fase 3: Regras de Tráfego (Roteamento e Segurança)

> Sub-redes criadas não servem de nada se elas não souberem como — e com quem — conversar.

**1. Segurança de Produção**

Planeje as regras de acesso (no desenho ou em uma tabela descritiva):

- A sub-rede da **Diretoria** deve conseguir acessar diretamente o **Banco de Dados na Produção**? Justifique o motivo lógico/segurança.
- O ambiente de **Desenvolvimento** precisa acessar os servidores de Produção. Qual **porta padrão** você liberaria para o time de Devs administrar os servidores Linux via terminal?

**2. O Gateway da Rede**

Qual IP você definiria como o **Gateway Padrão (Roteador)** para as máquinas da sub-rede de Desenvolvimento? *(Geralmente usa-se o primeiro ou o último IP utilizável da rede.)*

---

## 📝 O que eu espero que você me entregue

Mande no meu privado:

- **A tabela** com o cálculo das 3 sub-redes — contendo o Bloco CIDR, IP de Rede, Primeiro/Último IP útil e Broadcast de cada uma
- **O arquivo exportado** (PNG, JPEG ou PDF) do desenho da sua topologia de rede
- **A resposta curta** sobre a regra de segurança entre a Diretoria e o Banco de Dados da Produção

---

> Essa missão vai te dar a base exata para quando criarmos tabelas de roteamento e Security Groups em ambientes de Nuvem (Cloud). Estude a lógica dos bits da máscara e **capriche no desenho!**

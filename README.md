# Desafio: Configurando um Banco de Dados SQL no Microsoft Azure e Documentando o Processo

Este repositório documenta o processo de configuração de uma instância de Banco de Dados SQL na plataforma Microsoft Azure, como parte de um desafio prático. O objetivo é não apenas executar a configuração, mas também consolidar o aprendizado através da criação de um material de consulta com resumos, anotações e dicas sobre o uso do Azure.

---

## 🎯 Objetivos de Aprendizagem

Ao concluir este desafio, espera-se que eu seja capaz de:

* Aplicar os conceitos de serviços de nuvem do Azure em um ambiente prático.
* Documentar processos técnicos de forma clara, estruturada e compreensível.
* Utilizar o GitHub como ferramenta para versionamento e compartilhamento de documentação técnica.
* Entender as etapas fundamentais para provisionar e configurar um Banco de Dados SQL no Azure.
* (Opcional, mas explorado) Entender as etapas fundamentais para provisionar uma Máquina Virtual no Azure.

---

## 🛠️ Ferramentas Utilizadas

* **Microsoft Azure:** Plataforma de nuvem utilizada para provisionar e gerenciar os recursos.
* **GitHub:** Plataforma utilizada para hospedar este repositório e documentar o processo.
* **Markdown:** Linguagem de marcação utilizada para criar este README.

---

## ⚙️ Processo de Configuração do Banco de Dados SQL no Azure

A seguir, descrevo os passos gerais realizados para configurar uma instância de Banco de Dados SQL no Microsoft Azure:

1.  **Acesso ao Portal Azure:**
    * Login no [portal.azure.com](https://portal.azure.com) com as credenciais apropriadas.

2.  **Criação do Grupo de Recursos:**
    * Um Grupo de Recursos é um contêiner que mantém recursos relacionados para uma solução do Azure.
    * No portal, naveguei para "Grupos de recursos" e cliquei em "Criar".
    * Defini a **Assinatura**, um **Nome** para o grupo de recursos (ex: `rg-sqldb-desafio`) e a **Região**.

3.  **Criação do Banco de Dados SQL:**
    * Na barra de pesquisa do portal, busquei por "Banco de Dados SQL" e selecionei a opção correspondente.
    * Cliquei em "Criar Banco de Dados SQL".

4.  **Detalhes do Projeto e Banco de Dados:**
    * **Assinatura:** Selecionei a assinatura correta.
    * **Grupo de Recursos:** Selecionei o grupo de recursos criado anteriormente.
    * **Nome do banco de dados:** Inseri um nome para o banco de dados (ex: `testeteste`, como visto nas capturas).
    * **Servidor:**
        * Como não havia um servidor existente (ou para fins de aprendizado), cliquei em "Criar novo".
        * **Nome do servidor:** Um nome globalmente exclusivo (ex: `(novo) testestes (East US)`).
        * **Localização:** Escolhi uma região (ex: `(US) East US`).
        * **Método de autenticação:** Optei por "Usar autenticação SQL" (ou "Microsoft Entra authentication" conforme a necessidade).
            * Para autenticação SQL, defini um **Login de administrador do servidor** e uma **Senha**.
        * Cliquei em "OK" para criar o servidor.
    * **Pool elástico SQL:** Selecionei "Não" (para este desafio).
    * **Ambiente de carga de trabalho:** Selecionei "Desenvolvimento" (para otimizar custos, já que "Produção" teria outras configurações padrão).

5.  **Configurações de Rede (Networking):**
    * **Método de conectividade:** Mantive o padrão "Ponto de extremidade público".
    * **Permitir que serviços e recursos do Azure acessem este servidor:** Selecionei "Sim" (importante para outras aplicações Azure se conectarem).
    * **Adicionar endereço IP do cliente atual:** Selecionei "Sim" para permitir que minha máquina atual acesse o banco de dados para desenvolvimento/teste.
    * (Outras configurações como "Pontos de extremidade privados" e "Política de conexão" foram mantidas como padrão para este escopo).

6.  **Configurações de Segurança (Security):**
    * Explorei as opções do Microsoft Defender para SQL (geralmente iniciado com um trial ou desabilitado para economizar custos em ambientes de teste simples).

7.  **Configurações Adicionais (Additional settings):**
    * **Usar dados existentes:** Mantive "Nenhum" (para criar um banco de dados vazio).
    * **Ordenação (Collation):** Mantive o padrão ou escolhi um conforme a necessidade da aplicação.

8.  **Revisar + Criar:**
    * Revisei todas as configurações e os custos estimados (ex: "Uso Geral (GP_S_Gen5_1)", "Custo por GB", "Armazenamento máximo", "CUSTO ESTIMADO DE ARMAZENAMENTO/MÊS", "CUSTO DE CÁLCULO/VCORE SEGUNDO").
    * Cliquei em "Criar" para iniciar o provisionamento do banco de dados e do servidor (se novo).

---

## 🖥️ (Opcional) Processo de Configuração de Máquina Virtual (VM) no Azure

Durante a exploração da plataforma, também realizei a criação de uma Máquina Virtual. Os passos gerais foram:

1.  **Criação da Máquina Virtual:**
    * Busquei por "Máquinas Virtuais" e cliquei em "Criar".

2.  **Básico (Basics):**
    * **Detalhes do projeto:** Selecionei **Assinatura** e **Grupo de Recursos** (podendo ser o mesmo do BD SQL ou um novo).
    * **Detalhes da instância:**
        * **Nome da máquina virtual:** Um nome descritivo.
        * **Região:** Ex: `(US) East US`.
        * **Opções de disponibilidade:** Ex: "Zona de disponibilidade".
        * **Zona de disponibilidade:** Ex: "Zona 1".
        * **Tipo de segurança:** Ex: "Computadores virtuais de inicialização confiável".
        * **Imagem:** Sistema Operacional (ex: Windows Server, Ubuntu Server).
        * **Tamanho:** Tipo de VM com base em vCPU, RAM (afeta o custo).
        * **Conta de administrador:** Nome de usuário e senha.
        * **Regras de porta de entrada:** Selecionei portas necessárias (ex: RDP (3389) para Windows, SSH (22) para Linux).

3.  **Discos (Disks):**
    * Tipo de disco do SO (ex: SSD Premium).
    * Configurações de discos de dados (se necessário).

4.  **Rede (Networking):**
    * **Interface de rede:**
        * **Rede virtual:** Criar nova ou selecionar existente.
        * **Sub-rede:** Criar nova ou selecionar existente.
        * **IP público:** Criar novo ou selecionar existente (ou nenhum).
        * **Grupo de segurança de rede do adaptador de rede (NSG):** Básico ou Avançado. Configurei as portas de entrada permitidas (ex: RDP).

5.  **Gerenciamento (Management) e Monitoramento (Monitoring):**
    * Configurei opções de monitoramento e diagnóstico conforme a necessidade (ex: "Habilitar com a conta de armazenamento gerenciada (recomendado)").

6.  **Revisar + criar:**
    * Revisei as configurações e cliquei em "Criar".


### Sobre Bancos de Dados SQL no Azure:

* **Grupos de Recursos:** Essenciais para organizar todos os componentes de uma solução e gerenciar custos e permissões de forma agrupada.
* **Servidor SQL Lógico:** É um pré-requisito para criar um Banco de Dados SQL. Ele atua como um ponto de administração central para múltiplos bancos de dados. Não é uma instância de servidor como em um ambiente on-premises, mas um construto lógico.
* **Níveis de Serviço e Modelos de Compra:**
    * **DTU (Database Transaction Unit):** Modelo mais simples, com recursos pré-configurados de CPU, memória e I/O. Bom para começar.
    * **vCore (Virtual Core):** Maior flexibilidade, permite escolher o número de vCores, quantidade de memória e armazenamento de forma independente. Mais indicado para controle granular e workloads específicas. As capturas de tela mostram o modelo vCore ("Uso Geral (GP_S_Gen5_1)").
* **Autenticação:**
    * **Autenticação SQL:** Usuário e senha definidos no servidor.
    * **Autenticação do Microsoft Entra ID (anteriormente Azure Active Directory):** Permite usar identidades do Entra ID para se conectar, oferecendo gerenciamento centralizado de identidades e maior segurança.
* **Firewall:** É crucial configurar as regras de firewall no nível do servidor para permitir conexões. Lembre-se de adicionar o IP do cliente e permitir acesso de serviços Azure se necessário.
* **Custos:** Fique atento aos custos estimados durante a criação e monitore-os regularmente. O modelo "Desenvolvimento" para a carga de trabalho do banco de dados e a escolha de um "Ambiente de carga de trabalho" para Desenvolvimento no SQL podem ajudar a reduzir custos em ambientes não produtivos.
* **Elastic Pools:** Útil quando se tem múltiplos bancos de dados com picos de uso variáveis, permitindo que compartilhem recursos e otimizem custos.

### Sobre Máquinas Virtuais no Azure:

* **Zonas de Disponibilidade:** Aumentam a resiliência da aplicação ao distribuir VMs em diferentes locais físicos dentro de uma região Azure, protegendo contra falhas de datacenter. Selecionar várias zonas ao criar a VM (como sugerido na interface "Agora você pode selecionar várias zonas. Selecionar várias zonas criará uma VM por zona.") é uma prática para alta disponibilidade.
* **Tipos de Segurança:** "Computadores virtuais de inicialização confiável" oferecem recursos de segurança aprimorados.
* **Grupos de Segurança de Rede (NSG):** Atuam como um firewall para controlar o tráfego de entrada e saída da VM e suas sub-redes.
* **IP Público:** Necessário se você precisa acessar a VM diretamente da internet (ex: via RDP ou SSH).

### Dicas Gerais do Azure:

* **Nomenclatura:** Adote um padrão de nomenclatura consistente para seus recursos. Facilita a identificação e o gerenciamento.
* **Tags:** Use tags para organizar e categorizar recursos, especialmente para controle de custos e faturamento.
* **Azure CLI e PowerShell:** Além do portal, o Azure oferece ferramentas de linha de comando poderosas para automação e gerenciamento.
* **Documentação Oficial:** A documentação da Microsoft é extensa e um recurso valioso.

---

## 📚 Recursos Úteis
## ✨ Futuras Implementações/Melhorias

* Conectar uma aplicação simples ao Banco de Dados SQL provisionado.
* Explorar opções avançadas de segurança e backup.
* Automatizar o provisionamento com Azure CLI ou ARM Templates.

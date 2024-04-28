# AZ-900 
### Resumo de preparação pro Exame Azure AZ-900

# 1. Benefícios da Nuvem:

1- Alta Disponibilidade
-> Tempo de disponibilidade do recurso (SLA - Service Level Agreement)

2- Escalabilidade
-> Horizontal (Mais instâncias executando o recurso) ou vertical (Maior potencial de processamento de um recurso)
Durante um determinado pico eu quero aumentar o uso de um recurso.

3- Alcance Global
-> Recursos disponíveis globalmente

4- Agilidade
-> Provisionamento de recursos com muita velocidade

5- Recuperação de desastre
-> Conseguir distribuir os recursos de backup em caso de desatre, de uma forma global

6- Tolerância a Falhas
-> Permite monitoramento de recursos disponíveis e facilmente se direciona para um recurso com melhor resposta

7- Elasticidade
-> Configurar para que um recurso aumente seus recursos e depois volte ao normal

8- Capacidade de latÊncia do Cliente
-> O quanto meu cliente tem de tempo de resposta

9- Considerações sobre custo preditivo
-> Como é pago pelo uso, tem-se a previsibilidade de custo

10- Segurança
-> Políticas de segurança com exigência internacional

## 1.2 Tipos de investimento

CapEx e OpEx
1- CapEx:

- Gasto inicial de dinheiro com infraestrutura física.
- Tem um valor reduzido ao longo do tempo

2- OpEx:

- Gasto com produtos e serviços pagos conforme o uso
- Recebe a conta imediatamente
- Cloud é tudo OpEx

## 1.3 Modelo baseado em Consumo

Pizza As A Service

`On Premise - Feito em casa`

- **Suas responsabilidades:**

- 1- Mesa
- 2- Bebida
- 3- Eletricidade / Gás
- 4- Forno / Fogão
- 5- Fogo
- 6- Massa de Pizza
- 7- Molho de Tomate
- 8- Queijo
- 9- Complementos

`IaaS - Comprar congelado`

- **Suas responsabilidades:**

- 1- Mesa
- 2- Bebida
- 3- Eletricidade / Gás
- 4- Forno / Fogão
- 5- Fogo

- **Responsabilidades do terceiro:**
- 6- Massa de Pizza
- 7- Molho de Tomate
- 8- Queijo
- 9- Complementos

`PaaS - Pizza delivery`

- **Suas responsabilidades:**
- 1- Mesa
- 2- Bebida

- **Responsabilidades do terceiro:**
- 3- Eletricidade / Gás
- 4- Forno / Fogão
- 5- Fogo
- 6- Massa de Pizza
- 7- Molho de Tomate
- 8- Queijo
- 9- Complementos

`SaaS - Jantar fora:`

- **Responsabilidades do terceiro:**
- 1- Mesa
- 2- Bebida
- 3- Eletricidade / Gás
- 4- Forno / Fogão
- 5- Fogo
- 6- Massa de Pizza
- 7- Molho de Tomate
- 8- Queijo
- 9- Complementos

## 1.4. Caso Especial

Serverless

- -> Azure Functions
- -> Aplicativos lógicos do Azure

# 2. Componentes de Arquitetura do Azure

## 2.1. Regiões e Zonas de Disponibilidade

### 2.1.2 Região

`é uma localização física que você pode ter um ou mais Datacenters. `

Hoje, mais de 60 regiões em mais de 140 países.
Uma região, tipicamente, tem três Datacenters e cada Datacenter é conhecido como zona de disponibilidade. Seguindo esta referência, cada região possui três datacenters (zona de disponibilidade).

#### 2.1.2.1 Pares de Regiões

`São regiões com separação mínima de 300 milhas que possuem replicação autompatica  para alguns serviçoa, tem recuperação priorizada em caso de interrupção e que as atualizações são lançadas sequencialmente para minimizar o tempo de inatividade.`

#### 2.1.2.2 Opções de disponibilidade

`é possível melhorar a disponibilidade de meus recursos melhorando o nível de SLA trabalhando com Zonas de Disponibilidade e Pares de Regiões.`

## 2.2. Assinaturas e Grupos de Recursos

### 2.2.1 Recursos

`São componentes que são gerenciáveis dentro da plataforma podendo, a qualquer momento, construir, modificar seu comportamento ou excluir.`

- Máquinas Virtuais
- Contas de Armazenamento
- Redes Virtuais
- Serviços de Aplicativos
- Bancos de Dados SQL
- Funções
- etc.

### 2.2.2 Grupo de Recursos

`Container lógico para gerenciar e agregar recuros a um mesmo conjunto de Recursos do Azure.`

O grupo de recursos é criado em uma determinada região, mas os itens que compõem esse Grupo de Recursos podem estar em qualquer outra egião diferente da região na qual o Grupo de Recursos foi criado. Eles não possuem uma vinculçação direta de região.

Um recurso possui um e apenas um Grupo de Recursos responsável.

Você pode ter diferentes Grupos de Recursos, mas um recurso sempre vai estar vinculado a um e apenas um Grupo de recursos. E este recurso pode ser movido para qualquer um dos seus Grupos de Recursos.

Excluindo-se o Grupo de Recursos, todos os seus recursos são automaticamente excluídos, também.

Tomemos como exemplo um AppService, uma Máquina Virtual e um Banco de Dados. Estes recursos podem ter diferentes arranjos:

1- Todos em um mesmo Grupo de Recursos

2- Grupo de Recursos Web com o AppService

3- Grupo de Recursos Máquina Virtual com a Máquina Virtual

4- Grupo de Recursos Armazenamento com o Banco de Dados

### 2.2.3 Azure Resource Manager

`O Azure Resource Manager (ARM) oferece uma camada de gerenciamento que permite que você crie, atualize e exclua recursos na sua assinatura do Azure.`

Recurso disponível via:

1- Portal do Azure

2- Azure PowerShell

3- CLI doAzure

4- Clientes REST

Permite gerar os recursos com os devidos permissionamentos, além disso, pode-se utilizar tags para agrupar as informações de custo por tags.

### 2.2.4 Assinaturas do Azure

`Assinatura do Azure é uma partição lógica que permite estipular limites de cobrança e de controle de acesso para cada assinatura individualmente`

#### 2.2.4.1 Grupos de Gerenciamento

                                       Grupo de Gerenciamento        Grupos de Gerenciamento
                                                 |
                                     ____________|__________        ------------------------
                                     |                     |
                                     |                     |
                                Assinatura 1          Assinatura 2        Assinaturas
                                     |                     |
                       ______________|___________          |        -----------------------
                       |                        |          |
                       |                        |          |
                      GR 1                     GR 2       GR 3         Grupos de Recursos
                       |                        |          |
           ____________|_____________           |          |         ---------------------
           |           |            |           |          |
           |           |            |           |          |
       Recurso 1   Recurso 2   Recurso 3   Recurso 4    Recurso 5           Recursos

- Um Grupo de Gerenciamento pode incluir várias assinaturas do Azure
- As assinaturas herdam as condições aplicadas ao grupo de gerenciamento
- é possível oferecer suporte a **10.000 grupos de gerenciamento em um único diretório**
- Uma árvore de grupos de gerenciamento pode oferecer suporte a até **seis níveis de profundidade**

# 3. Serviços

## 3.1. Web App

- Escolha subscrição (Free Tier)
- Escolha o Grupo de Recursos ou crie um novo (AZ900-YT)
- Defina um nome para o Web App (gsantanawebapp01) - Irá gerar o endereço https://gsantantawebapp01.azurewebsites.net/
- Escolha uma forma de Publicação (Docker Container)
- Escolha o Sistema Operacional (Linux)
- Escolha a Região (East US)
- Escolha o Plano (Free F1)
- Clique Next para configurar Banco de Dados
- Não Criar Banco de Dados
- Clique Next para configurar Docker
- Escolha tipo de Container (Single Container)
- Escolha a fonte da imagem (Docker Hub)
- Escolha o tipo de imagem (Public)
- Defina o nome da imagem. Corresponde ao nome dela dentro do Docker Hub (mcr.microsoft.com/azuredocs/aci-helloworld)
- Startup Command não precisa informar
- Clique Next para configurar Rede
- Enable public access (On)
- Clique Next para configurar Monitoramento
- Application Insights (No)
- Clique Next para Configurar Tags
- department : Sistemas Web
- environment : Treinamento
- owner : gilmar.santana
- project : AZ900
- Clique Next para Review
- Clique Create para fazer o Deploy

## 3.2. Azure Virtual Desktop

A Área de Trabalho Virtual do Azure é um serviço de virtualização de aplicativos e área de trabalho executado no Azure. Aqui estão alguns dos principais destaques:

- Proporcione uma experiência completa do Windows com o Windows 11, Windows 10 ou Windows Server. Use uma única sessão para atribuir dispositivos a um único usuário ou use várias sessões para escalabilidade.

- Ofereça áreas de trabalho completas ou use o RemoteApp para entregar aplicativos individuais.

- Apresente os Aplicativos do Microsoft 365 para empresas e otimize-os para execução em cenários virtuais multiusuário.

- Instale sua linha de negócios ou aplicativos personalizados que você pode executar de qualquer lugar, incluindo aplicativos nos formatos Win32, MSIX e Appx.

- Forneça Software como serviço (SaaS) para uso externo.

- Substitua as implantações existentes dos Serviços de Área de Trabalho Remota (RDS).

- Gerencie as áreas de trabalho e os aplicativos de diferentes sistemas operacionais do Windows e do Windows Server com uma experiência de gerenciamento unificada.

- Hospede áreas de trabalho e aplicativos locais em uma configuração híbrida com o Azure Stack HCI.

## 3.3. Serviços de Rede do Azure

### 3.3.1 Virtual Networks (VNet)

Permite que recursos do Azure se comuniquem entre si, com a Internet e com redes locais.

### 3.3.2. VPN Gateway

O Gateway de VPN do Azure é um serviço que pode ser usado para enviar tráfego criptografado entre uma rede virtual do Azure e locais pela Internet pública. Também é possível usar um Gateway de VPN para enviar tráfego criptografado entre as redes virtuais do Azure pela rede da Microsoft. O Gateway de VPN usa um tipo específico de gateway de rede virtual do Azure chamado gateway de VPN. Várias conexões podem ser criadas com o mesmo gateway de VPN. Quando você cria várias conexões, todos os túneis de VPN compartilham a largura de banda de gateway disponível.

### 3.3.3. Express Route

O ExpressRoute permite que você estenda suas redes locais para a nuvem da Microsoft em uma conexão privada com a ajuda de um provedor de conectividade. Com o ExpressRoute, você pode estabelecer conexões com os serviços em nuvem da Microsoft, como o Microsoft Azure e o Microsoft 365.

A conectividade pode ocorrer de uma rede any-to-any (VPN de IP), uma rede Ethernet ponto a ponto ou uma conexão cruzada virtual por meio de um provedor de conectividade em uma colocação. As conexões de ExpressRoute oferecem mais confiabilidade, velocidades mais rápidas, latências consistentes e maior segurança que as conexões típicas, porque não acessam a Internet pública.

## 3.4. Serviços de Armazenamento do Azure

### 3.4.1. Storage Account (Blob)

Otimizado para armazenar grandes quantidades de dados não estruturados, como dados binários ou texto.

### 3.4.2. Disk

Fornece discos para máquinas virtuais, aplicativos e outros serviços acessarem e usarem.

### 3.4.3. Azure Files

Configuram compartilhamentos de arquivos de rede altamente disponíveis que podem ser acessados usando o protocolo padrão Bloco de Mensagens do Servidor (SMB)

## 3.5 Camadas de Armazenamento do Azure

### 3.5.1. Frequente (Hot)

Otimizada para armazenamento de dados acessados com frequência. Rápida escrita e leitura.

### 3.5.2. Esporádico (Cool)

Otimizada para armazenamento de dados acessados com pouca frequência e armazenados por pelo menos 30 dias. Maior custo pra leitura e menor custo pra escrita.

### 3.5.3. Arquivar (Archive)

Otimizada para armazenamento de dados acessados raramente e armazenados por plo menos 180 dias com requisitos de latência flexíveis. Custos menores ainda para escrita e maiores ainda para leitura, com latência para disponibilização dos dados.

## 3.6 Serviços de Banco de Dados do Azure

### 3.6.1. Azure Cosmos DB

Solução NoSQL distribuído globalmente que escala de maneira elástica e independente da taxa de transferência e armazenamento.

### 3.6.2. Azure SQL Server

Banco de dados relacional como serviço (Database as a Service - DaaS) baseado na última versão estável do necanismo de banco de dados do MSSQL Server.

### 3.6.3. Azure MySQL Server

Banco de dados relacional como serviço (Database as a Service - DaaS) do banco de dados MySQL totalmente gerenciado para desenvolvedores de aplicativos.

### 3.6.4. Azure PostgreSQL

Banco de dados relacional como serviço (Database as a Service - DaaS) do banco de dados PostgreSQL open-source.

## 3.7. Azure IoT

*IoT* é a capacidade dos dispositivos de reunir e retransmitir informações para análise de dados.

- **Iot Central Applications**: é uma solução SaaS de Iot global totalmente gerenciada que facilita conectar, monitorar e gerenciar ativos de IoT em escala.

- **Iot Hub**: é um serviço de gerenciamento hospedado na nuvem que atua como um hub central de mensagens para comunicação bidirecional entre aplicativos de IoT e os dispositivos que ele gerencia.

- **Azure Sphere**: é uma plataforma de aplicativo segura e de alto nível com recursos internos de comunicação e segurança para dispositivos conectados à internet.

O Azure Sphere é um dispositivo homologado pela Azure que coleta as informações no ambiente do cliente e se conecta com o IoT Hub que recebe mensagens em grande volume de dispositivos pré-cadastrados. Já o IoT Central funciona como um grande dashboard que concentra as informações de todos os seus dispositivos IoT bem como, monitora todo o tráfego dessas informações.

### 3.7.1. Criando um dispositivo IoT

- Acesse o endereço `https://azure-samples.github.io/raspberry-pi-web-simulator/` para visitar o simulador do dispositivo.
  
- No portal Azure, entre em Iot Hub e crie um novo IoT Hub fazendo suas definições e escolhendo a opção de pagamento Free Tier.
  
- Depois do Iot Hub criado, abra a opção Devices e adicione um novo dispositivo.

- No novo dispositivo, copie as definições de **Primary connection string** e a adicione no raspberry simulator na variável correspondente à connection string e clique em run. O simulador enviará mensagens para o IoT Hub e a chegada dessas mensagens podem ser percebidas pelo dashboard do IoT Hub.

- Para rotear as mensagens recebidas pelo IoT Hub para um determinado local como um banco de dados, por exemplo, é preciso configurar a funcionalidade **Message routing**.


## 3.8. Big Data e Análise

- **Azure Synapse Analytics**: Enterprise Data Warehouse baseado na nuvem. Trabalha com dados estruturados.

- **HDInsight clusters**: Serviço de análise open-source e gerenciado para empresas.

- **Azure Databricks**: Serviço de análise baseado no Apache Spark.

## 3.9. Inteligência Artificial e Machine Learning

- **Azure Machine Learning**: baseado em nuvem para desenvolver, treinar e implantar modelos de machine learning. Plataforma preparada do Azure. Cria uma infraestrutura de container, storage, etc que permite utilizar uma plataforma de machine learning automatizado. Trabalhar com previsões para seu negócio.

- **Azure AI services**: habilitar rapidamente os aplicativos para ver, ouvir, falar, entender e interpretar as necessidades de um usuário. Com este serviço, é possível enviar uma foto e e receber a descrição dessa foto, falar algo e receber a transcrição,enviar um texto e receber sua tradução, detecção de anomalias, etc. Uma funcionalidade interessante deste serviço é fazer o upload de uma fatura e automaticamente ter a extração de seus dados como: nome, valor, período, descrição do serviço, etc.

- **Bot Services**: desenvolver bots inteligentes, de nível empresarial.


## 3.10. Serverless

Computação baseada em evento. Um evento pode ser a criação de um arquivo em pasta, uma mensagem HTTP que chegou, uma mensagem HTTP que chegou na fila, um evento no banco de dados, etc.

- _Azure Functions_: código baseado em evento executando o serviço e não ainfraestrutura subjacente.
- _Logic Apps_: Automatizar e orquestrar tarefas, processos empresariais e fluxos de trabalho para integrar aplicativos.


## 3.11. Devops e GitHub

### 3.11.1. Azure DevOps

Ferramenta de colaboração de desenvolvimento, incluindo pipelines, cartões Kanban e testes de carga automatizados baseados em nuvem.

Gestão de projeto, armazenamento de código, versionamento de pacotes, testes e gestão de pipelines CI/CD

### 3.11.2. GitHub

Hosting de desenvolvimento de software com controle de versão, gerenciamento de código-fonte e gerenciamento de bugs/tarefas.

### 3.11.3. GitHub Actions

Automatizar o fluxo de trabalho de software para criar, testar e implantar de dentro do GitHub.

### 3.11.4. Azure DevTest Labs

Criar rapidamente ambientes no azure enquanto minimiza os gastos e controla os custos.

## 3.12. Ferramentas de Gerenciamento

Permite executar rotinas via Azure Resource Manager (ARM)

- Portal do Azure
- Azure PowerShell
- Aplicativo Móvel do Azure
- Interface de Linha de Comando (CLI)
- API REST do Azure
- Azure Cloud Shell

Criando uma vm via Azure Cloud Shell:

`az vm create --resource-group AZ900-YT --name gsantanavm02 --image win2022datacenter --public-ip-sku Standard --admin-username gilrsantana`

Na sequência, será pedido para informar a senha e confirmar.

`Admin Password: `

`Confirm Admin Password: `

Tudo ocorrendo com sucesso, a resposta:

```
{
  "fqdns": "",
  "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Compute/virtualMachines/gsantanavm02",
  "location": "eastus",
  "macAddress": "60-45-BD-FF-A8-E7",
  "powerState": "VM running",
  "privateIpAddress": "10.0.0.5",
  "publicIpAddress": "52.170.0.49",
  "resourceGroup": "AZ900-YT",
  "zones": ""
}
```

Instalação do IIS

`az vm run-command invoke -g AZ900-YT -n gsantanavm02 --command-id RunPowerShellScript --scripts "Install-WindowsFeature -name Web-Server -IncludeManagementTools"`

Resposta de sucesso

```
{
  "value": [
    {
      "code": "ComponentStatus/StdOut/succeeded",
      "displayStatus": "Provisioning succeeded",
      "level": "Info",
      "message": "Success Restart Needed Exit Code      Feature Result                               \n------- -------------- ---------      --------------                               \nTrue    No             Success        {Common HTTP Features, Default Document, D...\n\n",
      "time": null
    },
    {
      "code": "ComponentStatus/StdErr/succeeded",
      "displayStatus": "Provisioning succeeded",
      "level": "Info",
      "message": "",
      "time": null
    }
  ]
}
```

Abrir porta 80

`az vm open-port --port 80 --resource-group AZ900-YT --name gsantanavm02`

Resposta de sucesso

```
{
  "defaultSecurityRules": [
    {
      "access": "Allow",
      "description": "Allow inbound traffic from all VMs in VNET",
      "destinationAddressPrefix": "VirtualNetwork",
      "destinationAddressPrefixes": [],
      "destinationPortRange": "*",
      "destinationPortRanges": [],
      "direction": "Inbound",
      "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG/defaultSecurityRules/AllowVnetInBound",
      "name": "AllowVnetInBound",
      "priority": 65000,
      "protocol": "*",
      "provisioningState": "Succeeded",
      "resourceGroup": "AZ900-YT",
      "sourceAddressPrefix": "VirtualNetwork",
      "sourceAddressPrefixes": [],
      "sourcePortRange": "*",
      "sourcePortRanges": [],
      "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
    },
    {
      "access": "Allow",
      "description": "Allow inbound traffic from azure load balancer",
      "destinationAddressPrefix": "*",
      "destinationAddressPrefixes": [],
      "destinationPortRange": "*",
      "destinationPortRanges": [],
      "direction": "Inbound",
      "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG/defaultSecurityRules/AllowAzureLoadBalancerInBound",
      "name": "AllowAzureLoadBalancerInBound",
      "priority": 65001,
      "protocol": "*",
      "provisioningState": "Succeeded",
      "resourceGroup": "AZ900-YT",
      "sourceAddressPrefix": "AzureLoadBalancer",
      "sourceAddressPrefixes": [],
      "sourcePortRange": "*",
      "sourcePortRanges": [],
      "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
    },
    {
      "access": "Deny",
      "description": "Deny all inbound traffic",
      "destinationAddressPrefix": "*",
      "destinationAddressPrefixes": [],
      "destinationPortRange": "*",
      "destinationPortRanges": [],
      "direction": "Inbound",
      "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG/defaultSecurityRules/DenyAllInBound",
      "name": "DenyAllInBound",
      "priority": 65500,
      "protocol": "*",
      "provisioningState": "Succeeded",
      "resourceGroup": "AZ900-YT",
      "sourceAddressPrefix": "*",
      "sourceAddressPrefixes": [],
      "sourcePortRange": "*",
      "sourcePortRanges": [],
      "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
    },
    {
      "access": "Allow",
      "description": "Allow outbound traffic from all VMs to all VMs in VNET",
      "destinationAddressPrefix": "VirtualNetwork",
      "destinationAddressPrefixes": [],
      "destinationPortRange": "*",
      "destinationPortRanges": [],
      "direction": "Outbound",
      "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG/defaultSecurityRules/AllowVnetOutBound",
      "name": "AllowVnetOutBound",
      "priority": 65000,
      "protocol": "*",
      "provisioningState": "Succeeded",
      "resourceGroup": "AZ900-YT",
      "sourceAddressPrefix": "VirtualNetwork",
      "sourceAddressPrefixes": [],
      "sourcePortRange": "*",
      "sourcePortRanges": [],
      "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
    },
    {
      "access": "Allow",
      "description": "Allow outbound traffic from all VMs to Internet",
      "destinationAddressPrefix": "Internet",
      "destinationAddressPrefixes": [],
      "destinationPortRange": "*",
      "destinationPortRanges": [],
      "direction": "Outbound",
      "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG/defaultSecurityRules/AllowInternetOutBound",
      "name": "AllowInternetOutBound",
      "priority": 65001,
      "protocol": "*",
      "provisioningState": "Succeeded",
      "resourceGroup": "AZ900-YT",
      "sourceAddressPrefix": "*",
      "sourceAddressPrefixes": [],
      "sourcePortRange": "*",
      "sourcePortRanges": [],
      "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
    },
    {
      "access": "Deny",
      "description": "Deny all outbound traffic",
      "destinationAddressPrefix": "*",
      "destinationAddressPrefixes": [],
      "destinationPortRange": "*",
      "destinationPortRanges": [],
      "direction": "Outbound",
      "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG/defaultSecurityRules/DenyAllOutBound",
      "name": "DenyAllOutBound",
      "priority": 65500,
      "protocol": "*",
      "provisioningState": "Succeeded",
      "resourceGroup": "AZ900-YT",
      "sourceAddressPrefix": "*",
      "sourceAddressPrefixes": [],
      "sourcePortRange": "*",
      "sourcePortRanges": [],
      "type": "Microsoft.Network/networkSecurityGroups/defaultSecurityRules"
    }
  ],
  "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
  "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG",
  "location": "eastus",
  "name": "gsantanavm02NSG",
  "networkInterfaces": [
    {
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkInterfaces/gsantanavm02VMNic",
      "resourceGroup": "AZ900-YT"
    }
  ],
  "provisioningState": "Succeeded",
  "resourceGroup": "AZ900-YT",
  "resourceGuid": "c0f444ea-68a0-4f90-a69a-c7012eb381b0",
  "securityRules": [
    {
      "access": "Allow",
      "destinationAddressPrefix": "*",
      "destinationAddressPrefixes": [],
      "destinationPortRange": "3389",
      "destinationPortRanges": [],
      "direction": "Inbound",
      "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG/securityRules/rdp",
      "name": "rdp",
      "priority": 1000,
      "protocol": "Tcp",
      "provisioningState": "Succeeded",
      "resourceGroup": "AZ900-YT",
      "sourceAddressPrefix": "*",
      "sourceAddressPrefixes": [],
      "sourcePortRange": "*",
      "sourcePortRanges": [],
      "type": "Microsoft.Network/networkSecurityGroups/securityRules"
    },
    {
      "access": "Allow",
      "destinationAddressPrefix": "*",
      "destinationAddressPrefixes": [],
      "destinationPortRange": "80",
      "destinationPortRanges": [],
      "direction": "Inbound",
      "etag": "W/\"e8da33d7-6259-45b2-aa20-f9f6e23508cb\"",
      "id": "/subscriptions/cf2c2187-0754-416f-aca0-9ed1e69314fe/resourceGroups/AZ900-YT/providers/Microsoft.Network/networkSecurityGroups/gsantanavm02NSG/securityRules/open-port-80",
      "name": "open-port-80",
      "priority": 900,
      "protocol": "*",
      "provisioningState": "Succeeded",
      "resourceGroup": "AZ900-YT",
      "sourceAddressPrefix": "*",
      "sourceAddressPrefixes": [],
      "sourcePortRange": "*",
      "sourcePortRanges": [],
      "type": "Microsoft.Network/networkSecurityGroups/securityRules"
    }
  ],
  "tags": {},
  "type": "Microsoft.Network/networkSecurityGroups"
}
```

## 3.13. Azure Advisor

O Azure Advisor analisa os recursos implantados no Azure e faz recomendações com base nas melhores práticas para otimizar as implantações od azure. Ele analisa:
- Custo
- Segurança
- Confiabilidade
- Excelência operacional
- Desempenho

## 3.14. Azure Monitor

O Azure Monitor maximiza a disponibilidade e o desempenho de aplicativos e serviços coletando, analisado e agindo sobre a telemetria de ambientes em nuvens e locais. Recursos:
- Application Insights (observabilidade)
- Análise de Logs (registro de eventos)
- Alertas Inteligentes
- Ações de Automação
- Paineis Personalizados

Com esta ferramenta é possível, mediante a ocorrÊncia de eventos, enviar e-mail, realizar ligação telefônica, abrir tickets de chamado para o time técnico corrigir um erro.

## 3.15. Service Health

Status dos serviços do Azure e planejamento de manutenção dos serviços que você utiliza.


# 4. Segurança

A segurança dentro do Azure é pensada a partir de um modelo de segurança completa, começando pela proteção física do ambiente, identidade de acesso, perímetro de proteção, rede de comunicação, dispositivos de computação, aplicativo e dados.

Modelo de **Segurança Compartilhada**.

| Responsabilidade                         | No Local | IaaS      | PaaS              | SaaS    |
| :--- | :---: | :---: | :---: | :---: |
| Governança de dados e Rights Managements | Cliente  | Cliente   | Cliente           | Cliente |
| Pontos de Extremidade do cliente         | Cliente  | Cliente   | Cliente           | Cliente |
| Gerenciamento de Conta e Acesso          | Cliente  | Cliente   | Cliente           | Cliente |
| Infraestrutura de Identidade e Diretório | Cliente  | Cliente   | Microsoft/Cliente | Microsoft/Cliente |
| Aplicativo                               | Cliente  | Cliente   | Microsoft/Cliente | Microsoft |
| Controle de Redes                        | Cliente  | Cliente   | Microsoft/Cliente | Microsoft |
| Sistema Operacional                      | Cliente  | Cliente   | Microsoft         | Microsoft |
| Hosts Físicos                            | Cliente  | Microsoft | Microsoft         | Microsoft |
| Rede Física                              | Cliente  | Microsoft | Microsoft         | Microsoft | 
| Datacenter Físico                        | Cliente  | Microsoft | Microsoft         | Microsoft |

## 4.1. Microsoft Defender For Cloud

O Microsoft Defender For Cloud é um serviço de monitoramento que fornece proteção contra ameaças nos datacenters do Azure e nos datacenters locais.

- Fornecer recomendações de segurança
- Detectar e bloquear malwares
- Analisar e identificar possíveis ataques
- Controlar o acesso just-in-time para portas

Recursos:

- Conformidade com a Política: Executar políticas em grupos de gerenciamento, assinaturas ou locatários.
- Avaliações Contínuas: Avaliar recursos novos e implantados para garantir que eles sejam configurados corretamente.
- Recomendações Personalizadas: Recomendações baseadas na carga de trabalho existente com instruções sobre como implementá-las.
- Proteção contra ameaças: Analisar as ameaças experimentadas por meio de alertas e relatórios de recursos afetados.

## 4.2. Microsoft Sentinel

O Azure Sentinel é uma solução de gerenciamento de informações de segurança (Security Information and Event Management - SIEM) que juntam informações de logs de ocorrências e eventos causadores, e de resposta automatizada de segurança (Security Orchestration Automatic Response - SOAR) coletando dados sobre ameaças de segurança de várias fontes e respondendo a eventos de segurança de forma mais eficiente, que fornece uma análise de segurança e inteligência contra ameaças em uma empresa.

- Coletar dados
- Detectar ameaças
- Investigar eventos
- Responder ao evento

## 4.3. Azure Key Vault

O Azure Key Vault armazena segredos do aplicativo em um local de nuvem centralizado para controlar com segurança as permissões eo registro em log de acesso.
- Gertenciamento de segredos
- Gerenciamento de chaves
- Gerenciamento de certificados
- Armazenar segredos apoiados por módulos de segurança de hardware (HSMs)

Criando um Key Vault

- Subscription: Free Tier
- Resource Group: AZ900-YT
- Key vault name: keyvaultgsantana01
- Pricing Tier: Standard
- Days to retain deleted vaults: 90
- Purge protection: Disable purge protection (allow key vault and objects to be purged during retention period)
- Permission model: Azure role-based access control (recommended)
- Resource access: None
- Public network access: Enabled
Allow all inbound and outbound access with option to restrict select inbound access using resource access configurations for this resource
- Public Access: Allow access from: All networks


Criar um secret

- Upload options: Manual
- Name: segredo
- Secret value: meusegredoescondido

## 4.4. Network Security Group

Os NSGs filtram o tráfego da rede para os recursos do Azure (e apartir dele também) nas Redes Virtuais do Azure. É um verdadeiro controlador de tráfego definindo 'o que passa', 'quem passa' e 'quando passa' (firewall interno).

- Definir as regras de entrada e saída para filtrar por fonte e endereço IP de destino, porta e protocolo.
- Adicionar várias regras, conforme o necessários, dentro dos limites da assinatura.
- O Azure aplica regras de segurança de linha de base, padrão aos novos NSGs.
- Substituir as regras padrão por regras novas e de prioridade mais alta.


## 4.5. Azure Firewall

Firewall como serviço (FaaS) com estado e gerenciado que concede/nega acesso ao servidor com base no endereço IP de origem, para proteger recursos de rede.

- Aplica regras de filtragem de tráfego de entrada e saída
- Alta disponibilidade integrada
- Escalabilidade de nuvem irrestrita
- Usa o registro em log do Azure Monitor

Também tem suporte ao **DNAT**, que é um recurso de conversão entre endereço de entrada e endereço de destino.

O **Web Application Firewall policies** (WAF) também fornece um firewall, fornecendo proteção interna, centralizada para seus aplicativos web.

## 4.6. DDoS Protection

Os ataques DDoS sobrecarregam e esgotam recursos de rede, tornando os aplicativos lentos ou indisponíveis. 

- Limpa o tráfego de rede indesejado antes que ele afete a disponibilidade do serviço.
- A camada de serviço básica é automaticamente ativada no azure
- A camada de serviço padrão adiciona recursos de mitigação ajustados para proteger recursos de Rede Virtual do Azure

# 5. Identidade, Governança, Privacidade e Conformidade

## 5.1. Serviços de identidade

### 5.1.1. Autenticação e Autorização

**Autenticação**
- Identifica a pessoa ou serviço buscando acesso a um recurso
- Solicita credenciais de acesso legítimo
- Base para criar princípios de identidade e controle de acesso seguros

**Autorização**
- Determina o nível de acesso de uma pessoa ou serviço autenticado
- Define quais dados ele pode acessar e o que pode fazer com eles

### 5.1.2. Azure Active Directory

O **Azure Active Directory** é o serviço de gerenciamento de acesso e identidade baseado na nuvem do Azure.
- Autenticação(credenciais de funcionários para acessar recursos)
- Logon único (SSO)
- Gerenciamento de aplicativos
- Empresas (B2B) - Empresas Federadas
- Serviços de indentidade entre empresa e cliente (B2C)
- Gerenciamento de dispositivos

### 5.1.3. Acesso Condicional - MFA e SSO

O Acesso condicional é usado pelo active Directory para reunir sinais, tomar decisões e impor políticas organizacionais. Através dele, diante de um determinado conjunto de fatores é possível tomar a decisão de bloquear um acesso. Por exemplo, se o usuário no Brasil acabou de fechar uma seção no Teams e 5 minutos depois é feita uma tentativa de acesso na Alemanha, essa tentativa de acesso pode ser considerada suspeita e o acesso bloqueado, mesmo utilizando credenciais válidas deste usuário.
- Associação de usuários ou grupos
- Localização do IP
- Dispositivo
- Aplicativo
- Detecção de risco

A **Autenticação Multifator** (MFA) fornece segurança adicional para as identidades, exigindo dois ou mais elementos para autenticação completa.
Dividida em três partes:

- Algo que **você sabe**
- Algo que **você tem**
- Algo que **você é** 

O **Single Sign On** é um serviço que por meio de uma autenticação única você tem acesso a deferentes sistemas, sem precisar fazer login para cada sistema que você entrar. Este processo é feito internamente pelo **SSO**

## 5.2. Governança

### 5.2.1. RBAC (Role-Based Access Control)

- Gerenciamento de acesso de glanuralidade fina
- Divida as tarefas dentro da equipe e conceda somente a quantidade de acesso de que os usuários precisam para trabalhar
- Habilite o acesso ao portal do Azure e o controle de acesso aos recursos

### 5.2.2. Bloqueio de Recursos (Lock)

- Habilitado com grande glanuralidade
- Proteja os recursos do Azure de exclusão ou modificação acidental
- Gerencie bloqueios no nível de assinatura, grupo de recurso ou recurso individual no portal do Azure

| Tipo de Bloqueio | Leitura | Atualização | Exclusão |
| ---              | :---:   | :---:       | :---:    |
| CanNotDelete     | Sim     | Sim         | Não      |
| ReadOnly         | Sim     | Não         | Não      |

### 5.2.3. Tags

- Fornecem metadados aos recursos do Azure
- Organizam os recursos em uma taxoonomia de maneira lógica
- Consistem em um par nome-valor
- Muito úteis para reunir informações de cobrança

### 5.2.4. Azure Policy

O Azure Policy ajuda a impor padrões organizacionais e avaliar conformidade em escala. Forneça governaça e consistência de recursos com conformidade regulamentar, segurança, custos e gerenciamento.
- Avalia e identifica os recursos do Azure que não atendem à sua política
- Fornece definições de políticas e iniciativas integradas, em categorias como Computação, Segurança, Rede, Armazenamento e Monitoramento.

### 5.2.5. Blueprints

O Azure Blueprint permite que as equipes de desenvolvimento criem e implantem novos ambientes com rapidez. As equipes de desenvolvimento podem desenvolver a confiança rapidamente por meio de conformidade organizacional com um conjunto de componentes integrados (como rede) para acelerar o desenvolvimento e a entrega.

- Atribuições de função
- Atribuições de política
- Modelos de Azure Resource Manager
- Grupos de Recursos

### 5.2.6. Cloud Adoption Framework (CAF)

- Abordagem para adoção de nuvem no Azure
- Melhores práticas do funcionários, parceiros e clientes Microsoft
- Ferramentas, orientações e narrativas para entrega de resultados

Princiapis pontos:
- **Estratégia**: defina a justificativa comercial e resultados esperados
- **Planejar**: alinhe os planos de adoção acionáveis com os resultados comerciais
- **Pronto**: prepare o ambiente d enuvem para as ações planejadas
- **Migrar**: migre e modernize cargas de trabalho existentes
- **Inovar**: deselvolva novas soluções de nuvem nativas ou híbridas
- **Controlar**: controle o ambiente e as cargas de trabalho
- **Gerenciar**: gerenciamento de operações para soluções híbridas e de nuvem

## 5.3. Privacidade e Conformidade

**Segurança**: Intencionalmente seguro. Com segurança inteligente integrada, a Microsoft ajuda a proteger contra ameaças cibernéticas conhecidas e desconhecidas, usando automação e inteligÊncia artificial. 

**Privacidade**: Temos o compromisso de garantir a privacidade das organizações por meio de nossos acordos contratuais e fornecendo controle e transparência ao usuário.

**Conformidade**: Respeitamos legislações e regulamentos locais e fornecemos cobertura abrangente de ofertas de conformidade.

### 5.3.1. Termos e Requisitos de Conformidade

A Microsoft oferece o conjunto mais abrangente de ofertas de conformidade (incluindo certificações e atestados) de qualquer provedor de serviços em nuvem. Algumas ofertas de conformidade incluem:
|   |   |
| ---  | ---  |
| **CJIS** - Serviço de informações da Justiça Criminal | **HIPAA** - Lei de portabilidade e responsabilidade do seguro de Saúde |
| **Certificação CSA STAR** | **ISO/IEC 27018**  |
| **Cláusulas do Modelo da UE**  | **NIST** - National Institute of Satandard and Technology |

### 5.3.1. Política de Privacidade da Microsoft

A política de privacidade da Microsoft promove a abertura e honestidade sobre como a Microsft lida com os dados do usuário coletados de seus produtos e serviços.

A política de privacidade da Microsoft explica:
- Quais dados a Microsoft processa
- Como a Microsoft os processa
- Para quais finalidades os dados são usados

### 5.3.2. Termos dos Serviços Online e adendo de Proteção de Dados

[Termos de Uso](https://www.microsoft.com/en-us/legal/terms-of-use).

**Termos dos Serviços Online**: Os termos de licenciamento define os termos e condições para produtos e serviços online adquitidos por meio de programas de licenciamento por volume da Microsoft.

**Adendo de Proteção de Dados**: O DPA estabelece as obrigações com relação ao processamento e segurança de dados do cliente e dados pessoais, em relação aos serviços online

### 5.3.3. Trust Center -  Central de Confiabilidade

[Central de Confiabilidade](https://www.microsoft.com/pt-br/trust-center).

O site de Central de Confiabilidade fornece:
- Informações aprofundadas de especialistas
- Listas curadas de recursos recomendados, organizadas por tópico
- Informações específicas de função para gerentes de negócio, administradores, engenheiros, avaliadores de risco, agentes de privacidade e equipes jurídicas.

### 5.3.4. Regiões Soberanas do Azure 

#### 5.3.4.1. Serviços do Governo dos EUA
Atende as necessidades de segurança e conformidade das agÊncias federais dos EUA, governos estaduais e locais e seus provedores de soluções.

Azure Governamental:
- Instância separada do Azure
- Fisicamente isolada de implantações que não sejam do governo americano.
- Acessível somente a pessoal verificado e autorizado.

Exemplos de padrões:
- FedRAMP
- NIST 800.171 (DIB)
- ITAR
- IRS 1075
- DoD L2
- L4 & L5
- CJIS

#### 5.3.4.2. China

A Microsoft é o primeiro provedor estrangeiro de serviços em nuvem pública da China, em conformidade com as regulamentações governamentais.

Recursos:
- Instância fisicamente separada dos serviços de nuvem do Azure operados pela **21ViaNet**
- Todos os dados permanecem dentro da China para garantir a conformidade

# 6. Preço e Ciclo de Vida do Azure

## 6.1. Planejamento e gerenciamento de custos - Domínio objetivo

- Identifique fatores que possam afetar custos (tipos de recursos, serviços, localizações, tráfego de entrada e saída)
- Identifique fatores que possam reduzir custos (instâncias reservadas, capacidade reservada, benefícios de uso híbrido e preço de spots)
- Descreva a funcionalidade e o uso da calculadora de preços e da calculadora de custo total de propriedade (TCO)
- Descreva afuncionalidade e o uso do gerenciamento de custos do azure

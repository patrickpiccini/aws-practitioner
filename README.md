
<h1 align="center">Estudo para certificação AWS</h1>
<p align="center">
    <img src="images/aws.png" alt="aws" width="200"/>
</p>

---
# Cloud Computing
O que é Cloud Computing  é a entrega sob demanda de poder de computação, armazenamento de banco de dados, aplicativos e outros recursos.
- Só irá pagar o que for utilizado, quando não usar mais, irá parar de pagar.
- Proporciona exatamente o tamanho e tipo de recurso computacional que precisa.
- Pode acessar vários recursos quando precisar, instantaneamente.
- Tem uma interface simples para gerenciar todos seus recursos de server, storages, databases etc.
A ideia de usar o serviços de cloud computing é mudar de seus servidores locais em escritórios e garagens, para um cloud , que também utiliza datacenters.

## 5 caracteristicas de cloud computing:
- Autoatendimento sob demanda;
- Amplo acesso à rede;
- Multilocação e pool de recursos;
- Elasticidade e escalabilidade rápida;
- Paga somente o que usa;

## 6 vantagens do Cloud Computing:
- Calcular despesas capitais(CAPEX) com despesas oreacionais(OPEX);
- Beneficio de enormes economias de escala;
- Dimensionar automaticamente a capacidade de hardware para aplicação;
- Aumento de velocidade e agilidade;
- Sem pagamentos desnecessário para processamentos que não usamos;
- Criação de aplicação global.

## Tipos de Cloud Computing:
- Infraestructure as a Service(IaaS): Fornece blocos de construção para TI em nuvem. Fornece redes, computadores, data storage, Alta flexibilidade, Facil para migrar para TI tradicional (servidor local).
- Plataform as a Service(PaaS): Remove a necessidade de organizações de gerenciamento de infraestrutura. Desenvolvimento e gerenciamento de suas aplicações
- Sofware as a Service(SaaS): Produto completo que será gerencia e executado pelo provedor de serviço

## 3 Princípios básicos para precificação da AWS
- Para computação: Pago pelo tempo exato do computador ligado.
- Para Armazenamento: Pago pela quantidade exata de dados armazenados na nuvem.4
- Para transferência fora da Nuvem: Pago apenas quando dados saírem da AWS 

## AWS Cloud History
Foi lançada em 2002 internamente na Amazom.com. Em 2004 lançaram a primeira oferta publica chamada SQS. Em 2006 realçaram  com a disponibilidade de SQS, S3 e EC2. 2007 lançaram na Europa. 

## AWS Regions
Estão em todo o mundo e são alocados data centers nessas regiões, quando usamos algum serviço, na maioria das vezes serão vinculados a uma região especifica
Como escolher uma AWS region? Depende, pois vai depender da distância, podendo causar alta latência entra a comunicação do data center. Tambem há o fator de q algumas regiões não tem todos os serviços disponibilizados. Os preços variam de região para região, então teria q consultar a tabela de valores entre as regiões
AWS Avaliability Zone
São o que está acontecendo na região. Cada região terá varias Avaliability Zones(normalmente 3, min:2, max:6) Elas ficam separados para que cara uma seja isolada da outra para caso aconteça algum desastre, tenha outra para ser substituída. Elas são conectadas uma a aoutra com latência ultra-baixa. Juntas elas formam uma Região.


---
<h1 align="center">IAM – Identity and Acess Management</h1>

## Users, Goups and Policies
É criado User e Goups para possemos atribuir policies a eles, fazendo com que tenham acesso aos serviços que necessitam ter, e não a tudo como um ADM. Os User e Goups pode receber um JSON document chamado POLICIE.

É uma Boa pratica criar um usuário ADM para fazer a administração da AWS, e resguardar a conta Root por segurança

## IAM Policies
Json document há uma estrutura como os seguintes campos: **Numero de versão** , **Id** para identificação da policie,e **Statement** contendo mais informações como: **Sid** sendo um ID de instrução, **effect** sendo o efeito da policie. **Principals** consiste em quais contas, usuário ou funções receberão essa policie. **Action** contendo uma lista de chamadas a API q serão setadas de acondo com o valor do campo **effect**. E resource contem uma lista de recursos que as ações serão aplicadas.

As policies bom ser atribuídas a um grupo ou a um usuário. Também pode ser criado suas próprias Policies escrevendo um Json ou com interface visual.

## IAM MFA
É o sistema de proteção dos usuário e grupos contendo dois mecanismos de defesa. O primeiro é **Password Policy.** Nesse mecanismo pode ser configurado exigências na hora de cadastrar uma senha, como numero de caracteres, letras especiais etc. pode ser definido também um tempo de expiração das senhas para q sejam trocadas seguidamente. e também para não reutilizar senhas q já foram usadas.

O segundo mecanismo é o **MAF(Multi Factor Autentication).** O beneficio do MAF é que caso sua senha seja perdida/hackeada, não será comprometida pois para acessar, precisará dos números do MFA para fazer login.

**Dispositivos MAF da AWS:**
- **Virtual MFA** com Google Authenticator ou Authy;
- Universal 2nd Factor (U2F) Security Key. É um dispositivo Físico tipo USB;
- Hardware Key Fob MAF Device;
- AWS GovCloud;

## AWS Access Keys, CLI and SDK
Existem 3 jeitos de acessar a conta AWS;
- AWS Management Console (Password Policy + MFA);
- AWS CLI: Protegidas por chaves de acesso;
- AWS SDK: Protegidas por chave de acesso. Existe para Aplications, Mobile e IoT

Para gerar uma chave de acesso deve ser feito através da AWS Console

## Configurar AWS CLI

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-version.html

Após fazer a instalação do CLI no seu computador, é necessário configurar o o acesso do CLI com as chaves de acesso do usuario(IAM > users > youruser > Security credentials).

``` AWS CLI
**C:\Users\Patrick>** aws configure
**AWS Access Key ID [None]:** AKIA3BEXK6YIQICPK7HW
**AWS Secret Access Key [None]:** SOdsxnfd7Fqgomot4hXDTDLU/ZBUW/NyCdHZb6ip
**Default region name [None]:** sa-east-1
**Default output format [None]:** (enter)
```

Para testar o usuario adm configurado: 
``` AWS CLI
**C:\Users\Patrick>** aws iam list-users
```

## AWS Cloud Shell

Está disponível somente para algumas Regions

Todos os arquivos que forem criados em seu AWS Cloud Shell, mesmo após reiniciar o terminar ainda terá seus arquivos. É possível fazer Download e Upload de arquivos através do AWS Cloud Shell

## IAM Roles for AWS Services

É responsável por criar permissões aos serviços que o usuário esta usando, para q que este serviço possa fazer outra interações com a AWS

## IAM Security Tools

IAM Credential Report(Acount Level) - Pode ser criado um relatório de credenciais do IAM;
_IAM > Credential Report > Download_

IAM Access Advisor(User Level) – Mostrará as permissões de serviço concedidas a um usuário
_IAM > User > YourUser > Access Advison_

## Shared Responsibility Model for IAM
<img src="images/img1.png" alt="img1" width="800"/>

---
<h1 align="center">EC2 - Elastic Compute Cloud</h1>

## AWS Budget Setup
Para que o usuário IAM possa fazer alterações no Billings Dashboard deve-se logar no root > acount > e editar “Usuário do IAM e acesso de função às informações de faturamento”.

Esse serviço é responsável por toda a parte de custos da sua conta, com ele poderá criar alertas e alguns limites de gastos que você usa ou usará. Tambem poderá ver onde foi cobrado tal valor.

Na aba “Bills” poderá ver quais serviços eraram custos e em quais regiões ass como todos os detalhes do uso do serviço.
Para definir um Budget va em Budget > Create a Buget > Cost budget. Basta configurar o limite de gasto no mês definindo o valor. Na próxima aba deverá ciar thresholds para disparar algum alerta

## EC2 (Elastic Copute Cloud)

É uma das ofertas mais populares da AWS e é usada em todos os lugares.

EC2 é uma maeira de fazer "ifraestructure as a service". Não é apenas um serviço, ele é composto por muitas outras coisas de alto nível.

- Pode criar VMs o EC2;

- Armazenar dados em virtual drivers(EBS);

- Pode distribuir carga entre maquinas (Elastic Load Balancer - ELB);

- Pode escalar serviços usando um grupo de escalonamento automático (ASG)

## Configuração EC2

- Pode haver Windows, Linux e Mac;

- CPU, Memória RAM, Storage Space(EBS e EFS ou EC2 storage);

- Qual network deseja, Placa de rede, IP público;

- Regras de Firewall (security group);

- Boosttrap Script (EC2 User Data)

**Bootstrap (EC2 Data User)**

Bootstrapping significa os comando laçados quando a VM estiver iniciando. Esse comandos rodarão apenas uma vez quando essa maquina for criada, e nunca mais será rodado. Com o EC2 Data User script você pode: instalar softwares, instalar updates, baixar arquivos da internet para que a sua instância d VM seja inicializada e já configurada como deseja. Quanto mais Scripts colocar, mais demorado será para criar sua instância. TODOS os EC2 data user são rodados como Root.

## EC2 hands on

EC2 > instances > launch an Instance

Sempre usar a **t2.micro**

Key pair to login – é necessário se utilizar ua conexão SSH para acessar a instancia. Para gerar ua SSH Key pela AWS basta ir em **Create new key pair** nomear a chave,deixar como RSA. Para Mac, Linux ou widows 10 deixe como .pem. Se tiver Windows com versões infoeriores, use o .ppk.

Em Network Settings não precisa mudar nada. Terá um ip publico.

Em Storage (volumes) sempre é importante deixar habilitado a opção em advanced > Delete on termination > Yes. Para deletar a memoria quando a VM for termiada

Em Advanced details no ultimo box de texto você poderá escrever seu EC2 Data User, para executar loco que a maquia for criada. Um exemplo que será utilizado é a inicialização de um website simples.

``` AWS User Data
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemtl enabel httpd
echo "<h1>Hello Word from $(hostname -f)</h1>" > /var/www/html/index.html
```

Para interromper uma instância – Actions > Instance States > Stop

Para startar uma instância – Actions > Instance States > Start

Para Terminar uma instância – Actions > Instance States > Terminate

Quando dar um Stop em uma instância, o ip Publico pode alterar. Certifique-se sempre disto.

Nunca mudará o Private IP!

## EC2 Instance Types Basics

Existem diferentes tipos de EC2 para usar com diferentes casos, e com diferentes tipos de optimização. Para isso será dividido em 7 tipos de propósitos.

**General Purpose** - Bom para diversidade de cargas de trabalhos como servidores web, ou repositório de código. Tem uma equilíbrio entre compute, memória e Rede.

**Compute Optimized** – Ótimos para optimizar tarefas de computação intensiva. Bom para quando precisa de um CPU de alto nível. Uso para processos em lote, Transcode, Alta performance em web services, Alta performance em computação (HPC). Processamento de modelo de Machine learnig, ou server dedicado a jogos.

**Memory Optimized** – Terão um desempenho maior para o tipo de cargas de trabalho que processarão grandes conjuntos de dados na memória. Alta performance em Banco de dados, cache de web, memoria optimizada para BI e aplicativos que executam processamento em tempo real.

**Storage Optimized** – Ótimos quando necessita acessar um conjunto de dados o local storage.

Terão alta processamento transacional online de alta frequencia (OLTP), Banco de dados. Cache para banco de dados(ex: redis). Sistema de arquivos distribuídos

Os demais exemplos de Accelerated Computing, Instance Features e Measuring Instance Performance, bastam verificar em [https://aws.amazon.com/ec2/instance-types/?nc1=h\_ls](https://aws.amazon.com/ec2/instance-types/?nc1=h_ls)

## Security Groups &amp; Classic Ports Overview

Security Groups são fundamentais para a segurança de network da AWS. Eles controlam como o trafego entra e sair da EC2. Contém apenas  regras de entrada e saída, então é fácil de configurar. Podem ter configurações tanto por IP adress ou por outros security groups.

Security Groups são um “Firewall” para as instancias, irão regular o acesso as portas, autorizarão range de ips, controla a rede de entrada e saída da instancia.

<img src="images/img2.png" alt="img2" width="800"/>
 
 ### Importante:
- Security Groups pode ser relacionadas a varias instancias EC2, elas n tem uma relação direta;
- Security Groups são bloqueados para uma combinação de Region/VPC, caso mude de conta, terá que configurar uma nova Security Group;
- o Security Groups é uma configuração fora da instancia EC2, sendo uma espécie de firewall;
- É sempre bom manter separado os Security Groups apenas para SSH Access;
- Se tiver problema de time out, isso pode ser um problema de Security Groups;
- Se receber um erro de  “connection reused”, quer dizer que a segurança realmente fusionou;
- Por padrão, todo o trafego de entrada é bloqueado e todo o trafego de saída é autorizado;

<img src="images/img3.png" alt="img3" width="800"/>
 
### Para o Exame: Quais portas precisa saber.
- 22 = SSH (Secure Shell) – login em instancia Linux
- 21 = FTP (File Transer Protocol)
- 22 = SFTP (Secure File Transfer Protocol) – Upload de arquivos usando SSH
- 80 = HTTP – Acesso inseguro de sites
- 443 = HTTPS – Acesso seguro de sites
- 3389 = RDP (Remote Desktop Protocol) – Login em instancia Windows

## Security Groups Hands On
Para acessar a tela de Security Groups va em EC2 > Network e Security > Security Groups.
Sempre que tentar fazer qualquer tipo de conexão com a instância e der erro de time out, é 99% de chances de ser algo relacionada a security group. 
Para isso deve ser verificado as regras de Security Groups.

## SSH Overview
Para conexões em Linux server podemos nos conectar através da conexão SSH.
Com EC2 instance connect podemos nos conectar de qualquer browser porem so funciona em Amazon NX2
 
<img src="images/img4.png" alt="img4" width="800"/>

## Acessar instancia através do win 10
Devemos baixar o arquivo .pem (esse arquivo é baixado automaticamente quando é cria uma Key pairs. 

Caso não tenha, vá em EC2 > Network e Security > Keys Pairs e crie uma nova. Provavelmente deverá atribui-la a instancia que você está tentando conectar.

Para conectar deve-se estar na mesma pasta do arquivo .pem.

Devemos ter certeza que no Security Groups temos a porta 22 liberada.

Com o seguinte comando, deve ser conectado a instancia: 
``` CLI
ssh -i '.\ec2_tutorial.pem' ec2-user@<public_ip>
```

Caso tenha problemas para conexão, deve-se verificar se o arquivo esta no C:/user/patrick, e verificar as permissões do arquivo.

Caso não funcione de jeito nenhum, utilize a EC2 Instance Connect. Para isso vá em EC2 > instances > your_instance > Connect.

## EC2 Instance Roles Demo
Jamais utilize o aws configure dentro da instancia e configure com a IAM key.
Para que a instancia tenha acessos, é necessário criar IAM Rules. Para gerar essa Rule va em IAM > Roles > Create Roles. Coloque para AWS Service e Use case EC2. A permission será IAMReadOnlyAccess.
Agora é necessário atribuir a Rule para a instancia EC2. Vá em EC2 > your_instance > Actions > Istance Setings > Attach/Replace IAM Role, e selecione sua Rule.
Com isso você terá acesso a fazer os comando aws sem que precise utilizar o “aws configure”.
 
## EC2 Instance Purchasing Options
On-Demans Instances: 
- Irá pagar pelo que usar por segundo nos sistema Linux e Windows. Em outros sistemas pagará  por hora;
- Tem custo alto porem sem pagamentos antecipados e compromisso a longo prazo;
- É recomendado para uma carga de trabalho curta  e ininterrupta

### EC2 Reserved Instance:
- As instacias reservadas 72% de desconto em comparação com a On-Demand;
- Voce reserva atributos de instância especifico(Instance Type, region, Tenancy, OS);
- especifica um período de desconto de 1 a 3 anos, quando mais, maior o desconto;
- escolha entre pagar adiantado, pagar parcialmente, não pagar adiantado;
- Reserva de uma região ou zona q desejar de A à Z;
- Uso para casos de uso estável, como um banco de dados;
- Pode comprar ou vender suas instancias;
- Existe um tipo  específico de instância reservada chamada de Convertibla Reserved Instance que ganah 66% de desconto;

### EC2 Savings Plans
- Permite ter um desconto com base no use de longo prazo com 72% de desconto;
- Define quanto gastar por hora nos próximos 1 a 3 anos.
- Será cobrado pelo preço On-Deman;
- fica preso a família e region de instancias especificas. Por exemplo M5 em us-east-1, porem pode ter todos os type da instancia, pode alterar entre wind ou Linux, e pode alterar a tenancy.

### EC2 Spot Instance
- Tem descontos mais agressivo de ate 90% em comparação a On-Deman;
- são instancia que você pode perder a qualquer momentos porque você define um preço máximo que está disposto a pagar. E se o preço passar, você perde a instancia EC2 Spot;
- São instancias mais economicacs na AWS;
- Usadas para cargas de trabalho resilientes a falha;
- Não são adequadas para aplicações criticas ou banco de dados;

### EC2 Dedicated Hosts
- Disponibiliza um servidor físico;
- Pode escolher as instancias dentro host dedicado como On-Deman ou Reserved;
- É a opção mais cara da AWS pois você reserva um servidor físico;
- Ótimos para casos que você tem um software que tenha um licenciamento;

### EC2 Dedicated Instances
- São executadas em hardware dedicado a você; 
- Pode compartilhar o hardware com outras instancias na mesa conta;
- NÃO tem o controle sobre posicionamento das instancias;

### Diferença entre Dedicated Host and Instances

<img src="images/img5.png" alt="img5" width="350"/>


### EC2 Capacity Reservation
- Pode reservar instancias On-Deman em uma AZ especifica por qualquer duração;
- Poderá ter acesso a essa EC2 quando precisar;
- Pode reservar ou cancelar a qualquer momento; 
- Pode combinar com Reserved instances ou Savings Plans para ganhar descontos; 
- É cobrado de acondo com a ideia da On-Deman porem mesmo que não esteja executando algo, você será cobrado sobre ela (???);
- É adequado para cargas de trabalho curto com prazo de termino.

### Preços Exemplar de m4.large – us-east-1 
  
<img src="images/img6.png" alt="img6" width="800"/>

## Shared Responsibility Model for EC2
A AWS é responsável por todos os data centers, sua infraestrutura e segurança deles. Tambem é responsável pelo isomaneto no host físico se estiver um host dedicado como vimos acima, e subistituindo hardwares com defeitos.

O usuário é responsável pela segurança para acessar os serviços da nuvem. Definindo Scurity Roules, para definir quem pode acessar as instancias EC2. Possui todos os OS dentro de sua instancia EC2. Todos os softwares  e utilitários instalados é responsabilidade do usuário. Criar IAM Roles para garantir quais usuário terão acesso as instancias EC2. E também  o usuário deve garantir que sus dados estejam seguros na instancia EC2.

## EC2 Sumary
<img src="images/img7.png" alt="img7" width="600"/>

---
<h1 align="center">EC2 instance Storge</h1>

- EBS significa Elastic Block Storage. È uma uniadede de rede que você pode anexar as suas instancias quando são executadas.
- EBS nos permite persistir dados mesmo depois que a instância é encerrada. Podemos recriar uma intancia e monta-la no mesmo volume EBS.
- Quando você cria um EBS volume, ele é vinculado a uma Availability zone especifica.
- Podem pensar que a EBS volume é como se fosse um UBS de Rede. Onde você pode pegar de uma instancia e coloca-la em outra.

## EBS Volume
 - São drivers de rede que não são uma unidade física; Para se comunicar entre a instancia e EBS volume utilizará a rede, podendo conter um pouco de latência na transferência de dados
- EBS por estar na rede, pode ser anexada a um instancia EC2 rapidamente;
- EBS volumes são bloqueados para Availability Zone especificas, então, não podem ser anexadas em outra zonas;
- Se fizer uma snapshot poderemos mover um volume para outras zonas;
- Precisa provisionar a capacidade com antecedência. Será cobrado por todo o provisionamento da capacidade que escolher, e poderá aumenta a capacidade ao longo do  tempo se quiser
Para ver os EBS Volumes basta ir em EC2 > Volumes.


## EBS Snapshot
Serve para criar um backup(snapshot) de seu volume em qualquer momento que desejar. A ideia é fazer backup do estado do volume mesmo que ele esteja encerrado. 

Para fazer um backup, não é necessário desanexar o volume, porem é recomendado certificar-se que tudo esta certo com o volume EBS.

O motivo de fazer snapshots é para poder restaura-los em alguma situação, ou também copiar para outra zonas ou regiões, com a ideia de transferir alguns de seus dados para um região.

### Recursos EC2 Snapshot
- EBS Snapshot Archive: Permite que você mova seus snapshots para outra camada de armazenamentom chamado de “Camada de Armazenamento”. 75% mais Barato. Mas se tiver no Archive, leva de 24 a 72 horas para restaurar do arquivo.
- Recycle Bin for EBS Snapshots: Por padrão, se deletar uma Snapshot eles desaparecem. Mas com essa função você pode configurar uma lixeira onde terá todos as snapshots excluídos. E com ela, pode configurar o tempo que as snapshot serão excluídas.

### Hands On EC2 Snapshot
- Para criar uma SnapShot de um volume vá em EC2 > Volume > your_volume > Actions > Create Snapshot.
- Para visualizar suas SnapShots vá em EC2 > SnapShot.
- Para copiar a Snapshot para um outra Region vá em EC2 >  SnapShot > your_snapshot > Actions > Copy.
- Para criar um volume apartir de uma Snapshot vá em EC2 >  SnapShot > your_snapshot > Actions > Create Volume.
- Para criar uma  Recycle Bin vá em EC2 >  SnapShot > Recycle Bin > Create Retention Rule.


## AMI Overview
Significa Amazon Machine Image, e representam uma personificação de uma Instancia EC2. Voce pode criar AMI através de instancia que já criou , ou personificar as suas próprias.
- AMI configura o SO qualquer ferramenta de monitoramento, e tempo de inicialização de instância mais rápido, visto que já tem tudo configurado em seu AMI.
- AMI podem ser construídos para uma região e em seguida, copiados em toda a região que quisermos usar depois. 
- Pode iniciar instancias EC2 de diferentes tipos de AMIs. Sendo elas Public AMI, criar a sua AMI ou em AWS marketplace AMI.
Como funciona AMI 
Primeir deve-se iniciar uma instancia EC2 e personaliza-la. Depois daremos um Stop na mesma, para garantir a integridade dos dados. E apartir da instancia construir uma AMI onde também criará EBS Snapshot por baixo dos panos. E finalmente poderá iniciar instnacias  apartir de outra AMIs

**Como funciona AMI**

Primeir deve-se iniciar uma instancia EC2 e personaliza-la. Depois daremos um Stop na mesma, para garantir a integridade dos dados. E a partir da instancia construir uma AMI onde também criará EBS Snapshot por baixo dos panos. E finalmente poderá iniciar instâncias a partir de outra AMIs.

## AMI Hands On

Para criar uma imagem de uma instancia que desejar vá em EC2 > Instances > Right click > Image > Create Image.

Para criar uma Instâcia a partir de uma AMI pode ir em EC2 > AMI > Build. Ou em EC2 > Instance > Launch Image > (escolher sua AMI na hora de configurar)

## EC2 Image Builder Overview

- É usado para automatizar a criação de VMs ou Containers Images.

- Através do EC2 Images Builder poderá automatizar a criação, manter e testar AMIs para instancias EC2.

- EC2 Images Builder pode ser executado em uma programação (semanal, sempre que os pacotes foram atualizados, etc...)

- É um serviço gratuito(porem se o serviço criar instancias, e outras coisas, você será cobrado pela EC2 instance normalmente)

**Funcionamento:**

<img src="images/img8.png" alt="img8" width="800"/>


## EC2 Image Builder Hands On

Essa parte é um pouco complexa, mas nada que fazer com calma e se atentar as coisas que estão escritas possa dar errado.

Na aba de pesquisa, vá em **EC2 Image builder** > Create Image Pipeline. Escreva um "Pipeline name" e marque a opção, **Build schedule** com "Manual" e Next.

**Em Choose recipe:**

Uma receita de imagem é um documento que define os componentes a serem aplicados às imagens de base para criar a configuração desejada para a imagem de saída. Após a criação de uma receita, ela não pode ser modificada. Uma nova versão deve ser criada para alterar os componentes.

Selecione **Create New Recipe**. A Image Type deixe como AMI, escolha um Nome e Versão para a Recipe. Em **Base image Não mexer em nada.** Em **Image Name** escolha a "Amazon Linux 2 x86". Posteriormente entenderão o porquê dessa escolha.

Em **Components** vamos selecionar os "amazon-corretto-11-headless", "aws-cli-version-2-linux".

A parte de **Test components - Amazon Linux** pode pular. Após isso podemos ir para próxima página (Next).

Na página de **Define infrastructure configuration** devemos ccriar um IAM Rule caso n tenha, chamada de **EC2InstanceProfileForImageBuilder.** É uma rule para EC2 e é composta pelas seguintes permissões: EC2InstanceProfileForImageBuilder, EC2InstanceProfileForImageBuilderECRContainerBuilds e AmazonSSMManagedInstanceCore

Após criar a Rule caso não tenha, selecione a opção **Create a new infrastructure configuration.**

De um nome a ela, e em IAM Rule selecione a rule citada anteriormente. Em Instance type vamos selecionar a VM **T2.micro x86_64** visto que no tipo da imagem escolhemos anteriormente a "Amazon Linux 2 x86". Logo após, clique em Next.

Em **Define distribution settings** podem ser configurada as regions que a pipeline será testada, porem nessa Demo Free devemos deixar em **Create distribution settings using service defaults.**

**Após isso poderá criar a pipeline e esperar os estágios. Demora em media de 30 min para finalizar todos os estágios.**

## EC2 instance storage
É o disco rígido(HD) conectado ao servidor físico.
- Com ele há um melhor desempenho de I/O;
- É bom se tiver algum Buffer,cache, dados temporários, nada para armazenamento a longo prazo;
- O ruim é se Parar uma Instancia EC2 que tenha um armazenamento Instance storagem, será perdido e excluído tudo  que há nela. Por isso é chamado de “Armazenamento Efêmeo”;
- Caso a instancia EC2 falhe, corre grandes riscos de perder os dados, pois o hardware conectado a instancia EC2 também falhará;
- se utilizar esse tipo de armazenamento, é responsabilidade do usuário cuidar das rotinas de backup para que n se perca nenhum dado.


## EFS – Elastic File System
É um sistema de arquivos de rede ou NFS. E a ideia e os benefícios disso é que ele pode ser montado em centenas de instâncias do EC2 por vez, se tornando uma rede de arquivos compartilhados.
- o EFS funciona apenas com instancias **Linux EC2** e funciona multi-AZ. Ou seja, uma instancia em certa região  q esteja anexado em um volume EFS pode usar o mesmo volume para outras instancias em outra regiões;
- EFS é Altamente disponível, escalável e bastante caro. Chegando a ser cerca de 3x o valor de uma EBS;

<img src="images/img9.png" alt="img9" width="800"/>

### EFS-IA (Elastic File System Infrequent Access)
É uma classe da EFS que será optimizada em termo de custo, ou seja, mais barata para arquivos que você não terá acesso com muita frequência;
-essa opção dará até 92% de desconto para armazenar os dados em comparação a outra classe (EFS normal);
- Se habilitar o EFS-IA, o EFS movera automaticamente os arquivos para uma EFS-IS com base nas ultimas vezes que foram acessados e em algo chamado “life circle policy”;
- definindo uma life circle policy, poderá criar regras para arquivos que não foram acessados/modificados em X tempo, e mover para uma classe diferente de armazenamento EFS-IA, que terá uma economia de custos. Tudo isso é feito automaticamente.

## Shared Responsibility Model for EC2 Storage
A **AWS** é responsável por provisionar a infraestrutura para armazenar seus dados. Replicar os dados dos EBS Volumes e EFS driver caso haja alguma falha no hardware por parte da AWS, e seu cliente não seja impactado. AWS é responsável pela troca de hardware defeituosos. A AWS é responsável por garantir que funcionários AWS não acessem seus dados.

O **Cliente** é responsável por criar rotinas de Backup, snapshots para que não perca seus dados. Configurar uma camada de criptografia para que pessoas não possam ter acesso aos seus dados. Qualquer coisa que for gravada nos storages é de responsabilidade do Cliente. Se o Cliente estiver usando EC2 instance Store, deve saber os riscos de armazenar dados nesse serviço, que pode perder os dados caso houver alguma falha na instancia ou um hardware estar defeituoso.

<img src="images/img10.png" alt="img10" width="800"/>

## Amazon FSx
É um serviço gerenciado para ativar a high-performace file system na AWS para terceiros.
Há 3 ofertas de FSx: FSx for Lustre, FSx for Windows File Server e FSx for NetApp ONTAP.
### FSx for Windows File Server: É um sistema de arquivos compartilhado nativo do Windows totalmente gerenciado.
- Construido no Windows server;
- Suporte para todos os protocolos nativos do Windows como o SMB e Windws NTFS;
- Intgrado com Microsoft Active Directory;

### FSx for Lustre: 
- Significa ter um armazenamento de arquivos totalmente gerenciado de alto desempenho e escalável para High Performaece Computing (HPC);
- Nome Lustre deriva de Linux e Cluster;
- Permite para casos de HPC como análise de dados, Machine learnig, Processamento de Vídeo, modelagem financeira etc... 
- Trafego extremamente alto em termos de centenas de milhões de GB/s IOp/s com latência de sub-ms.

EC2 Instance Storage Summary
<img src="images/img11.png" alt="img11" width="800"/>



---
<h1 align="center">ELB & ASG - Elastic Load Balancing e Auto Scaling</h1>
**Scalability:** é a capacidade de um sistema de acomodar uma carga maior, tornando o hardware mais forte(scaling UP) ou adicionando mais Nós(scaling  OUT).

**Elasticity:** é algo mais nativo da nuvem. Ocorre quando um sistema é realmente escalonável, que você pode aumenta-lo ou amplicalo. Significa que haverá algum tipo de escalonamento automático nele, para que o sistema possa escalar com base na carga que está recebendo. **Para esses casos, paga por uso, para atender a demanda  e optimizar os custos.**

**Agility:** Não esta relacionada a nenhuma dos itens acima. Sgnifica que os novos recursos de TI estão a apenas um clique de distancia, podendo reduzir o tempo de disponibilização desses recursos para seus desenvolvedores de semanas para alguns minutos.

## Scalability e High Availability 
- Aplicativos podem ser escalonados, isso quer dizer que eles podem lidar com cargas maiores por meio da adaptação. 
- Existem dois tipos de Scalability na nuvem:
	- Vertical Scalability
	- Horizon Scalability (= Elasticity)
- Escalabilidade será vinculada , mas diferende da alta disponibilidade

## Vertical Scalability
- Pode aumenta o tamanho da instancia. Por exemplo se uma aplicação está rodando em um t2.micro, e fazer um vertical scalability, a instancia agora mudara para uma t2.large.
- é muito comum fazer escalabilidade vertical quando se tem um sistema não distribuído, como um, banco de dados. Para que se possa dar mais performace ao DB.
- Tem um limite que se pode fazer escalabilidade vertical, que é o hardware. Mesmo q esses limites sejam muito altos, ainda assim tem um limite.

## Horizon Scalability
- Aumenta o numero de instancias ou sistemas para a aplicação.
- Para esse tipo de escalabilidade, é necessário que seja um sistema distribuído(aplicações intependentes como MS).
- É fácil de escalar graças ao Amazon EC2 e aos grupos de escalonamento automático e load balancer.

## High Availability
- Esse serviço fica de mãos dadas com o  Horizontal Scaling.
- Siguinifica que você está executando um aplicativo em pelo menos duas zonas de disponibilidade da AWS.
- O objetivo é a combater a perda de um serviço um uma AZ, e ser direcionada para a outra AZ que está disponível ainda.

## Elastic Load Balancing (ELB)
Um Balanceador de carga é um servidor que encaminhará o trafego da internet para vários servidores (EC2 Instances) downstreams, que também são chamadas de instancias EC2 backend.

ELB é algo Gerenciado pela AWS. O que será publicado será o Load Balancer e por trás desse serviço terá múltipla instancias EC2. 

- ELB serve obviamente para balancear as carcas de requisições por varias instancias downsrtream.
- Pode expor um único ponto de acesso (DNS host) para seu aplicativo.
- pode lidar perfeitamente com falhas de instancias de recebimento de dados.
- Poderá faze regularmente exames de saúde nas instancias sem que tenha indisponibilidade de serviço
- Fornece terminação SSL (HTTP) para os sites com muita facilidade.
- Pode usar um ELB em varias AZ, o torna seu aplicativo altamente disponível.

### Porque usar Elastic Load Balancer? 
- ELB é um gerenciador de balanceador de carga
	- AWS garante que estará funcionando
	- AWS cuidará dps updates, manutenções e alta disponibilidade
	- AWS fornece apelas configurações fáceis.
- É menos trabalhoso user o serviço da AWS, do que criar seu próprio Load Balancer, pois terá que cuidar de toda a manutenção dele
- Há 3 tipos de Load Balancer  na AWS
	- Aplication Load Balancer (HTTP / HTTPS ) – Layer 7
	-  Network Load Balancer (ultra-high performace for TCP) – Layer 4 
	- Classic Load Balancer – Laayer 4 e 7

## ELB Hands On
Crie duas instancias EC2 com o apache rodando um o site demo.
Em EC2 > Load Balancing > Load Balancer > Create Load Balancer > ALB 

## Auto Scaling Groups (ASG)
O Objetivo de um grupo de escalonamento automático é escalar horizontalmente suas instancias rapidamente, e também remover instancias de acordo com a necessidade. Isso garantirá a quantidade exatas de Intacias EC2 rodando para que n haja custos desnecessários. Se alguma instancia tiver algum problema, o ASG consegue identifica-lo e repor a instancia com uma nova.

Outro dos benefícios é Cost Savings(Economia de custos) pois será sempre rodado as instancias necessárias para a necessidade da aplicação

## Auto Scaling Groups (ASG) Hands On
Vá em EC2 > Auto Scaling > Auto Scaling Groups > Create Auto Scalig

## Auto Scaling Groups (ASG) Strategies
- Escalonamento manual: Atualizar o tamanho do ASG manualmente.
- Escalonamento Dinamico: Responde as demandas em constante mudança.
- Simple / Step Scaling: Define trasholds para criar ou deletar istancias
- Target Trackig Scaling : Define uma media que as instâncias devem ser mantidas
- Escalonamento Programado: agenda as mudanças do dimensionamento das instâncias
- Escalonamento Preditivo: Utiliza Machie Learnnig para predizer o trafego futuro que terá.
- Provisionará automaticamente o número certo de instancias EC2 com antecedência para corresponder a predição calculada. 
- É recomendado quando se tem padrões


---
<h1 align="center">Amazon S3</h1>

- S3 está no centro de muitos outros bloco s de construção da AWS;
- É chamada de “Armazenamento de escala infinita”. Onde pode armazenar quantos objetos quiser;
- S3 será usado como um backbone para muitos sites e muitos serviços da AWS usarão S3 como uma integração;

## Usos de S3 
- Backup e Armazeamento;
- Recuperação de desastres;
- Arquivar dados no S3;
- Ter uma armazeameto em nuvem hibrida;
- Hospedagem de Aplicativos;
- Hospeadagem de mídia;
- Datalakes e Big data analytics;
- Software delivery;
- Site estatico

## Amazon S3 – Buckets
- Amazo S3 deixa pessoas armazenar arquivos(objects) em “Buckets”(diretórios);
- Os buckets devem ter um nome exclusivo globalmente. Significado que esta em todas as regiões e todas as cotas na AWS;
- Buckets são definidas no nível da região;
- 	**O S3 parece ser um serviço global, mas os bucktes são criados em uma Região.**
- Nome de convenção:
	- Não pode ter letras maiúsculas;
	- sem sublinhado;
	- deve ter entre 3 – 63 caracteres;
- Não deve ser um IP;
- Não deve começar com letra minúscula ou úmero; 



## Amazon S3 – Objects
Pode armazenar Objects que contém um **Key**
<img src="images/img12.png" alt="img12" width="800"/>

- O tamanho máximo de um Objects é de 5TB;
- para objetos maiores que 5GB terá q dividir e enviar em partes, usado o “multi-part upload”;
- Acima do conteúdo do Body a os Metadados, que são um conjunto de key/value;
- Pode ter Tags. Unicode key/value quando se tem segurança ou lifecircle;
- ID ad versão;

## Amazon S3 Hands On
Em Storage > S3 > Create a Buckets

Não pode usar nomes que já existam em outros clientes da amazon.
Após fazer um upload de um arquivo, pode-se notar que no botão “Open”, conseguirá abrir o seu arquivo, porem quanto tentar usar o Object URL não irá abrir. Isto porque o bucket não público. Para conseguir isso terá que adicionar polycies ao seu bucket.


## S3 Security
Há diferentes componentes de segurança no S3.
- **Por usuário:**
	- É anexado IAM policies,para permitir que tenham acesso ao buckets S3
- **Resouce Based:**
	- podemos definir um buckets policies, que será uma regra anexada diretamente no bucket S3, para permitir ou negar as solicitações publicas ou de outras contas.
	- Object Access Control List (ACL), podem definir o nivel do objeto, quem pode fazer algo
	- Bucket Access Controll List (ACL), menos comum.

Pode-se acessar um object s3 quando as permissões IAM anexadas ao IAM principal de forma que o usuário OU grupo da função possa permitir o acesso ao Bucket S3, ou se a politica de Bucket S3 Permitir OU se não nenhuma política  e negação de acesso. 
 
**Exemplos de Acesso:**
<img src="images/img13.png" alt="img13" width="800"/>
<img src="images/img14.png" alt="img14" width="800"/>
<img src="images/img15.png" alt="img15" width="800"/>
<img src="images/img16.png" alt="img16" width="800"/>

## S3 Website Overview
Uma das razões pelas quais tornamos os Objects Públicos  é para poder hospedar sites no Amazon S3. Sendo uma ótima maneira de hospeda-los em disponibiliza-los em rede mundial.
As URL dos sites serão:
- \<bucket-name\>.s3-website-\<aws-region\>.amazonaws.com OU
- \<bucket-name\>.s3-website.\<aws-region\>.amazonaws.com

Se não tornar o buckets público, os usuários receberão um erro 403 (forbidden), tendo certeza q é relacionada a permissão do bucket.

**OBS: os sites no S3 serão somente para sites estáticos.**

Para criar um website va em Amazon S3 > Buckets > <piccini-s3-2022-v1>  > Properties > Static website hosting > e anexe eu index.html.

Lembre-se que antes de tudo, o bucket deve estar público, fazendo os passos de Bucket policy

## Amazon S3 – Versioning
Supondo que criamos um site e queremos atualizar ou adicionar novos arquivos a ele, seria bom marte versões anteriores como um backup para possíveis roll back.

Para isso, pode-se habilitar o controle de versões para seus arquivos no S3.
- Toda a vez que atualizar um arquivo, ele terá uma nova versão;
- É uma boa pratica criar versões de seus buckets;
	- Protege contra qualquer exclusão indesejada;
	- pode reverter para uma versão anterior;
- Qualquer arquivo que não tiver versão, será atribuído o valor “null” a ele.
Hands On
Vá em seu bucket S3 > Properties > Bucket Versioning > Habilitar.

## S3 Access Loggin
- É usado caso você precise utilizar ou analizar os logs do seu S3 Bucket;
- Terá acesso a todas as requisições feitas para o S3.
- Tambem é utilizado para analisar quem pode ter excluído algum arquivo, em que momento e como.

**Hands On**

Primeiramente terá que criar um novo S3 para que possa armazenar os logs no S3 principal.
Depois vá no S3 principal > Propreties > Server access logging > habilita > e coloque o s3 de log /logs.

## S3 Replication (CRR & SRR)
Esta função replica seus buckets. Pode ser uma réplica entre regiões (Cross Replication Terio - CRR) ou replica na mesma região (Same Replication Region).

Para isso:
- Controle de versão no bucket de origem e destino deve estar habilitado;
- e habilitar o CRR ou SRR;
- podem estar em contas diferentes;
- a copia é assyncrona;
- para funcionar deve-se dar permissão de IAM adequadas para copiar os arquivos

Casos de uso CRR – Acesso de menor latência, Replicação entre cotas diferentes...
Casos de uso SRR – Agregar loggs, replicação ao vivo entre PRD e TEST Acounts

**Hands On**

Crie um novo bucket e habilite o sistema de versionamento. No bucket principal va em Maagement > Replication rules > Create replication rulem, e configuro como desejar a replica.

## S3 Storage Classes
Quando é criado um object S3, você pode escolher manualmente sua classe, também pode modificar sua classe de armazenamento manualmente ou pode usar configurações de ciclo para mover objects automaticamente entre todos esses 
## Storage Classes
S3 Durability and Availability:
- Durability:
	- Há uma durabilidade Muito Alta (99.999999999%).
	- Se tiver 10milhoes de objects no S3, pode considerar perde um em 10mil anos;
	- Isso para todas as classe S3
- Availability:
	- Representa rapidez com que um serviço é.
	- Isso depende da classe de storage;
	- Ex: S3 Standard tem 99.99% de disponibilidade

**S3 Standard – General Purpose**

- 99.99% de disponibilidade;
- Usado para Dados acessados frequentemente
- Tem baixa latência e alta taxa de transferência
- Pode sustentar 2 falha de instalação simultâneas

**S3 Storage Classes – Infrequent Access**
- Usado para dados não acessados com frequência porem com acesso rápido quando necessário;
- Custo será menor do o que S3 Standard

	**Amazon S3 Standard-Infrequent Access (S3 Standard-IA)**
	- tem um pouco menos de disponibilidade – 99.9%
	- Usado em casos de Disaster Recovery, backups

	**Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA)**
	- High durability (99.999999999%) em uma única zona, e os dados serão perdidos se a AZ for um pouco destruída.
	-  tem um pouco menos de disponibilidade – 99.5%
	- são usadas para armazenar copias secundarias de backups

**Amazon S3 Glacier Storage Classes**
- É um armazenamento de objetos de baixo custo destinado a arquivamento e backup
- Paragá pelo armazenamento + custo de recuperação

	**Amazon S3 Glacier Instant Retrieval**
	- Recuperação de milissegundos, excelente para dados acessados uma vez por trimestre
	- Duração mínima de armazenamento de 90 dias

	**Amazon S3 Glacier Flexible Retrieval (formerly Amazon S3 Glacier):**
	- Rápido (1 a 5 minutos), Padrão (3 a 5 horas), Granel (5 a 12 horas) – grátis
	- Duração mínima de armazenamento de 90 dias

	**Amazon S3 Glacier Deep Archive – for long term storage:**
	- Padrão (12 horas), Granel (48 horas)
	- Duração mínima de armazenamento de 180 dias

**S3 Intelligent-Tiering**
	- Pequeno monitoramento mensal e taxa de classificação automática
- Move objetos automaticamente entre níveis de acesso com base no uso
- Não há cobranças de recuperação no S3 Intelligent-Tiering
- Nível de acesso frequente (automático): nível padrão
- Nível de acesso pouco frequente (automático): objetos não acessados por 30 dias
- Nível de acesso instantâneo de arquivo (automático): objetos não acessados por 90 dias
- Nível de acesso ao arquivo (opcional): configurável de 90 dias a mais de 700 dias
- Camada Deep Archive Access (opcional): config. de 180 dias a mais de 700 dias

<img src="images/img17.png" alt="img17" width="800"/>
<img src="images/img18.png" alt="img18" width="800"/>

**Hands On**

Adicionando um arquivo a se bucket, vá em properties e encontrará todas as storage classes disponíveis. 

Após o upload do arquivo também é possível mover de classe, basta nas propriedades do arquivo.

Para movimentar automaticamente os objetos vá no seu bucket > Management > Create lifecircle rules. Com isso você pode definir todas para mudar de classe.

## S3 Object Lock & Glacier Vault Lock
-  S3 Object Lock
	- A ideia é caso queria adotar o modelo WORM (Write Once Read 
	Many) model
	- Isso faz com que você suba um arquivo e defina um tempo para que ninguém possa modificalo
- Glacier Vault Lock
	- A ideia é caso queria adotar o modelo WORM (Write Once Read 
	Many) model
	- Cria uma politica de bloqueio que impede futuras alterações do arquivo. Depois de configurada, ninguem pode excluir a policie.
	- Garante n ter perda de dados nunca.

## S3 Encryption
- No Encryption:
	- não sofre nenhum tipo de criptografia ao fazer uploads de arquivos ao S3
- Server-Side Encryption:
	- o usuário faz upload ao S3 e o servidor Amazon criptografa o arquivo após recebe-lo
- Client-Side Encryption:
	- o usuário faz o upload de um arquivo já criptografado ao S3 e e não será criptografado pelo servidor. 

## Shared Responsibility Model for S3
A **AWS** será responsável por toda a infraestrutura, incluído todas as coisas especificas ao S3(global security, durability, availability, sustentar perdas de dados). Configuração e analise de vulnerabilidade. E sua própria validação.

O **Usuário** será responsável por configurar o controle de versão do S3, ter a certeza de configurar as buckets policies, configurações de replicação de dados, registro e monitoramento de log, saber se a storage class que está usando é a ideal, saiba como criptografar os dados na S3.

<img src="images/img19.png" alt="img19" width="800"/>

## AWS Snow Family
Dispositivos portáteis altamente seguros para coletar e processar dados na borda, e migrar dados para dentro e fora da AWS.

<img src="images/img20.png" alt="img20" width="800"/>

O tempo para migrar seus arquivos para a AWS pode levar muito tempo, e as vezes pode dar problemas. Com o AWS Snow Family a aws envia um dispositivo físico para você, onde terá que fazer o upload dos arquivos a ele, e depois você enviará novamente para Amazon para que ela possa fazer a transferência dos arquivos rapidamente.

A regra é que só use esse serviço caso a sua transferência leve mais de uma semana pela rede. Assim poderá usar um dispositivo Snowball

**Snowball Edge (for data transfers)**
- Solução de transporte de dados físicos: mova TBs ou PBs de dados para dentro ou para fora da AWS
- Alternativa para mover dados pela rede (e pagar honorários)
- Pague por trabalho de transferência de dados 
- Forneça armazenamento em bloco e Amazon S3-compatible object storage
- Armazenamento otimizado para Snowball Edge 
	- 80 TB de capacidade de HDD para volume em bloco e objeto compatível com S3 storage
- Snowball Edge Compute otimizado 
	- 42 TB de capacidade de HDD para volume em bloco e objeto compatível com S3 storage
- **Casos de uso:** grandes migrações de nuvem de dados, descomissionamento de DC, desastre recuperação

**AWS Snowcone**
- Computação pequena e portátil, em qualquer lugar, robusta e seguro, resiste a ambientes agressivos
- Leve (4,5 libras, 2,1 kg) 
- Dispositivo usado para computação de borda, armazenamento e dados transferir
- 8 TBs de armazenamento utilizável 
- Use o Snowcone onde o Snowball não se encaixa (espaço-ambiente restrito)
- Deve fornecer sua própria bateria/cabos 
- Pode ser enviado de volta para a AWS offline ou conectá-lo a internet e use o AWS DataSync para enviar dados

**AWS Snowmobile**
- Transferir exabytes de dados (1 EB = 1.000 PB = 1.000.000 TBs)
- Cada Snowmobile tem 100 PB de capacidade (use vários em paralelo)
- Alta segurança: temperatura controlada, GPS, vigilância por vídeo 24 horas por dia, 7 dias por semana
- Melhor que Snowball se você transferir mais de 10 PB

**AWS Snow Family for Data Migrations**
<img src="images/img21.png" alt="img21" width="800"/>

## Snow Family – Edge Computing
Edge Computing é quando fosse processa dados enquanto eles estão sendo criados em um edge location(é um lugar que n tenha internet ou sem conexão a nuvem). E ainda estando nesses locais deseja fazer algum processamento de dados o cliente solicitará um Snowball Edge ou Snowcone.

**Use cases of Edge Computing:**
- Preprocess data
- Machine learning at the edge
- Transcoding media streams

<img src="images/img22.png" alt="img22" width="800"/>

## AWS OpsHub
Para usar a Snow Family devices antigamente utilizava-se o CLI.
Atualmente usa-se o OpsHub que é um software que você instala em seu computador para gerenciar a Snow Family devices.

- Desbloquear e configurar dispositivos únicos ou em cluster
- Transferindo arquivos
- Iniciar e gerenciar instâncias em execução no Snow Dispositivos da família
- Monitore as métricas do dispositivo (capacidade de armazenamento, ativo instâncias no seu dispositivo)
- Inicie serviços compatíveis da AWS em seus dispositivos (ex: instâncias do Amazon EC2, AWS DataSync, Network File System (NFS))

**Hands On**
Vá na aba da AWS Snow Family e crie uma ordem de device escolhendo o dispositivo que desejar. (ISSO PAGA, CUIDADO)

## Storage Gateway Overview
Vimos que o S3 é um serviço autônomo, mas é possível usa-lo em um tipo de configuração de nuvem hibrida.
	- Parter da infraestrutura ficará no local e o resto ficara na nuvem
	Isso pode acontecer em casos de que começou sua infra local e deseja ter em cloud, porem será muito longo o processo de migração, por isso usa o Hybrid Cloud. Ou também é uma estratégia ter a infra separada.

Para expor esses dados que ficam no S3 é necessário usar o AWS Storage Gateway.

A AWS Storage Gateway fará uma ponte entre os seus dados locais e seus dados na nuvem, também utilizado em casos de disaster recovery, backup & restore, tiered storage.

- Tipos ode Storage Gateway:
	- File Gateway 
	- Volume Gateway
	- Tape Gateway

<img src="images/img24.png" alt="img24" width="800"/>

---
<h1 align="center">Databases</h1>

## Databases e Shared Responsability o AWS
A AWS se proponha  a gerencias bancos de dados. 
- O benefício é que é muito rápido para provisionar, terá alta disponibilidade, pode fazer escalonamento vertical e horizontal. 
- Terá backup e restauração automatizado dos bancos de dados, operações e atualizações do banco.
- Corrige a instancia que esta alocado o DB.
- Monitoramento e alertas serão integrados 

RDS & Aurora Overview
RDS significa  Relation Database Service e obviamente é um banco relational que usa SQL como linguagem. Esse serviço provisionar bancos de dado que serão gerenciados pela AWS podendo ser de diferentes tipos:
- Postgrs
- MySQL
- MariaDB
- Oracle
- Microsoft SQL Server
- Aurora (BD proprietário da AWS)

**Vantagens de usar RDS ao invés de criar em uma EC2:**
- RDS é um serviço gerenciado:
- Provisionamento automatizado, patch de SO
- Backups contínuos e restauração para timestamp específico (Point in Time Restore)!
- Painéis de monitoramento
- Réplicas de leitura para melhor desempenho de leitura
- Configuração Multi AZ para DR (Recuperação de Desastres)
- Janelas de manutenção para atualizações
- Capacidade de dimensionamento (vertical e horizontal)
- Armazenamento suportado por EBS (gp2 ou io1)
- MAS você não pode usar SSH em suas instâncias.

<img src="images/img25.png" alt="img25" width="600"/>

## **Aurora**
- Aurora é uma tecnologia proprietária da AWS (não de código aberto)
- PostgreSQL e MySQL são suportados como Aurora DB
- O Aurora é “otimizado para a nuvem da AWS” e reivindica uma melhoria de desempenho de 5x sobre MySQL no RDS, mais de 3x o desempenho do Postgres no RDS
- O armazenamento Aurora cresce automaticamente em incrementos de 10 GB, até 64 TB.
- Aurora custa mais do que RDS (20% a mais) – mas é mais eficiente
- **Não está no nível gratuito**

**Hands On**
Vá em RDS > DataBases > Create Database, e configure seu banco. Lembre-se de verificar para usar o free tier.
Pode ser criado snapshots para restaurar em um novo banco de dados futuramente na aba Actions > Take Snapshot.
Na Snapshot va em Actions > Restore Snapshot e configure um novo banco de dados.

## RDS Deployments: Read Replicas, Multi-AZ
**Read Replicas:**
	- distribui a leitura de informações em seu banco de dados para não sobrecarregar
	-  pode ser criado até 5 Read Replicas
	- Os dados podem ser gravados somente no banco principal

<img src="images/img26.png" alt="img26" width="400"/>

**Multi-AZ:**
- É útil quando se tem um failover no caso de uma AZ travar. Usa-la te trará(high-availability)
- os dados são somente lidos e gravados no banco principal
- Pode ter uma outra AZ como AZ failover

<img src="images/img27.png" alt="img27" width="400"/>

## RDS Deployments: Multi-Region
**Multi-Region (Read Replicas):**
- Usados para casos de Disaster Recovery 
- Cria replicar em regiões diferentes
- tem melhor performace para aplicações globais
- haverá um custo de replicação associado a uma transferência de dados entre regiões

<img src="images/img28.png" alt="img28" width="800"/>

## ElastiCache Overview
- Da mesma forma que o RDS é para obter bancos de dados relacionais gerenciados…
- ElastiCache é obter Redis ou Memcached gerenciado
- Caches são bancos de dados na memória com alto desempenho e baixa latência
- Ajuda a reduzir a carga de bancos de dados para cargas de trabalho de leitura intensa
- A AWS cuida da manutenção / aplicação de patches, otimizações, instalação, configuração, monitoramento, recuperação de falhas e backups

<img src="images/img29.png" alt="img29" width="800"/>

## DynamoDB
- é um serviço de banco de dados sem servidor (sem uma instancia especifica)
- Totalmente gerenciado Altamente disponível com replicação em 3 AZ
- Banco de dados NoSQL - não é um banco de dados relacional
- Escala para cargas de trabalho massivas, banco de dados distribuído "sem servidor"
- Suporta milhões de solicitações por segundo, trilhões de linhas, centenas de TB de armazenamento
- Rápido e consistente em desempenho
- Latência de milissegundos de um dígito - recuperação de baixa latência
- Integrado com IAM para segurança, autorização e administração
- Recursos de baixo custo e dimensionamento automático
- Possui classes Standar e Infrequent Access (IA) para economizar seus dados
- trabalha com dados de Key/Value assim como JSON

## DynamoDB Accelerator - DAX 
- É um cache de memória totalmente gerencia para o DynamoDB
- Melhoria de desempenho de 10x – latência de milissegundos de um dígito para microssegundos latência – ao acessar seu DynamoDB 
- Seguro, altamente escalável e altamente disponível
- Diferença com o ElastiCache no CCP nível: DAX é usado apenas para e é integrado ao DynamoDB, enquanto o ElastiCache pode ser usado para outros bancos de dados

## DynamoDB Global Tables
- É uma maneira de tornar o DynamoDB acessível com baixa latência em múltiplas regiões.
- É criada uma replica do DB em outra region, porem os usuário também pode ler e escrever nessa replica.


## Redshift Overview 
- Redshift é baseado no PostgreSQL, mas não é usado para OLTP
- OLAP é o processamento analítico online (análise e armazenamento de dados)
- Carregar dados uma vez a cada hora, não a cada segundo
- Desempenho 10x melhor do que outros data warehouses, dimensione para PBs de dados
- Armazenamento colunar de dados (em vez de baseado em linha)
- Execução de Consulta Massivamente Paralela (MPP), altamente disponível
- Pague conforme o uso com base nas instâncias provisionadas
- Possui interface SQL para realizar as consultas
- Ferramentas de BI, como AWS Quicksight ou Tableau integram-se a ele

## Amazon EMR
- Signnifica Elastic MapReduce
- não bem um database. Ele ajuda a criar um Hadoop cluster quando deseja fazer big data
- Hadoop é usado para analisar e processar uma grande quantia de dados.
- usado o hadoop, pode ser criado centenas de EC2 instances para analisar seus dados.
- Apache Spark, HBase, Presto, Flink etc estarão funcionando no topo do seu cluster hadoop
- EMR é responsável por criar todas essas instâncias que você precisa 
- possui escalonamento automático e integração com Spot Instances

## Amazon Athena
É um serviço de consulta sem servidor para realizar análises em relação ao seu armazenamento de objects (S3)
- A ideia é usar uma linguagem SQL para consultar esses arquivos, mas não carrega-los.
- Esses arquivos podem ser formatados em CSV, JSON, ORC, Acro e Parquet (Athena tem engine Presto)
- Preço: US$ 5,00 por TB de dados verificados
- Use dados compactados ou colunares para economia de custos (menos varredura)

- Casos de uso: BI / análise / relatórios, análise e consultar logs de fluxo de VPC, logs de ELB, trilhas do CloudTrail, etc...
- Dica de exame: analise dados no S3 usando SQL sem servidor, use Athena

## Amazon Quicksight
É um serviço de BI sem servidor com Machine learning para criar painéis interativos.
- pode criar Dashboards em seus bancos de dados para monitoramento e representar visualmente os dados.
- É rápido, escalonável automaticamente, tem o preço por sessão 
Use cases:
- Business analytics
- Building visualizations
- Perform ad-hoc analysis
- Get business insights using data

Pode ser integrado com RDS, Aurora, Athena, Redshift

## DocumentDB
É o mesmo conceito do Aurora porem no formato de MongoDB.
- É um banco de dados totalmente gerenciado, com alta disponibilidade com replicação em 3 AZ.
- O armazenamento pode aumentar automaticamente 10GB até 64TB
- Pode ser dimensionado para cargas de trabalho com milhões de solicitações por segundo.

## Amazon Neptune
É um banco de dados gráfico totalmente gerenciado, tem alta disponibilidade em até 3 AZ com até 15 réplicas de leitura.
- É usado para rodar application que estarão com conjuntos de dados altamente conectados, como uma rede social. Pois o Neptune é optimizado para executar consultas que são complexas encima desses conjuntos de dados gráficos.
- Podem armazenar Bilhões de Relações no banco de dados e consultar o gráfico com latência de milissegundos.
- É ótimo para armazenar gráficos de conhecimento por ex Wikipedia, Detecção de fraude, mecanismo de recomendação e rede social.

Para o exame, sempre que ver algo relacionado a banco de dados de gráficos pense no Neptue

## Amazon QLDB
QLDB significa ”Quantum Ledger Database”. 
- um ledger é um livro que registra transações financeiras
- É um banco totalmente gerenciado, serverless, com alta disponibilidade e com replicação de ate 3 AZ.

É usado para revisar o histórico de toas as alterações feitas nos dados do seu App ao longo do tempo.

É um sistema imutável significando que uma vez que você grava algo no DB, ele não pode ser removido ou modificado. E também há uma maneira de ter uma assinatura criptográfica para ver que nada foi removiso.

- Desempenho 2-3x melhor do que as estruturas comuns de ledger blockchain, e pode manipular dados usando SQL
- Diferença com Amazon Managed Blockchain: sem componente de descentralização, de acordo com regras de regulação financeira. Isso significa se somente um banco de dados central de propriedade da Amazon que permite que você escreva os diários.


## Amazon Managed Blockchain
Blockchain torna possível construir aplicativos onde várias partes podem executar transações sem a necessidade de uma central confiável autoridade.
O Amazon Managed Blockchain é um serviço gerenciado para:
- Junte-se a redes públicas de blockchain
- Ou crie sua própria rede privada escalável
- Compatível com os frameworks Hyperledger Fabric & Ethereum

## DMS – Database Migration Service
É usado para migrar os dados de um serviço de DB para outro serviço de DB.
- com o DMS há uma migração de banco de dados rapidae segura pela AWS, sendo resiliente e autocorretiva.
- Os dados do DB de origem continuam disponível durante migração.

**Suporta:**
- Migrações homogêneas: ex Oracle para Oracle
-  Migrações heterogêneas: ex Microsoft SQL Server para Aurora

## AWS Glue
É um serviço gerenciado de extração, transformação e carregamento(ELT).
- ETl é muito útil quando se tem alguns conjutos de dados, mas eles não estão exatamente na forma certa ou formato que você precisa. Por isso, você usará o ETL para transformar esse dados.
- GLue é totalmente serverless

<img src="images/img30.png" alt="img30" width="800"/>

---
<h1 align="center">Other compute Service: ECS, Lambda, Batch, Lightsail</h1>

## Elastic Container Service – ECS
É usado para criar containers na AWS
- Para que funcione, precisamos  que os containers sejam executados em uma EC2.
- A AWS se encarrega de iniciar ou parar os containers
- Tem integração com ELB

## Fargate
É usado para criar containers na AWS
- Os containers nesse caso não precisam de uma instancia para rodar pois são serveless offerig
- A AWS apenas executará os containers que você precisa baseado no CPU e RAM que precisar.

## Elastic Container Registry – ECR
É usado para armazenar imagens do Docker para que possam ser executadas na AWS.
- É uma Registry privado na AWS
- Armazena as imagem e podem ser executadas tanto no EDS quando no Forgate

## Serverless
É um paradigma no qual os desenvolvedores não gerenciam mais os servidores.
- Hoje tudo que é serverless é mencionado principalmente como algo que é gerenciado e isso inclui databases,messagin storage, etc.
- Serverless não significa que não haja servidores, eles existem em backend. Mas apenas que como usuário final, fosse não gerencia e provisiona ou vê os servidores

## AWS Lambda
- Apenas há funções virtuais e serverless
- São destinadas a execuções mais curtas
- São executadas sob demanda
- podem ser escalonadas automaticamente

**Benefits of AWS Lambda**
- Paga por request ou tempo de computação. No Free Tier tem 1 milhão de requisições Lambda por  mês, e 400GBs de segundos de tempo de computação.
- É integrado com todo os serviços da AWS
- É Orientado a Eventos. As funções são invocadas quando precisam
- É integrado com varias linguagens de programação
- Tem monitoramento fácil pelo CloudWatch
- É fácil obter mais recursos por funções(chegando a 10GB de RAM)
- pode aumentar a RAM e isso melhorará o CPU e a Network

**AWS Lambda language support**
- Node.js (JavaScript) 
- Python 
- Java (Java 8 compatible) 
- C# (.NET Core) 
- Golang 
- C# / Powershell 
- Ruby 
- Custom Runtime API (community supported, example Rust) 

**Lambda Container Image **
- The container image must implement the Lambda Runtime API 
- ECS / Fargate is preferred for running arbitrary Docker images

<img src="images/img31.png" alt="img31" width="800"/>
<img src="images/img32.png" alt="img32" width="800"/>

**Hands On**
Vá em https://us-east-1.console.aws.amazon.com/lambda/home?region=us-east-1#/begin 
Basta criar uma function que será serverless, e pode definir triggers para disparar essas functions

## Amazon AP Gateway
Usado se deseja construir um Serveless HTTP API. Pode criar uma API gateway para acessar suas funções Lambda externamente

<img src="images/img33.png" alt="img33" width="800"/>

- É usado como um serviço totalmente gerenciado que permitira os desenvolvedores Criar, Publicar,  Manutenir, monitorar e proteger APIs
- É Serverless e Escalonavel
- Suporta RESTfull e WebSockets APIs
- Suporta Segurança, User Authentication, API Throttling, API Keysn Monitoring...

## AWS Batch
- Processamento em lote totalmente gerenciado em qualquer escala
- Execute com eficiência 100.000 trabalhos em lote de computação na AWS
 -Um trabalho "Batch" é um trabalho com início e fim (oposto a contínuo)
- O Lote iniciará dinamicamente instâncias do EC2 ou instâncias spot
- O AWS Batch provisiona a quantidade certa de computação/memória
- Você envia ou agenda trabalhos em lote e o AWS Batch faz o resto!
- Os trabalhos em lote são definidos como imagens do Docker e executados no ECS
- Útil para otimizações de custos e menos foco na infraestrutura

## Diferença entre Batch e Lambda
**Lambda:**
- Limite de tempo
- Tempos de execução limitados 
- Espaço em disco temporário limitado 
- Sem servidor 

**Bacth:**
- Sem limite de tempo 
- Qualquer tempo de execução, desde que seja empacotado como uma imagem do Docker 
- Confie no EBS/armazenamento de instâncias para espaço em disco 
- Depende do EC2 ( pode ser gerenciado pela AWS)

## Amazon Lifthsail
É uma espécie de “serviço autônomo” da AWS. Com ele pode obter  Virtual servers, storage, databases, and networking.
- Todos com preços baixos e previsíveis
- É uma alternativa simples para usar EC2, RDS, ELB, EBS, Route 53…
- É um serviço para pessoas que tem pouca experiencia em cloud
- Pode configurar notificações e monitoramento de seus recursos do Lightsail

**Casos de uso:**
- Aplicações web simples (tem templates para LAMP, Nginx, MEAN, Node.js…)
- Sites (modelos para WordPress, Magento, Plesk, Joomla)
- Ambiente de desenvolvimento/teste
- Tem alta disponibilidade, mas sem dimensionamento automático, integração limitada da AWS

<img src="images/img34.png" alt="img34" width="800"/>

---
<h1 align="center">Deployments & managin Infraestructure at Scale</h1>

## CloudFormation
É uma forma declarativa de delinear sua infraestrutura AWS, para qualquer recurso.

Por exemplo, em um modelo do CloudFormation, você diz:
- Quero um grupo de segurança
- Quero duas instâncias do EC2 usando este grupo de segurança
- Eu quero um bucket S3
- Eu quero um balanceador de carga (ELB) na frente dessas máquinas

Então o CloudFormation cria aqueles para você, na ordem certa, com o configuração exata que você especifica

**Beneficios da AWS CloudFormation**
Infraestrutura como código
- Nenhum recurso é criado manualmente, o que é excelente para controle
- As alterações na infraestrutura são revisadas por meio de código

**Custo**
- Cada recurso na pilha é marcado com um identificador para que você possa ver facilmente como quanto custa uma pilha
- Você pode estimar os custos de seus recursos usando o modelo CloudFormation
- Estratégia de economia: no Dev, você pode automatizar a exclusão de modelos às 17h e recriado às 8h, com segurança

**Produtividade**
- Capacidade de destruir e recriar uma infraestrutura na nuvem em tempo real
- Geração automatizada de Diagramas para seus templates!
- Programação declarativa (sem necessidade de descobrir ordenação e orquestração)

**Não reinvente a roda**
- Aproveite os modelos existentes na web!
- Aproveite a documentação

**Suporta (quase) todos os recursos da AWS:**
- Tudo o que veremos neste curso é compatível
- Você pode usar "recursos personalizados" para recursos que não são compatíveis

**Em resumo para o exame**, o CloudFomation será usado quando tivermos infraestrutura como código, e quando precisamos repetir uma arquitetura em diferentes ambientes, regiões ou até mesmo diferentes contas da AWS.

**Hands On**
Antes de tudo mudo sua AZ para N.Virigia. Vá até o serviço de CloudFormation, e crie um Stack. Pode ter um tamplate em aum Bucket S3 ou carregar seu próprio arquivo .ymal
~~~exemple.ymal
---
Resources:
    MyInstance:
        Type: AWS::EC2::Instance
        Properties:
            AvailabilityZone: us-east-1a
            ImageId: ami-a4c7edb2
            InstanceType: t2.micro
~~~

Pode colocar alguma tag para identificar seus serviços.
Com o CloudFormation pode-se atualizar as coisas que você quer, basta atualizar o arquivo, ou até mesmo excluir tudo

## CDK AWS Cloud Development Kit
É uma maneira de criar sua infraestrutura com um linguaem de programação familiar (JavaScript/TypeScript, Python, Java, and .NET ). Após a escrita do código, ele será compilado para o CloudFormation para o tamplate JSON/YMAL.
- Pode implantar infraestrutura e sua própria aplicação juntas pois podem compartilhar as mesmas linguagens.
	- Otimo para Lambda Functions
	- Otimo para ECS / EKS

<img src="images/img35.png" alt="img35" width="800"/>

## AWS Elastic Beanstalk
**Problemas do desenvolvedor na AWS**
- Gerenciamento de infraestrutura
- Código de implantação
- Configurando todos os bancos de dados, balanceadores de carga, etc.
- Preocupações de dimensionamento
- A maioria dos aplicativos da web tem a mesma arquitetura (ALB + ASG)
- Tudo o que os desenvolvedores querem é que seus códigos sejam executados!
- Possivelmente, de forma consistente em diferentes aplicativos e ambientes

Elastic Beanstalk é uma visão centrada no desenvolvedor da implantação de um aplicativo na AWS.
- Utiliza todos os componentes que foi visto no curso por baixo dos panos(EC2, ASG, ELB, RDS, etc…)
- Se tem o controle de toda a configuração sobre todos os componentes, mas esta tudo dentro do Beanstalk

Beanstalk = Platform as a Service (PaaS) 
- Beanstalk é grátis, **mas pagará pelos serviços que eles estarão usando**

- Serviço gerenciado 
	- Configuração de instância / SO é tratado pelo Beanstalk 
	- A estratégia de implantação é configurável, mas executada pelo Elastic Beanstalk 
	- Provisionamento de capacidade 
	- Balanceamento de carga e dimensionamento automático 
	- Monitoramento de integridade e capacidade de resposta do aplicativo 
- **A responsabilidade como Dev é apenas o código do aplicativo é responsabilidade do desenvolvedor**
- Três modelos de arquitetura: 
	- Implantação de instância única: bom para dev 
	- LB + ASG: ótimo para aplicativos Web de produção ou pré-produção 
	- Somente ASG: ótimo para aplicativos não Web em produção (trabalhadores, etc.)

**Support for many platforms:**
Go, Java SE, Java with Tomcat, .NET on Windows Server with IIS, Node.js, PHP, Python, Ruby, Packer Builder, Single Container Docker, Multi-Container Docker, Preconfigured Docker

**Hands On**

Vá até Elastic Beanstalk, crie sua aplicação, e escolha a linguagem que desejar. Depois é só criar. Esse serviço usara o CloudFormation para criar a infraestrutura, porem você só precisa configurar como deseja, e ele cria sozinho.

## AWS CodeDeploy
É uma maneira de implantarmos os aplicativos automaticamente.
- Funciona com EC2 Instance
- Funciona em servidores Locais
- Funciona em servidore Huibrido

Servidores / Instâncias devem ser provisionados e configurado antecipadamente com o Agente CodeDeploy

## AWS CodeCommit
Antes de dar Push do código da aplicação para o server, você precisa armazenalo em algum lugar.
- É o mesmo propósito do GitHub

**CodeCommit:**
- Serviço de controle de origem que hospeda repositórios baseados em Git
- Facilita a colaboração com outras pessoas no código
- As alterações de código são versionadas automaticamente

**Benefícios:**
- Totalmente gerenciado
- Escalável e altamente disponível
- Privado, protegido, integrado com a AWS

## AWS CodeBuild
Permite que faça build do código na nuvem. O Codigo fonte será compilado, testes serão rodados, e em seguita esses packages estarão porntos para ser implementados.

<img src="images/img36.png" alt="img36" width="800"/>

**Benefícios:**
- Totalmente gerenciado, serverless
- Continuamente escalável e altamente disponível
- Seguro
- Preços de pagamento conforme o uso - pague apenas pelo tempo de construção.

## AWS CodePipeline
É uma maneira de orquestrar as diferentes etapas para que o código seja enviado automaticamente para a produção.
- Code => Build => Test => Provision => Deploy
- Basis for CICD (Continuous Integration & Continuous Delivery)

**Benefícios:**
- Totalmente gerenciado, compatível com CodeCommit, CodeBuild, CodeDeploy, Elastic Beanstalk, CloudFormation, GitHub, serviços de terceiros (GitHub…) e plugins personalizados…
- Entrega rápida e atualizações rápidas

<img src="images/img37.png" alt="img37" width="800"/>

## AWS CodeArtifact
- Os pacotes de software dependem uns dos outros para serem construídos (também chamados de código dependências), e novas são criadas
- Armazenar e recuperar essas dependências é chamado de gerenciamento de artefatos
- Tradicionalmente, você precisa configurar seu próprio sistema de gerenciamento de artefatos
- CodeArtifact é um artefato seguro, escalável e econômico gerenciamento para desenvolvimento de software
- Funciona com ferramentas comuns de gerenciamento de dependência, como Maven, Gradle, npm, fios, barbantes, pip e NuGet
- Desenvolvedores e CodeBuild podem então recuperar dependências diretamente do CodeArtifact

## AWS CodeStar
É uma UI unificada para gerenciar facilmente as atividades de desenvolvimento de software em um só lugar.

Fornece um único lugar para que apresa inicie um projeto, e automaticamente o CodeStar fornecerá uma tela e em back-end criará p CodeCommit, CodePipeline, CodeBuild, CodeDeploy, Elastic Beanstalk, EC2, etc…
Pode editar o código “in the cloud” usando AWS cloud9.

## AWS Cloud9
É uma Cloud IDE para escrever, rodar e debugar seu código, executado no navegador.
- pode ser usado dentro do Chrome, Firefox, Internet Explorer etc...
- pode trabalhar em seus projetos de qualquer lugar que se tenha uma conexão com a internet.
- Permite que haja colaboração de  código em tempo real, podendo programar junto com colegas no mesmo código.

## AWS System Manager(SSM)
Ajuda a gerenciar suas EC2 e sistemas On-Promises em escala.
- É outro sistema hibrido da AWS
- Obtem insights operacionais sobre o estado de sua infraestrutura
- Tem acesso a um conjunto de  mais de 10 produtos

**Importante para o exame**

Sempre que precisar corrigir sua frota de EC2 Instances ou servidores locais, pense em SSM
- Automação de patches para maior conformidade
- Pode executar comando em toda a sua frota de servidores diretamente
- Pode armazenar a configuração primaria com o armazenamento de parâmetros SSM

**Como funciona:**
- Funciona para Windows e Linux
- Tem que instalar o Agent em seu sistema operacional
- nas imagens Amazon Linux AMI ou ubundu AMI eles já vêm instalados
- Se uma instancia não poder controlar com SSM, provavelmente é um problema com o SSM Agent
- Graças ao agente SSM, nós pode executar comandos, patch e configurar nossos servidores 


## Systems Manager – SSM Session Manager
- Permita o lançamento de um shell seguro em seu EC2 e servidores locais
- Não é necessário acesso SSH, bastiões de hosts ou chaves SSH
- Não há necessidade de porta 22 (melhor segurança)
- Suporta Linux, macOS e Windows
- Envie dados de log de sessão para S3 ou CloudWatch Logs

**Hands On**

Crie uma instancia EC2 ena configuração de IAM instance profile, crie uma Role com a seguinte Policie: AmazonSSMServiceRolePolicy. Após isso, atribua a sua EC2.
Vá ao serviço AWS Systems Manager e espere sua instancia aparecer la, pois já tem o agente instalado na imagem. 

## AWS OpsWorks
- O Chef & Puppet ajuda você a configurar o servidor automaticamente ou ações repetitivas
- Eles funcionam muito bem com EC2 e VM no local
- AWS OpsWorks = Chef gerenciado e marionete
- É uma alternativa ao AWS SSM
- Provisione apenas recursos padrão da AWS:
- Instâncias EC2, bancos de dados, balanceadores de carga, volumes EBS…
- No exame: Chef ou Puppet necessário => AWS OpsWorks

<img src="images/img38.png" alt="img38" width="800"/>
<img src="images/img39.png" alt="img39" width="800"/>

---
<h1 align="center">Global Infrastructure Section</h1>

É uma aplicação implantado em várias áreas Geográficas(Regions ou  Edge Locations)

**Latência diminuída**
- Latência é o tempo que leva para um pacote de rede chegar a um servidor
- Leva tempo para um pacote da Ásia chegar aos EUA
- Implante seus aplicativos mais perto de seus usuários para diminuir a latência e melhorar a experiência

**Recuperação de Desastres (DR)**
- Se uma região da AWS ficar inativa (terremoto, tempestades, desligamento de energia, política)…
- Você pode fazer failover para outra região e manter seu aplicativo funcionando
- Um plano de DR é importante para aumentar a disponibilidade do seu aplicativo
- Proteção contra ataques: a infraestrutura global distribuída é mais difícil de atacar

## Global AWS Infrastructure
- Regions: para implantação aplicativos e a infraestrutura
- Availability Zones: Feito de vários data centers 
- Edge Locations (Points of Presence):para entrega de conteúdo como próximo possível de usuários

## Aplicativos globais na AWS

**DNS Global: Rota 53**
- Ótimo para direcionar os usuários para a implantação mais próxima com menos latência
- Ótimo para estratégias de recuperação de desastres

**Rede Global de Entrega de Conteúdo (CDN): CloudFront**
- Replique parte do seu aplicativo para pontos de presença da AWS – diminua a latência
- Cache de solicitações comuns – experiência do usuário aprimorada e latência reduzida

**Aceleração de Transferência S3**
- Acelere uploads e downloads globais no Amazon S3

**Acelerador global da AWS:**
- Melhore a disponibilidade e o desempenho global de aplicativos usando o AWS global
rede

## Amazon Route 53 Overview
É um sistema de DNS(Domain Name Sysem) gerenciado
- DNS é uma coleção de regras e registros que ajudam os clientes a entender como chegar a um servidor através de URLs.

<img src="images/img40.png" alt="img40" width="800"/>

## Route 53 Routing Policies
- **Simple Routing Policy:** o Web faz a requisição para o Route 53 e ele devolve o IP sem nenhuma verificação de saúde.
- **Weighted Routing Policy:** Permite distribuir o trafego entre várias instâncias. Porém é necessário setar pesos para as instancias. Pode usar verificações de saúde.
- **Latency Routing Policy:** É usado para minimizar a latência entre os usuários e servidores, fazendo os usuários se conectar aos servidores mais próximos a eles.
- **Failover Routing Policy:** A Web faz uma requisição para o Route 53, ele faz um health check da instancia primaria, caso esteja com falha, ele manda para uma instancia FailOver.

**OBS: Route53 NÃO É GRATUITO. 12doll/month**

## AWS CloudFront
É uma rede de entrega de conteúdo(CDN)
- Melhora o desempenho de leitura, armazenamento em cache de conteúdo do seu site em diferentes Edge Location. Melhorando a experiencia do usuário
- CloudFront é composto por 216 pontos de presença globalmente (edge locations)
- Tem proteção de DDos, integração com Shield e AWS Web Applications Firewall

## CloudFront – Origens
**Bucket S3**
- Para distribuir arquivos e armazená-los em cache na borda 
- Segurança aprimorada com CloudFront Origin Access Identity (OAI) 
- CloudFront pode ser usado como uma entrada (para fazer upload de arquivos para S3) 

**Origem personalizada (HTTP)**
- Balanceador de carga de aplicativos 
- Instância do EC2 
- Site S3 (primeiro deve habilitar o bucket como um site S3 estático) 
- Qualquer back-end HTTP desejado

## Replicação entre regiões do CloudFront vs S3
**CloudFront:**
- Rede de borda global
- Os arquivos são armazenados em cache por um TTL (talvez um dia)
- Ótimo para conteúdo estático que deve estar disponível em todos os lugares

**Replicação entre regiões do S3:**
- Deve ser configurado para cada região em que você deseja que a replicação aconteça
- Os arquivos são atualizados quase em tempo real
- Somente leitura
- Ótimo para conteúdo dinâmico que precisa estar disponível com baixa latência em algumas regiões

**Hands On**
Primeiro crie um bucket no S3 com um site estatico. Após isso, vá em CloudFront configure as opções padrões, e crie um OIA(Origin Access Identity) caso não tenha. E marque como Yes no campo bucket Policy.

## S3 Transfer Acceleration
É um serviço que aumenta a velocidade de transferência dos arquivos do S3 para outra Região.

É pego o arquivo que você deseja transferir, é feito o carregamento em uma Edge Location, e depois é usado uma rede interna de edge location para enviar o arquivo para outra region.

Para testar a velocidade de transferencia: https://s3-accelerate-speedtest.s3-accelerate.amazonaws.com/en/accelerate-speed-comparsion.html

## AWS Global Accelerator
É usado para melhorar a disponibilidade e desempenho de uma aplicação global. A ideia é que suas solicitações sejam encaminhadas através da rede interna citada anteriormente, permitindo que optimize a rota para sua aplicação cerca de 60%.

Voce conecta seu aplicativo por meio do “2 Anycast IP”, e através dele você é redigido automaticamente para a Edge Location.

## AWS Global Accelerator vs CloudFront
Ambos usam a rede global da AWS e seus pontos de presença em todo o mundo

Ambos os serviços se integram ao AWS Shield para proteção contra DDoS.

**CloudFront – Content Delivery Network**
- Melhora o desempenho do seu conteúdo em cache (como imagens e vídeos)
- O conteúdo é veiculado na borda

**Global Accelerator**
- Sem armazenamento em cache, pacotes de proxy na borda para aplicativos executados em uma ou mais regiões da AWS.
- Melhora o desempenho para uma ampla variedade de aplicativos em TCP ou UDP
- Bom para casos de uso HTTP que exigem endereços IP estáticos
- Bom para casos de uso HTTP que exigiam failover regional rápido e determinístico
Para testar a Global Accelerator: https://speedtest.globalaccelerator.aws/ 

## AWS Outposts
- AWS Outposts são “racks de servidores” que oferecem a mesma infraestrutura, serviços, APIs e ferramentas da AWS para construir seus próprios aplicativos on-premises assim como na nuvem
- AWS irá configurar e gerenciar “Outposts Racks” dentro do on-premises e você pode  começar a aproveitar os serviços da AWS no local.
- Você é responsável pelo rack de postos avançados segurança física

**Benefícios:**
- Acesso de baixa latência a sistemas locais
- Processamento de dados locais
- Residência de dados
- Migração mais fácil do local para a nuvem
- Serviço totalmente gerenciado
	
## AWS WaveLength
- Zonas WaveLength são implantações de infraestrutura incorporadas aos provedores de telecomunicações datacenters na borda das redes 5G
- Leva os serviços da AWS para a borda das redes 5G
- Exemplo: EC2, EBS, VPC…
- Aplicativos de latência ultrabaixa por meio de redes 5G
- O tráfego não sai do Serviço de Comunicação Rede do provedor (CSP)
- Conexão segura e de alta largura de banda com a região pai da AWS
- Sem encargos adicionais ou contratos de serviço
- Casos de uso: cidades inteligentes, diagnóstico assistido por ML, veículos conectados, fluxos de vídeo interativos ao vivo, AR/VR, Jogos em tempo real,…

## AWS Local Zones
- Coloca computação, armazenamento, banco de dados da AWS, e outros serviços selecionados da AWS mais próximos aos usuários finais para executar sensíveis à latência formulários
- Estenda sua VPC para mais locais – “Extensão de uma região da AWS”
- Compatível com EC2, RDS, ECS, EBS, ElastiCache, Conexão Direta…
Exemplo:
- Região da AWS: norte da Virgínia (us-east-1)
- Zonas locais da AWS: Boston, Chicago, Dallas, Houston, Miami, …

## Global Applications Architecture

<img src="images/img41.png" alt="img41" width="800"/>
<img src="images/img42.png" alt="img42" width="800"/>

## Summary
<img src="images/img43.png" alt="img43" width="800"/>
<img src="images/img44.png" alt="img44" width="800"/>

---
<h1 align="center">Cloud Integration Section</h1>

## Section Introduction
**Tipos de comuniacção etre aplicações**

<img src="images/img45.png" alt="img45" width="800"/>

- A sincronização entre aplicativos pode ser problemática se houver picos de tráfego repentinos
- E se de repente você precisar codificar 1.000 vídeos, mas geralmente são 10?
- Nesse caso, é melhor desacoplar suas aplicações:
	- usando SQS: modelo de fila
	- usando SNS: modelo pub/sub
	- usando Kinesis: modelo de streaming de dados em tempo real (fora do escopo do exame)
- Esses serviços podem ser dimensionados independentemente do nosso aplicativo!

## Amazon SQS(Simple Queue Service)
- Oferta mais antiga da AWS (mais de 10 anos)
- Serviço totalmente gerenciado (~serverless), use para desacoplar aplicativos
- Escala de 1 mensagem por segundo a 10.000s por segundo
- Retenção padrão de mensagens: 4 dias, máximo de 14 dias
- Sem limite de quantas mensagens podem estar na fila
- As mensagens são excluídas depois de lidas pelos consumidores
- Baixa latência (<10 ms na publicação e recepção)
- Os consumidores compartilham o trabalho de ler mensagens e dimensionar horizontalmente

<img src="images/img46.png" alt="img46" width="800"/>

## Amazon SNS (Simple Notification Service)
É usado para enviar mensagem para os tópicos SNS e automaticamente irá enviar uma notificação para o serviço do mesmo tópico.
- Os “editores de eventos” só enviam mensagens para um tópico do SNS
- Quantos "assinantes de eventos" quisermos ouvir as notificações de tópicos do SNS
- Cada assinante do tópico receberá todas as mensagens
- Até 12.500.000 assinaturas por tópico, limite de 100.000 tópicos

## Amazon Kinesis
- Para o exame: Kinesis = real-time big data streaming
- Serviço gerenciado para coletar, processar e analisar streaming em tempo real dados em qualquer escala
- Detalhado demais para o exame Cloud Practitioner, mas é bom saber:
- Kinesis Data Streams: streaming de baixa latência para ingerir dados em escala de centenas de milhares de fontes
- Kinesis Data Firehose: carregue streams no S3, Redshift, ElasticSearch, etc…
- Kinesis Data Analytics: execute análises em tempo real em fluxos usando SQL
- Streams de vídeo do Kinesis: monitore fluxos de vídeo em tempo real para análise ou ML

## Amazon MQ
- SQS, SNS são serviços “nativos de nuvem” e usam protocolos proprietários da AWS.
- Os aplicativos tradicionais executados no local podem usar protocolos abertos, como: MQTT, AMQP, STOMP, Openwire, WSS
- Ao migrar para a nuvem, em vez de reprojetar o aplicativo para usar SQS e SNS, podemos usar o Amazon MQ
- Amazon MQ = Apache ActiveMQ gerenciado
- O Amazon MQ não “escalona” tanto quanto o SQS/SNS
- O Amazon MQ é executado em uma máquina dedicada (não sem servidor)
- O Amazon MQ tem recursos de fila (~SQS) e de tópicos (~SNS)

## Summary
<img src="images/img47.png" alt="img47" width="800"/>

---
<h1 align="center">Cloud Monitoring Section</h1>

## Amazon CloudWatch Metrics
- Fornece métricas para cada serviço na AWS
- Métrica é uma variável a ser monitoradar (CPUUtilization, NetworkIn…)
- As métricas terão Timestamps
- Pode criar uma dashborad para todas as métricas.

**Matricas Importantes**
- EC2 instances: CPU Utilization, Status Checks, Network (not RAM)
- Obtem a métrica a cada 5 min por padão
- Pode habilitar o Monitoramento detalhado para pegar a cada minuto. Pago 
- EBS volumes: Disk Read/Writes
- S3 buckets: BucketSizeBytes, NumberOfObjects, AllRequests
- Billing: Total Estimated Charge (only in us-east-1)
- Service Limits: how much you’ve been using a service API
- Custom metrics: push your own metrics

## Amazon CloudWatch Alarm
- Os alarmes são usados para acionar notificações para qualquer métrica
- Ações de alarmes…
	- **Auto Scaling:** aumente ou diminua a contagem “desejada” de instâncias do EC2
	- **Ações do EC2:** pare, encerre, reinicialize ou recupere uma instância do EC2
	- **Notificações SNS:** envie uma notificação para um tópico SNS
- Várias opções (amostragem, %, max, min, etc…)
- Pode escolher o período no qual avaliar um alarme
- Exemplo: crie um alarme de cobrança na métrica de cobrança do CloudWatch
- Estados de alarme: OK. INSUFICIENT_DATA, ALARME

## Amazon CloudWatch Logs
**Coleta logs dos serviços através do:**
- Elastic Beanstalk: Coleta logs através dos agentes
- ECS: Coleta logs de containers
- AWS Lambda: Coleta logs das functions
- CloudTrail baseado no filtro
- CloudWatch log agents: nas EC2 machines ou on-premises servers
- Route53: Logs de querires de DNS

Pode habilitar o monitoramento em tempo real dos logs.

Pode reajustar os logs para retenção

## CloudWatch Logs for EC2
- Por padrão, nenhum log do seu EC2 instância irá para o CloudWatch
- Você precisa executar um CloudWatch agente no EC2 para enviar os arquivos de log você quer
- Certifique-se de que as permissões do IAM sejam correto
- O agente de log do CloudWatch pode ser configuração no local também

## Amazon CloudWatch Events
É uma maneira de reagir as eventos que acontecem dentro da AWS
<img src="images/img48.png" alt="img48" width="800"/>

## Amazon EventBridge
- EventBridge é a próxima evolução do CloudWatch Events
- Barramento de eventos padrão: gerado pelos serviços da AWS (CloudWatch Events)
- Barramento de eventos do parceiro: receba eventos de serviços ou aplicativos SaaS (Zendesk, DataDog, Segment, Auth0…)
- Barramentos de eventos personalizados: para seus próprios aplicativos
- Registro de Esquema: esquema de evento de modelo
- EventBridge tem um nome diferente para marcar os novos recursos
- O nome do CloudWatch Events será substituído por EventBridge

## AWS CloudTrail
É uma forma de fornece governança, conformidade e auditoria para sua conta da AWS
- CloudTrail está habilitado por padrão!
- Obtenha um histórico de eventos/chamadas de API feitas em sua conta da AWS:
	- Console
	- SDK
	- CLI
- Serviços da AWS
- Pode colocar logs do CloudTrail no CloudWatch Logs ou S3
- Uma trilha pode ser aplicada a Todas as Regiões (padrão) ou a uma única Região.
- Se um recurso for excluído na AWS, investigue o CloudTrail primeiro!

## CloudTrail Events
**Management Event**
- Operações realizadas em recursos na conta AWS
- Exemplos:
	- Configuring security (IAM AttachRolePolicy) 
	- Configuring rules for routing data (Amazon EC2 CreateSubnet) 
	- Setting up logging (AWS CloudTrail CreateTrail) 
- Por padrão, as trilas são configuradas para registrar eventos de gerenciamento
- Pode separar em Eventos de Leitura(não modifica o recurso), e Eventos de Escrita(Modificam recursos)

**Data Events**
- Por padrão não são registrados nos logs (por causa do grande volume)
-  Quando se tem um nível de objeto na S3 (ex: GetObject, DeleteObject, PutObject), e tem a opção de separa a Leitura e Escrita.
- Sempre que alguém usar API invoque, você poderá obter insights sobre quantas vezes as funções estão sendo chamadas

## CloudTrail Insights Events (Pago)
Serviço que analisa seus eventos e tenta detectar atividades incomuns na sua conta.
- Provisionamento impreciso de recurso
- Limites atingidos dos serviços
- Surto de ações na AWS
- Gaps na atividade de manutenção periódica
O CloudTrail irá analisar como são as atividade normais de gerenciamento para criar uma linha de base, e em seguida irá analisar continuamente qualquer coisa que seja um tipo de Write event fora do padrão.
- As anomalias irão aparecer no CloudTrail Console
- Podem ser enviadas para um S3 se quiser
- Um EnventBridge será gerado caso precise

## CloudTrail Events Retention
Os eventos são armazenados por 90 dias no CloudTrail e só depois são deletados.
- Para manter os arquivos além do período, pode ser armazenado em um S3 e usar athena para analisar eles

**Hands On**
Em CloudTrail > Dashboard pode-se ter uma visão ampla do serviço.
Na aba Event History podemos obter as informações de todas as chamadas de API feitas por alguns serviços. Pode criar uma Athena Table para fazer análise dos dados.
Na aba Trail pode criar um S3 para armazenar os logs, e deve desmarcar a criptografia SSE-KMS. Habilitar  CloudWatch Logs. Criar uma nova IMA Role. Depois é necessário escolher um tipo de log events(é pago se habilitar mais)

## AWS X-Ray
Serve para fazer um rastreamento e obter uma analise visual de sua aplicação
Vantagens:
- Solução de problemas de performance
- Entender as dependências uma arquitetura de microsserviços
- Identificar um problema de serviço
- Revisar o comportamento de uma solicitação em PRD
- Encontrar erros e exceções dessas solicitações
- se está cumprindo os SLA
- Identificar quais usuários estão sendo impactados por algum problema

## Amazon CodeGuru  
É um serviço baseado em Machine Learning Power service para automatizar code review e recomendação de desempenho de aplicativo.

**CodeGuru Reviewer:** revisões de código automatizadas para análise de código estático (desenvolvimento).
- Identificar problemas críticos, segurança vulnerabilidades e bugs difíceis de encontrar
- Exemplo: práticas recomendadas de codificação comuns, vazamentos de recursos, detecção de segurança, entrada validação
- Usa Machine Learning e automatizado raciocínio
- Lições aprendidas com dificuldade em milhões de revisões de código em 1000s de código aberto e repositórios da Amazon
-  Suporta Java e Python
-  Integra-se ao GitHub, Bitbucket e AWS CodeCommit

**CodeGuru Profiler:** visibilidade/recomendações sobre o desempenho do aplicativo durante tempo de execução (produção)
- Ajuda a entender o comportamento de tempo de execução do seu inscrição
- Exemplo: identifique se seu aplicativo está consumindo capacidade excessiva da CPU em uma rotina de log
- **Características:**
	- Identificar e remover ineficiências de código
	- Melhore o desempenho do aplicativo (por exemplo, reduza a CPU utilização)
	- Reduza os custos de computação
	- Fornece resumo de heap (identificar quais objetos usando memória)
	- Detecção de anomalia
- Suporte a aplicativos executados na AWS ou no local
- Sobrecarga mínima na aplicação

## AWS Status - Service Health Dashboard
Mostra a saúde de todos as regions e serviços que esta rodando.
- Mostra um histórico diário, e tem um RSS feed que pode assinar para receber notificações de status.
Status dos serviços: https://status.aws.amazon.com/ 

## AWS Personal Health Dashboard
Provisiona alertas e orientação de correção quando a AWS estiver experimentando eventos que podem impactar  sua aplicação.
- Enquanto o Service Health Dashboard exibe o status geral de serviços da AWS, o Personal Health Dashboard oferece uma visualizar o desempenho e a disponibilidade dos serviços da AWS subjacente aos seus recursos da AWS.
- O painel exibe informações relevantes e oportunas para ajudá-lo gerenciar eventos em andamento e fornece notificação proativa para ajudá-lo a planejar as atividades programadas.

Global service https://phd.aws.amazon.com/

## Summary

<img src="images/img49.png" alt="img49" width="800"/>

---
<h1 align="center">VPC Section</h1>
Significa Virtual Private Cloud

## VPC & Subnets Primer
- VPC -Virtual Private Cloud: rede privada para implantar seus recursos(recurso regional)
- As Subnets permitem particionar sua rede dentro de sua VPC (recurso de zona de disponibilidade)
- Uma sub-rede pública é uma sub-rede que é acessível pela internet
- Uma sub-rede privada é uma sub-rede que não é acessível pela internet
- Para definir o acesso à internet e entre sub-redes, usamos tabelas de rotas

## Internet Gateway & NAT Gateways

Internet gateway faz com que as instancias que estão na subnet tenham acesso a internet e sejam públicas. NAT fica conectada a uma Private Subnet e faz uma ponte para que ela tenha acesso a internet, utilizando internet gateway
- Gateways de Internet ajudam nossa VPC instâncias se conectam à internet
- As sub-redes públicas têm uma rota para o porta de internet.
- Gateways NAT (gerenciados pela AWS) e Instâncias NAT (autogerenciadas) permitem suas instâncias em suas sub-redes privadas para acessar a internet enquanto permanece privado
Site para visualizar o range de IPs: https://cidr.xyz/ 

## Network ACL & Security Groups
**NACL (Network ACL)**
- É um firewall que controla o trafico de e para sua subnet
- Pode ter regras PERMISSÃO e NEGAÇÃO
- Estão anexados no nível de sub-rede
- As regras incluem apenas endereços IP

**Securiry Groups**
- Um firewall que controla o tráfego de e para um ENI/uma instância EC2
- Pode ter apenas regras PERMITIR
- As regras incluem endereços IP e outros itens de segurança grupos

<img src="images/img50.png" alt="img50" width="600"/>

## VPC Flow Logs
São registros de todo o tráfego de IP que passa pelas interfaces:
- VPC Flow Logs
- Subnet Flow Logs
- Elastic Network Interface Flow Logs

Ajuda a monitorar e resolver problemas de conectividade. Exemplo:
Subnet não conecta a internet, Subnet não conecta a outra Subnet, Internet não consegue se conectar a subnet.

Captura informações de network do gerenciamento de interface AWS como: Elastic Load Balancers, ElastiCache, RDS, Aurora, etc…

Os dados da VPC Flow Logs podem ser armazenados em um S3 ou enviados para CloudWatch

## VPC Peering
É uma forma de conectar duas VPC de forma privada usando a rede da AWS, em fazer com que se comportem como se fossem parte da mesma rede. 

Para fazer isso deve-se ter certeza que a faixa de IPs não se sobreponham. Caso isso aconteça, não será possível estabelecer uma coneção de VPC Peering.

Outra coisa é que a conexão de VPC Peering não é transitiva. Isso significa que para se conectar a uma terceira VPC, é necessário fazer a conexão com as duas VPC já existentes.

<img src="images/img51.png" alt="img51" width="400"/>

## VPC Endpoints
Endpoints permite você conectar nos serviços da AWS usando uma Private Network ao invés de uma Public Network.
Usar isso dará uma segurança porque não estará navegando pela internet, e também terá menos latência por não acessar os serviços através de pulos de rede.
- VPC Endpoint Gateway: S3 & DynamoDB
- VPC Endpoint Interface: the rest


## Site to Site VPN & Direct Connect
**VPN site a site**
- Conecte uma VPN local à AWS
- A conexão é automaticamente criptografado
- Passa pela internet pública
- On-premises: precisa usar uma Customer Gateway (CGW)
- AWS: precisa usar uma Virtual Private Gateway (VGW)
**Conexão Direta (DX)**
- Estabeleça uma conexão física entre local e AWS
- A conexão é privada, segura e rápida
- Passa por uma rede privada
- Leva pelo menos um mês para estabelecer

## Transit Gateway
- deve ter conexão de peering entre milhares de VPC e seu sitema On-premises, com uma conexão hub-and-spoke (star) 
- Um único Gateway para fornecer esta funcionalidade
- Funciona com Conexão Direta Gateway, conexões VPN

<img src="images/img52.png" alt="img52" width="300"/>

## Summary
<img src="images/img53.png" alt="img53" width="800"/>

---
<h1 align="center">Security e Compliance</h1>

## AWS Shared Responsibility Model
**AWS responsibility - Security of the Cloud**
- Proteção da infraestrutura (hardware, software, instalações e rede) que funcionatodos os serviços da AWS
- Serviços gerenciados como S3, DynamoDB, RDS, etc. Responsabilidade do cliente - Segurança na Nuvem
**Customer responsibility - Security in the Cloud:**
- Para instância do EC2, o cliente é responsável pelo gerenciamento do SO convidado (incluindo patches de segurança e atualizações), configuração de firewall e rede, IAM
- Criptografia de dados do aplicativo
**Controles compartilhados:**
- Gerenciamento de patches, gerenciamento de configuração, conscientização e treinamento

## DDOS Protection on AWS
É um ataque de negação de serviço distribuído na infraestrutura. O Hacker criar varias maquinas q lanças milhares de bots para a sua aplicação, fazendo com que em algum momento ela pare de funcionar por sobrecarga de requests.

## AWS Shield
**AWS Shield Standard:**
- É um serviço gratuito para os clientes, que fornece proteção  para ataques de SYN/UDP Floods, Reflection attacks e ataques nas layer 3/layer 4 
**AWS Shield Advanced:**
- É um serviço opcional que custa 3000 doll/mês.
- Protege de ataques mais sofisticados na Amazon EC2, Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator, and Route 53.
- Tem acesso ao time de DDoS para ajudar na defesa contra o ataque

## AWS WAF – Web Application Firewall
Protege as aplicações na web. Pode ser aplicado no Application Load Balancer, API Gateway, CloudFront.
- Pode ser definido uma ACL(Web Access Control List), e as regras podem incluir a filtragem de  IP addresses, HTTP headers, HTTP body, or URI strings.
- Fornece proteção contra SQL injection e Cross-Site Scripting(XSS)
- Pode definir o tamanho das solicitações para que não sejam muito grandes e também bloquear certos países usando uma Geo-Match.
- Para DDoS pode ser usado a Rate-Based Rules

## Penetration Testing on AWS Cloud
É quando você esta tentando atacar sua própria infraestrutura para testar a segurança.
Os clientes da AWS podem realizar avaliações de segurança ou testes de penetração em sua infraestrutura AWS sem aprovação prévia para 8 serviços:
- Amazon EC2 instances, NAT Gateways, and Elastic Load Balancers
- Amazon RDS
- Amazon CloudFront
- Amazon Aurora
- Amazon API Gateways
- AWS Lambda and Lambda Edge functions
- Amazon Lightsail resources
- Amazon Elastic Beanstalk environments

**Atividades Proibidas para testar**
- Zona DNS caminhando pelas zonas hospedadas do Amazon Route 53
- Negação de Serviço (DoS), Negação de Serviço Distribuída (DDoS), DoS Simulado, DDoS simulado
- Port flooding
- Protocol flooding
- Protocol flooding (inundação de solicitação de login, inundação de solicitação de API)

## Data at rest vs. Data in transit
At rest(dado que não esta se movendo): Dados armazenados ou arquivados em um dispositivo fisico(HD,RDS instance, S3, etc)
At Transit(dado que esta se movendo): Dados que estão se movendo de uma direção parar outra, ou dados transferidos pela rede(transferência de dados de on-premises para AWS, EC2, DynamoDB, etc).
Para ambos os casos é utilizado encrypted key para proteger as informações

## AWS KMS (Key Management Service)
A AWS gerencia as encryption Keys para a gente
**Encryption Opt-in:**
- EBS volumes: encrypt volumes
- S3 buckets: Server-side encryption of objects
- Redshift database: encryption of data
- RDS database: encryption of data
- EFS drives: encryption of data
**Encryption Automatically enabled:**
- CloudTrail Logs
- S3 Glacier
- Storage Gateway

## CloudHSM
A AWS gerencia criptográfica de hardware. Um Hardware é dedicado chamado HSM(Hardware Security Module) porem as encryption Keys é o usuário que terá que gerenciar

## Types of Customer Master Keys: CMK

**Customer Managed CMK:**
- Criado, gerenciado e utilizado pelo cliente, pode habilitar ou desabilitar.
- Possibilidade de política de rotação (nova chave gerada todos os anos, chave antiga preservada).
- Possibilidade de trazer sua própria chave.

**AWS managed CMK:**	
- Criado, gerenciado e usado em nome do cliente pela AWS
- Usado pelos serviços da AWS (aws/s3, aws/ebs, aws/redshift)

**AWS owned CMK:**
- Coleção de CMKs que um serviço da AWS possui e gerencia para usar em várias contas
- A AWS pode usá-los para proteger recursos em sua conta (mas você não pode visualizar as chaves)

**CloudHSM Keys (custom keystore):**
- Chaves geradas a partir do seu próprio dispositivo de hardware CloudHSM
- As operações criptográficas são realizadas no cluster do CloudHSM

## AWS Certificate Manager (ACM)
É um serviço para provisionar, gerenciar e implantar facilmente certificados SSL ou TSL. É utilizado para fornecer criptografias in-fligth para sites. ACM suporta certificados TSL públicos e privados. 
- É **Gratuito** para certificados TSL. 
- Tem um sistema de renovação automático de certificado TSL
- Tem integração para carregar certificados em diferentes serviços como ELB, CloudFront, APIs ou APIs Gateway

## AWS Secrets Manager
É um serviço recente e destina-se ao armazenamento de secrets. Pode forçar a rotação de secrets, podendo ser alteradas a cara **X** dias.
- Pode automatizar a criação de Secrets usando Lambda
- Tem integração com RDS
- As secretsd são criptografadas usando KMS
- Sempre que ver um secrets para ser gerenciado no RDS e ser rotacionado, a resposta será AWS Secrets Manager

## AWS Artifact (not really a service)
É portal que oferece aos clientes acesso sob demanda à documentação de conformidade da AWS e aos contratos da AWS.
Esses relatórios podem ser usados para oferecer suporte aos recursos de auditorias internas dentro da sua empresa ou necessidades de reclamações.

## Amazon GuardDuty
É um serviço que realizará a descoberta inteligente de ameaçar para proteger a conta da AWS. Ele usa algoritmos de Machine Learning, detecção de anomalias e dados de terceiros.
GuardDuty obtem alguns dados de input como 
- CloudTrail Events Logs – unusual API calls, unauthorized deployments
	- CloudTrail Management Events – create VPC subnet, create trail, …
	- CloudTrail S3 Data Events – get object, list objects, delete object, …
- VPC Flow Logs – unusual internal traffic, unusual IP address
- DNS Logs – compromised EC2 instances sending encoded data within DNS queries
- Kubernetes Audit Logs – suspicious activities and potential EKS cluster compromises

- Pode configurar CloudWatch Event rules para receber notificação em casos de descobertas.
- Pode configurar também Lambda function ou SNS
- O GuardDuty pode ajudar contra ataques de criptomoedas porque possui descoberta(“finding”) dedicada para isso

## Amazon Inspector
Permite que você faça avaliações de segurança automática na infraestrutura AWS. Ele ira olar para duas coisas.
EC2 Instances:
- Erecutará no back-end o agente do gerenciador de sistemas da AWS.
- Em seguida analisará a acessibilidade de rede não intencional.
- Analizará o OS executando em relação a vulnerabilidades conhecidas
Containers push to Amazon ECR:
- Avaliação dos containers a medida que são enviados para ECR

Todos os reports estão integrados com AWS Security Hub, e as descobertas serão enviadas ao Amazon Event Brige.

**O que AWS Inspector avalia?**
- Lembre-se: apenas para instâncias do EC2 e infraestrutura de contêiner
- Verificação contínua da infraestrutura, somente quando necessário
- Vulnerabilidades do pacote (EC2 e ECR) – banco de dados do CVE
- Acessibilidade da rede (EC2)
- Uma pontuação de risco está associada a todas as vulnerabilidades para priorização

## AWS Config
- Ajuda na auditoria e registro de conformidade de seus recursos da AWS, registrando configurações e alterações ao longo do tempo.
- Possibilidade de armazenar os dados de configuração no S3 (analisado pelo Athena)
- Perguntas que podem ser resolvidas pelo AWS Config:
- Existe acesso SSH irrestrito aos meus grupos de segurança?
- Meus buckets têm acesso público?
- Como minha configuração do ALB mudou ao longo do tempo?
- Você pode receber alertas (notificações SNS) para quaisquer alterações
- AWS Config é um serviço por região
- Pode ser agregado entre regiões e contas

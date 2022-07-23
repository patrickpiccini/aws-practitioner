
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

# EC2 instance Storge
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

# ELB & ASG - Elastic Load Balancing e Auto Scaling.
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


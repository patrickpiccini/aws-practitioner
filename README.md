
<h1 align="center">Estudo para certificação AWS</h1>
<p align="center">
    <img src="images/aws.png" alt="aws" width="200"/>
</p>

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
Shared Responsability Model Diagram
 
<img src="images/img1.png" alt="img1" width="800"/>

# IAM – Identity and Acess Management
piccini-aws - patrick-adm - P@ssw0rd
Users, Goups and Policies
 É criado User e Goups para possemos atribuir policies a eles, fazendo com que tenham acesso aos serviços que necessitam ter, e não a tudo como um ADM. Os  User e Goups pode receber um JSON document chamado POLICIE.
È uma Boa pratica criar um usuário ADM para fazer a administração da AWS, e resguardar a conta Root por segurança


# Como criar uma rede VPC e uma Maquina Virtual no Google Cloud Platform

## Rede VPC

A rede VPC é uma rede virtual disponibilizada pela Google para interconexão entre as instancias de maquinas virtuais (VM) do Compute Engine, conteineres do Google Kubernetes Engine (GKE) e o ambiente flexivel do App engine. Essa rede é global, escalonada e flexível


### Criando a rede VPC

Por padrão o GCP já possui uma VPC padrão (default), porém poderemos criar outras redes. Para criar você deverá ir no menu lateral esquerdo e ir na opção "Rede VPC" > , ou poderá  efetuar a busca através da barra de pesquisa.
Ao clicar no botão "criar rede VPC" você poderá iniciar dando um nome a sua nova rede. No exemplo abaixo foi utilizado o nome vpc-geral. Nessa mesma tela você poderá dar maiores descrições sobre a sua rede e poderá também ativar o IPv6.

Mais abaixo você poderá criar as sub-redes. Essas sub-redes serão utilizadas pelas VMs, GKEs e todos os outros recursos que necessitem de uma VPC. Toda sub-rede é necessaria que seja vinculada a uma região e essa sub-rede só estará disponivel para as maquinas que estiverem na mesma região. Próximo passo será configurar o intervalo de IPv4 utilizado. Caso serja necessario, você poderá ativar o acesso privado e os registros de fluxo da VPC

Com esses passos, a sua sub-rede VPC e a sua rede VPC já estarão prontas, próximo passo será configurar as regras de firewall, caso haja necessidade. O VPC já vem com algumas regras padrão então, essas serão as utilizadas nesse exemplo

Também temos a configuração do modo de roteamento. No exemplo abaixo utilizamos o modo regional. Após isso finalizamos a criação da nossa rede e sub-rede




## Compute Engine

Compute Engine é o produto do Google Cloud Platform onde você poderá criar suas maquinas virtuais e fazer instalação das suas aplicações. Ao acessar o console do GCP (console.cloud.google.com), você poderá acessar essa ferramenta através do botão "criar uma VM" que irá aparecer no dashboard, através do menu lateral esquerdo e ir até a opção "Compute Engine" ou digitando na barra de pesquisa.
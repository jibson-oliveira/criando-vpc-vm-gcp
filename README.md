# Como criar uma rede VPC e uma Maquina Virtual no Google Cloud Platform

## Rede VPC

A rede VPC é uma rede virtual disponibilizada pela Google para interconexão entre as instancias de maquinas virtuais (VM) do Compute Engine, conteineres do Google Kubernetes Engine (GKE) e o ambiente flexivel do App engine. Essa rede é global, escalonada e flexível


### Criando a rede VPC

Por padrão o GCP já possui uma VPC padrão (default), porém poderemos criar outras redes. Para criar você deverá ir no menu lateral esquerdo e ir na opção "Rede VPC" , ou poderá  efetuar a busca através da barra de pesquisa.
![](/images/menu-vpc.JPG)

Ao clicar no botão "criar rede VPC" você poderá iniciar dando um nome a sua nova rede. 
![](/images/dashboard-vpc.JPG)

No exemplo abaixo foi utilizado o nome vpc-geral. Nessa mesma tela você poderá dar maiores descrições sobre a sua rede e poderá também ativar o IPv6.

![](/images/criar-rede.JPG)
> Tela de Criação de Rede no GCP

Mais abaixo você poderá criar as sub-redes. Essas sub-redes serão utilizadas pelas VMs, GKEs e todos os outros recursos que necessitem de uma VPC.Elas podem ser criadas automaticamente ou de modo personalizado. Toda sub-rede é necessaria que seja vinculada a uma região e essa sub-rede só estará disponivel para as maquinas que estiverem na mesma região. Próximo passo será configurar o intervalo de IPv4 utilizado. Caso seja necessario, você poderá ativar o acesso privado e os registros de fluxo da VPC

![](/images/editar-subrede.JPG)
> Tela de criação de sub-redes

Com esses passos, a sua sub-rede VPC e a sua rede VPC já estarão prontas, próximo passo será configurar as regras de firewall, caso haja necessidade. O VPC já vem com algumas regras padrão então, essas serão as utilizadas nesse exemplo

![](/images/firewall.JPG)
> Campo firewall com algumas regras default

Também temos a configuração do modo de roteamento. No exemplo abaixo utilizamos o modo regional. Após isso finalizamos a criação da nossa rede e sub-rede
![](/images/roteamento.JPG)
> Tela de definição do roteamento

## Compute Engine

Compute Engine é o produto do Google Cloud Platform onde você poderá criar suas maquinas virtuais e fazer instalação das suas aplicações. Ao acessar o console do GCP (console.cloud.google.com), você poderá acessar essa ferramenta através do botão "criar uma VM" que irá aparecer no dashboard, através do menu lateral esquerdo e ir até a opção "Compute Engine" ou digitando na barra de pesquisa.

### Criando uma Virtual Machine (VM)

Para criar a nossa VM, iremos clicar no botão "criar instância". Nessa nova tela iremos dar o nome pra nossa VM. Caso haja necessidade, você pode criar uma label pra vincular a essa VM. Iremos também escolher a região e zona onde ela estará alocada. A região e zona são permanentes e a escolha interfere na estimativa mensal de custo da VM. No exemplo abaixo utilizaremos a região East-1 pois foi a mesma utilizada na criação da VPC do tópico anterior.

Próximo passo será a escolha da configuração da máquina. Cada máquina tem um propósito e um objetivo, por isso é necessário saber qual tipo de aplicação será utilizada. Na pagina de documentação do Compute Engine tem uma página que pode te auxiliar a escolher qual tipo de máquina será o ideal para a sua aplicação (https://cloud.google.com/compute/docs/machine-resource?hl=pt-br#recommendations_for_machine_types)

Para o exemplo abaixo foi utilizado uma VM do tipo e2-medium que possui 2vCPU e 4 GB de memória

![](/images/criar-vm.JPG)
> Tela de criação da VM onde poderemos definir o nome, região, zona e configuração da máquina

Próximo passo será escolher o disco de inicialização. Você poderá escolher entre imagens Windows e Linux públicas, imagens personalizadas ou snapshots de discos já existentes. Também poderá escolher os tipos de discos de inicialização e determinar o tamanho desse disco.
![](/images/imagens-disco.JPG)

Na opção de firewall, você poderá permitir se essa máquina irá receber trafego HTTP/HTTPS

Ao clicar em opções avançadas, você poderá adicionar novos discos a essa VM, onde poderá ser armazenados os dados separadamente do disco de inicialização, poderá criar chaves SSH para conexão remota, poderá criar politicas de proteção contra exclusão da VM entre outras funcionalidades.
![](/images/opcoes.JPG)

Detalhando mais um pouco as opções avançadas e clicando em rede, você poderá atribuir uma tag de rede. Essa tag poderá ser usada para configurações de regras de firewall configuradas no VPC. Assim você poderá criar uma regra e vincular a uma tag e com essa tag, definir essa regra para várias VMs. Você também poderá configurar a rede e a sub-rede a qual essa VM irá se comunicar. Conforme configurado no tópico anterior, nós utilizaremos a vpc-geral com a sub-rede subnet-geral
![](/images/interface-rede.JPG)

Ao finalizar a criação nós poderemos verificar que a máquina se encontra ativa e poderemos acessá-la ao clicar no botão SSH 

![](/images/vm-criada.JPG)
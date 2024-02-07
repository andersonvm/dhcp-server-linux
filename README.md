# dhcp-server-linux
Configuração do serviço DHCP em um servidor Linux e Windows

## Configurar um Servidor DHCP no Debian (ou Ubuntu):

### Instalar o pacote DHCP:

```
sudo apt-get update
sudo apt-get install isc-dhcp-server
```

### Configurar o DHCP:

Edite o arquivo de configuração /etc/dhcp/dhcpd.conf com um editor de texto como o nano ou vim.

```
sudo vim /etc/dhcp/dhcpd.conf
```

### Aqui está um exemplo básico de configuração para um servidor DHCP:

```
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.100;
    option routers 192.168.1.1;
    option domain-name-servers 8.8.8.8, 8.8.4.4;
}
```

subnet: Define o intervalo de endereços IP a serem atribuídos.

range: Especifica a faixa de endereços IP disponíveis.

option routers: Define o gateway padrão para os clientes.

option domain-name-servers: Define os servidores DNS para os clientes.


### Configurar a interface de rede:

Abra o arquivo /etc/default/isc-dhcp-server para definir a interface de rede onde o servidor DHCP irá escutar.


### Reiniciar o serviço DHCP:

Depois de configurar o arquivo dhcpd.conf e definir a interface de rede, reinicie o serviço DHCP:

```
sudo systemctl restart isc-dhcp-server
```

## Configurar um Servidor DHCP no CentOS:

### Instalar o pacote DHCP:

```
sudo yum install dhcp
```

### Configurar o DHCP:

Edite o arquivo de configuração /etc/dhcp/dhcpd.conf:

```
sudo vim /etc/dhcp/dhcpd.conf
```

### Aqui está um exemplo básico de configuração para um servidor DHCP:

```
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.100;
    option routers 192.168.1.1;
    option domain-name-servers 8.8.8.8, 8.8.4.4;
}
```

Configurar a interface de rede: Edite o arquivo /etc/sysconfig/dhcpd e defina a interface de rede a ser usada pelo servidor DHCP.

### Iniciar e Habilitar o Serviço DHCP:

```
sudo systemctl start dhcpd
sudo systemctl enable dhcpd
```

Certifique-se de ajustar os parâmetros de acordo com sua rede, como endereços IP, máscara de sub-rede, gateway e servidores DNS, para atender às necessidades específicas da sua configuração de rede.

## Configurar um Servidor DHCP no Windows Server

## Instalar o Serviço DHCP:

Abra o "Server Manager" no Windows Server. Selecione "Add roles and features". Escolha "DHCP Server" na lista de funções disponíveis e siga as instruções para instalá-lo.

### Configurar o Serviço DHCP:

Após a instalação, abra o "DHCP" no "Server Manager". Clique com o botão direito do mouse em "IPv4" ou "IPv6", dependendo da sua configuração de rede. Selecione "New Scope" para criar um novo escopo DHCP.

### Criar um Novo Escopo:

Siga o assistente para configurar o escopo. Isso inclui: Nome e descrição do escopo.Faixa de endereços IP a serem atribuídos aos dispositivos. Máscara de sub-rede. Gateway padrão. DNS e outros servidores de rede (se aplicável). Duração do aluguel de IP (tempo de validade da concessão).

### Configurar Opções Adicionais (Opcional):

Você pode configurar opções adicionais para o escopo, como servidores DNS, servidores WINS, etc. Isso depende das necessidades específicas da sua rede.

### Ativar o Escopo:

Certifique-se de ativar o escopo recém-criado para que o servidor DHCP comece a atribuir endereços IP.

### Autorizar o Servidor DHCP (Se Necessário):

Em um ambiente de domínio do Active Directory, o servidor DHCP precisa ser autorizado.Clique com o botão direito no servidor DHCP no "DHCP Manager" e selecione "Authorize".

### Testar a Configuração:

Conecte um dispositivo à rede e verifique se ele obtém um endereço IP automaticamente do servidor DHCP.

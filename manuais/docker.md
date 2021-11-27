# Docker 🐳

Um container é uma instância de uma imagem em execução, quando criamos um container iniciamos um ambiente isolado que vai executar aquela imagem.

<hr>

#### Imagem vs Container

- Uma imagem é o arquivo propriamente dito, como se fosse uma imagem de disco.
- Um container é uma instância daquela imagem, é a imagem sendo executada (rodando).

Apenas para ilustrar, podemos comparar isto com a máquina virtual: cada imagem é como se fosse o arquivo da máquina virtual salvo no nosso disco, e cada container é uma máquina virtual em funcionamento (rodando).

Diferente de uma máquina virtual que só pode executar uma instancia daquela máquina especifica, podemos ter varios containers usando a mesma imagem. 



Neste documento vamos usar **nome_container** para nos referir ao **nome**, o **apelido** ou o **ID** do **container** obtido usando **docker ps**.



<hr>



## Get started - Primeiros passos



#### Listando imagens locais

Para iniciarmos um container precisamos de uma imagem usando o comando abaixo podemos ver quais imagens estão disponíveis em seu repositório local.

```bash
docker images
```

> Se você acabou de instalar o docker é provável que o comando não retorne nenhuma imagem.

####  Adicionando imagens ao repositório local

Podemos baixar imagens do repositório oficial para nossa maquina, podemos acessar a página <a href="https://hub.docker.com/search">hub docker</a> ou podemos pesquisar usando o terminal.

> Neste documento vamos usar a imagem alpine, fique à vontade para escolher outra imagem se desejar.



```bash
docker search alpine
```

> Este comando irá mostras imagens disponíveis com a palavra buscada.



#### Fazendo o download da imagem

``` bash
docker pull alpine
```

Após o download podemos iniciar um novo container usando esta imagem.



#### Iniciando um container

```bash
docker run alpine
```

> Provavelmente você esta pensando que isso não fez nada mas isto criou e executou um container e finalizou.

Vamos passar alguns parâmetros para termos a linha de comando do nosso container

```bash 
docker run -it alpine /bin/sh
```

> O `-i` significa interatividade e o `-t` que queremos um link com o Terminal do container.

Podemos finalizar com ctrl + d ou digitando `exit` no terminal.



#### Esclarecendo um pouco as coisas

Cada comando `docker run` que executamos cria um novo container neste caso nós já temos 2 containers. Como assim? Vamos listar nossos containers:



#### Listando os containers

```bash
docker container list
```

Este comando é igual ao `docker ps` ele mostra todos os containers que estão em execução no momento. Se a lista estiver vazia não quer dizer que não temos nenhum container, vamos passar o parametro `-a` para listar todos os container incluindo os desligados.



#### Listando todos os containers

```bash
docker container list -a
```

> Podemos usar também `docker ps -a`, agora podemos ver todos os container que criamos.

Como posso remover os containers que não estamos usando mais?



#### Removendo um container

```bash
docker container rm container_ID
```



#### Criando conteiner autodestrutivo

Se não quisermos nos procupar em ficar removendo containers podemos passar o parâmetro `--rm` que fará com que o container seja removiao ao finalizar a seção.

```bash
docker run -it --rm alpine /bin/sh
```

> Ou seja, quando finalizarmos o container com ctrl + d ou `exit` o container será removido.



#### Salvando alterações do nosso container

```bash
docker commit nome_container nome_da_nova_imagem
```



#### Mapeando uma porta para o container

```bash
docker run -it -p 8080:80 nome_container
```

> Estamos informando que a porta 8080 no Host é aberta e deve ser mapeada na porta 80 do container.



<hr>

## Persistencia de dados

Como vimos anteriormente para mantermos as alterações em nossos containers precisamos fazer commit gerando assim uma nova imagem.

Se tratando de banco de dados isto seria inviável, sendo assim precisamos armazear nossas informações em outro lugar.

Podemos fazer isto usando volumes, que seriam algo como HDs virtuais que criamos e ficam fora de nossa imagem do container. Então iniciamos um container e adicionamos o volume para armazenar os dados, e este volume pode ser compartilhado com outros containers também. Vejamos...



#### Criando volumes no docker

```bash
docker volume create nome_volume
```



#### Iniciando o container com o volume

```bash
docker run -dp -v nome_volume:/caminho nome_imagem
```



<hr>

#### Transferência de arquivos

```bash
docker cp arquivo.txt nome_container:/arquivo.txt #Maquina Local > Container
docker cp nome_container:/arquivo.txt arquivo.txt #Container > Maquina local
```



#### Transferência de pastas

```bash
docker cp pasta/. nome_container:/destino #Maquina Local > Container
docker cp nome_container:/pasta/. destino		#Container > Maquina local
```



<hr>

## Flags

A seguir algumas das flags que podemos usar ao iniciar um container com ***container run***:

```bash
-p 8080:80 # Conecta a porta 8080 do hospedeiro com a porta 80 do container
					 # pode ser a mesma porta nos dois lados ex: 80:80
```

```bash
-v nome_volume:/caminho # Monta um volume no container definindo 
											  #	o ponto de montagem
```

<hr>





## Container criado mas não está rodando

```
docker start -ai container_idCOPIAR CÓDIGO
```

## Container criado, está rodando em background

```
docker attach container_idCOPIAR CÓDIGO
```

## Sair do container

### Parar o container

Para sair do container digite `exit` ou `CTRL+D`, neste caso o container vai ser parado.

### Deixar rodando em background

Para "desanexar" o container do seu terminal, mas mantê-lo rodando em background utilize `CTRL+P, CTRL+Q`.



# Comandos úteis para linux

Comandos úteis para quem estar iniciando com o linux. Esses comandos são para distribuições baseadas no ubuntu, uitlize-os no seu shell de preferencia.




## Documentação

- Processos
- Firewall




### Processos:

#### 1. Usando o PID (Process ID):

- Descubra o PID do processo que você deseja encerrar usando o comando ps. Por exemplo, para encontrar o PID de um processo chamado nome_do_processo:

```bash
ps aux | grep nome_do_processo

```
- Use o comando kill com o PID para encerrar o processo:

```bash
kill PID

```

#### 2. Usando pkill (por nome do processo):

- Você pode encerrar um processo diretamente pelo nome usando o pkill. Por exemplo, para encerrar um processo chamado nome_do_processo:

```bash
pkill nome_do_processo

```

#### 3. Usando killall (por nome do comando):

- Para encerrar todos os processos com um determinado nome de comando:

```
killall nome_do_comando

```
- Substitua nome_do_comando pelo nome do comando associado aos processos que você deseja encerrar.

#### 4. Encerramento forçado:

- Se o processo não responder ao kill normal, você pode usar o sinal -9 para forçar o encerramento:

```
kill -9 PID

ou

pkill -9 nome_do_processo

```
- Tenha cuidado ao usar o sinal -9, pois ele não dá ao processo a oportunidade de realizar qualquer limpeza ou desalocação de recursos.
 
#### 5. Listar todos os processos:

```
ps aux

```
- Este comando mostra uma lista detalhada de todos os processos em execução no sistema.

#### 6. Listar processos de um usuário específico:
```
ps -u nome_do_usuario
```
- Substitua "nome_do_usuario" pelo nome do usuário cujos processos você deseja visualizar.

#### 7. Listar processos de forma arborescente:
```
pstree
```
- Este comando exibe uma representação hierárquica dos processos em execução.

#### 8. Listar processos com um formato personalizado:

```
ps -eo pid,ppid,cmd
```
- Este exemplo exibe o ID do processo (`pid`), o ID do processo pai (`ppid`), e o comando (`cmd`) que está sendo executado.

#### 9. Listar os processos em tempo real (atualizando a cada segundo):

```
top
```
- O comando `top` fornece uma visão dinâmica dos processos em execução e suas estatísticas, atualizando a cada poucos segundos. Para sair do `top`, pressione `q`.

```
***Sempre que tiver duvidas utilize o nome do comando seguido de help:

ex: top help
```

### Firewall:
- Aqui algumas ferramentas para monitoramento de conexões em tempo real.

#### 1. tcpdump:
- O `tcpdump` é uma ferramenta poderosa para capturar e exibir pacotes em uma rede. Você pode usá-lo para monitorar as conexões em tempo real.

```
sudo tcpdump -i <interface_de_rede>
```
- Substitua `<interface_de_rede>` pela sua interface de rede, por exemplo, `eth0`.

#### 2. iftop:
- O `iftop` é uma ferramenta que exibe informações em tempo real sobre o uso da largura de banda em uma interface de rede.

```
sudo iftop
```
- O `iftop` também mostra informações sobre as conexões ativas.




# Comandos úteis para linux

Comandos úteis para quem está iniciando com o Linux. Esses comandos são para distribuições baseadas no Ubuntu; utilize-os no seu shell de preferência.
Esse conteudo será continuamente atualizado.




## Documentação
- [Processos](#processos)
- [Firewall](#firewall)
- [User root no terminal](#user-root-no-terminal)
- [Dicas](#dicas)
- [Erros](#erros)




## Processos:
- [Usando o PID (Process ID)](#usando-o-pid-process-id)
- [Usando pkill (por nome do processo)](#usando-pkill-por-nome-do-processo)
- [Usando killall (por nome do comando)](#usando-killall-por-nome-do-comando)
- [Encerramento forçado](#encerramento-forcado)
- [Listar todos os processos](#listar-todos-os-processos)
- [Listar processos de um usuário específico](#listar-processos-de-um-usuario-especifico)
- [Listar processos de forma arborescente](#listar-processos-de-forma-arborescente)
- [Listar processos com um formato personalizado](#listar-processos-com-um-formato-personalizado)
- [Listar os processos em tempo real (atualizando a cada segundo)](#listar-os-processos-em-tempo-real-atualizando-a-cada-segundo)

#### Usando o PID (Process ID):

- Descubra o PID do processo que você deseja encerrar usando o comando ps. Por exemplo, para encontrar o PID de um processo chamado `nome_do_processo`:

```bash
ps aux | grep nome_do_processo

```
- Use o comando `kill` com o PID para encerrar o processo:

```bash
kill PID

```

#### Usando pkill (por nome do processo):

- Você pode encerrar um processo diretamente pelo nome usando o pkill. Por exemplo, para encerrar um processo chamado `nome_do_processo`:

```bash
pkill nome_do_processo

```

#### Usando killall (por nome do comando):

- Para encerrar todos os processos com um determinado nome de comando:

```
killall nome_do_comando

```
- Substitua nome_do_comando pelo nome do comando associado aos processos que você deseja encerrar.

#### Encerramento forçado:

- Se o processo não responder ao kill normal, você pode usar o sinal -9 para forçar o encerramento:

```
kill -9 PID

ou

pkill -9 nome_do_processo

```
- Tenha cuidado ao usar o sinal -9, pois ele não dá ao processo a oportunidade de realizar qualquer limpeza ou desalocação de recursos.
 
#### Listar todos os processos:

```
ps aux

```
- Este comando mostra uma lista detalhada de todos os processos em execução no sistema.

#### Listar processos de um usuário específico:
```
ps -u nome_do_usuario
```
- Substitua "nome_do_usuario" pelo nome do usuário cujos processos você deseja visualizar.

#### Listar processos de forma arborescente:
```
pstree
```
- Este comando exibe uma representação hierárquica dos processos em execução.

#### Listar processos com um formato personalizado:

```
ps -eo pid,ppid,cmd
```
- Este exemplo exibe o ID do processo (`pid`), o ID do processo pai (`ppid`), e o comando (`cmd`) que está sendo executado.

#### Listar os processos em tempo real (atualizando a cada segundo):

```
top
```
- O comando `top` fornece uma visão dinâmica dos processos em execução e suas estatísticas, atualizando a cada poucos segundos. Para sair do `top`, pressione `q`.

```
***Sempre que tiver duvidas utilize o nome do comando seguido de help:

ex: top help
```

## Firewall:
- [tcpdump](#tcpdump)
- [iftop](#iftop)

#### tcpdump:
- O `tcpdump` é uma ferramenta poderosa para capturar e exibir pacotes em uma rede. Você pode usá-lo para monitorar as conexões em tempo real.

```
sudo tcpdump -i <interface_de_rede>
```
- Substitua `<interface_de_rede>` pela sua interface de rede, por exemplo, `eth0`.

#### iftop:
- O `iftop` é uma ferramenta que exibe informações em tempo real sobre o uso da largura de banda em uma interface de rede.

```
sudo iftop
```
- O `iftop` também mostra informações sobre as conexões ativas.

## User root no terminal
- A maneira comum de usar o usuário root no terminal é através do comando su (substitute user). Aqui estão os passos básicos:

#### 1. Abra o terminal:
- No Linux, geralmente você pode pressionar `Ctrl + Alt + T` para abrir um terminal.
- Digite o comando `su` seguido de Enter.
- Para sair do usuário root e voltar ao seu usuário normal, basta digitar o comando `exit` e pressionar Enter.
- Ao usar o usuário `root`, tenha cautela com os comandos que você executa. Comandos incorretos podem causar danos ao sistema.


## Dicas:
- [Alterar permissao de um dispositivo](#alterar-permissao-de-um-dispositivo)
- [Abrir pasta pelo terminal](#abrir-pasta-pelo-terminal)

#### - Abrir pasta pelo terminal
- Comando:
  ```
  xdg-open <folder>
  ```

#### - Alterar permissao de um dispositivo
- Para permitir que todos os usuários editem um dispositivo no Linux, você precisa ajustar as permissões desse dispositivo. Use o comando `chmod` para alterar as permissões do dispositivo. Aqui está um exemplo genérico de como você pode fazer isso:

##### 1-Identificar o dispositivo:
- Primeiro, descubra o caminho do dispositivo que você deseja editar. Isso pode ser, por exemplo, um dispositivo de bloco (como um disco rígido) ou um dispositivo de caractere (como uma impressora).

##### 2-Alterar as permissões:
- Use o comando `chmod` para alterar as permissões do dispositivo. O formato básico é:
```
sudo chmod permissões /caminho/do/dispositivo

```
- Substitua `permissões` pelos valores numéricos apropriados e `/caminho/do/dispositivo` pelo caminho real do dispositivo.

- Para permitir que todos os usuários leiam, escrevam e executem (para dispositivos de bloco, como discos rígidos):
```
sudo chmod a+rwx /caminho/do/dispositivo
```
- Para permitir que todos os usuários leiam, escrevam e executem (para dispositivos de caractere, como impressoras):
```
sudo chmod a+rw /caminho/do/dispositivo
```
- *** Se você precisar de permissões mais granulares, pode ser útil aprender sobre o uso do comando `chown` para alterar o proprietário do arquivo ou dispositivo.***
## Erros:
- [Erro de montagem de devices](#erro-de-montagem-de-devices)
#### - Erro de montagem de devices:
```
Unknown erro when mounting /dev/sdb3
```
- Tive esse erro ao tentar montar devices com arquivos ntfs. Resolvido verificando a integridade do sistema de arquivos NTFS do dispositivo. Para isso use o comando:
```
sudo ntfsfix <device>

Isso tentará corrigir possíveis problemas no sistema de arquivos NTFS.
```
- Certifique-se de ter o driver ntfs instalado. No Linux, você pode usar o `ntfs-3g` para montar partições NTFS. Se não estiver instalado, você pode instalá-lo usando o gerenciador de pacotes da sua distribuição. Por exemplo, no Ubuntu, você pode usar o seguinte comando:

```
sudo apt-get install ntfs-3g
```
- [Travamento do plasmashell](#travamento-do-plasmashell)
#### Travamento do plasmashell
```
file:///usr/share/plasma/plasmoids/org.kde.plasma.kickoff/contents/ui/KickoffListView.qml:68:18: QML ListView: possible QQuickItem::polish() loop
file:///usr/share/plasma/plasmoids/org.kde.plasma.kickoff/contents/ui/KickoffListView.qml:68:18: QML ListView: ListView called polish() inside updatePolish() of ListView
```
Use o comando: ```kquitapp5 plasmashell ``` para encerrar o processo.
Use o comando: ``` kstart5 plasmashell ```para reiniciar o processo.

Isso deve resolver o problema de loop nesses arquivos.
 

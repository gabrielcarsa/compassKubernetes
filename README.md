

## **Documentação de atividade**

### **Integrantes:**

- ****André Augusto Borges Guariento****
- ****Eduardo Chagas Pacheco****
- ****Gabriel Henrique Cardoso Dos Santos****
- **Emerson Gabriel da Silva Guimarães**

## Instruções da Atividade:


## 1 - Instalação do Docker for Windows

> **Para baixar o Docker Desktop for Windows, acesse esse link:**
> 

[https://desktop.docker.com/win/edge/46784/Docker Desktop Installer.exe](https://desktop.docker.com/win/edge/46784/Docker%20Desktop%20Installer.exe)

A versão utilizada na atividade foi a v4.11.1, após a instalação do programa finalizar, reinicie o computador e o programa aparecerá. 

Vale lembrar também que para poder realizar as alterações dos dados dos arquivos .yaml, nós utilizamos o Visual Studio + Extensão para validação dos arquivos tipo .YAML:

VSCode: [https://visualstudio.microsoft.com/pt-br/downloads/](https://visualstudio.microsoft.com/pt-br/downloads/)

Extensão YAML pela Red Hat: [https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) 

### ATENÇÃO!


*Imagem retirada do Fórum da Alura*

O que aconteceu em um dos eventos de instalação do Docker Desktop foi após a reinicialização do Sistema, constar 2 popups informando erros de Instalação do WSL 2. 

Após pesquisas no próprio Fórum da Alura e documentações, há 2 links compatíveis que resolveram diferentemente esse erro: 

[https://cursos.alura.com.br/forum/topico-wsl-2-installation-is-incomplete-182106](https://cursos.alura.com.br/forum/topico-wsl-2-installation-is-incomplete-182106)

[https://docs.microsoft.com/pt-br/windows/wsl/install](https://docs.microsoft.com/pt-br/windows/wsl/install)

Caso não tenha problemas na instalação do WSL2, prossiga na página inicial do Docker Desktop, clique no ícone de engrenagem e vá no campo “Kubernetes” Após isso, marque a caixa de seleção “Enable Kubernetes”. 

Após esse processo você finalizou a etapa de instalação do Docker Desktop.

# Versão do Linux

Para utilizar o Kubernetes no Linux, é necessário a instalação do MiniKube e Kubectl: O Minikube **é uma implementação leve do Kubernetes que cria uma VM em sua máquina local e implanta um cluster simples contendo apenas um node e Kubectl é um gerenciador de Clusters por linha de comando.** 

Após a realização da instalação, necessita-se utilizar o comando:

```docker
minikube start --driver=docker

```

Com esse comando, inicializa o Minikube com Driver de Docker.

Para verificar se o Minikube está rodando na máquina, utilize o comando:

```docker
kubectl get nodes
```

Caso apareça os nodes na listagem, a instalação foi concluída com sucesso.

## 2 - Criando um Namespace

Ao iniciar a atividade, a primeira tarefa indicada foi crumar um namespace chamado labwordpress, tudo que for feito ao longo da atividade deverá estar dentro deste namespace. 

Ao abrir o Windows Power Shell como administrador, você inicializará com o comando 

```docker
kubectl get namespace
```

O resultado será assim:

```docker
Output
NAME              STATUS   AGE
default           Active   2d21h
kube-node-lease   Active   2d21h
kube-public       Active   2d21h
kube-system       Active   2d21h
```

Para criar um namespace, use:

```docker
kubectl create namespace labwordpress
```

```docker
Output
namespace/labwordpress created
```

Para definir como padrão o namespace, pode utilizar o comando:

```docker
kubectl config set-context --current --namespace=labwordpress
```

Após isso, finalizamos o passo inicial. 

## 3 - Faça a apply do arquivo de service do MySQL

Dentro desse passo, nós conseguimos adiantar todo o processo com o auxílio da documentação oficial do Kubernetes: 

[https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/](https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/)

Baixamos os 2 arquivos fornecido pelo site do Kubernetes de MySQL e Wordpress, realizamos as alterações devidas como mudança do Port do SQL, adição do nome de Volume Storage para ambos serviços. 

Após isso, criamos o arquivo *kustomization*.yaml, baseado com as informações fornecidas pelo próprio site e o resultado foi: 

```yaml
secretGenerator:
- name: mysql-pass
  literals:
  - password=Emerson@300598
resources:
  - ./mysql-deployment.yaml
  - ./wordpress-deployment.yaml
```

> Exemplo de um arquivo criado por um dos integrantes.
> 

Após esse processo, juntamos todos os arquivos e criamos uma pasta dentro de outra chamada .kube, para a realização do processo de apply dentro do Power Shell.

Após acessar o Power Shell e se direcionar até a pasta criada, utilizamos o comando:

```docker
kubectl apply -k ./
```

Após isso a mensagem de confirmação de aplicação, utilizamos os seguintes códigos:

```docker
kubectl get pods 
```

```docker
kubectl get pvc
```

```docker
kubectl get service
```

Após a confirmação das informações, testamos o serviço pelo navegador utilizando o “localhost:80” e conseguimos acessar a página do Wordpress. 


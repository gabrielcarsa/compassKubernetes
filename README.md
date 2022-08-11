# Atividade 5 - PB Compass - DevSecOps **💻**

![servlet.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9d04074f-a9fb-4750-8449-b5e519da962d/servlet.png)

## **Documentação de atividade**

### **Integrantes:**

- ****André Augusto Borges Guariento****
- ****Eduardo Chagas Pacheco****
- ****Gabriel Henrique Cardoso Dos Santos****
- **Emerson Gabriel da Silva Guimarães**

## Instruções da Atividade:

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/953ec119-e95c-4cb6-ae13-07de40b9d311/Untitled.png)

## 1 - Instalação do Docker for Windows

> **Para baixar o Docker Desktop for Windows, acesse esse link:**
> 

[https://desktop.docker.com/win/edge/46784/Docker Desktop Installer.exe](https://desktop.docker.com/win/edge/46784/Docker%20Desktop%20Installer.exe)

A versão utilizada na atividade foi a v4.11.1, após a instalação do programa finalizar, reinicie o computador e o programa aparecerá. 

### ATENÇÃO!

![cf664b5a-43b3-416b-b52c-cc8e0bc306df.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dcc3fead-e7a4-4f62-b9e7-062dcd55f8ac/cf664b5a-43b3-416b-b52c-cc8e0bc306df.png)

*Imagem retirada do Fórum da Alura*

O que aconteceu em um dos eventos de instalação do Docker Desktop foi após a reinicialização do Sistema, constar 2 popups informando erros de Instalação do WSL 2. 

Após pesquisas no próprio Fórum da Alura e documentações, há 2 links compatíveis que resolveram diferentemente esse erro: 

[https://cursos.alura.com.br/forum/topico-wsl-2-installation-is-incomplete-182106](https://cursos.alura.com.br/forum/topico-wsl-2-installation-is-incomplete-182106)

[https://docs.microsoft.com/pt-br/windows/wsl/install](https://docs.microsoft.com/pt-br/windows/wsl/install)

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

# Ace4 ERP

Repositório orquestrador do ERP Ace4.

Este projeto utiliza **Git Submodules** para organizar:
- Aplicação principal
- Módulos funcionais
- Bibliotecas compartilhadas

##Estrutura do proejto atual:
````
Ace4_ERP/
├─ .gitmodules
├─ README.md
└─ src/
   ├─ Main/
   ├─ Lib/
   └─ Modulos/
    └─ FIN
    └─ SRV
````

## ✅ ETAPA 1 – Clonando todo Projeto (caso ainda não tenha o projeto na maquina)

````
git clone --recurse-submodules https://github.com/Ace4Vitor/Ace4_ERP.git
````
### Se já clonou mas não trouxe os submódulos:

````
git submodule update --init --recursive
````

## ✅ ETAPA 2 – Antes de alterar: atualizar o módulo

### ⚠️ Regra obrigatória: Sempre atualizar o submódulo antes de começar qualquer alteração.

### 2.1 Entrar no módulo
````
cd src/Modulos/FIN
````

###2.2 Verificar branch
````
git branch
````

Se necessário:
````
git checkout develop
````

(ou a branch padrão usada pela equipe)

### 2.3 Atualizar o módulo
````
git pull origin develop
````

Agora o módulo está atualizado.

### 2.4 Voltar para o projeto principal
````
cd ../../..
````

### 2.5 Atualizar referência do submódulo no projeto pai
````
git submodule update --remote --merge
````


ou, se quiser garantir:
````
git add src/Modulos/FIN
git commit -m "Atualiza referência do módulo FIN"
````


## ✅ ETAPA 3 – Criar branch para alteração (boa prática)
````
cd src/Modulos/FIN
git checkout -b feature/ajuste-financeiro
````

## ✅ ETAPA 4 – Fazer a alteração
Editar:
````
FinanceiroService.pas
````

Depois:
````
git status
````

Adicionar alteração:
````
git add Classes/FinanceiroService.pas
````

Commitar:
````
git commit -m "Ajuste regra de cálculo de juros"
````

## ✅ ETAPA 5 – Publicar alteração do módulo

Ainda dentro do módulo:
````
git push origin feature/ajuste-financeiro
````

Ou, se estiver direto na develop:
````
git push origin develop
````
## ✅ ETAPA 6 – Atualizar o projeto principal (MUITO IMPORTANTE)

Voltar para o projeto principal:
````
cd ../../..
````

Agora o Git vai perceber que o submódulo mudou de commit.
````
git status
````

Você verá algo assim:
````
modified: src/Modulos/FIN (new commits)
````
### Confirmar a nova referência do módulo
````
git add src/Modulos/FIN
git commit -m "Atualiza submódulo FIN após ajuste de juros"
git push origin develop
````

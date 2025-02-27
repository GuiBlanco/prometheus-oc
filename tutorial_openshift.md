# Tutorial para Subir o Pod no OpenShift

Este tutorial fornece instruções passo a passo para subir um pod utilizando a imagem `vendor/docker/portworx/prometheus:v3.1.0` no OpenShift.

## Passo 1: Criar o Persistent Volume Claim (PVC)

Execute o seguinte comando para criar o PVC:

```bash
oc apply -f pvc.yaml
```

## Passo 2: Criar o Deployment

Execute o seguinte comando para criar o deployment:

```bash
oc apply -f deployment.yaml
```

## Passo 3: Criar o Serviço

Execute o seguinte comando para criar o serviço:

```bash
oc apply -f service.yaml
```

## Passo 4: Criar a Rota

Execute o seguinte comando para criar a rota:

```bash
oc apply -f route.yaml
```

## Passo 5: Acessar o Prometheus

Após a criação da rota, você pode acessar o Prometheus através da URL fornecida pela rota. Use o seguinte comando para obter a URL:

```bash
oc get routes
```

## Configuração de RBAC

Para restringir o acesso ao serviço do Prometheus, você pode configurar o controle de acesso baseado em funções (RBAC) no OpenShift. Siga os passos abaixo:

### Para um único usuário:

1. **Criar um RoleBinding**: Execute o seguinte comando para vincular o papel a um único usuário:

```bash
oc apply -f prometheus-rolebinding-single.yaml
```

Certifique-se de substituir `<USERNAME>` no arquivo `prometheus-rolebinding-single.yaml` pelo nome do usuário que deve ter acesso.

### Para múltiplos usuários:

1. **Criar um RoleBinding**: Execute o seguinte comando para vincular o papel a múltiplos usuários:

```bash
oc apply -f prometheus-rolebinding-multiple.yaml
```

## Conclusão

Agora você deve ter o Prometheus rodando no seu cluster OpenShift. Para verificar se tudo está funcionando corretamente, você pode acessar a interface do Prometheus através da URL obtida na etapa 5.

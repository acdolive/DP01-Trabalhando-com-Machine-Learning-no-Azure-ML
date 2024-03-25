# Trabalhando com Machine Learning no Azure ML

O objetivo deste desafio é a criação de um modelo preditivo utilizando o recurso de aprendizado de máquina automatizado do Azure.
Para isso será necessário seguir algumas etapas, vejamos:

# 💻 Criação de Workspace no Azure

Para usar o Azure ML você precisa ter um workspace, caso ainda não tenha,seguir os passos abaixo:   

1. Entre no portal do Azure. https://portal.azure.com
2. Selecione "+ Criar um recurso", procure Aprendizado de Máquina e crie um novo recurso de Aprendizado de Máquina do Azure com as seguintes configurações:
    * Assinatura: sua assinatura do Azure.
    * Grupo de recursos: crie ou selecione um grupo de recursos.
    * Nome: insira um nome exclusivo para seu espaço de trabalho.
    * Região: Selecione a região geográfica mais próxima.
    * Conta de armazenamento: observe a nova conta de armazenamento padrão que será criada para seu espaço de trabalho.
    * Cofre de chaves: observe o novo cofre de chaves padrão que será criado para seu espaço de trabalho.
    * Application insights: observe o novo recurso padrão de insights de aplicativo que será criado para seu espaço de trabalho.
    * Registro de contêiner: Nenhum (um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner).

3. Selecione Revisar + criar e, em seguida, selecione Criar. Aguarde até que seu espaço de trabalho seja criado (pode levar alguns minutos) e vá para o recurso implantado.
4. Selecione Iniciar estúdio (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no estúdio do Aprendizado de Máquina do Azure usando sua conta da Microsoft). Feche todas as mensagens exibidas.
5. No estúdio de Aprendizado de Máquina do Azure, você deve ver seu espaço de trabalho recém-criado. Caso contrário, selecione Todos os espaços de trabalho no menu à esquerda e, em seguida, selecione o espaço de trabalho que você acabou de criar.

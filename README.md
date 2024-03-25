# Trabalhando com Machine Learning no Azure ML

O objetivo deste desafio é a criação de um modelo preditivo utilizando o recurso de aprendizado de máquina automatizado do Azure.
Para isso será necessário seguir algumas etapas, vejamos:

# 💻 Criação de Workspace no Azure

Para acessar o Azure ML você precisa ter um workspace, caso ainda não tenha,seguir os passos abaixo:   

1. Entre no portal do Azure. https://portal.azure.com
2. Selecione "+ Criar um recurso"

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/53698bc7-7abb-45c9-b22e-68147c7c6f3e)

3. Procure "Azure Machine Learning" e crie um novo recurso de Aprendizado de Máquina do Azure com as seguintes configurações:
    * Assinatura: sua assinatura do Azure.
    * Grupo de recursos: crie ou selecione um grupo de recursos. Ex.: Lab-AI900
    * Nome: insira um nome exclusivo para seu espaço de trabalho
    * Região: Selecione a região geográfica
    * Conta de armazenamento: criação automática
    * Cofre de chaves: criação automática
    * Application insights: criação automática
    * Registro de contêiner: Nenhum (um será criado automaticamente na primeira vez que você implantar um modelo em um contêiner).
    
![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/76612c07-860c-41f6-a756-76eb1a9d2c1d)

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/abb927e2-a768-4d7e-ab0e-71692cb38966)

4. Selecione Revisar + criar e, em seguida, selecione Criar. Aguarde até que seu espaço de trabalho seja criado (pode levar alguns minutos) e vá para o recurso implantado.

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/d15d8fcd-af44-4ea8-86c8-6aeaff18ba2e)

5. Selecione "Iniciar estúdio" (ou abra uma nova guia do navegador e navegue até https://ml.azure.com e entre no estúdio do Aprendizado de Máquina do Azure usando sua conta da Microsoft). Feche todas as mensagens exibidas.

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/83452044-b67f-43ae-a492-39ac35769c8e)

6. No estúdio Azure ML, você deve ver seu espaço de trabalho recém-criado. Caso contrário, selecione Todos os espaços de trabalho no menu à esquerda e, em seguida, selecione o espaço de trabalho que você acabou de criar.

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/de550023-4dcc-4172-bdca-c60b035f995d)

# 📈 Utilizando o Azure ML automatizado para treinar um modelo

Neste desafio vamos utilizar um conjunto de dados pre-existentes com detalhes históricos de aluguel de bicicletas para treinar um modelo que prevê o número de aluguéis de bicicletas que devem ser esperados em um determinado dia, com base em características sazonais e meteorológicas.
1. No estúdio de Aprendizado de Máquina do Azure, exiba a página ML automatizada (em Criação).

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/d79145f4-3521-437f-aee2-ef6ebf62c4b4)

2.Crie um novo trabalho de ML automatizado com as seguintes configurações, usando Avançar conforme necessário para progredir pela interface do usuário:

   * Configurações básicas:
      * Nome do trabalho: mslearn-bike-automl
      * Novo nome do experimento: mslearn-bike-rental
      * Descrição: Aprendizado de máquina automatizado para previsão de aluguel de bicicletas
      * Tags: nenhuma

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/a5b5f052-413f-474b-aa28-299ad02651e1)

   * Tipo de tarefa (task) e data:
      * Selecionar tipo de tarefa: Regressão
    
![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/f1900f28-82b3-4e7a-91ee-cd933670631d)
       
3. Selecionar conjunto de dados: crie um novo conjunto de dados com as seguintes configurações:
   * Tipo de dados:
      * Nome: bike-rentals
      * Descrição: Dados históricos de aluguer de bicicletas
      * Tipo: Tabular

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/f10981c7-330f-4731-95e2-5fff28dee24c)

4. Fonte de dados:
   *Selecionar de arquivos da Web

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/887e2525-a7fc-408c-8f6c-eca62e80f916)

   *URL da Web:
      * URL da Web: https://aka.ms/bike-rentals

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/a93915c5-5ce4-4766-9ce5-334afacdbadb)
      
Ignorar validação de dados: não selecione
Configurações:
Formato de arquivo: Delimitado
Delimitador: Vírgula
Codificação: UTF-8
Cabeçalhos de coluna: Somente o primeiro arquivo tem cabeçalhos
Pular linhas: Nenhum
O conjunto de dados contém dados de várias linhas: não selecione
Esquema:
Incluir todas as colunas diferentes de Caminho
Revisar os tipos detectados automaticamente
Selecione Criar. Depois que o conjunto de dados for criado, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

Configurações da tarefa:

Tipo de tarefa: Regressão
Conjunto de dados: aluguel de bicicletas
Coluna de destino: Aluguéis (inteiro)
Definições de configuração adicionais:
Métrica primária: Erro quadrático médio da raiz normalizada
Explicar melhor modelo: Não selecionado
Use todos os modelos suportados: Nãoselecionado. Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
Modelos permitidos: selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o maior número possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.
Limites: expanda esta seção
Máximo de tentativas: 3
Máximo de tentativas simultâneas: 3
Nós máximos: 3
Limiar de pontuação métrica: 0,085 (de modo que, se um modelo atingir uma pontuação métrica quadrática média normalizada de 0,085 ou menos, o trabalho termina.)
Tempo limite: 15
Tempo limite de iteração: 15
Habilitar rescisão antecipada: Selecionado
Validação e teste:
Tipo de validação: Divisão de validação de trem
Porcentagem de dados de validação: 10
Conjunto de dados de teste: Nenhum
Computação:

Selecione o tipo de computação: Serverless
Tipo de máquina virtual: CPU
Camada de máquina virtual: Dedicado
Tamanho da máquina virtual: Standard_DS3_V2*
Número de instâncias: 1
* Se sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível.

Envie o trabalho de treinamento. Ele começa automaticamente.

Aguarde a conclusão do trabalho. Pode demorar um pouco – agora pode ser um bom momento para uma pausa para o café!


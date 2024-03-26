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
      *Ignorar validação de dados: não selecione

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/a93915c5-5ce4-4766-9ce5-334afacdbadb)
      
5. Configurações:
      * Formato de arquivo: Delimitado
      * Delimitador: Vírgula
      * Codificação: UTF-8
      * Cabeçalhos de coluna: Somente o primeiro arquivo tem cabeçalhos
      * Pular linhas: Nenhum
      * O conjunto de dados contém dados de várias linhas: não selecione

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/862666ec-c4ec-41d6-be7a-f9efe73cef4e)

6. Esquema:
      * Incluir todas as colunas diferentes de Caminho
      * Revisar os tipos detectados automaticamente
      * Selecione Criar. Depois que o conjunto de dados for criado, selecione o conjunto de dados de aluguel de bicicletas para continuar a enviar o trabalho de ML automatizado.

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/c4c4671d-963d-410e-8ecd-47d2e42192f8)

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/705483ed-1066-4da4-b512-4c6eac999a1c)

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/0a118fb4-82d5-4bae-b866-782752618b53)


7. Configurações da tarefa:

      * Tipo de tarefa: Regressão
      * Conjunto de dados: aluguel de bicicletas
      * Coluna de destino: Aluguéis (inteiro)
      * Definições de configuração adicionais:
      * Métrica primária: Erro quadrático médio da raiz normalizada
      * Explicar melhor modelo: Não selecionado
      * Use todos os modelos suportados: Nãoselecionado. Você restringirá o trabalho para tentar apenas alguns algoritmos específicos.
      * Modelos permitidos: selecione apenas RandomForest e LightGBM — normalmente você gostaria de tentar o maior número possível, mas cada modelo adicionado aumenta o tempo necessário para executar o trabalho.
      
![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/e7d6562f-e88a-441b-9dfd-02b710e023c1)

* Limites: expanda esta seção
      * Máximo de tentativas: 3
      * Máximo de tentativas simultâneas: 3
      * Nós máximos: 3
      * Limiar de pontuação métrica: 0,085 (de modo que, se um modelo atingir uma pontuação métrica quadrática média normalizada de 0,085 ou menos, o trabalho termina.)
      * Tempo limite: 15
      * Tempo limite de iteração: 15
      * Habilitar rescisão antecipada: Selecionado

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/36f2f669-4b3c-409e-b7d0-d29994ba6f18)

8. Validação e teste:
      * Tipo de validação: Divisão de validação de trem
      * Porcentagem de dados de validação: 10
      * Conjunto de dados de teste: Nenhum

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/ec8760b0-924d-4554-be7b-fd1b2d5bf904)


9. Envio do trabalho 
      * Selecione o tipo de computação: Serverless
      * Tipo de máquina virtual: CPU
      * Camada de máquina virtual: Dedicado
      *   Tamanho da máquina virtual: Standard_DS3_V2¹
      *Número de instâncias: 1

¹Se sua assinatura restringir os tamanhos de VM disponíveis para você, escolha qualquer tamanho disponível.

Envie o trabalho de treinamento. Ele começa automaticamente.

Aguarde a conclusão do trabalho. Pode demorar um pouco.

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/ec3bf680-b8f7-463e-9bf1-f55c19202114)

Quando o trabalho de aprendizado de máquina automatizado for concluído, você poderá revisar o melhor modelo treinado.

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/23582234-766b-4aef-af15-774d218a4e02)

Na guia Visão geral do trabalho de aprendizado de máquina automatizado, observe o melhor resumo do modelo.

Selecione o texto em Nome do algoritmo para o melhor modelo para exibir seus detalhes.
![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/82780641-eb9f-4554-8344-c29683690ace)

Selecione a guia Métricas e selecione os gráficos de resíduos e predicted_true se ainda não estiverem selecionados.
![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/a12f56df-1d2d-42c0-9b21-9f4e8a49ebb9)

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/575ed0f9-131c-431d-8e5d-e69ce601e338)

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/88d3f5c0-b30f-4ce3-bbea-78add71e9618)

10. Analise os gráficos que mostram o desempenho do modelo. O gráfico de resíduos mostra os resíduos (as diferenças entre os valores previstos e reais) como um histograma. O gráfico predicted_true compara os valores previstos com os valores verdadeiros.

# ✅ Implantar Modelo de Teste 

Na guia Modelo para obter o melhor modelo treinado pelo seu trabalho de aprendizado de máquina automatizado, selecione Implantar e usar a opção Serviço Web para implantar o modelo com as seguintes configurações:
      * Nome: predict-rentals
      * Descrição: Prever aluguéis de ciclos
      * Tipo de computação: Instância de Contêiner do Azure
      * Habilitar autenticação: Selecionado

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/496b05a3-f86f-4095-965e-247ed17e92a3)

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/b8e70ccf-c78f-4324-86a9-96ad54903435)

Aguarde o início da implantação, isso pode levar alguns segundos. O status de implantação para o ponto de extremidade de aluguel de previsão será indicado na parte principal da página como "Em execução".
Aguarde até que o status "Implantar" seja alterado para "Bem-sucedido". Isso pode levar de 5 a 10 minutos.

#🔎 Testar Modelo

Agora você pode testar seu serviço implantado.
No estúdio do Aprendizado de Máquina do Azure, no menu à esquerda, selecione Pontos de extremidade e abra o ponto de extremidade em tempo real de aluguéis de previsão.
![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/a7741cbb-0a59-405b-9d99-e6079b9e0e2a)

Na página de ponto de extremidade em tempo real de aluguéis de previsão, exiba a guia Teste.

No painel Dados de entrada para testar o ponto de extremidade, substitua o modelo JSON pelos seguintes dados de entrada:

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/8d31373c-73a5-4fe7-836c-f320701b6778)

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/ceae2575-9f19-4785-b393-c24ed2502193)

Clique no botão Testar.

Analise os resultados do teste, que incluem um número previsto de aluguéis com base nos recursos de entrada - semelhante a este:
![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/79d1531d-b316-4bac-a5b9-f9c695d12758)

Vamos rever o que você fez. Você usou um conjunto de dados de dados históricos de aluguel de bicicletas para treinar um modelo. O modelo prevê o número de aluguéis de bicicletas esperados em um determinado dia, com base em características sazonais e meteorológicas.

# 🧹Limpeza

O serviço Web que você criou está hospedado em uma Instância de Contêiner do Azure. Se você não pretende experimentá-lo mais, exclua o ponto de extremidade para evitar o uso desnecessário do Azure.

No estúdio do Aprendizado de Máquina do Azure, na guia Pontos de extremidade, selecione o ponto de extremidade de aluguel de previsão. Em seguida, selecione Excluir e confirme que deseja excluir o ponto de extremidade.

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/d182f5d3-8bf6-4708-839e-0f4d1b93d67a)

A exclusão da computação garante que sua assinatura não será cobrada por recursos de computação. No entanto, será cobrado um pequeno valor pelo armazenamento de dados, desde que o espaço de trabalho do Aprendizado de Máquina do Azure exista em sua assinatura. Se você tiver terminado de explorar o Aprendizado de Máquina do Azure, poderá excluir o espaço de trabalho do Aprendizado de Máquina do Azure e os recursos associados.

Para excluir seu espaço de trabalho:

No portal do Azure, na página Grupos de recursos, abra o grupo de recursos especificado ao criar seu espaço de trabalho do Aprendizado de Máquina do Azure.
Clique em Excluir grupo de recursos, digite o nome do grupo de recursos para confirmar que deseja excluí-lo e selecione Excluir.

![image](https://github.com/acdolive/DP01-Trabalhando-com-Machine-Learning-no-Azure-ML/assets/162451624/200af141-275e-43ea-aa35-ecea0f45f10d)





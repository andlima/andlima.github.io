<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. Princípios de Modelagem Preditiva</a></li>
<li><a href="#sec-2">2. Geral</a>
<ul>
<li><a href="#sec-2-1">2.1. "Todos os modelos são errados; alguns são úteis"</a></li>
<li><a href="#sec-2-2">2.2. Tenha clareza sobre as premissas do modelo</a></li>
<li><a href="#sec-2-3">2.3. Considere o trade-off acurácia vs interpretabilidade</a></li>
<li><a href="#sec-2-4">2.4. Não misture dados de treino e teste</a></li>
<li><a href="#sec-2-5">2.5. Entenda como o modelo associa o input à previsão</a></li>
<li><a href="#sec-2-6">2.6. Combine diferentes modelos usando técnicas de ensemble</a></li>
</ul>
</li>
<li><a href="#sec-3">3. Etapas do Processo CRISP-DM</a>
<ul>
<li><a href="#sec-3-1">3.1. Business Understanding (entendimento do negócio)</a>
<ul>
<li><a href="#sec-3-1-1">3.1.1. Comece pela pergunta de negócio</a></li>
<li><a href="#sec-3-1-2">3.1.2. Estabeleça uma métrica de desempenho adequada</a></li>
<li><a href="#sec-3-1-3">3.1.3. Avalie granularidade e periodicidade adequadas para o problema</a></li>
<li><a href="#sec-3-1-4">3.1.4. Entenda e comunique o que é viável conseguir de acurácia</a></li>
<li><a href="#sec-3-1-5">3.1.5. Entenda qual é a acurácia mínima para que o modelo traga valor</a></li>
<li><a href="#sec-3-1-6">3.1.6. Estebeleça quão importante é a explicabilidade do modelo</a></li>
<li><a href="#sec-3-1-7">3.1.7. Entenda a estabilidade do fenômeno a ser previsto</a></li>
<li><a href="#sec-3-1-8">3.1.8. Levante hipóteses de negócio</a></li>
</ul>
</li>
<li><a href="#sec-3-2">3.2. Data Understanding (entendimento dos dados)</a>
<ul>
<li><a href="#sec-3-2-1">3.2.1. Organize os metadados dos dados crus em um documento dinâmico</a></li>
<li><a href="#sec-3-2-2">3.2.2. Entenda se o volume de dados é suficiente para o problema</a></li>
<li><a href="#sec-3-2-3">3.2.3. Questione a qualidade dos dados</a></li>
<li><a href="#sec-3-2-4">3.2.4. Confirme o entendimento do negócio através dos dados</a></li>
</ul>
</li>
<li><a href="#sec-3-3">3.3. Data Preparation (preparação dos dados)</a>
<ul>
<li><a href="#sec-3-3-1">3.3.1. Automatize o tratamento dos dados</a></li>
<li><a href="#sec-3-3-2">3.3.2. Automatize uma validação técnica do dados</a></li>
<li><a href="#sec-3-3-3">3.3.3. Valide o dataset final com visão de negócio</a></li>
<li><a href="#sec-3-3-4">3.3.4. Organize os metadados do dataset final em um documento dinâmico</a></li>
</ul>
</li>
<li><a href="#sec-3-4">3.4. Modeling (modelagem)</a>
<ul>
<li><a href="#sec-3-4-1">3.4.1. Estabeleça uma boa variável-resposta</a></li>
<li><a href="#sec-3-4-2">3.4.2. Defina o tamanho dos dados de teste com critério</a></li>
<li><a href="#sec-3-4-3">3.4.3. Dados de teste devem seguir a distribuição de produção</a></li>
<li><a href="#sec-3-4-4">3.4.4. Foque em uma métrica única para calibração do modelo</a></li>
<li><a href="#sec-3-4-5">3.4.5. Comece com um modelo simplificado e evolua com critério</a></li>
<li><a href="#sec-3-4-6">3.4.6. Refine o modelo de maneira estratégica</a></li>
</ul>
</li>
<li><a href="#sec-3-5">3.5. Evaluation (validação de negócio)</a>
<ul>
<li><a href="#sec-3-5-1">3.5.1. Evolua analiticamente a modelagem</a></li>
<li><a href="#sec-3-5-2">3.5.2. Valide os resultados do modelo com visão de negócio</a></li>
</ul>
</li>
<li><a href="#sec-3-6">3.6. Deployment (implantação ou entrega)</a>
<ul>
<li><a href="#sec-3-6-1">3.6.1. Automatize uma validação técnica da saída do modelo</a></li>
<li><a href="#sec-3-6-2">3.6.2. Faça log do processo de predição em produção</a></li>
<li><a href="#sec-3-6-3">3.6.3. Armazene o input utilizado para predição em produção</a></li>
<li><a href="#sec-3-6-4">3.6.4. Versione o modelo disponível em produção</a></li>
</ul>
</li>
</ul>
</li>
<li><a href="#sec-4">4. Obrigado!</a></li>
</ul>
</div>
</div>

Por [André Lima](https://www.linkedin.com/in/andlima/), em 2020-02-01

# Princípios de Modelagem Preditiva<a id="sec-1" name="sec-1"></a>

Este documento apresenta um conjunto de princípios que entendo que
ajudam a direcionar a **construção de um modelo preditivo** para
problemas reais. Ele é fruto da minha experiência fazendo ciência de
dados (principalmente machine learning), trabalhando em consultoria
para diferentes indústrias, então naturalmente carrega um pouco dessa
perspectiva.

Na primeira seção estão os princípios mais gerais; em seguida, outros
que segmentei pelas etapas do [CRISP-DM](https://pt.wikipedia.org/wiki/Cross_Industry_Standard_Process_for_Data_Mining). A ideia aqui não é propor uma
metodologia ou plano de trabalho. Apenas me baseei no **propósito
principal** de cada etapa para organizar os princípios.

Cada princípio é apresentado **de maneira direta, como uma
recomendação**. Em seguida, vem uma fundamentação **sucinta da sua
importância**. Tive inspiração na concepção de princípios do [Ray Dalio](https://www.principles.com/)
e no estilo do livro [Effective C++](https://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876).

# Geral<a id="sec-2" name="sec-2"></a>

## ["Todos os modelos são errados; alguns são úteis"](https://en.wikipedia.org/wiki/All_models_are_wrong)<a id="sec-2-1" name="sec-2-1"></a>

-   Um modelo é uma simplificação da realidade
-   É necessário conviver com algum grau de erro
-   Importante mensurar a incerteza do modelo
-   A acurácia do modelo deveria ser avaliada frente às alternativas,
    não a um ideal inexistente
-   A utilidade do modelo vem do valor que ele traz ao negócio

## Tenha clareza sobre as premissas do modelo<a id="sec-2-2" name="sec-2-2"></a>

-   Quais são as premissas?
-   Quão sólidas elas são?
-   Se elas falharem, o quanto modelo é impactado?

## Considere o trade-off acurácia vs interpretabilidade<a id="sec-2-3" name="sec-2-3"></a>

-   Acurácia aqui é uma medida de quão pequeno é o erro que se espera
    numa predição do modelo
-   Interpretabilidade é a facilidade de entender como a predição é
    feita
-   Existem modelos complexos, com pouca transparência no mecanismo de
    predição
-   Por vezes, modelos mais complexos conseguem trazer maior acurácia
-   Em princípio, a interpretabilidade pode ficar prejudicada
-   Pode-se tentar quebrar a caixa-preta com técnicas como SHAP ou LIME
    -   Isso é mais complicado e envolve mais esforço

## Não misture dados de treino e teste<a id="sec-2-4" name="sec-2-4"></a>

-   Overfitting: quando um modelo se ajusta de maneira otimista aos
    dados de treino
-   Testar o modelo em dados não treinados permite detectar overfitting
-   Calibrar uma diversidade de modelos e hiperparâmetros nos mesmos
    dados de validação também pode causar overfitting
-   É importante ter dados separados (test set) que não serão utilizados
    na calibração automática

## Entenda como o modelo associa o input à previsão<a id="sec-2-5" name="sec-2-5"></a>

-   O modelo e as variáveis devem estar relacionados ao fenômeno que se
    deseja predizer
-   As variáveis de entrada devem ser compatíveis com a natureza do
    modelo

## Combine diferentes modelos usando técnicas de ensemble<a id="sec-2-6" name="sec-2-6"></a>

-   Modelos estruturalmente diferentes por vezes capturam nuances
    diferentes do fenômeno
-   Técnicas de ensemble explorar isso, combinando modelos distintos
    para gerar a previsão final
-   Isso costuma trazer resultados mais robustos, pois a fragilidade de
    um modelo específico é compensada pelos demais

# Etapas do Processo CRISP-DM<a id="sec-3" name="sec-3"></a>

## Business Understanding (entendimento do negócio)<a id="sec-3-1" name="sec-3-1"></a>

### Comece pela pergunta de negócio<a id="sec-3-1-1" name="sec-3-1-1"></a>

-   Não adianta resolver muito bem o problema errado!
-   Entenda o contexto:
    -   Pessoas (perfil, capacidades, hierarquia)
    -   Empresa (cultura, produtos)
    -   Indústria (indicadores, concorrência)
-   Delimite o problema como uma **pergunta de negócio** clara
-   Prioridade: entenda o que é mais ou menos importante

### Estabeleça uma métrica de desempenho adequada<a id="sec-3-1-2" name="sec-3-1-2"></a>

-   A métrica deve refletir a necessidade real do negócio
-   Otimizar uma métrica errada é um desperdício
-   A métrica do treinamento dos modelos não precisa ser igual à métrica
    de dev e teste
    -   A métrica de treinamento deve ajudar a encontrar modelos melhores,
        que capturem melhor fenômeno (ex.: mean squared error,
        cross-entropy)
    -   A métrica de validação/teste deve ajudar a verificar se o modelo
        tem um bom desempenho em dados reais (ex.: MAPE, F1-score)

### Avalie granularidade e periodicidade adequadas para o problema<a id="sec-3-1-3" name="sec-3-1-3"></a>

-   Qual é a agregação mais adequada para resolver o problema de
    negócio?
    -   Tempo: em séries temporais, frequência diária, semanal ou mensal?
    -   Localidade: loja, centro de distribuição, cidade, UF, país?
    -   Hierarquia: SKU, categoria, família de produto?
-   Em geral, com maior agregação é mais fácil prever
-   O importante é se adequar à necessidade do negócio

### Entenda e comunique o que é viável conseguir de acurácia<a id="sec-3-1-4" name="sec-3-1-4"></a>

-   Fenômenos mais difíceis de prever devem ter erros maiores
-   Os dados disponíveis (volume e qualidade) impactam o desempenho
-   A acurácia deve ser avaliada considerando as alternativas
    -   São conhecidos modelos satisfatórios para o fenômeno?
-   Gerencie a expectativa: perfis menos analíticos podem ter
    expectativas irreais do que é possível fazer

### Entenda qual é a acurácia mínima para que o modelo traga valor<a id="sec-3-1-5" name="sec-3-1-5"></a>

-   Um erro muito grande pode inviabilizar a solução do problema de
    negócio
-   Quanto de acurácia é suficiente para que o modelo seja útil?
-   Qual é o impacto de errar a previsão?
-   Regressão: faz diferença errar para mais ou para menos?
-   Classificação: é pior um falso positivo ou um falso negativo?

### Estebeleça quão importante é a explicabilidade do modelo<a id="sec-3-1-6" name="sec-3-1-6"></a>

-   A criticidade de um modelo explicável depende do problema de negócio
    -   "Detectar o rosto de uma pessoa em fotos de redes sociais"
    -   "Predizer a propensão de inadimplência numa solicitação de crédito"
-   Entender o mecanismo da predição é importante para a solução procurada?
    -   Existem preocupações éticas ou legais relevantes?
    -   O objetivo é dar suporte a um ser humano na decisão?
-   Que tipo de explicabilidade é importante?
    -   Quais são as variáveis importantes para o modelo
    -   Quantificar quanto cada variável é relevante?
    -   É importante ter explicações no nível de item predito?

### Entenda a estabilidade do fenômeno a ser previsto<a id="sec-3-1-7" name="sec-3-1-7"></a>

-   Existem questões comportamentais envolvidas no fenômeno?
-   Existem questões econômicas envolvidas no fenômeno?
-   A introdução do modelo impacta o comportamento futuro?
    -   Ex.: detectar melhor fraudes pode causar mudança no perfil dos
        fraudadores
-   Modelos para fenômenos mais instáveis podem perder a validade mais
    rapidamente
    -   A solução deveria contemplar um monitoramento do desempenho do modelo

### Levante hipóteses de negócio<a id="sec-3-1-8" name="sec-3-1-8"></a>

-   Levante hipóteses importantes para o negócio
    -   O que é relevante e conhecido, para **validar** junto aos dados?
    -   O que é relevante e desconhecido, para **aprender** com os dados?
-   Formalize as hipóteses para posteriormente testá-las com os dados
-   Isso ajuda a definir melhor o problema a ser atacado
-   Também é ajuda a validar se os dados estão bons

## Data Understanding (entendimento dos dados)<a id="sec-3-2" name="sec-3-2"></a>

### Organize os metadados dos dados crus em um documento dinâmico<a id="sec-3-2-1" name="sec-3-2-1"></a>

-   Relacione as fontes de dados crus, explicitando os metadados de cada
    tabela de interesse
-   Mantenha um documento de referência a ser atualizado sempre que
    houver mudanças
-   Em caso de uma equipe, é bom ter alguém específico que responda pela
    sua confiabilidade (um dono)

### Entenda se o volume de dados é suficiente para o problema<a id="sec-3-2-2" name="sec-3-2-2"></a>

-   Use a [lei dos grandes números](https://pt.wikipedia.org/wiki/Lei_dos_grandes_n%C3%BAmeros) e o [teorema central do limite](https://pt.wikipedia.org/wiki/Teorema_central_do_limite) a seu
    favor
-   Modelos mais simples podem não conseguir explorar uma quantidade
    grande de dados (mais dados não aumentam a acurácia)
    -   Avalie se é oportuno trabalhar com uma amostra
-   Modelos mais complexos (de deep learning, p. ex.) podem se
    beneficiar de mais volume e variedade de dados

### Questione a qualidade dos dados<a id="sec-3-2-3" name="sec-3-2-3"></a>

-   Avalie a ocorrência de dados **faltantes** e **outliers**
    -   Como devem ser interpretados?
    -   Pode-se contornar ou corrigir a ocorrência problemática?
    -   A observação como um todo deve ser descartada?
-   Certifique-se de que os dados realmente trazem a informação esperada

### Confirme o entendimento do negócio através dos dados<a id="sec-3-2-4" name="sec-3-2-4"></a>

-   Teste agora as hipóteses levantadas no Business Understanding
    -   Procure insights e oportunidades não mapeadas no conhecimento
        tácito do negócio
-   Inconsistências entre os dados e o negócio podem levar a:
    -   Identificar problemas inesperados nos dados
    -   Identificar problemas no tratamento inicial dos dados
    -   Corrigir erros de entendimento de negócio

## Data Preparation (preparação dos dados)<a id="sec-3-3" name="sec-3-3"></a>

### Automatize o tratamento dos dados<a id="sec-3-3-1" name="sec-3-3-1"></a>

-   Tratamento de dados muito manual pode exigir retrabalho no futuro
-   Em caso de novos dados no mesmo padrão, o esforço adicional de
    tratá-los deveria ser mínimo

### Automatize uma validação técnica do dados<a id="sec-3-3-2" name="sec-3-3-2"></a>

-   Certifique-se que os dados crus estão conforme o esperado
-   Certifique-se que o dataset final está conforme o esperado
-   Erros ou alertas deveriam notificar problemas detectados
-   A validação pode evoluir ao longo do tempo a partir de problemas
    inicialmente não detectados
-   Isso dá mais robustez para alterações no tratamento não quebrarem o
    que já havia sido testado anteriormente

### Valide o dataset final com visão de negócio<a id="sec-3-3-3" name="sec-3-3-3"></a>

-   Dados sólidos são fundamentais para o resultado do modelo
-   O dataset final geralmente incorpora várias fontes distintas
    -   Erros são especialmente comuns na consolidação (merge, joins)
-   Importante testar se os grandes números são reconhecidos
    -   Totais, médias, percentuais
-   Também é útil inspecionar amostras dos dados com especialistas e ver
    se não há nada estranho
-   Formalize a validação com os especialistas de negócio

### Organize os metadados do dataset final em um documento dinâmico<a id="sec-3-3-4" name="sec-3-3-4"></a>

-   Descreva os metadados do dataset final em um documento estruturado
    (premissas, descrições das colunas)
-   Mantenha um documento de referência a ser atualizado sempre que
    houver mudanças
-   Em caso de uma equipe, é bom ter alguém específico que responda pela
    sua confiabilidade (um dono)

## Modeling (modelagem)<a id="sec-3-4" name="sec-3-4"></a>

### Estabeleça uma boa variável-resposta<a id="sec-3-4-1" name="sec-3-4-1"></a>

### Defina o tamanho dos dados de teste com critério<a id="sec-3-4-2" name="sec-3-4-2"></a>

-   Isso se aplica a dados de validação (dev) e de teste
-   O objetivo principal do teste é estimar o desempenho esperado para o
    modelo em produção
-   A regra popular de reservar 30% dos dados para teste não é universal
    -   Faz sentido num dataset da ordem de milhares de observações
    -   Com milhões de observações disponíveis, pode ser um desperdício
-   O tamanho deve ser o suficiente para dar confiança à mensuração da
    métrica

### Dados de teste devem seguir a distribuição de produção<a id="sec-3-4-3" name="sec-3-4-3"></a>

-   Isso se aplica a dados de validação (dev) e de teste
-   O objetivo principal do teste é estimar o desempenho esperado para o
    modelo em produção
-   Se o modelo for usado em dados de natureza muito diferente dos de
    teste, pode ter um desempenho bem pior do que o anteriormente
    mensurado
-   O treino pode ter mais nuances e se utilizar de uma distribuição
    diferente, pois são os dados de validação e teste que vão suportar a
    estimativa de desempenho
-   É importante reservar dados de um período não utilizado no treino
    (out-of-time) para validar a sua **estabilidade**

### Foque em uma métrica única para calibração do modelo<a id="sec-3-4-4" name="sec-3-4-4"></a>

-   Conviver com várias métricas de desempenho pode atrapalhar a busca
    pelo melhor modelo
-   Caso as necessidades de negócio exija conviver com vários critérios
    distintos, algumas opções são:
    -   Tentar combinar diferentes indicadores em uma métrica única (ex.:
        F1-score em classificação)
    -   Impor restrições sobre mínimo ou máximo de alguns indicadores, mas
        tentar otimizar uma métrica específica (ex.: o modelo de menor
        MAPE que leva menos de 10s de execução)

### Comece com um modelo simplificado e evolua com critério<a id="sec-3-4-5" name="sec-3-4-5"></a>

-   Um baseline inicial permite entender melhor a dificuldade do
    problema
-   O modelo baseline pode fundamentar uma conversa analítica com o
    negócio, refinando mais cedo o entendimento
-   Uma **análise de erro** direcionada a partir do modelo baseline pode
    guiar as iterações seguintes
    -   Um erro num segmento específico ou num período específico pode
        revelar o que o novo modelo precisa levar em conta
-   Uma abordagem mais ágil favorece ciclos de evolução e validação

### Refine o modelo de maneira estratégica<a id="sec-3-4-6" name="sec-3-4-6"></a>

-   Investigue os principais ofensores (observações com grandes
    distorções)
-   Investigue se há padrões claros de concentração de erro:
    -   Erro consistentemente maior numa categoria específica
    -   Erro consistentemente maior num período específico
-   Verifique se o modelo está sofrendo com underfitting (erro in-sample
    mais alto que o esperado)
    -   Uma ideia é reduzir (se houver) a regularização do modelo
    -   Outra opção é tentar incluir novas variáveis com potencial de se
        adequar mais ao fenômeno
-   Verifique se o modelo está sofrendo com overfitting (erro in-sample
    muito menor que out-of-sample)
    -   Uma ideia é aumentar (ou incluir) alguma forma de regularização
    -   Se for uma opção viável, adicionar mais dados ao modelo poderia
        ajudar a reduzir o overfitting

## Evaluation (validação de negócio)<a id="sec-3-5" name="sec-3-5"></a>

### Evolua analiticamente a modelagem<a id="sec-3-5-1" name="sec-3-5-1"></a>

-   É um momento para trazer pessoas experientes em ciência de daos para
    aportar conhecimento:
    -   O tratamento de dados já deveria estar maduro
    -   Diversos modelos já foram testados
-   Pequenas mudanças no fluxo de tratamento e treino podem levar a
    aumentos expressivos no desempenho

### Valide os resultados do modelo com visão de negócio<a id="sec-3-5-2" name="sec-3-5-2"></a>

-   É importante validar se o modelo se comporta como esperado pelo
    negócio
-   Mesmo um modelo com bom desempenho analítico pode não atender as
    necessidades de negócio
-   Isso pode sugerir mudanças mais ou menos profundas na abordagem:
    -   Alterar a métrica de desempenho
    -   Alterar a variável-resposta
    -   Repensar o recorte dos dados (granularidade, periodicidade)
-   Dependendo do cenário, pode não valer a pena implantar o modelo em
    produção

## Deployment (implantação ou entrega)<a id="sec-3-6" name="sec-3-6"></a>

### Automatize uma validação técnica da saída do modelo<a id="sec-3-6-1" name="sec-3-6-1"></a>

-   Testes automatizados podem identificar problemas críticos na saída
    -   Perda de observações durante o processo de predição
    -   Predição em branco
    -   Predição com valor inválido (negativo, string)
    -   Predição com valor muito acima ou abaixo do razoável
    -   Problemas de formato (data, casas decimais)
-   A automatização acelera a identificação e o diagnóstico do problema

### Faça log do processo de predição em produção<a id="sec-3-6-2" name="sec-3-6-2"></a>

-   Registre informações que possam ajudar na investigação de problemas
-   Registre também o instante em que cada etapa começou e terminou

### Armazene o input utilizado para predição em produção<a id="sec-3-6-3" name="sec-3-6-3"></a>

-   Quando um problema é identificado no processo, é importante ter o
    disponível o input exato para investigação
-   Se o modelo puxa o input direto de um banco de dados dinâmico, pode
    ser difícil reproduzir o erro

### Versione o modelo disponível em produção<a id="sec-3-6-4" name="sec-3-6-4"></a>

-   Quando o modelo evolui ao longo do tempo, é importante versioná-lo
-   Além de código-fonte, é importante versionar:
    -   Os modelos serializados (conforme resultado do treino)
    -   Arquivos de configuração
    -   Em suma, tudo que define o comportamento do modelo
-   Garanta que é simples reverter o modelo para uma versão anterior

# Obrigado!<a id="sec-4" name="sec-4"></a>

Espero que o documento seja proveitoso para outros entusiastas de
ciência de dados, especialmente para quem está começando. Vou tentar
evoluir o material no futuro. Comentários e sugestões são bem-vindos e
podem ser feitos [neste gist](https://gist.github.com/andlima/d19fdfde3b0c94a602d2606021d2e877).
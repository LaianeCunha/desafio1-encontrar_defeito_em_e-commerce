# Desafio 1 - Mentoria em Testes de Software
<mark> Testando um produto de mercado com ajuda da IA Generativa </mark>

## Visão geral

Pesquisar e criar uma lista de testes que podem ser realizados para testar a qualidade, encontrar defeitos e possíveis ajustes para o site “Enjoei” (https://www.enjoei.com.br), site de compra e vendas de produtos usados. Além da lista de testes, serão apresentados possíveis melhorias ao site/software, baseado nos resultados dos testes que podem ser realizados.

## Objetivos
1. Listar os principais testes que podem ser realizados e que venham a fazer sentido com a visão de testes de Michael Bolton.
2. Identificar as possíveis falhas e defeitos e junto a elas, os riscos que o site apresenta que podem ser cruciais para o funcionamento.
3. Apresentar de forma clara e objetiva os níveis de risco que cada falha pode trazer ao negócio sem o teste de qualidade.

## Especificações
Para executar a proposta desta tarefa, foi adotado o pensamento e visão de Michael Bolton, na qual se baseia em testes de maneira de exploração para encontrar falhas dentro de um software e/ou site.

*"Testar é -entre outras coisas - avaliar um produto aprendendo sobre ele por meio de exploração, experimentação, observação e inferência."*  Michael Bolton

Para a execução da tarefa, os testes foram divididos em 5 categorias diferentes, utilizando um modelo de prompts muito similar para todos os casos. Cada um deles voltado a uma página do site, sendo eles: página inicial, catálogo de produtos, carrinho de compras, login e pagamento. Com base nos estudos de testes de cada categoria, foram condensados os testes considerados mais importantes e cruciais para o funcionamento do site, adensados em lista de testes, riscos e tabela de níveis de risco.

## Lista de testes

* ### Página inicial
**1. Descoberta por cliques:**
   
Clicar em todos os itens do menu (moças, rapazes, crianças, enjoei pro, promoções e banners) e validar o destino.

**2. Links do logo:**

Clicar no logo sempre retorna à home sem perder o estado inesperadamente.

**3. Busca básica:**

Pesquisar termos válidos e inválidos; respostas de resultado, empty state e sugestões.

**4. Promoções e preços:**

Verificar formatação (R$, separadores, %off), coerência entre banner e página de destino.

**5. Cookie banner:**

Não bloqueia conteúdo essencial; botões “entendo e concordo”/política funcionam e persistem.

**6. Lazy-loading:**

Imagens fora da viewport carregam sob demanda? Placeholders não ficam “congelados”.


* ### Catálogo de produtos

**7. Inserção de caracteres especiais:**

Digitar símbolos como #$%&*@ para observar se a busca lida bem com entradas não usuais.

***8. Pesquisa com letras maiúsculas e minúsculas misturadas:**

Verificar se o resultado muda ao procurar "ELLUS", "ellus" e "ElLuS".

***9. Inserção de espaços em excesso***

Digitar " Ellus " (com espaços antes e depois) e observar se o sistema interpreta corretamente.

***10. Inserção de números:***

Testar "12345" para observar se a aplicação retorna algo ou trata como erro.

***11. Testar autocorreção ou tolerância a erros de digitação:***

Digitar "Elus" em vez de "Ellus" e observar se o sistema ajuda o usuário com sugestões.

* ### Carrinho de compra
***12. Adicionar produto à sacolinha:***

Verificar se o produto aparece imediatamente no carrinho, com informações corretas (nome, foto, preço, tamanho).

***13. Adicionar múltiplos produtos diferentes:***

Observar se todos estão listados corretamente e se o carrinho atualiza valores.

***14. Remover produto do carrinho:***

Validar se o item realmente some e se o total é recalculado.

***15. Esvaziar o carrinho:***

Testar a opção de limpar todos os itens de uma vez, avaliando se o estado final fica consistente. Observar se o site mostra mensagem amigável e sugere voltar às compras.

***16. Carrinho com usuário não logado:***

Explorar se é possível adicionar itens sem login e se eles se mantêm ao criar/entrar em conta. Verificar se, ao sair da conta e entrar novamente, os itens continuam salvos.

* ## Login
***17. Navegar sem estar com login:***

Verificar se é possível navegar pelo site (por exemplo, acessar listagens e produtos) sem fazer login, ou se o login é obrigatório para qualquer interação.

***18. Autenticação (login) permissiva com dados incorretos:***

Inserir e-mail válido com senha incorreta, verificar se aparece mensagem de erro apropriada (por exemplo, “E-mail ou senha incorretos”) e se o reCAPTCHA está ativado corretamente.

***19. Validação de campos obrigatórios:***

Deixar o campo e-mail ou senha em branco, tentar enviar — experimentar validação de campos obrigatórios e mensagens exibidas.

***20. Validação e coerência para autenticação:***

Inserir e-mail e senha válidos, confirmar que o login acontece corretamente e que redireciona para a página esperada após autenticação.

***21. Conexão ininterrupta:***

Testar a persistência do “Continuar conectado”: fazer login, fechar navegador, reabrir e verificar se a sessão permanece ativa conforme esperado ou termina corretamente pelo tempo previsto.

* ## Pagamento

***22. Pagamento com ou sem login:***

Acessar a página de pagamento sem login. Verificar se é possível dar continuidade ao pagamento sem ter realizado o login.

***23. Duração de tempo mínimo para pagamento:***

Simular expiração de sessão (tempo de inatividade). Verificar se o pagamento deve ser realizado dentro de um tempo estipulado ou não.

***24. Salvamento automático de dados de pagamento:***

Atualizar a página de pagamento. Testar se dados de pagamento ficam salvos ao sair da tela de pagamento.

***25. Memória de pagamento ao sair da página:***

Fazer login, acessar pagamento e depois usar “logout” em outra aba. Verificar se os dados de pagamento e produtos selecionados se mantém após o “logout”.

***26. Opções de parcelamento (mínimo e máximo):***

Testar opções de parcelamento. Observar se os juros são aplicados corretamente, e se a UI mostra as condições com clareza.


## Lista descritiva de defeitos e falhas com impacto para o negócio

* ### Página inicial

***1. Preço divergente: banner vs. destino***

Impacto: Valores e “até X% off” na home não batem com a listagem/PDP. Reclamações/chargebacks, Reclame Aqui, erosão de confiança.

***2. Carrossel que trava a primeira impressão***

Impacto: Site sem fallback em conexões lentas; não navega por teclado; quebra em mobile. LCP ruim, abandono precoce e perda da janela de impacto das campanhas e com isso, possível perda de clientes.

***3. Cookie banner que bloqueia conversão***

Impacto: Aviso de cookies cobre CTAs/menus na primeira dobra e/ou não respeita preferência. Impede cliques rentáveis, piora métricas e contamina A/B tests.

***4. Menu que leva ao lugar errado***

Impacto: Links “moças/rapazes/crianças/outros” da home apontam para categorias erradas ou 404. Drop na navegação, fricção na descoberta e receita perdida.

***5. Imagens pesadas sem lazy-load***

Descrição: herói e sessões da home carregam assets grandes sem otimização. Impacto: tempo de carregamento alto, pior SEO, CPC desperdiçado e conversão menor.

* ## Catálogo de produtos

***6. Pesquisa travando com textos muito longos***

Impacto: Usuários que colarem parágrafos grandes podem travar ou quebrar a busca, causando frustração e abandono da compra, além de gerar sobrecarga no sistema.

***7. Busca não reconhece emojis usados pelos clientes***

Impacto: Usuários que pesquisam produtos utilizando emojis (ex.: 👟👗🔥) não encontraram resultados, o que pode gerar perda de oportunidades de venda, principalmente entre públicos mais jovens que utilizam esse recurso com frequência.

***8. Demora no retorno da pesquisa prejudica conversão***

Impacto: Quando a pesquisa demora para retornar resultados, os usuários podem desistir da navegação antes de encontrar o que procuram, o que aumenta a taxa de abandono e reduz as chances de venda.

***9. Pesquisa inviável em tablets afasta compradores móveis***

Impacto: Usuários que acessam a plataforma via tablet enfrentam dificuldade para realizar pesquisas. Isso impede que um público relevante conclua suas compras, reduzindo o alcance do negócio em dispositivos móveis.

***10. Ausência de autocomplete reduz descoberta de produtos***

Impacto: A falta de sugestões automáticas durante a pesquisa dificulta que os usuários encontrem rapidamente o que desejam ou descubram novos produtos. Isso pode resultar em menos vendas e menor engajamento na plataforma.

* ## Carrinho de compras

***11. Produto adicionado ao carrinho não apresenta informações corretas***

Impacto: O usuário perde confiança no site e pode desistir da compra ao não visualizar corretamente nome, foto, preço ou tamanho do item.

***12. Carrinho não reflete corretamente múltiplos produtos diferentes***

Impacto: O valor total pode ficar errado, levando à frustração ou abandono da compra.

***13. Carrinho não é esvaziado corretamente***

Impacto: Usuário fica inseguro sobre o estado do carrinho e pode desistir de finalizar a compra.

***14. Itens no carrinho desaparecem após login/logout***

Impacto: Usuário perde tempo refazendo a seleção, o que gera frustração e pode levá-lo ao abandono

***15.Itens adicionados sem login não migram após autenticação***

Impacto: Usuário refaz todo o processo de escolha, aumentando frustração e chance de desistência.

* ## Login

***16. Login aceitando senha incorreta***

Usuários conseguem acessar contas sem autenticação real, abrindo brecha para fraudes, sequestro de contas e transações indevidas, causando perda financeira e quebra de confiança dos clientes na plataforma.

***17. Login permitindo múltiplas tentativas ilimitadas (força bruta)***

Se não houver bloqueio após várias tentativas erradas, atacantes podem descobrir senhas por força bruta, comprometendo dados sensíveis, compras indevidas e até roubo de saldo de vendedores.

***18. Login aceitando senhas fracas ou repetidas***

Permitir que usuários cadastrem senhas muito simples ou já utilizadas aumenta a exposição a ataques, facilitando acessos não autorizados, impactando a segurança de contas e podendo gerar responsabilidade legal para o site.

***19. Sessões de login não expiram corretamente***

Se as sessões não forem encerradas após tempo limite, usuários podem continuar logados indefinidamente em dispositivos públicos ou compartilhados, expondo contas a uso indevido, fraudes de compra/venda e perda de confidencialidade.

***20. Login não notifica tentativas suspeitas de acesso***

Se não houver alertas (e-mail, SMS, push) para acessos de locais ou dispositivos diferentes, usuários podem não perceber invasões em tempo hábil, resultando em roubo de identidade digital, fraude em transações e perda de confiança na marca.

* ## Pagamento

***21.Pagamento sem login obrigatório***

Impacto: Permitir que o usuário finalize a compra sem estar logado impede o rastreamento correto de pedidos e identidades, abrindo espaço para fraudes, dificultando disputas e reduzindo a base de clientes cadastrados — prejudicando o crescimento e a confiança no marketplace.

***22.Interrupção no meio do pagamento sem rollback***

Impacto: Se a transação cair por falha de internet e não houver rollback claro, o cliente pode ser cobrado em duplicidade ou ficar com pedido sem confirmação, o que gera grande insatisfação e alto custo para o suporte.

***23.Mensagens de erro genéricas no pagamento***

Impacto: Mensagens pouco claras (“Erro no pagamento”) sem indicar o motivo real aumentam a taxa de abandono de compra, sobrecarregam o suporte e reduzem o volume de conversão.

***24.Cartões inválidos ou expirados aceitos***

Impacto: Se o sistema não bloquear números de cartão inválidos ou com data expirada, o site pode registrar pedidos fantasmas que nunca serão liquidados, aumentando a carga operacional com estornos e impactando a confiabilidade da plataforma.

***25.Histórico de pedidos inconsistente***

Impacto: Se a compra for interrompida mas mesmo assim registrada, o comprador pode reclamar de pedidos cobrados indevidamente, exigindo estorno e comprometendo a imagem de segurança do site.

## Tabela de riscos e impactos para o negócio


| ID | RISCO POTENCIAL   | IMPACTO |
|---------|--------|-------|
|   |
|  | **RISCO POTENCIAL - PÁGINA INICIAL** |  |
|    |
| 1 | Promoções expiradas/sem estoque em destaque (banner e CTA levam para oferta inexistente) | Alto |
| 2 | Preço/percentual divergente entre banner da home e página de destino | Alto |
| 3 | Mensagens de frete/prazo na home inconsistente com CEP (promessa não cumprida) | Alto |
| 4 | Carrossel pesado/travado prejudica LCP/CTR dos destaques e converte em menos vendas | Médio |
| 5 | Venda acima do estoque via CTA da home (ex.: anúncio unitário permitindo comprar >1) | Alto |
|   | RISCO POTENCIAL - Catálogo de produtos|  |
| 6 | Busca falhar com caracteres especiais (#$%&*@). Pode impedir usuários de encontrar produtos; afeta experiência mas não bloqueia compra diretamente | Médio |
| 7 | Diferença de resultados ao usar maiúsculas/minúsculas. Usuários podem acreditar que o produto não existe; reduz usabilidade e confiança no sistema. | Médio |
| 8 | Sistema não tratar espaços em excesso. Usuários podem não localizar produtos existentes, causando frustração e perda de vendas. | Médio |
| 9 | Inserção apenas de números sem tratamento. Pode afetar buscas por códigos de produtos; perda de vendas se o cliente usar SKU/código como referência. | Médio |
| 10 | Não ter tolerância a erros de digitação/autocorreção. Usuários podem desistir se não encontrarem produtos por pequenos erros; perda significativa de vendas. | Médio |
|    |
|    | **RISCO POTENCIAL - CARRINHO DE COMPRAS**                                                                 | |
|    |
| 11 | Usuário não logado adiciona item e ao realizar login perde os itens.                                 | Alto |
| 12 | Itens adicionados à sacola desaparecem após atualização/navegação                                                               | Alto |
| 13 | Carrinho vazio não apresenta mensagem clara ou sugestão de ação                                                                 | Alto |
| 14 | Remoção de item não é refletida corretamente                                                                                    | Médio|
| 15 | Checkout interrompido não mantém os itens na sacola                                                                             | Alto |
| 16 | Navegação sem login em áreas restritas. Uso indevido de usuários pode gerar problemas.                                          | Alto |
| 17 | Login com credenciais válidas não funciona. Cliente pode desistir de comprar ou vender.                                         | Alto |
| 18 | “Continuar conectado” mal implementado. Desistência do usuário caso carrinho de compras esteja cheio e não salve o histórico de navegação de compra. | Alto |
| 19 | Enviar campos em branco sem validação. Possível divergência nas áreas de dados de entrega e/ou pagamento causando na baixa conversão ao cliente. | Médio|
| 20 | Mensagem incorreta ao inserir senha errada. Risco de cliente desistir de dar continuidade no login ao site e gerar assim baixa conversão de vendas e compras. | Médio|
|                                                                                                                                            |
|    | **RISCO POTENCIAL - PAGAMENTO**                                                                                                      |
|    |
| 21 | Acessar a página de pagamento sem login. Exposição de dados sensíveis ou bypass de autenticação.                                 | Alto |
| 22 | Fazer login, acessar pagamento e depois usar “logout” em outra aba. Sessão ainda ativa em áreas críticas mesmo após logout.      | Alto |
| 23 | Simular expiração de sessão (tempo de inatividade). Usuário continua logado em área crítica sem revalidação.                     | Alto |
| 24 | Histórico de pedidos inconsistente: transações falhas aparecem como concluídas.                                                  | Alto |
| 25 | Usuários conseguem finalizar compra com cartão inválido ou expirado.                                                             | Alto |

  ## Notas Gerais

 Ao longo das pesquisas e estudos de caso, alguns integrantes do grupo tiveram problemas para acessar o site, se cadastrar ou navegar. Mesmo através de outros navegadores e rede de internet, o problema persistiu, mostrando que o site, apesar de funcionar, apresenta problemas críticos para alguns usuários.

O site oferece duas funções aos usuários: compra e venda de produtos variados. Entretanto, a maioria dos testes foram realizados pensando na usabilidade de compra. Uma nova bateria de testes, pensada sob a perspectiva de usabilidade para vendas, pode ser realizada para aperfeiçoar e complementar os testes, tornando o site melhor tanto para quem compra quanto para quem vende.

A atividade realizada gerou diversas respostas, porém foi acordado por todos os integrantes do grupo que seriam apresentados apenas 5 testes de cada categoria, com o objetivo de apresentar os pontos considerados mais relevantes, tornando o documento final mais objetivo e enxuto.

 # Modelos de Prompts para os estudos de caso
 
* ## Prompts página inicial
  
 ### Prompt 1

Objetivo: Use a mentalidade do Michael Bolton, testador e QA, para listar testes que eu poderia fazer neste site para identificar defeitos relacionados a página inicial. O site a ser usado para o estudo de caso é o site de vendas e compras brasileiro Enjoei.

-Segue o link oficial do site.

Contexto: A mentalidade de testes de Bolton se baseia em uma abordagem de exploração do software. Ele diz que : "Testar é -entre outras coisas - avaliar um produto aprendendo sobre ele por meio de exploração, experimentação, observação e inferência." Ele utiliza deste pensamento para encontrar defeitos e falhas.

-Segue uma foto em anexo do site.

-Segue uma imagem da parte do site em HTML.

Regras: Foque apenas na visão do Bolton e de mais nenhum outro testador. Foque também em uma listas de testes que podem ser realizadas pensando na página inicial do site.

Exemplo:

-Teste 1: Se é possível navegar no site normalmente sem cadastro com login e senha. Ou se isso é obrigatório para navegar.

Formato: Liste a lista de testes com identificador numérico e um resumo breve do teste que você recomenda que seja feito.

### Prompt 2

Objetivo: Com base nesta lista de defeitos que me passou, coloque nomes em defeitos que deixam mais claro o seu impacto negativo para o negócio.

Contexto: Lista de defeitos =

1) Usuários podem comprar mais de um item quando só se tem um.

2) Usuários tentam vender produtos que não se encaixam no perfil de produtos do site.

3) Conseguir realizar o login mesmo com a senha incorreta.

Negócio = Site de compras e vendas operando no setor comercial auxiliando pessoas a venderem ou comprarem itens semi-novos ou usados na internet.

Regras: Leve em consideração que quanto é o impacto negativo, mais fáceis os defeitos serão aceitos pelo time. Lembre-se de fazer isso baseado na proposta inicial, pensando na página inicial do site.

Exemplo: "Usuários que trocam a senha pela que já foi usada" deveria ser algo como "usuários que já alteraram a senha conseguem comprar e vender com a senha anterior, possibilitando ataques e usos de usuários mal intencionados gerando prejuízos tanto para o site quanto para quem usa para comprar ou vender".

Formato: Listar com identificador numérico para cada defeito e sua descrição.

### Prompt 3

Objetivo: Relacione quais são os riscos do site que estou testando, o Enjoei.com.br.

Contexto: Segue imagem do site em anexo.

Trata-se de um e-commerce de vendas de produtos semi-novos e usados, como roupas, sapatos, acessórios, eletrônicos e entre outros.

Regras: Foque apenas em riscos relacionados ao negócio da empresa que podem se tornar problemas caso o site tenha falhas e relacionados a página inicial.

Exemplo:

-Risco 1: Usuários inserirem CEP não identificado para finalizar a compra.

-Risco 2: Usuários tem opção de comprarem mais de um produto sem ter no estoque a quantidade desejada.

-Risco 3: Usuários colocarem a venda produtos não relacionados ao tipo de perfil do site.

Formato: Tabular, contendo colunas ID, Risco, Impacto (Baixo, Médio e Alto).

* ## Prompts catálogo de produtos

### Prompt 1

Objetivo:

-Utilize a mentalidade de Testes de Michael Bolton para listar testes de software que eu poderia fazer no site "https://www.enjoei.com.br/" para identificar defeitos, vulnerabilidades e possíveis melhorias que envolvem o header de busca do catálogo de produtos do site.

Contexto:
A mentalidade de testes de Michael Bolton se baseia em uma abordagem de exploração, experimentação e observação do software.

Regras: A prioridade é focar apenas na visão de testes do Michael Bolton. Não utilize a mentalidade de outros pesquisadores e testadores.

Exemplo:

Teste 1: Inserir um texto de um tipo de produto que não faz parte da lista de produtos disponíveis no site e ver se a aplicação irá retornar com uma mensagem de aviso como "produto não encontrado".

Formato:
Lista de testes com identificador numérico com um breve resumo do teste que você recomenda que seja feito.

### Prompt 2

Objetivo: Colocar nomes em defeitos que deixem mais claro o seu impacto negativo para o negócio

Contexto: Lista de defeitos = 

1) retorno da pesquisa muito demorado,
   
 2 ) dificuldade de pesquisa utilizando tablet,
   
   3 )não realizou o autocomplete com sugestões no momento da pesquisa Negócio = plataforma de compra e venda online
   
   4) Entrada de texto muito grande Copiar e colar um parágrafo enorme para ver se a caixa de pesquisa e o sistema conseguem processar ou quebrar.
      
 5) Pesquisa com emojis Colocar caracteres como "👟👗🔥" e observar o comportamento.

Regras: -leve em consideração que quanto mais claro é o impacto negativo, mais fácil os defeitos serão aceitos pelo time

Exemplo: "não funcionam com pessoas que utilizam tablet" deveria ser algo como "Os usuários que utilizam tablet não conseguem realizar pesquisa no site, e com isso podemos perder possíveis compradores"

Formato: Lista com identificadores numéricos para cada defeito e sua descrição.

### Prompt 3

Objetivo: listar quais são os riscos relacionados aos testes realizados

Contexto: https://www.enjoei.com.br/ trata-se de um e-commerce

Regras: foque apenas em riscos relacionados ao negócio da empresa que podem se tornar problemas caso o site tenha falhas

Exemplo: 

-Risco 1: usuários conseguirem comprar produtos que tenham estoque esgotado 

-Risco 2: usuários não logados conseguirem realizar compras e vendas

Formato: -Tabular, contendo colunas ID+1, Risco, Impacto (Baixo,Médio e Alto) e racional com relação ao impacto.

* ## Prompts carrinho de compras

### Prompt 1
Objetivo:
- Com a Mentalidade de Testes de Michael Boton liste testes da tela de carrinhos do site Enjoei

Contexto:
- A mentalidade de testes de Michael Bolton diz que : "Testar é -entre outras coisas - avaliar um produto aprendendo sobre ele por meio de exploração, experimentação, observação e inferência."

  Regras:
- Com o site do Enjoiei, link: https://www.enjoei.com.br/, liste testes que podem ser feitos a fim de encontrar erros, falhas e defeitos no carrinho de compra do site;
Foque apenas na visão do Michael Bolton, não use a mentalidade de outros pesquisadores.

Exemplo:
Adicione produto a sacolinha e esse produto seja identificado e visível ao carrinho de compra no site Enjoei.

Formato:
- Lista de testes com identificador numérico e um resumo breve do teste que você recomenda que seja feito.

### Prompt 2
Objetivo:
- Colocar nomes em defeitos que deixem mais claro o seu impacto negativo para o negócio com base na lista anterior que foi passada.
  
Contexto:
Lista de defeitos: 1. Adicionar produto à sacolinha conferindo as informações do produto; 2. Esvaziar o carrinho e verificar mensagem

Regras:
- Leve em consideração que quanto mais claro é o impacto negativo, mais fácil os defeitos serão aceitos pelo time.
  
- Realizar com todos que foram listados.

  
Exemplo:
- "Usuário adiciona um item e depois mais item no carrinho de compra e o valor muda" deveria ser algo como "Usuário adiciona mais de um item no carrinho de compras e o valor total da compra atualiza conforme o valor dos itens adicionados"

Formato:
- Lista com identificador numérico para cada defeito e a sua descrição.

### Prompt 3

Objetivo:
- Listar quais são os riscos relacionados ao site que estou testando.

- Site que estou testando é o Enjoei link: https://www.enjoei.com.br/ da aba sacola de compra, link: https://www.enjoei.com.br/continue-comprando

Contexto:
Imagem do site da aba sacola de compras sem inserir item em anexo.
- Trata-se de um site de compra e venda focando na sacola de compra

Regras:
- Foque apenas em riscos relacionados a sacola de compras que podem se tornar problemas caso o site tenha falhas ou a sacola de compras não funcione.

Exemplo:
- Risco 1: Usuário não logado adiciona o item a sacola de compras e ao realizar login perde o item inserido.
  
- Risco 2: Usuário não consegue criar conta para acessar a sacola de compra do site.
  
Formato:
- Tabular, contento colunas ID, Risco, Impacto (Baixo, Médio e Alto) e racional com relação ao impacto

* ## Prompts login

### Prompt 1
Objetivo:
Use a mentalidade do Michael Bolton, testador e QA, para listar testes que eu poderia fazer neste site para identificar defeitos relacionados a pagina do login. O site a ser usado para o estudo de caso é o site de vendas e compras brasileiro Enjoei. -Segue o link oficial do site na área do login "https://www.enjoei.com.br/usuario/identifique-se".

Contexto:
A mentalidade de testes de Bolton se baseia em uma abordagem de exploração do software. Ele diz que : "Testar é -entre outras coisas - avaliar um produto aprendendo sobre ele por meio de exploração, experimentação, observação e inferência." Ele utiliza deste pensamento para encontrar defeitos e falhas.

Regras:
Foque apenas na visão do Bolton e de mais nenhum outro testador. Foque também em uma listas de testes que podem ser realizadas pensando na página do login do site.

Exemplo:
-Teste 1: Se é possível navegar no site normalmente sem cadastro com login e senha. Ou se isso é obrigatório para navegar.

Formato: Liste a lista de testes com identificador numérico e um resumo breve do teste que você recomenda que seja feito.

* ## Prompts pagamento

### Prompt 1

Objetivo: Usar a mentalidade do Michael Bolton, testador e QA, para listar testes que eu poderia fazer, nesta página que envio o link e estou anexando o html, para identificar defeitos relacionados a página do login. O site a ser usado para o estudo de caso é o site de vendas e compras brasileiro Enjoei.

Segue o link oficial do site da área de pagamento:
“https://www.enjoei.com.br/checkout/173477340/formas-de-pagamento?action_source=store_bundle_bar&ref=meu_enjoei_continue_comprando&search_id=000ce8f8-8fd6-4274-b67d-31ce90b6fb29-1757543755302".

Segue em anexo o html da página.

Contexto: A mentalidade de testes de Bolton se baseia em uma abordagem de exploração do software. Ele diz que : "Testar é -entre outras coisas - avaliar um produto aprendendo sobre ele por meio de exploração, experimentação, observação e inferência." Ele utiliza deste pensamento para encontrar defeitos, vulnerabilidades e falhas.

Regras: Foque apenas na visão do Bolton e de mais nenhum outro testador. Foque também em uma listas de testes que podem ser realizadas pensando na página do login do site.

Exemplo:

Teste 1: Se é possível navegar no site normalmente sem cadastro com login e senha. Ou se isso é obrigatório para navegar.

Formato: Listar os testes com identificador numérico e um resumo breve do teste que você recomenda que seja feito, categorizar os riscos graduados em baixo, médio e alto e mostrando o risco potencial.


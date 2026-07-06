MINHAS ANOTAÇÕES SOBRE O TEXTO EM RELAÇÃO A VERSÃO ATUAL

---

> Use of Artificial Intelligence Tools
> -> isso tem que ser depois das conclusões, vamos usar a sugestao do SBIE
> "I A Generativa: Em atendimento ao Código de Conduta para autores da S B C, o uso de ferramentas de Inteligência Artificial (I A) Generativa na escrita e/ou revisão do conteúdo de artigos deve ser declarada explicitamente. Essas ferramentas não podem ser listadas como autores de um artigo e seu uso não exime os autores da responsabilidade sobre todo o seu conteúdo, inclusive no caso de ser identificado plágio. Nas submissões ao S B I E, esta declaração deve ser feita em uma seção ao final do artigo, com o título de “Declaração sobre uso de Inteligência Artificial”."

---

"""
\caption{Physical prototype setup (ESP32 + wearable sensors), used for functional data transmission validation. The physiological data for classifier validation (Sections 5.8--5.10) originate from the WESAD dataset, not from this setup.}
\label{fig:physical_setup}
"""

essa figura ficou muito ruim. eu vou tirar uma foto literalmente do setup e colocar no lugar. a foto vai conter o esp, o celular com o app aberto e no fundo o computador com o terminal dos servidores aberto.

para cumprir o requisito de explicação da analucia tb faltou explicar que o esp não esta COLETANDO dados fisiologicos, visto que isso era fora do escopo do trabalho. O esp assume que dados podem ser coletados e tem na memoria FLASH do microcontrolador que são lidos a cada 30 segundos tal qual seria se fossem dados reais e vai salva em uma PILHA na memoria RAM e quando o ble solicita, é feito um flush da pilha inteira para o celular. O celular então envia os dados para o servidor, que é o que é validado no trabalho.
isso eu acho que n foi falado, mas é importante reforçar isso. Garanta consistencia nas explicações e no texto, para que fique claro que o ESP32 não está coletando dados fisiológicos reais, mas sim simulando a coleta e transmissão desses dados para validação do sistema. O trabalho foca na transmissão, analise, treino e uso dos dados, não na coleta em si.

(setup_fisico.png)

para a comunicação entre as partes verifique a imagem (federated_integration_architecture.png) que ja deve estar no texto e é onde explica como o sistema ocmo um todo funciona em um exemplo com 2 hospitais com 2 pacientes em cada um. deixe consistente, atualize o texto para garantir essa compreensão e não deixar duvidas ao ver a imagem setup_fisico pra pessoa n pensar "ta mas e como isso funciona em detalhes?" pq ai agt pode referenciar ela para a imagem "federated_integration_architecture.png" que ja explica o funcionamento do sistema como um todo.

---

garantir que todas as figuras e tabelas estejam com referencias de \ref{} no texto

---

essa table aqui \label{tab:model_and_training} ta com texto sobreposto nas colunas 3 e 4, talvez longtable resolva

---

adicionar referencias para as tecnicas usadas

- augmentation usada -> buscar referencia para ele
- metricas e loss function usada (olhe no wesad_proj pra ver o que ta sendo usado e ache os artigos que propoem essas tecnicas e cite eles)

---

adiciona uma citação para justificar o uso do onion entre o mobile e o servidor, para deixar claro que a comunicação é feita de forma segura e anônima. e adiciona uma citação para justificar o HMAC e explica o pq agt usou
basicamente o hmac existe para garantir que quem esta mandando para o onion, ja que é um enederço publico e tecnicamente poderia ser achado por qualquer um com o endereço .opnion, precisamos garantir que quem enviou o pacote é de fato quem poderia, mas não podem existir usuarios, então, como garatir a autenticação de alghuiem que eu não conheço? por isso o hmac. ele vai servir pq quando eu subi o servidor na rede onion, eu gerei um secret junto com o enderço e isso eu uso para fazer um qr code que o celular lê, dessa forma o celular le o endereço onion e o secret. então, quandop ele faz a assinatura hm,ac do body que ele ta enviando com o secret eu sei que ele escaneou o qr coide, logo, ele esta no hospital e portanto, posso confiar nos dados. além disso, que é um middleware de autenticação no express, fazemos uma validação do schema do body do post, pra garantir que um ataque de man in the middle não possa enviar dados corrompidos (tem uma subsection sobre hmac, pode explicar la) - e isso do hmac eu to falando ali meio tirando da bunda, podemos citar algum artigo ou a propria documentação do hmac pra justificar o uso e explicar melhor.

===

AGORA AS ANOTAÇÕES DO JIM LAU (BANCA) EM RELAÇÃO À 1A VERSÃO
(nem tudo se aplica pq ja corrigimos algumas coisas com os goals 0~8 corrigindo o que a analucia pediu)
"""
Olá Rodrigo, boa tarde

As principais correções, além do que a Analúcia pediu, são:

- Capa, contracapa, ficha catalográfica, resumo em português e inglês, folha de assinatura

- Verificar a formatação dos espaços

- Melhorar na introdução qual a proposta do trabalho. No caso, deixar clara a questão dos "pesos " enviados pelo servidor.

- Talvez trocar a seção da descrição da descrição da arquitetura começando pela seção 5.2 (\subsection{Mobile Application as Privacy Gateway}) e depois a seção 5.1 (\subsection{Evolved System Architecture})

- Deixar claro o papel do ESP32 na sua implementação, no caso, ele só tem o papel de validar o aplicativo e não de monitorar dados dos sensores e enviar para o gateway.

- Seria importante também adicionar artigos sobre anonimização de IPs

- colocar no texto ou como trabalhos futuros sobre o problema do gateway ser um ponto único de falha e como trabalhos futuros investigar uma solução para contornar esse problema.

At.te

Jim
"""

> "- Melhorar na introdução qual a proposta do trabalho. No caso, deixar clara a questão dos "pesos " enviados pelo servidor."
> -> acho que o que ele ta querendo dizer é o que o global api retorna depois, que são os pesos globais depois de ter feito a união dos pesos de cada hospital. Verifica se ja não esta bom e se não estiver claro, melhore.

> "- Seria importante também adicionar artigos sobre anonimização de IPs"
> -> estamos usando rede onion para comunicação do paciente (celular) com o servidor, então não é necessário anonimizar o IP do paciente. Mas podemos adicionar uma explicação sobre isso no texto, para deixar claro que a comunicação é feita de forma segura e anônima.

===

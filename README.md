# esp-tflite-micro

Executando os exemplos disponibilizados pela Espressif para inserção de modelos nos seus chips. Estou montando este repositório porque, ao tentar executar os exemplos, mesmo os mais simples geravam erros. Isso é um pouco frustrante, considerando a importância de rodar esses exemplos para usar como base em outros projetos.  

Embora não seja a única forma de aprender a utilizar uma biblioteca, a documentação disponível é bastante restrita, e os exemplos que encontrei ou eram para versões muito antigas ou tinham uma complexidade desnecessária.

[esp-tflite-micro](https://github.com/espressif/esp-tflite-micro):  
<img alt="Static Badge" src="https://img.shields.io/badge/vers%C3%A3o%20atual%20-%201.3.2%20-blue?style=flat">

---

## ⚠️ Observações  
- **Framework**: ESP-IDF  
- **IDE**: ESPRESSIF IDE  

**Por que ESP-IDF?**  
Os modelos disponíveis são baseados nesse framework. Apesar de já utilizar o Arduino no VS Code ou na IDE do Arduino, o suporte geral é oferecido pelo ESP-IDF. Já queria começar a trabalhar com ele e, como adquiri um ESP32-S3 AI, resolvi migrar. Até agora tem sido mais simples trabalhar diretamente com o ESP-IDF.  

Caso eu não tivesse migrado, dependeria de terceiros para fazer a conversão dos modelos para o framework Arduino. Portanto, optei pelo padrão oficial. (Quem sabe eu volte a migrar no futuro, dependendo das necessidades.)

---

## Exemplo: `hello_world`

Entre os exemplos disponibilizados, considero este o menos complexo. Ele é o equivalente ao famoso **blink** do Arduino/ESP.  

O exemplo consiste em rodar um modelo em um ESP. Um dos motivos que me fazem pensar em projetos simples é que, para este exemplo, não precisamos de periféricos extras além da placa de desenvolvimento.  

### O que o modelo faz?

O modelo inserido simula a função seno. Valores são passados para o modelo, que retorna o seno correspondente e imprime o resultado no monitor serial.  

### Etapas do processo:
1. O modelo foi **treinado** (isso será detalhado em uma seção futura)..  
2. O modelo foi **convertido** (isso será detalhado em uma seção futura).  
3. O modelo foi **inserido** no ESP.  

Neste primeiro momento, vamos focar apenas na etapa de inserção, assumindo que todas as etapas anteriores já foram concluídas e que já está tudo montado, o objetivo é penas executar o projeto pronto destacando problemas que tive...

- Como  ESPIDF instalado basta abrir o terminal que deve ter aparecido em sua área de trabalho, não especificamente é necessário utilizar esse prompt ``ESP-IDF 5.3 CMD``, mas são configurações a menos para serem feitas.
- Antes de iniciar veja se o gerenciador python está funcionado: ``idf.py --version``
   Aversão do seu Framework deve aparecer na tela, o que indica que o seu ambiente esta configurado nas variaveis de ambiente do sistema
   Não lembro muito bem, mas esse foi um dos erro que tive, onde os comandos  ``idf.py``  não funcionavam senso necessários adicionar na PATH 
- Após isso vamos fazer o download da última versão do tensorflow-lite-micro, digite no terminal: ``idf.py add-dependency "esp-tflite-micro"``
  Com isso basta apenas criar um dos modelo de exemplo disponibilizados e com base nele criar seus próprios projetos, nesse artigo vamos começar pelo ***hellow_world*** devido que para visualização mão será necessário nenhum periférico externo além do esp.
  -Para criar o modelo basta navegar pelas pastas até o local onde você deseja criar o mesmo e digitar: ``idf.py create-project-from-example "esp-tflite-micro:hello_world"
``
Em suma são três projetos disponíveis, e como mencionaei eles servem de base para você desenvolver o seu, são eles: hello_world...
  O terminal além das várias funcionalidades serve principalmente para você manipular/configurar o seu projeto, por exemplo, diferende da IDE do Arduino ou da ESPRESSIF que utilizam uma interface, aqui aplicamos linhas de comando, nessa primeira abordagem achei mais interessante começar por aqui. Um bom exemplo é em relação a configuração do tipo de placa utilizado, na interface navegamos por uma barra de rerramentas já na interface digitamso: ``idf.py set-target esp32s3
``, no meu caso uso o esp32s3.
- Após configurarmos a placa presisamos configurar o nosso modelo, para isso fazemos ``idf.py build``
  Essa etapa é muito importante, se você olhar a pasta onde o projeto foi criado verá que ao executar esse comando outros arquivos apareceram e outras pastas, isso ocorroque porque...

  

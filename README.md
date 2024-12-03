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


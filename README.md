# esp-tflite-micro

Executando os exemplos disponibilizados pela Espressif para inserção de modelos em seus chips. Estou montando este repositório porque, ao tentar executar os exemplos, mesmo os mais simples, erros frequentes surgiam. Isso pode ser frustrante, considerando a importância de rodar esses exemplos como base para outros projetos.

Embora não seja a única forma de aprender a utilizar uma biblioteca, a documentação disponível é bastante limitada. Os exemplos encontrados, em sua maioria, eram para versões muito antigas ou apresentavam uma complexidade desnecessária.

[esp-tflite-micro](https://github.com/espressif/esp-tflite-micro):  
<img alt="Static Badge" src="https://img.shields.io/badge/vers%C3%A3o%20atual%20-%201.3.2%20-blue?style=flat">

---

## ⚠️ Observações  
- **Framework**: ESP-IDF  
- **IDE**: ESPRESSIF IDE  

### Por que ESP-IDF?  
Os modelos disponíveis são baseados nesse framework. Apesar de já utilizar o Arduino no VS Code ou na IDE do Arduino, o suporte oficial é oferecido pelo ESP-IDF. Decidi migrar para ele, especialmente após adquirir um ESP32-S3 AI. Até o momento, trabalhar diretamente com o ESP-IDF tem se mostrado mais simples.

Se não tivesse migrado, dependeria de terceiros para converter os modelos para o framework Arduino. Optei pelo padrão oficial, mas posso reavaliar no futuro, dependendo das necessidades.

---

## Exemplos Disponíveis

O repositório `esp-tflite-micro` fornece alguns exemplos básicos para você começar a trabalhar com modelos de machine learning. Estes exemplos são projetados para rodar no ESP32 e ESP32-S3, com foco em inferência de modelos TinyML. Entre os exemplos fornecidos, temos:

- **hello_world**: O exemplo mais simples e ideal para quem está começando, pois não requer periféricos externos. O modelo simula a função seno e imprime os resultados no monitor serial.
- **image_classification**: Exemplo para classificação de imagens usando um modelo pré-treinado.
- **gesture_recognition**: Modelo de reconhecimento de gestos, útil para projetos de interação com dispositivos por movimento.

Esses exemplos servem como base para que você possa criar seus próprios projetos de machine learning com ESP32. 

---

## Exemplo: `hello_world`

Entre os exemplos disponibilizados, considero este o menos complexo, sendo o equivalente ao famoso **blink** do Arduino/ESP.  

Este exemplo consiste em rodar um modelo no ESP, sem a necessidade de periféricos extras além da placa de desenvolvimento.

### O que o modelo faz?  

O modelo simula a função seno. Ele recebe valores como entrada, calcula o seno correspondente e imprime o resultado no monitor serial.  

### Etapas do processo:
1. **Treinamento** do modelo (detalhado em uma seção futura).  
2. **Conversão** do modelo (detalhado em uma seção futura).  
3. **Inserção** do modelo no ESP.  

Neste primeiro momento, focaremos na etapa de inserção, assumindo que as etapas anteriores já foram concluídas e que o ambiente está configurado para executar o projeto.

---

## Instruções para executar o exemplo

### Passo 1: Verificar o ambiente

1. Certifique-se de que o **ESP-IDF** está instalado. Abra o terminal específico do ESP-IDF, geralmente chamado `ESP-IDF 5.3 CMD`. Embora não seja obrigatório usá-lo, ele reduz a necessidade de configurações adicionais.
   
2. Verifique se o gerenciador Python está funcionando corretamente com:
   ```bash
   idf.py --version
   ```
   Se a versão do framework aparecer na tela, significa que o ambiente está configurado corretamente. Caso contrário, pode ser necessário configurar a variável de ambiente `PATH`.

### Passo 2: Baixar o TensorFlow Lite Micro

Faça o download da última versão da biblioteca TensorFlow Lite Micro com o comando:
```bash
idf.py add-dependency "esp-tflite-micro"
```

Esse comando vai baixar e configurar automaticamente a biblioteca TensorFlow Lite Micro no seu projeto, que é necessário para realizar inferência de modelos de machine learning no ESP32.

### Passo 3: Criar o projeto `hello_world`

1. Navegue até a pasta onde deseja criar o projeto.  
2. Digite o comando:
   ```bash
   idf.py create-project-from-example "esp-tflite-micro:hello_world"
   ```
   
Isso cria um novo projeto baseado no exemplo `hello_world`, onde você pode visualizar o funcionamento básico de como rodar um modelo TinyML no ESP32.

### Passo 4: Configurar o dispositivo

1. Configure o tipo de placa que será utilizado. No terminal, use:
   ```bash
   idf.py set-target esp32s3
   ```
   (Substitua `esp32s3` pelo modelo do seu dispositivo, se for diferente.)

2. Configure o projeto com:
   ```bash
   idf.py build
   ```

### Explicação do comando `idf.py build`

O comando `idf.py build` é utilizado para compilar o projeto e gerar os arquivos binários necessários para o firmware do ESP32. Durante a execução desse comando, o ESP-IDF realiza as seguintes etapas:

- **Compilação do código-fonte**: O código presente no diretório `src` do projeto é compilado. Isso inclui arquivos C/C++ que são convertidos em código de máquina.
- **Linkagem**: Os arquivos compilados são linkados para criar o binário final que será carregado no dispositivo.
- **Geração de arquivos de firmware**: O comando também gera os arquivos binários, como `firmware.bin`, que contêm o código compilado pronto para ser flashado no ESP32.
- **Criação de diretórios e arquivos adicionais**: Ao executar o comando `idf.py build`, você notará que novas pastas e arquivos são criados automaticamente. Entre esses, temos a pasta `build/`, onde ficam armazenados todos os arquivos gerados durante a compilação.

O processo de compilação é necessário porque, antes de carregar o código no dispositivo, é necessário gerar os binários para o firmware. Isso envolve otimização e adaptação do código para a arquitetura do ESP32, bem como a inclusão de qualquer dependência do TensorFlow Lite Micro.

### Passo 5: Flash no dispositivo

Após a compilação, o firmware pode ser carregado no dispositivo ESP32 com o comando:
```bash
idf.py -p PORT flash
```
Substitua `PORT` pela porta serial em que seu ESP32 está conectado. Esse comando faz o flash do firmware gerado no dispositivo, permitindo que o modelo seja executado diretamente no chip.

---

## Conclusão

Após concluir os passos acima, o projeto estará pronto para compilar, flashar e executar no seu dispositivo. Se encontrar dificuldades, revise as configurações do ambiente ou consulte a documentação oficial.

A partir daqui, você pode começar a modificar os exemplos para se adequar às suas necessidades e explorar os diferentes modelos disponíveis no `esp-tflite-micro`.

mode

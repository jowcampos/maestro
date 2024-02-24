# Simplificando a automação de testes de UI em dispositivos móveis com Maestro

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*Bed4d9UmFGx2wuHxo46tDA.png)

# Indolor

O Maestro é um player relativamente novo no cenário de testes, mas está rapidamente conquistando popularidade devido à sua simplicidade e eficiência na implementação. Essa ferramenta permite a automação de testes ponta a ponta (e2e), simulando interações de usuário e verificando se o comportamento é o esperado.
Nesse sentido, trata-se de uma ferramenta multiplataforma com suporte para iOS e Android, React Native, Flutter e WebViews. O Maestro evoluiu a partir de seus predecessores, como: Appium, Espresso, UIAutomator e XCTest, incorporando o que já funcionava bem e adicionando melhorias fundamentais, ao mesmo tempo, em que mantém uma abordagem de uso simplificada, sem complexidades.

![](https://miro.medium.com/v2/resize:fit:720/format:webp/0*t_Q_QKj8HuNnbkIy)

Essa abordagem simplificada e de alto desempenho torna o Maestro uma escolha especialmente atrativa para desenvolvedores que buscam configurar testes e2e de maneira ágil e descomplicada em seus aplicativos. Com o Maestro, você pode garantir que seu aplicativo funcione conforme as expectativas, economizando tempo e recursos no processo de desenvolvimento e garantindo a qualidade do seu produto final.

Além da agilidade, destaco aqui:
- **Execução rápida:** Os testes são interpretados, sem necessidade de compilação, e o Maestro pode monitorar e executar automaticamente os arquivos de teste conforme são modificados.
- **Sintaxe simples:** Configure seus testes facilmente em um arquivo YAML simples.
- **Tolerância integrada:** O Maestro lida com a imprevisibilidade dos elementos da interface do usuário, toques na tela e atrasos nos aplicativos e dispositivos móveis.
- **Sem atrasos artificiais:** O Maestro evita a necessidade de pausas arbitrarias nos testes com "chamadas sleep()" e aguarda automaticamente pelo carregamento do conteúdo.
- **Configuração descomplicada:** O Maestro é um único arquivo executável que pode ser usado em qualquer lugar.

# Na prática
Para começar a utilizar da maneira mais simples estarei demonstrando como instalar e rodar em uma máquina MacOS.
Se estiver utilizando uma máquina com SO diferente, recomendo seguir a doc oficial: https://maestro.mobile.dev/getting-started/installing-maestro

1. Execute o comando para instalar:
```bash
curl -Ls "https://get.maestro.mobile.dev" | bash
```

2. crie um arquivo com extensão .yaml no diretório de sua escolha, por exemplo: /Users/you/Desktop/flow.yml'
e escreva ao menos uma primeira linha para iniciar o seu app:
```bash
appId: seu.app.id
---
- launchAppFluxos
```
3. Certifique-se de que um dispositivo/emulador Android ou iOS esteja em execução.

4. Em sua IDE favorita, navegue até o local onde o arquivo está localizado e execute o seguinte comando:
```bash
maestro test flow.yml
```

Você escreve as etapas de como navegar pela aplicação similarmente ao Appium UI ou Espresso. Exemplo:
```bash
appId: com.apple.MobileAddressBook
---
- launchApp:
    clearState: true
- tapOn: "Adicionar"
- tapOn: "Adicionar Foto"
- "scroll"
- tapOn:
    point: "62%,40%"
- tapOn: "OK"
- tapOn: "OK"
- tapOn:
    id: "Nome"
- inputRandomPersonName
- tapOn:
    id: "Sobrenome"
- inputText: "Test"
- tapOn:
    id: "Empresa"
```
https://maestro.mobile.dev/api-reference/commands

A cobertura de teste pode ser escalonada conforme a evolução do projeto, uma vez que o Maestro possui comandos de alto nível que permite que qualquer pessoa colabore, mesmo não sendo o autor original.

# Maestro Studio
Sabe quando você fica perdidão nas telas que não possui ID, o Maestro resolve esse problema com o Mestro Studio que está integrado ao CLI. Com apenas um comando é possível selecionar visualmente um elemento da interface clicando e capturando na tela do dispositivo, também possibilitando capturar o elemento por texto ou posição na ausência dos ID.
Segunda parte em breve. "Melhores Práticas para utilizar o Maestro".

# Referências
https://maestro.mobile.dev

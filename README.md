# FloodAlertESP32

**Resumo:**  
Este repositório contém o código-fonte do projeto "FloodAlertESP32", que propõe uma solução de baixo custo para a detecção e notificação em tempo real de enchentes em comunidades de risco. Utilizando ESP32, sensores ambientais e a API do CallMeBot, o sistema coleta e exibe dados críticos por meio de uma interface web interativa.

---

## Estrutura do README.md

Este documento está organizado da seguinte forma:
- **Título e Resumo:** Objetivo e escopo do projeto.
- **Estrutura do Repositório:** Organização dos arquivos e pastas.
- **Selos Considerados:** Selos adotados no processo de avaliação.
- **Informações Básicas:** Requisitos de hardware e software.
- **Dependências:** Versões e instruções para instalação de bibliotecas.
- **Preocupações com Segurança:** Riscos e medidas de segurança.
- **Instalação:** Passos para baixar e configurar a aplicação.
- **Teste Mínimo:** Instruções para executar um teste básico do sistema.
- **Experimentos:** Passo a passo para reproduzir as principais reivindicações.
- **Reivindicações:** Detalhamento das funcionalidades-chave.
- **LICENSE:** Informações sobre a licença do projeto.

---

## Selos Considerados

Os selos considerados para este projeto são:  

`Disponíveis`, `Funcionais`, `Sustentáveis` e `Reprodutíveis`.

---

## Informações Básicas

**Hardware Necessário:**
- 2x ESP32 (modelo DOIT ou similar)
- Sensor HC-SR04 (ultrassônico)
- Sensor DHT11 (temperatura e umidade)
- Sensor de umidade do solo (entrada analógica)
- Protoboard, jumpers e cabos
- Fonte de alimentação USB

**Software Necessário:**
- Arduino IDE (recomendado: versão 1.8.x ou superior)
- Navegador web moderno para visualização da interface
- Biblioteca HTTPClient, WiFi e DHT (para ESP32)

**Ambiente de Execução:**
- Sistema operacional compatível com a Arduino IDE (Windows, Linux ou macOS)
- Conexão à internet para envio de dados e notificações

---

## Dependências

- **WiFi.h:** Inclusa na instalação padrão do ESP32.
- **HTTPClient.h:** Para comunicação via HTTP.
- **DHT.h:** Para interação com o sensor DHT11.
- Outras dependências podem ser instaladas via Gerenciador de Bibliotecas do Arduino IDE.  
*Obs.: Certifique-se de utilizar as versões recomendadas pelas documentações oficiais.*

---

## Preocupações com Segurança

Este artefato não apresenta riscos diretos aos avaliadores. Contudo, recomenda-se manter a chave de API do CallMeBot e informações sensíveis (como números de telefone) protegidas, principalmente em ambientes de produção.

---

## Instalação

1. **Clone o Repositório:**

   ```
   git clone https://github.com/DayanFA/FloodAlertESP32.git
   cd FloodAlertESP32
   ```

2. **Configuração no Arduino IDE:**
   - Abra o arquivo `envia.ino` (e os demais arquivos conforme a organização).
   - Configure a placa ESP32 e a porta serial na Arduino IDE.
   - Instale as bibliotecas necessárias (WiFi, HTTPClient e DHT).

3. **Configuração da API do CallMeBot:**
   - Acesse o site do CallMeBot e obtenha sua chave de API.
   - Atualize os parâmetros `phone`, `text` e `apikey` no arquivo `envia.ino`.

4. **Carregue os Sketches:**
   - Faça upload de `envia.ino` para o ESP32 responsável pela coleta.
   - Faça upload de `ip.ino` e `receb.ino` conforme a função de cada dispositivo.

---

## Teste Mínimo

1. **Conexão WiFi:**  
   - Verifique o Monitor Serial para confirmar que o ESP32 se conecta à rede (mensagem "Conectado ao WiFi").

2. **Envio de Dados:**  
   - Observe os dados dos sensores sendo enviados pelo arquivo `envia.ino` no Monitor Serial.
   - Acesse o endereço IP exibido pelo `ip.ino` para confirmar a conectividade.

3. **Visualização na Interface Web:**  
   - Conecte-se ao ESP32 Servidor (arquivo `receb.ino`) via navegador e observe os dados atualizados em tempo real na interface web.

4. **Simulação de Alerta:**  
   - Modifique, se necessário, os parâmetros no código para simular um nível de água crítico e verifique o disparo de notificações via WhatsApp.

---

## Experimentos

Para reproduzir as principais reivindicações do artigo, siga os passos abaixo:

### Reivindicação #1: Monitoramento Contínuo
- **Configuração:** Conecte os sensores conforme o diagrama de montagem.
- **Execução:** Faça upload do `envia.ino` no ESP32 de Coleta.
- **Verificação:** Utilize o Monitor Serial e acesse a interface web para confirmar que os dados (nível da água, temperatura, umidade) são atualizados em tempo real.

### Reivindicação #2: Notificações Automáticas
- **Configuração:** Atualize os parâmetros de alerta no código (incluindo a chave de API do CallMeBot).
- **Execução:** Simule uma condição em que o nível da água ultrapassa 100 cm.
- **Verificação:** Confirme, via Monitor Serial, que o sistema envia uma solicitação GET para o CallMeBot e que a notificação é recebida no WhatsApp.

---

## LICENSE

Este projeto está licenciado sob a [MIT License](LICENSE).

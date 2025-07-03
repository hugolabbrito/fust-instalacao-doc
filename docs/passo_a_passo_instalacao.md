# 🛠️ Passo a Passo da Instalação – Projeto FUST

Este documento orienta os técnicos responsáveis pela instalação da internet nas escolas do Projeto FUST.

---

## ✅ 1. Documentação Inicial

Antes de iniciar a instalação, certifique-se de ter em mãos:

- 📄 **Ofício de Apresentação**  
  - Caminho: `doc/oficio-apresentacao.pdf`  
  - Deve ser impresso e apresentado na escola no início do atendimento.

- 📝 **Termo de Recebimento do Serviço**  
  - Caminho: `doc/termo-recebimento-servico.pdf`  
  - Deve ser preenchido e assinado após a instalação, e enviado no grupo de atendimento correspondente.

---

## 📋 2. Checklist de Equipamentos

### 🔻 Instalação com até 6 Access Points

1. TP-Link Omada **ER7206** – Firewall  
2. DATACOM **DM2500 4GT** – Switch Gerenciável  
3. TP-Link AC1350 **EAP225** – Access Point  
4. Cabo de rede **UTP CAT5e**  
5. **Cabo Console** – para configuração do DATACOM  
6. **Patchcord** de 1,5m ou 2,0m (conforme a quantidade de APs)  
7. **Canaletas de PVC ALUMBRA REF 6262**

---

### 🔺 Instalação com 7 ou mais Access Points

1. TP-Link Omada **ER7206** – Firewall  
2. DATACOM **DM2500 4GT** – Switch Gerenciável  
3. TP-Link Omada Smart Switch **SG22210P** – Switch PoE  
4. TP-Link AC1350 **EAP225** – Access Point  
5. Cabo de rede **UTP CAT5e**  
6. **Cabo Console** – para configuração do DATACOM  
7. **Patchcord** de 1,5m ou 2,0m (conforme a quantidade de APs)  
8. **Canaletas de PVC ALUMBRA REF 6262**  
9. **Gabinete Metálico - Rack** (acima de 8 APs, geralmente são 2)

---

## 📦 2.1 Unboxing e Registro dos Equipamentos

Após identificar os equipamentos conforme o checklist, siga os passos abaixo:

1. **Realize o unboxing (retirada da embalagem)** de todos os equipamentos da instalação.
2. **Tire fotos das etiquetas** de cada equipamento, garantindo que o número de série (serial) esteja visível.
3. Envie cada foto no **grupo de atendimento da escola** com a seguinte descrição:

**Exemplo de envio:**

{Foto 01} - Equipamento Firewall - Descrição: FIREWALL
{Foto 02} - Equipamento DATACOM - Descrição: DATACOM
{Foto 03} - Equipamento SWITCH - Descrição: SWITCH
{Foto 04} - Equipamento ACCESS POINT - Descrição: AP-01 - DIRETORIA


> 💡 **Importante:**  
> Cada **Access Point** deve ser **numerado com caneta na parte de baixo da etiqueta branca** (ex: "AP-01", "AP-02", etc.), e a descrição enviada no grupo deve seguir o formato:
>
> `AP-{NÚMERO} - {LOCAL INSTALADO}`  
> Exemplo: `AP-03 - SALA DOS PROFESSORES`

---

## ⚙️ 3. Etapas Técnicas da Instalação

### 3.1 Montagem Física

- Instale o gabinete metálico (se aplicável).
- Monte o rack e organize os equipamentos.
- Ligue o ER7206 (Firewall) na Porta 2 - WAN2 o cabo da operadora. (se for ONU direto) (se for DATACOM via sair da porta 5)
- Interligue o cabo do DATACOM porta 1 ao ER7206 (Firewall) na porta 3.
- Interligue o cabo do Switch porta 1 ao ER7206 (Firewall) na porta 4.(caso a instalação tenha)
- Interligue o cabo dos Access Points ao ER7206 (Firewall) a partir da porta 4 (caso não tenha switch)
- Ligue as Fontes PoE (instalações sem Switch) dos Access Points da porta LAN nas portas 4, 5 e 6 do (Firewall) e nas portas 2, 3 e 4 do Datacom. (instalações com até 6 access point)
- Instalação acima de 7 access point, serão ligados diretamente no Switch até 6 access point sem a necessidade do uso das fontes PoE.
- Caso haja 2 rack (geralmente em escolas que tem um espaço fisico grande com mais de 8 aps) faça a passagem de cabo do Rack Principal para o Rack Secundário e instale o Switch no Rack secondário fazendo a distribuição dos cabos (o tecnico define quantos pontos vai chegar no rack secundário)
- Faça passagem e organização dos cabos com canaletas.

### 3.2 Configuração do Switch DATACOM

### Dependência para configuração do DATACOM
- Putty - https://the.earth.li/~sgtatham/putty/latest/w64/putty.exe - 64bits
        - https://the.earth.li/~sgtatham/putty/latest/w32/putty.exe - 32bits
        - https://the.earth.li/~sgtatham/putty/latest/putty-0.83.tar.gz - Unix/Linux/MacOS
### Configuração
- Verifique por meio do Gerenciamento de Dispositivo qual a porta de COM foi estabelida ao instalação o cabo console no Windows.
- Abra o Putty
- Selecione Connection type: Serial
- No campo Serial line coloque a porta referente ao cabo conselo EX: COM3
- No campo Speed coloque o valor 9600 (geralmente já está nessa velocidade)
- Clique em Open
- Geralmente a tela fica preta piscando, só aperta a tecla ENTER 1x e vai aparece o login
- digite admin + ENTER (usuário)
- digite admin + ENTER (senha)

- Acesse via **cabo console**.
- Configure VLANs, endereços IP e portas conforme orientação técnica.
- Salve as configurações ao finalizar.

### 3.3 Atualização do Firmware do Firewall (se necessário)

- Acesse via navegador: `System Tools → Firmware Upgrade`.
- Use o firmware localizado em:  
  `firmware/firmware-update-firewall-ER7206v2-2025-02-18.bin`
- Atualize, aguarde reinicialização e valide conexões.

### 3.4 Configuração de Rede

- Configure IP fixo (ex: `192.168.1.1/24`) no ER7206.
- Ative o servidor DHCP no firewall.
- Verifique se os APs recebem IP e têm acesso à internet.
- Acesse cada EAP225 e configure o nome da rede (SSID), segurança e canais.

---

## 🔍 4. Testes Finais

- Teste a navegação em:
  - 2 dispositivos via cabo
  - 2 dispositivos via Wi-Fi
- Verifique velocidade da internet, ping e latência.
- Acesse a interface de gerenciamento para validar o status dos APs.

---

## 📸 5. Registros e Envio

- Tire fotos:
  - Painel montado
  - Cabeamento
  - Acomodações dos equipamentos
- Preencha e assine o **Termo de Recebimento**
- Envie a imagem no grupo correspondente da instalação

---

## ✅ 6. Finalização

- Confirme a conclusão da instalação no grupo do projeto
- Arquive o termo digitalizado
- Mantenha um histórico organizado por escola

---

**Responsável pela documentação:**  
**Hugo Leonardo Araujo Batista Brito – Innovatech**  
📍 Camaçari – Bahia  
📧 innovatechba@gmail.com  
📱 (71) 98704-8150

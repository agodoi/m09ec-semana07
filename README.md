# 🔷 Estrutura Didática da Aula (Cisco Packet Tracer)

## 1. 🚀 Abertura (Problema real) — 10 min

Comece com um cenário:

> “Uma empresa precisa organizar sua rede em setores (RH, Financeiro, TI, Operações), mas todos precisam imprimir em uma única impressora central.”

👉 Perguntas para provocar:

* Como separar setores sem misturar tudo?
* Como garantir que todos consigam imprimir?
* Como evitar conflitos de IP?

💡 Aqui você planta:

* Subredes
* Roteamento
* Comunicação entre redes

---

## 2. 🧠 Conceito-chave antes da prática — 15 min

Explique **o mínimo necessário para agir**:

* O que é **subrede**
* Por que usar **roteadores**
* Diferença entre:

  * IP de rede
  * IP de host
  * Gateway
* Ideia de **máscara de sub-rede**

👉 Use um exemplo simples:

```
192.168.1.0 /24 → dividir em 4 redes
```

Não aprofunde demais — a ideia é **dar ferramenta para a prática**.

---

## 3. 🧮 Desafio guiado (cálculo das subredes) — 20 min

1. Problema real
2. Conceitos mínimos
3. Cálculo das subredes
4. Montagem da rede
5. Configuração de IP
6. Roteamento
7. Impressora compartilhada
8. TCP vs UDP
9. Testes
10. Reflexão

Agora entra o raciocínio:

### Proposta:

* Criar **4 subredes**
* Definir:

  * Quantidade de hosts por rede
  * Máscara adequada

👉 Exemplo guiado:

* Rede base: 192.168.1.0/24
* Dividir em 4 → /26

| Subrede | Faixa               |
| ------- | ------------------- |
| 1       | 192.168.1.0 – 63    |
| 2       | 192.168.1.64 – 127  |
| 3       | 192.168.1.128 – 191 |
| 4       | 192.168.1.192 – 255 |

💡 Aqui você trabalha:

* CIDR
* Cálculo de hosts
* Planejamento de rede

---

## 4. 🖥️ Montagem da Topologia — 30 min

Agora sim: Packet Tracer.

### Estrutura:

* 1 roteador MASTER
* 3 roteadores subordinados
* Cada roteador → 1 subrede
* Impressora em uma subrede específica
* PCs distribuídos

---

## 🔽 Visual da topologia (para o aluno entender rápido)

![Image](https://community.cisco.com/t5/image/serverpage/image-id/209974iC0D7E221EE6E3999/image-size/large?px=999\&v=v2)

![Image](https://studfile.net/html/2706/1268/html_UOe4Xz3rAk.6pza/htmlconvd-IRNZs72x1.jpg)

![Image](https://www.ciscopress.com/content/images/chap1_9781587133329/elementLinks/01fig06_alt.jpg)

![Image](https://learningnetwork.cisco.com/sfc/servlet.shepherd/version/renditionDownload?contentId=05T3i00000ACKZw\&operationContext=CHATTER\&page=0\&rendition=THUMB720BY480\&versionId=0683i000001rnSx)

---

### Objetivo do aluno aqui:

* Arrastar dispositivos
* Conectar corretamente (cabos)
* Entender hierarquia de rede

---

## 5. ⚙️ Configuração manual de IP — 25 min

Agora entra a prática técnica:

Cada aluno deve:

* Definir IP manualmente nos PCs
* Definir gateway
* Configurar interfaces dos roteadores

👉 Exemplo:

```
PC:
IP: 192.168.1.10
Mask: 255.255.255.192
Gateway: 192.168.1.1
```

💡 Aqui você reforça:

* Endereçamento
* Gateway
* Comunicação local vs remota

---

## 6. 🔁 Roteamento entre redes — 25 min

Agora o ponto-chave:

* Configurar rotas (estático ou RIP/OSPF — você decide o nível)

👉 Sugestão didática:

* Começar com **roteamento estático**
* Depois provocar:

  > “E se essa rede crescer?”

💡 Aqui entra:

* Conceito de camada de rede
* Encaminhamento de pacotes

---

## 7. 🖨️ Impressora compartilhada — 15 min

Desafio prático:

* Colocar impressora em uma subrede
* Garantir acesso de todas as outras

👉 Teste:

* Ping
* Envio de “impressão”

💡 Conceitos:

* Interconectividade
* Serviços na rede

---

## 8. 🌐 TCP vs UDP (exploração prática) — 20 min

Agora você eleva o nível:

### Mostrar no Packet Tracer:

* Simulação de pacotes

👉 Comparação:

| TCP         | UDP             |
| ----------- | --------------- |
| Confiável   | Rápido          |
| Confirmação | Sem confirmação |
| Mais lento  | Mais leve       |

---

## 🔽 Visual para reforçar conceito

![Image](https://www.freecodecamp.org/news/content/images/2021/07/udp-and-tcp-comparison.jpg)

![Image](https://www.cloud4y.ru/upload/medialibrary/b74/d97dkgfm5tu0ngqu8oirrev3ltj4rqql/TCP-i-UDP.jpeg)

![Image](https://www.cdebyte.com/Uploadfiles/Picture/2023-3-24/20233241342233065.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AW4PkTTwBdrH4MkICc4gXMw.png)

---

👉 Atividade:

* Simular envio de pacote
* Observar diferença no modo simulation

---

## 9. 🧪 Testes finais (validação) — 15 min

Checklist do aluno:

* ✅ PCs se comunicam dentro da subrede
* ✅ PCs acessam outras subredes
* ✅ Impressora acessível por todos
* ✅ Ping entre todos os dispositivos

---

## 10. 🎯 Fechamento (reflexão) — 10 min

Perguntas finais:

* O que aconteceria sem subredes?
* Qual o papel do roteador?
* TCP ou UDP: quando usar cada um?

---



---

# 💡 Dica pedagógica (do seu perfil)

Essa aula funciona muito bem se você tratar como:

> **“Missão de Engenharia”**

Exemplo:

* Fase 1: Planejar rede
* Fase 2: Construir infraestrutura
* Fase 3: Garantir comunicação
* Fase 4: Validar sistema



Este vídeo da **Hardware Redes Brasil** ensina como dividir uma rede principal em sub-redes menores para que roteadores possam se comunicar (já que roteadores exigem redes diferentes em cada interface).

Abaixo, apresento um roteiro prático detalhado para você reproduzir todo o laboratório no **Cisco Packet Tracer**.

---

### **Objetivo do Laboratório**
Dividir a rede Classe C `192.168.0.0/24` em sub-redes menores usando a máscara `255.255.255.192` e configurar a comunicação básica entre dois roteadores.

---

### **1. Preparação do Cenário (Topologia)**
Abra o Packet Tracer e adicione os seguintes dispositivos:
* **Roteadores:** 2x Roteadores (Modelo 2911 ou similar). [[00:32](http://www.youtube.com/watch?v=X8tboS6NZLA&t=32)]
* **Switches:** 2x Switches (Modelo 2960). [[00:44](http://www.youtube.com/watch?v=X8tboS6NZLA&t=44)]
* **Computadores:** 2x PCs (um para cada lado). [[00:51](http://www.youtube.com/watch?v=X8tboS6NZLA&t=51)]

**Conexões de Cabos:**
1.  **PC para Switch:** Cabo Direto (Copper Straight-Through) na porta FastEthernet.
2.  **Switch para Roteador:** Cabo Direto conectando a porta **Gigabit 0/1** do Switch à porta **Gigabit 0/0** do Roteador. [[01:08](http://www.youtube.com/watch?v=X8tboS6NZLA&t=68)]
3.  **Roteador para Roteador:** Cabo Cruzado (**Copper Cross-over**) conectando as portas **Gigabit 0/1** de ambos os roteadores. [[01:28](http://www.youtube.com/watch?v=X8tboS6NZLA&t=88)]

---

### **2. Cálculo das Sub-redes**
O instrutor utiliza a técnica do "salto" para definir as redes: [[06:08](http://www.youtube.com/watch?v=X8tboS6NZLA&t=368)]
* **Máscara Escolhida:** `255.255.255.192`
* **Cálculo do Salto:** $256 - 192 = 64$.
* **Sub-redes Criadas:**
    * **Sub-rede 1 (LAN Esquerda):** `192.168.0.0` (IPs válidos: `.1` a `.62`).
    * **Sub-rede 2 (Link Roteadores):** `192.168.0.64` (IPs válidos: `.65` a `.126`).
    * **Sub-rede 3 (LAN Direita):** `192.168.0.128` (IPs válidos: `.129` a `.190`). [[10:14](http://www.youtube.com/watch?v=X8tboS6NZLA&t=614)]

---

### **3. Configuração de IP nos PCs**
**PC da Esquerda:** [[11:56](http://www.youtube.com/watch?v=X8tboS6NZLA&t=716)]
* **IP Address:** `192.168.0.1`
* **Subnet Mask:** `255.255.255.192`
* **Default Gateway:** `192.168.0.62`

**PC da Direita:** [[14:48](http://www.youtube.com/watch?v=X8tboS6NZLA&t=888)]
* **IP Address:** `192.168.0.129`
* **Subnet Mask:** `255.255.255.192`
* **Default Gateway:** `192.168.0.190`

---

### **4. Configuração dos Roteadores**
No Packet Tracer, clique no roteador, vá na aba **Config** e habilite as interfaces (clique em "On").

**Roteador 0 (Esquerda):**
* **Interface G0/0 (LAN):** IP `192.168.0.62` / Máscara `255.255.255.192`. [[14:15](http://www.youtube.com/watch?v=X8tboS6NZLA&t=855)]
* **Interface G0/1 (WAN/Meio):** IP `192.168.0.65` / Máscara `255.255.255.192`. [[16:10](http://www.youtube.com/watch?v=X8tboS6NZLA&t=970)]

**Roteador 1 (Direita):**
* **Interface G0/0 (LAN):** IP `192.168.0.190` / Máscara `255.255.255.192`. [[15:34](http://www.youtube.com/watch?v=X8tboS6NZLA&t=934)]
* **Interface G0/1 (WAN/Meio):** IP `192.168.0.66` / Máscara `255.255.255.192`. [[16:40](http://www.youtube.com/watch?v=X8tboS6NZLA&t=1000)]

---

### **5. Verificação e Observações Finais**
* **Luzes Verdes:** Certifique-se de que todas as interfaces nos roteadores foram ligadas (**Port Status: On**). [[01:40](http://www.youtube.com/watch?v=X8tboS6NZLA&t=100)]
* **Comunicação:** Neste ponto, o PC da esquerda conseguirá "pingar" o seu Gateway (`.62`), e os dois roteadores conseguirão se comunicar entre si através da rede `.64`. [[17:33](http://www.youtube.com/watch?v=X8tboS6NZLA&t=1053)]
* **Importante:** O instrutor ressalta que, embora as sub-redes estejam configuradas, os PCs de lados opostos ainda não se comunicam. Para isso, é necessária a **Tabela de Roteamento** (estático ou dinâmico), que é o tema da aula seguinte. [[17:39](http://www.youtube.com/watch?v=X8tboS6NZLA&t=1059)]

Assista ao vídeo completo aqui: [Criando Sub-redes no Packet Tracer - Aula 15](https://www.youtube.com/watch?v=X8tboS6NZLA)


http://googleusercontent.com/youtube_content/0

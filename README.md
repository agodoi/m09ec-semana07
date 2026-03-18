## 0. Nossa trilha de hoje

1. Problema real
2. Conceitos-chave
3. Cálculo das subredes
4. Montagem da rede
5. Configuração de IP
6. Configuração da Tabela de Roteamento
7. Impressora compartilhada
8. TCP vs UDP
9. Testes
10. Conclusões

## 1. Problema Real

Uma empresa precisa organizar sua rede em 2 setores: RH e Financeiro, mas todos precisam imprimir em uma única impressora central.

Reflita:

* Como separar setores sem misturar tudo?
* Como garantir que todos consigam imprimir?
* Como evitar conflitos de IP?

## 2. Conceitos-chave

* O que é **subrede**?
* Por que usar **roteadores**?
* Máscara de sub-rede
* IP da rede
* IP do primeiro host
* IP do último host
* IP de broadcast
* IP do Gateway (que

## 3. Mapeamento de Rede

1) Crie 3 sub-redes a partir de 192.168.0.1, onde cada sub-rede tenha no máximo 64 hosts;
2) Preencha essa tabela

| Sub-rede | Localização/Uso              | Endereço de Rede | 1º Útil        | Último Útil     | Máscara           | Gateway (Configurado)      |
|----------|-----------------------------|------------------|----------------|-----------------|-------------------|----------------------------|
| Sub 1    | LAN Alunos (Esquerda)        | 192.168.?.?      | 192.168.?.?    | 192.168.0.?    | 255.255.255.?   | 192.168.0.?              |
| Sub 2    | Link WAN (Roteadores)       | 192.168.0.?     | 192.168.?.?   | 192.168.0.?   | 255.255.255.?   | N/A (Ponto-a-Ponto)        |
| Sub 3    | LAN Profs (Direita)      | 192.168.0.?    | 192.168.?.?  | 192.168.0.?   | 255.255.255.?   | 192.168.0.?             |
| Sub 4    | Disponível (Reserva)        | 192.168.0.?    | 192.168.0.?  | 192.168.0.?   | 255.255.255.?   | -                          |


## 4. Montagem da Topologia no Cisco Packet Tracer

### 4.1 Topologia

<img src="https://github.com/agodoi/m09ec-semana07/blob/main/assets/topologia-01a.png" width="1000">


<img src="https://github.com/agodoi/m09ec-semana07/blob/main/assets/topologia-01b.png" width="1000">

### 4.2 Lista de peças:
* 02 Roteador: 1941
* 02 Switch: 2960
* 04 PC-PT
* 01 Printer-PT

### 4.3 O que fazer dentro do Packet Tracer?

* Arrastar dispositivos
* Conectar corretamente (cabos)
* Entender hierarquia de rede

### 4.4 Configuração manual de IP

* Configurar interfaces dos roteadores digitando o IP e máscara;
* Ligar cada interface;
* Definir IP manualmente nos PCs;
* Defini máscara manualmente nos PCs;
* Definir gateway nos PCs.


## 5. Configurações Gerais

### **5.1. Preparação do Cenário (Topologia)**
Abra o Packet Tracer e adicione os seguintes dispositivos:
* **Roteadores:** 2x Roteadores (Modelo 2911 ou similar).
* **Switches:** 2x Switches (Modelo 2960).
* **Computadores:** 2x PCs (um para cada lado).

**Conexões de Cabos:**
1.  **PC para Switch:** Cabo Direto (Copper Straight-Through) na porta FastEthernet.
2.  **Switch para Roteador:** Cabo Direto conectando a porta **Gigabit 0/1** do Switch à porta **Gigabit 0/0** do Roteador.
3.  **Roteador para Roteador:** Cabo Cruzado (**Copper Cross-over**) conectando as portas **Gigabit 0/1** de ambos os roteadores.

---

### **5.2. Cálculo das Sub-redes**
O instrutor utiliza a técnica do "salto" para definir as redes:
* **Máscara Escolhida:** `255.255.255.192`
* **Cálculo do Salto:** $256 - 192 = 64$.
* **Sub-redes Criadas:**
    * **Sub-rede 1 (LAN Esquerda):** `192.168.0.0` (IPs válidos: `.1` a `.62`).
    * **Sub-rede 2 (Link Roteadores):** `192.168.0.64` (IPs válidos: `.65` a `.126`).
    * **Sub-rede 3 (LAN Direita):** `192.168.0.128` (IPs válidos: `.129` a `.190`).

---

### **5.3. Configuração de IP nos PCs**
**PC da Esquerda:**
* **IP Address:** `192.168.0.1`
* **Subnet Mask:** `255.255.255.192`
* **Default Gateway:** `192.168.0.62`

**PC da Direita:**
* **IP Address:** `192.168.0.129`
* **Subnet Mask:** `255.255.255.192`
* **Default Gateway:** `192.168.0.190`

---

### **5.4. Configuração dos Roteadores**
No Packet Tracer, clique no roteador, vá na aba **Config** e habilite as interfaces (clique em "On").

**Roteador 0 (Esquerda):**
* **Interface G0/0 (LAN):** IP `192.168.0.62` / Máscara `255.255.255.192`.
* **Interface G0/1 (WAN/Meio):** IP `192.168.0.65` / Máscara `255.255.255.192`.

**Roteador 1 (Direita):**
* **Interface G0/0 (LAN):** IP `192.168.0.190` / Máscara `255.255.255.192`.
* **Interface G0/1 (WAN/Meio):** IP `192.168.0.66` / Máscara `255.255.255.192`.

---

### **5.5. Verificação e Observações Parciais**
* **Luzes Verdes:** Certifique-se de que todas as interfaces nos roteadores foram ligadas (**Port Status: On**).
* **Comunicação:** Neste ponto, o PC da esquerda conseguirá "pingar" o seu Gateway (`.62`), e os dois roteadores conseguirão se comunicar entre si através da rede `.64`.
* **Importante:** Embora as sub-redes estejam configuradas, os PCs de lados opostos ainda não se comunicam. Para isso, é necessária a **Tabela de Roteamento** (estático ou dinâmico).


**Configuração dos PCs:**
* **PC Esquerda (PC1):** IP `192.168.0.1` | Máscara `255.255.255.192` | Gateway `192.168.0.62`.
* **PC Direita (PC4):** IP `192.168.0.129` | Máscara `255.255.255.192` | Gateway `192.168.0.190`.

**Configuração dos Roteadores:**
* **Roteador Aluno (Esquerda):**
    * Interface `G0/0`: `192.168.0.62` (Ligada à LAN esquerda).
    * Interface `G0/1`: `192.168.0.65` (Ligada ao outro roteador).
* **Roteador Professor (Direita):**
    * Interface `G0/1`: `192.168.0.66` (Ligada ao outro roteador).
    * Interface `G0/0`: `192.168.0.190` (Ligada à LAN direita).

---

### **5.6. Identificação de Redes Conectadas e Não Conectadas**
Para configurar o roteamento, você precisa dizer ao roteador como chegar nas redes que **não** estão ligadas diretamente a ele por um cabo.

* **Roteador Aluno (Esquerda):**
    * *Redes Conectadas:* `192.168.0.0` e `192.168.0.64`.
    * *Rede NÃO Conectada:* `192.168.0.128`. (É nesta rede que precisamos ensinar o roteador a chegar).
* **Roteador Professor (Direita):**
    * *Redes Conectadas:* `192.168.0.64` e `192.168.0.128`.
    * *Rede NÃO Conectada:* `192.168.0.0`. (Precisamos ensinar o caminho para esta rede).


O segredo aqui é o conceito de **Next Hop** (Próximo Salto): o endereço de IP do roteador vizinho que está no caminho para o destino.

---

### **5.7. Configurando o Roteador Aluno (Esquerda)**
O Roteador Auno conhece as redes à sua volta, mas não sabe como chegar na rede do PC da direita (`192.168.0.128`).
1.  Clique no Roteador **Aluno**.
2.  Vá na aba **Config** > **Static**.
3.  Preencha os campos:
    * **Network:** `192.168.0.128` (A rede de destino que ele não conhece).
    * **Mask:** `255.255.255.192`
    * **Next Hop:** `192.168.0.66` (O IP da interface do Roteador Professor que está virada para o Aluno).
4.  Clique em **Add**.

---

### **5.8. Configurando o Roteador Professor (Direita)**
Agora o inverso: o Professor precisa aprender o caminho para a rede da esquerda (`192.168.0.0`).
1.  Clique no Roteador **Professor**.
2.  Vá em **Config** > **Static**.
3.  Preencha os campos:
    * **Network:** `192.168.0.0` (A rede de destino à esquerda).
    * **Mask:** `255.255.255.192`
    * **Next Hop:** `192.168.0.65` (O IP da interface do Roteador Aluno que está virada para o Professor).
4.  Clique em **Add**.

---

### **5.9. Teste de Conectividade (Ping)**
Para verificar se tudo deu certo:
1.  Mude para o modo **Simulation** (canto inferior direito).
2.  Clique no filtro **Edit Filters** e deixe marcado apenas o protocolo **ICMP**.
3.  Use a ferramenta de "cartinha" (Add Simple PDU) e clique primeiro no **PC 01** (esquerda) e depois no **PC 04** (direita).
4.  Dê **Play** na simulação. Você verá o pacote indo até o destino e voltando com sucesso.
5.  Clique novamente em filtro **Edit Filters** e deixe marcado apenas o protocolo **TCP**.
6.  Use novamente a ferramenta de "cartinha" (Add Simple PDU) e clique primeiro no **PC 01** (esquerda) e depois no **PC 04** (direita).
7.  Dê **Play** na simulação. Você verá o pacote indo até o destino e voltando com sucesso.
8.  Faça o mesmo para o protocolo UDP. 

---

### **Dica de Diagnóstico**
É normal que o primeiro ping falhe no Packet Tracer (timeout). Se isso acontecer, apague o teste e tente novamente; na segunda vez, o pacote deve chegar ao destino sem problemas.

---

## 6. Impressora compartilhada

### 6.1 Desafio prático:

* Colocar impressora em uma subrede
* Garantir acesso de todas as outras

### 6.2 Teste:

* Ping
* Envio de “impressão”

---

## 7. TCP vs UDP (exploração prática)

### 7.1 Simular envios de pacotes

* Simular envio de pacote
* Observar diferença no modo simulation

| TCP         | UDP             |
| ----------- | --------------- |
| Confiável   | Rápido          |
| Confirmação | Sem confirmação |
| Mais lento  | Mais leve       |

---

## 8. Testes finais (validação)

Checklist do aluno:

* ✅ PCs se comunicam dentro da subrede
* ✅ PCs acessam outras subredes
* ✅ Impressora acessível por todos
* ✅ Ping entre todos os dispositivos



Agora seu laboratório de sub-redes e roteamento estático com teste UDP e TCP está completo!

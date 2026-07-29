# TechStart Network Lab

## 📌 Sobre o projeto

Este projeto consiste na criação de uma infraestrutura de rede corporativa simulada utilizando o **Cisco Packet Tracer**.

O laboratório representa uma empresa fictícia chamada **TechStart**, que necessita melhorar sua organização de rede, separando seus departamentos e criando uma infraestrutura mais eficiente, segura e escalável.

O objetivo é aplicar na prática conceitos fundamentais de redes de computadores, simulando um ambiente próximo ao encontrado em uma empresa real.

---

# 🏢 Cenário da empresa

A empresa TechStart possui os seguintes departamentos:

* Financeiro
* Tecnologia da Informação (TI)
* Recursos Humanos (RH)
* Diretoria

Atualmente, todos os computadores estão conectados na mesma rede, dificultando o gerenciamento, organização e expansão da infraestrutura.

A equipe de TI solicitou uma nova arquitetura de rede contendo:

* Separação dos departamentos utilizando VLANs.
* Melhor organização dos endereços IP.
* Configuração automática dos dispositivos.
* Comunicação entre diferentes redes.
* Estrutura preparada para crescimento futuro.

---

# 🎯 Objetivos do projeto

Neste laboratório serão implementados:

* Segmentação da rede utilizando VLANs.
* Comunicação entre switches através de links Trunk.
* Roteamento entre VLANs utilizando Router-on-a-Stick.
* Planejamento de endereçamento IP utilizando VLSM.
* Distribuição automática de endereços IP utilizando DHCP.
* Testes de conectividade para validar o funcionamento da rede.

---

# 🛠️ Ferramenta utilizada

* Cisco Packet Tracer

---

# 🌐 Tecnologias e conceitos aplicados

## VLAN (Virtual Local Area Network)

As VLANs foram utilizadas para separar logicamente os departamentos da empresa, criando redes independentes dentro da mesma infraestrutura física.

## Trunk

Os links Trunk foram utilizados para transportar múltiplas VLANs entre switches através de uma única conexão utilizando o protocolo IEEE 802.1Q.

## VLSM (Variable Length Subnet Mask)

O VLSM foi aplicado para dividir a rede IP de forma eficiente, criando sub-redes de diferentes tamanhos conforme a necessidade de cada departamento.

## Router-on-a-Stick

O Router-on-a-Stick foi utilizado para permitir a comunicação entre diferentes VLANs utilizando subinterfaces em uma única interface física do roteador.

## DHCP (Dynamic Host Configuration Protocol)

O DHCP foi configurado para distribuir automaticamente:

* Endereço IP.
* Máscara de sub-rede.
* Gateway padrão.
* Servidor DNS.

---

# 🖥️ Estrutura da rede

A rede foi dividida utilizando VLANs:

| VLAN    | Departamento | Quantidade de hosts |
| ------- | ------------ | ------------------- |
| VLAN 10 | Financeiro   | 50 dispositivos     |
| VLAN 20 | TI           | 20 dispositivos     |
| VLAN 30 | RH           | 10 dispositivos     |
| VLAN 40 | Diretoria    | 5 dispositivos      |

---

# 🌐 Planejamento de endereçamento IP (VLSM)

A rede inicial disponibilizada para a empresa:

```
192.168.1.0/24
```

O método VLSM foi utilizado para criar sub-redes conforme a quantidade de dispositivos de cada setor.

| VLAN    | Departamento | Rede             | Máscara         | Hosts disponíveis | Gateway       |
| ------- | ------------ | ---------------- | --------------- | ----------------- | ------------- |
| VLAN 10 | Financeiro   | 192.168.1.0/26   | 255.255.255.192 | 62 hosts          | 192.168.1.1   |
| VLAN 20 | TI           | 192.168.1.64/27  | 255.255.255.224 | 30 hosts          | 192.168.1.65  |
| VLAN 30 | RH           | 192.168.1.96/28  | 255.255.255.240 | 14 hosts          | 192.168.1.97  |
| VLAN 40 | Diretoria    | 192.168.1.112/28 | 255.255.255.240 | 14 hosts          | 192.168.1.113 |

---

# 📍 Distribuição dos endereços IP

## VLAN 10 - Financeiro

Rede:

```
192.168.1.0/26
```

Máscara:

```
255.255.255.192
```

Gateway:

```
192.168.1.1
```

Faixa disponível para dispositivos:

```
192.168.1.2 - 192.168.1.62
```

Broadcast:

```
192.168.1.63
```

---

## VLAN 20 - TI

Rede:

```
192.168.1.64/27
```

Máscara:

```
255.255.255.224
```

Gateway:

```
192.168.1.65
```

Faixa disponível para dispositivos:

```
192.168.1.66 - 192.168.1.94
```

Broadcast:

```
192.168.1.95
```

---

## VLAN 30 - RH

Rede:

```
192.168.1.96/28
```

Máscara:

```
255.255.255.240
```

Gateway:

```
192.168.1.97
```

Faixa disponível para dispositivos:

```
192.168.1.98 - 192.168.1.110
```

Broadcast:

```
192.168.1.111
```

---

## VLAN 40 - Diretoria

Rede:

```
192.168.1.112/28
```

Máscara:

```
255.255.255.240
```

Gateway:

```
192.168.1.113
```

Faixa disponível para dispositivos:

```
192.168.1.114 - 192.168.1.126
```

Broadcast:

```
192.168.1.127
```

---

# 📡 Topologia da rede

Estrutura utilizada:

```
                 Router 1941
                     |
                  Trunk
                     |
                Switch Core
                     |
        ┌────────────┼────────────┐
        |            |            |
     SW-FIN      SW-TI-RH       SW-DIR

     VLAN 10    VLAN 20/30     VLAN 40
```

Imagem da topologia criada no Cisco Packet Tracer:

**(Adicionar imagem aqui)**

---

# ⚙️ Configurações realizadas

## VLANs

VLANs configuradas:

```
VLAN 10 - FINANCEIRO
VLAN 20 - TI
VLAN 30 - RH
VLAN 40 - DIRETORIA
```

Print da configuração:

**(Adicionar imagem aqui)**

---

## Links Trunk

Links configurados:

```
SW-Core Fa0/10  → SW-FIN
SW-Core Fa0/15  → SW-TI-RH
SW-Core Fa0/20  → SW-DIR
SW-Core Gi0/1   → Router
```

Todos configurados utilizando:

```
802.1Q Trunk
```

Print:

**(Adicionar imagem aqui)**

---

## Router-on-a-Stick

Subinterfaces configuradas no roteador:

```
GigabitEthernet0/0.10 → VLAN 10
GigabitEthernet0/0.20 → VLAN 20
GigabitEthernet0/0.30 → VLAN 30
GigabitEthernet0/0.40 → VLAN 40
```

Print:

**(Adicionar imagem aqui)**

---

## DHCP

Pools DHCP configurados:

```
FINANCEIRO
TI
RH
DIRETORIA
```

Cada pool entrega:

* IP
* Máscara
* Gateway
* DNS

Print:

**(Adicionar imagem aqui)**

---

# 🧪 Testes realizados

Testes realizados:

* [x] Dispositivo recebendo IP via DHCP.
* [ ] Comunicação dentro das VLANs.
* [ ] Comunicação entre VLANs.
* [x] Funcionamento dos links Trunk.
* [ ] Testes de conectividade utilizando ping.

Prints dos testes:

**(Adicionar imagem aqui)**

---

# 📸 Imagens do projeto

Adicionar imagens:

* Topologia da rede.
* Configuração das VLANs.
* Funcionamento do DHCP.
* Configuração do Router-on-a-Stick.
* Testes de conectividade.

---

# 📚 Objetivo de aprendizado

Este projeto tem como objetivo desenvolver conhecimentos práticos em:

* Fundamentos de redes.
* VLANs e segmentação de redes.
* Configuração de equipamentos Cisco.
* Planejamento de endereçamento IP.
* VLSM.
* DHCP.
* Roteamento entre redes.
* Conceitos utilizados em redes e cibersegurança.

---

# 🚧 Status do projeto

Em desenvolvimento.

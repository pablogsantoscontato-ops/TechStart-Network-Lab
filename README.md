# TechStart Network Lab

## 📌 Sobre o projeto

Este projeto consiste na criação de uma infraestrutura de rede corporativa simulada utilizando o **Cisco Packet Tracer**.

O laboratório representa uma empresa fictícia chamada **TechStart**, que precisa melhorar sua organização de rede, separando seus departamentos e criando uma infraestrutura mais eficiente e escalável.

O objetivo é aplicar na prática conceitos fundamentais de redes de computadores, simulando um ambiente próximo ao encontrado em uma empresa real.

---

# 🏢 Cenário da empresa

A empresa TechStart possui os seguintes departamentos:

* Financeiro
* Tecnologia da Informação (TI)
* Recursos Humanos (RH)
* Diretoria

Atualmente, todos os computadores estão conectados na mesma rede, dificultando a organização, gerenciamento e expansão da infraestrutura.

A equipe de TI solicitou uma nova arquitetura de rede com:

* Separação dos departamentos.
* Melhor organização dos endereços IP.
* Configuração automática dos dispositivos.
* Comunicação eficiente entre equipamentos de rede.
* Estrutura preparada para crescimento futuro.

---

# 🎯 Objetivos do projeto

Neste laboratório serão implementados:

* Segmentação da rede utilizando VLANs.
* Comunicação entre switches através de links Trunk.
* Planejamento de endereçamento IP utilizando VLSM.
* Distribuição automática de endereços IP utilizando DHCP.
* Testes de conectividade para validar o funcionamento da rede.

---

# 🛠️ Ferramenta utilizada

* Cisco Packet Tracer

---

# 🌐 Tecnologias e conceitos aplicados

## VLAN (Virtual Local Area Network)

As VLANs serão utilizadas para separar logicamente os departamentos da empresa, criando redes independentes dentro da mesma infraestrutura física.

## Trunk

Os links Trunk serão utilizados para permitir que múltiplas VLANs sejam transportadas entre switches através de uma única conexão.

## VLSM (Variable Length Subnet Mask)

O VLSM será aplicado para dividir a rede IP de forma eficiente, criando sub-redes de diferentes tamanhos conforme a necessidade de cada departamento.

## DHCP (Dynamic Host Configuration Protocol)

O DHCP será utilizado para configurar automaticamente os computadores da rede, fornecendo:

* Endereço IP.
* Máscara de sub-rede.
* Gateway.
* Servidor DNS.

## Subnetting

O subnetting será utilizado para dividir uma rede maior em redes menores e organizadas.

---

# 🖥️ Estrutura da rede

A rede será dividida utilizando VLANs:

| VLAN    | Departamento | Quantidade de hosts |
| ------- | ------------ | ------------------- |
| VLAN 10 | Financeiro   | 50 dispositivos     |
| VLAN 20 | TI           | 20 dispositivos     |
| VLAN 30 | RH           | 10 dispositivos     |
| VLAN 40 | Diretoria    | 5 dispositivos      |

---

# 🌐 Planejamento de endereçamento IP (VLSM)

A rede inicial disponibilizada para a empresa será:

```
192.168.1.0/24
```

O método VLSM será utilizado para criar sub-redes de acordo com a necessidade de cada departamento.

| VLAN    | Departamento | Rede             | Máscara         | Hosts disponíveis |
| ------- | ------------ | ---------------- | --------------- | ----------------- |
| VLAN 10 | Financeiro   | 192.168.1.0/26   | 255.255.255.192 | 62 hosts          |
| VLAN 20 | TI           | 192.168.1.64/27  | 255.255.255.224 | 30 hosts          |
| VLAN 30 | RH           | 192.168.1.96/28  | 255.255.255.240 | 14 hosts          |
| VLAN 40 | Diretoria    | 192.168.1.112/28 | 255.255.255.240 | 14 hosts          |

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

Faixa de hosts:

```
192.168.1.1 - 192.168.1.62
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

Faixa de hosts:

```
192.168.1.65 - 192.168.1.94
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

Faixa de hosts:

```
192.168.1.97 - 192.168.1.110
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

Faixa de hosts:

```
192.168.1.113 - 192.168.1.126
```

Broadcast:

```
192.168.1.127
```

---

# 📡 Topologia da rede

Imagem da topologia criada no Cisco Packet Tracer:

**(Adicionar imagem aqui)**

---

# ⚙️ Configurações realizadas

## VLANs

**(Adicionar informações das VLANs configuradas aqui)**

---

## Links Trunk

**(Adicionar informações dos links Trunk aqui)**

---

## DHCP

**(Adicionar informações da configuração DHCP aqui)**

---

# 🧪 Testes realizados

Testes que serão realizados:

* [ ] Dispositivos recebendo IP via DHCP.
* [ ] Comunicação dentro das VLANs.
* [ ] Funcionamento dos links Trunk.
* [ ] Testes de conectividade utilizando ping.

**(Adicionar prints dos testes aqui)**

---

# 📸 Imagens do projeto

Adicionar imagens:

* Topologia da rede.
* Configuração das VLANs.
* Funcionamento do DHCP.
* Testes de conectividade.

---

# 📚 Objetivo de aprendizado

Este projeto tem como objetivo desenvolver conhecimentos práticos em:

* Fundamentos de redes.
* Planejamento de endereçamento IP.
* Configuração de redes Cisco.
* Segmentação de redes.
* Organização de infraestrutura.
* Conceitos utilizados em redes e cibersegurança.

---

# 🚧 Status do projeto

Em desenvolvimento.

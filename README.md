# 🖥️ TechStart Network Lab

<div align="center">

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco_Packet_Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)
![Networking](https://img.shields.io/badge/Networking-0073E6?style=for-the-badge&logo=network&logoColor=white)
![VLAN](https://img.shields.io/badge/VLAN-0052CC?style=for-the-badge&logo=cisco&logoColor=white)
![DHCP](https://img.shields.io/badge/DHCP-FF6B00?style=for-the-badge&logo=dhcp&logoColor=white)

<img src="https://img.shields.io/badge/Status-Concluído-success?style=for-the-badge" />
<img src="https://img.shields.io/badge/Versão-1.0-blue?style=for-the-badge" />

</div>

---

## 📌 Sobre o projeto

Projeto de infraestrutura de rede corporativa desenvolvido utilizando o **Cisco Packet Tracer**.

O cenário representa a empresa fictícia **TechStart**, que precisava melhorar sua organização de rede através da separação dos departamentos, controle de endereçamento IP e comunicação eficiente entre os dispositivos.

Foram aplicados conceitos fundamentais de redes como **VLANs, Trunk, VLSM, Router-on-a-Stick e DHCP**.

---

<div align="center">

## 🎯 Objetivos do projeto

</div>

- Separar departamentos utilizando VLANs.
- Organizar o endereçamento IP utilizando VLSM.
- Permitir comunicação entre diferentes VLANs.
- Automatizar a configuração dos dispositivos através do DHCP.
- Validar o funcionamento da rede através de testes de conectividade.

---

<div align="center">

## 🛠️ Ferramenta utilizada

</div>

- Cisco Packet Tracer

---

<div align="center">

## 🌐 Conceitos aplicados

</div>

### VLAN (Virtual Local Area Network)

VLANs permitem dividir uma rede física em redes lógicas independentes.

Neste projeto, cada departamento recebeu uma VLAN própria, melhorando a organização e reduzindo o tráfego de broadcast.

| VLAN | Departamento |
|---|---|
| VLAN 10 | Financeiro |
| VLAN 20 | TI |
| VLAN 30 | RH |
| VLAN 40 | Diretoria |

---

### Trunk (802.1Q)

O Trunk permite transportar múltiplas VLANs através de um único link entre equipamentos de rede.

Foi utilizado para permitir que os switches e o roteador trocassem informações de todas as VLANs.

---

### VLSM (Variable Length Subnet Mask)

O VLSM permite criar sub-redes de tamanhos diferentes conforme a necessidade de cada departamento, evitando desperdício de endereços IP.

Rede inicial:

```
192.168.1.0/24
```

Planejamento:

| VLAN | Rede | Máscara | Gateway |
|---|---|---|---|
| VLAN 10 | 192.168.1.0/26 | 255.255.255.192 | 192.168.1.1 |
| VLAN 20 | 192.168.1.64/27 | 255.255.255.224 | 192.168.1.65 |
| VLAN 30 | 192.168.1.96/28 | 255.255.255.240 | 192.168.1.97 |
| VLAN 40 | 192.168.1.112/28 | 255.255.255.240 | 192.168.1.113 |

---

### Router-on-a-Stick

O Router-on-a-Stick permite que um único roteador realize a comunicação entre VLANs utilizando subinterfaces.

Cada subinterface representa o gateway de uma VLAN.

---

### DHCP (Dynamic Host Configuration Protocol)

O DHCP permite que os computadores recebam automaticamente:

- Endereço IP.
- Máscara de rede.
- Gateway.
- Configurações necessárias para comunicação.

Neste projeto, o roteador foi configurado como servidor DHCP.

---

<div align="center">

## 🏢 Estrutura da rede

</div>

| VLAN | Departamento | Quantidade de hosts |
|---|---|---|
| VLAN 10 | Financeiro | 50 |
| VLAN 20 | TI | 20 |
| VLAN 30 | RH | 10 |
| VLAN 40 | Diretoria | 5 |

---

<div align="center">

## 📡 Topologia da rede

</div>

![Topologia da rede](screenshots/topology.png)

---

<div align="center">

## ⚙️ Configurações realizadas

</div>

### 1. Criação das VLANs

As VLANs foram criadas nos switches para separar os departamentos.

Comandos utilizados:

```bash
enable
configure terminal

vlan 10
name FINANCEIRO

vlan 20
name TI

vlan 30
name RH

vlan 40
name DIRETORIA

end
```

Verificação:

```bash
show vlan brief
```

Resultado:

![VLANs configuradas](screenshots/vlans.png)

---

### 2. Configuração dos links Trunk

Os links Trunk foram configurados para permitir a passagem das VLANs entre os equipamentos.

Comando utilizado:

```bash
interface fastEthernet 0/10

switchport mode trunk
```

Verificação:

```bash
show interfaces trunk
```

Resultado:

![Links Trunk](screenshots/trunk.png)

---

### 3. Configuração do Router-on-a-Stick

Foram criadas subinterfaces no roteador para cada VLAN.

#### VLAN 10

```bash
interface gigabitEthernet 0/0.10

encapsulation dot1Q 10

ip address 192.168.1.1 255.255.255.192
```

#### VLAN 20

```bash
interface gigabitEthernet 0/0.20

encapsulation dot1Q 20

ip address 192.168.1.65 255.255.255.224
```

#### VLAN 30

```bash
interface gigabitEthernet 0/0.30

encapsulation dot1Q 30

ip address 192.168.1.97 255.255.255.240
```

#### VLAN 40

```bash
interface gigabitEthernet 0/0.40

encapsulation dot1Q 40

ip address 192.168.1.113 255.255.255.240
```

Verificação:

```bash
show ip interface brief
```

Resultado:

![Interfaces do roteador](screenshots/router-interfaces.png)

---

### 4. Configuração DHCP

O roteador foi configurado como servidor DHCP para distribuir IPs automaticamente.

#### Pool Financeiro

```bash
ip dhcp pool FINANCEIRO

network 192.168.1.0 255.255.255.192

default-router 192.168.1.1
```

#### Pool TI

```bash
ip dhcp pool TI

network 192.168.1.64 255.255.255.224

default-router 192.168.1.65
```

#### Pool RH

```bash
ip dhcp pool RH

network 192.168.1.96 255.255.255.240

default-router 192.168.1.97
```

#### Pool Diretoria

```bash
ip dhcp pool DIRETORIA

network 192.168.1.112 255.255.255.240

default-router 192.168.1.113
```

Verificação dos pools:

```bash
show ip dhcp pool
```

![DHCP Pools](screenshots/dhcp-pools.png)

Verificação dos IPs entregues:

```bash
show ip dhcp binding
```

![DHCP Bindings](screenshots/dhcp-bindings.png)

---

<div align="center">

## 🧪 Testes de conectividade

</div>

Foram realizados testes utilizando o comando:

```bash
ping
```

Exemplo:

```bash
ping 192.168.1.65
```

Teste entre VLANs:

```bash
ping 192.168.1.1
```

Resultado:

![Testes de conectividade](screenshots/ping-tests.png)

---

<div align="center">

## 📚 Conhecimentos desenvolvidos

</div>

Durante o projeto foram praticados:

- ✅ Configuração de equipamentos Cisco.
- ✅ Criação e gerenciamento de VLANs.
- ✅ Configuração de links Trunk.
- ✅ Endereçamento IPv4.
- ✅ Subnetting e VLSM.
- ✅ Roteamento entre VLANs.
- ✅ Configuração de DHCP.
- ✅ Troubleshooting utilizando comandos Cisco.

---

<div align="center">

## ✅ Status do projeto

</div>

<div align="center">

### 🟢 Concluído

---

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

Estudante de Segurança Cibernética com foco em Redes e Cibersegurança.

---

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Desenvolvido com ❤️ para o aprendizado de redes</sub>

</div>

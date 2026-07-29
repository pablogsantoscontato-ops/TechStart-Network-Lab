# 🖥️ TechStart Network Lab

## 📌 Sobre o projeto

Este projeto consiste na criação de uma infraestrutura de rede corporativa simulada utilizando o **Cisco Packet Tracer**.

A empresa fictícia **TechStart** possuía uma rede sem segmentação, onde todos os dispositivos estavam conectados no mesmo ambiente. O objetivo do projeto foi desenvolver uma nova arquitetura de rede mais organizada, segura e escalável.

Foram aplicados conceitos fundamentais de redes de computadores, como:

- VLANs
- Trunking
- VLSM
- Router-on-a-Stick
- DHCP
- Subnetting
- Testes de conectividade

---

# 🏢 Cenário da empresa

A TechStart possui quatro departamentos:

- Financeiro
- Tecnologia da Informação (TI)
- Recursos Humanos (RH)
- Diretoria

A nova infraestrutura foi criada para:

- Separar os departamentos logicamente.
- Melhorar a organização da rede.
- Reduzir domínios de broadcast.
- Facilitar o gerenciamento.
- Preparar a rede para expansão futura.

---

# 🎯 Objetivos do projeto

Neste laboratório foram implementados:

✅ Segmentação utilizando VLANs  
✅ Comunicação entre switches através de Trunk  
✅ Planejamento IP utilizando VLSM  
✅ Roteamento entre VLANs utilizando Router-on-a-Stick  
✅ Distribuição automática de IP utilizando DHCP  
✅ Testes de conectividade

---

# 🛠️ Ferramenta utilizada

- Cisco Packet Tracer

---

# 🌐 Tecnologias e conceitos aplicados

## VLAN (Virtual Local Area Network)

As VLANs foram utilizadas para separar logicamente os departamentos da empresa dentro da mesma infraestrutura física.

| VLAN | Departamento | Hosts |
|---|---|---|
| 10 | Financeiro | 50 |
| 20 | TI | 20 |
| 30 | RH | 10 |
| 40 | Diretoria | 5 |

---

# 🌐 Planejamento IP (VLSM)

Rede inicial:

```
192.168.1.0/24
```

Divisão utilizando VLSM:

| VLAN | Departamento | Rede | Máscara | Gateway |
|-|-|-|-|-|
| 10 | Financeiro | 192.168.1.0/26 | 255.255.255.192 | 192.168.1.1 |
| 20 | TI | 192.168.1.64/27 | 255.255.255.224 | 192.168.1.65 |
| 30 | RH | 192.168.1.96/28 | 255.255.255.240 | 192.168.1.97 |
| 40 | Diretoria | 192.168.1.112/28 | 255.255.255.240 | 192.168.1.113 |

---

# 📡 Topologia da rede

![Topologia da rede](screenshots/topology.png)

---

# ⚙️ Configurações realizadas

# 1. Criação das VLANs

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

![VLANs](screenshots/vlans.png)

---

# 2. Configuração das portas de acesso

Exemplo:

```bash
interface fastEthernet 0/1

switchport mode access
switchport access vlan 10

end
```

Cada departamento recebeu suas respectivas portas dentro da VLAN correspondente.

---

# 3. Configuração dos links Trunk

Os links entre switches foram configurados como trunk para transportar múltiplas VLANs.

Comandos:

```bash
interface fastEthernet 0/10

switchport mode trunk

end
```

Verificação:

```bash
show interfaces trunk
```

Resultado:

![Trunk](screenshots/trunk.png)

---

# 4. Configuração do Router-on-a-Stick

O roteador foi configurado utilizando subinterfaces para realizar o roteamento entre VLANs.

Exemplo:

```bash
interface gigabitEthernet 0/0.10

encapsulation dot1Q 10

ip address 192.168.1.1 255.255.255.192
```

VLAN 20:

```bash
interface gigabitEthernet 0/0.20

encapsulation dot1Q 20

ip address 192.168.1.65 255.255.255.224
```

VLAN 30:

```bash
interface gigabitEthernet 0/0.30

encapsulation dot1Q 30

ip address 192.168.1.97 255.255.255.240
```

VLAN 40:

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

# 5. Configuração DHCP

O roteador foi utilizado como servidor DHCP.

Exemplo:

```bash
ip dhcp pool FINANCEIRO

network 192.168.1.0 255.255.255.192

default-router 192.168.1.1
```

Pool TI:

```bash
ip dhcp pool TI

network 192.168.1.64 255.255.255.224

default-router 192.168.1.65
```

Pool RH:

```bash
ip dhcp pool RH

network 192.168.1.96 255.255.255.240

default-router 192.168.1.97
```

Pool Diretoria:

```bash
ip dhcp pool DIRETORIA

network 192.168.1.112 255.255.255.240

default-router 192.168.1.113
```

Verificação:

```bash
show ip dhcp pool
```

![Pools DHCP](screenshots/dhcp-pools.png)

Endereços entregues:

```bash
show ip dhcp binding
```

![DHCP Bindings](screenshots/dhcp-bindings.png)

---

# 🧪 Testes realizados

Foram realizados testes de conectividade utilizando o comando:

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

# 📚 Conhecimentos desenvolvidos

Durante o projeto foram praticados:

- Configuração de equipamentos Cisco.
- Segmentação de redes com VLAN.
- Comunicação utilizando Trunk.
- Planejamento de endereçamento IP.
- Subnetting e VLSM.
- Configuração de DHCP.
- Roteamento entre VLANs.
- Análise e troubleshooting de redes.

---

# 🚧 Status do projeto

✅ Concluído

---

# 👨‍💻 Autor

Pablo Gonçalves Santos

Estudante de Segurança Cibernética com foco em Redes e Cibersegurança.

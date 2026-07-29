# 🖥️ TechStart Network Lab

## 📌 Sobre o projeto

Projeto de infraestrutura de rede corporativa desenvolvido no **Cisco Packet Tracer**.

O objetivo foi criar uma rede organizada para a empresa fictícia **TechStart**, realizando a separação dos departamentos através de VLANs, configuração de Trunks, planejamento IP com VLSM, roteamento entre VLANs e distribuição automática de endereços utilizando DHCP.

---

# 🎯 Objetivos

- Implementar segmentação de rede utilizando VLANs.
- Configurar comunicação entre switches através de links Trunk.
- Realizar subnetting utilizando VLSM.
- Configurar Router-on-a-Stick para comunicação entre VLANs.
- Implementar DHCP para configuração automática dos dispositivos.
- Realizar testes de conectividade.

---

# 🏢 Estrutura da rede

Departamentos:

| VLAN | Departamento | Hosts |
|---|---|---|
| 10 | Financeiro | 50 |
| 20 | TI | 20 |
| 30 | RH | 10 |
| 40 | Diretoria | 5 |

---

# 📡 Topologia da rede

![Topologia da rede](screenshots/topology.png)

---

# 🌐 Planejamento IP (VLSM)

Rede inicial:

```
192.168.1.0/24
```

| VLAN | Rede | Máscara | Gateway |
|---|---|---|---|
| VLAN 10 | 192.168.1.0/26 | 255.255.255.192 | 192.168.1.1 |
| VLAN 20 | 192.168.1.64/27 | 255.255.255.224 | 192.168.1.65 |
| VLAN 30 | 192.168.1.96/28 | 255.255.255.240 | 192.168.1.97 |
| VLAN 40 | 192.168.1.112/28 | 255.255.255.240 | 192.168.1.113 |

---

# ⚙️ Configurações realizadas

## 1. Criação das VLANs

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

# 2. Configuração dos links Trunk

Os links entre os switches foram configurados como trunk para transportar múltiplas VLANs.

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

# 3. Configuração do Router-on-a-Stick

O roteador foi configurado com subinterfaces para realizar o roteamento entre VLANs.

Exemplo VLAN 10:

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

# 4. Configuração DHCP

O roteador foi configurado como servidor DHCP para entregar IP automaticamente aos dispositivos.

Exemplo:

```bash
ip dhcp pool FINANCEIRO

network 192.168.1.0 255.255.255.192

default-router 192.168.1.1
```

Verificação dos pools:

```bash
show ip dhcp pool
```

![Pools DHCP](screenshots/dhcp-pools.png)

Verificação dos IPs entregues:

```bash
show ip dhcp binding
```

![DHCP Bindings](screenshots/dhcp-bindings.png)

---

# 🧪 Testes de conectividade

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

# 📚 Conceitos aprendidos

Durante o desenvolvimento do projeto foram aplicados:

- VLAN e segmentação de redes.
- Trunk 802.1Q.
- Endereçamento IPv4.
- Subnetting e VLSM.
- Router-on-a-Stick.
- DHCP.
- Troubleshooting utilizando comandos Cisco.

---

# 🛠️ Ferramentas utilizadas

- Cisco Packet Tracer
- Equipamentos Cisco simulados

---

# ✅ Status do projeto

Concluído

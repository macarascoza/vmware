# Definições infraestrutura VMware.

# Templates

Dois Tipos:

OVA => VMware
OVF => VMware e vários players

Padrão OVF possui varios arquivos.
Padrão OVA é um único arquivo compactado.


# Estação Virtual VM

 Disco THICK x THIN

>[!IMPORTANT]
>HOJE NÃO EXISTE DIFERENÇA DE DESEMPENHO ENTRE DISCOS EAGER / LAZY THICK E THIN

Thick:

Provisiona no datastore o espaço do disco imediatament, prepara os blocos do disco, inserindo zeros na hora ou antes de escrever algum bloco de dados da VM.
possui um gerenciamento do ambiente e cuidados menores.

Tipos:
Thick Provision Lazy Zeroed: opção padrão para praticamente todas as aplicações, exceto as que requerem o Eager Zeroed.
Thick Provision Eager Zeroed: normalmente utilizado por VM que irão utilizar a funcionalidade Fault Tolerance do VMware, ou se for utilizar a funcionalidade do Microsoft Failover Cluster dentro das máquinas virtuais.

Thin: 

Thin Provision: normalmente utilizado quando se deseja provisionar mais espaço que o total de espaço físico disponível, porém pode causar problemas se todas as VMs utilizarem todo o espaço disponível do datastore.
Não provisiona o espaço em disco no datastore e nem prepara inserindo zeros antes de escrever um bloco de dados.

# Adaptadores de Rede

Dois tipos de placa de rede:

Emulados:

E1000 | E1000E	=> Adaptador Intel de 1 Gbps

VM => E1000 =>  VMM (Virtual Machine Monitor)  => Hypervisor => HW

Paravirtualizados:

>[!IMPORTANT]
>Recomendado pela VMware é utilizar o VMXNET3

VMXNET / VMXNET2 / VMXNET3

VMXNET e VMXNET3 (hoje)

VM => VMXNET3 => …(bypass VMM) … =>  Hypervisor => HW

Dependem da instalação do VMware Tools!

VMXNET	=> 10/100 Mbps
VMXNET2	=> 1 Gbps (não existe mais)
VMXNET3	=> 10 Gbps


# Vcenter - vSphere
vSphere 8 necessario vCenter + ESXi o ambiente do vCenter deve ter hosts no mínimo ESXi 6.7, 7.0 e 8.0

>[!IMPORTANT]
>8000 mil estações virtuais por Cluster, estações virtuais por host físico.
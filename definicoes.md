# Definições infraestrutura VMware.

## Gerenciamento de CPU

VM =>  Sockets e Cores = sockets x cores = quantidade de vCPUs (uma vCPU para uma CPU física).

Um cenário com uma VM 8 vCPUs pode ter as configurações:

1 socket e 8 cores (recomendado)
2 sockets e 4 cores
4 sockets e 2 cores
8 sockets e 1 core 

Depender do SO instalado no Guest.

NUMA - Non-Uniform Memory Access

Tecnologia foi criada pela IBM que hoje está disponível em todos os servidores físicos (hosts)

## Templates

Dois Tipos:

OVA => VMware
OVF => VMware e vários players

Padrão OVF possui varios arquivos.
Padrão OVA é um único arquivo compactado.

## Estação Virtual VM

 ### Disco THICK x THIN

>[!IMPORTANT]
>HOJE NÃO EXISTE DIFERENÇA DE DESEMPENHO ENTRE DISCOS EAGER / LAZY THICK E THIN

#### Thick:

Provisiona no datastore o espaço do disco imediatament, prepara os blocos do disco, inserindo zeros na hora ou antes de escrever algum bloco de dados da VM.
possui um gerenciamento do ambiente e cuidados menores.

Tipos:
Thick Provision Lazy Zeroed: opção padrão para praticamente todas as aplicações, exceto as que requerem o Eager Zeroed.
Thick Provision Eager Zeroed: normalmente utilizado por VM que irão utilizar a funcionalidade Fault Tolerance do VMware, ou se for utilizar a funcionalidade do Microsoft Failover Cluster dentro das máquinas virtuais.

#### Thin: 

Thin Provision: normalmente utilizado quando se deseja provisionar mais espaço que o total de espaço físico disponível, porém pode causar problemas se todas as VMs utilizarem todo o espaço disponível do datastore.
Não provisiona o espaço em disco no datastore e nem prepara inserindo zeros antes de escrever um bloco de dados.

## Adaptadores de Rede

Dois tipos de placa de rede:

### Emulados:

E1000 | E1000E	=> Adaptador Intel de 1 Gbps

VM => E1000 =>  VMM (Virtual Machine Monitor)  => Hypervisor => HW

### Paravirtualizados:

>[!IMPORTANT]
>Recomendado pela VMware é utilizar o VMXNET3

VMXNET / VMXNET2 / VMXNET3

VMXNET e VMXNET3 (hoje)

VM => VMXNET3 => …(bypass VMM) … =>  Hypervisor => HW

Dependem da instalação do VMware Tools!

VMXNET	=> 10/100 Mbps
VMXNET2	=> 1 Gbps (não existe mais)
VMXNET3	=> 10 Gbps

## Vcenter - vSphere
vSphere 8 necessario vCenter + ESXi o ambiente do vCenter deve ter hosts no mínimo ESXi 6.7, 7.0 e 8.0

>[!IMPORTANT]
>8000 mil estações virtuais por Cluster, estações virtuais por host físico [Link](https://configmax.esp.vmware.com/guest?vmwareproduct=vSphere&release=vSphere%208.0&categories=2-0).

## DRS
Balanceamento de carga automatizado 0 DRS distribui as cargas de trabalho da máquina virtual pelos hosts do vSphere em um cluster e monitora os recursos disponíveis para você. Com base no nível de automação, o DRS migrará (VMware vSphere vMotion) máquinas virtuais para outros hosts no cluster para maximizar o desempenho.

## HA

O VMware vSphere High Availability proporciona a disponibilidade exigida pela maioria dos aplicativos em execução em máquinas virtuais, independentemente do sistema operacional e dos aplicativos em execução. O High Availability fornece proteção uniforme e econômica contra falhas de hardware e sistema operacional no seu ambiente de TI virtualizado. O High Availability permite:

 
. Monitorar hosts e máquinas virtuais do VMware vSphere para detectar falhas de hardware e sistema operacional guest.
. Reiniciar as máquinas virtuais em outros hosts vSphere no cluster sem intervenção manual quando uma interrupção do servidor for detectada.
. Reduzir o tempo de inatividade do aplicativo ao reiniciar automaticamente as máquinas virtuais após a detecção de uma falha no sistema operacional.

## Migração de estação virtual

>[!IMPORTANT]
>Necessário que os hosts estevam com o DRS habilitado, todos os datastores apresentados em todos os hosts físicos e virtual switches.

### Migração fria
A migração a frio é a migração de máquinas virtuais desligadas ou suspensas entre hosts em clusters, centros de dados e vCenter Server instâncias. Ao usar a migração a frio, você também pode mover discos associados de um repositório de dados para outro. [Leia mais](https://docs.vmware.com/br/VMware-vSphere/7.0/com.vmware.vsphere.vcenterhost.doc/GUID-98C18721-A4B0-4BD2-96BF-1BBC29391B3E.html)

### Migração com o vMotion
Se você precisar colocar um host offline para manutenção, poderá mover a máquina virtual para outro host. A migração com o vSphere vMotion permite que os processos da máquina virtual continuem funcionando durante a migração. [Leia mais](https://docs.vmware.com/br/VMware-vSphere/7.0/com.vmware.vsphere.vcenterhost.doc/GUID-D19EA1CB-5222-49F9-A002-4F8692B92D63.html)

### Migração com Storage vMotion
Com o Storage vMotion, você pode migrar uma máquina virtual e seus arquivos de disco de um repositório de dados para outro enquanto a máquina virtual está em execução. Com o Storage vMotion, você pode mover as máquinas virtuais das matrizes para manutenção ou atualização. Você também tem a flexibilidade de otimizar discos para desempenho ou transformar tipos de disco, que você pode usar para recuperar espaço. [Leia mais](https://docs.vmware.com/br/VMware-vSphere/7.0/com.vmware.vsphere.vcenterhost.doc/GUID-AB266895-BAA4-4BF3-894E-47F99DC7B77F.html)

### Compatibilidade de CPU e EVC
vCenter Server executa verificações de compatibilidade antes de permitir a migração de máquinas virtuais em execução ou suspensas para garantir que a máquina virtual seja compatível com o host de destino. [Leia mais](https://docs.vmware.com/br/VMware-vSphere/7.0/com.vmware.vsphere.vcenterhost.doc/GUID-03E7E5F9-06D9-463F-A64F-D4EC20DAF22E.html)
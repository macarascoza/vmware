# Definicoes infraestrutura VMware.

# Categoria VM

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


# Vcenter
vSphere 8 necessario vCenter + ESXi o ambiente do vCenter deve ter hosts no mínimo ESXi 6.7, 7.0 e 8.0
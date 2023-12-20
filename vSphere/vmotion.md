# Migrcao de estacao virtual

>[!IMPORTANT]
>Necessário que os hosts estevam com o DRS habilitado, todos os datastores apresentados em todos os hosts físicos e virtual switches.

## Migração fria
A migração a frio é a migração de máquinas virtuais desligadas ou suspensas entre hosts em clusters, centros de dados e vCenter Server instâncias. Ao usar a migração a frio, você também pode mover discos associados de um repositório de dados para outro. [Leia mais](https://docs.vmware.com/br/VMware-vSphere/7.0/com.vmware.vsphere.vcenterhost.doc/GUID-98C18721-A4B0-4BD2-96BF-1BBC29391B3E.html)

## Migração com o vMotion
Se você precisar colocar um host offline para manutenção, poderá mover a máquina virtual para outro host. A migração com o vSphere vMotion permite que os processos da máquina virtual continuem funcionando durante a migração. [Leia mais](https://docs.vmware.com/br/VMware-vSphere/7.0/com.vmware.vsphere.vcenterhost.doc/GUID-D19EA1CB-5222-49F9-A002-4F8692B92D63.html)

## Migração com Storage vMotion
Com o Storage vMotion, você pode migrar uma máquina virtual e seus arquivos de disco de um repositório de dados para outro enquanto a máquina virtual está em execução. Com o Storage vMotion, você pode mover as máquinas virtuais das matrizes para manutenção ou atualização. Você também tem a flexibilidade de otimizar discos para desempenho ou transformar tipos de disco, que você pode usar para recuperar espaço. [Leia mais](https://docs.vmware.com/br/VMware-vSphere/7.0/com.vmware.vsphere.vcenterhost.doc/GUID-AB266895-BAA4-4BF3-894E-47F99DC7B77F.html)

## Compatibilidade de CPU e EVC
vCenter Server executa verificações de compatibilidade antes de permitir a migração de máquinas virtuais em execução ou suspensas para garantir que a máquina virtual seja compatível com o host de destino. [Leia mais](https://docs.vmware.com/br/VMware-vSphere/7.0/com.vmware.vsphere.vcenterhost.doc/GUID-03E7E5F9-06D9-463F-A64F-D4EC20DAF22E.html)
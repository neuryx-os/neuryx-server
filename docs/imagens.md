# Imagens previstas

Todas as imagens serão geradas pela mesma descrição KIWI (em `kiwi/`), com um
perfil por tipo. Nenhuma inclui driver NVIDIA, CUDA ou modelos de IA.

| Imagem | Formato | Uso previsto |
| --- | --- | --- |
| ISO de instalação | `.iso` (híbrida, BIOS e UEFI) | Instalação em hardware físico, seguindo o instalador do Lyra OS Server |
| Imagem de máquina virtual | `.qcow2` | KVM/QEMU, Proxmox, libvirt |
| Imagem de nuvem | a definir (por exemplo, `.raw` ou `.qcow2` com `cloud-init`) | Provedores de nuvem com instâncias de GPU |

## Primeiro boot

Em todas as imagens, o primeiro boot deve permitir executar
`neuryxctl gpu setup` para detectar a GPU e instalar o driver a partir do
repositório oficial da NVIDIA. Sem GPU compatível ou sem rede, o sistema usa a
variante CPU ou Vulkan do `llama-cpp`.

## Pendências

- Formatos e provedores da imagem de nuvem.
- Integração com `cloud-init` para executar o setup de GPU sem interação.
- Tamanho mínimo de disco, considerando o espaço para modelos.

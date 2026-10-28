# kiwi

Aqui ficará a descrição KIWI do Neuryx (`config.kiwi` e scripts associados).
Ela ainda **não existe**: depende de haver no Lyra um pattern reutilizável do
Server ([ADR 0001](https://github.com/neuryx-os/research/blob/main/adr/0001-edicao-do-lyra-server.md))
e da pesquisa
[04](https://github.com/neuryx-os/research/blob/main/topics/04-dependencia-da-base-lyra.md).

## O que irá aqui

- `config.kiwi` com os perfis das imagens previstas em
  [`../docs/imagens.md`](../docs/imagens.md).
- Repositórios: o projeto OBS do Lyra (`home:rodrigosbrito:lyra`) e o do
  Neuryx (`home:rodrigosbrito:lyra:Neuryx`, nome provisório).
- Pacotes: o **pattern do Lyra Server** e o `patterns-neuryx`. Nada além disso,
  salvo pacotes exigidos pelo próprio KIWI para cada tipo de imagem.
- `config.sh`, se necessário, apenas com passos específicos do Neuryx.

## O que não irá aqui

- **Nenhuma cópia** da descrição KIWI, dos scripts ou do overlay do
  [`lyraos-server`](https://github.com/lyra-os-linux/lyraos-server). Se algo do
  Lyra Server for necessário, ele deve virar pacote ou pattern no Lyra.
- Listas de pacotes da base do sistema: elas pertencem ao pattern do Lyra.
- Driver NVIDIA, módulos `nvidia-open` ou CUDA
  ([ADR 0004](https://github.com/neuryx-os/research/blob/main/adr/0004-driver-nvidia-no-primeiro-boot.md)).
- Modelos de IA: são baixados depois da instalação pelo `neuryxctl`.

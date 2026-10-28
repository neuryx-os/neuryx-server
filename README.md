# neuryx-server

Descrição KIWI das imagens do Neuryx (ISO, qcow2, nuvem) — edição de IA do Lyra OS Server.

**Status:** Planejado

## Propósito

Este repositório vai conter a descrição [KIWI](https://osinside.github.io/kiwi/)
que gera as imagens do Neuryx. Seguindo o
[ADR 0001](https://github.com/neuryx-os/research/blob/main/adr/0001-edicao-do-lyra-server.md),
o Neuryx é uma **edição do Lyra OS Server**: a imagem não redefine a base do
sistema, apenas a compõe a partir de pacotes publicados no OBS.

## Composição prevista

```
imagem do Neuryx = pattern do Lyra Server  (repositório OBS do Lyra)
                 + patterns-neuryx          (repositório OBS do Neuryx)
                 + overlay mínimo em root/  (só o que for específico da IA)
```

- **Pattern do Lyra Server:** o conjunto de pacotes da edição Server do Lyra,
  publicado no projeto OBS `home:rodrigosbrito:lyra`. A descrição de
  referência é [`lyra-os-linux/lyraos-server`](https://github.com/lyra-os-linux/lyraos-server),
  que **não é copiada** para cá.
- **`patterns-neuryx`:** pattern definido em
  [`neuryx-packages`](https://github.com/neuryx-os/neuryx-packages), que puxa
  `llama-cpp`, `neuryx-tuning`, `neuryxctl` e `neuryx-release`.
- **Driver NVIDIA e CUDA:** **não** entram na imagem; são instalados no
  primeiro boot pelo `neuryxctl`
  ([ADR 0004](https://github.com/neuryx-os/research/blob/main/adr/0004-driver-nvidia-no-primeiro-boot.md)).

## Pré-requisitos

Antes de existir um `config.kiwi` funcional, é preciso:

1. **Existir no Lyra um pattern reutilizável do Server**, publicado no OBS,
   que descreva a edição Server sem depender da descrição KIWI do
   `lyraos-server`. Hoje ele não existe.
2. Concluir a pesquisa
   [04 — Dependência da base Lyra](https://github.com/neuryx-os/research/blob/main/topics/04-dependencia-da-base-lyra.md).
3. Existir o projeto OBS do Neuryx com os pacotes de `neuryx-packages`.

## Estrutura

```
neuryx-server/
├── kiwi/          # descrição KIWI (ainda não criada; ver kiwi/README.md)
├── root/          # overlay de arquivos da imagem, se necessário
└── docs/
    └── imagens.md # imagens previstas
```

## Relação com outros repositórios

- [`neuryx-packages`](https://github.com/neuryx-os/neuryx-packages): fornece `patterns-neuryx` e os pacotes do Neuryx.
- [`research`](https://github.com/neuryx-os/research): ADRs 0001 e 0004, tópico 04.
- [`lyra-os-linux/lyraos-server`](https://github.com/lyra-os-linux/lyraos-server): edição Server do Lyra, referência da base.

## Licença

[GPL-3.0](LICENSE).

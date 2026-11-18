# Filme por conversa

[![Filme por conversa: seu filme de lançamento feito só conversando com a IA](guia/assets/banner.jpg)](https://inematds.github.io/filme-de-lancamento/guia/)

**🇧🇷 [Português](README.md) · 🇺🇸 [English](README.en.md) · 🇪🇸 [Español](README.es.md)**

## O que é

Você tem um negócio bom e nenhum vídeo que mostre isso. O **filme por conversa** é um kit grátis e aberto para fazer um filme de lançamento de cerca de 30 segundos, sem programa de edição, conversando em português com o Claude Code, uma IA que cria arquivos no seu computador. Serve para quem tem um pequeno negócio, procura trabalho ou quer uma renda extra e nunca editou vídeo. Você precisa de um computador, de um plano pago do Claude e de fotos do negócio feitas no celular; números, só se tiver. A IA confere o que falta instalar.

**O que precisa:** computador e plano pago do Claude. O kit é grátis; o plano mais barato com Claude Code, o Pro, custava [US$ 20 por mês](https://claude.com/pricing) em 18/11/2026, no pagamento mensal. Todo plano tem limite de uso, e não medimos quanto um filme consome. **Testado em Linux; Windows e Mac ainda sem teste.** Nesses sistemas, confira o [mínimo oficial do Claude Code](https://code.claude.com/docs/pt/setup), que não garante o filme, e teste primeiro com o filme de exemplo.

**Programas gratuitos:** a IA pode precisar instalar Node.js, que roda o programa que monta o filme; FFmpeg, que junta imagem e som; Chrome, que desenha cada quadro; e Python, que mede a música, se você usar uma. Você aprova antes.

## 📖 Guia de uso

Guia completo, sem termos técnicos: **https://inematds.github.io/filme-de-lancamento/guia/**

Primeira vez? Abra o [COMECE-AQUI.md](COMECE-AQUI.md).

## Peça para a IA começar

Abra o Claude Code nesta pasta e cole:

```text
Leia o COMECE-AQUI.md e a pasta prompts/ deste projeto. Depois me explique em linguagem
simples como vamos fazer um filme de lançamento de cerca de 30 segundos para o meu negócio.
Confira o que falta instalar usando a seção de instalação técnica do README e peça minha
aprovação antes de instalar. Faça uma pergunta por vez sobre o negócio, o problema que ele
resolve e as fotos, telas e números reais que eu tenho. Não mude nenhum arquivo antes do meu
sim. Não publique nem envie nada. Converse comigo em português.
```

Depois, basta pedir `siga o arquivo prompts/P1`, e assim por diante. Você não precisa abrir os arquivos.

## O que tem aqui

| Pasta ou arquivo | Para que serve |
|---|---|
| [COMECE-AQUI.md](COMECE-AQUI.md) | O caminho curto para quem nunca editou vídeo |
| [prompts/](prompts/) | P1 a P7, os pedidos para colar na IA, com os campos explicados |
| [amostra/METODO-DA-AMOSTRA.md](amostra/METODO-DA-AMOSTRA.md) | Como fazer um filme curto para um negócio e mostrar só ao dono |
| [checklists/](checklists/) | O que conferir antes de gerar, depois de gerar e antes de enviar |
| [filme/](filme/) | O filme de exemplo, editável |
| [ferramentas/mapa_batidas.py](ferramentas/mapa_batidas.py) | Mede a música e aponta onde cortar |
| [guia/](guia/) | A página do projeto em português, inglês e espanhol |
| [AVISOS.md](AVISOS.md) | Licenças de terceiros e limites de uso da trilha e da marca |

## O filme de exemplo

O exemplo fala do próprio INEMA.CLUB: [`guia/assets/filme-inema.mp4`](guia/assets/filme-inema.mp4). São 28,9 s em 1920x1080, a 30 quadros por segundo, com 7 cenas, música e efeitos.

---

## O processo, do início ao fim

🧠 = sessão com a pessoa · ⚙️ = script · 🤖 = IA

Rode os comandos ⚙️ dentro da pasta indicada. Os pedidos 🤖 são colados no Claude Code, aberto na raiz do projeto.

| # | Passo | Comando ou pedido | Quem |
|---|---|---|---|
| 1 | Contar o negócio, o público e o problema | conversa inicial do [COMECE-AQUI.md](COMECE-AQUI.md) | 🧠 |
| 2 | Escrever a história do problema | [P1](prompts/P1-historia-do-problema.md) | 🤖 + 🧠 aprova |
| 3 | Juntar fotos, telas e números reais | [P2](prompts/P2-telas-e-numeros-reais.md) | 🧠 entrega, 🤖 organiza |
| 4 | Montar as cenas como imagens paradas | [P3](prompts/P3-imagens-paradas.md) | 🤖 |
| 5 | Gerar os quadros para conferir | na pasta `filme/`: `npx hyperframes@0.8.77 snapshot . --at 2,9,17` | ⚙️ |
| 6 | Aprovar os quadros | abrir `filme/snapshots/` e dizer o que muda | 🧠 |
| 7 | Medir a música, se houver | na raiz: `python3 ferramentas/mapa_batidas.py filme/assets/audio/trilha.wav` (troque pelo arquivo da sua música) | ⚙️ |
| 8 | Animar e cortar na batida | [P4](prompts/P4-musica-e-batida.md) | 🤖 |
| 9 | Pôr sons só nas ações visíveis | [P5](prompts/P5-sons-nas-acoes.md) | 🤖 |
| 10 | Trocar o que ainda é do exemplo pela sua marca e mostrar as imagens paradas | [P7](prompts/P7-sua-marca.md) | 🤖 + 🧠 entrega o logo |
| 11 | Conferir e aprovar as imagens | [checklist antes de gerar](checklists/antes-de-renderizar.md) e, em `filme/`: `npx hyperframes@0.8.77 check` | ⚙️ + 🧠 |
| 12 | Gerar o vídeo depois da aprovação | em `filme/`: `npx hyperframes@0.8.77 render . -o renders/filme.mp4 --fps 30` | ⚙️ |
| 13 | Assistir e pedir correções por segundo | [checklist depois de gerar](checklists/depois-de-gerar.md) e [P6](prompts/P6-revisao-por-segundo.md); depois volte ao passo 11 | 🧠 + 🤖 |
| 14 | Conferir antes de mostrar a alguém | [checklist](checklists/antes-de-enviar.md) | 🧠 |
| 15 | Fazer para outro negócio, se quiser | [método da amostra](amostra/METODO-DA-AMOSTRA.md) | 🧠 |

P6 vem depois de P7 porque a revisão olha o filme já gerado com a sua marca.

## Instalação técnica

### O que precisa

- **Claude Code**, incluído nos [planos pagos do Claude](https://claude.com/pricing). No Windows e no Mac, use o [app Claude](https://code.claude.com/docs/pt/desktop-quickstart), aba **Code**, **Local** e **Open folder…**. No Linux, use a [instalação oficial](https://code.claude.com/docs/pt/setup). O render é local; o custo é o plano da IA.
- **Node.js** com `npx`. Testado com a versão 24.22.3.
- **FFmpeg e FFprobe**. Testado com a versão 6.1.1.
- **Chrome para render**. Rode `npx hyperframes@0.8.77 doctor` em `filme/` para ver o que falta. Ele também avisa que existe versão mais nova do HyperFrames; este kit fica fixo na 0.8.77 para o filme sair igual.
- **Python 3 com `numpy` e `scipy`**, só para medir a música.

Testado em Linux ARM64. Windows e Mac não foram testados com o kit. O mínimo oficial do Claude Code é Windows 10 versão 1809 ou macOS 13, com 4 GB de memória, processador x64 ou ARM64 e internet. Isso não garante o filme: o mínimo para gerá-lo não foi medido.

### Rodar o filme de exemplo

```bash
cd filme
npx hyperframes@0.8.77 check
npx hyperframes@0.8.77 render . -o renders/filme.mp4 --fps 30
```

O resultado fica em `filme/renders/filme.mp4`. O render levou cerca de 20 s nesta máquina, com Linux ARM64 e 118 GB de memória. Num computador comum leva mais.

O kit usa 1920x1080 por padrão. Para WhatsApp e Instagram, peça 1080x1920 no [P3](prompts/P3-imagens-paradas.md). Esse formato ainda não foi testado no kit.

### Como funciona por dentro

Cada cena é uma página HTML em `filme/compositions/`, animada com GSAP. O `filme/index.html` diz quando cada cena, música e efeito entra. O HyperFrames 0.8.77 abre tudo num navegador sem janela, grava quadro a quadro e entrega o MP4.

| Cena | Arquivo | Começa em | O que faz |
|---|---|---|---|
| 1 | `pilha.html` | 0 s | Vídeos salvos se empilham |
| 2 | `queda.html` | 4,288 s | A pilha cai: "O depois não chegou." |
| 3 | `barras.html` | 8,896 s | A virada: "Aprenda. Pratique. Evolua." |
| 4 | `busca.html` | 11,968 s | Busca real no catálogo |
| 5 | `parede.html` | 17,088 s | Parede de cursos e o número 385 |
| 6 | `promessa.html` | 23,232 s | "Grátis. Direto na internet." |
| 7 | `marca.html` | 25,28 s | Logo e pergunta final |

### Os números do exemplo

- Trilha: 117,2 BPM, uma batida a cada 0,512 s, medida por `ferramentas/mapa_batidas.py`. As viradas caem em 8,896 s e 17,088 s.
- Busca em [inema.club/cursos](https://www.inema.club/cursos/), em 18/11/2026: "criar vídeo com IA" deu 0 cursos; "vídeo" deu 53. O catálogo tinha 385 fichas de curso.
- A revisão por quadros parados pegou dois erros: o primeiro quadro com metade da tela vazia e os resultados em ordem diferente da do site.

## Licença

Código e textos deste kit: [MIT](LICENSE). A trilha do exemplo é só para uso não comercial, e há outras exceções em [AVISOS.md](AVISOS.md). Leia antes de usar o filme num negócio.

---

Feito pelo [INEMA.CLUB](https://inema.club).

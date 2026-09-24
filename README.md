# Quiz de Lógica e História da Informática

Jogo de perguntas com pontos, combos, poderes, conquistas e ranking de escolas e alunos. Feito para alunos de 12 a 18 anos.

Tudo está em **um único arquivo**: `quiz-computacao.html`.

---

## 1. Como abrir

1. **Baixe** o arquivo `quiz-computacao.html` e guarde em uma pasta fácil de achar (por exemplo, a Área de Trabalho).
2. **Dê dois cliques** no arquivo. Ele abre no navegador padrão.
   - Se abrir em outro programa, clique com o botão direito no arquivo, escolha **Abrir com** e selecione **Google Chrome**, **Microsoft Edge** ou **Firefox**.
3. A primeira tela é o **ranking**. Clique em **Jogar agora** para começar.

**Importante:**

- Abra o arquivo **direto no navegador**. Se você abrir dentro de um painel de pré-visualização (como o do próprio Claude), o ranking pode não ser salvo.
- É preciso ter **internet** ao abrir, porque o quiz carrega bibliotecas e fontes da web. Depois de aberto, ele segue funcionando mesmo que a conexão caia.
- Use um navegador atualizado. Internet Explorer não funciona.
- No celular, o quiz funciona, mas para abrir o arquivo baixado costuma ser mais simples usar um computador ou notebook.

---

## 2. Como funciona uma partida

1. O aluno informa a **escola** e o **apelido**.
2. O quiz **sorteia 4 perguntas**: 2 de Lógica e 2 de História da Informática.
3. O aluno responde dentro do tempo (30 segundos por pergunta, por padrão).
4. Acertos valem 100 pontos, mais bônus por velocidade e por acertos seguidos (combo).
5. Cada aluno tem 2 poderes por partida: **50/50** (elimina duas alternativas erradas) e **+10s** (mais tempo).
6. No final aparecem estrelas, rank, conquistas, a posição do aluno e da escola, e se ele ganhou o prêmio (acertar as 4 perguntas).

---

## 3. Ranking

- Cada aluno conta com a **melhor** pontuação dele.
- A escola vale a **soma** da melhor pontuação de cada aluno. Para usar a **média**, veja o `criterioEscola` na seção 5.
- O ranking tem as abas **Escolas** e **Alunos**, com o top 10. O link **Ver todos os registros** mostra a lista completa.

### Onde o ranking fica guardado

O ranking é salvo **no navegador do computador** usado pelos alunos. Por isso:

- Atualizar a página **não** apaga o ranking.
- Trocar de navegador ou de computador mostra **outro** ranking, começando do zero.
- Limpar os dados de navegação ou jogar em aba anônima **apaga ou não guarda** o ranking.

### Juntar rankings de vários computadores

1. No computador A, abra o ranking, clique em **Área do professor**, depois em **Gerar código** e informe a senha. Copie o texto que aparece na caixa.
2. No computador B, cole o texto na mesma caixa e clique em **Importar código**.
3. Os registros se somam sem duplicar.

Use **Gerar código** também como **cópia de segurança** antes de limpar o navegador. **Baixar CSV** exporta o ranking de alunos para planilha.

### Excluir registros

Ao lado de cada aluno ou escola há um botão 🗑. Ao clicar, o quiz pede a **senha de administrador** e uma confirmação. Excluir uma escola apaga também os registros de todos os alunos dela.

**Senha de administrador padrão: `134562`**

---

## 4. Editar o quiz

Abra o arquivo `quiz-computacao.html` em um editor de texto (Bloco de Notas, VS Code ou similar):
botão direito no arquivo, **Abrir com**, **Bloco de Notas**.

Procure por `CONFIGURAÇÕES DO PROFESSOR` (Ctrl + F). Altere os valores, salve o arquivo e atualize a página no navegador (F5).

> Não apague as vírgulas e as aspas. Mude só os valores.

---

## 5. Configurações principais

| Opção | Padrão | O que faz |
|---|---|---|
| `titulo` | Quiz de Lógica e História da Informática | Título mostrado nas telas |
| `tempoPorPergunta` | `30` | Segundos por pergunta. `0` desativa o timer |
| `sorteio` | Lógica: 2, História da Informática: 2 | Quantas perguntas sortear de cada categoria |
| `evitarRepetir` | `true` | Não repete perguntas na mesma sessão até esgotar a categoria |
| `animacaoSorteio` | `true` | Mostra a tela de sorteio antes das perguntas |
| `embaralharPerguntas` | `true` | Mistura a ordem das perguntas sorteadas |
| `embaralharAlternativas` | `true` | Muda a posição das alternativas |
| `mostrarExplicacao` | `true` | Mostra a explicação depois de cada resposta |
| `pontosPorAcerto` | `100` | Pontos base por acerto |
| `bonusPorSegundo` | `5` | Pontos extras por segundo que sobrar |
| `bonusCombo` | `25` | Pontos extras por acerto seguido |
| `poderesAtivos` | `true` | Liga ou desliga 50/50 e +tempo |
| `segundosExtra` | `10` | Segundos ganhos com o poder +tempo |
| `somAtivo` | `true` | Efeitos sonoros (o aluno pode silenciar no botão 🔊) |
| `rankingAtivo` | `true` | Liga ou desliga o ranking |
| `criterioEscola` | `"soma"` | `"soma"` ou `"media"` para a pontuação da escola |
| `senhaAdmin` | `134562` | Senha para exportar, importar e excluir registros |
| `escolas` | `[]` | Lista de escolas sugeridas no cadastro. Ex.: `["Escola A", "Colégio B"]` |
| `premioAtivo` | `true` | Liga ou desliga a mensagem de prêmio |
| `acertosParaGanhar` | `4` | Acertos necessários para ganhar o prêmio |
| `textoPremio` | Você ganhou o prêmio! | Mensagem exibida ao ganhar |

### Adicionar ou trocar perguntas

As perguntas ficam logo abaixo, na lista `PERGUNTAS`. Hoje são **80: 40 de Lógica e 40 de História da Informática**. Em cada partida, o quiz sorteia só 4 delas (2 de cada tema). Copie o formato de uma pergunta existente:

```js
{
  categoria: "Lógica",              // ou "História da Informática"
  pergunta: "Texto da pergunta?",
  alternativas: ["A", "B", "C", "D"],
  correta: 2,                       // posição da correta: 0, 1, 2 ou 3
  explicacao: "Por que essa é a resposta certa."
},
```

`correta` conta a partir de **0**: a primeira alternativa é `0`, a segunda é `1`, e assim por diante.

As perguntas do bloco `BANCO AMPLIADO` usam um formato mais curto, com a mesma ordem de informações. Use `L(...)` para Lógica e `H(...)` para História da Informática:

```js
L("Texto da pergunta?", ["A", "B", "C", "D"], 2, "Explicação da resposta."),
```

---

## 6. Problemas comuns

- **A página abre em branco:** confira a internet. Em redes escolares, o site `cdnjs.cloudflare.com` pode estar bloqueado. Peça ao responsável pela rede que libere.
- **O ranking sumiu:** provavelmente foi aberto em outro navegador, em aba anônima ou os dados de navegação foram limpos. Se você gerou um código de backup, use **Importar código** para restaurar.
- **Aparece um aviso amarelo no ranking:** o ambiente está bloqueando o salvamento permanente. Abra o arquivo direto no Chrome, Edge ou Firefox.
- **Sem som:** clique primeiro em qualquer botão da página (os navegadores só liberam áudio depois de um clique) e confira o botão 🔊 no canto superior direito.
- **Esqueci a senha:** ela está em `senhaAdmin`, no bloco de configurações do arquivo.

---

## 7. Segurança

A senha de administrador fica escrita dentro do arquivo. Ela evita exclusões acidentais, mas quem abrir o código-fonte consegue lê-la. Se os computadores forem dos alunos, considere guardar o arquivo do professor separado.

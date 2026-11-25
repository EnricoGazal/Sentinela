# Como contribuir

## Fluxo

1. O `main` é protegido: ninguém faz push direto. Toda mudança entra por pull request.
2. Um ramo por mudança, com prefixo que diz o tipo:
   `feat/`, `fix/`, `refactor/`, `docs/`, `test/`, `chore/`, `ci/`.
   Exemplos: `feat/normalizador-firewall`, `refactor/chain-regras`, `docs/adr-0006`.
3. PR pequeno, uma mudança só, usando o modelo em `.github/pull_request_template.md`.
   Quando o PR aplica um padrão, princípio ou decisão, a descrição cita
   (ex.: "aplica Decorator na reputação, ver ADR-0005").
4. Outro integrante revisa e aprova. Quem abriu não aprova o próprio PR.
5. O CI (ruff check, ruff format --check, pytest e verificação da documentação) precisa passar.
6. Estratégia de merge do projeto: **merge commit** (sem squash), para que o histórico
   do `main` preserve os commits e os autores de cada PR.

## Commits

Seguimos [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/):

```
feat(triagem): adiciona regra de linha de comando suspeita
fix(ingestao): rejeita veredito desconhecido do gateway de e-mail
refactor(triagem): troca if/elif das regras por Chain of Responsibility
docs(adr): registra ADR-0006 substituindo o ADR-0002
```

## Antes de abrir o PR

```bash
ruff check . && ruff format --check . && pytest && python scripts/docs.py verificar
```

## Documentação

- Cada afirmação da documentação aponta para o trecho de código que a prova.
- Durante o desenvolvimento, aponte para o símbolo com link relativo:
  `[TriarAlerta](../src/sentinela/triagem/caso_de_uso.py#TriarAlerta)`.
  O CI confere se o símbolo existe.
- Na entrega, `python scripts/docs.py permalinks --repo dono/repositorio --sha <hash>`
  troca esses links pelos links permanentes do GitHub com o hash do commit.
- ADR aceito não se edita: escreve-se um novo que o substitui.

# NESK

Assistente pessoal para Windows, desenvolvido em Python. O NESK combina comandos locais, interface desktop, interação por voz e interpretação contextual com proteções para confirmar ações e limitar o que pode ser executado.

## Versão publicada

Esta cópia corresponde ao código-fonte **0.2.0.5.2 — First Listen**, com melhorias de interpretação semântica em português e descoberta controlada de programas.

O pacote completo com a estrutura original, código, testes e documentação está disponível em [`nesk-source-0.2.0.5.2.zip`](nesk-source-0.2.0.5.2.zip). Baixe e extraia o arquivo para acessar o projeto localmente.

## Recursos desta versão

- Interface desktop e fluxo de conversa por texto.
- Captura e transcrição de voz opcionais.
- Comandos locais para navegador, programas e estado do computador.
- Contexto de sessão curto para referências recentes.
- Política de permissões e validação antes da execução de ações.
- Histórico opcional em SQLite.
- Provedor semântico remoto opcional; o funcionamento básico usa o interpretador local.

O NESK ainda está em desenvolvimento. Nesta versão, ele responde por texto; síntese de voz, palavra de ativação e escuta contínua ainda não estão disponíveis. Veja [limitações conhecidas](docs/KNOWN_LIMITATIONS.md).

## Requisitos

- Windows 10 ou superior para os scripts de instalação fornecidos.
- Python 3.10 a 3.14 (Python 3.11 de 64 bits é a opção recomendada nos scripts).

## Instalação no Windows

1. Instale uma versão compatível do Python e habilite o launcher `py`.
2. Baixe ou clone este repositório.
3. Execute `scripts/setup_windows.bat`.
4. Depois da instalação, execute `scripts/run_nesk.bat`.

A primeira utilização da transcrição local pode baixar um modelo e exigir internet. A instalação completa de áudio/voz pode depender dos componentes disponíveis no Windows.

## Desenvolvimento

```bash
python -m venv .venv
```

Ative o ambiente virtual e instale o projeto com as dependências desejadas:

```bash
python -m pip install -e ".[dev]"
```

Para incluir os recursos de voz:

```bash
python -m pip install -e ".[voice,dev]"
```

O adaptador OpenAI é opcional e só deve ser ativado com uma chave configurada localmente. Nunca publique chaves ou arquivos `.env`.

## Testes

```bash
python -m pytest
python scripts/smoke_test.py
```

## Estrutura

- `src/nesk/`: aplicação, lógica central, provedores, armazenamento, voz e ferramentas.
- `tests/`: testes automatizados.
- `docs/`: arquitetura, decisões, planos de teste e limitações.
- `scripts/`: instalação, diagnóstico, execução e verificações de release.

## Segurança e privacidade

As ações passam pelo núcleo do NESK, ferramentas registradas e política de permissões. O interpretador semântico não executa ferramentas diretamente. O histórico SQLite é opcional e local. Consulte [arquitetura](docs/ARCHITECTURE.md) e [política de privacidade](PRIVACY.md) para detalhes.

## Licença

Nenhuma licença de reutilização foi definida neste repositório. Consulte o autor antes de redistribuir ou incorporar o código em outros projetos.

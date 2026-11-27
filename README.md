# Sistema de Gestão Acadêmica (CRUD em Python)

Sistema de linha de comando para cadastrar **estudantes, professores, disciplinas, turmas e matrículas**, com os dados salvos em arquivos JSON.

O destaque do projeto é a arquitetura: em vez de escrever um CRUD para cada entidade, criei uma classe `Repositorio` genérica. Para adicionar uma entidade nova, basta descrever os campos dela numa configuração, sem repetir código.

## 🧱 Stack

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white&style=flat-square)
![JSON](https://img.shields.io/badge/JSON-000000?logo=json&logoColor=white&style=flat-square)

Somente biblioteca padrão do Python (`json`, `os`, `typing`). Nenhuma instalação extra.

## ✨ Funcionalidades

- Listar, incluir, editar e excluir registros de 5 entidades
- Código único garantido na inclusão e na edição
- Validação de campos obrigatórios e de tipos (texto ou número)
- Edição parcial: aperte Enter para manter o valor atual
- Persistência automática em `data/*.json`
- Script para popular a base com dados de exemplo

## 🏗️ Arquitetura

```python
Repositorio(
    arquivo="estudantes.json",
    campo_id="codigo",
    label="ESTUDANTE",
    campos=[("nome", "Nome do(a) estudante", str),
            ("cpf",  "CPF do(a) estudante",  str)],
)
```

Cada entidade é só uma configuração como essa. Todas as operações (listar, incluir, editar, excluir) vêm da mesma classe.

## ▶️ Como rodar

Os comandos abaixo são executados de dentro da pasta `crud_project/`:

```bash
cd crud_project
python populate.py                      # (opcional) cria dados de exemplo
python src/crud.py                      # abre o menu interativo
python -m unittest tests/test_unit.py   # testes unitários
```

> Requer Python 3.6 ou superior.

## 📂 Estrutura

```
crud_project/
├── src/crud.py          # Repositório genérico + menu
├── data/                # Arquivos JSON (dados de exemplo fictícios)
├── tests/
│   ├── test_unit.py     # Testes unitários
│   └── test_crud.py     # Roteiro de verificação manual
├── populate.py          # Popula a base
└── docs/documentacao.md # Documentação detalhada
```

## 🧠 O que pratiquei

- Orientação a objetos e o princípio DRY (não repetir código)
- Tipagem com `typing` e tratamento de erros de leitura de arquivo
- Persistência simples com JSON

## 🔭 Próximos passos

- [ ] Incluir o código da turma na matrícula (hoje ela guarda só o estudante)
- [ ] Validar se professor, disciplina e estudante existem antes de criar turmas e matrículas
- [ ] Transformar `test_crud.py` em testes com `assert`, usando uma pasta de dados temporária
- [ ] Resolver o caminho da pasta `data/` a partir do arquivo, e não da pasta onde o comando é executado

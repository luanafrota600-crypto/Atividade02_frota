name: Validação do Projeto

on:
  push:
    branches:
      - '**'

jobs:
  validar:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout do código
        uses: actions/checkout@v5

      - name: Exibir repositório e usuário
        run: |
          echo "Repositório: ${{ github.repository }}"
          echo "Usuário que iniciou a execução: ${{ github.actor }}"

      - name: Verificar se o README.md existe
        run: |
          if [ -f README.md ]; then
            echo "README.md encontrado."
          else
            echo "::error::README.md não encontrado. Falhando o workflow."
            exit 1
          fi

      - name: Validação concluída
        run: echo "Validação concluída com sucesso!"
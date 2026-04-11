## 👨🏽‍💻Cayo Vinnicius

**`Desenvolvedor/Programador front-end`**

Me chamo Cayo Vinnicius, sou desenvolvedor e programador faço HTML e CSS e também faço JacaScript, tenho alguns projetos bem legais do meu curso de html e css , mas futuramente pretendo fazer alguns projetos pessoais

##
  🤖 Linguagens:
<div style="display: inline_block">
  <img align="center" alt="Rafa-HTML" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg">
  <img align="center" alt="Rafa-CSS" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original.svg">
  <img align="center" alt="Rafa-Js" height="30" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg">
</div>

  ##

<div> 
  <a href = "mailto:almeidafeitosa112@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
</div>


name: generate animation

on:
  # Executa automaticamente a cada 24 horas
  schedule:
    - cron: "0 */24 * * *" 
  
  # Permite rodar manualmente a qualquer momento
  workflow_dispatch:
  
  # Executa a cada push no branch main
  push:
    branches:
    - main

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    
    steps:
      # Gera a animação da cobrinha
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      # Faz o push do arquivo gerado para o branch 'output'
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

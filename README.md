
# Hello, world! 👋

### 📌 Resumidamente

- **👨‍💻 Estudante de Ciência da Computação na UFC e de Engenharia da Computação na UniAteneu**

---

### 🌱 Atualmente Aprendendo
- **Cibersegurança**: Participando de encontros e eventos sobre segurança da informação.
- **Desenvolvimento de Software**: Projetos práticos em C++ e JavaScript.
- **Soft Skills**: Trabalhando para melhorar minha comunicação e superar a timidez em ambientes profissionais.
- **Robótica**: Explorando a criação de robôs utilizando `ROS` (Robot Operating System) e programação de microcontroladores como `Arduino` e `Raspberry Pi`.
- **Redes**: Estudando protocolos de rede, administração de redes e como configurar redes seguras para ambientes corporativos e pessoais.

---
### 🛠️ Atualmente trabalhando com
<div>
  <img src="https://github.com/devicons/devicon/blob/master/icons/html5/html5-original.svg" title="HTML5" alt="HTML" width="40" height="40"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/javascript/javascript-original.svg" title="JavaScript" alt="JavaScript" width="40" height="40"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/c/c-original.svg" title="C++" alt="JavaScript" width="40" height="40"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/css3/css3-original.svg" title="CSS" alt="CSS" widht="40" height="40"/>&nbsp;
</div>

---

<div align = "left">
<img height = "200em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=NicolasHarnisch&show_icons=true&theme=bear&count_private=true"/>
<img height = "200em" src="https://github-readme-stats.vercel.app/api?username=NicolasHarnisch&show_icons=true&show_icons=true&theme=bear&count_private=true" />
</div>

name: generate animation

on:
  schedule:
    - cron: "0 0 * * *"  # Executa 1 vez por dia
  workflow_dispatch:
  push:
    branches:
      - main  # Certifique-se de que sua branch principal é 'main' ou 'master'

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

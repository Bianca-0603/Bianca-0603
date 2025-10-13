## Oi você ! 

Bem vinda (o) ao meu perfil ! 
<div>  
   
<img src="https://github-readme-stats.vercel.app/api?username=Bianca-0603&show_icons=true&theme=great-gatsby&include_all_commits=true&count_private=true"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Bianca-0603&layout=compact&langs_count=16&theme=great-gatsby"/>
</div>


<div align="center"> 
  <div style="display: inline_block"><br>
    <img align="left" height="250" alt="coding-time" src="code.gif">
     <h1 align="center">       T e c h n o l o g i a s </h1>
    <img align="center" height="30" width="40" alt="js-icon"  src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg">
    <img align="center" height="30" width="40" alt="react-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original.svg">
    <img align="center" height="30" width="40" alt="html-icon" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original.svg">
    <img align="center" height="30" width="40" alt="css-icon" 
src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original.svg">

   </div>
    
  <div>
    <h1 align="center">Social Media</h1>
    <a href="mailto:biancasouto.eu@gmail.com">
       <img src = "https://github.com/user-attachments/assets/071bb4e4-b797-4eab-827e-4d39b9683885" 
       <div align = "left" width ="30px"> 
       </a>
</div>

<div>
   <a href = "https://www.linkedin.com/in/biancapinto0676">
      <img src = "https://github.com/user-attachments/assets/d143e126-a2a7-48c8-97b0-478584da2cf7" 
justify-content: space-between; width ="30px">
    </a>
    </div>

  name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
     

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

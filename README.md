# Python Faded Parsons Problems with Visual Output

<sup>Based on https://github.com/pamelafox/faded-parsons-static/</sup> and **pyp5js** and a lot of help from many people!</sup>

## Work in progress! Working prototype!

Check out at https://abav.lugaralgum.com/faded-parsons-visual/

The website should allow you to run Faded Parsons Problems in the browser, with visual results, using **pyodide** and the _p5js_ canvas to show sketch results, written in a dialect close to **py5** in *imported mode* style.

## A quick way to make and publish your own puzzles

You can fork this repository, edit the YAML files in the `parsons_prob` folder as explained bellow, and set the GitHub Pages settings to publish your own page, or upload on some other webhosting server. This tool is based on "static pages", so uploading the files (mostly html, js, yaml, images and etc.) is all there is to it.

## If you want to contribute with this tool/project 

### Setting up a local development environmet

Be sure to have `nodejs` installed. To install `nodejs`, go to their download page and download the installer for your operating system: https://nodejs.org/en/download/

We will assume you have at least some familiarity with the command line. After installing, open a terminal, go to the project's folder using `cd` (the one you're in right now) and run:

`npm install`

This will install all the dependencies for the website.

If you don't have `npm` installed, double check the installation instructions for `nodejs` for your operating system.

### Running the website locally 

From the download directory:

`npm run dev`

This will start a local server at http://localhost:8000/ where you can see the website. Also, whenever you change something in the code, reload the page to see the changes.

### Building the website

To make the site ready for deployment, run:

`npm run build`

This will recreate the `dist` folder with the website ready to be deployed.

### Deploying the website

This website can be deployed anywhere since it's entirely static, and is currently deployed on Github Pages. You can enable Pages on your own fork of the repo to host on Github.

## Adding a new problem

Add files to the `parson_probs` folder:

- `problem_file.yaml`: This is a YAML file that includes the problem description (HTML) and code lines with blanks.

- You should add an image to the description, like `problem_file.png`, in the same folder.

- Example `000_variables.yaml` that uses `000_variables.png` in the same folder:

```yaml

problem_name: Variables

problem_subtitle: assignement

problem_category: Getting Started

problem_description: |
	<code>Variáveis </code>
		Organize as linhas para formar o desenho abaixo
		</br>
		<img src="parsons_probs/000_variables.png">
		</br>

code_lines: |
	 def setup(): #0given
	 size(400, 400) #1given
	 background(200) # fundo cinza
	 nome = '!BLANK'
	 text(nome, 20, 180)  # desenha o texto de `nome`
	 # Se tentar usar a variável `a` antes de criar...
	 # ... vai ter um erro do tipo NameError (não conheço `a`)
	 a = 10  # cria a variável `a` que aponta para o valor 10
	 square(a, 10, 140)  # desenha um quadrado de lado 140 em x:10, y:10
	 a = a + 145  # calcula o valor de `a + 145` e muda a variável `a`
	 square(a, 10, !BLANK)  # desenha um quadrado de lado 140

```

Then you can access the new problem at **`.../problem.html?name=problem_file`**

### Updating the index/home page

There is a [Python script](https://github.com/villares/faded-parsons-visual/blob/hack/update_index.py) that will look for YAML problems, check the category and update the `index.html` with links to all the problems found in `parsons_probs`.

### Automating YAML generation from puzzle source code 

Also inside the `parson_probs` folder, you will find some `.py` files that contain py5 imported mode style code for a problem, with added annotations like `#0given` as explained above, and some extra special comments, like`#REMOVE` on some lines, and commened out lines with code containing `!BLANK`. Those scripts will generate the YAML problem file and the image file for the problem description.

## About the main prototipe page

Again, the working prototype at https://abav.lugaralgum.com/faded-parsons-visual/ is served with GitHub Pages now from the main branch's `index.html` (home page) and `problem.html` (puzzle page). If you have any question you can open an issue or contact Alexandre B A Villares.

# Build web scrapers with AI for non-coding journalists

**Dataharvest 2026**

Keng (Kuek Ser Kuang Keng)

**[View the workshop materials](https://github.com/kuangkeng/dataharvest2026-ai-scraper)**

**[Read the tutorial published in Oct 2025](https://pulitzercenter.org/resource/how-non-coding-journalists-can-build-web-scrapers-ai-examples-and-prompts-included)**

#### Cheatsheet:
[Task #1 Colab (created with Claude Pro)](https://colab.research.google.com/drive/1qwlBd3bc128D2dVyLFADi1LNu5QnuH51?usp=sharing)<br>
[Task #1 Colab (created using free Gemini)](https://colab.research.google.com/drive/1pdv4DTsUe-K4pHXRvd7eWxXbjnxxTmsK?usp=sharing)<br>
[Task #2 Colab (created using free built-in Gemini in Colab)](https://colab.research.google.com/drive/14edVK9ET0R1Mq7oMo2SazdCUyIB-2q2u?usp=sharing)

## Task #1:

The Metals Company (TMC) is a Canadian-based deep-sea mining company pushing for permits to start deep sea mining operations in the Pacific Ocean. You want to report on how TMC has changed its official narrative to push for such approvals. To do that you need to collect all 148 press releases (or more) from its website. You know nothing about coding but you want to use a LLM to help you build a Python web scraper from scratch and run it either from Google Collab (register a free account) or your own computer (Terminal for macOS or PowerShell for Windows).

First, build a scraper to extract the title, date, and url of each press release, and store the data as a csv file.

If you manage to get the above data, build a second scraper to visit the url of each press release (that you’ve stored in the first csv) and extract the title, date and full content of each press release, then store the data as a second csv file.

### Steps:

#### 1. Try to figure out if the web page is static or dynamic to help you plan your strategy.
```
Here is the URL of a web page that I would like to scrape data from.
Can you tell me if the information and data on the page is directly available in the code [static] or if it loads later with scripts [dynamic]?

https://investors.metals.co/news-events/press-releases
```
Note: If the LLM faces a problem accessing the web page, you need to spoon-feed it by copy-pasting the whole HTML source code of the web page. You can see the source code by right clicking the web page and selecting “View page source” on Chrome.
```
Here's the HTML source code: [paste the HTML source code]
```

#### 2. Now ask LLM to build the first scraper to extract the title, date, and url of each press release.
```
I need to build a scraper for the web page below. It is a static web page.
Write me a Python script to scrape the web page in Google Collab. 

https://investors.metals.co/news-events/press-releases

It has a list of press releases with title, date, and url to the press release page.
I need all 3 of them stored in separate columns in a CSV file.
The web page has pagination. I need the full list of press releases from all pages. 
```
Note: If you plan to run the script on your laptop command-line interface (CLI), you should change the mention of Google Collab to your own CLI (e.g. Terminal for macOS or PowerShell for Windows).

If you’ve never run a Python script on your computer, you’ll need a quick setup. LLMs can generate step-by-step instructions with the prompt below. Setup usually includes installing Python (and its package manager Pip, or Homebrew on macOS) plus common scraping libraries like Requests, Beautifulsoup4, and optionally Selenium.
```
I need to run a Python scraping script on macOS/Windows.
Show me step-by-step setup instructions.
```

#### 3. Now ask the LLM to build the second scraper to visit the url of each press release (that you’ve stored in the first csv) and extract the title, date and full content of each press release.
```
Now I need a second script to visit each press release webpage, then scrap the content of the press release.
The csv should have the url, title, date and full content of each press release.
I need to run the script in Google Collab following the first script.
I will copy paste it into a new code cell in Google Collab. 
```
Note: Again, If the LLM faces a problem reading/understanding the web page, you need to spoon-feed it by copy-pasting the whole HTML source code of one of the press release pages.
```
Here's the HTML of one of the press release pages [paste HTML source code of any press release page]
```


## Task #2:

```
I would like to write a Python script that I will run from Google Collab to scrape data from an online database and store it in a CSV file. It is a dynamic web page. Below are the steps required to view the data. I’ve specified the HTML elements that the scraper should interact with. Print messages at different steps to show progress and help debug any errors. Let me know if you need any more information from me.

1. Go to the search page:

https://www.imprensaoficial.com.br/ENegocios/BuscaENegocios_14_1.aspx

2. Fill in the search criteria in nine dropdown menus:

Select "Materiais e Equipamentos" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Negocio$cboArea" id="content_content_content_Negocio_cboArea" class="form-control" onchange="javascript:CarregaSubareasNegocios();">

Select "Generos Alimenticios" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Negocio$cboSubArea" id="content_content_content_Negocio_cboSubArea" class="form-control">

Select "ENCERRADA" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Status$cboStatus" id="content_content_content_Status_cboStatus" class="form-control" onchange="fncAjustaCampos();">

Select "1" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Status$cboAberturaSecaoInicioDia" id="content_content_content_Status_cboAberturaSecaoInicioDia" class="form-control">

Select "1" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Status$cboAberturaSecaoInicioMes" id="content_content_content_Status_cboAberturaSecaoInicioMes" class="form-control">

Select "2024" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Status$cboAberturaSecaoInicioAno" id="content_content_content_Status_cboAberturaSecaoInicioAno" class="form-control">

Select "31" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Status$cboAberturaSecaoFimDia" id="content_content_content_Status_cboAberturaSecaoFimDia" class="form-control">

Select "12" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Status$cboAberturaSecaoFimMes" id="content_content_content_Status_cboAberturaSecaoFimMes" class="form-control">

Select "2024" for:

<select name="ctl00$ctl00$ctl00$content$content$content$Status$cboAberturaSecaoFimAno" id="content_content_content_Status_cboAberturaSecaoFimAno" class="form-control">

3. Click this button:

<input type="submit" name="ctl00$ctl00$ctl00$content$content$content$btnBuscar" value="Buscar" onclick="return verify();" id="content_content_content_btnBuscar" class="btn btn-primary">

4. Wait for the result page to load; wait for the complete loading of the result table:

<table class="table table-bordered table-sm table-striped table-hover" cellspacing="0" rules="all" border="1" id="content_content_content_ResultadoBusca_dtgResultadoBusca" style="border-collapse:collapse;"></table>

5. Scrape the text content in the whole table. Create an extra column to store the <href> tag of the last column.

6. Go to the next page of the result table and repeat the scraping of the table for the first 5 pages. The number of pages appears in:

<span id="content_content_content_ResultadoBusca_PaginadorCima_QuantidadedePaginas">5659</span>

Click this button to go to the next page: 

<a id="content_content_content_ResultadoBusca_PaginadorCima_btnProxima" class="btn btn-link xx-small" href="javascript:__doPostBack('ctl00$ctl00$ctl00$content$content$content$ResultadoBusca$PaginadorCima$btnProxima','')">próxima &gt;&gt;</a>

7. Give me a preview of the csv file at the end.
```





If you have no idea how to start, you can refer to this tutorial.


# Simple-MVC 
(<a href="https://beier.f4.htw-berlin.de/wiki/php/simple-mvc/">Source or German Version</a>)

Simple-MVC is a small PHP framework that is based on the <a href="http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller">Model-View-Controller</a> pattern and the code of websites is fundamentally structured in three parts.

It brings with different helper, for example, take care of the database access or session management. In addition, it has an autoloader, which automatically loads all those classes that are needed during program execution.

<h3>Installation</h3>

I use a modified version. For the original code, see <a href="http://simplemvcframework.com/php-framework">simplemvcframework.com</a> or on <a href="https://github.com/simple-mvc-framework/v1">Github</a>. Note: The original document may differ partially.
<ul>
<li>Download or clone the Framework.</li>
<li>Unpack the archive.</li>
<li>Move the new folder Simple-MVC in the document root of your webserver (htdocs, public_html or similar).</li>
<li>Open config.php file and change the constant DIR on the URL to the directory (for example, http://localhost/Simple-MVC/) then change the data in the database. Beware that the line define ('DB_TYPE', 'mysql'); not commented out or deleted. <b>You can configure the database later because we don’t use it for the first step yet.</b> </li>
<li>It is included a file called .htaccess. Make sure that this file exists safely. (Linux or Mac OS, it is invisible - you can in the Shell by ls -a check if it is available.). If there is, change the path to where your Simple-MVC is. </li>
<div class="highlight language-shell" data-lang="shell"><pre><code><span class="c">#For example</span>
RewriteRule ^<span class="o">(</span>.<span class="k">*</span><span class="o">)</span><span class="nv">$ </span>/Simple-MVC/index.php?url<span class="o">=</span><span class="nv">$1</span> <span class="o">[</span>QSA,L]
</code></pre></div> 
<li>On this example i use apache server. After starting the server, open the browser and go to <code>http://localhost/Simple-MVC/</code>. If there isn’t any problem, you can see this view on your browser. </li></ul>
![alt tag](https://raw.githubusercontent.com/cescgie/Simple-MVC/master/static/img/Screenshoot2015-05-18um15.33.42.png)

<br>
Before we start using the site (in case you want to understand the code more deeply), here is an explanation of the contents of the framework.

<h3>Directories and files</h3>
<div class="highlight language-" data-lang=""><pre><code>* Directory / File *         * Description*
├── config.php                  - Config file
├── controllers                 - All Controller
│   └── welcome.php             - Example for Controller
├── core                        - Core file of Simple-MVC
│   ├── bootstrap.php           - Heart of all file
│   ├── controller.php          - Base Controller
│   ├── error.php               - Error Controller
│   ├── logger.php              - Logger Information
│   ├── model.php               - Base Model
│   └── view.php                - Base View
├── errorlog.html               - Error log
├── helpers                     - All Helpers
│   ├── database.php            - Access to Database
│   ├── message.php             - Message Store
│   ├── password.php            - Passwort Generator
│   ├── session.php             - Session Management
│   └── url.php                 - Address Helper
├── index.php                   - Start Point
├── models                      - All Models
│   └── sample_model.php        - Example for Model
├── static                      - Static File
│   ├── css                     - Stylesheets
│   │   ├── bootstrap.min.css   - Bootstrap
│   │   └── style.css           - Own Created Styles
│   └── img                     - Directory for Images
└── views                       - All Views
    ├── error                   - Error Management
    │   └── 404.php             - File not found
    │   └── default.php         - Standard Error
    ├── footer.php              - Foot of Page
    ├── header.php              - Header of Page
    ├── message.php             - Messages
    └── welcome.php             - Welcome Page
</code></pre>
</div>

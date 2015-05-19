# Simple-MVC 
(<a href="https://beier.f4.htw-berlin.de/wiki/php/simple-mvc/">Source or German Version</a>)

Simple-MVC is a small PHP framework that is based on the <a href="http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller">Model-View-Controller</a> pattern and the code of websites is fundamentally structured in three parts.

It brings with different helper, for example, take care of the database access or session management. In addition, it has an autoloader, which automatically loads all those classes that are needed during program execution.

<h3>Installation</h3>

This is modified version. For the original code, see <a href="http://simplemvcframework.com/php-framework">simplemvcframework.com</a> or on <a href="https://github.com/simple-mvc-framework/v1">Github</a>. Note: The original document may differ partially.
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
Thi is an explanation of the contents of the framework.

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

<br>
<h3>Model View Controller</h3>

Model–View–Controller (MVC) is a software architectural pattern for implementing user interfaces. It divides a given software application into three interconnected parts, so as to separate internal representations of information from the ways that information is presented to or accepted from the user. (Wikipedia 19.05.2015 11:02 CET)

<h4>Controller</h4>
The controller contains the program logic, ie those parts in which decisions, which is under what conditions do. From here, the data model will be handed over or received from that. And ultimately, the finished data to be passed to the view, rendered and communicated to the visitors of the site.

Controller always inherit from - surprise - the class Controller, or one of his children. And they come as standard _model about the variables and _view, about which can be accessed on the corresponding model and a general view. example:
<div class="highlight language-php" data-lang="php"><pre><code>$this-&gt;_model-&gt;get($id);
$this-&gt;_view-&gt;render('header', $data);
</code></pre>
</div>
At this point, it is again important to the HTTP methods to call itself into memory. Since links will work through GET, we have methods like DELETE (see example above: ... / users / delete / bob) rebuild as part of the URL. This is problematic in that we have two requests in a request: Deleting a user and display a page. To resolve this conflict, the two parts are separated: To delete a product, the corresponding URL is driven, but rendered no view, but then redirected to another page - for example, an overview of all users. This also prevents e.g. an erase command accidentally requested several times, shared or bookmarked (oO) is.
![alt tag](https://raw.githubusercontent.com/cescgie/Simple-MVC/master/static/img/Controller2.png)

<h4>Model</h4>

The model takes care of everything that has to do with data and writes to the database or read from there. Our <code>user</code>-controller there were a model <code>User_Model</code>, the individual or issue multiple users, create new and can modify and delete existing ones. Models must be in the folder models, such as the controller can be called and bear the suffix <code>_model</code>. (Ie the file of the controller user.php that the model has hot user_model.php.)

<h4>View</h4>

About the View our templates from the folder view will be rendered. A template contains HTML and PHP code to output and little or no own logic. Try to build templates that one - to meet task - and only one. And you can combine these templates later into larger ones. For example, if a search form, you should outsource it to a separate file and integrate them into other templates.

The template can only render data that has been also handed over to him. In Simple MVC the array <code>data</code> is used as a container for it. This new keys and values can always be assigned to the controller. In the example, you will find the key <code>title</code>, which will be presented later on the function <code>render</code> to the template <code>header</code> and output there.

<div class="highlight language-php" data-lang="php"><pre><code>$data['title'] = 'Home';
   ...
$this-&gt;_view-&gt;render('header', $data);
   ...
<span class="nt">&lt;title&gt;</span><span class="cp">&lt;?=</span> <span class="nv">$data</span><span class="p">[</span><span class="s1">'title'</span><span class="p">]</span> <span class="cp">?&gt;</span><span class="nt">&lt;/title&gt;</span>
</code></pre>
</div>

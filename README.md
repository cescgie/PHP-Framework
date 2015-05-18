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
<li>On this example i use apache server. After starting the server, open the browser and go to <code>http://localhost/Simple-MVC/</code>. If there isn’t any problem, you can see <a href="http://www.mediafire.com/view/x8x8xnqc4rdftvg/Screenshoot%202015-05-18%20um%2014.12.49.png">this view</a> on your browser. </li>
</ul>

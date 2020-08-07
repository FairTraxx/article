---


---

<h1 id="pythons-django-a-crash-course-part-1">Python’s Django: A crash course (Part 1)</h1>
<p>Hello, In this short tutorial we are gonna go through a brief overview of the popular backend Python framework <strong>Django</strong>,  According to stackoverflow’s survey Django is currently among the top 5 most favorite frameworks for 2020.  Django is really good with data oriented systems hence it’s used by data oriented services like Spotify and Instagram. There is also great support for REST APIs that allows us to create robust backend black magic.</p>
<h2 id="creating-a-project">Creating a project</h2>
<p><strong>Before you proceed, Make sure you have Python and PIP installed.</strong><br>
To create your first Django project, Start your terminal and install Django and virtualenv (virtual environment)</p>
<pre><code>   pip install Django
   pip install virtualenv
</code></pre>
<p>Now we have Django and virtualenv installed, It’s always a good practice to start your projects in virtual environments to prevent packages and their versions from messing up other packages used in other projects on your local machine.<br>
<strong>Now we are ready to create our django project using :</strong></p>
<pre><code>django-admin startproject mysite
</code></pre>
<p>now django will create a new project in the directory you are in, go ahead and run <code>cd mysite</code> to navigate to that directory we just created.</p>
<h2 id="starting-a-virtual-environment">Starting a virtual environment</h2>
<p>Now that we have a django project installed let’s start a virtual environment to we can properly manage all of our installed packages later on in the project. To do so, run the following:</p>
<pre><code>python -m venv yourenviromentname
</code></pre>
<p>To activate <code>yourenvironmentname</code> run :</p>
<pre><code>yourenvironmentname\Scripts\activate
</code></pre>
<p>In your terminal now you should see yourenvironmentname in the head  of every terminal line and that indicates our venv is activated !</p>
<h2 id="testing...">Testing…</h2>
<p>Now let’s test our project, make sure you are in the main project directory which should look something like this.</p>
<pre><code>mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py
</code></pre>
<p>The <code>manage.py</code> file is the main file that we use to invoke django commands, the mysite is the main project directory which contains our <code>settings.py</code><br>
let’s go ahead and run our server using</p>
<pre><code>python manage.py runserver
</code></pre>
<p>And voila !<br>
You should see something like this in your terminal</p>
<pre><code>Performing system checks...

System check identified no issues (0 silenced).

You have unapplied migrations; your app may not work properly until they are applied.
Run 'python manage.py migrate' to apply them.

August 07, 2020 - 15:50:53
Django version 3.1, using settings 'mysite.settings'
Starting development server at [http://127.0.0.1:8000/](http://127.0.0.1:8000/)
Quit the server with CONTROL-C.
</code></pre>
<h2 id="configuring-pip-and-venv-to-install-packages">configuring pip and venv to install packages</h2>
<p>Now I’ll demonstrate how to install packages in your virtual environment, such that anyone else running the project can install the same packages with the same versions inside their virtual environment.</p>
<p>Inside the main Django project folder (mysite) go ahead an create an empty .txt file, call it <code>requirements.txt</code><br>
Let’s install a package, I’ll install REST Framework since we will use it in the future in this tutorial.</p>
<pre><code>pip install djangorestframework
</code></pre>
<p>Now Django REST Framework is installed, let’s add it to requirements.txt using :</p>
<pre><code>pip freeze &gt; requirements.txt
</code></pre>
<p>Now if you open the .txt file you should see a list of our installed packages<br>
Django<mark>3.0.7<br>
djangorestframework</mark>3.1<br>
This indicates that these are the requirments we need to install in order to successfully run this codebase on our local machine.<br>
<strong>Additionally</strong>, to install these requirements on another environment all you have to do is run :</p>
<pre><code>pip install -r requirements.txt 
</code></pre>
<p>And this will install all the necessary packages</p>
<h2 id="models">Models</h2>
<p>Let’s play around with some models so in our main directory which should look like this</p>
<pre><code>mysite/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        asgi.py
        wsgi.py 
</code></pre>
<p>I will create a new app using</p>
<pre><code>python manage.py startapp REST-Tutorial
</code></pre>
<p>A new folder will now be created in my main directory and it will look like this</p>
<pre><code>REST-Tutorial/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
</code></pre>
<p>i will open <code>REST-Tutorial</code> folder in my favorite editor or IDE and navigate to <code>models.py</code><br>
Inside the <a href="http://models.py">models.py</a> I will write a very simple model, let’s say for example question model .</p>
<pre><code>class  Question(models.Model):
id  = models.UUIDField(primary_key=True, default=uuid.uuid4, editable=False)
category = models.CharField(max_length=100000, on_delete=models.CASCADE)
question = models.CharField(max_length=100000, unique=False, null=False)
answer = models.ForeignKey(Options, related_name="correct", on_delete=models.CASCADE)  
</code></pre>
<p><strong>To be continued</strong>…</p>


<body id="tie-body" class="post-template-default single single-post postid-1200 single-format-standard wrapper-has-shadow block-head-3 magazine2 is-thumb-overlay-disabled is-mobile is-header-layout-1 one-column-no-sidebar post-layout-1 narrow-title-narrow-media is-standard-format hide_post_authorbio hide_post_nav">
<div class="background-overlay" style="height: auto !important;">
<div id="tie-container" class="site tie-container" style="height: auto !important; min-height: 0px !important;">
<div id="tie-wrapper" style="height: auto !important; min-height: 0px !important;">

<div id="content" class="site-content container" style="height: auto !important;">
<div class="tie-row main-content-row" style="height: auto !important;">
<div class="main-content tie-col-md-8 tie-col-xs-12" role="main" style="height: auto !important; min-height: 0px !important;">
<article id="the-post" class="container-wrapper post-content tie-standard" style="height: auto !important;">
<header class="entry-header-outer">
<div class="entry-header">
<h1 class="post-title entry-title">Building A Blog Application With Django</h1>
</div>
</header>
<div class="featured-area"><div class="featured-area-inner"><figure class="single-featured-image"><img width="780" height="405" src="https://djangocentral.com/wp-content/uploads/2019/03/New-Project-21-780x405.png" class="attachment-jannah-image-post size-jannah-image-post wp-post-image" alt="Building a Blog Application With Django"></figure></div></div>
<div class="entry-content entry clearfix" style="height: auto !important;">
<p>In this tutorial, we’ll build a Blog application with Django that allows users to create, edit, and delete posts. The homepage will list all blog posts, and there will be a dedicated detail page for each individual post. Django is capable of making more advanced stuff but making a blog is an excellent first step to get a good grasp over the framework. The purpose of this chapter is to get a general idea about the working of Django.</p>
<p>Here is a sneak peek of what we are going to make.</p>
<p><img class="aligncenter wp-image-1233 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/ezgif.com-video-to-gif.gif" alt="Building a blog with django 2.1" width="600" height="274"></p>
<p>Before kicking off, I hope you already have a brief idea about the framework we are going to use for this project if not then read the following article: <a href="https://djangocentral.com/django-introduction/" rel="noopener noreferrer">Django – Web Framework For Perfectionists</a>.</p>
<h2>Pre-Requirements</h2>
<p>Django is an open-source web framework, written in Python, that follows the model-view-template architectural pattern. So Python is needed to be installed in your machine. Unfortunately, there was a significant update to Python several years ago that created a big split between Python versions namely Python 2 the legacy version and Python 3 the version in active development.</p>
<p>Since Python 3 is the current version in active development and addressed as the future of Python, Django rolled out a significant update, and now all the releases after Django 2.0 are only compatible with Python 3.x. Therefore this tutorial is <strong>strictly for Python 3.x</strong>. Make sure you have Python 3 installed on your machine if not follow the below guides.</p>
<h3>Windows Users</h3>
<ul>
<li><a style="font-size: 16px; font-weight: 400;" href="https://djangocentral.com/how-to-install-python-on-windows/" rel="noopener noreferrer">How To Install Python On Windows</a></li>
</ul>
<h2>Mac And Unix Users</h2>
<ul>
<li><a href="https://djangocentral.com/how-to-install-python-3-and-set-up-a-local-programming-environment-on-mac-os/" rel="noopener noreferrer">How To Install Python 3 on Mac OS</a></li>
</ul>
<h2>Creating And Activating A Virtual Environment</h2>
<p>While building python projects, it’s a good practice to work in virtual environments to keep your project, and it’s dependency isolated on your machine. There is an entire article on the importance of virtual environments Check it out here: <a href="https://djangocentral.com/how-to-a-create-virtual-environment-for-python/" rel="noopener noreferrer">How To A Create Virtual Environment for Python</a></p>
<h3>Windows Users</h3>
<pre><code class="language-python hljs">cd Desktop
virtualenv django
cd django
Scripts\<span class="hljs-built_in">activate</span>.bat</code></pre>
<h3>Mac and Unix Users</h3>
<pre><code class="language-python hljs">mkdir django
<span class="hljs-built_in">cd</span> django
<span class="n"><span class="hljs-attribute">python3</span></span> <span class="o">-</span><span class="n">m</span> <span class="n">venv django</span>
<span class="n"><span class="hljs-built_in">source</span></span> django<span class="o">/</span><span class="nb">bin</span><span class="o">/</span><span class="n"><span class="hljs-built_in">activate</span></span></code></pre>
<p>Now you should see&nbsp;<code>(django)</code>&nbsp;prefixed in your terminal, which indicates that the virtual environment is successfully activated, if not then go through the guide again.</p>
<h2>Installing Django In The Virtual Environment</h2>
<p>If you have already installed Django, you can skip this section and jump straight to the Setting up the project section. To Install Django on your virtual environment run the below command</p>
<pre><code class="shell-session hljs sql">pip <span class="hljs-keyword"><span class="hljs-keyword">install</span></span> Django</code></pre>
<p>This will install the latest version of Django in our virtual environment. To know more about Django installation read: <a href="https://djangocentral.com/how-to-install-django/" rel="noopener noreferrer">How To Install Django</a></p>
<p><strong>Note –&nbsp;</strong>You must install a version of Django greater than 2.0</p>
<h2>Setting Up The Project</h2>
<p>In your workspace create a directory called <code>mysite</code> and navigate into it.</p>
<pre><code class="language-python hljs">cd Desktop
mkdir mysite
cd mysite</code></pre>
<p>Now run the following command in your shell to create a Django project.</p>
<pre><code class="language-python hljs">django-admin startproject mysite</code></pre>
<p>This will generate a project structure with several directories and python scripts.</p>
<pre><code class="language-python hljs">├── mysite
│   ├── __init__<span class="hljs-selector-class">.py</span>
│   ├── settings<span class="hljs-selector-class">.py</span>
│   ├── urls<span class="hljs-selector-class">.py</span>
│   ├── wsgi<span class="hljs-selector-class">.py</span>
├── manage<span class="hljs-selector-class">.py</span></code></pre><div class="google-auto-placed ap_container" style="width: 100%; height: auto; clear: none; text-align: center;"><ins data-ad-format="auto" class="adsbygoogle adsbygoogle-noablate" data-ad-client="ca-pub-6198408027063356" data-adsbygoogle-status="done" style="display: block; margin: auto; background-color: transparent; height: 0px;"><ins id="aswift_2_expand" style="display: inline-table; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent;"><ins id="aswift_2_anchor" style="display: block; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent; overflow: hidden; opacity: 0;"></ins></ins></ins></div>
<p>To know more about the function of the files read: <a href="https://djangocentral.com/starting-a-django-project/" rel="noopener noreferrer">Starting A Django Project</a></p>
<p>Next, we need the create a Django application called blog. A Django application exists to perform a particular task. You need to create specific applications that are responsible for providing your site desired functionalities.</p><div class="google-auto-placed ap_container" style="width: 100%; height: auto; clear: none; text-align: center;"><ins data-ad-format="auto" class="adsbygoogle adsbygoogle-noablate" data-ad-client="ca-pub-6198408027063356" data-adsbygoogle-status="done" style="display: block; margin: auto; background-color: transparent; height: 0px;"><ins id="aswift_3_expand" style="display: inline-table; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent;"><ins id="aswift_3_anchor" style="display: block; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent; overflow: hidden; opacity: 0;"></ins></ins></ins></div>
<p>Navigate into the outer directory where <code>manage.py</code> script exists and run the below command.</p>
<pre><code class="language-python hljs">cd mysite
python manage.py startapp blog</code></pre>
<p>These will create an app named blog in our project.</p>
<pre><code class="language-python hljs">├── db<span class="hljs-selector-class">.sqlite3</span>
├── mysite
│   ├── __init__<span class="hljs-selector-class">.py</span>
│   ├── settings<span class="hljs-selector-class">.py</span>
│   ├── urls<span class="hljs-selector-class">.py</span>
│   ├── wsgi<span class="hljs-selector-class">.py</span>
├── manage<span class="hljs-selector-class">.py</span>
└── blog
    ├── __init__<span class="hljs-selector-class">.py</span>
    ├── admin<span class="hljs-selector-class">.py</span>
    ├── apps<span class="hljs-selector-class">.py</span>
    ├── migrations
    │   └── __init__<span class="hljs-selector-class">.py</span>
    ├── models<span class="hljs-selector-class">.py</span>
    ├── tests<span class="hljs-selector-class">.py</span>
    └── views<span class="hljs-selector-class">.py</span></code></pre><div class="google-auto-placed ap_container" style="width: 100%; height: auto; clear: none; text-align: center;"><ins data-ad-format="auto" class="adsbygoogle adsbygoogle-noablate" data-ad-client="ca-pub-6198408027063356" data-adsbygoogle-status="done" style="display: block; margin: auto; background-color: transparent; height: 0px;"><ins id="aswift_4_expand" style="display: inline-table; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent;"><ins id="aswift_4_anchor" style="display: block; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent; overflow: hidden; opacity: 0;"></ins></ins></ins></div>
<p>Now we need to inform Django that a new application has been created, open your <code>settings.py</code> file and scroll to the installed apps section, which should have some already installed apps.</p>
<pre><code class="language-python hljs">INSTALLED_APPS = [
    <span class="hljs-string"><span class="hljs-string">'django.contrib.admin'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.auth'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.contenttypes'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.sessions'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.messages'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.staticfiles'</span></span>,
]</code></pre><div class="google-auto-placed ap_container" style="width: 100%; height: auto; clear: none; text-align: center;"><ins data-ad-format="auto" class="adsbygoogle adsbygoogle-noablate" data-ad-client="ca-pub-6198408027063356" data-adsbygoogle-status="done" style="display: block; margin: auto; background-color: transparent; height: 0px;"><ins id="aswift_5_expand" style="display: inline-table; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent;"><ins id="aswift_5_anchor" style="display: block; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent; overflow: hidden; opacity: 0;"></ins></ins></ins></div>
<p>Now add the newly created app blog at the bottom and save it.</p>
<pre><code class="language-python hljs">INSTALLED_APPS = [
    <span class="hljs-string"><span class="hljs-string">'django.contrib.admin'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.auth'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.contenttypes'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.sessions'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.messages'</span></span>,
    <span class="hljs-string"><span class="hljs-string">'django.contrib.staticfiles'</span></span>,
    <span class="hljs-string">'blog'</span>
]</code></pre>
<p>Next, make migrations.</p>
<pre><code class="language-python hljs">python manage.py migrate</code></pre>
<p>This will apply all the unapplied migrations on the SQLite database which comes along with the Django installation.</p>
<p>Let’s test our configurations by running the&nbsp; Django’s built-in development server.</p>
<pre><code class="language-python hljs">python manage.py runserver</code></pre>
<p>Open your browser and go to this address <code>http://127.0.0.1:8000/</code> if everything went well you should see this page.</p>
<h2><img class="aligncenter wp-image-1151 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1552995251107.png" alt="Starting A Django Project" width="1497" height="778" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1552995251107.png 1497w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1552995251107-300x156.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1552995251107-768x399.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1552995251107-1024x532.png 1024w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1552995251107-780x405.png 780w" sizes="(max-width: 1497px) 100vw, 1497px"><br>
Database Models</h2>
<p>Now we will define the data models for our blog. A model is a <a href="https://djangocentral.com/classes-in-python/" target="_blank" rel="noopener noreferrer">Python class</a> that subclasses <code>django.db.models.Model</code>, in which each attribute represents a database field. Using this subclass functionality, we automatically have access to everything within <a class="msbooks-tabindex-restored" tabindex="0" href="https://docs.djangoproject.com/en/2.1/topics/db/models/">django.db.models.Models</a> and can add additional fields and methods as desired.&nbsp;We will have a Post model in our database to store posts.</p>
<pre><code class="language-python hljs"><span class="hljs-keyword">from</span> django.db <span class="hljs-keyword">import</span> models
<span class="hljs-keyword">from</span> django.contrib.auth.models <span class="hljs-keyword">import</span> User


STATUS = (
    (<span class="hljs-number">0</span>,<span class="hljs-string">"Draft"</span>),
    (<span class="hljs-number">1</span>,<span class="hljs-string">"Publish"</span>)
)

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Post</span><span class="hljs-params">(models.Model)</span>:</span>
    title = models.CharField(max_length=<span class="hljs-number">200</span>, unique=<span class="hljs-literal">True</span>)
    slug = models.SlugField(max_length=<span class="hljs-number">200</span>, unique=<span class="hljs-literal">True</span>)
    author = models.ForeignKey(User, on_delete= models.CASCADE,related_name=<span class="hljs-string">'blog_posts'</span>)
    updated_on = models.DateTimeField(auto_now= <span class="hljs-literal">True</span>)
    content = models.TextField()
    created_on = models.DateTimeField(auto_now_add=<span class="hljs-literal">True</span>)
    status = models.IntegerField(choices=STATUS, default=<span class="hljs-number">0</span>)

    <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Meta</span>:</span>
        ordering = [<span class="hljs-string">'-created_on'</span>]

    <span class="hljs-function"><span class="hljs-keyword">def</span> <span class="hljs-title">__str__</span><span class="hljs-params">(self)</span>:</span>
        <span class="hljs-keyword">return</span> self.title
</code></pre><div class="google-auto-placed ap_container" style="width: 100%; height: auto; clear: none; text-align: center;"><ins data-ad-format="auto" class="adsbygoogle adsbygoogle-noablate" data-ad-client="ca-pub-6198408027063356" data-adsbygoogle-status="done" style="display: block; margin: auto; background-color: transparent; height: 0px;"><ins id="aswift_6_expand" style="display: inline-table; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent;"><ins id="aswift_6_anchor" style="display: block; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent; overflow: hidden; opacity: 0;"></ins></ins></ins></div>
<p>At the top, we’re importing the class <code>models</code> and then creating a subclass of <code>models.Model</code> Like any typical blog, each blog post will have a title, slug, author name, and the timestamp or date when the article was published or last updated.</p>
<p>Notice how we declared a tuple for <code>STATUS</code> of a post to keep draft and published posts separated when we render them out with templates.</p>
<p>The Meta class inside the model contains metadata. We tell Django to sort results in the <code>created_on</code> field in descending order by default when we query the database. We specify descending order using the negative prefix. By doing so, posts published recently will appear first.</p><div class="google-auto-placed ap_container" style="width: 100%; height: auto; clear: none; text-align: center;"><ins data-ad-format="auto" class="adsbygoogle adsbygoogle-noablate" data-ad-client="ca-pub-6198408027063356" data-adsbygoogle-status="done" style="display: block; margin: auto; background-color: transparent; height: 0px;"><ins id="aswift_7_expand" style="display: inline-table; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent;"><ins id="aswift_7_anchor" style="display: block; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent; overflow: hidden; opacity: 0;"></ins></ins></ins></div>
<p>The <code>__str__()</code> method is the default human-readable representation of the object. Django will use it in many places, such as the administration site.</p>
<p>Now that our new database model is created we need to create a new migration record for it and migrate the change into our database.</p>
<pre><code class="language-python hljs">(django) $ python manage.py makemigrations 
(django) $ python manage.py migrate</code></pre>
<p>Now we are done with the database.</p>
<h2>Creating An Administration Site</h2>
<p>We will create an admin panel to create and manage Posts. Fortunately, Django comes with an inbuilt admin interface for such tasks.</p>
<p>In order to use the Django admin first, we need to create a superuser by running the following command in the prompt.</p>
<pre><code class="language-python hljs">python manage.py createsuperuser</code></pre>
<p>You will be prompted to enter email, password, and username. Note that for security concerns Password won’t be visible.</p>
<pre><code class="language-python hljs">Username (leave blank to use <span class="hljs-string">'user'</span>): admin
Email address: admin@gamil.com
Password:
Password (again):</code></pre><div class="google-auto-placed ap_container" style="width: 100%; height: auto; clear: none; text-align: center;"><ins data-ad-format="auto" class="adsbygoogle adsbygoogle-noablate" data-ad-client="ca-pub-6198408027063356" data-adsbygoogle-status="done" style="display: block; margin: auto; background-color: transparent; height: 0px;"><ins id="aswift_8_expand" style="display: inline-table; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent;"><ins id="aswift_8_anchor" style="display: block; border: none; height: 0px; margin: 0px; padding: 0px; position: relative; visibility: visible; width: 750px; background-color: transparent; overflow: hidden; opacity: 0;"></ins></ins></ins></div>
<p>Enter any details you can always change them later. After that rerun the development server and go to the address <code>http://127.0.0.1:8000/admin/</code></p>
<pre><code class="language-python hljs">python manage.py runserver</code></pre>
<p>You should see a login page, enter the details you provided for the superuser.</p>
<p><img class="aligncenter wp-image-1204 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612048937.png" alt="Django Admin login" width="1566" height="1102" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612048937.png 1566w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612048937-300x211.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612048937-768x540.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612048937-1024x721.png 1024w" sizes="(max-width: 1566px) 100vw, 1566px"></p>
<p>After you log in you should see a basic admin panel with Groups and Users models which come from Django authentication framework located in <code>django.contrib.auth</code>.</p>
<p><img class="aligncenter wp-image-1205 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612316308.png" alt="Building a Blog application with Django" width="1566" height="758" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612316308.png 1566w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612316308-300x145.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612316308-768x372.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553612316308-1024x496.png 1024w" sizes="(max-width: 1566px) 100vw, 1566px"><br>
Still, we can’t create posts from the panel we need to add the Post model to our admin.</p>
<h2>Adding Models To The Administration Site</h2>
<p>Open the <code>blog/admin.py</code> file and register the Post model there as follows.</p>
<pre><code class="language-python hljs"><span class="hljs-keyword">from</span> django.contrib <span class="hljs-keyword">import</span> admin
<span class="hljs-keyword">from</span> .models <span class="hljs-keyword">import</span> Post 

admin.site.register(Post)</code></pre>
<p>Save the file and refresh the page you should see the Posts model there.</p>
<p><img class="aligncenter wp-image-1221 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553823885694.png" alt="Building Blog application with django admin" width="1536" height="801" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553823885694.png 1536w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553823885694-300x156.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553823885694-768x401.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553823885694-1024x534.png 1024w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553823885694-1170x610.png 1170w" sizes="(max-width: 1536px) 100vw, 1536px"><br>
Now let’s create our first blog post click on the Add icon beside Post which will take you to another page where you can create a post. Fill the respective forms and create your first ever post.</p>
<p><img class="aligncenter wp-image-1230 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553962571432.png" alt="Writing blog Post with Django" width="1482" height="809" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553962571432.png 1482w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553962571432-300x164.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553962571432-768x419.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553962571432-1024x559.png 1024w" sizes="(max-width: 1482px) 100vw, 1482px"><br>
Once you are done with the Post save it now, you will be redirected to the post list page with a success message at the top.</p>
<p><img class="aligncenter wp-image-1209 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553613384141.png" alt="Building a Blog Application With Django" width="1566" height="807" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553613384141.png 1566w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553613384141-300x155.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553613384141-768x396.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553613384141-1024x528.png 1024w" sizes="(max-width: 1566px) 100vw, 1566px"></p>
<p>Though it does the work, we can customize the way data is displayed in the administration panel according to our convenience. Open the <code>admin.py</code> file again and replace it with the code below.</p>
<pre><code class="language-python hljs"><span class="hljs-keyword">from</span> django.contrib <span class="hljs-keyword">import</span> admin
<span class="hljs-keyword">from</span> .models <span class="hljs-keyword">import</span> Post

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PostAdmin</span><span class="hljs-params">(admin.ModelAdmin)</span>:</span>
    list_display = (<span class="hljs-string">'title'</span>, <span class="hljs-string">'slug'</span>, <span class="hljs-string">'status'</span>,<span class="hljs-string">'created_on'</span>)
    list_filter = (<span class="hljs-string">"status"</span>,)
    search_fields = [<span class="hljs-string">'title'</span>, <span class="hljs-string">'content'</span>]
    prepopulated_fields = {<span class="hljs-string">'slug'</span>: (<span class="hljs-string">'title'</span>,)}
  
admin.site.register(Post, PostAdmin)</code></pre>
<p>This will make our admin dashboard more efficient. Now if you visit the post list, you will see more details about the Post.</p>
<p><img class="aligncenter wp-image-1222 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824052453.png" alt="Creating a Blog Application With Django" width="1506" height="758" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824052453.png 1506w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824052453-300x151.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824052453-768x387.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824052453-1024x515.png 1024w" sizes="(max-width: 1506px) 100vw, 1506px"></p>
<p>Note that I have added a few posts for testing.</p>
<p>The <code>list_display</code> attribute does what its name suggests display the properties mentioned in the tuple in the post list for each post.</p>
<p>If you notice at the right, there is a filter which is filtering the post depending on their Status this is done by the <code>list_filter</code> method.</p>
<p>And now we have a search bar at the top of the list, which will search the database from the <code>search_fields</code> attributes. The last attribute <code>prepopulated_fields</code> populates the slug, now if you create a post the slug will automatically be filled based upon your title.</p>
<p>Now that our database model is complete we need to create the necessary views, URLs, and templates so we can display the information on our web application.</p>
<h2>Building Views</h2>
<p>A Django view is just a <a href="https://djangocentral.com/functions-in-python/" target="_blank" rel="noopener noreferrer">Python function</a> that receives a web request and returns a web response. We’re going to use class-based views then map URLs for each view and create an HTML templated for the data returned from the views.</p>
<p>Open the <code>blog/views.py</code> file and start coding.</p>
<pre><code class="language-python hljs"><span class="hljs-keyword">from</span> django.views <span class="hljs-keyword">import</span> generic
<span class="hljs-keyword">from</span> .models <span class="hljs-keyword">import</span> Post

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PostList</span><span class="hljs-params">(generic.ListView)</span>:</span>
    queryset = Post.objects.filter(status=<span class="hljs-number">1</span>).order_by(<span class="hljs-string">'-created_on'</span>)
    template_name = <span class="hljs-string">'index.html'</span>

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PostDetail</span><span class="hljs-params">(generic.DetailView)</span>:</span>
    model = Post
    template_name = <span class="hljs-string">'post_detail.html'</span>
</code></pre>
<p>The built-in ListViews which is a subclass of generic class-based-views render a list with the objects of the specified model we just need to mention the template, similarly DetailView provides a detailed view for a given object of the model at the provided template.</p>
<p>Note that for <code>PostList</code> view we have applied a filter so that only the post with status published be shown at the front end of our blog. Also in the same query, we have arranged all the posts by their creation date. The ( – ) sign before the <code>created_on</code> signifies the latest post would be at the top and so on.</p>
<h2>Adding URL patterns for Views</h2>
<p>We need to map the URL for the views we made above. When a user makes a request for a page on your web app, the Django controller takes over to look for the corresponding view via the <code>urls.py</code> file, and then return the HTML response or a 404 not found error, if not found.</p>
<p>Create an <code>urls.py</code> file in your blog application directory and add the following code.</p>
<pre><code class="language-python hljs"><span class="hljs-keyword">from</span> . <span class="hljs-keyword">import</span> views
<span class="hljs-keyword">from</span> django.urls <span class="hljs-keyword">import</span> path

urlpatterns = [
    path(<span class="hljs-string">''</span>, views.PostList.as_view(), name=<span class="hljs-string">'home'</span>),
    path(<span class="hljs-string">'&lt;slug:slug&gt;/'</span>, views.PostDetail.as_view(), name=<span class="hljs-string">'post_detail'</span>),
]</code></pre>
<p>We mapped general URL patterns for our views using the path function. The first pattern takes an empty string denoted by <code>' '</code> and returns the result generated from the <code>PostList</code> view which is essentially a list of posts for our homepage and at last we have an optional parameter name which is basically a name for the view which will later be used in the templates.</p>
<p>Names are an optional parameter, but it is a good practice to give unique and rememberable names to views which makes our work easy while designing templates and it helps keep things organized as your number of URLs grows.</p>
<p>Next, we have the generalized expression for the <code>PostDetail</code> views which resolve the slug (a string consisting of ASCII letters or numbers) Django uses angle brackets <code>&lt; &gt;</code> to capture the values from the URL and return the equivalent post detail page.</p>
<p>Now we need to include these blog URLs to the actual project for doing so open the <code>mysite/urls.py</code> file.</p>
<pre><code class="language-python hljs"><span class="hljs-keyword">from</span> django.contrib <span class="hljs-keyword">import</span> admin

urlpatterns = [
    path(<span class="hljs-string">'admin/'</span>, admin.site.urls),
]
</code></pre>
<p>Now first import the include function and then add the path to the new <code>urls.py</code> file in the URL patterns list.</p>
<pre><code class="language-python hljs"><span class="hljs-keyword">from</span> django.contrib <span class="hljs-keyword">import</span> admin
<span class="hljs-keyword">from</span> django.urls <span class="hljs-keyword">import</span> path, include

urlpatterns = [
    path(<span class="hljs-string">'admin/'</span>, admin.site.urls),
    path(<span class="hljs-string">''</span>, include(<span class="hljs-string">'blog.urls'</span>)),
]
</code></pre>
<p>Now all the request will directly be handled by the blog app.</p>
<h2>Creating Templates For The Views</h2>
<p>We are done with the Models and Views now we need to make templates to render the result to our users. To use Django templates we need to <a href="https://djangocentral.com/configuring-django-templates/" rel="noopener noreferrer">configure the template setting</a> first.</p>
<p>Create directory templates in the base directory. Now open the project’s <code>settings.py</code> file and just below <code>BASE_DIR</code> add the route to the template directory as follows.</p>
<pre><code class="language-python hljs">TEMPLATES_DIRS = os.path.join(BASE_DIR,<span class="hljs-string">'templates'</span>)
</code></pre>
<p>Now In&nbsp;<code>settings.py</code>&nbsp;scroll to the,<code>TEMPLATES</code> which should look like this.</p>
<pre><code class="language-python hljs">TEMPLATES = [
    {
        <span class="hljs-string"><span class="hljs-string">'BACKEND'</span></span>: <span class="hljs-string"><span class="hljs-string">'django.template.backends.django.DjangoTemplates'</span></span>,
        <span class="hljs-string"><span class="hljs-string">'DIRS'</span></span>: [],
        <span class="hljs-string"><span class="hljs-string">'APP_DIRS'</span></span>: <span class="hljs-keyword"><span class="hljs-literal">True</span></span>,
        <span class="hljs-string"><span class="hljs-string">'OPTIONS'</span></span>: {
            <span class="hljs-string"><span class="hljs-string">'context_processors'</span></span>: [
                <span class="hljs-string"><span class="hljs-string">'django.template.context_processors.debug'</span></span>,
                <span class="hljs-string"><span class="hljs-string">'django.template.context_processors.request'</span></span>,
                <span class="hljs-string"><span class="hljs-string">'django.contrib.auth.context_processors.auth'</span></span>,
                <span class="hljs-string"><span class="hljs-string">'django.contrib.messages.context_processors.messages'</span></span>,
            ],
        },
    },
]
</code></pre>
<p>Now add the newly created&nbsp;<code>TEMPLATE_DIRS</code>&nbsp; in the&nbsp;<code>DIRS</code>.</p>
<pre><code class="language-python hljs">TEMPLATES = [
    {
        <span class="hljs-string"><span class="hljs-string">'BACKEND'</span></span>: <span class="hljs-string"><span class="hljs-string">'django.template.backends.django.DjangoTemplates'</span></span>,
        <span class="hljs-comment"><span class="hljs-comment">#  Add  'TEMPLATE_DIRS' here</span></span>
        <span class="hljs-string"><span class="hljs-string">'DIRS'</span></span>: [TEMPLATE_DIRS],
        <span class="hljs-string"><span class="hljs-string">'APP_DIRS'</span></span>: <span class="hljs-keyword"><span class="hljs-literal">True</span></span>,
        <span class="hljs-string"><span class="hljs-string">'OPTIONS'</span></span>: {
            <span class="hljs-string"><span class="hljs-string">'context_processors'</span></span>: [
                <span class="hljs-string"><span class="hljs-string">'django.template.context_processors.debug'</span></span>,
                <span class="hljs-string"><span class="hljs-string">'django.template.context_processors.request'</span></span>,
                <span class="hljs-string"><span class="hljs-string">'django.contrib.auth.context_processors.auth'</span></span>,
                <span class="hljs-string"><span class="hljs-string">'django.contrib.messages.context_processors.messages'</span></span>,
            ],
        },
    },
]</code></pre>
<p>Now save and close the file we are done with the configurations.</p>
<p>Django makes it possible to separate python and HTML, the python goes in views and HTML goes in templates. Django has a powerful template language that allows you to specify how data is displayed. It is based on template tags, template variables, and template filters.</p>
<p>I’ll start off with a <code class="calibre21">base.html</code> file and a <code class="calibre21">index.html</code> file that inherits from it. Then later when we add templates for homepage and post detail pages, they too can inherit from <code class="calibre21">base.html</code>.</p>
<p>Let’s start with the base.html file which will have common elements for the blog at any page like the navbar and footer. Also, we are using <a href="https://getbootstrap.com/" rel="noopener noreferrer">Bootstrap</a> for the UI and Roboto font.</p>
<pre></pre>
<div>
<p>This is a regular HTML file except for the tags inside curly braces <code>{ }</code> these are called template tags.</p>
<p>The <code>{% url 'home' %}</code> Returns an absolute path reference, it generates a link to the home view which is also the List view for posts.</p>
<p>The <code>{% block content %}</code> Defines a block that can be overridden by child templates, this is where the content from the other HTML file will get injected.</p>
<p>Next, we will make a small sidebar widget which will be inherited by all the pages across the site. Notice sidebar is also being injected in the <code>base.html</code> file this makes it globally available for pages inheriting the base file.</p>
<pre><code class="language-html hljs xml">{% block sidebar %}

<span class="hljs-tag">&lt;<span class="hljs-name">style</span>&gt;</span><span class="css">
        <span class="hljs-selector-class">.card</span>{
            <span class="hljs-attribute">box-shadow</span>: <span class="hljs-number">0</span> <span class="hljs-number">16px</span> <span class="hljs-number">48px</span> <span class="hljs-number">#E3E7EB</span>;
        }
       
</span><span class="hljs-tag">&lt;/<span class="hljs-name">style</span>&gt;</span>

<span class="hljs-comment">&lt;!-- Sidebar Widgets Column --&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"col-md-4 float-right "</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card my-4"</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">h5</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-header"</span>&gt;</span>About Us<span class="hljs-tag">&lt;/<span class="hljs-name">h5</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-body"</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-text"</span>&gt;</span> This awesome blog is made on the top of our Favourite full stack Framework 'Django', follow up the tutorial to learn how we made it..!<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">a</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"https://djangocentral.com/building-a-blog-application-with-django"</span>
           <span class="hljs-attr">class</span>=<span class="hljs-string">"btn btn-danger"</span>&gt;</span>Know more!<span class="hljs-tag">&lt;/<span class="hljs-name">a</span>&gt;</span>
    <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>

{% endblock sidebar %}</code></pre>
</div>
<p>Next, create the <code>index.html</code> file of our blog that’s the homepage.</p>
<pre><code class="language-html hljs xml">{% extends "base.html" %} 
{% block content %}
<span class="hljs-tag">&lt;<span class="hljs-name">style</span>&gt;</span><span class="css">
    <span class="hljs-selector-tag">body</span> {
        <span class="hljs-attribute">font-family</span>: <span class="hljs-string">"Roboto"</span>, sans-serif;
        <span class="hljs-attribute">font-size</span>: <span class="hljs-number">18px</span>;
        <span class="hljs-attribute">background-color</span>: <span class="hljs-number">#fdfdfd</span>;
    }
    
    <span class="hljs-selector-class">.head_text</span> {
        <span class="hljs-attribute">color</span>: white;
    }
    
    <span class="hljs-selector-class">.card</span> {
        <span class="hljs-attribute">box-shadow</span>: <span class="hljs-number">0</span> <span class="hljs-number">16px</span> <span class="hljs-number">48px</span> <span class="hljs-number">#E3E7EB</span>;
    }
</span><span class="hljs-tag">&lt;/<span class="hljs-name">style</span>&gt;</span>

<span class="hljs-tag">&lt;<span class="hljs-name">header</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"masthead"</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"overlay"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"container"</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"row"</span>&gt;</span>
            <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">" col-md-8 col-md-10 mx-auto"</span>&gt;</span>
                <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"site-heading"</span>&gt;</span>
                    <span class="hljs-tag">&lt;<span class="hljs-name">h3</span> <span class="hljs-attr">class</span>=<span class="hljs-string">" site-heading my-4 mt-3 text-white"</span>&gt;</span> Welcome to my awesome Blog <span class="hljs-tag">&lt;/<span class="hljs-name">h3</span>&gt;</span>
                    <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"text-light"</span>&gt;</span>We Love Django As much as you do..! &amp;nbsp
                    <span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
                <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
            <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
        <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
    <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">header</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"container"</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"row"</span>&gt;</span>
        <span class="hljs-comment">&lt;!-- Blog Entries Column --&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"col-md-8 mt-3 left"</span>&gt;</span>
            {% for post in post_list %}
            <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card mb-4"</span>&gt;</span>
                <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-body"</span>&gt;</span>
                    <span class="hljs-tag">&lt;<span class="hljs-name">h2</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-title"</span>&gt;</span>{{ post.title }}<span class="hljs-tag">&lt;/<span class="hljs-name">h2</span>&gt;</span>
                    <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-text text-muted h6"</span>&gt;</span>{{ post.author }} | {{ post.created_on}} <span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
                    <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-text"</span>&gt;</span>{{post.content|slice:":200" }}<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
                    <span class="hljs-tag">&lt;<span class="hljs-name">a</span> <span class="hljs-attr">href</span>=<span class="hljs-string">"{% url 'post_detail' post.slug  %}"</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"btn btn-primary"</span>&gt;</span>Read More <span class="hljs-symbol">&amp;rarr;</span><span class="hljs-tag">&lt;/<span class="hljs-name">a</span>&gt;</span>
                <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
            <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
            {% endfor %}
        <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
        {% block sidebar %} {% include 'sidebar.html' %} {% endblock sidebar %}
    <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
{%endblock%}</code></pre>
<p>With the <code>{% extends %}</code> template tag, we tell Django to inherit from the base.html template. Then, we are filling the content blocks of the base template with content.</p>
<p>Notice we are using <a href="https://djangocentral.com/while-loops-in-python/" target="_blank" rel="noopener noreferrer">for loop</a> in HTML that’s the power of Django templates it makes HTML Dynamic. The loop is iterating through the posts and displaying their title, date, author, and body, including a link in the title to the canonical URL of the post.</p>
<p>In the body of the post, we are also using template filters to limit the words on the excerpts to 200 characters. Template filters allow you to modify variables for display and look like <code>{{ variable | filter }}</code>.</p>
<p>Now run the server and visit <code>http://127.0.0.1:8000/</code> you will see the homepage of our blog.</p>
<p><img class="aligncenter wp-image-1223 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824626096.png" alt="blog made with django" width="1468" height="807" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824626096.png 1468w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824626096-300x165.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824626096-768x422.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824626096-1024x563.png 1024w" sizes="(max-width: 1468px) 100vw, 1468px"></p>
<p>Looks good..!</p>
<p>You might have noticed I have imported some dummy content to fill the page you can do the same using this <a href="https://toolspit.com/generate/lorem" target="_blank" rel="noopener noreferrer">lorem ipsum generator tool</a>.</p>
<p>Now let’s make an HTML template for the detailed view of our posts.</p>
<p>Next, Create a file <code>post_detail.html</code> and paste the below HTML there.</p>
<pre><code class="language-html hljs xml">{% extends 'base.html' %} {% block content %}

<span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"container"</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"row"</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"col-md-8 card mb-4  mt-3 left  top"</span>&gt;</span>
      <span class="hljs-tag">&lt;<span class="hljs-name">div</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-body"</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">h1</span>&gt;</span>{% block title %} {{ object.title }} {% endblock title %}<span class="hljs-tag">&lt;/<span class="hljs-name">h1</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">" text-muted"</span>&gt;</span>{{ post.author }} | {{ post.created_on }}<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">p</span> <span class="hljs-attr">class</span>=<span class="hljs-string">"card-text "</span>&gt;</span>{{ object.content | safe }}<span class="hljs-tag">&lt;/<span class="hljs-name">p</span>&gt;</span>
      <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
    <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
    {% block sidebar %} {% include 'sidebar.html' %} {% endblock sidebar %}
  <span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">div</span>&gt;</span>

{% endblock content %}
</code></pre>
<p>At the top, we specify that this template inherits from.<code>base.html</code> Then display the <code>body</code> from our context object, which <code>DetailView</code> makes accessible as an object.</p>
<p>Now visit the homepage and click on read more, it should redirect you to the post detail page.</p>
<p><img class="aligncenter wp-image-1224 size-full" src="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824848299.png" alt="Blog detail page with django" width="1478" height="807" srcset="https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824848299.png 1478w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824848299-300x164.png 300w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824848299-768x419.png 768w, https://djangocentral.com/wp-content/uploads/2019/03/screely-1553824848299-1024x559.png 1024w" sizes="(max-width: 1478px) 100vw, 1478px"></p>
<h2>Extending The Application</h2>
<p>Adding Comments System – <a href="https://djangocentral.com/creating-comments-system-with-django/" target="_blank" rel="noopener noreferrer">https://djangocentral.com/creating-comments-system-with-django/</a></p>
<p>Adding Pagination to the Index page –&nbsp;<a href="https://djangocentral.com/adding-pagination-with-django/" target="_blank" rel="noopener noreferrer">https://djangocentral.com/adding-pagination-with-django/</a></p>
<p>Integrating PostgreSQL with Django –&nbsp;<a href="https://djangocentral.com/using-postgresql-with-django/" target="_blank" rel="noopener noreferrer">https://djangocentral.com/using-postgresql-with-django/</a></p>
<p>Configuring static assets –&nbsp;<a href="https://djangocentral.com/static-assets-in-django/" target="_blank" rel="noopener noreferrer">https://djangocentral.com/static-assets-in-django/</a></p>
<p class="post-title entry-title">Integrating Summernote WYSIWYG Editor –&nbsp;<a href="https://djangocentral.com/integrating-summernote-in-django/" target="_blank" rel="noopener noreferrer">Integrating Summernote WYSIWYG Editor in Django&nbsp;</a></p>
<p>Creating Sitemap –&nbsp;<a href="https://djangocentral.com/creating-sitemaps-in-django/" target="_blank" rel="noopener noreferrer">https://djangocentral.com/creating-sitemaps-in-django/</a></p>
<p>Creating Feeds –&nbsp;<a href="https://djangocentral.com/creating-feeds-with-django/" target="_blank" rel="noopener noreferrer">https://djangocentral.com/creating-feeds-with-django/</a></p>
<p>Deploy Django Application –&nbsp;<a href="https://djangocentral.com/deploy-django-with-nginx-gunicorn-postgresql-and-lets-encrypt-ssl-on-ubuntu/" target="_blank" rel="noopener noreferrer">How To Deploy Django App with Nginx, Gunicorn, PostgreSQL and Let’s Encrypt SSL on Ubuntu</a></p>
</body>

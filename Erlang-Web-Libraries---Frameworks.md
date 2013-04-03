# Erlang Web Libraries & Frameworks

**Original Date: August 2011**

This post used to exist on my blog. It's far more useful to exist here, where others can contribute to it too.

<p>
  Recently I needed to compare a few Erlang web libraries and frameworks for a
  friend who was writing a simple internal API endpoint.
  He suggested I should publish the rundown for others, so here it is.
</p>

<p>
  Thanks to everyone that has provided corrections and updates since I originally
  published this post.
</p>

<h2><a href="http://yaws.hyber.org/">Yaws</a></h2>
<p>
  Yaws is a high performance web server aimed mostly at serving dynamic web pages.
  However, using <a href="http://yaws.hyber.org/appmods.yaws">appmods</a>, it is
  possible to construct an API instead.
</p>
<p>
  The Yaws documentation is good, and it looks very well put together. It can be
  embedded into a supervision hierachy.
</p>

<h2><a href="https://github.com/mochi/mochiweb">Mochiweb</a></h2>
<p>
  This one seems to be one of the most-used libraries for API development
  with Erlang. Overall it does the job, but it does have a few quirks.
</p>
<p>
  The docs for mochiweb aren't very good, and it uses parameterised modules quite
  a lot, which I don't like. That said, it's trivial to embed into another erlang
  application.
</p>

<h2><a href="https://github.com/ostinelli/misultin">Misultin</a></h2>
<p>
  Misultin seems very similar in general architecture to Mochiweb, except that
  it also includes support for websockets.
</p>
<p>
  The examples are well put-together and clear. There is also copious documentation
  in <a href="https://github.com/ostinelli/misultin/wiki/Exports">their wiki</a>.
</p>

<h2><a href="https://github.com/extend/cowboy">Cowboy</a></h2>
<p>
  Cowboy is also fairly similar to Mochiweb, only without the parameterised modules
  and instead using whole modules to handle requests. Cowboy is (I think) one of
  the only fully-binary HTTP Servers, for increased speed and lower memory usage.
</p>
<p>
  There are examples of how to use it in
  <a href="https://github.com/extend/cowboy_examples">this Repository on github</a>.
</p>

<h2><a href="http://erldocs.com/R14B03/inets/httpd.html">httpd</a></h2>
<p>
  The httpd module comes bundled as part of the inets application, which suggests
  that it's good enough for lots of uses, and if you need to get up and running
  quickly. httpd is the only one on the list with support for WSGI- or Rack-like
  middleware, for chaining arbitary request handlers together.
</p>
<p>
  Unfortunately, it also has a fixation on using one single callback function
  and the docs aren't that great. To help when writing httpd mods, Garrett
  Smith wrote <a href="https://github.com/gar1t/modlib">modlib</a> which is a
  wrapper library to help clear up the API somewhat.
</p>

<h2><a href="https://github.com/nitrogen/simple_bridge">SimpleBridge</a></h2>
<p>
  Speaking of wrappers, SimpleBridge is a project "to provide a simple,
  standardized interface to Erlang HTTP Servers". What this means in practice is
  that you wrap the framework you're using's request and response objects in
  some SimpleBridge Adapters so that it's slightly easier to change which
  library you're actually using.
</p>
<p>
  I feel that SimpleBridge doesn't quite go far enough to be a HTTP Library
  adapter. It has support for Mochiweb, Inets httpd and Yaws, with support for
  Misultin in the pipeline.
</p>

<h2><a href="http://webmachine.basho.com/">webmachine</a></h2>
<p>
  This is built upon mochiweb, but abstracts you away from lots of the lower-level
  HTTP semantics. Instead it bills itself as a &ldquo;REST Toolkit&rdquo;.
</p>
<p>
  For Basic RPC over HTTP applications, this isn't what you'd use, however, it
  makes lots of sense if the application is very resource-orientated. As it's
  come out of Basho, I'd expect it to be well written and documented.
</p>

<h2><a href="https://github.com/flashingpumpkin/spooky">Spooky</a></h2>
<p>
  Spooky is a web framework built on top of Misultin. Its API has semantics
  similar to <a href="http://sinatrarb.com">Sinatra</a>, a Ruby web framework.
</p>
<p>
  Spooky also brings middleware and the ability to stack other handlers, something
  similar to how WSGI (Python) or Rack (Ruby) work. It seems to also be built so
  it can fit into an OTP application.
</p>
<p>
  Here is a
  <a href="http://owns.ch/tiny-lightweight-erlang-web-framework-spooky.html">blog post about Spooky</a>,
  which is a good introduction to the framework.
</p>

<h2><a href="http://nitrogenproject.com/">Nitrogen</a></h2>
<p>
  Nitrogen is aimed more at building functional user interfaces.
  It brings its own system for sending events back and forth between the client
  and the server which I find very interesting. Here's an
  <a href="http://nitrogenproject.com/doc/tutorial.html">Introduction to Nitrogen</a>.
</p>
<p>
  As every page is just a module, and templates are optional, it is trivial to
  construct an API with Nitrogen.
</p>

<h2><a href="http://zotonic.com/">Zotonic</a></h2>
<p>
  Zotonic is a fully-fledged CMS, with included support for WebSocets and Comet.
  It is easy to extend, and there is quite a lot of documentation on their site.
</p>
<p>
  From what I can tell, it uses webmachine and nitrogen underneath, but it is
  also possible to define your own API inside a site, complete with OAuth support.
</p>

<h2><a href="http://chicagoboss.org/">Chicago Boss</a></h2>
<p>
  This framework is much closer to what Rails is for Ruby. It has models and lots
  of already-implemented behaviour to bring you up to speed quickly. Probably
  too complex for a simple API, but it depends on what you're doing.
</p>

# Algolia meets Marc & vice versa

<center> Algolia, 2017-09-21 </center>
<br>
<center><div style="line-height:220px; text-align:center"> <img src="algolia-mark-blue.png" width="120px">  +  <img style="border-radius:30px" src="marc.jpg" width="120px"> </div> </center>


***

[Marc Helbling](https://twitter.com/marchelbling)

Software engineer@[sketchfab.com](http://sketchfab.com)

<center> <img width="320px" src="the_captain.gif">  <img width="320px" src="rosetta_stone.gif"> </center>


# Previously

<center> <img width="90px" src="ds.png"> / <img width="190px" src="tc.png"> / <img width="120px" src="ct.png"> </center>

***

<center> <img width="400px" src="birdie.png"> </center>
<p class="footnote">fulguroboom</p>


# Algolia ❤

<center> product 👫 community <center>


# Algolia ❤

<center> product 👫 community <center>

Milliseconds matter. Size does too!


# Algolia ❤

<center> product 👫 community <center>

Milliseconds matter. Size does too!<br>
⇒  helping Anthony & Sylvain to (re)build the analytics infrastructure?


***

<img width="900px" src="gltf-blue.png">


# glTF

* new standard for 3D data transmission
* glTF 1.0 2015/10 →  glTF 2.0 2017/06
* supports all modern 3D features (animation, PBR materials)
* human/machine friendly (JSON + binary buffers)


# A big deal for Sketchfab?

* very good industry adoption
    * major open-source projects
    * new major industry actors
    <center> <img width="400px" src="apple-gltf.png"> </center>
    * traditional actors _will_ adopt


# A big deal for Sketchfab?

⇒  from a consumer of data to a producer of data

let's generate glTF data for our 100K downloadable models!


# Transcoding 3D

* scene graph: "standard" objects in 3D so good compatibility
* textures: Sketchfab textures are unpacked, glTF textures are mostly packed
* materials: Sketchfab materials are custom, some data not supported by glTF
* animation: not for launch! (3 weeks ETA)


# Import pipeline overview

load user data ⇒  clean ⇒  normalize ⇒  keep 'generic' data ⇒  optimize/compress for viewer  (→  further optimizations on user edits)


# glTF export pipeline overview

load 'generic' data & Sketchfab materials ⇒  convert materials ⇒  pack textures ⇒  write glTF


# Project steps (processing-wise)

1. support (basic) glTF output <p class="footnote">not me</p>
2. add a pipeline transforming 'generic' data into glTF <p class="footnote">me</p>
3. write a texture packing tool <p class="footnote">me</p>
4. write a material transcoder <p class="footnote">not me</p>
5. test & iterate


# Testing 3D

mostly numerical values + ∞ of cases: it's hard!<br>


# Testing 3D (transcoding)

glTF has a validator ⇒  adding it in the pipeline ensure data readability <br>
\+ write unit test for 'typical' material conversion <br>
\+ write basic packing unit tests <br>

testing transcoding correctness requires comparing renders:<br>
glTF supported as import format so let's test `render(scene) ?= render(import(export(scene)))`


# Comparing renders

* Sketchfab settings are not all supported (orientation, post-processes, etc.)
* image diff not practical (change of scene representation impacts 3D compression, materials not fully exportable)

⇒  built tools to upload and apply 'presets' (a lacking product feature); use product features to ease manual process (tags + original url)


# Issues

* 'generic' data read failures; we failed at ensuring legacy data validaty in time
    * →  added patchers in the pipeline
* image library failing to extract some image channels
    * dependency not updated for 2+ years, hard to catch up


# Lessons

* user data is always messier than anticipated: do batch test to (implicitely) cover as many cases as possible
* corollary: building automated tools is a must
* data traceability is a must too: timestamps not enough & should not be an after-thought
* major dependencies from lively projects should be updated regularly


***

<div>
<center>
Thanks for listening!<br>
Questions?
</center>
</div>

# Timings

<img width="800px" src="gltf-timing.png">


# Launch failure

<img width="800px" src="gltf-release.png">

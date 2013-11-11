---
layout: page
title: oose Innovative Informatik
tagline: Code & Repositories
---
{% include JB/setup %}

## Repository

The maven style repository can be found here: 
[releases](./m2/releases) and [snapshots](./m2/snapshots)

In order to publish locally configure sbt to 

    val snapshots = Some(Resolver.file("Local github (snapshots)",  
      new File(Path.userHome.absolutePath+"/oose.github.io/m2/snapshots")))
    
    val releases =  Some(Resolver.file("Local github (releases)", 
      new File(Path.userHome.absolutePath+"/oose.github.io/m2/releases")))
    
    publishMavenStyle := true
    
    publishTo <<= version { (v: String) =>
      if (v.trim.endsWith("SNAPSHOT"))
        snapshots
      else
        releases
    }

If you just need to configure sbt to resolve one of the repositories add:

    resolvers += "oose (releases)" at "http://oose.github.io/m2/releases"

or

    resolvers += "oose (releases)" at "http://oose.github.io/m2/snapshots"

## Social Coding

Here is our github repository: [oose github](http://github.com/oose)

## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>




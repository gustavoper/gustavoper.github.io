---
layout: default
title: Gustavo Pereira
project-name: Gustavo Pereira
---
{% include header.html %}

<div style="text-align:center">

<a target="_blank" title="My Twitter Account" href="https://twitter.com/{{ site.twitter_username }}"> 
<i class="fab fa-twitter-square fa-2x"></i>
</a>
<a target="_blank" title="My Linkedin Profile" href="https://linkedin.com/in/{{ site.linkedin_username }}">
<i class="fab fa-linkedin fa-2x"></i> 
</a>
<a target="_blank" title="My SpeakerDeck Presentations (Sorry, portuguese only)" href="https://speakerdeck.com/{{ site.speakerdeck_username }}">
<i class="fab fa-speaker-deck fa-2x"></i> 
</a>
</div>




## Blog posts
{% for p in site.posts %}
<li><a href="{{ site.baseurl }}{{ p.url }}">{{ p.title }}</a></li>
{% endfor %}

## About me 

Gustavo Pereira is a Full-stack developer since 2005, using several languages (from ASP.net to Ruby, C# and PHP) and always trying to achieve best practices on his projects (both personal and professional ones). 

He puts a lot of passion on what he does and likes to share his knowledge on communities, talks and mentoring. Also, he believes that everyone has something to share and help the community, regardless of graduation, expertise or point of view.



{% include footer.html %}

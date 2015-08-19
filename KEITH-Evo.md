---
layout: page
title: KEITH Evolution (2015)

<div class="posts">
   {% assign index = true %}
   <!-- This section shows sticky posts at the top o the page -->
   {% if paginator.page == 1 %}
      {% for post in site.categories.sticky %}
         <div class="post">
            <h1 class="post-title">
               <a href="{{ post.url }}">
                  {{ post.title }}
               </a>
            </h1>
            
            <span class="post-date">{{ post.date | date_to_string }} - sticky</span>
            
            {{ post.content }}
            <p>If you haven't already, don't forget to subscribe to our <em><a href="http://eepurl.com/bwu2Cj">mailing list</a></em> for updates on when new blog posts are live!</p>
         </div>
      {% endfor %}
   {% endif %}
   {% for post in paginator.posts %}
      <!-- This next section is used to see if the post is sticky or hidden, in which case it's already been shown -->
      {% assign sticky = false %}
      {% assign hidden = false %}
      {% for cat in post.categories %} <!-- Roll through this pages categories to find if it is sticky -->
         {% if cat == 'sticky' %}
            {% assign sticky = true %}
         {% endif %}
         {% if cat == 'hidden' %}
            {% assign hidden = true %}
         {% endif %}
      {% endfor %}
      {% unless sticky %} <!-- Only show the article if it is NOT sticky -->
         {% unless hidden %} <!-- Also only shows if article is not hidden -->
            <div class="post">
               <h1 class="post-title">
                  <a href="{{ post.url }}">
                     {{ post.title }}
                  </a>
               </h1>
               
               <span class="post-date">{{ post.date | date_to_string }}</span>
               
               {{ post.content }}
               <p>If you haven't already, don't forget to subscribe to our <a href="http://eepurl.com/bwu2Cj">mailing list</a> for updates on when new blog posts are live!</p>
               </div>
         {% endunless %}
      {% endunless %}
   {% endfor %} 
</div>

<div class="pagination">
  {% if paginator.next_page %}
    <a class="pagination-item older" href="{{ site.baseurl }}page{{paginator.next_page}}">Older</a>
  {% else %}
    <span class="pagination-item older">Older</span>
  {% endif %}
  {% if paginator.previous_page %}
    {% if paginator.page == 2 %}
      <a class="pagination-item newer" href="{{ site.baseurl }}">Newer</a>
    {% else %}
      <a class="pagination-item newer" href="{{ site.baseurl }}page{{paginator.previous_page}}">Newer</a>
    {% endif %}
  {% else %}
    <span class="pagination-item newer">Newer</span>
  {% endif %}
</div>
---
layout: default
---
{% capture the_collection %}{{page.collection}}{% endcapture %}
  {% if page.collection %}
    {% assign  document = site[the_collection]  %}
  {% endif %}
{% for links in document  %}
  {% if links.title == page.title %}
    {% unless forloop.first %}
      {% assign prevurl = prev.url %}
    {% endunless %}
    {% unless forloop.last %}
      {% assign next = document[forloop.index] %}
      {% assign nexturl = next.url %}
    {% endunless %}
  {% endif %}
  {% assign prev = links %}
{% endfor %}

<script>
document.body.onkeyup = function(e){
if (e.keyCode == '37') { window.location = '{{prevurl}}'; }
if (e.keyCode == '39') { window.location = '{{nexturl}}'; }
};
</script>

{% if prevurl %}<a href="{{prevurl}}" class="prev">&lt;</a>{% else %}&lt;{% endif %} {{ page.title }}
{% if nexturl %}<a href="{{nexturl}}" class="nxt">&gt;</a>{% else %}&gt;{% endif %}
<br>
{% if page.children %}
Tweets will appear below if you hove over them... You can click them too.
<iframe id='twitframe' border=0 frameborder=0 height=250 width=550
 src="" hidden=true></iframe>{% endif %}

<div class='img'>
	{% if page.children %}
		{% for c in page.children -%}
			{% if c.url -%}
				<a href='{{ c.url }}' title='{{ c.url }}' target='_new' onMouseOver="
						document.getElementById('twitframe').src = 'https://twitframe.com/show?url={{ c.url | uri_escape }}'
						document.getElementById('twitframe').hidden = false
				  ">
					<img class='subimg subimgurl' src='/img/{{ c.id }}.png'>
				</a>
			{%- else -%}
					<img class='subimg' src='/img/{{ c.id }}.png'>
			{%- endif -%}
		{%- endfor %}
	{% else %}
	<img alt='Page {{ page.title }}' src='/img/{{ page.title }}.png'>
	{% endif %}
	{{ content }}
</div>

{% if page.children %}
	You can download the <a href='/img/{{ page.title }}.png'>full image here</a>.<br>
{% endif %}

{% if prevurl %}<a href="{{prevurl}}" class="prev">&lt;</a>{% else %}&lt;{% endif %} {{ page.title }}
{% if nexturl %}<a href="{{nexturl}}" class="nxt">&gt;</a>{% else %}&gt;{% endif %}

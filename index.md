# MCH 2022 is over...

But whatever got sent on the text remains in this archive.

The [@mch2022telex](https://twitter.com) was a Telex connected to twitter during the [MCH 2022](https://mch2022.org) haker kamp in Zeewolde.

This project would not have been possible without:
* [@BigBaldGeek](https://twitter.com/BigBaldGeek) and [@gertkremer](https://twitter.com), who helpt with the creating and debugging the PCBs and PIs,
* [@FablabWuerzburg](https://twitter.com/FablabWuerzburg) who created the initial PiTelex software and PCBs and placed them [on GitHub](https://github.com/fablab-wue/piTelex), and
* [@Seccubus] who put it all together, rewrote the Twitter software and created this site (his [github repo is here](https://github.com/MrSeccubus/piTelex/tree/merged))

Now go and click on a sheet below.

{% for page in site.sheets %}
[![Sheet {{ page.title }}](/img/thumb_{{ page.title }}.png)]({{ page.url }})
{% endfor %}


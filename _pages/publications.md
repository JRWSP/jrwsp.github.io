---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>

*J. Saiphet, S. Suwanna, A. R. R. Carvalho, and A. Chantasri, Time-delayed Quantum Feedback and Incomplete Decoherence Suppression with No-Knowledge Measurement. <u><a href="https://doi.org/10.1103/PhysRevA.103.022208">Phys. Rev. A 103, 022208 (2021)</a>.</u>
    
*J. Saiphet, S. Suwanna, T. Chotibut, and A. Chantasri, Quantum Approximate Optimization and K-means Algorithms for Data Clustering. <u><a href ="https://doi.org/10.1088/1742-6596/1719/1/012100">J. Phys.: Conf. Ser. 1719 012100 (2021)</a>.</u> 
    
*J. Saiphet, A. Chantasri, and S. Suwanna, Effects of Time Delay in No-Knowledge Quantum Feedback Control. <u><a href ="https://doi.org/10.1088/1742-6596/1380/1/012113">{J. Phys.: Conf. Ser. 1380 012113 (2019)</a>.</u>
<!---
{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}
-->
{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}

# My projects over the years

I like when people have a whole big list of all their projects somewhere. I've meant to put one together for a while but haven't ever gotten around to it.

<ul>
{{ it.context.htmlSlugsInDirectory("/projects/").forEach(function(slug){ }}
  <li><a href="{{= slug }}">{{= slug }}</a></li>
{{ }) }}
</ul>

# My projects over the years

I like when people have a whole big list of all their projects somewhere. I've meant to put one together for a while but haven't ever gotten around to it.

{{/* Adapted from: https://ryankubik.com/blog/force-date-time-zone */}}
{{function forceDateToTimeZone(date, timeZone) {
const [isoDate, isoTime] = new Date(date).toISOString().split("T");
return new Date(isoDate + " (" + timeZone + ")")}
}}
{{const currTz = Intl.DateTimeFormat().resolvedOptions().timeZone}}

<ul>
{{ it.context
      .htmlFilesInDirectory("/projects/")
      /* I'm not sure why we pick up _template.eta in this right now, we should filter that out in rk-ssg */
      .filter(file => !!file.transformations.matter)
      .sort((a, b) => forceDateToTimeZone(b.transformations.matter.publishedAt, currTz).getTime() - forceDateToTimeZone(a.transformations.matter.publishedAt, currTz).getTime())
      .forEach(function(file){ 
}}
  <li><a href="{{= file.slug }}">{{= file.transformations.matter.title }}</a> - {{=new Intl.DateTimeFormat("en-US", {year:"numeric",month:"short"}).format(forceDateToTimeZone(file.transformations.matter.publishedAt, currTz))}} - {{= file.transformations.matter.description }}</li>
{{ }) }}
</ul>

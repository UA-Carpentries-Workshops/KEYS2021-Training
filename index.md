---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "University of Arizona"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "us"      # lowercase two-letter ISO country such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the
latitude: "32.231901"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "110.9495000"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "June 8, 2021"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "8:00 am - 12:00 pm"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2021-06-07      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2021-06-11        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Uwe Hilgert & Instructor Team"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["KEYS Crew", "KEYS Staff", "Jonathan King", "Isabella Viney"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["hilgert@bio5.org"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes: http://pad.software-carpentry.org/KEYS2021-Training # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

<h2 id="general">FOUNDATIONAL COMPUTATIONAL SKILLS</h2>

<h3 id="general"><u>General Information</u></h3>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong>
{% if online == "false" %}
  We are committed to making this workshop
  accessible to everybody. The workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Material will be provided in advance of the workshop.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
{% else %}
  We are dedicated to providing a positive and accessible learning environment for all. Please
  notify the instructors in advance of KEYS Training Week if you require any accommodations or if there is
  anything we can do to make the workshops more accessible to you.
</p>
{% endif %}

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<!--
<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>
-->
<!--
{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}
-->
<hr/>
<!--
{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h3 id="code-of-conduct"><u>Code of Conduct</u></h3>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>
-->

{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h3 id="collaborative_notes"><u>Collaborative Notes</u></h3>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}

<h3><u>Workshop Preparation</u></h3>

<p>
  This Google Doc at <a href="https://docs.google.com/document/d/1Pj1igupTrAa04KyEx19OTJVi8j-O5n2aKE7DtUcjcFQ/edit">https://docs.google.com/document/d/1b3c4Um68zARppshBoxQ5uotrOjG0_Vn50VuVo-Wk1z8/edit?usp=sharing</a> holds additional IMPORTANT information on the workshop and how to prepare for it. 
<p>

{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<!--
<h3 id="surveys"><u>Surveys</u></h3>
<p>Please be sure to complete these surveys before and after the workshop.</p>
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
-->
<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<!--
<h3 id="schedule"><u>Schedule</u></h3>

{% if site.carpentry == "swc" %}
{% include swc/schedule.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/schedule.html %}
{% elsif site.carpentry == "pilot" %}
The lesson taught in this workshop is being piloted and a precise schedule is yet to be established. The workshop will include regular breaks. If you would like to know the timing of these breaks in advance, please [contact the workshop organisers](#contact). For a list of lesson sections and estimated timings, [visit the lesson homepage]({{ site.lesson_site }}).
{% comment %}
Edit/replace the text above if you want to include a schedule table.
See the contents of the _includes/custom_schedule.html file for an example of
how one of these schedule tables is constructed.
{% endcomment %}
{% endif %}
-->
<hr/>

<h3 id="syllabus"><u>Syllabus</u></h3>

<div class="row">
  <div class="col-md-6">
    <h3 id="syllabus-shell">The Command Shell</h3>
    The command shell (a.k.a. UNIX Shell, Bash Shell, Shell) is a power tool that allows computer users to do complex things with just a few keystrokes. Contrary to graphical user interfaces (GUI) it allows users to direct the computer from a more foundational level, using written commands. Even what happens when you click on items in GUIs is directed by written commands. Working in the 'Shell' helps users combine existing programs in new ways and automate repetitive tasks so they aren’t typing the same things over and over again. Shell proficiency is fundamental to using a wide range of other powerful tools and computing resources, including “high-performance computing” supercomputers.<br>
    <br>
    Using the Bash Shell the workshop will introduce these concepts and procedures:<br>
    <br>
    <ul>
      <li>Files and Directories</li>
      <li>History and Tab Completion</li>
      <li>Pipes and Redirection</li>
      <li>Looping Over Files</li>
      <li>Creating and Running Shell Scripts</li>
    </ul> 
    <u>Additional Resources:</u>
      <ul>
		  <li><a href="{{site.swc_pages}}/shell-novice/reference">Shell Quick Reference</a></li>
		  <li><a href="{{site.swc_pages}}/shell-novice">Shell Lessons</a></li>
      <li><a href="http://explainshell.com/" target="_blank"><em>Explain Shell</em> (Parses shell commands and shows docs about the command)</a></li>
		  <li><a href="http://www.shellcheck.net/" target="_blank"><em>ShellCheck</em> (Identifies bugs in shell scripts)</a></li>
		  <li><a href="http://man.he.net/" target="_blank"><em>Linux Man Pages Online</em> (Same content as command line man/help pages)</a></li>
	  </ul>
  </div>
  <div class="col-md-6">
    <h3 id="syllabus-git">Version Control with Git</h3>
    Version control is the lab notebook of the digital world: it’s what professionals use to keep track of what they’ve done and to collaborate with other people. Every large software development project relies on it, and most programmers use it for their small jobs as well. And it isn’t just for software: books, papers, small data sets, and anything that changes over time or might need to be shared can and should be stored in a version control system.<br>
    <br>
  Using git (on your local computer) and GitHub (in the cloud), the workshop will introduce these version control concepts and procedures:<br>
    <br>
    <ul>
      <li>Creating and initializing a Repository: <code>init</code></li>
      <li>Recording Changes to Files: <code>add</code>, <code>commit</code>, ...</li>
      <li>Viewing Changes: <code>status</code>, ...</li>
      <li>Working on the Web: <code>clone</code>, <code>pull</code>, <code>push</code>, ...</li>
    </ul>
    <u>Additional Resources:</u>
	  <ul>
		  <li><a href="{{site.swc_pages}}/git-novice/reference">Git Quick Reference</a></li>
		  <li><a href="{{site.swc_pages}}/git-novice">Git Lessons</a></li>
      <li><a href="https://git-scm.com/book/en/v2/Git-in-Other-Environments-Git-in-Bash" target="_blank"><i>Mac/Linux:</i> Integrating Git into your shell prompt</a></li>
		  <li><a href="https://github.com/magicmonty/bash-git-prompt" target="_blank">An informative and fancy bash prompt for Git users</a></li>
		  <li><a href="https://education.github.com/pack" target="_blank">Unlimited <em>private</em> repositories for free on Github, <i>while you are a student</i></a></li>
		  <li><a href="https://git-annex.branchable.com/" target="_blank">Git for Archiving Data</a></li>
	  </ul>
  </div>
</div>


<h3 id="setup"><u>Setup</u></h3>

<p>
{% comment %}
  To participate in a
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to software as described below.
  In addition, you will need an up-to-date web browser. We recommend Firefox and/or Safari. Chrome may work, too. MS Edge or Internet Explorer, maybe...
{% endcomment %}
</p>

<p>
  To participate in the workshop,
  you will need access to software as described below.
  In addition, you will need an up-to-date web browser.
Prior to your scheduled Zoom Practice meeting, install the software below on your computer, following the instructions provided for your operating system (Windows, Mac, Unix).
</p>

<p>
 You can find a list of common issues that may occur during installation at 
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
  </p>

<p>
  We will try to address any remaining issues in the Zoom Practice meetings – so, if you experience unsurmountable hurdles, take good notes about what you did and what went wrong. (Screenshots would be helpful for trouble-shooting!) You can also send an email to hilgert@bio5.org with any computational issues you may encounter and we'll try to get you help as quickly as possible.
</p>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}

{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

{% if site.carpentry == "swc" %}
{% include swc/setup.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/setup.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/setup.html %}
{% elsif site.carpentry == "pilot" %}
Please check the "Setup" page of
[the lesson site]({{ site.lesson_site }}) for instructions to follow
to obtain the software and data you will need to follow the lesson.
{% endif %}



<h3 id="vpn">Very Private Network (VPN)</h3>

<p>
The UA Virtual Private Network (VPN) provides a secure connection from your home computer, laptop, or mobile device to the UA's network. It is also a valuable security tool when you are on an unsecured wireless network (e.g., coffee shops, airports).
</p>


<h4>Install UA VPN on your computer</h4>

<p>
  <ul>
    <li>Go to the University of Arizona’s Information Technology (UITS) site at <a href="https://it.arizona.edu/">https://it.arizona.edu/</a>.</li>
    <li>Click on the ‘UA Virtual Private Network (VPN)’ Tile.</li>
    <li>Click on the ‘Support, How-To’s & Info’ tab.</li>
    <li>In the ‘Installation’ section select the ‘UA VPN Download and Installation Instructions’ for your Operating System.</li>
    <li>Follow the instructions to install VPN on your computer.</li>
    <li>In the ‘Prerequisite and Training Links’ section, open ‘Connecting the UA VPN Basics for Mac and PC’ and watch the video applicable to your operating system. Then, follow the instructions to connect your machine to the UA VPN.</li>
  </ul>
Again, we will try to address any issues in the Zoom Practice meetings – so, if you experience unsurmountable hurdles, take good notes about what you did and what went wrong. (Screenshots would be helpful for trouble-shooting!) You can also send an email to hilgert@bio5.org with any comutational issues you may encounter and we'll try to get you help as quickly as possible.
</p>

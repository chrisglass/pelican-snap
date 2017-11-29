Snap packaging for your pelican blog
=====================================

This project aims to provide a self-contained packaging recipe to deploy and
host your blog in production using the snapcraft pacakging system.


Building the snap
-----------------

Simple as pie! Copy the snap/ subfolder and the Caddyfile to your existing
pelican project, and run "snapcraft" from pelican's top-level directory.

You'll need to change two things:

- Put your website's desired FQDN in the Caddyfile
- Change the snap name to something you like and makes sense to you. Keeping
  the same name will prevent you from pushing the snap to the store.


Testing locally
---------------

With your site's FQDN as "localhost:8080", simply install the created snap to
your local machine with:

  snap install --dangerous mysnap.snap

Note: "--dangerous" is needed since your snap is unsigned (the store usually
signs snaps to ensure they are not tampered with).


Deploying to production
-----------------------
 
Login to the snap store with "snapcraft login", then push you new snap with
"snapcraft push".

The snap, once pushed, needs to be published to a "channel" (edge, beta,
candidate, or stable). Feel free to use any mix of those for your own needs.

  snapcraft publish <snap name> <snap revision> <channel>

On the target machine, login to the snap store with:

  snap login

Then install your snap with:

  snap install mysnap

There you go! Your pelican blog will be kept up to date. Simply push to the
store form your development machine and it will auto deploy :)


Improvements
------------

This is just a first draft of my blog server, and there's a few areas I'd like
to see this project improve:

 - Build caddy from source instead of downloading it.
 - Checksum downloads

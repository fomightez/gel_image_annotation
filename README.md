[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/gel_image_annotation/master?filepath=index.ipynb)

# gel_image_annotation

Click a `launch binder` badge anywhere on this page to begin.

---

Seeing if [this](https://twitter.com/Steve_Harborne/status/1133064277445627904) can be binderized?

Simple script for automatically annotating SDS-PAGE images 

## Going beyond the built-in demo gel

To upload your own data, click on the Jupyter logo in the upper left to access a typical file browser that allows file uploads.

Then change `gel_file` assignment to specify your gel name.

(Drag-and-drop is possible with the the JupyterLab interface; however, you'd probably want to switch back after uploading your gel as currently plotting is more reliable in the classic notebook interface. See [here](https://github.com/binder-examples/jupyterlab#start-jupyterlab-after-you-start-your-binder) about switching interfaces.)

----

## Technical details

*Many thanks to mathieuboudreau for working out using Plotly's orca with the MyBinder.org service.* This section details that as it explains why this repo needs a Dockerfile to be binderized for full-featured abilities.  
Everything worked as in [the original demo]((https://twitter.com/Steve_Harborne/status/1133064277445627904)) with simply a repo with a `requirments.txt` file (link to that version is [here](https://github.com/fomightez/gel_image_annotation/tree/4421855f2b3a7d1ea53008456b4393371ec3cb10). However, I wanted to add automatic static image generation of the nice interactive plotly graphs to the workflow as that would automate things further for use of the generated content elsewhere, such as in a lab notebook. It looked like all from [here](https://plot.ly/python/static-image-export/) that all I'd need to do is add plot-orca using conda. I tried it first in an active session and it said it wasn't valid orca installation and listed what normally would be helpful installation directions if I wasn't inside a Binder session. I thought perhaps I just needed to switch to using conda to install, and so I removed the `requirements.txt` file I was using to direct dependency isntallation and tried including `plotly-orca` among the dependencies list in `environment.yml`. However, that resulted in the following:

```bash
Solving environment: ...working... failed

ResolvePackageNotFound:
  - plotly-orca
```

Fixed that build problem by adding `plotly` under the channels in `environment.yml`. So now the build ran (working `environment.yml` [here[(https://github.com/fomightez/gel_image_annotation/tree/24bf618b43ef1451128868f4d3591efa9549cbdc), but when I tried running the `pio.write_image()` code from [here](https://plot.ly/python/static-image-export/), I was still getting the note about it not being valid plotly orca installation.
Searching 'environment.yml plotly-orca' the title 'Error to locate Orca - Python - Plotly Forum' caught me eye and lead me to [here](https://community.plot.ly/t/error-to-locate-orca/16729/5) where the post was exactly what I had seen when I tried using conda inside a Binder session to install it for prototyping. Fortunately, down below that happened to list mathieuboudreau's comment about also struggling with this. Luckily I clicked on [the link](https://github.com/plotly/orca/issues/150#issuecomment-482585518) in his comment and looked because although the comment didn't reference Binder-based use, that is exactly what he was trying to work out as referenced in [the post below](https://github.com/plotly/orca/issues/150#issuecomment-482585956) the initially linked one and was indeed later able to work it out [here](https://github.com/plotly/orca/issues/150#issuecomment-483484860). It is apparent from [here](https://github.com/plotly/orca) it is complex and very thankful that it was already worked out.
Actually later when I got the build working from `environment.yml`, it says the following at the bottom of the large segment that starts with saying there wasn't a valid orca installtion when trying to the `pio.write_image()` code :
>"[Return code: 127]
/srv/conda/envs/notebook/lib/orca_app/orca: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
Note: When used on Linux, orca requires an X11 display server, but none was
detected. Please install X11, or configure your system with Xvfb. See
the orca README (https://github.com/plotly/orca) for instructions on using
orca with Xvfb."

That is in line with what mathieuboudreau ended up addressing.

----

Click the `launch binder` badge below to begin:

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/gel_image_annotation/master?filepath=index.ipynb)


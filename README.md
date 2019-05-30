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

*Many thanks to mathieuboudreau for working out using Plotly's orca with the MyBinder.org service.* This details that as it explains why this repo needs a Dockerfile to be binderized for full-featured abilities.  
Everything worked as in [the original demo]((https://twitter.com/Steve_Harborne/status/1133064277445627904)) with simply a repo with a `requirments.txt` file. However, I wanted to add automatic static image generation of the nice interactive plotly graphs to the workflow as that would automate things further for use of the generated content elsewhere, such as in a lab notebook. It looked like all from [here](https://plot.ly/python/static-image-export/) that all I'd need to do is add plot-orca using conda. I tried it first in a session and it said it wasn't valid orca and listed what normally would be helpful installation directions if I wasn't inside a Binder session. I thought perhaps I just needed to switch to using conda to install, and so I removed the `requirements.txt` file I was using to direct dependency isntallation and tried including `plotly-orca` among the dependencies list in `environment.yml`. However, that resulted in the following:

```bash
Solving environment: ...working... failed

ResolvePackageNotFound:
  - plotly-orca
```

So I checked the notes that came up when searching '' and it looks like all I should need to add was `plotly-orca`. (However,  I even tried `plotly plotly-orca` as a depenency line in the `enviroment.yml` line and that didn't work either.)
Searching 'environment.yml plotly-orca' the title 'Error to locate Orca - Python - Plotly Forum' caught me eye and lead me to [here](https://community.plot.ly/t/error-to-locate-orca/16729/5) where the post was exactly what I had seen when I tried using conda inside a Binder session to install it for prototyping. Fortunately, down below that happened to list mathieuboudreau's comment about also struggling with this. Luckily I clicked on [the link](https://github.com/plotly/orca/issues/150#issuecomment-482585518 27) in his comment and looked because although the comment didn't reference Binder-based use, that is exactly what he was trying to work out as referenced in [the post below](https://github.com/plotly/orca/issues/150#issuecomment-482585956) the initially linked one and was indeed later able to work it out [here](https://github.com/plotly/orca/issues/150#issuecomment-483484860).

----

Click the `launch binder` badge below to begin:

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/gel_image_annotation/master?filepath=index.ipynb)


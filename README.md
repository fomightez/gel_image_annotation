[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/gel_image_annotation/master?urlpath=lab/tree/index.ipynb)

# gel_image_annotation

Click a `launch binder` badge anywhere on this page to begin.

---

Seeing if [this](https://twitter.com/Steve_Harborne/status/1133064277445627904) can be binderized?

Simple script for automatically annotating SDS-PAGE images 



## Use your own data

Go beyond the built-in demonstration by adding your own gel image.  
To upload your own data, drag and drop into the file browser panel on the left.  
Then change `gel_file` assignment to specify your gel name.

(If you prefer the classic notebook interface, you can change the end of the url from `lab` to `tree` to switch to classic. See [here](https://github.com/binder-examples/jupyterlab#start-jupyterlab-after-you-start-your-binder) for more about that.)


## A note on the interactive plots generated

The interactive plots made by the demonstration will not render as output when you first launch the active notebook via MyBinder.org. You must run the cells in the notebook again, and then they will show up in the output cell area. This is a security feature to block abuse.

The interactive versions of the plots do not get rendered when viewing the static notebooks in Github; however, **if you view the static notebook page via nbviewer [here](https://github.com/fomightez/gel_image_annotation/blob/master/index.ipynb), the interactive Plotly plots will render and be interactive**.


----

## Technical details

*Many thanks to mathieuboudreau for working out using Plotly's orca with the MyBinder.org service.* See [here](https://github.com/fomightez/orca-plotly-binderized/blob/d437e56032188ee0c1de24c379ed40b5e49eaf34/README.md) for more on that. Keeping the Dockerfile here for now, but as a hidden file, since it may be useful for future efforts by myself or others. Especially since quite different approach for the last steps dealing with getting orca ready. In particular, I couldn't find a way to work with `usr/bin` in postBuild (or terminal) without permissions problems even though it seems to work for the Dockerfile. 

----

Click the `launch binder` badge below to begin:

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fomightez/gel_image_annotation/master?urlpath=lab/tree/index.ipynb)


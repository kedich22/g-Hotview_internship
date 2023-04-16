:bangbang: **TO BE UPDATED!** :bangbang:

:bangbang: Change the link to binder later :bangbang:
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/kedich22/Thermal-Sentinel/main?labpath=Burnscar_forfires_new.ipynb)

# G-Hotview
### Tool for visualization of lava flows/fires/thermal activity on the land surface, using Google Earth Engine   

**VERSION 1.0.0**  

<ins>Author</ins>: Andrei KEDICH - KULeuven (Belgium)   
<ins>Supervision</ins>: Benoît SMETS - Royal Museum for Central Africa / Vrije Universiteit Brussel (Belgium)   

### Description 
The tool is capable of making various visualizations of thermal anomalies on the surface. Now it is working with Sentinel-2 imagery and allows based on SWIR bands to detect 'high-temperature' areas. These areas are highlighted, whereas the background is a usual multispectral image. Hot areas have a 3-level gradation which helps to distinguish the most heated parts. The background also could be modified, and the series of predefined band combinations are available, furthermore, two combinations could be blended with different opacity. The tool is applicable for the detection of volcanic activity and visualization of forest fires. The tool compiles a mosaic of images of the same date in case the selected area is large and not covered by one image.

### How to use it?
1. There are two ways to use the tool: **on your local server** and through the **binder deployed application**. This option is recommended, you always could inspect the code in the Jupyter Notebook or on GitHub.
If you still want to use it on your local computer, you will find inside the file `requirements.txt` the necessary Python packages with their versions which you should install in your python environment. The `runtime.txt` contains the used version of Python.  
2. In the Binder-deployed application all packages are already installed and all data could be retrieved on the web. 

### The tutorial
1. Click on the binder badge at the top of the README file or [change the link](https://mybinder.org/v2/gh/kedich22/Thermal-Sentinel/main?labpath=Test%20burnscar.ipynb) to load the Jupyter Notebook. It might take some time to load the page (up to several minutes) due to the rendering process.
2. During the first access to the application you should authorize yourself through the Jupyter Notebook.
3. After the page is loaded if you are accessing the app for the first time you should authenticate yourself with Earth Engine to provide the access to this Notebook. For this purpose, your account should be already activated through the Google Earth Engine platform. 
Run the first chunk of code &rarr; follow the link &rarr; click "Generate Token" &rarr; Choose your Google account &rarr There will be a notification that Google has not verified this app, click `Continue` &rarr grant access by ticking both boxes &rarr; copy the provided authorization code into the field in Jupyter Notebook and press enter &rarr; Congratulation! You are successfully authorized and could use the app!

![auth](https://user-images.githubusercontent.com/70434411/183929591-2a1d9d6f-62eb-422f-b38f-63e3e444988e.png)
![auth_token](https://user-images.githubusercontent.com/70434411/183929684-a87aa178-820b-46c1-9011-e2248fdc84e9.png)

4. After clicking on the viola rendering icon and wait until the application is rendered. After it is finally deployed and ready to use!
![voila](https://user-images.githubusercontent.com/70434411/183935707-ced0268c-56fb-4f51-b69b-fefe47df5190.png)

The following screen will be opened:
![application](https://user-images.githubusercontent.com/70434411/186253616-70241bf0-02c5-438c-819f-9721d2dbb185.png)

1. `Select the area of interest` Firstly you need to specify the area of interest (AOI) by indicating the coordinates and buffer area, or after ticking the box `User-defined AOI` you could draw manually the area on the map. It is not recommended to make an area very large to prevent not covered areas by satellite images.
2. 'Select the date range` After the area is specified, please indicate the period of interest.
3. Click the button `List images` to list below all the existing dates with available Sentinel-2 imagery. Also, you could `Clear fields` just by clicking the button. All parameters will be reversed to default values. After the area has been chosen manually you could delete the drawn polygon by clicking on the bin at the left map bar to prevent overlapping the output. That should be done after `List images` is clicked.
4. If everything is selected properly, after a while the list with dates should appear below the `List images` button. You should select the date of interest and put the number in the field below `Select the image` and click `Submit`. After that, the phrase `The image is selected` will appear below. Now you successfully selected the image to visualize.
---
5. The next step is visualization. The parameters are adjusted via the menu below the map.
You should specify 2 band combinations and their opacity in the first step. `Select the band combination` from the dropdown menu and set an opacity that will be associated with this layer. Two layers will be blended for visualization, so the background will mix two band combinations. If you want to show only one band combination just set the opacity slider at 0 for one of the layers.
Options for visualization (by Pierre Markuse, [click here](https://pierre-markuse.net/2018/04/30/visualizing-wildfires-burn-scars-sentinel-hub-eo-browser/)
- *Natural Colors* - A natural color band combination
- *Enhanced Natural Colors* - Natural colors with NIR mixed in, to get more bright green color for vegetation
- *Natural NIR SWIR Mix* - A mix of natural and NIR/SWIR bands
- *NIR SWIR Colors 1* - A classic NIR/SWIR combination
- *NIR SWIR Colors 2* - Similar to the first one, colors are more subtle with better smoke penetration
- *NIR SWIR Colors 3* - Very red and punchy combination
- *NIR SWIR Colors 4* - Good atmospheric penetration, visible burn scars, and highlighted hot spots
- *False Color* - Classic NIR false color image
- *Nat False Color* - NIR false color image with a natural-color-like appearance
- *Vegetation* - Useful to show healthy vegetation
- *Pan Band* - Monochrome B08 image

`Stretch min` and `Stretch max` is responsible for adjusting the lightness of the resulting image. 

With `Saturation` you could adjust the vividness of the image. If set to 0, the monochrome version will have resulted.

`Fire sensitivity` defines the sensitivity of hot spot detection. If you want to visualize more hotspot areas increase the number (but be aware of false positives). 1 is default and tested to work rather "well".

The next line allows the user to `adjust` manually the RGB visualization of the image. It's a "cheat" option if you want to change the appearance of the image. You could add by defining positive values or subtract by defining negative ones.

You also could highlight burn scars by modifying the backdrop (desaturation and darkness). To set up the visualization change the parameter `Highlight` from 0. 

In the section `Burnscar highlight` adjust the values:
- `Thsd low` Burnscar detection threshold low
- `Thsd high` Burnscar detection threshold high
- `Desat back` Desaturates the backdrop
- `Darken back` Darkens the backdrop

Carefully inspect and adapt these parameters for every image.

In addition in this version, the export possibility is implemented.

By `cropping and visualization` the choice of how to present the visualization on the map could be done: to clip to the polygon of interest or to show the full image.

You could export the visualized image on your computer. The exported image should have a size of less than 32 MB. You could adjust the scale for the export in case you are interested in exporting a large area. The image is exported in tiff format, exported image contains three bands.
Firstly, select the path where to save the file. The image cannot be directly saved on your computer. Firstly, it will appear in the environment, where all application files are stored. You could keep the default provided path: after clicking `Change`. 
To export the image after the path has been chosen click `Export image`. 
The image will appear on the left panel: you have to left-click on it and at this step choose where to save it on your local computer:
![image](https://user-images.githubusercontent.com/70434411/195396364-aa5e0299-d02e-4fce-bd8a-071099a8e5c0.png)


### To-do list for future improvements
- [ ] Add similar enhanced RGB composition for Landsat collections (at least L8 and L9)
- [ ] Circumvent the size limit of image export
- [ ] Fix the moment with a visualization of the AOI polygon
- [ ] Add the information while selecting images about the cloud cover in the AOI
- [ ] Transfer the application to another deployment platform (from Binder)
- [ ] Add the option to visualize the downloaded outside polygon (in JSON)

# QGIS Lesson
This repository contains contents for teaching SoS crews how to set up and interact with the open source, lightweight, and efficient geographic information system (GIS) QGIS.

# Background:

A **Geographic Information System** (GIS) is a system that is used for displaying, analyzing, and in part distributing data which have geographic attributes. As of the last few decades, GIS are nearly synonymous with computers, although they predate them. Several different GIS softwares exist. The most popular are generally: R, Python, GrassGIS, SagaGIS, QGIS, and ArcGIS - which is being superseded by ArcPro. The 'Arc' line of products are produced by the company ESRI, and are very popular in multiple tiers of government in the United States (e.g. city, county, state, and federal). The other Geographic Information Systems are very popular in academic settings (Universities, or the Research Divisions of Government Agencies like the USGS), and worldwide. Most of these earlier systems are all Open-source, which means individuals and organization are able to contribute code to improve their performance for certain applications. Most of these other GIS software compose a ecosystem, where some rely on others. 

QGIS is arguably the most common GIS in the open source ecosystem with a **Graphical User Interface**. Many appreciate that it is 'light', i.e. it does not take up enormous computer resources which allows it to load very fast and be responsive to users panning and toggling around the map. We will use QGIS as a supplement to the ESRI Geoplatform product. This is simply due to the fact that we have generated a ton of data which I do not have access to add back to the BLM servers! Such is government. 


## Installation 

![QGIS](./images/QGIS_logo.resized.png)

Normally, I would not ask you to install GIS software on your computer; but due to being so 'light' QGIS is the exception. QGIS can be downloaded from [here](https://www.qgis.org/en/site/forusers/download.html), for all major operating systems: Windows, Mac, and several flavors of Linux. 

**Windows** users are **unlikely** to need the OSGeo4W installer; although it is a small efficient piece of software which does not take up much room. It might be safer to download than be sorry if you want to keep using this in the not so near future!

**Mac** "macOS High Sierra (10.13) or newer is required. QGIS is not yet notarized as required by macOS Catalina (10.15) security rules. On first launch, please control-click on the icon and choose Open from the context menu, after which a confirmation dialog is shown and you need to click the Open button."

**Linux** please refer to [this](https://www.qgis.org/en/site/forusers/alldownloads.html#linux) additional page on installation 

Great that is about it! It is a quick install! Once downloaded navigate to the program, and if necessary feel free to pin it to your start bar or something so you don't forget about it!

![Plugins](./images/Manage-install_Plugins.resized.png)

Part of why QGIS is so light it that it does not come with many interfaces to the other open-source software which some folks may use. You download these using **Plugins**. We will install two Plugins. Open QGIS, if it is not already, and navigate to the **Plugins** tab on the top bar and **Plugins >> Manage and Install Plugins**. From this pop-up screen use the **Search** bar at top to search for **QuickMapServices**. We will use this Plugin to display base maps. Now let's add one more Plugin, using the **Search** bar search for **Load Them All**. We will use this service to import many files quickly. 

![Search Plugins](./images/Install-QuickMapServics.resized.png)

That's it! We now have an operational GIS on our hands!

## Gather your project specific data

You all *should* have gotten an invite to some data sitting on Google Drive; if you don't have this email me. The drive should have a **zip** file; this is a formatting for compressing data which makes it easier to send. Please download this file. Once downloaded (or if you have the change to before), please drag this to your project specific folder for Seeds of Success this year. A good place to put this folder, if you do not already have it, is in your **Documents**. From this location you can unzip the folder. On most software systems you can right click the file, and select an option like **decompress**. Great this folder contains a ton of supplemental project data. Most importantly it contains **Species Distribution Models** (SDMs), we generated species distribution models for all but two of the Great Basin Ecoregion Target Species. We skipped these two because you will have no difficulty finding them! If you would like to learn more about SDM's please visit [this lecture](https://rpubs.com/steppe27/1006352) I recently gave. This folder also contains ccurrence data for the species, a subset of the records here are identical to those on the tablet, but we have several times more! We used this large dataset of occurrences to create our Species Distribution Models. 

The only other data sets we have which are not present on the tablet are some data on **Drought**, **Invasives annual grasses**. If you are interested in learning more about Ecological Drought check out this section of a big ol' government report [here](https://github.com/sagesteppe/UFO_drought/blob/main/scripts/Section_6.pdf), and some more good info on invasive species from the same report can be found [here](https://github.com/sagesteppe/UFO_noxious_weeds/blob/main/scripts/Section_10.pdf). Cool! So while these data are very similar to what is on the tablet, we have a few more tricks up our sleeves as you will see. 

Now we are also going to download some data that contains pre-specified aesthetics for our project. Let's be honest, this should style automatically, but I hardly ever use GUI GIS software, so I just don't know how to do that! Normally it sucks to suck, but I am just going to make you all have to map the aesthetics over yourselves!! So ya!

Download the zip file 'qml_styles' from [here](https://github.com/sagesteppe/QGIS_Lesson/blob/main/data/qml_styles.zip), and click the little 'download' button. Place this in the same directory as above, and remember to unzip it. 

![Download from Github](./images/Download-QML.resized.png)

## Create a QGIS Project

Many GIS operate on the sense of a **project** a big related set of objects for each thing you are working on. We will create a **Project** for your SoS-Planning. The easy way to do this is to **close** QGIS (if it is open), and reopen it, and click on **'New Project'**, if you already have a project than click **Project >> New**. You have now entered a new Project, now let's save this at the **root** of your Geodata folder. 


![Save at root](./images/SaveAs-location.resized.png)



```
.
└── Geodata
    ├── Admin
    │   ├── Boundaries
    │   └── Surface
    ├── Disturb
    │   ├── Fire
    │   └── Invasive
    ├── Drought
    ├── Roads
    ├── Species
    │   ├── Historic_SoS
    │   ├── Occurrences
    │   └── SDM
    └── STZ
```

If you are unfamiliar with the **root**, it is the base of something! So if we look in the geodata folder, and think of it as the soil, we have 'Admin', 'Disturb', 'Drought', 'Roads', 'Species' and 'STZ' all rooted in it! So let's save your project in 'Geodata'

```
.
└── Geodata
    ├── Admin
    │   ├── Boundaries
    │   └── Surface
    ├── Disturb
    │   ├── Fire
    │   └── Invasive
    ├── Drought
    ├── Roads
    ├── Species
    │   ├── Historic_SoS
    │   ├── Occurrences
    │   └── SDM
    └── STZ
    |__ SoS-Planning.qgz # this is now rooted in the geodata directory!!!
```

## Import data to QGIS

We are now ready to import data to our QGIS project, it looks a little sad without any content doesn't it? First let's add in a basemap so that we are oriented. We will use the **QuickMapServices** Plugin which we just installed. This Plugin is generally located on the right end of your toolbar. It looks like a globe with binoculars. 

![Plug in Locations](./images/Plugins.resized.png)

Once you have located it, we will use it to import the standard basemap which it ships with, **OSM >> OSM Standard**. This imports a freely available base map tile service. Cool!

![Import basemap](./images/Import_OSM.resized.png)

Now we will import our two big sets of data, our **Species Distribution Models**, and the **occurrence** data we used to create them. These are most complex imports, so we will do them before we have a chance to mess up the project and need to revert back!


https://user-images.githubusercontent.com/62572330/231841827-b28abb00-aff3-42be-8813-43a2a6c8ddb1.mp4


We will utilize our other plugin **Load them all**, load them all looks like a folder with a green arrow coming down from it, like the folder is being opened. So click on that! Now make sure that the leftmost option, **Vector**, is toggled. Vector data are what sometimes are called 'shapefiles', shapefiles are a specific type of vector data, but not all vector data are shapefiles!!! If you are unfamiliar with geographic data formats, check out a lecture on the topic [here](). We will now navigate to the to the folder containing your geodata **'Geodata/Species/Occurrences'**, and select the file format **ESRI Shapefile (*.shp)** there should be somewhere from around 30-50 files showing in that location. Now at the very bottom right of this window select 'Load Data'. 

Ok now the occurrence data are imported! We are going to turn these into a **Group**, a set of data which we can manage simultaneously. To create a **Group** right click on the top-most record scroll down to the very last record, and right click again while holding shift. With any luck every record will now be selected! Now on this menu select **'Create Group'**, and let's name this group **Occurrence**. 


https://user-images.githubusercontent.com/62572330/231843627-46e51410-4609-4417-bc49-59254283174f.mp4


We will style these data now quickly. Because well, they are uninformative, and data which are uninformative are not worth much. We will load some pre-loading styles I came up with using [Colorbrewer](https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3), hopefully they look okay. Right click on the top-most record, it is probably *Achnatherum lemmonii*, and select **'Properties'** and then **Style >> Load Style**, now navigate to the **qml_styles** directory, and select the **Occurrences.qml** file. Now **Apply** and **OK** this selection. 

You might not even be able to see what we did there... Let's turn of all of the records in our **Occurrence** group really quick. Right click on the group, and select **Uncheck and all it's children**, now just check the little cell next to the record you added the stylings to, maybe *Achnatherum lemmonii*, OK see what we did? If not you might need to **Right Click >> Zoom to layer**; now you should be focused on these records. Keep in mind for you field offices there could only be 1 record! 

Now, let's apply this styling to every species in our Occurrence group. Click on the name of the top-most record and **Style >> Copy Style >> Symbology**, and now **right click >> Paste style**. If all goes to plan, each species will have the same symbology!

But wait... why? Why should each species be the same color! This makes no sense!!! So, the way we came up with this stuff is using a lot of code and approaches from a technique called **'Data Science'**, I'm sure you have heard these term, there is a lot of hype around it. One of the fundamental rules of data science is **don't get overwhelmed by data**. So I seriously, suggest, that you look through each species one at a time! Yep... more on this later. You will also notice that their are several sets of symbology within this layer; the older a record the lighter the color; you will also notice you can deselect old records? Why, because many of those old populations may no longer exist; we want to use current data. 


Now if that all went to plan, let's **save** our project! Now we can add in the **SDMs**

### Add in Species Distribution Models



### Add in remaining variables

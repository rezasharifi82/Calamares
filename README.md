# Calamares
A mechanism to develop a GUI based installer for any kind of linux distros.    
I've recently faced with a project that aimed to develop a new distribution of linux. In order to develop the installation wizard, I've used [Calamares](https://calamares.io/)        

which is an extraordinary tool to develop that kind of installers. In this repo, I'm trying to share whatever I've learned during this project.(It's absolutely not going to be the best document for learning the Calamares, but I'm almmost think It can resolve your problem If you are a beginner user)

------
With special thanks to:
- Parch Linux([website](https://parchlinux.com/download),[GitHub](https://github.com/parchlinux))
- DT Os([Website](https://distro.tube/dtos/),[YouTube](https://www.youtube.com/watch?v=mgqWBFHFdAc),[Video](https://www.youtube.com/watch?v=peTmPXuoW-0))
- This Guy :) ([Video](https://www.youtube.com/watch?v=L91iAquEopc))
- 
And If you want to link to [EzArcher](https://www.youtube.com/watch?v=G6a2TpyrIhY) or [ArchIso](https://www.youtube.com/watch?v=peTmPXuoW-0)
> I would be grateful if you can provide me some expert tips or other resources to learn Calamares :)

-------




### 1. Calamares Installation
Ok, In this step you should install calamares. There are several way to install calamares.     
The easiset way is:
```
sudo apt-get install calamares
```
But If you don't want this way, feel free to clone the official (repo)[https://github.com/calamares/calamares].    

### 2. Get the Output
If you've installed the calamares using apt, you can easily run ``` calamares``` command in your terminal and see the output.
### 3. Configuration
Now It's Show time :)    
The sophisticated part of calamares is the subtle configuration protocol which can handle everything.    
There are couple of ways to handle out the configuration:
- Using .ui files and Qt :
  I don't know too much about this one. but you can edit .ui files and use cmake or qmake to compile those files. It doesn't make sense for me because I've not had a good experience with Cpp and Qt.(So I am grateful if you can share your experience towards this subject)
- Using .qml file :
  This one is absolutely easier. You can change this qml file by texteditor or using Qt. There is nothing special with that.


<details>

  <summary>My Current File Structure</summary>
  <pre><font color="#12488B"><b>.</b></font>
├── <font color="#12488B"><b>branding</b></font>
│   └── <font color="#12488B"><b>fumarch</b></font>
│       ├── <font color="#A347BA"><b>banner.png</b></font>
│       ├── banner.png.license
│       ├── branding.desc
│       ├── <font color="#A347BA"><b>calamares_background.svg</b></font>
│       ├── <font color="#A347BA"><b>calamares_bg_image.png</b></font>
│       ├── <font color="#A347BA"><b>calamares_install_image.png</b></font>
│       ├── <font color="#A347BA"><b>calamares_product_icon.png</b></font>
│       ├── <font color="#A347BA"><b>calamares_product_logo.png</b></font>
│       ├── calamares-sidebar.qml
│       ├── <font color="#A347BA"><b>calamares_welcome_logo (another copy).svg</b></font>
│       ├── <font color="#A347BA"><b>calamares_welcome_logo (copy).png</b></font>
│       ├── <font color="#A347BA"><b>calamares_welcome_logo.png</b></font>
│       ├── calamares_welcome_logo.png2
│       ├── FadeBehavior.qml
│       ├── finishedq.qml
│       ├── i18n.qml
│       ├── ItemSection.qml
│       ├── keyboardq.qml
│       ├── <font color="#12488B"><b>lang</b></font>
│       │   ├── calamares-default_ar.qm
│       │   ├── calamares-default_en.qm
│       │   ├── calamares-default_eo.qm
│       │   ├── calamares-default_fr.qm
│       │   └── calamares-default_nl.qm
│       ├── <font color="#A347BA"><b>languages.png</b></font>
│       ├── languages.png.license
│       ├── ListItemDelegate.qml
│       ├── ListViewTemplate.qml
│       ├── localeq.qml
│       ├── Map.qml
│       ├── Offline_orig.qml
│       ├── Offline.qml
│       ├── ResponsiveBase.qml
│       ├── show.qml
│       ├── <font color="#A347BA"><b>squid.png</b></font>
│       ├── squid.png.license
│       ├── stylesheet.qss
│       ├── summaryq.qml
│       ├── usersq.qml
│       ├── ViewStepsBar.qml
│       ├── <font color="#A347BA"><b>wallpaper.png</b></font>
│       └── welcomeq.qml
├── <font color="#26A269"><b>launch.sh</b></font>
├── <font color="#12488B"><b>modules</b></font>
│   ├── initcpio.conf
│   ├── localeq.conf
│   ├── mount.conf
│   ├── packages.conf
│   ├── partition.conf
│   ├── removeuser.conf
│   ├── shellprocess-alg-mkinitcpio.conf
│   ├── shellprocess-remove-livecd.conf
│   ├── unpackfs.conf
│   ├── users.conf
│   ├── usersq.conf
│   ├── welcome.conf
│   └── welcomeq.conf
├── <font color="#A347BA"><b>parchinstall.png</b></font>
├── <font color="#12488B"><b>qml</b></font>
│   └── <font color="#12488B"><b>calamares</b></font>
│       └── <font color="#12488B"><b>slideshow</b></font>
│           ├── BackButton.qml
│           ├── ForwardButton.qml
│           ├── NavButton.qml
│           ├── Presentation.qml
│           ├── qmldir
│           ├── qmldir.license
│           ├── SlideCounter.qml
│           └── Slide.qml
└── settings.conf

</pre>
</details>    


**branding**: This one is important part of your journey. You should clarify the details of your linux. (e.g. name,version and ...)    
**modules**: This is a folder that has every .conf files. You can configure your files by editting these sensational parts of project.
**qml**: This folder is related to slideshow qml files which you don't need it(at least at the beginning parts of the procedure :))
**setting.conf**: absolutely important part.


### 4. Branding
Branding folder consists of several important things. Remember, the branding folder name should be same as component name in ``` branding.desc``` file and also it should changed in ```setting.conf``` file.
<details>
  <summary>
    Branding File Structure
  </summary>
  <pre><font color="#12488B"><b>.</b></font>
└── <font color="#12488B"><b>fumarch</b></font>
    ├── <font color="#A347BA"><b>banner.png</b></font>
    ├── banner.png.license
    ├── branding.desc
    ├── <font color="#A347BA"><b>calamares_background.svg</b></font>
    ├── <font color="#A347BA"><b>calamares_bg_image.png</b></font>
    ├── <font color="#A347BA"><b>calamares_install_image.png</b></font>
    ├── <font color="#A347BA"><b>calamares_product_icon.png</b></font>
    ├── <font color="#A347BA"><b>calamares_product_logo.png</b></font>
    ├── calamares-sidebar.qml
    ├── <font color="#A347BA"><b>calamares_welcome_logo (another copy).svg</b></font>
    ├── <font color="#A347BA"><b>calamares_welcome_logo (copy).png</b></font>
    ├── <font color="#A347BA"><b>calamares_welcome_logo.png</b></font>
    ├── calamares_welcome_logo.png2
    ├── FadeBehavior.qml
    ├── finishedq.qml
    ├── i18n.qml
    ├── ItemSection.qml
    ├── keyboardq.qml
    ├── <font color="#12488B"><b>lang</b></font>
    │   ├── calamares-default_ar.qm
    │   ├── calamares-default_en.qm
    │   ├── calamares-default_eo.qm
    │   ├── calamares-default_fr.qm
    │   └── calamares-default_nl.qm
    ├── <font color="#A347BA"><b>languages.png</b></font>
    ├── languages.png.license
    ├── ListItemDelegate.qml
    ├── ListViewTemplate.qml
    ├── localeq.qml
    ├── Map.qml
    ├── Offline_orig.qml
    ├── Offline.qml
    ├── ResponsiveBase.qml
    ├── show.qml
    ├── <font color="#A347BA"><b>squid.png</b></font>
    ├── squid.png.license
    ├── stylesheet.qss
    ├── summaryq.qml
    ├── usersq.qml
    ├── ViewStepsBar.qml
    ├── <font color="#A347BA"><b>wallpaper.png</b></font>
    └── welcomeq.qml
</pre>
</details>

**fumarch** is the name of my branding.    
Those ```.qml``` files configure the graphical part of each page(It's easy to understand and you can even edit it by texteditor:))      
The important file of this folder is ```branding.desc```.(Feel free to read it carefully :))



### 5.module
module is another important folder. You can configure the back part of you qml files which you've edited in the branding folder. I actually mean you can write down what those files should do in order to preform as best as it can be.(See some of them and you'll realize what i mean)


---------


### Screen Shots of My Project:


| ![Welcome Page](https://github.com/rezasharifi82/Calamares/blob/main/shot/1.png?raw=true) | ![Region](https://github.com/rezasharifi82/Calamares/blob/main/shot/2.png?raw=true) |
|--|--|
| ![Keyboard](https://github.com/rezasharifi82/Calamares/blob/main/shot/3.png?raw=true) | ![Partitions](https://github.com/rezasharifi82/Calamares/blob/main/shot/4.png?raw=true) |

|![User2](https://github.com/rezasharifi82/Calamares/blob/main/shot/5.png?raw=true)|
|:--:|
|![User2](https://github.com/rezasharifi82/Calamares/blob/main/shot/6.png?raw=true)|













--------     


## This project has designed for OS course at Ferdowsi University of Mashhad- fall 2023





# ensembleLibrary
Modified version Weka ensembleLibrary package

This is a officially provided Weka package.

I had run into a bug some time ago and created this repository with a work around.

I was going to look into ensembles again and decided to take a closer look at this. 
It again had issues, this time related to current Weka package manager ClassLoader changes.

I fixed for that and decided as long as I was updating I would make some other changes.

I changed the default CV folds from 1 to 5. 1 apparently means no CV but instead uses some similar process based on the original
Caruana paper. I found normal CV seemed to give better performance. For the high overhead already involved I chose 5 folds instead of 10.
You get a dialog with a incorrect error message if you try to change the number of folds for an existing model. I'm still thinking about
trying to change that somehow.

I changed the default directory from $user.home to $user.home/wekafiles/packagesStore. Although you can change this to something else
yourself I didn't like how it started piling up directories into your home directory by default. I may look at the saved model files to 
see if there are any other possibilities there.

Builds started failing for JUnit failures in the Weka classifier regression test. A reference 'ref' file appeared to be included. I 
deleted that, it was recreated and the test started working.

About it on this for now.
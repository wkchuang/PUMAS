PUMAS
======
Parameterization for Unified Microphysics Across Scales

This repository contains the open source code for most versions of the Morrison-Gettleman (MG) microphysics as well as the most recent releases called the Parameterization for Unified Microphysics Across Scales, or PUMAS.

 Checking out and running PUMAS
================================
 Running with an PUMASDevelopment/CAM or ESCOMP/CAM branch
-----------------------------------
The code in this repository is not sufficient for completing a simulation on its own. To run within the Community Atmosphere Model (CAM), you will need to check out a branch of CAM.

These are instructions for checking out a branch of CAM and pointing to a differnt branch of PUMAS then what you recieve from a checked out CAM branch or tag.

Clone a repository that contains a CAM source tree. ::

git clone https://github.com/PUMASDevelopment/CAM.git Github_CAM_PUMAS_Clone

This will create a directory Github_CAM_PUMAS_Clone in your current working directory.

(optional) Go into the newly created directory and checkout a modified branch. ::

cd Github_CAM_PUMAS_Clone git checkout cam_pumas_development

From the root of the CAM clone, run the script manage_externals/checkout_externals. ::

./manage_externals/checkout_externals

The checkout_externals script will populate the cam directory with the relevant versions of each of the components along with the CIME infrastructure code.

At this point you have all of the code needed for CAM with the PUMAS microphysics available.

To make changes to PUMAS, first create a branch for your work in the ESCOMP/PUMAS Github repository by clicking on the "Branch:master" drop down box on the middle left part of the main page (just below the purble line), and type the name of your new branch into the "Find or create a branch..." text area.

For new branch names, it is generally a good idea to put your Github name first, and then the goal of the branch after a slash. So, a name for a branch to fix conservation bugs might be "katetc/graupel_consv_fix". Hit enter, and your new branch is now shown in Github.

The second step for making changes in PUMAS is to update the source code in the pumas subdirectory to work with this branch. For various reasons, we are not going to use manage_externals for this. Just cd into the pumas subdirectory and checkout your remote branch. ::

cd Github_CAM_PUMAS_Clone/src/physics/pumas
git fetch
git checkout katetc/graupel_consv_fix
Once you have your own branch checked out, you can make local changes to the code. When it's time to commit them, you will need to ::

git add filename.F90 git commit -m "Commit message" git push

This will push your changes to your remote branch. When you have finished with ALL of your changes (can be multiple commits), then it will be time to merge your branch changes back to the master branch in the ESCOMP/PUMAS repo. You can do this by clicking "Pull requests" in the PUMAS github repo main page, and then the big green "New Pull Request" button. In the gray bar, for the "compare" pull down, click and select your branch. This will show all of the differences between your branch and the master PUMAS branch. If you are happy with these changes, click the green "Create pull request" button again, and that will take you to a pull request form. Fill out a description of your changes and issue the pull request. This request will be reviewed by a software engineer and then merged into the main branch. Your development branch can then be deleted, and you can start a new one for the next issue.


References
Gettelman, A., H. Morrison, K. Thayer‐Calder, and C. M. Zarzycki. 2019. The Impact of Rimed Ice Hydrometeors on Global and Regional Climate. Journal of Advances in Modeling Earth Systems. https://doi.org/10.1029/2018MS001488.

Gettelman, A. and H. Morrison, Advanced Two-Moment Microphysics for Global Models. Part I: Off line tests and comparisons with other schemes. J. Climate, 28, 1268-1287. doi: 10.1175/JCLI-D-14-00102.1, 2015.

Gettelman, A., H. Morrison, S. Santos, P. Bogenschutz and P. H. Caldwell. Advanced Two-Moment Microphysics for Global Models. Part II: Global model solutions and Aerosol-Cloud Interactions. J. Climate, 28, 1288-1307. doi:10.1175/JCLI-D-14-00103.1 , 2015.

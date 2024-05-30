# hcppipeline-ICAfix error run in ubuntu 20.04
##to sovle the problem when running hcppipeline ICA_fix
registration of standard space masks
 extract features
No valid labelling file specified
Thu May 30 20:03:43 CST 2024:hcp_fix_multi_run: Done running FIX
Could not find a supported file with prefix "task-rest_dir-RL_LR_hp0.ica/filtered_func_data_clean"
Thu May 30 20:03:43 CST 2024:hcp_fix_multi_run: ERROR: '/opt/fsl/bin/immv' command failed with return code: 1

===> ERROR: Command returned with nonzero exit code
---------------------------------------------------
         script: hcp_fix_multi_run
stopped at line: 793
           call: $FSLDIR/bin/immv ${concatfmrihp}.ica/filtered_func_data_clean ${concatfmrihp}_clean
  expanded call: /opt/fsl/bin/immv task-rest_dir-RL_LR_hp0.ica/filtered_func_data_clean task-rest_dir-RL_LR_hp0_clean
      exit code: 1
---------------------------------------------------

===> Aborting execution!

##That means you didn't install R and R's dependence packages:
See the README file in the fix folder:
tart R and run the following command
install.packages("devtools")

On Ubuntu:

sudo apt-get install r-base r-cran-devtools

Then on either Linux:

require(devtools)
chooseCRANmirror()
install_version("kernlab", version="0.9-24")
install_version("ROCR", version="1.0-7")
install_version("class", version="7.3-14")
install_version("mvtnorm", version="1.0.8")
install_version("multcomp", version="1.4-8")
install_version("coin", version="1.2.2")
install_version("party", version="1.0-25")
install_version("e1071", version="1.6-7")
install_version("randomForest", version="4.6-12")

###however when running install_version("mvtnorm", version="1.0.8"), you may face the following error:
Downloading package from url: https://cloud.r-project.org/src/contrib/Archive/mvtnorm/mvtnorm_1.0-8.tar.gz
Installing package into ‘/home/ubuntu/R/x86_64-pc-linux-gnu-library/3.6’
(as ‘lib’ is unspecified)
* installing *source* package ‘mvtnorm’ ...
** package ‘mvtnorm’ successfully unpacked and MD5 sums checked
** using staged installation
** libs
gcc -std=gnu99 -I"/usr/share/R/include" -DNDEBUG     -fpic  -g -O2 -fdebug-prefix-map=/build/r-base-jbaK_j/r-base-3.6.3=. -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2 -g  -c C_FORTRAN_interface.c -o C_FORTRAN_interface.o
gcc -std=gnu99 -I"/usr/share/R/include" -DNDEBUG     -fpic  -g -O2 -fdebug-prefix-map=/build/r-base-jbaK_j/r-base-3.6.3=. -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2 -g  -c miwa.c -o miwa.o
gfortran -fno-optimize-sibling-calls  -fpic  -g -O2 -fdebug-prefix-map=/build/r-base-jbaK_j/r-base-3.6.3=. -fstack-protector-strong  -c mvt.f -o mvt.o
/bin/bash: gfortran: command not found
make: *** [/usr/lib/R/etc/Makeconf:191: mvt.o] Error 127
ERROR: compilation failed for package ‘mvtnorm’
* removing ‘/home/ubuntu/R/x86_64-pc-linux-gnu-library/3.6/mvtnorm’
Warning message:
In i.p(...) :
  installation of package ‘/tmp/RtmpmhLSpl/remotes235ff92174530e/mvtnorm’ had non-zero exit status


###That means you lack gfortran
Then you can solve it by entering the following code in the terminal:
sudo apt-get install aptitude
sudo aptitude install gfortran

After you can install these package in R:
install_version("mvtnorm", version="1.0.8")
install_version("multcomp", version="1.4-8")
install_version("coin", version="1.2.2")
install_version("party", version="1.0-25")
install_version("e1071", version="1.6-7")
install_version("randomForest", version="4.6-12")



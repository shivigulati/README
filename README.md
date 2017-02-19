# README
Stage 5 Udacity IPND


How to access and use the files in this github repository:

If you dont have them already, download VirtualBox (made by Oracle) and Vagrant(made by HashiCorp).
Place the Tournament folder (located in this GitHub repo) in an easily available spot.
Use a Command Line to navigate to the Tournament folder.
Type "vagrant up". This could take a while if you are just setting up Vagrant for the first time.
Type "vagrant ssh" to log into Vagrant.
Type "cd /vagrant" to navigate to shared files.
To run the tournament tests, type "python tournament_test.py". The output will be shown in your Command Line.
To run only the SQL file, navigate back to vagrant (ctrl + z generally does the trick) and type "psql". Then type "\i tournament.sql".

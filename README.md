# obspyDMT_worldwide_and_sahke_waveforms
Use obspyDMT to plot waveforms from worldwide networks and include a raspberry shake waveform.

obspyDMT is a command line tool for retrieving, processing and management of seismological 
datasets in a fully automatic way.

These instructions show how a Raspberry shake waveform can be combined with waveforms from
stations in the worldwide network e.g. IRIS

Install obspyDMT (see https://github.com/kasra-hosseini/obspyDMT)

The steps below are related to the Solomon Islands 7.9 event on 22nd Jan 2017 (change it
for the event you need)

Extract the waveforms into the directory "solomon", using the terminal command:

obspyDMT --datapath solomon --min_date 2017-01-22 --max_date 2017-01-23 --min_mag 7.5 
--data_source IRIS --net "II" --loc "00" --cha "BHZ"

Edit the file "availability.txt" in a sub-directory "info" beneath "solomon".
Insert a line at the beginning of this file and put you Raspberry Shake details in e.g.

AM,RD4A6,00,BHZ,55.76,12.4,23.0,5.3,RASP,AM_RD4A6_00_SHZ

where 55.76,12.4, 23.0 is lat, long, elevation of your Raspberry Shake

Find your mseed file for the day of the event e.g. AM.RD4A6.00.SHZ.D.2017.022

Then copy this file to the sub-directory "raw" beneath "solomon" and rename it in a 
similar format like this: AM.RD4A6.00.BHZ

Then run the terminal command to plot the waveforms:

obspyDMT --datapath solomon --local --plot_waveform


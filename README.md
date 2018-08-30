# MilliQan

Most files have option at the beginning to choose which run to plot, and a reasonably sensible naming system, some may need updating to include option of plotting Physics runs 

Terms used:
"muon cut" requires events of a certain height (normally set to 100) in 'slabs' 18, 20, 28 & 21
 TCut('MaxIf$(height,chan==18)>100&&MaxIf$(height,chan==21)>100&&MaxIf$(height,chan==20)>100&&MaxIf$(height,chan==28)>100')
 
 "time cut" puts a restriction on the time taken for the muon to travel through the detector (in some of the older files the inequality may be the wrong way round). To SELECT muons it should be 'MinIf$(time,chan==21&&height>'+str(cutlevel) +')-MinIf$(time,chan==18&&height>' + str(cutlevel)+')>-20'
 

Files:

"background_fit" - plots a scaled 'height' graph of the background noise from Run 1345 against the Physics runs (or run 843). Hashed parts include a power law fit to the background part, can easily change to plot nPE but will need to change to alternative histogram binning option. 

"background_fit_total" _ same as above but adds up each individual channel to find total background. Currently set to plot nPE.

"bar_coincidence_rates" - includes 3 options. Currently set to zoom in on the x values 0-200
1. to plot the rates (integrates 'max-height' graph) in each channel
2. to plot predicted coincidence rates in each channel, takes two rate (in Hz) vs threshold histograms, multiplies them together, and then scales by 1280x10-9 s.  The result is a plot of coincidence rate (Hz) vs threshold for those two channels.
3. to plot the actual coincidence rates. Requires events above a certain height in a specified channel, and then plots the rates in another one 

"bar_efficiency" - produces plots of efficiency for each of the bar channels. Assumes a straight path through the detector, requires two of the other bars 'enroute' to have a signal in above a certain height (set to 100). 

"bar_rates_cumulative" - creates plots of the average rate for each of the different PMTs

"bar_rates_overlay" - similar to above, but instead of plotting the average rate all channels corresponding to a different PMT are plotted on same graph

"correlation_plot" - plots a scatter graph of the minimum time_module_calibrated values for two channels. Includes an option to apply a 'time cut', already includes a 'muon cut'. 

"cosmic_ray_coincidence_rates" - similar to option 3 of "bar_coincidence_rates", but includes a cut to veto cosmic rays

"cosmic_rays" - produces max-height graphs/ rate graphs for the bar channels, applying cuts which veto possible events caused by cosmic rays. Can choose between plotting height/rate and between plotting individual bars or plots for different PMTs. Can't currently plot 'height' for different PMTs though, that needs to be fixed

"efficiency_cumulative" - plots an average efficiency graph for each of the PMT tubes

"efficiency_overlay" - creates graphs of the bar effiencies for each of the different PMT channels, overlays each of the bars onto one graph per PMT

"roc_all_options" - produces ROC plots using Run 1345 for the background rates, and a choice of run for the efficiency calculation. Includes options to apply a cut to veto cosmic rays and to plot individual bars or PMTs

"skimming_events" - takes a file/files and reduces it by appling cuts. Use when graphs take a long time to load etc. 

"splashes" -  Requires pulses going straight through the detector, ie through channels 18-0-20-6-28-2-21, the specific route is noted by 'titlechan' or 'passing through chan' on the title of the graph produced. Requiring this path, heights(/nPE) in surrounding channels will be plotted to look at the 'splashes produced' in other bars.

"splashes_total" - takes all 6 "spalshes" plots from above and adds them together. Then fits two power laws, one background prediction with the parameter p1 set using a fit from "background_fit", one taking that power law and adding another one. 



Older code (less useful, mainly just for practice):

Will need to update if you want to plot anything other than Run 843

"muon cut" - produces plot of variable with a cut to identify muons
"height overlays with muon cut" - draws haights in separate bar channels on same graph with a muon cut applied
"individual channels" - produces plots of a variable in each individual channel
"muon cut with time restriction" - produces plot of variable with a cut to identify muons and a restriction on the time taken to travel through the detector


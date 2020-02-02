# -*- coding: utf-8 -*-
"""
Created on Fri Dec  6 13:52:43 2019
 
@author: labuser, Daniel Escalante
"""
#if excel file data.csv is opened while this is running, it will stop running.
 
import csv
 
import requests
 
from datetime import datetime
from time import sleep
 
 
CSV_FILE = "data.csv"
DIALECT = "excel"
FETCH_URL = "http://192.168.5.35/index.html" #data is uploaded here via a virtual machine, see ionwiki
 
# Fetches values over 60 seconds, averages them, and returns a list of the averages
def getSixtySecondAvg():
  fetched_values = {0: [], 1: [], 2: [], 3: []}
  start_time = datetime.now()
  while((datetime.now() - start_time).total_seconds() < 60): # loop until a minute passes, then return
	func_start_time = datetime.now()
	r = requests.get("http://192.168.5.35/index.html") #requests.get fetches the html code,
	s = r.text
    fetched_values[0].append(float(s[1046:1050])) # add the fetched values to the list of those values this minute
    fetched_values[1].append(float(s[1302:1306])) # the value we want is encoded in characters 1302-1306 of the html
    fetched_values[2].append(float(s[1346:1350]))
    fetched_values[3].append(float(s[1556:1560]))
    time_elapsed_during_call = (datetime.now() - func_start_time).total_seconds()
	if time_elapsed_during_call > 0: # sleep for one second, minus the time it took to compute this
  	sleep(1 - time_elapsed_during_call)
 
  ret = []
  for _, all_fetched_values in fetched_values.items(): # find the avg of each list of stored values...
    ret.append(sum(all_fetched_values)/len(all_fetched_values))
  return ret # ...and return them
	
 
# Main function
if __name__ == "__main__":
  while True:
	sixty_second_avg = getSixtySecondAvg()
    sixty_second_avg.insert(0, int(datetime.now().strftime("%y%m%d%H%M%S"))) # add date at beginning of the line, encoded as yymmddhhmmss
	with open(CSV_FILE, "a+", newline="") as f:
  	writer = csv.writer(f, dialect=DIALECT)
      writer.writerow(sixty_second_avg) # write the averages, plus the date, to the csv

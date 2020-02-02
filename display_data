import matplotlib.pyplot as plt
import csv
 
a = []
b = []
c = []
d = []
e = []
 
 
ti = 191206062000.0 #initial time of chart, here time is econded as yymmddhhmmss
tf = 191214174621.0 #final time of chart
 
with open('data.csv','r') as csvfile: #data.csv is file created by getSixySecondAvg.py
	plots = csv.reader(csvfile, delimiter=',') #reads the file
	for row in plots:
    	x = float(row[0]) #row 0 is the date column
    	if x>= ti and x<= tf:
            a.append(x)  #adds values of x that satisfies conditions above to a
            b.append(float(row[1])) #adds values of column 2 of csv file to b
            c.append(float(row[2]))
            d.append(float(row[3]))
            e.append(float(row[4]))
 
plt.plot(a,b) # plots time vs table temperature..
plt.xlabel('Time (m)')
plt.ylabel('Temp (f)')
plt.title('Table_Temp')
 
plt.show() #displays plot
 
plt.plot(a,c)
plt.xlabel('Time (m)')
plt.ylabel('Temp (f)')
plt.title('Table_Humidity')
 
plt.show()
 
plt.plot(a,d)
plt.xlabel('Time (m)')
plt.ylabel('Temp (f)')
plt.title('Lab_Ambient_Temp')
 
plt.show()
 
plt.plot(a,e)
plt.xlabel('Time (m)')
plt.ylabel('Relative Humidity')
plt.title('Input_Air_Temp')
 
plt.show() #long straight line means that over a certain time, data was not collected...
#...perheaps someone opened the csv file, stopping getSixtySecondAvg.py

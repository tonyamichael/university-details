# university-details
Calculating mean and median of student enrollment and tuition of different universities each with three information school name, enrollment, and tuition.
list = [["Califonia Institute of Technology", 2175, 37704], 
["Havard", 19627, 39849], 
["Massachusetts Institute of Technology", 10566, 40732],
["Princeton", 7802, 37000],
["Rive", 5879, 35551],
["Stanford", 19535, 40569],
["Yale", 11701, 40500]]

a = [0,0,0,0,0,0,0]
d = [0,0,0,0,0,0,0]


def enrollment_stats(list):	
	return list[1],list[2]
	
tot_tut =0
tot_enr = 0

def mean(list):
	i = 0
	global tot_enr
	global tot_tut
	for i in range(7):
		result = enrollment_stats(list[i])
		tot_tut += result[1]
		tot_enr += result[0]

	return tot_enr/7,tot_tut/7
	
def median(list):
	
	sum = 0
	sum2 = 0
	k=0
	m = 0
	a[0] = list[0][1]
	d[0] = list[0][2]
	for i in range(1,7,1):
		b = list[i][1]
		c = list[i][2]
		for j in range(i):
			if(b<a[j]):
				temp=b
				b = a[j]
				a[j] = temp
			if(c<d[j]):
				temp=c
				c = d[j]
				d[j] = temp			
		a[i] = b
		d[i] = c
	
	for i in range(7):
		if(sum < tot_enr/2):
			sum = sum + a[i]
			k = i
		if(sum2 < tot_tut/2):
			sum2 = sum2 + d[i]
			m = i

	return k,m


result = mean(list)
med = median(list)

print("Total Students: ", tot_enr)
print("Total Tuition: $",tot_tut)
print("Students mean: ", format(result[0], ".2f"))
print("Students median: ", a[med[0]])
print("Tuition mean: ", format(result[1], ".2f"))
print("Tuition median: $",d[med[1]])

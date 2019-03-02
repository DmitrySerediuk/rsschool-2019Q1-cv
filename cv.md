# Resume: full stack developer
## 1. 	Name:
Dmitry Serediuk<br/>
## 2. 	Contacts:
- Email: [k0sm0s@tut.by](mailto:k0sm0s@tut.by)<br/>
- Phone: +375295715440<br/>

## 3. Summary:
My target is learn new technologies in practice, work on complex projects and study from experienced colleagues.<br/>
## 4. Skill:
OOP, PHP, Python, MYSQL, JS, phantomjs, jquery, git, Yii, Bash, Linux<br/>
## 5. Code example:
```python
#!/usr/bin/python
import subprocess
import datetime

"""
	Check file zone and getting url with current zones
	@param String 	lastUrl  	Last updated url
	@param List	zones  	List of zones for getting data
	@param String	resultDir  	Patch for output data
	@param Dict	fileZoneHandles  	Dictionary with handles opened output files
"""

class chekingFilesZone:
	"""
	Init setting.
		@return void
	"""
	def __init__(self,settings,fileIn):
		self.zones = settings['zones']
		self.resultDir = settings['resultDir']
		self.fileMassOpened(self.zones)
		self.fileIn = fileIn
		self.lastUrl = ""
		
	"""
    	Mass open output files
			@param List listZones List of zones for checking in input files
			@return void
	"""
	def fileMassOpened(self,listZones):
		self.fileZoneHandles = {}
		for zone in listZones:
			self.fileZoneHandles[zone] = open(self.resultDir+zone+".out","a")

	"""
		Open handle output zone file
			@param String zone Zone for open output file
			@return void
	"""		
	def fileOpenByZone(self,zone):
		if zone not in self.fileZoneHandles:
			self.fileZoneHandles[zone] = open(self.resultDir+zone+".out","a")
		
	"""
		Mass close output file zone
			@return void
	"""		
	def fileMassClose(self):
		for key in self.fileZoneHandles:
			self.fileZoneHandles[key].close()

	"""
		Parse input file and writing all urls into output files
			@return void
	"""
	def parseFileInAllZones(self):
		fileIn = open(self.fileIn, 'r')

		for line in fileIn:	
			urlTmp = line.split(')')[0]
			
			if self.lastUrl != urlTmp:
			self.lastUrl = urlTmp
			listPartUrl = urlTmp.split(',')		
			zone = listPartUrl[0]
			
			url = ".".join(listPartUrl[::-1])	

			self.fileOpenByZone(zone)
			self.fileZoneHandles[zone].write(url+"\n")
			
			
		self.fileMassClose()
		fileIn.close()
```

## 6. Experience:
#### 2007-2009: Freelance
[https://www.fl.ru/users/k0sm0s/](https://www.fl.ru/users/k0sm0s/)<br/>
Improving and creating small sites.<br/>
Tecnology: PHP, MYSQL, CSS, HTML<br/><br/>

#### 2009-2015: MFA and MFS
Mass create sites for MFA and MFS. Automatic creation sites with used public CMS: wordpress, Shop-Script, OpenCart.<br/>
Tecnology: PHP, MYSQL, Smarty, CSS, HTML<br/><br/>

#### 2009-2019: System administration
System administration >16 servers. Support uptime 24/7 work, config LAMP, VPN, update software, antiDDOS(iptables, fail2ban), backup. <br/>
Tecnology: CentOS, Debian, apache, MYSQL, BIND, python, cron, fail2ban, iptables, vnstat, rsync, wget, bash<br/><br/>

#### 2011-2011: Sites and parameters monitoring(Diploma):
Basic functionality of [domaintools.com](domaintools.com). Daily monitoring > 150 000 000 domains and >10 parameters for each domains : whois, DNS, IP, TCY, PR, index, title, server answer, cms, keywords etc. <br/>
Tecnology: CentOS, mysql, PHP, multithreading, cron, curl, wget, raid<br/><br/>

#### 2011-2012 and 2017-2019 Mining cryptocurrency
Creating farms based on GPU. Build, configure, optimize and support 24x7 performance. Use mining pools API to track statistics.<br/>
Tecnology: Ethash, Bitcoin, php, mysql<br/><br/>

#### 2012-2014: Forex. Trade, investment:
Forex trading. Testing various strategies, writing small helpers in mql5.<br/>
Tecnology: mql5<br/><br/>

#### 2013-2015: Creating an analog [web.archive.org](web.archive.org).
Creating a robot for indexing ru sites. ~4 000 000 sites occupied ~ 60 Tb of information in the archive.<br/>
Tecnology: CentOS, mysql, PHP, JS, multithreading, cron, curl, wget, raid, rsync<br/><br/>

#### 2015-2019: Domaing (.RU).
Interception of released domain names in the zone RU. Creating software for analysis, selection and registration of domain names.<br/>
Tecnology: CentOS, mysql, PHP, Python, JS, JQuery, multithreading, cron, curl.<br/><br/>

#### 2016-2016: Screenshot service.
Create full-page screenshots of sites.<br/>
Tecnology: CentOS, mysql, PHP, phantomJS, multithreading, cron<br/>

#### 2018-2019: Learning python
Self study python. <br/>
Tecnology: python<br/><br/>

#### 2018-2019: Domayning (.CO.UK)
Updating and adaptation of software to intercept .CO.UK domain name. Creating a universal software that is quickly configured to any domain zone.<br/>
Tecnology: CentOS, mysql, PHP, Python, JQuery, multithreading, cron, curl.<br/><br/>

#### 2018-2019: Creating a tool to get the file zone of any domain zone.
Software based on the work of the dictionary allows you to collect at the moment> 70% of active domain names in any domain zone.<br/>
Tecnology: CentOS, bash, PHP, Python, mysql, cron, curl<br/><br/>

#### 2019-2019: Small projects on Arduino
Automated temperature control system in a private house.<br/>
Tecnology: Arduino, php, mysql<br/><br/>

## 7. Education:
- 2006-2011: 	Belarusian State University of Informatics and Radioelectronics.
- 2011-2014: 	Streamline: from Elemetary to Intermidiate level courses.
- 2018-2019: 	[https://www.hackerrank.com/k0sm0s](https://www.hackerrank.com/k0sm0s)
	
## 8. English level:
Intermediate.<br/>
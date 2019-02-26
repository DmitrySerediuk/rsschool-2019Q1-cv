# Resume:
1. 	Name:
		Dmitry Serediuk
2. 	Contacts:
		Email: k0sm0s@tut.by
		Phone: +375295715440
	
3. Summary:
		My target is learn new technologies in practice, work on complex projects and study from experienced colleagues.
4. Skill: 
		OOP, PHP, Python, MYSQL, JS, phantomjs, jquery, git, Yii, Bash, Linux  
5. Code example:
    ```python
		#!/usr/bin/python

		import subprocess
		import datetime

		"""
			check file zone and getting url whith current zones
				@param String 	lastUrl  	Last updated url
				@param List		zones  		List of zones for getting data
				@param String	resultDir  	String of zones for getting data
				@param Dict		fileZoneHandles  	Dictionary whith opened file zone result
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
				Mass open file output file zone
					@param List listZones List of zones for checking in input files
					@return void
			"""
			def fileMassOpened(self,listZones):
				self.fileZoneHandles = {}
				for zone in listZones:
					self.fileZoneHandles[zone] = open(self.resultDir+zone+".out","a")

			"""
				Mass open file output file zone
					@param List listZones List of zones for checking in input files
					@return void
			"""			
			def fileOpenByZone(self,zone):
				if zone not in self.fileZoneHandles:
					self.fileZoneHandles[zone] = open(self.resultDir+zone+".out","a")
			
			"""
				Mass close file output file zone
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
			

		"""
			Main class for getting urls by commoncrawl files
				@param Dict settingTread  		Dictionary whith setting for tread chekingFilesZone class
				@param Dict	settingMain  		Dictionary whith setting for current class
		"""
		class checkingAllFiles:

			"""
				Init setting.
					@return void
			"""		
			def __init__(self,settingMain,settingTread):
				self.settingTread = settingTread
				self.settingMain = settingMain
				
			"""
				Print debug messages if DEBUG enable
					@return void
			"""
			def printLog(self,msg):
				if DEBUG: print(datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")+" | "+msg)
				
			"""
				Main function parsing files from commoncrawl. Download by server. Unpack it and getting urls by unzipped files.
					@return void
			"""
			def runParsingFiles(self):
				for numFile in range(0,self.settingMain['countFiles']):
					
					fileName = self.settingMain['baseFilename']+str(numFile).zfill(5)
					cmdRm = "rm -rf "+self.settingMain['resultDir']+"*"
					subprocess.call(cmdRm, shell=True)
					self.printLog("Clean download dir done..."+cmdRm)
					
					fileIn = self.settingMain['resultDir']+fileName			
					urlDownload = self.settingMain['baseUrlDownload'].replace('[filename]',fileName)
					cmdWget = "wget -O "+fileIn+".gz "+urlDownload
					subprocess.call(cmdWget, shell=True)
					self.printLog("getting "+urlDownload+" done..."+cmdWget)
					
					
					cmdGunzip = "gunzip "+fileIn+".gz"
					subprocess.call(cmdGunzip, shell=True)
					self.printLog("Unzip "+fileName+" done..."+cmdGunzip)
					
					tread =	chekingFilesZone(self.settingTread, fileIn)
					tread.parseFileInAllZones()
					self.printLog(str(numFile)+"|"+str(settingMain['countFiles'])+"Parsing fileIn done\n\n")
					
					
			
		zones = []
		settingTread = {	'zones':zones,
							'resultDir': '/root/run/zones/aw/out/'}

		settingMain = {	'baseUrlDownload':'https://commoncrawl.s3.amazonaws.com/cc-index/collections/CC-MAIN-2019-04/indexes/[filename].gz',
						'baseFilename':'cdx-',
						'countFiles':299,
						'resultDir':'/root/run/zones/aw/in/'}	

		DEBUG = False	

		parsing = checkingAllFiles(settingMain,settingTread)
		parsing.runParsingFiles()
	```

6. Experience:
		2007-2009. 
		Freelance
		https://www.fl.ru/users/k0sm0s/
		Improving and creating small sites.
		Tecnology: PHP, MYSQL, CSS, HTML

		2009-2015.
		MFA and MFS
		Mass create sites for MFA and MFS(>6000 sites and >4 000 000 views per a month). Automatic creation sites with used public CMS: wordpress, Shop-Script, OpenCart.
		Tecnology: PHP, MYSQL, Smarty, CSS, HTML

		2009-2019.
		System administration
		System administration >16 servers. Support uptime 24/7 work, config LAMP, VPN, update software, antiDDOS(iptables, fail2ban), backup. 
		Tecnology: CentOS, Debian, apache, MYSQL, BIND, python, cron, fail2ban, iptables, vnstat, rsync, wget, bash

		2011-2011.
		Sites and parameters monitoring(Diploma):
		Basic functionality of domaintools.com. Daily monitoring > 150 000 000 domains and >10 parameters for each domains : whois, DNS, IP, TCY, PR, index, title, server answer, cms, keywords etc.  Engineering big database who increase every day in 100 Gb
		Tecnology: CentOS, mysql, PHP, multithreading, cron, curl, wget, raid

		2011-2012
		2017-2019
		Mining cryptocurrency
		Creating farms based on GPU. Build, configure, optimize and support 24x7 performance. Use mining pools API to track statistics.
		Tecnology: Ethash, Bitcoin, php, mysql

		2012-2014
		Forex. Trade, investment:
		Forex trading. Testing various strategies, writing small helpers in mql5.
		Tecnology: mql5

		2013-2015
		Creating an analog web.archive.org.
		Creating a robot for indexing ru sites. Was used 1 local server, ~4 000 000 sites occupied ~ 60 Tb of information in the archive, indexing took about 2 months (channel 100 Mbit).
		Tecnology: CentOS, mysql, PHP, JS, multithreading, cron, curl, wget, raid, rsync

		2015-2019
		Domaing (.RU).
		Interception of released domain names in the zone RU. Creating software for analysis, selection and registration of domain names.
		Tecnology: CentOS, mysql, PHP, Python, JS, JQuery, multithreading, cron, curl, client-server, distributed servers.

		2016-2016
		Screenshot service.
		Create full-page screenshots of sites.
		Tecnology: CentOS, mysql, PHP, phantomJS, multithreading, cron

		2018-2019
		Learning python
		Independent study of the new programming language python. Language attracts with its multifunctional, portability, brevity, structuring and conciseness.
		Tecnology: python

		2018-2019
		Domayning (.CO.UK)
		Updating and adaptation of software to intercept domain names from other domain zones other than RU. Application of registration experience in RU zones to other zones: co.uk. Creating a universal software that is quickly configured to any domain zone.
		Tecnology: CentOS, mysql, PHP, Python, JQuery, multithreading, cron, curl, client-server, distributed servers.

		2018-2019
		Creating a tool to get the file zone of any domain zone.
		Software based on the work of the dictionary allows you to collect at the moment> 70% of active domain names in any domain zone.
		Tecnology: CentOS, bash, PHP, Python, mysql, distributed servers, cron, curl

		2019-2019
		Small projects on Arduino
		Automated temperature control system in a private house based on 2 arduino boards. One collects information on the current temperature in the house, and the other, using a servo drive, regulates the temperature of the coolant supply to the heating system to maintain the set temperature.
		Tecnology: Arduino, php, mysql

7. Education:
		2006-2011 	Belarusian State University of Informatics and Radioelectronics
		2011-2014: 	Streamline: from Elemetary to Intermidiate level courses.
		2018-2019: 	https://www.hackerrank.com/k0sm0s
	
8. English level:
	Current level - intermediate.
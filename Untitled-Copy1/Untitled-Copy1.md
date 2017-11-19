

```python
from citipy import citipy
import json
import requests
import numpy as np
import matplotlib.pyplot as plt
from apikeys import OWP_key
import pandas as pd
from time import sleep
```


```python
cities = []
last_city = ''
latstep = 2
lngstep = 2
for j in range(-180,180,lngstep):
    for i in range(-90,90,latstep):
        city = citipy.nearest_city( i, j)
        if city != last_city:
            cities.append({'name': city.city_name, 'country': city.country_code } )
            print(city.city_name, city.country_code, end = '\t\t')
        last_city = city
temps = {}
print('DONE!')
```

    vaini to		halalo wf		vaitupu wf		kapaa us		provideniya ru		egvekinot ru		mys shmidta ru		vaini to		neiafu to		halalo wf		vaitupu wf		kapaa us		provideniya ru		egvekinot ru		mys shmidta ru		vaini to		neiafu to		hihifo to		halalo wf		vaitupu wf		kapaa us		provideniya ru		egvekinot ru		mys shmidta ru		vaini to		pangai to		neiafu to		hihifo to		falealupo ws		sataua ws		vaitupu wf		kapaa us		provideniya ru		lavrentiya ru		mys shmidta ru		vaini to		pangai to		alofi nu		neiafu to		hihifo to		pata ws		saleaula ws		kapaa us		bethel us		provideniya ru		lavrentiya ru		mys shmidta ru		vaini to		alofi nu		satitoa ws		samusu ws		samalaeulu ws		saleaula ws		kapaa us		bethel us		provideniya ru		lavrentiya ru		mys shmidta ru		barrow us		mataura pf		vaini to		alofi nu		satitoa ws		samusu ws		samalaeulu ws		saleaula ws		nanakuli us		kapaa us		bethel us		nome us		lavrentiya ru		barrow us		mataura pf		avarua ck		alofi nu		satitoa ws		samusu ws		samalaeulu ws		saleaula ws		makakilo city us		kapaa us		bethel us		nome us		barrow us		mataura pf		avarua ck		alofi nu		satitoa ws		samusu ws		lufilufi ws		samalaeulu ws		hilo us		makakilo city us		kapaa us		bethel us		nome us		barrow us		mataura pf		avarua ck		samusu ws		hilo us		makakilo city us		nanakuli us		kapaa us		kodiak us		bethel us		nome us		barrow us		mataura pf		avarua ck		faanui pf		samusu ws		hilo us		ewa beach us		makakilo city us		kapaa us		kodiak us		bethel us		barrow us		mataura pf		avarua ck		faanui pf		hilo us		lahaina us		honolulu us		wahiawa us		kapaa us		kodiak us		bethel us		barrow us		mataura pf		avera pf		avarua ck		vaitape pf		faanui pf		hilo us		kihei us		kahului us		kailua us		ahuimanu us		kapaa us		kodiak us		kenai us		barrow us		mataura pf		avera pf		vaitape pf		faanui pf		hilo us		kahului us		kailua us		ahuimanu us		kapaa us		kodiak us		homer us		kenai us		barrow us		mataura pf		avera pf		moerai pf		tevaitoa pf		faanui pf		atuona pf		hilo us		kahului us		kailua us		ahuimanu us		kapaa us		kodiak us		homer us		kenai us		anchorage us		college us		barrow us		mataura pf		moerai pf		teahupoo pf		haapiti pf		fare pf		faanui pf		atuona pf		hilo us		kahului us		kodiak us		homer us		sterling us		wasilla us		college us		barrow us		mataura pf		teahupoo pf		tautira pf		tiarei pf		fare pf		atuona pf		hilo us		kahului us		kodiak us		anchorage us		palmer us		college us		barrow us		mataura pf		tautira pf		tiarei pf		atuona pf		hilo us		kahului us		kodiak us		palmer us		fairbanks us		college us		barrow us		mataura pf		tautira pf		atuona pf		hilo us		kahului us		fortuna us		sitka us		palmer us		fairbanks us		aklavik ca		barrow us		mataura pf		rikitea pf		tautira pf		atuona pf		hilo us		fortuna us		sitka us		haines junction ca		fairbanks us		aklavik ca		tuktoyaktuk ca		rikitea pf		atuona pf		hilo us		fortuna us		port hardy ca		sitka us		haines junction ca		mayo ca		aklavik ca		tuktoyaktuk ca		rikitea pf		atuona pf		hilo us		half moon bay us		fortuna us		port hardy ca		ketchikan us		sitka us		haines junction ca		mayo ca		aklavik ca		tuktoyaktuk ca		rikitea pf		atuona pf		hilo us		lompoc us		pacific grove us		half moon bay us		fortuna us		north bend us		port hardy ca		prince rupert ca		ketchikan us		sitka us		whitehorse ca		mayo ca		aklavik ca		tuktoyaktuk ca		rikitea pf		atuona pf		hilo us		lompoc us		pacific grove us		half moon bay us		fortuna us		north bend us		port hardy ca		prince rupert ca		ketchikan us		sitka us		juneau us		whitehorse ca		mayo ca		inuvik ca		tuktoyaktuk ca		rikitea pf		atuona pf		guerrero negro mx		lompoc us		pacific grove us		half moon bay us		pacifica us		fortuna us		coos bay us		north bend us		port hardy ca		prince rupert ca		ketchikan us		juneau us		whitehorse ca		mayo ca		inuvik ca		tuktoyaktuk ca		rikitea pf		atuona pf		constitucion mx		guerrero negro mx		san quintin mx		lompoc us		pacific grove us		half moon bay us		fortuna us		coos bay us		north bend us		port hardy ca		prince rupert ca		ketchikan us		juneau us		norman wells ca		tuktoyaktuk ca		rikitea pf		atuona pf		constitucion mx		guerrero negro mx		san quintin mx		lompoc us		pacific grove us		half moon bay us		ukiah us		fortuna us		eureka us		north bend us		ucluelet ca		port hardy ca		kitimat ca		smithers ca		norman wells ca		tuktoyaktuk ca		punta arenas cl		rikitea pf		atuona pf		cabo san lucas mx		constitucion mx		guerrero negro mx		san quintin mx		lompoc us		pacific grove us		half moon bay us		ukiah us		fortuna us		eureka us		north bend us		astoria us		ucluelet ca		campbell river ca		port hardy ca		burns lake ca		smithers ca		fort nelson ca		norman wells ca		tuktoyaktuk ca		punta arenas cl		rikitea pf		atuona pf		cabo san lucas mx		constitucion mx		guerrero negro mx		san quintin mx		lompoc us		pacific grove us		half moon bay us		healdsburg us		fortuna us		grants pass us		north bend us		astoria us		sooke ca		powell river ca		quesnel ca		vanderhoof ca		mackenzie ca		fort nelson ca		norman wells ca		tuktoyaktuk ca		punta arenas cl		rikitea pf		atuona pf		cabo san lucas mx		constitucion mx		guerrero negro mx		san quintin mx		lompoc us		monterey us		concord us		red bluff us		klamath falls us		bend us		washougal us		west lake stevens us		lillooet ca		williams lake ca		prince george ca		fort saint john ca		fort nelson ca		norman wells ca		tuktoyaktuk ca		punta arenas cl		rikitea pf		atuona pf		cabo san lucas mx		constitucion mx		guerrero negro mx		san quintin mx		rosarito mx		port hueneme us		isla vista us		avenal us		merced us		sun valley us		susanville us		redmond us		grandview us		east wenatchee bench us		peachland ca		chase ca		beaverlodge ca		dawson creek ca		fort saint john ca		fort nelson ca		hay river ca		yellowknife ca		norman wells ca		tuktoyaktuk ca		punta arenas cl		rikitea pf		atuona pf		san patricio mx		cabo san lucas mx		constitucion mx		guerrero negro mx		san quintin mx		rosarito mx		hacienda heights us		ridgecrest us		fallon us		winnemucca us		baker city us		walla walla us		cheney us		nakusp ca		jasper ca		hinton ca		fairview ca		high level ca		hay river ca		yellowknife ca		norman wells ca		tuktoyaktuk ca		punta arenas cl		rikitea pf		atuona pf		san patricio mx		cabo san lucas mx		constitucion mx		guerrero negro mx		san quintin mx		ensenada mx		twentynine palms us		pahrump us		elko us		mountain home us		garden city us		lewiston us		sandpoint us		kimberley ca		banff ca		whitecourt ca		high prairie ca		high level ca		hay river ca		yellowknife ca		norman wells ca		punta arenas cl		rikitea pf		puerto ayora ec		coahuayana mx		san patricio mx		cabo san lucas mx		constitucion mx		guerrero negro mx		san felipe mx		fortuna foothills us		lake havasu city us		kingman us		saint george us		west wendover us		burley us		hailey us		hamilton us		polson us		claresholm ca		penhold ca		westlock ca		slave lake ca		hay river ca		yellowknife ca		punta arenas cl		castro cl		rikitea pf		puerto ayora ec		lazaro cardenas mx		coahuayana mx		san patricio mx		cabo san lucas mx		constitucion mx		loreto mx		santa rosalia mx		pitiquito mx		sonoita mx		paradise valley us		flagstaff us		cedar city us		payson us		preston us		rexburg us		butte us		great falls us		taber ca		hanna ca		two hills ca		athabasca ca		yellowknife ca		punta arenas cl		castro cl		rikitea pf		puerto ayora ec		ixtapa mx		lazaro cardenas mx		coahuayana mx		san patricio mx		tomatlan mx		cabo san lucas mx		la paz mx		ahome mx		cocorit mx		cumpas mx		sierra vista us		show low us		winslow us		cortez us		price us		green river us		jackson us		livingston us		havre us		maple creek ca		macklin ca		grand centre ca		yellowknife ca		punta arenas cl		castro cl		rikitea pf		puerto ayora ec		ixtapa mx		lazaro cardenas mx		coahuayana mx		san patricio mx		tomatlan mx		mazatlan mx		eldorado mx		sinaloa mx		creel mx		benito juarez mx		deming us		socorro us		bloomfield us		montrose us		craig us		rawlins us		worland us		billings us		shaunavon ca		swift current ca		biggar ca		meadow lake ca		la ronge ca		yellowknife ca		punta arenas cl		castro cl		ancud cl		lebu cl		rikitea pf		puerto ayora ec		acapulco mx		san jeronimo mx		ixtapa mx		lazaro cardenas mx		coahuayana mx		san patricio mx		tomatlan mx		teacapan mx		tayoltita mx		santa maria del oro mx		santa cruz de rosales mx		ahumada mx		socorro us		ruidoso us		espanola us		alamosa us		boulder us		laramie us		gillette us		miles city us		glendive us		assiniboia ca		watrous ca		prince albert ca		la ronge ca		yellowknife ca		punta arenas cl		castro cl		ancud cl		lebu cl		puerto ayora ec		acapulco mx		san jeronimo mx		ixtapa mx		lazaro cardenas mx		la orilla mx		coahuayana mx		juchitlan mx		villa guerrero mx		vicente guerrero mx		mapimi mx		camargo mx		ojinaga mx		carlsbad us		portales us		tucumcari us		pueblo us		fort morgan us		torrington us		spearfish us		glendive us		sidney us		weyburn ca		wadena ca		nipawin ca		la ronge ca		yellowknife ca		punta arenas cl		castro cl		ancud cl		lebu cl		pisco pe		puerto ayora ec		tecoanapa mx		acapulco mx		san jeronimo mx		petatlan mx		la union mx		tlazazalca mx		palo alto mx		canitas mx		parras mx		muzquiz mx		del rio us		midland us		plainview us		dumas us		lamar us		sterling us		north platte us		rapid valley us		dickinson us		minot us		moosomin ca		kamsack ca		flin flon ca		thompson ca		yellowknife ca		punta arenas cl		castro cl		ancud cl		lebu cl		pisco pe		puerto ayora ec		puerto escondido mx		tecoanapa mx		acapulco mx		apaxtla mx		temascalcingo mx		fernandez mx		doctor arroyo mx		marin mx		nuevo laredo mx		uvalde us		abilene us		vernon us		woodward us		dodge city us		lexington us		north platte us		pierre us		bismarck us		devils lake us		brandon ca		dauphin ca		the pas ca		thompson ca		yellowknife ca		punta arenas cl		castro cl		ancud cl		lebu cl		pisco pe		puerto ayora ec		pochutla mx		puerto escondido mx		huazolotitlan mx		acatlan mx		zacatlan mx		panuco mx		soto la marina mx		rio bravo mx		alice us		kyle us		stephenville us		wichita falls us		enid us		hutchinson us		hastings us		norfolk us		mitchell us		aberdeen us		grafton us		carman ca		gimli ca		thompson ca		yellowknife ca		punta arenas cl		castro cl		ancud cl		lebu cl		pisco pe		hualmay pe		puerto ayora ec		champerico gt		pochutla mx		xadani mx		loma bonita mx		emilio carranza mx		tamiahua mx		nuevo progreso mx		brownsville us		port lavaca us		katy us		athens us		durant us		jenks us		emporia us		beatrice us		south sioux city us		marshall us		fergus falls us		grand forks us		pinawa ca		gimli ca		thompson ca		qaanaaq gl		punta arenas cl		castro cl		ancud cl		lebu cl		pisco pe		hualmay pe		puerto ayora ec		champerico gt		ocos gt		puerto madero mx		paredon mx		las choapas mx		paraiso mx		vega de alatorre mx		matamoros mx		freeport us		galveston us		nederland us		bossier city us		hope us		fayetteville us		clinton us		excelsior springs us		boone us		mankato us		brainerd us		fort frances ca		kenora ca		thompson ca		qaanaaq gl		ushuaia ar		punta arenas cl		castro cl		ancud cl		lebu cl		pisco pe		hualmay pe		huarmey pe		san cristobal ec		puerto ayora ec		acajutla sv		san jose gt		champerico gt		la trinitaria mx		jonuta mx		sabancuy mx		celestun mx		morgan city us		abbeville us		monroe us		pine bluff us		batesville us		rolla us		quincy us		cedar rapids us		winona us		superior us		atikokan ca		sioux lookout ca		thompson ca		qaanaaq gl		ushuaia ar		punta arenas cl		castro cl		ancud cl		lebu cl		coquimbo cl		marcona pe		pisco pe		hualmay pe		huarmey pe		chicama pe		san cristobal ec		puerto ayora ec		santa cruz cr		la libertad sv		acajutla sv		conguaco gt		chisec gt		escarcega mx		hecelchakan mx		progreso mx		houma us		chalmette us		brandon us		grenada us		blytheville us		waterloo us		jacksonville us		clinton us		wisconsin rapids us		merrill us		thunder bay ca		sioux lookout ca		thompson ca		qaanaaq gl		ushuaia ar		punta arenas cl		castro cl		ancud cl		lebu cl		coquimbo cl		marcona pe		pisco pe		hualmay pe		huarmey pe		pimentel pe		sechura pe		san cristobal ec		puerto baquerizo moreno ec		nicoya cr		santa cruz cr		san rafael del sur ni		corinto ni		la florida hn		puerto cortes hn		san pedro bz		felipe carrillo puerto mx		panaba mx		estelle us		pascagoula us		fairhope us		meridian us		columbus us		paris us		henderson us		urbana us		elk grove village us		manitowoc us		marquette us		terrace bay ca		geraldton ca		attawapiskat ca		thompson ca		qaanaaq gl		ushuaia ar		punta arenas cl		castro cl		ancud cl		lebu cl		coquimbo cl		marcona pe		pisco pe		hualmay pe		huarmey pe		chicama pe		sechura pe		paita pe		talara pe		san cristobal ec		burica pa		nicoya cr		santa cruz cr		granada ni		trojes hn		puerto castilla hn		savannah bight hn		cozumel mx		isla mujeres mx		mantua cu		saint pete beach us		panama city us		troy us		gadsden us		lebanon us		radcliff us		noblesville us		granger us		big rapids us		escanaba us		marathon ca		longlac ca		attawapiskat ca		clyde river ca		qaanaaq gl		ushuaia ar		punta arenas cl		castro cl		ancud cl		lebu cl		coquimbo cl		marcona pe		pisco pe		lima pe		hualmay pe		chimbote pe		chicama pe		sechura pe		paita pe		talara pe		salinas ec		manta ec		muisne ec		burica pa		buenos aires cr		san isidro cr		bluefields ni		rosita ni		barra patuca hn		santa fe cu		guane cu		bahia honda cu		south venice us		clearwater us		tallahassee us		cordele us		lawrenceville us		knoxville us		winchester us		tipp city us		adrian us		bay city us		thessalon ca		chapleau ca		hearst ca		attawapiskat ca		clyde river ca		qaanaaq gl		ushuaia ar		punta arenas cl		coihaique cl		castro cl		ancud cl		lebu cl		talcahuano cl		coquimbo cl		marcona pe		pisco pe		hualmay pe		huarmey pe		santiago de cao pe		pimentel pe		sechura pe		el alto pe		salinas ec		manta ec		muisne ec		la palma pa		remedios pa		bocas del toro pa		san andres co		puerto cabezas ni		iralaya hn		george town ky		west bay ky		batabano cu		key west us		naples us		winston us		lakeside us		jesup us		greenwood us		boone us		saint albans us		zanesville us		blenheim ca		goderich ca		little current ca		timmins ca		kapuskasing ca		attawapiskat ca		clyde river ca		qaanaaq gl		ushuaia ar		punta arenas cl		coihaique cl		castro cl		ancud cl		lebu cl		constitucion cl		coquimbo cl		antofagasta cl		marcona pe		pisco pe		lima pe		hualmay pe		chimbote pe		chicama pe		olmos pe		alamor ec		el triunfo ec		pedernales ec		esmeraldas ec		mosquera co		la palma pa		guarare pa		portobelo pa		san andres co		black river jm		bodden town ky		manicaragua cu		corralillo cu		aventura us		sebastian us		ormond beach us		charleston us		florence us		high point us		hollins us		uniontown us		erie us		orangeville ca		sturgeon falls ca		kirkland lake ca		cochrane ca		moose factory ca		attawapiskat ca		iqaluit ca		clyde river ca		qaanaaq gl		ushuaia ar		punta arenas cl		coihaique cl		castro cl		ancud cl		lebu cl		talcahuano cl		valparaiso cl		coquimbo cl		taltal cl		antofagasta cl		marcona pe		pisco pe		chancay pe		huarmey pe		quiruvilca pe		chachapoyas pe		yantzaza ec		palora ec		cayambe ec		magui co		litoral del san juan co		mutis co		el real de santa maria pa		ailigandi pa		tigre pa		bull savanna jm		black river jm		niquero cu		esmeralda cu		andros town bs		high rock bs		merritt island us		georgetown us		wilmington us		rocky mount us		culpeper us		chambersburg us		olean us		colborne ca		deep river ca		malartic ca		matagami ca		moose factory ca		attawapiskat ca		iqaluit ca		clyde river ca		qaanaaq gl		ushuaia ar		punta arenas cl		coihaique cl		castro cl		ancud cl		valdivia cl		lebu cl		constitucion cl		valparaiso cl		coquimbo cl		taltal cl		antofagasta cl		tocopilla cl		camana pe		acari pe		marcona pe		subtanjalla pe		chicla pe		ambo pe		tocache pe		yurimaguas pe		barranca pe		palora ec		puerto asis co		saladoblanco co		tulua co		salgar co		tierralta co		san onofre co		puerto colombia co		morant bay jm		el cobre cu		gibara cu		rock sound bs		dunmore town bs		marsh harbour bs		wilmington us		havelock us		elizabeth city us		lexington park us		coatesville us		endicott us		watertown us		maniwaki ca		senneterre ca		chapais ca		moose factory ca		iqaluit ca		clyde river ca		qaanaaq gl		ushuaia ar		punta arenas cl		coihaique cl		castro cl		ancud cl		valdivia cl		lebu cl		talcahuano cl		constitucion cl		valparaiso cl		coquimbo cl		vallenar cl		taltal cl		antofagasta cl		tocopilla cl		ilo pe		camana pe		acari pe		tambo pe		ayna pe		satipo pe		pucallpa pe		requena pe		nauta pe		iquitos pe		puerto leguizamo co		la macarena co		acacias co		florian co		santa rosa del sur co		bosconia co		santa marta co		riohacha co		les cayes ht		baracoa cu		clarence town bs		cockburn town bs		marsh harbour bs		havelock us		virginia beach us		ocean city us		point pleasant us		kingston us		glens falls us		sainte-adele ca		la tuque ca		chapais ca		iqaluit ca		clyde river ca		qaanaaq gl		ushuaia ar		punta arenas cl		rio gallegos ar		coihaique cl		puerto montt cl		panguipulli cl		mulchen cl		parral cl		san antonio cl		la ligua cl		coquimbo cl		vallenar cl		taltal cl		antofagasta cl		tocopilla cl		iquique cl		ilo pe		lluta pe		santo tomas pe		pangoa pe		porto walter br		cruzeiro do sul br		ipixuna br		iquitos pe		miraflores co		calamar co		puerto gaitan co		paz de ariporo co		san juan de colon ve		villa del rosario ve		uribia co		manaure co		pedernales do		cap-haitien ht		cockburn harbour tc		cockburn town bs		marsh harbour bs		havelock us		elizabeth city us		virginia beach us		brigantine us		mastic beach us		southbridge us		haverhill us		warwick ca		desbiens ca		dolbeau ca		chapais ca		iqaluit ca		clyde river ca		qaanaaq gl		ushuaia ar		punta arenas cl		rio gallegos ar		coihaique cl		san carlos de bariloche ar		neuquen ar		san clemente cl		machali cl		salamanca cl		vicuna cl		copiapo cl		diego de almagro cl		antofagasta cl		tocopilla cl		iquique cl		tacna pe		puno pe		macusani pe		iberia pe		manoel urbano br		feijo br		eirunepe br		leticia co		japura br		mitu co		cumaribo co		cravo norte co		barinas ve		carora ve		punto fijo ve		oranjestad aw		bani do		bajos de haina do		sosua do		cockburn town tc		cockburn town bs		hamilton bm		nantucket us		brewster us		topsham us		liniere ca		la malbaie ca		forestville ca		chute-aux-outardes ca		port-cartier ca		iqaluit ca		clyde river ca		narsaq gl		qaanaaq gl		ushuaia ar		rio gallegos ar		comodoro rivadavia ar		trelew ar		neuquen ar		san rafael ar		san juan ar		la rioja ar		diego de almagro cl		calama cl		uyuni bo		eucaliptus bo		coroico bo		rurrenabaque bo		cobija bo		rio branco br		boca do acre br		jutai br		santo antonio do ica br		tonantins br		sao gabriel da cachoeira br		inirida co		puerto ayacucho ve		calabozo ve		tacarigua ve		kralendijk an		rincon an		guanica us		rincon us		samana do		cockburn town tc		hamilton bm		nantucket us		brewster us		bar harbor us		houlton us		price ca		baie-comeau ca		port-cartier ca		sept-iles ca		iqaluit ca		pangnirtung ca		clyde river ca		narsaq gl		qaanaaq gl		ushuaia ar		rio gallegos ar		comodoro rivadavia ar		trelew ar		puerto madryn ar		general roca ar		santa rosa ar		mercedes ar		san luis ar		la rioja ar		catamarca ar		tucuman ar		jujuy ar		villazon bo		potosi bo		capinota bo		chimore bo		santa rosa bo		rodrigues alves br		riberalta bo		pauini br		carauari br		fonte boa br		santa isabel do rio negro br		sao gabriel da cachoeira br		inirida co		puerto carreno co		zaraza ve		altagracia de orituco ve		caraballeda ve		kralendijk an		arroyo us		patillas us		san juan us		hamilton bm		saint george bm		nantucket us		shelburne ca		yarmouth ca		oromocto ca		new richmond ca		sept-iles ca		iqaluit ca		pangnirtung ca		clyde river ca		narsaq gl		qaanaaq gl		ushuaia ar		comodoro rivadavia ar		rawson ar		puerto madryn ar		viedma ar		santa rosa ar		general pico ar		rio cuarto ar		rio tercero ar		cordoba ar		santiago del estero ar		tucuman ar		libertador general san martin ar		yacuiba bo		monteagudo bo		mairana bo		ascension bo		san ramon bo		rodrigues alves br		ariquemes br		porto velho br		canutama br		coari br		maraa br		santa isabel do rio negro br		boa vista br		ciudad bolivar ve		cumana ve		la asuncion ve		barroualie vc		middle island kn		road town vg		hamilton bm		saint george bm		shelburne ca		liverpool ca		lunenburg ca		amherst ca		grande-riviere ca		havre-saint-pierre ca		iqaluit ca		pangnirtung ca		clyde river ca		narsaq gl		ushuaia ar		comodoro rivadavia ar		rawson ar		viedma ar		punta alta ar		bahia blanca ar		lincoln ar		venado tuerto ar		san francisco ar		rafaela ar		presidencia roque saenz pena ar		doctor pedro p. pena py		mayor pablo lagerenza py		pailon bo		san javier bo		rolim de moura br		presidente medici br		jaru br		humaita br		manicore br		codajas br		barcelos br		boa vista br		upata ve		point fortin tt		gouyave gd		canaries lc		vieux-habitants gp		codrington ag		the valley ai		hamilton bm		saint george bm		liverpool ca		halifax ca		antigonish ca		cap-aux-meules ca		havre-saint-pierre ca		saint-augustin ca		pangnirtung ca		upernavik gl		narsaq gl		ushuaia ar		rawson ar		viedma ar		tres arroyos ar		veinticinco de mayo ar		san pedro ar		parana ar		reconquista ar		resistencia ar		presidencia roque saenz pena ar		pozo colorado py		filadelfia py		mayor pablo lagerenza py		san pedro bo		san rafael bo		vilhena br		aripuana br		novo aripuana br		borba br		manaus br		boa vista br		lethem gy		bartica gy		mabaruma gy		rio claro tt		scarborough tt		crab hill bb		saint-francois gp		codrington ag		the valley ai		hamilton bm		saint george bm		port hawkesbury ca		louisbourg ca		channel-port aux basques ca		saint-augustin ca		pangnirtung ca		upernavik gl		narsaq gl		ushuaia ar		rawson ar		viedma ar		necochea ar		mar del plata ar		dolores ar		carmelo uy		paysandu uy		bella union uy		cerrito py		villa oliva py		concepcion py		san lazaro py		fuerte olimpo py		puerto quijarro bo		caceres br		nova olimpia br		vilhena br		alta floresta br		jacareacanga br		maues br		urucara br		bonfim br		ituni gy		linden gy		georgetown gy		mabaruma gy		oistins bb		bathsheba bb		crab hill bb		saint-francois gp		codrington ag		saint george bm		louisbourg ca		burgeo ca		deer lake ca		saint-augustin ca		maniitsoq gl		sisimiut gl		upernavik gl		narsaq gl		ushuaia ar		rawson ar		necochea ar		mar del plata ar		paso de carrasco uy		florida uy		tacuarembo uy		alegrete br		posadas ar		abai py		lima py		bela vista br		miranda br		coxim br		santo antonio do leverger br		diamantino br		alta floresta br		jacareacanga br		itaituba br		juruti br		oriximina br		grand-santi gf		brokopondo sr		totness sr		georgetown gy		oistins bb		bathsheba bb		saint-francois gp		codrington ag		saint george bm		saint-pierre pm		harbour breton ca		springdale ca		saint anthony ca		nuuk gl		maniitsoq gl		sisimiut gl		upernavik gl		ushuaia ar		rawson ar		necochea ar		mar del plata ar		maldonado uy		rocha uy		melo uy		santa maria br		santo augusto br		santo antonio do sudoeste br		altonia br		rio brilhante br		campo verde br		coxim br		guiratinga br		jaciara br		alta floresta br		sao felix do xingu br		santarem br		monte alegre br		prainha br		camopi gf		grand-santi gf		mana gf		marienburg sr		oistins bb		bathsheba bb		saint-francois gp		codrington ag		saint george bm		saint-pierre pm		marystown ca		carbonear ca		hare bay ca		saint anthony ca		paamiut gl		nuuk gl		maniitsoq gl		sisimiut gl		kangaatsiaq gl		aasiaat gl		upernavik gl		ushuaia ar		necochea ar		mar del plata ar		maldonado uy		rocha uy		chuy uy		santa vitoria do palmar br		rio grande br		butia br		tapejara br		pinhao br		barbosa ferraz br		presidente venceslau br		tres lagoas br		jatai br		aragarcas br		mozarlandia br		sao miguel do araguaia br		formoso do araguaia br		sao felix do xingu br		altamira br		porto de moz br		mazagao br		amapa br		saint-georges gf		kourou gf		sinnamary gf		iracoubo gf		mana gf		bathsheba bb		saint-francois gp		codrington ag		saint george bm		saint-pierre pm		bay roberts ca		torbay ca		bonavista ca		saint anthony ca		paamiut gl		nuuk gl		maniitsoq gl		aasiaat gl		ilulissat gl		upernavik gl		ushuaia ar		mar del plata ar		rocha uy		chuy uy		rio grande br		palmares do sul br		tramandai br		sao joaquim br		mafra br		terra roxa br		pompeia br		cardoso br		goiatuba br		goias br		crixas br		formoso do araguaia br		miranorte br		conceicao do araguaia br		itupiranga br		tucurui br		oeiras do para br		tucuma br		amapa br		saint-georges gf		cayenne gf		sinnamary gf		iracoubo gf		bathsheba bb		codrington ag		saint george bm		torbay ca		bonavista ca		saint anthony ca		paamiut gl		nuuk gl		qasigiannguit gl		ilulissat gl		upernavik gl		ushuaia ar		mar del plata ar		rocha uy		chuy uy		rio grande br		cidreira br		laguna br		florianopolis br		pontal do parana br		capao bonito br		ibate br		miguelopolis br		catalao br		brasilia br		cavalcante br		parana br		palmas br		araguaina br		ananas br		paragominas br		acara br		curuca br		salinopolis br		amapa br		saint-georges gf		cayenne gf		sinnamary gf		bathsheba bb		saint-francois gp		codrington ag		saint george bm		torbay ca		bonavista ca		nanortalik gl		qaqortoq gl		paamiut gl		nuuk gl		qasigiannguit gl		ilulissat gl		upernavik gl		ushuaia ar		mar del plata ar		rocha uy		chuy uy		rio grande br		cidreira br		laguna br		florianopolis br		peruibe br		guaruja br		pouso alegre br		bambui br		joao pinheiro br		arinos br		posse br		taguatinga br		morros br		balsas br		grajau br		santa ines br		maracacume br		viseu br		salinopolis br		saint-georges gf		cayenne gf		sinnamary gf		bathsheba bb		codrington ag		saint george bm		torbay ca		bonavista ca		nanortalik gl		qaqortoq gl		ilulissat gl		upernavik gl		ushuaia ar		mar del plata ar		rocha uy		chuy uy		rio grande br		cidreira br		laguna br		imbituba br		ilhabela br		mangaratiba br		lima duarte br		ibirite br		diamantina br		sao joao da ponte br		carinhanha br		ibotirama br		bom jesus br		urucui br		colinas br		coroata br		sao jose de ribamar br		cururupu br		carutapera br		salinopolis br		saint-georges gf		cayenne gf		sinnamary gf		bathsheba bb		codrington ag		ribeira grande pt		torbay ca		nanortalik gl		qaqortoq gl		tasiilaq gl		ilulissat gl		upernavik gl		ushuaia ar		mar del plata ar		rocha uy		chuy uy		cidreira br		laguna br		imbituba br		arraial do cabo br		itaocara br		manhuacu br		malacacheta br		taiobeiras br		livramento br		ibipeba br		remanso br		simplicio mendes br		elesbao veloso br		batalha br		tutoia br		cururupu br		carutapera br		cayenne gf		ponta do sol cv		ribeira grande pt		torbay ca		nanortalik gl		tasiilaq gl		ilulissat gl		upernavik gl		ushuaia ar		mar del plata ar		rocha uy		chuy uy		cidreira br		laguna br		arraial do cabo br		armacao dos buzios br		sao joao da barra br		serra br		montanha br		itarantim br		jitauna br		baixa grande br		jaguarari br		ouricuri br		taua br		iraucuba br		acarau br		carutapera br		cayenne gf		porto novo cv		ponta do sol cv		ribeira grande pt		torbay ca		nanortalik gl		tasiilaq gl		ilulissat gl		ushuaia ar		mar del plata ar		rocha uy		chuy uy		cidreira br		laguna br		arraial do cabo br		sao joao da barra br		vila velha br		linhares br		caravelas br		belmonte br		marau br		entre rios br		jeremoabo br		flores br		umarizal br		beberibe br		jardim br		itarema br		sao filipe cv		porto novo cv		ponta do sol cv		ribeira grande pt		nanortalik gl		tasiilaq gl		ushuaia ar		mar del plata ar		rocha uy		chuy uy		cidreira br		laguna br		arraial do cabo br		sao joao da barra br		vila velha br		caravelas br		belmonte br		camacari br		aracaju br		coruripe br		toritama br		sao tome br		macau br		aquiraz br		caucaia br		trairi br		itarema br		sao filipe cv		porto novo cv		ponta do sol cv		ribeira grande pt		lagoa pt		nanortalik gl		tasiilaq gl		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		laguna br		arraial do cabo br		sao joao da barra br		vila velha br		caravelas br		belmonte br		conde br		coruripe br		maragogi br		olinda br		nisia floresta br		touros br		aquiraz br		jardim br		trairi br		sao filipe cv		porto novo cv		ponta do sol cv		ribeira grande pt		lagoa pt		nanortalik gl		tasiilaq gl		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		arraial do cabo br		sao joao da barra br		guarapari br		vila velha br		caravelas br		belmonte br		coruripe br		maragogi br		sao jose da coroa grande br		itamaraca br		cabedelo br		touros br		sao filipe cv		ponta do sol cv		ribeira grande pt		lagoa pt		tasiilaq gl		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		arraial do cabo br		sao joao da barra br		vila velha br		caravelas br		belmonte br		coruripe br		maceio br		maragogi br		olinda br		pitimbu br		cabedelo br		natal br		touros br		sao filipe cv		porto novo cv		ponta do sol cv		ribeira grande pt		lagoa pt		grindavik is		olafsvik is		bolungarvik is		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		arraial do cabo br		sao joao da barra br		vila velha br		caravelas br		belmonte br		maceio br		maragogi br		sao jose da coroa grande br		olinda br		pitimbu br		cabedelo br		nisia floresta br		touros br		sao filipe cv		porto novo cv		ponta do sol cv		ponta delgada pt		horta pt		lagoa pt		grindavik is		olafsvik is		bolungarvik is		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		arraial do cabo br		sao joao da barra br		vila velha br		caravelas br		maceio br		maragogi br		sao jose da coroa grande br		olinda br		pitimbu br		cabedelo br		natal br		touros br		sao filipe cv		mindelo cv		ponta do sol cv		los llanos de aridane es		vila franca do campo pt		ponta delgada pt		arrifes pt		praia da vitoria pt		lagoa pt		grindavik is		olafsvik is		bolungarvik is		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		arraial do cabo br		sao joao da barra br		vila velha br		caravelas br		georgetown sh		bubaque gw		sao filipe cv		praia cv		ribeira brava cv		pombas cv		ponta do sol cv		los llanos de aridane es		vila franca do campo pt		praia da vitoria pt		lagoa pt		grindavik is		olafsvik is		bolungarvik is		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		arraial do cabo br		sao joao da barra br		vila velha br		caravelas br		georgetown sh		goderich sl		bubaque gw		praia cv		vila do maio cv		sal rei cv		santa maria cv		nouadhibou mr		los llanos de aridane es		ponta do sol pt		vila franca do campo pt		praia da vitoria pt		dingle ie		vestmannaeyjar is		grindavik is		kopavogur is		stykkisholmur is		bolungarvik is		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		arraial do cabo br		jamestown sh		georgetown sh		goderich sl		bubaque gw		oussouye sn		gunjur gm		dakar sn		santa maria cv		nouadhibou mr		los llanos de aridane es		ponta do sol pt		vila franca do campo pt		dingle ie		vestmannaeyjar is		hvolsvollur is		skagastrond is		illoqqortoormiut gl		ushuaia ar		mar del plata ar		chuy uy		cidreira br		arraial do cabo br		jamestown sh		georgetown sh		bonthe sl		goderich sl		bubaque gw		oussouye sn		dakar sn		nouakchott mr		nouadhibou mr		adeje es		los llanos de aridane es		santa cruz de la palma es		ponta do sol pt		camacha pt		vila franca do campo pt		muros es		dingle ie		vestmannaeyjar is		akureyri is		husavik is		illoqqortoormiut gl		ushuaia ar		cape town za		jamestown sh		georgetown sh		mattru sl		bonthe sl		goderich sl		conakry gn		bubaque gw		canchungo gw		kahone sn		louga sn		nouakchott mr		nouadhibou mr		santa lucia es		galdar es		santa cruz de tenerife es		machico pt		camacha pt		peniche pt		muros es		dingle ie		westport ie		hofn is		husavik is		illoqqortoormiut gl		ushuaia ar		cape town za		jamestown sh		georgetown sh		monrovia lr		mattru sl		bonthe sl		goderich sl		boffa gn		gabu gw		tambacounda sn		gollere sn		ndioum sn		atar mr		aguimes es		puerto del rosario es		teguise es		porto santo pt		camacha pt		colares pt		peniche pt		muros es		dingle ie		westport ie		hofn is		husavik is		illoqqortoormiut gl		hermanus za		cape town za		jamestown sh		georgetown sh		harper lr		buchanan lr		monrovia lr		robertsport lr		serabu sl		mamou gn		mali gn		kayes ml		maghama mr		bababe mr		atar mr		puerto del rosario es		arrecife es		teguise es		asfi ma		aljezur pt		cascais pt		peniche pt		muros es		carballo es		bantry ie		dingle ie		westport ie		ballina ie		sorvag fo		hofn is		husavik is		illoqqortoormiut gl		hermanus za		cape town za		saldanha za		jamestown sh		georgetown sh		harper lr		buchanan lr		koindu sl		tokonou gn		dinguiraye gn		bafoulabe ml		nioro ml		atar mr		tiznit ma		asfi ma		azimur ma		lagos pt		cascais pt		peniche pt		vila praia de ancora pt		carballo es		ferrol es		skibbereen ie		killorglin ie		westport ie		ballina ie		stornoway gb		sorvag fo		hofn is		husavik is		illoqqortoormiut gl		hermanus za		cape town za		saldanha za		jamestown sh		georgetown sh		harper lr		zwedru lr		touba ci		odienne ci		kangaba ml		kolokani ml		nara ml		araouane ml		taoudenni ml		tiznit ma		tarudant ma		marrakesh ma		casablanca ma		faro pt		ferreira do alentejo pt		castanheira de pera pt		real pt		naron es		cervo es		penzance gb		kinsale ie		youghal ie		boyle ie		buncrana ie		stornoway gb		vagur fo		sorvag fo		vestmanna fo		klaksvik fo		husavik is		illoqqortoormiut gl		hermanus za		cape town za		saldanha za		jamestown sh		georgetown sh		tabou ci		sassandra ci		gagnoa ci		mankono ci		tingrela ci		koutiala ml		niono ml		sokolo ml		araouane ml		taoudenni ml		tarudant ma		marrakesh ma		mrirt ma		sidi qasim ma		barbate es		azuaga es		bejar es		la baneza es		aviles es		plouzane fr		penzance gb		wexford ie		newry gb		bowmore gb		stornoway gb		vagur fo		klaksvik fo		husavik is		illoqqortoormiut gl		barentsburg sj		hermanus za		cape town za		saldanha za		jamestown sh		axim gh		jacqueville ci		adzope ci		dabakala ci		gaoua bf		solenzo bf		bandiagara ml		goundam ml		araouane ml		taoudenni ml		adrar dz		mrirt ma		tawnat ma		torrox es		andujar es		toledo es		aranda de duero es		santander es		ploemeur fr		quimper fr		ivybridge gb		carmarthen gb		whitehaven gb		cumbernauld gb		golspie gb		stromness gb		klaksvik fo		barentsburg sj		hermanus za		cape town za		saldanha za		luderitz na		jamestown sh		axim gh		dunkwa gh		wenchi gh		wa gh		kokologo bf		djibo bf		tombouctou ml		araouane ml		taoudenni ml		adrar dz		nador ma		almeria es		cehegin es		cuenca es		arnedo es		hendaye fr		challans fr		rennes fr		octeville fr		cheltenham gb		keighley gb		eyemouth gb		fraserburgh gb		scalloway gb		brae gb		klaksvik fo		barentsburg sj		hermanus za		cape town za		saldanha za		luderitz na		jamestown sh		port-gentil ga		takoradi gh		cape coast gh		winneba gh		akropong gh		kpandae gh		yendi gh		koupela bf		dori bf		gao ml		kidal ml		tessalit ml		adrar dz		aflu dz		wahran dz		sidi ali dz		benidorm es		burriana es		barbastro es		tonneins fr		angouleme fr		allonnes fr		fecamp fr		hertford gb		bridlington gb		whitley bay gb		peterhead gb		lerwick gb		brae gb		raudeberg no		roald no		barentsburg sj		hermanus za		cape town za		saldanha za		luderitz na		jamestown sh		gamba ga		omboue ga		port-gentil ga		anloga gh		ouidah bj		savalou bj		djougou bj		diapaga bf		ouallam ne		ayorou ne		kidal ml		tessalit ml		adrar dz		aflu dz		medea dz		santa eulalia del rio es		calvia es		berga es		gaillac fr		gueret fr		saint-jean-de-braye fr		abbeville fr		lowestoft gb		great yarmouth gb		bridlington gb		visnes no		solsvik no		floro no		raudeberg no		roald no		bud no		barentsburg sj		hermanus za		cape town za		saldanha za		luderitz na		walvis bay na		henties bay na		namibe ao		soyo ao		gamba ga		omboue ga		port-gentil ga		yenagoa ng		warri ng		epe ng		oyo ng		nikki bj		jega ng		dogondoutchi ne		tahoua ne		kidal ml		tessalit ml		adrar dz		warqla dz		birin dz		tazmalt dz		tigzirt dz		mahon es		palafrugell es		ales fr		riorges fr		saint-andre-les-vergers fr		fourmies fr		monster nl		den helder nl		vigrestad no		varhaug no		solsvik no		floro no		raudeberg no		roald no		bud no		sorland no		barentsburg sj		hermanus za		cape town za		saldanha za		luderitz na		walvis bay na		henties bay na		namibe ao		luanda ao		mayumba ga		gamba ga		omboue ga		port-gentil ga		abonnema ng		yenagoa ng		agbor ng		ode ng		kontagora ng		gusau ng		madaoua ne		abalak ne		arlit ne		gat ly		warqla dz		tuggurt dz		constantine dz		mahon es		la seyne-sur-mer fr		manosque fr		cran-gevrier fr		vesoul fr		clervaux lu		rheden nl		kollumerland nl		hvide sande dk		egersund no		rosendal no		nordfjordeid no		bud no		sistranda no		sorland no		barentsburg sj		hermanus za		cape town za		saldanha za		luderitz na		walvis bay na		henties bay na		opuwo na		namibe ao		luanda ao		soyo ao		mayumba ga		gamba ga		omboue ga		port-gentil ga		luba gq		opobo ng		afikpo ng		makurdi ng		kafanchan ng		malumfashi ng		tessaoua ne		agadez ne		arlit ne		gat ly		warqla dz		duz tn		tawzar tn		manzil salim tn		carbonia it		cabras it		ajaccio fr		imperia it		zermatt ch		kirchzarten de		geisenheim de		sassenberg de		jever de		hvide sande dk		kristiansand no		amot no		ovre ardal no		sistranda no		sorland no		barentsburg sj		hermanus za		cape town za		saldanha za		oranjemund na		luderitz na		walvis bay na		henties bay na		opuwo na		namibe ao		benguela ao		luanda ao		soyo ao		loandjili cg		mayumba ga		gamba ga		kango ga		bata gq		edea cm		mbengwi cm		wukari ng		bauchi ng		azare ng		goure ne		tanout ne		agadez ne		arlit ne		gat ly		nalut ly		qabis tn		harqalah tn		manzil jamil tn		tortoli it		porto-vecchio fr		lerici it		sondrio it		bad wurzach de		werneck de		bad salzdetfurth de		neumunster de		stilling dk		hirtshals dk		vikersund no		folldal no		olden no		rorvik no		sorland no		barentsburg sj		bredasdorp za		hermanus za		cape town za		saldanha za		oranjemund na		luderitz na		walvis bay na		henties bay na		opuwo na		namibe ao		benguela ao		luanda ao		soyo ao		loubomo cg		mbigou ga		booue ga		bitam ga		mfou cm		banyo cm		tignere cm		numan ng		damaturu ng		maine-soroa ne		goure ne		bilma ne		gat ly		awbari ly		mizdah ly		jadu ly		jarjis tn		tabulbah tn		marsala it		anzio it		cerveteri it		bertinoro it		valdobbiadene it		grafing de		wunsiedel de		zerbst de		bad doberan de		frederiksvaerk dk		kungalv se		skotterud no		roros no		klaebu no		bronnoysund no		sorland no		gravdal no		barentsburg sj		bredasdorp za		hermanus za		cape town za		saldanha za		oranjemund na		luderitz na		walvis bay na		henties bay na		khorixas na		opuwo na		lubango ao		caluquembe ao		lobito ao		sumbe ao		caxito ao		matadi cd		madingou cg		lekoni ga		okandja ga		sembe cg		batouri cm		betare oya cm		tchollire cm		guider cm		bama ng		mao td		bilma ne		marzuq ly		sabha ly		mizdah ly		bani walid ly		tripoli ly		san lawrenz mt		cefalu it		sorrento it		sulmona it		ancona it		idrija si		vorchdorf at		kraluv dvur cz		lubben de		wolgast de		kristianstad se		jonkoping se		kristinehamn se		ostersund se		korgen no		stamsund no		stokmarknes no		andenes no		barentsburg sj		longyearbyen sj		bredasdorp za		hermanus za		cape town za		saldanha za		oranjemund na		luderitz na		rehoboth na		karibib na		outjo na		ondangwa na		ondjiva ao		caconda ao		huambo ao		malanje ao		camabatela ao		kasongo-lunda cd		brazzaville cg		gamboma cg		owando cg		ouesso cg		berberati cf		baoro cf		bol td		lai td		dourbali td		moussoro td		mao td		faya td		bilma ne		marzuq ly		sabha ly		hun ly		waddan ly		misratah ly		pachino it		melito di porto salvo it		lauria it		vieste it		knin hr		zagreb hr		berndorf at		holice cz		wolsztyn pl		bialogard pl		karlskrona se		linkoping se		fagersta se		bollnas se		ostersund se		rognan no		kjopsvik no		andenes no		longyearbyen sj		bredasdorp za		hermanus za		cape town za		vredendal za		springbok za		karasburg na		keetmanshoop na		mariental na		gobabis na		grootfontein na		tsumeb na		menongue ao		camacupa ao		malanje ao		kasongo-lunda cd		kikwit cd		bulungu cd		inongo cd		mbandaka cd		impfondo cg		mbaiki cf		bouca cf		moissala td		goundi td		bitkine td		ati td		faya td		marzuq ly		waddan ly		surt ly		benghazi ly		locri it		crotone it		gallipoli it		dubrovnik hr		gromiljak ba		szentlorinc hu		kolarovo sk		stepankovice cz		pleszew pl		koscierzyna pl		wladyslawowo pl		visby se		uppsala se		harnosand se		ornskoldsvik se		beisfjord no		finnsnes no		tromso no		longyearbyen sj		bredasdorp za		robertson za		calvinia za		karasburg na		bokspits bw		aranos na		gobabis na		grootfontein na		rundu na		luena ao		saurimo ao		lucapa ao		tshikapa cd		mangai cd		inongo cd		boende cd		binga cd		bosobolo cd		grimari cf		ndele cf		am timan td		oum hadjer td		biltine td		faya td		jalu ly		awjilah ly		ajdabiya ly		benghazi ly		tukrah ly		methoni gr		lixourion gr		delvine al		fushe-arrez al		kosjeric rs		kanjiza rs		matranovak hu		wieliczka pl		lowicz pl		morag pl		primore ru		pavilosta lv		maarianhamina fi		kristiinankaupunki fi		umea se		skelleftea se		kiruna se		lyngseidet no		skjervoy no		longyearbyen sj		bredasdorp za		george za		oudtshoorn za		carnarvon za		prieska za		upington za		tsabong bw		tshane bw		dekar bw		nokaneng bw		shakawe bw		kalabo zm		lumeje ao		luau ao		lucapa ao		kananga cd		mweka cd		lodja cd		boende cd		bumba cd		kembe cf		bria cf		ouadda cf		birao cf		adre td		biltine td		faya td		jalu ly		darnah ly		koroni gr		kalavrita gr		kranea elassonos gr		sveti nikole mk		bogovina rs		ohaba lunga ro		levelek hu		rzeszow pl		siedlce pl		gizycko pl		plunge lt		salme ee		parainen fi		noormarkku fi		pietarsaari fi		boden se		kautokeino no		oksfjord no		hammerfest no		longyearbyen sj		bredasdorp za		plettenberg bay za		graaff-reinet za		de aar za		danielskuil za		werda bw		dutlwe bw		tsienyane bw		maun bw		kachikau bw		senanga zm		kabompo zm		mwinilunga zm		kamina cd		kaniama cd		mbuji-mayi cd		lodja cd		yangambi cd		aketi cd		bondo cd		rafai cf		ouadda cf		birao cf		kutum sd		faya td		jalu ly		bardiyah ly		tubruq ly		palaiokhora gr		ayia marina gr		rafina gr		sikea gr		velingrad bg		marsani ro		cenade ro		bocicoiu mare ro		zhovkva ua		zabinka by		druskininkai lt		linkuva lt		tostamaa ee		lohja fi		kangasala fi		ylivieska fi		tornio fi		kautokeino no		rypefjord no		havoysund no		longyearbyen sj		bredasdorp za		kruisfontein za		port elizabeth za		cradock za		bloemfontein za		hoopstad za		lichtenburg za		boatlaname bw		moiyabana bw		nata bw		victoria falls zw		namwala zm		kasempa zm		solwezi zm		bukama cd		lubao cd		kampene cd		kindu cd		kisangani cd		buta cd		zemio cf		obo cf		raga sd		umm kaddadah sd		kutum sd		marawi sd		asyut eg		abnub eg		marsa matruh eg		bardiyah ly		koutsouras gr		astipalaia gr		piryion gr		canakkale tr		harmanli bg		daia ro		cernat ro		musenita ro		lanivtsi ua		pinsk by		navahrudak by		subate lv		torva ee		loviisa fi		jyvaskyla fi		muhos fi		rovaniemi fi		karasjok no		honningsvag no		longyearbyen sj		bredasdorp za		kruisfontein za		port elizabeth za		port alfred za		east london za		butterworth za		quthing ls		bethlehem za		midrand za		ellisras za		tobane bw		bulawayo zw		sinazongwe zm		mazabuka zm		mpongwe zm		chililabombwe zm		mwense zm		manono cd		kabalo cd		uvira cd		kabare cd		butembo cd		wamba cd		yambio sd		tambura sd		waw sd		babanusah sd		umm kaddadah sd		marawi sd		tahta eg		abnub eg		matay eg		marsa matruh eg		karpathos gr		lardos gr		odemis tr		susurluk tr		ahtopol bg		dumbraveni ro		suceveni ro		drochia md		chudniv ua		lyuban by		minsk by		zilupe lv		seredka ru		narva-joesuu ee		varkaus fi		kajaani fi		kemijarvi fi		mehamn no		longyearbyen sj		kruisfontein za		port elizabeth za		port alfred za		east london za		umzimvubu za		richmond za		glencoe za		breyten za		tzaneen za		beitbridge zw		shurugwi zw		chegutu zw		luangwa zm		mkushi zm		samfya zm		luwingu zm		kaputa zm		kalemie cd		rutana bi		kigali rw		kilembe ug		bunia cd		yei sd		yirol sd		ler sd		talawdi sd		abu zabad sd		bara sd		marawi sd		aswan eg		esna eg		asyut eg		matay eg		madinat sittah uktubar eg		rosetta eg		kumluca tr		dinar tr		bozuyuk tr		agva tr		sfantu gheorghe ro		kulevcha ua		zavallya ua		fastiv ua		lyubech ua		orsha by		nevel ru		dno ru		lisiy nos ru		lakhdenpokhya ru		lieksa fi		kuusamo fi		kovdor ru		vadso no		batsfjord no		berlevag no		mehamn no		port elizabeth za		port alfred za		east london za		umzimvubu za		margate za		ballitoville za		ulundi za		mhlume sz		phalaborwa za		chiredzi zw		chipinge zw		marondera zw		mount darwin zw		katete zm		mpika zm		chinsali zm		sumbawanga tz		inyonga tz		masumbwe tz		muleba tz		lukaya ug		masindi ug		moyo ug		juba sd		malakal sd		marabba sd		umm jarr sd		umm durman sd		marawi sd		aswan eg		el balyana eg		abnub eg		suez eg		damietta eg		pafos cy		alanya tr		beysehir tr		gerede tr		zonguldak tr		zaozerne ua		bekhtery ua		kompaniyivka ua		drabiv ua		shchors ua		khislavichi ru		zapadnaya dvina ru		parfino ru		novaya ladoga ru		suoyarvi ru		muyezerskiy ru		zelenoborskiy ru		verkhnetulomskiy ru		pechenga ru		vardo no		berlevag no		port elizabeth za		port alfred za		east london za		umzimvubu za		margate za		durban za		richards bay za		xai-xai mz		manjacaze mz		chipinge zw		dondo mz		chimoio mz		tete mz		lilongwe mw		mzimba mw		karonga mw		dunda tz		mgandu tz		igurubi tz		nyamuswa tz		port victoria ke		katakwi ug		kaabong ug		kapoeta sd		gambela et		asosa et		galgani sd		sinnar sd		wad rawah sd		barbar sd		aswan eg		safaga eg		hurghada eg		mizpe ramon il		ashqelon il		dromolaxia cy		silifke tr		aksaray tr		sungurlu tr		kastamonu tr		katsiveli ua		voyinka ua		sofiyivka ua		velyka bahachka ua		druzhba ua		betlitsa ru		sychevka ru		berezayka ru		boksitogorsk ru		shuya ru		nadvoitsy ru		umba ru		kirovsk ru		polyarnyy ru		skalistyy ru		vardo no		berlevag no		port elizabeth za		port alfred za		east london za		umzimvubu za		margate za		scottsburgh za		richards bay za		xai-xai mz		inhambane mz		beira mz		quelimane mz		phalombe mw		mangochi mw		tingi tz		mahanje tz		ilula tz		msanga tz		magugu tz		magadi ke		rongai ke		amudat ug		lodwar ke		bako et		gore et		nedjo et		bahir dar et		doka sd		wagar sd		sinkat sd		sawakin sd		umm lajj sa		tabuk sa		wadi musa jo		jawa jo		riyaq lb		samandag tr		goksun tr		zile tr		bafra tr		ordzhonikidze ua		novyy svit ua		novomykolayivka ua		peresichna ua		fatezh ru		sosenskiy ru		volokolamsk ru		maksatikha ru		vytegra ru		pudozh ru		solovetskiy ru		tumannyy ru		vardo no		port elizabeth za		port alfred za		east london za		umzimvubu za		margate za		port shepstone za		richards bay za		inhambane mz		quelimane mz		mocuba mz		montepuez mz		masuguru tz		liwale tz		kisanga tz		lugoba tz		kisiwani tz		wote ke		maua ke		marsabit ke		mega et		dilla et		butajira et		dejen et		debre tabor et		aksum et		barentu er		tawkar sd		sawakin sd		jiddah sa		umm lajj sa		tabuk sa		bayir jo		turayf sa		yabrud sy		manbij sy		malatya tr		susehri tr		ordu tr		divnomorskoye ru		primorsko-akhtarsk ru		vysoke ua		urazovo ru		volovo ru		brusyanskiy ru		fryazino ru		novyy nekouz ru		lipin bor ru		kargopol ru		onega ru		ostrovnoy ru		tumannyy ru		vardo no		port elizabeth za		port alfred za		east london za		umzimvubu za		margate za		richards bay za		beloha mg		ampanihy mg		toliary mg		mocuba mz		angoche mz		nacala mz		pemba mz		lindi tz		kilindoni tz		sokoni tz		mombasa ke		witu ke		garissa ke		wajir ke		moyale et		goba et		robe et		abomsa et		korem et		adwa et		ginda er		tawkar sd		mecca sa		umm lajj sa		sakakah sa		turayf sa		abu kamal sy		viransehir tr		ergani tr		bayburt tr		trabzon tr		kamennomostskiy ru		novoleushkovskaya ru		almaznyy ru		mitrofanovka ru		verkhnyaya khava ru		korablino ru		sobinka ru		danilov ru		kharovsk ru		shalakusha ru		kodino ru		severodvinsk ru		ostrovnoy ru		tumannyy ru		port alfred za		east london za		umzimvubu za		margate za		tsihombe mg		beloha mg		ampanihy mg		toliary mg		morondava mg		angoche mz		mocambique mz		nacala mz		moroni km		madimba tz		kilindoni tz		chake chake tz		malindi ke		bur gabo so		afmadu so		dujuma so		mandera ke		ginir et		harer et		dire dawa et		asayita et		edd er		jizan sa		abha sa		mecca sa		buraydah sa		sakakah sa		hit iq		rawah iq		sinjar iq		siirt tr		horasan tr		naruja ge		dzheguta ru		gorodovikovsk ru		tsimlyansk ru		alekseyevskaya ru		rzhaksa ru		shatsk ru		nikologory ru		ostrovskoye ru		verkhovazhye ru		shenkursk ru		lukovetskiy ru		ostrovnoy ru		belushya guba ru		port alfred za		east london za		umzimvubu za		margate za		tsihombe mg		beloha mg		betioky mg		ankazoabo mg		morondava mg		miandrivazo mg		mahajanga mg		boueni yt		fomboni km		mitsamiouli km		micheweni tz		bur gabo so		kismayo so		barawe so		xuddur so		hargeysa so		jibuti dj		jiblah ye		sayyan ye		najran sa		abha sa		riyadh sa		buraydah sa		baghdad iq		balad iq		irbil iq		hakkari tr		janfida am		gori ge		sovetskaya ru		arshan ru		oktyabrskiy ru		danilovka ru		rtishchevo ru		kovylkino ru		dalneye konstantinovo ru		makaryev ru		nyuksenitsa ru		mirnyy ru		karpogory ru		kamenka ru		ostrovnoy ru		belushya guba ru		port alfred za		east london za		umzimvubu za		tsihombe mg		ambovombe mg		amboasary mg		ihosy mg		miandrivazo mg		fenoarivo mg		mahajanga mg		bandrele yt		dzaoudzi yt		domoni km		mitsamiouli km		bur gabo so		barawe so		mogadishu so		mahadday weyne so		hobyo so		odweyne so		berbera so		aden ye		lahij ye		sayyan ye		najran sa		riyadh sa		doha kw		mehran ir		mandali iq		baneh ir		azar shahr ir		istisu az		bezhta ru		terekli-mekteb ru		komsomolskiy ru		chernyy yar ru		kamyshin ru		novyye burasy ru		bolshiye berezniki ru		vasilsursk ru		vetluga ru		kichmengskiy gorodok ru		krasnoborsk ru		leshukonskoye ru		mezen ru		belushya guba ru		port alfred za		east london za		tsihombe mg		taolanaro mg		vangaindrano mg		manakara mg		marolambo mg		anjozorobe mg		tsaratanana mg		ambanja mg		ambilobe mg		mutsamudu km		barawe so		mogadishu so		jawhar so		hobyo so		garowe so		bosaso so		sayyan ye		najran sa		riyadh sa		buqayq sa		bayan kw		abadan ir		shush ir		alashtar ir		bijar ir		ardabil ir		imisli az		khuchni ru		makhachkala ru		kamyzyak ru		tambovka ru		novouzensk ru		balakovo ru		bolshiye klyuchishchi ru		zvenigovo ru		tuzha ru		zarya ru		urdoma ru		blagoyevo ru		leshukonskoye ru		belushya guba ru		port alfred za		east london za		tsihombe mg		taolanaro mg		farafangana mg		mananjary mg		mahanoro mg		toamasina mg		mananara mg		sambava mg		ambilobe mg		victoria sc		mogadishu so		hobyo so		eyl so		bandarbeyla so		qandala so		bereda so		salalah om		abu samrah qa		buqayq sa		bushehr ir		hendijan ir		masjed-e soleyman ir		arak ir		qazvin ir		astaneh-ye ashrafiyeh ir		zig az		gilazi az		fort-shevchenko kz		marfino ru		inderborskiy kz		ozinki ru		perelyub ru		novaya malykla ru		arsk ru		kumeny ru		raduzhnyy ru		mikun ru		koslan ru		ust-tsilma ru		naryan-mar ru		belushya guba ru		port alfred za		east london za		tsihombe mg		taolanaro mg		farafangana mg		saint-leu re		andevoranto mg		ambodifototra mg		antalaha mg		sambava mg		ambilobe mg		victoria sc		hobyo so		eyl so		bandarbeyla so		bereda so		salalah om		abu samrah qa		doha qa		khor qa		khormuj ir		kazerun ir		shahreza ir		kashan ir		damavand ir		fereydun kenar ir		gurgan az		kuryk kz		shetpe kz		balykshi kz		inderborskiy kz		zachagansk kz		kurmanayevka ru		kamyshla ru		grakhovo ru		yukamenskoye ru		lesnoy ru		kortkeros ru		sindor ru		ust-tsilma ru		naryan-mar ru		belushya guba ru		port alfred za		east london za		taolanaro mg		saint-joseph re		saint-pierre re		saint-leu re		le port re		antalaha mg		sambava mg		victoria sc		hobyo so		eyl so		bandarbeyla so		bargal so		bereda so		salalah om		abu dhabi ae		bandar-e lengeh ir		gerash ir		fasa ir		meybod ir		semnan ir		damghan ir		bandar-e torkaman ir		balkanabat tm		zhanaozen kz		karaton kz		makat kz		chingirlau kz		perevolotskiy ru		priyutovo ru		agidel ru		kez ru		gayny ru		ust-kulom ru		sosnogorsk ru		shchelyayur ru		iskateley ru		belushya guba ru		port alfred za		east london za		taolanaro mg		saint-joseph re		saint-philippe re		sainte-suzanne re		grand baie mu		cap malheureux mu		antalaha mg		sambava mg		victoria sc		eyl so		bandarbeyla so		bargal so		bereda so		salalah om		nizwa om		dubai ae		sharjah ae		qeshm ir		rafsanjan ir		bafq ir		tabas ir		shahrud ir		kalaleh ir		gazanjyk tm		beyneu kz		shubarkuduk kz		matveyevka ru		tolbazy ru		starobaltachevo ru		kondratovo ru		kerchevskiy ru		troitsko-pechorsk ru		nizhniy odes ru		puteyets ru		usinsk ru		iskateley ru		belushya guba ru		port alfred za		east london za		taolanaro mg		saint-philippe re		souillac mu		roches noires mu		cap malheureux mu		victoria sc		bandarbeyla so		bargal so		salalah om		ibra om		ruwi om		minab ir		jiroft ir		bam ir		ravar ir		tabas ir		sabzevar ir		buzmeyin tm		baherden tm		akdepe tm		kegayli uz		shubarshi kz		emba kz		khromtau kz		buribay ru		lomovka ru		bolsheustikinskoye ru		lysva ru		severnyy-kospashskiy ru		nyrob ru		vuktyl ru		usinsk ru		amderma ru		belushya guba ru		east london za		taolanaro mg		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		grand gaube mu		cap malheureux mu		victoria sc		bandarbeyla so		bargal so		salalah om		sur om		qurayyat om		chabahar ir		iranshahr ir		zabol ir		birjand ir		taybad ir		mashhad ir		kaka tm		hazorasp uz		mangit uz		karauzyak uz		kazalinsk kz		emba kz		dombarovskiy ru		krasnoyarskiy ru		uyskoye ru		nizhniy ufaley ru		nizhniy tagil ru		volchansk ru		polunochnoye ru		inta ru		amderma ru		belushya guba ru		east london za		taolanaro mg		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		quatre cocos mu		grand gaube mu		victoria sc		ugoofaaru mv		kavaratti in		salalah om		sur om		jiwani pk		gwadar pk		khash ir		mirabad af		farah af		herat af		sarakhs ir		murgab tm		seydi tm		gazojak tm		kazalinsk kz		svetlyy ru		lisakovsk kz		bobrovka ru		martyush ru		verkhnyaya sinyachikha ru		gari ru		pelym ru		agirish ru		verkhnyaya inta ru		amderma ru		taolanaro mg		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		quatre cocos mu		grand gaube mu		victoria sc		thinadhoo mv		kudahuvadhoo mv		mahibadhoo mv		ugoofaaru mv		kavaratti in		porbandar in		sur om		ormara pk		pasni pk		dalbandin pk		geresk af		sahrak af		dawlatabad af		sayat tm		romitan uz		gazli uz		dzhusaly kz		kushmurun kz		borovskoy kz		kargapolye ru		turinsk ru		uray ru		zelenoborsk ru		igrim ru		muzhi ru		severnyy ru		amderma ru		taolanaro mg		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		quatre cocos mu		grand gaube mu		hithadhoo mv		thinadhoo mv		kudahuvadhoo mv		mahibadhoo mv		ugoofaaru mv		kavaratti in		veraval in		porbandar in		dwarka in		keti bandar pk		karachi pk		bela pk		surab pk		nushki pk		qandahar af		panjab af		sar-e pul af		qarqin af		aktash uz		nurota uz		shieli kz		tasbuget kz		zhezkazgan kz		derzhavinsk kz		esil kz		polovinnoye ru		uporovo ru		nizhnyaya tavda ru		lugovoy ru		oktyabrskoye ru		andra ru		labytnangi ru		kharp ru		sovetskiy ru		severnyy ru		amderma ru		taolanaro mg		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		quatre cocos mu		grand gaube mu		hithadhoo mv		thinadhoo mv		kudahuvadhoo mv		mahibadhoo mv		ugoofaaru mv		dhidhdhoo mv		kavaratti in		ratnagiri in		veraval in		porbandar in		dwarka in		jati pk		sann pk		garhi khairo pk		harnai pk		sharan af		gardan diwal af		aybak af		denau uz		zomin uz		chardara kz		kentau kz		zhezkazgan kz		atbasar kz		sergeyevka kz		armizonskoye ru		tobolsk ru		kondinskoye ru		oktyabrskoye ru		aksarka ru		sovetskiy ru		amderma ru		dikson ru		taolanaro mg		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		quatre cocos mu		hithadhoo mv		thinadhoo mv		kudahuvadhoo mv		mahibadhoo mv		ugoofaaru mv		dhidhdhoo mv		kavaratti in		malwan in		ratnagiri in		diu in		veraval in		lalpur in		diplo pk		chor pk		ubauro pk		barkhan pk		tank pk		azrow af		andarab af		leningradskiy tj		chkalovsk tj		lenger kz		zhanatas kz		atasu kz		astana kz		makinsk kz		krasnoarmeysk kz		ishim ru		vagay ru		gornopravdinsk ru		nadym ru		yar-sale ru		dikson ru		taolanaro mg		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		quatre cocos mu		hithadhoo mv		thinadhoo mv		kudahuvadhoo mv		mahibadhoo mv		ugoofaaru mv		dhidhdhoo mv		kavaratti in		kankon in		malwan in		srivardhan in		chinchani in		dhola in		patan in		balotra in		phalodi in		mailsi pk		mitha tiwana pk		nowshera pk		chitral pk		karakendzha tj		stantsiya gorchakovo uz		talas kg		mikhaylovka kz		saryshagan kz		atasu kz		shakhtinsk kz		stepnogorsk kz		poltavka ru		tyukalinsk ru		tevriz ru		salym ru		cheuskiny ru		muravlenko ru		nadym ru		yar-sale ru		dikson ru		busselton au		taolanaro mg		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		hithadhoo mv		viligili mv		hithadhoo mv		male mv		manadhoo mv		dhidhdhoo mv		kavaratti in		kannangad in		honavar in		savantvadi in		wai in		ojhar in		kavant in		salumbar in		raipur in		bhadasar in		ganganagar in		kamoke pk		uri in		gilgit pk		hunza pk		ozgon kg		toktogul kg		shu kz		saryshagan kz		gulshat kz		aktau kz		ereymentau kz		russkaya polyana ru		kolosovka ru		znamenskoye ru		surgut ru		muravlenko ru		pangody ru		yar-sale ru		dikson ru		busselton au		saint-philippe re		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		hithadhoo mv		viligili mv		muli mv		male mv		manavalakurichi in		varkkallai in		kochi in		ponnampet in		channagiri in		hungund in		tuljapur in		deulgaon raja in		bhikangaon in		susner in		tonk in		narnaul in		dirba in		talwara in		kargil in		hunza pk		shache cn		kashi cn		kemin kg		boralday kz		balkhash kz		karkaralinsk kz		maykain kz		kachiry kz		ust-tarka ru		sedelnikovo ru		megion ru		novoagansk ru		gubkinskiy ru		novyy urengoy ru		tazovskiy ru		dikson ru		busselton au		souillac mu		mahebourg mu		bambous virieux mu		grand river south east mu		hithadhoo mv		viligili mv		muli mv		galle lk		moratuwa lk		udankudi in		sholavandan in		pennagaram in		kadiri in		alampur in		medak in		digras in		amla in		bamora in		antri in		aligarh in		haridwar in		sarahan in		leh in		shache cn		kyzyl-suu kg		saryozek kz		ushtobe kz		ayagoz kz		semey kz		aksu kz		karasuk ru		severnoye ru		kedrovyy ru		strezhevoy ru		tarko-sale ru		urengoy ru		tazovskiy ru		dikson ru		busselton au		mahebourg mu		bambous virieux mu		grand river south east mu		hithadhoo mv		matara lk		weligama lk		galle lk		anuradhapura lk		valvedditturai lk		pondicherry in		nayudupeta in		addanki in		mahbubabad in		mul in		waraseoni in		pawai in		kurara in		pawayan in		bageshwar in		gangotri in		leh in		shache cn		aksu cn		zharkent kz		sarkand kz		ayagoz kz		semey kz		mikhaylovskoye ru		pankrushikha ru		ubinskoye ru		kedrovyy ru		kargasok ru		strezhevoy ru		tarko-sale ru		urengoy ru		tazovskiy ru		dikson ru		busselton au		mahebourg mu		bambous virieux mu		grand river south east mu		hithadhoo mv		matara lk		hambantota lk		batticaloa lk		mullaitivu lk		mamallapuram in		kattivakkam in		razole in		chitrakonda in		umarkot in		bilaspur in		sidhi in		pratapgarh in		bhinga in		jumla np		dharchula in		joshimath in		leh in		aksu cn		kuche cn		yining cn		urdzhar kz		glubokoe kz		pospelikha ru		suzun ru		kolyvan ru		podgornoye ru		parabel ru		kargasok ru		krasnoselkup ru		karaul ru		dikson ru		busselton au		bambous virieux mu		grand river south east mu		hithadhoo mv		hambantota lk		kalmunai lk		trincomalee lk		madras in		amalapuram in		yarada in		srikakulam in		udayagiri in		sundargarh in		daltenganj in		sikandarpur in		waling np		pokhara np		jumla np		kuche cn		kuytun cn		karamay cn		kurchum kz		zyryanovsk kz		petropavlovskoye ru		pervomayskoye ru		kozhevnikovo ru		molchanovo ru		belyy yar ru		krasnoselkup ru		karaul ru		dikson ru		busselton au		geraldton au		carnarvon au		bengkulu id		hithadhoo mv		hambantota lk		wattegama lk		kalmunai lk		batticaloa lk		kattivakkam in		yarada in		narasannapeta in		gopalpur in		nimaparha in		rairangpur in		hesla in		darbhanga in		banepa np		kathmandu np		pokhara np		jumla np		korla cn		shihezi cn		baijiantan cn		zaysan kz		ust-koksa ru		gorno-altaysk ru		guryevsk ru		anzhero-sudzhensk ru		pervomayskoye ru		belyy yar ru		turukhansk ru		igarka ru		dudinka ru		dikson ru		albany au		busselton au		geraldton au		carnarvon au		bengkulu id		padang id		meulaboh id		hambantota lk		kalmunai lk		port blair in		puri in		paradwip in		haldia in		kandi in		kishanganj in		mangan in		lasa cn		korla cn		urumqi cn		altay cn		aktash ru		tashtagol ru		mezhdurechensk ru		suslovo ru		teguldet ru		turukhansk ru		snezhnogorsk ru		talnakh ru		dikson ru		albany au		busselton au		geraldton au		carnarvon au		bengkulu id		padang id		meulaboh id		banda aceh id		sabang id		port blair in		labutta mm		akyab mm		mathbaria bd		mirzapur bd		dhuburi in		gasa bt		lasa cn		korla cn		urumqi cn		altay cn		mugur-aksy ru		abaza ru		sorsk ru		nazarovo ru		novobirilyussy ru		teya ru		turukhansk ru		svetlogorsk ru		talnakh ru		dikson ru		albany au		busselton au		geraldton au		carnarvon au		labuhan id		bengkulu id		padang id		sibolga id		meulaboh id		banda aceh id		sabang id		port blair in		labutta mm		akyab mm		bandarban bd		kamalpur in		nongpoh in		tawang in		lasa cn		hami cn		ulaangom mn		chaa-khol ru		sayanskiy ru		divnogorsk ru		pirovskoye ru		teya ru		svetlogorsk ru		talnakh ru		dikson ru		albany au		busselton au		geraldton au		carnarvon au		palabuhanratu id		labuhan id		bengkulu id		padang id		sibolga id		meulaboh id		banda aceh id		sabang id		port blair in		labutta mm		myanaung mm		minbu mm		falam mm		churachandpur in		bokajan in		ziro in		along in		lasa cn		yumen cn		hami cn		erzin ru		samagaltay ru		turan ru		koshurnikovo ru		shalinskoye ru		kazachinskoye ru		severo-yeniseyskiy ru		baykit ru		svetlogorsk ru		talnakh ru		khatanga ru		albany au		busselton au		geraldton au		carnarvon au		palabuhanratu id		labuhan id		bengkulu id		padang id		sibolga id		meulaboh id		sigli id		sabang id		ranong th		mergui mm		dawei mm		pyapon mm		letpadan mm		pyinmana mm		mandalay mm		katha mm		khonsa in		tezu in		pasighat in		along in		yumen cn		hami cn		erzin ru		toora-khem ru		ilanskiy ru		motygino ru		baykit ru		tura ru		khatanga ru		albany au		busselton au		geraldton au		carnarvon au		palabuhanratu id		labuhan id		bengkulu id		padang id		sibolga id		langsa id		lhokseumawe id		kathu th		ranong th		mergui mm		dawei mm		mudon mm		pa sang th		mae hong son th		lashio mm		banmo mm		myitkyina mm		tezu in		xining cn		jiuquan cn		yumen cn		moron mn		kungurtug ru		nizhneudinsk ru		tayshet ru		boguchany ru		baykit ru		tura ru		khatanga ru		albany au		busselton au		geraldton au		carnarvon au		palabuhanratu id		labuhan id		bengkulu id		padang id		payakumbuh id		rantauprapat id		lumut my		kuala kedah my		ron phibun th		ko samui th		kui buri th		bang len th		khanu woralaksaburi th		den chai th		chiang rai th		yunjinghong cn		simao cn		dali cn		panzhihua cn		yaan cn		xining cn		zhangye cn		jiuquan cn		hovd mn		moron mn		orlik ru		tulun ru		chunskiy ru		kodinsk ru		tura ru		khatanga ru		albany au		busselton au		geraldton au		carnarvon au		palabuhanratu id		labuhan id		pringsewu id		bengkulu id		sungaipenuh id		sijunjung id		sungai udang my		kuala lipis my		sungai kolok th		yaring th		ko samui th		laem sing th		sa kaeo th		chaiyaphum th		nam som th		luang prabang la		dien bien vn		zhoucheng cn		panzhihua cn		xichang cn		yaan cn		linqiong cn		linxia cn		xining cn		jinchang cn		hovd mn		bulgan mn		zakamensk ru		kyren ru		zima ru		bratsk ru		ust-ilimsk ru		vanavara ru		tura ru		khatanga ru		albany au		busselton au		geraldton au		carnarvon au		palabuhanratu id		labuhan id		pringsewu id		baturaja id		jambi id		kijang id		kota tinggi my		cukai my		kuala terengganu my		ca mau vn		kampot kh		pousat kh		phrai bung th		selaphum th		seka th		xam nua la		lao cai vn		zhongshu cn		rongcheng cn		zhaotong cn		leshan cn		jiangyou cn		linxia cn		lanzhou cn		wuwei cn		jinchang cn		hovd mn		bulgan mn		kholtoson ru		bolshoy lug ru		osa ru		shestakovo ru		rudnogorsk ru		vanavara ru		tura ru		khatanga ru		albany au		busselton au		geraldton au		carnarvon au		kawalu id		banjar id		palabuhanratu id		cilegon id		metro id		mentok id		kijang id		cukai my		paka my		bac lieu vn		can tho vn		kracheh kh		champasak la		saravan la		ha tinh vn		ninh binh vn		bac can vn		bose cn		anshun cn		tongzi cn		heyang cn		baoning cn		beidao cn		pingliang cn		yinchuan cn		shitanjing cn		haibowan cn		mandalgovi mn		ulaanbaatar mn		suhbaatar mn		istok ru		kachug ru		ust-kut ru		yerbogachen ru		khatanga ru		albany au		busselton au		geraldton au		carnarvon au		bambanglipuro id		srandakan id		kroya id		kawalu id		pamanukan id		manggar id		sungairaya id		pemangkat id		bac lieu vn		vung tau vn		phan thiet vn		da lat vn		play cu vn		da nang vn		dong hoi vn		cam pha vn		qinzhou cn		jinchengjiang cn		xiaoweizhai cn		tongzi cn		fuling cn		daxian cn		yuxia cn		pingliang cn		yinchuan cn		haibowan cn		mandalgovi mn		darhan mn		ulaanbaatar mn		bichura ru		onokhoy ru		khuzhir ru		kazachinskoye ru		kirensk ru		yerbogachen ru		aykhal ru		khatanga ru		albany au		busselton au		geraldton au		carnarvon au		karratha au		bambanglipuro id		srandakan id		mlonggo id		manggar id		pangkalanbuun id		pontianak id		kuching my		sibu my		phan thiet vn		phan rang vn		nha trang vn		qui nhon vn		quang ngai vn		wanning cn		lingao cn		yashan cn		luorong cn		guilin cn		jishou cn		enshi cn		shiyan cn		weinan cn		yanan cn		dongsheng cn		hohhot cn		erenhot cn		darhan mn		ondorhaan mn		krasnyy chikoy ru		kizhinga ru		kurumkan ru		kichera ru		alekseyevsk ru		yerbogachen ru		aykhal ru		saskylakh ru		albany au		busselton au		geraldton au		carnarvon au		karratha au		gondanglegi id		kanigoro id		tulungagung id		lasem id		pangkalanbuun id		sri aman my		sibu my		bintulu my		miri my		phan rang vn		nha trang vn		qui nhon vn		wanning cn		qiongshan cn		tangping cn		huaicheng cn		yongzhou cn		loudi cn		nanhai cn		xiangfan cn		yima cn		linfen cn		taiyuan cn		hohhot cn		erenhot cn		baruun-urt mn		ondorhaan mn		kyra ru		mogzon ru		sosnovo-ozerskoye ru		yanchukan ru		sogdiondon ru		vitim ru		chernyshevskiy ru		aykhal ru		udachnyy ru		saskylakh ru		albany au		busselton au		kwinana au		geraldton au		carnarvon au		karratha au		denpasar id		muncar id		bondowoso id		sumenep id		banjarmasin id		kualakapuas id		kapit my		miri my		labuan my		kota kinabalu my		taburi ph		candawaga ph		qui nhon vn		wanning cn		zhuhai cn		yingcheng cn		xiongzhou cn		pingxiang cn		puqi cn		xinyang cn		xuchang cn		hebi cn		luancheng cn		datong cn		jining cn		erenhot cn		baruun-urt mn		aksha ru		makkaveyevo ru		bagdarin ru		severomuysk ru		mamakan ru		lensk ru		mirnyy ru		udachnyy ru		saskylakh ru		albany au		collie au		perth au		northam au		geraldton au		carnarvon au		karratha au		praya id		mataram id		singaraja id		martapura id		barabai id		loa janan id		tarakan id		limbang my		kota kinabalu my		balabac ph		panalingaan ph		tagusao ph		cabra ph		aloleng ph		catuday ph		jieshi cn		rongcheng cn		ganzhou cn		linchuan cn		huangmei cn		gushi cn		bozhou cn		yanggu cn		hengshui cn		mentougou cn		zhangjiakou cn		mujiayingzi cn		baruun-urt mn		zabaykalsk ru		sherlovaya gora ru		shilka ru		bukachacha ru		taksimo ru		kropotkin ru		lensk ru		suntar ru		almaznyy ru		nyurba ru		udachnyy ru		saskylakh ru		albany au		northam au		geraldton au		roebourne au		port hedland au		waingapu id		sumbawa id		galesong id		majene id		balikpapan id		bontang id		tarakan id		tawau my		sandakan my		rio tuba ph		aporawan ph		bacuit ph		cabra ph		aloleng ph		puro ph		davila ph		haimen cn		shima cn		sanming cn		shangrao cn		tunxi cn		chaohu cn		suicheng cn		nanma cn		binzhou cn		fengrun cn		mujiayingzi cn		chifeng cn		hailar cn		manzhouli cn		krasnokamensk ru		sretensk ru		ksenyevka ru		chara ru		suntar ru		nyurba ru		saskylakh ru		new norfolk au		albany au		esperance au		northam au		port hedland au		broome au		waingapu id		ruteng id		tanete id		singkang id		poso id		palu id		tarakan id		manuk mangkaw ph		pandan niog ph		simbahan ph		osmena ph		salvacion ph		cabra ph		paitan ph		sinait ph		davila ph		tungkang tw		erhlin tw		rongcheng cn		lishui cn		fuyang cn		taixing cn		dongkan cn		jiaonan cn		longkou cn		qinhuangdao cn		chaoyang cn		chifeng cn		wulanhaote cn		hailar cn		nerchinskiy zavod ru		mogocha ru		khani ru		verkhnevilyuysk ru		zhigansk ru		saskylakh ru		new norfolk au		albany au		esperance au		port hedland au		broome au		kupang id		ende id		maumere id		katobu id		kendari id		luwuk id		gorontalo id		latung ph		tabialan ph		siocon ph		magdalena ph		caticlan ph		alabat ph		dumabato ph		awallan ph		basco ph		taitung tw		suao tw		keelung tw		wenling cn		dinghai cn		huilong cn		dafeng cn		wencheng cn		weihai cn		xiongyue cn		heishan cn		tongliao cn		wulanhaote cn		zalantun cn		genhe cn		yerofey pavlovich ru		khani ru		vilyuysk ru		zhigansk ru		tiksi ru		new norfolk au		albany au		esperance au		yulara au		broome au		kupang id		soe id		atambua id		katobu id		kendari id		luwuk id		gorontalo id		manado id		sarangani ph		palimbang ph		munai ph		clarin ph		cataingan ph		caramoran ph		dicabisagan ph		basco ph		ishigaki jp		shenjiamen cn		huilong cn		yatou cn		dandong cn		fushun cn		zhengjiatun cn		tailai cn		gannan cn		alihe cn		tahe cn		skovorodino ru		zolotinka ru		serebryanyy bor ru		nizhniy kuranakh ru		kysyl-syr ru		zhigansk ru		tiksi ru		new norfolk au		albany au		esperance au		yulara au		broome au		kununurra au		soe id		atambua id		ambon id		tidore id		bitung id		sarangani ph		lamidan ph		santa josefa ph		san benito ph		dapdap ph		gigmoto ph		pandan ph		dicabisagan ph		basco ph		hirara jp		yomitan jp		shenjiamen cn		fukue jp		seoul kr		huanren cn		erdaojiang cn		jiutai cn		zhaodong cn		keshan cn		nenjiang cn		ushumun ru		magdagachi ru		zolotinka ru		lebedinyy ru		tommot ru		berdigestyakh ru		sangar ru		zhigansk ru		tiksi ru		new norfolk au		portland au		mount gambier au		port lincoln au		esperance au		flinders au		yulara au		kununurra au		port keats au		nguiu au		atambua id		ambon id		amahai id		tidore id		ternate id		sarangani ph		pundaguitan ph		kinablangan ph		union ph		sulangan ph		alugan ph		gigmoto ph		pandan ph		hirara jp		itoman jp		nishihara jp		nago jp		naze jp		fukue jp		seoul kr		linjiang cn		songjianghe cn		huangnihe cn		binzhou cn		cuiluan cn		tambovka ru		shimanovsk ru		zeya ru		tommot ru		mokhsogollokh ru		sangar ru		batagay-alyta ru		tiksi ru		hobart au		new norfolk au		portland au		mount gambier au		port lincoln au		flinders au		yulara au		kununurra au		port keats au		nguiu au		tual id		amahai id		sorong id		ternate id		san isidro ph		baculin ph		bacolod ph		sulangan ph		san policarpo ph		alugan ph		payo ph		itoman jp		nishihara jp		nago jp		naze jp		kaseda jp		ushibuka jp		maebaru jp		nagato jp		seoul kr		khasan ru		ningan cn		yilan cn		xinqing cn		novobureyskiy ru		fevralsk ru		chagda ru		nizhniy bestyakh ru		namtsy ru		batagay-alyta ru		tiksi ru		hobart au		new norfolk au		portland au		mount gambier au		port lincoln au		flinders au		yulara au		alice springs au		katherine au		jabiru au		nguiu au		tual id		sorong id		kloulklubed pw		meyungs pw		san policarpo ph		gigmoto ph		nishihara jp		gushikawa jp		naze jp		kushima jp		shintomi jp		hikari jp		oda jp		izumo jp		khasan ru		shkotovo-22 ru		vozdvizhenka ru		baoqing cn		babstovo ru		tyrma ru		stoyba ru		tokur ru		chagda ru		amga ru		churapcha ru		borogontsy ru		verkhoyansk ru		batagay-alyta ru		tiksi ru		hobart au		new norfolk au		portland au		mount gambier au		port lincoln au		flinders au		yulara au		alice springs au		ngukurr au		maningrida au		tual id		nabire id		manokwari id		kloulklubed pw		meyungs pw		nishihara jp		naze jp		kushima jp		nichinan jp		muroto jp		waki jp		tottori jp		vrangel ru		preobrazheniye ru		chuguyevka ru		dalnerechensk ru		smidovich ru		litovko ru		sofiysk ru		zlatoustovsk ru		chumikan ru		ust-maya ru		churapcha ru		khandyga ru		verkhoyansk ru		batagay ru		ust-kuyga ru		nizhneyansk ru		hobart au		new norfolk au		portland au		mount gambier au		victor harbor au		port lincoln au		port augusta au		alice springs au		mount isa au		ngukurr au		alyangula au		galiwinku au		tual id		nabire id		biak id		kloulklubed pw		airai pw		nishihara jp		naze jp		muroto jp		shingu jp		kumano jp		sabae jp		wajima jp		olga ru		rudnaya pristan ru		vostok ru		mukhen ru		elban ru		berezovyy ru		chumikan ru		ayan ru		eldikan ru		dzhebariki-khaya ru		khandyga ru		batagay ru		ust-kuyga ru		nizhneyansk ru		hobart au		new norfolk au		portland au		mount gambier au		victor harbor au		port pirie au		port augusta au		alice springs au		mount isa au		alyangula au		nhulunbuy au		merauke id		kiunga pg		nabire id		biak id		airai pw		naze jp		shingu jp		oyama jp		tatsuno jp		ryotsu jp		oga jp		kamiiso jp		terney ru		svetlaya ru		gurskoye ru		gorin ru		mnogovershinnyy ru		ayan ru		solnechnyy ru		khandyga ru		batagay ru		deputatskiy ru		nizhneyansk ru		hobart au		new norfolk au		burnie au		portland au		mount gambier au		murray bridge au		broken hill au		mount isa au		alyangula au		nhulunbuy au		merauke id		kiunga pg		vanimo pg		airai pw		naze jp		shingu jp		shimoda jp		tateyama jp		mitsukaido jp		nagai jp		tenno jp		kamiiso jp		yoichi jp		svetlaya ru		sovetskaya gavan ru		vysokogornyy ru		bogorodskoye ru		mnogovershinnyy ru		ayan ru		solnechnyy ru		ust-nera ru		khonuu ru		deputatskiy ru		nizhneyansk ru		hobart au		new norfolk au		burnie au		warrnambool au		hamilton au		horsham au		mildura au		broken hill au		mount isa au		atherton au		mareeba au		daru pg		morehead pg		kiunga pg		ambunti pg		vanimo pg		airai pw		shimoda jp		tateyama jp		katsuura jp		hasaki jp		ishinomaki jp		miyako jp		shizunai jp		fukagawa jp		shebunino ru		ilinskiy ru		boshnyakovo ru		lazarev ru		okha ru		okhotsk ru		ust-nera ru		khonuu ru		deputatskiy ru		nizhneyansk ru		hobart au		new norfolk au		burnie au		colac au		geelong au		swan hill au		broken hill au		roma au		emerald au		charters towers au		atherton au		mareeba au		daru pg		balimo pg		mount hagen pg		angoram pg		wewak pg		aitape pg		lorengau pg		airai pw		shimoda jp		tateyama jp		katsuura jp		hasaki jp		kamaishi jp		miyako jp		kushiro jp		bihoro jp		novikovo ru		makarov ru		poronaysk ru		katangli ru		okha ru		okhotsk ru		artyk ru		ust-nera ru		khonuu ru		belaya gora ru		chokurdakh ru		hobart au		new norfolk au		ulverstone au		burnie au		warragul au		corowa au		griffith au		dubbo au		roma au		emerald au		charters towers au		innisfail au		cairns au		port moresby pg		kerema pg		kainantu pg		madang pg		lorengau pg		airai pw		katsuura jp		hasaki jp		kamaishi jp		nemuro jp		yuzhno-kurilsk ru		otradnoye ru		vostok ru		poronaysk ru		katangli ru		ekhabi ru		okha ru		okhotsk ru		kadykchan ru		artyk ru		belaya gora ru		chokurdakh ru		hobart au		launceston au		lakes entrance au		tumut au		young au		dubbo au		narrabri au		roma au		emerald au		moranbah au		bowen au		ayr au		cairns au		port moresby pg		popondetta pg		finschhafen pg		lorengau pg		airai pw		katsuura jp		hasaki jp		kamaishi jp		nemuro jp		kurilsk ru		vostok ru		ekhabi ru		arman ru		ust-omchug ru		kholodnyy ru		shirokiy ru		zyryanka ru		belaya gora ru		chokurdakh ru		bluff nz		hobart au		lakes entrance au		cooma au		batemans bay au		lithgow au		mudgee au		narrabri au		moree au		roma au		biloela au		mackay au		bowen au		innisfail au		samarai pg		alotau pg		kandrian pg		kimbe pg		kavieng pg		lorengau pg		airai pw		katsuura jp		hasaki jp		nemuro jp		sentyabrskiy ru		vostok ru		magadan ru		arman ru		yagodnoye ru		zyryanka ru		chokurdakh ru		bluff nz		hobart au		lakes entrance au		batemans bay au		ulladulla au		sydney au		taree au		armidale au		warwick au		kingaroy au		gladstone au		yeppoon au		mackay au		bowen au		samarai pg		alotau pg		kokopo pg		rabaul pg		kavieng pg		airai pw		katsuura jp		hasaki jp		nemuro jp		sentyabrskiy ru		vostok ru		oktyabrskiy ru		sobolevo ru		ola ru		orotukan ru		seymchan ru		zyryanka ru		srednekolymsk ru		chokurdakh ru		bluff nz		hobart au		batemans bay au		ulladulla au		kiama au		nelson bay au		port macquarie au		coffs harbour au		gold coast au		coolum beach au		hervey bay au		gladstone au		yeppoon au		mackay au		samarai pg		buin pg		panguna pg		namatanai pg		kavieng pg		katsuura jp		hasaki jp		sentyabrskiy ru		severo-kurilsk ru		oktyabrskiy ru		sobolevo ru		ola ru		talaya ru		dukat ru		seymchan ru		srednekolymsk ru		chokurdakh ru		bluff nz		tuatapere nz		hobart au		batemans bay au		ulladulla au		nelson bay au		port macquarie au		ballina au		byron bay au		kawana waters au		hervey bay au		bundaberg au		yeppoon au		samarai pg		gizo sb		kieta pg		namatanai pg		kavieng pg		katsuura jp		hasaki jp		sentyabrskiy ru		severo-kurilsk ru		oktyabrskiy ru		sobolevo ru		tigil ru		omsukchan ru		srednekolymsk ru		cherskiy ru		chokurdakh ru		bluff nz		tuatapere nz		te anau nz		ulladulla au		nelson bay au		port macquarie au		ballina au		byron bay au		kawana waters au		hervey bay au		poum nc		kirakira sb		honiara sb		gizo sb		kieta pg		namatanai pg		kavieng pg		butaritari ki		hasaki jp		sentyabrskiy ru		severo-kurilsk ru		petropavlovsk-kamchatskiy ru		yelizovo ru		esso ru		tigil ru		palana ru		evensk ru		omsukchan ru		cherskiy ru		bluff nz		tuatapere nz		te anau nz		nelson bay au		port macquarie au		sawtell au		byron bay au		gold coast au		koumac nc		poum nc		kirakira sb		honiara sb		buala sb		kieta pg		namatanai pg		butaritari ki		hasaki jp		sentyabrskiy ru		severo-kurilsk ru		petropavlovsk-kamchatskiy ru		milkovo ru		klyuchi ru		palana ru		evensk ru		cherskiy ru		bluff nz		tuatapere nz		te anau nz		port macquarie au		ballina au		byron bay au		noumea nc		poya nc		voh nc		poum nc		kirakira sb		auki sb		buala sb		kieta pg		butaritari ki		hasaki jp		sentyabrskiy ru		severo-kurilsk ru		petropavlovsk-kamchatskiy ru		ust-kamchatsk ru		ossora ru		evensk ru		cherskiy ru		bluff nz		tuatapere nz		te anau nz		ahipara nz		noumea nc		bourail nc		voh nc		poum nc		luganville vu		lata sb		kirakira sb		auki sb		bairiki ki		butaritari ki		sentyabrskiy ru		severo-kurilsk ru		petropavlovsk-kamchatskiy ru		nikolskoye ru		ust-kamchatsk ru		ossora ru		kamenskoye ru		bilibino ru		cherskiy ru		pevek ru		bluff nz		tuatapere nz		te anau nz		wanaka nz		westport nz		ahipara nz		vao nc		noumea nc		bouloupari nc		fayaoue nc		vila vu		luganville vu		sola vu		lata sb		tabiauea ki		bairiki ki		butaritari ki		sentyabrskiy ru		severo-kurilsk ru		nikolskoye ru		tilichiki ru		kamenskoye ru		bilibino ru		pevek ru		bluff nz		otautau nz		wanaka nz		westport nz		ahipara nz		vao nc		tadine nc		we nc		vila vu		lakatoro vu		sola vu		lata sb		tabiauea ki		butaritari ki		severo-kurilsk ru		nikolskoye ru		tilichiki ru		kamenskoye ru		bilibino ru		pevek ru		bluff nz		kaitangata nz		milton nz		fairlie nz		hokitika nz		westport nz		karamea nz		ahipara nz		vao nc		tadine nc		isangel vu		vila vu		sola vu		lata sb		lolua tv		utiroa ki		tabiauea ki		buariki ki		butaritari ki		severo-kurilsk ru		nikolskoye ru		tilichiki ru		kamenskoye ru		pevek ru		bluff nz		kaitangata nz		dunedin nz		waitati nz		rakaia nz		reefton nz		takaka nz		okato nz		ahipara nz		vao nc		isangel vu		vila vu		sola vu		lolua tv		utiroa ki		temaraia ki		tabiauea ki		taburao ki		butaritari ki		nikolskoye ru		tilichiki ru		kamenskoye ru		komsomolskiy ru		pevek ru		bluff nz		kaitangata nz		dunedin nz		lincoln nz		christchurch nz		seddon nz		manaia nz		kawhia nz		dargaville nz		kaeo nz		vao nc		isangel vu		sola vu		asau tv		lolua tv		ijaki ki		utiroa ki		temaraia ki		rawannawi ki		butaritari ki		nikolskoye ru		beringovskiy ru		anadyr ru		komsomolskiy ru		pevek ru		bluff nz		kaitangata nz		dunedin nz		christchurch nz		waipawa nz		takapau nz		mamaku nz		whitianga nz		ngunguru nz		russell nz		kaeo nz		vao nc		isangel vu		asau tv		lolua tv		ijaki ki		tabukiniberu ki		rawannawi ki		butaritari ki		nikolskoye ru		beringovskiy ru		anadyr ru		leningradskiy ru		bluff nz		kaitangata nz		dunedin nz		christchurch nz		waipawa nz		otane nz		wairoa nz		ruatoria nz		whitianga nz		ngunguru nz		russell nz		kaeo nz		isangel vu		asau tv		lolua tv		rungata ki		rawannawi ki		butaritari ki		nikolskoye ru		beringovskiy ru		anadyr ru		leningradskiy ru		DONE!



```python
#cities = list(set(cities))

```


```python
url = 'http://api.openweathermap.org/data/2.5/weather?q='
for city in cities:
    sleep(.1)
    #print(city)
    #w_dat = requests.get(url + city + ',' + country_code + '&apikey=' + OWP_key).json()
    w_dat = requests.get(url + city['name'] + ',' + city['country'] + '&apikey=' + OWP_key).json()
    try:
        #print(w_dat['main']['temp_max'])
        city['temp'] = w_dat['main']['temp_max']
        city['lat'] = w_dat['coord']['lat']
        city['lng'] = w_dat['coord']['lon']
        city['hum'] = w_dat['main']['humidity']
        city['wind'] = w_dat['wind']['speed']
        city['clouds'] = w_dat['clouds']['all']
        print(city['name'], end = '\t')
    except KeyError:
        print(f'{city["name"]} not found', end = '\t')
print(w_dat)   
```

    vaini not found	halalo not found	vaitupu not found	kapaa not found	provideniya not found	egvekinot not found	mys shmidta not found	vaini not found	neiafu not found	halalo not found	vaitupu not found	kapaa not found	provideniya not found	egvekinot not found	mys shmidta not found	vaini not found	neiafu not found	hihifo not found	halalo not found	vaitupu not found	kapaa not found	provideniya not found	egvekinot not found	mys shmidta not found	vaini not found	pangai not found	neiafu not found	hihifo not found	falealupo not found	sataua not found	vaitupu not found	kapaa not found	provideniya not found	lavrentiya not found	mys shmidta not found	vaini not found	pangai not found	alofi not found	neiafu not found	hihifo not found	pata not found	saleaula not found	kapaa not found	bethel not found	provideniya not found	lavrentiya not found	mys shmidta not found	vaini not found	alofi not found	satitoa not found	samusu not found	samalaeulu not found	saleaula not found	kapaa not found	bethel not found	provideniya not found	lavrentiya not found	mys shmidta not found	barrow not found	mataura not found	vaini not found	alofi not found	satitoa not found	samusu not found	samalaeulu not found	saleaula not found	nanakuli not found	kapaa not found	bethel not found	nome not found	lavrentiya not found	barrow not found	mataura not found	avarua not found	alofi not found	satitoa not found	samusu not found	samalaeulu not found	saleaula not found	makakilo city not found	kapaa not found	bethel not found	nome not found	barrow not found	mataura not found	avarua not found	alofi not found	satitoa not found	samusu not found	lufilufi not found	samalaeulu not found	hilo not found	makakilo city not found	kapaa not found	bethel not found	nome not found	barrow not found	mataura not found	avarua not found	samusu not found	hilo not found	makakilo city not found	nanakuli not found	kapaa not found	kodiak not found	bethel not found	nome not found	barrow not found	mataura not found	avarua not found	faanui not found	samusu not found	hilo not found	ewa beach not found	makakilo city not found	kapaa not found	kodiak not found	bethel not found	barrow not found	mataura not found	avarua not found	faanui not found	hilo not found	lahaina not found	honolulu not found	wahiawa not found	kapaa not found	kodiak not found	bethel not found	barrow not found	mataura not found	avera not found	avarua not found	vaitape not found	faanui not found	hilo not found	kihei not found	kahului not found	kailua not found	ahuimanu not found	kapaa not found	kodiak not found	kenai not found	barrow not found	mataura not found	avera not found	vaitape not found	faanui not found	hilo not found	kahului not found	kailua not found	ahuimanu not found	kapaa not found	kodiak not found	homer not found	kenai not found	barrow not found	mataura not found	avera not found	moerai not found	tevaitoa not found	faanui not found	atuona not found	hilo not found	kahului not found	kailua not found	ahuimanu not found	kapaa not found	kodiak not found	homer not found	kenai not found	anchorage not found	college not found	barrow not found	mataura not found	moerai not found	teahupoo not found	haapiti not found	fare not found	faanui not found	atuona not found	hilo not found	kahului not found	kodiak not found	homer not found	sterling not found	wasilla not found	college not found	barrow not found	mataura not found	teahupoo not found	tautira not found	tiarei not found	fare not found	atuona not found	hilo not found	kahului not found	kodiak not found	anchorage not found	palmer not found	college not found	barrow not found	mataura not found	tautira not found	tiarei not found	atuona not found	hilo not found	kahului not found	kodiak not found	palmer not found	fairbanks not found	college not found	barrow not found	mataura not found	tautira not found	atuona not found	hilo not found	kahului not found	fortuna not found	sitka not found	palmer not found	fairbanks not found	aklavik not found	barrow not found	mataura not found	rikitea not found	tautira not found	atuona not found	hilo not found	fortuna not found	sitka not found	haines junction not found	fairbanks not found	aklavik not found	tuktoyaktuk not found	rikitea not found	atuona not found	hilo not found	fortuna not found	port hardy not found	sitka not found	haines junction not found	mayo not found	aklavik not found	tuktoyaktuk not found	rikitea not found	atuona not found	hilo not found	half moon bay not found	fortuna not found	port hardy not found	ketchikan not found	sitka not found	haines junction not found	mayo not found	aklavik not found	tuktoyaktuk not found	rikitea not found	atuona not found	hilo not found	lompoc not found	pacific grove not found	half moon bay not found	fortuna not found	north bend not found	port hardy not found	prince rupert not found	ketchikan not found	sitka not found	whitehorse not found	mayo not found	aklavik not found	tuktoyaktuk not found	rikitea not found	atuona not found	hilo not found	lompoc not found	pacific grove not found	half moon bay not found	fortuna not found	north bend not found	port hardy not found	prince rupert not found	ketchikan not found	sitka not found	juneau not found	whitehorse not found	mayo not found	inuvik not found	tuktoyaktuk not found	rikitea not found	atuona not found	guerrero negro not found	lompoc not found	pacific grove not found	half moon bay not found	pacifica not found	fortuna not found	coos bay not found	north bend not found	port hardy not found	prince rupert not found	ketchikan not found	juneau not found	whitehorse not found	mayo not found	inuvik not found	tuktoyaktuk not found	rikitea not found	atuona not found	constitucion not found	guerrero negro not found	san quintin not found	lompoc not found	pacific grove not found	half moon bay not found	fortuna not found	coos bay not found	north bend not found	port hardy not found	prince rupert not found	ketchikan not found	juneau not found	norman wells not found	tuktoyaktuk not found	rikitea not found	atuona not found	constitucion not found	guerrero negro not found	san quintin not found	lompoc not found	pacific grove not found	half moon bay not found	ukiah not found	fortuna not found	eureka not found	north bend not found	ucluelet not found	port hardy not found	kitimat not found	smithers not found	norman wells not found	tuktoyaktuk not found	punta arenas not found	rikitea not found	atuona not found	cabo san lucas not found	constitucion not found	guerrero negro not found	san quintin not found	lompoc not found	pacific grove not found	half moon bay not found	ukiah not found	fortuna not found	eureka not found	north bend not found	astoria not found	ucluelet not found	campbell river not found	port hardy not found	burns lake not found	smithers not found	fort nelson not found	norman wells not found	tuktoyaktuk not found	punta arenas not found	rikitea not found	atuona not found	cabo san lucas not found	constitucion not found	guerrero negro not found	san quintin not found	lompoc not found	pacific grove not found	half moon bay not found	healdsburg not found	fortuna not found	grants pass not found	north bend not found	astoria not found	sooke not found	powell river not found	quesnel not found	vanderhoof not found	mackenzie not found	fort nelson not found	norman wells not found	tuktoyaktuk not found	punta arenas not found	rikitea not found	atuona not found	cabo san lucas not found	constitucion not found	guerrero negro not found	san quintin not found	lompoc not found	monterey not found	concord not found	red bluff not found	klamath falls not found	bend not found	washougal not found	west lake stevens not found	lillooet not found	williams lake not found	prince george not found	fort saint john not found	fort nelson not found	norman wells not found	tuktoyaktuk not found	punta arenas not found	rikitea not found	atuona not found	cabo san lucas not found	constitucion not found	guerrero negro not found	san quintin not found	rosarito not found	port hueneme not found	isla vista not found	avenal not found	merced not found	sun valley not found	susanville not found	redmond not found	grandview not found	east wenatchee bench not found	peachland not found	chase not found	beaverlodge not found	dawson creek not found	fort saint john not found	fort nelson not found	hay river not found	yellowknife not found	norman wells not found	tuktoyaktuk not found	punta arenas not found	rikitea not found	atuona not found	san patricio not found	cabo san lucas not found	constitucion not found	guerrero negro not found	san quintin not found	rosarito not found	hacienda heights not found	ridgecrest not found	fallon not found	winnemucca not found	baker city not found	walla walla not found	cheney not found	nakusp not found	jasper not found	hinton not found	fairview not found	high level not found	hay river not found	yellowknife not found	norman wells not found	tuktoyaktuk not found	punta arenas not found	rikitea not found	atuona not found	san patricio not found	cabo san lucas not found	constitucion not found	guerrero negro not found	san quintin not found	ensenada not found	twentynine palms not found	pahrump not found	elko not found	mountain home not found	garden city not found	lewiston not found	sandpoint not found	kimberley not found	banff not found	whitecourt not found	high prairie not found	high level not found	hay river not found	yellowknife not found	norman wells not found	punta arenas not found	rikitea not found	puerto ayora not found	coahuayana not found	san patricio not found	cabo san lucas not found	constitucion not found	guerrero negro not found	san felipe not found	fortuna foothills not found	lake havasu city not found	kingman not found	saint george not found	west wendover not found	burley not found	hailey not found	hamilton not found	polson not found	claresholm not found	penhold not found	westlock not found	slave lake not found	hay river not found	yellowknife not found	punta arenas not found	castro not found	rikitea not found	puerto ayora not found	lazaro cardenas not found	coahuayana not found	san patricio not found	cabo san lucas not found	constitucion not found	loreto not found	santa rosalia not found	pitiquito not found	sonoita not found	paradise valley not found	flagstaff not found	cedar city not found	payson not found	preston not found	rexburg not found	butte not found	great falls not found	taber not found	hanna not found	two hills not found	athabasca not found	yellowknife not found	punta arenas not found	castro not found	rikitea not found	puerto ayora not found	ixtapa not found	lazaro cardenas not found	coahuayana not found	san patricio not found	tomatlan not found	cabo san lucas not found	la paz not found	ahome not found	cocorit not found	cumpas not found	sierra vista not found	show low not found	winslow not found	cortez not found	price not found	green river not found	jackson not found	livingston not found	havre not found	maple creek not found	macklin not found	grand centre not found	yellowknife not found	punta arenas not found	castro not found	rikitea not found	puerto ayora not found	ixtapa not found	lazaro cardenas not found	coahuayana not found	san patricio not found	tomatlan not found	mazatlan not found	eldorado not found	sinaloa not found	creel not found	benito juarez not found	deming not found	socorro not found	bloomfield not found	montrose not found	craig not found	rawlins not found	worland not found	billings not found	shaunavon not found	swift current not found	biggar not found	meadow lake not found	la ronge not found	yellowknife not found	punta arenas not found	castro not found	ancud not found	lebu not found	rikitea not found	puerto ayora not found	acapulco not found	san jeronimo not found	ixtapa not found	lazaro cardenas not found	coahuayana not found	san patricio not found	tomatlan not found	teacapan not found	tayoltita not found	santa maria del oro not found	santa cruz de rosales not found	ahumada not found	socorro not found	ruidoso not found	espanola not found	alamosa not found	boulder not found	laramie not found	gillette not found	miles city not found	glendive not found	assiniboia not found	watrous not found	prince albert not found	la ronge not found	yellowknife not found	punta arenas not found	castro not found	ancud not found	lebu not found	puerto ayora not found	acapulco not found	san jeronimo not found	ixtapa not found	lazaro cardenas not found	la orilla not found	coahuayana not found	juchitlan not found	villa guerrero not found	vicente guerrero not found	mapimi not found	camargo not found	ojinaga not found	carlsbad not found	portales not found	tucumcari not found	pueblo not found	fort morgan not found	torrington not found	spearfish not found	glendive not found	sidney not found	weyburn not found	wadena not found	nipawin not found	la ronge not found	yellowknife not found	punta arenas not found	castro not found	ancud not found	lebu not found	pisco not found	puerto ayora not found	tecoanapa not found	acapulco not found	san jeronimo not found	petatlan not found	la union not found	tlazazalca not found	palo alto not found	canitas not found	parras not found	muzquiz not found	del rio not found	midland not found	plainview not found	dumas not found	lamar not found	sterling not found	north platte not found	rapid valley not found	dickinson not found	minot not found	moosomin not found	kamsack not found	flin flon not found	thompson not found	yellowknife not found	punta arenas not found	castro not found	ancud not found	lebu not found	pisco not found	puerto ayora not found	puerto escondido not found	tecoanapa not found	acapulco not found	apaxtla not found	temascalcingo not found	fernandez not found	doctor arroyo not found	marin not found	nuevo laredo not found	uvalde not found	abilene not found	vernon not found	woodward not found	dodge city not found	lexington not found	north platte not found	pierre not found	bismarck not found	devils lake not found	brandon not found	dauphin not found	the pas not found	thompson not found	yellowknife not found	punta arenas not found	castro not found	ancud not found	lebu not found	pisco not found	puerto ayora not found	pochutla not found	puerto escondido not found	huazolotitlan not found	acatlan not found	zacatlan not found	panuco not found	soto la marina not found	rio bravo not found	alice not found	kyle not found	stephenville not found	wichita falls not found	enid not found	hutchinson not found	hastings not found	norfolk not found	mitchell not found	aberdeen not found	grafton not found	carman not found	gimli not found	thompson not found	yellowknife not found	punta arenas not found	castro not found	ancud not found	lebu not found	pisco not found	hualmay not found	puerto ayora not found	champerico not found	pochutla not found	xadani not found	loma bonita not found	emilio carranza not found	tamiahua not found	nuevo progreso not found	brownsville not found	port lavaca not found	katy not found	athens not found	durant not found	jenks not found	emporia not found	beatrice not found	south sioux city not found	marshall not found	fergus falls not found	grand forks not found	pinawa not found	gimli not found	thompson not found	qaanaaq not found	punta arenas not found	castro not found	ancud not found	lebu not found	pisco not found	hualmay not found	puerto ayora not found	champerico not found	ocos not found	puerto madero not found	paredon not found	las choapas not found	paraiso not found	vega de alatorre not found	matamoros not found	freeport not found	galveston not found	nederland not found	bossier city not found	hope not found	fayetteville not found	clinton not found	excelsior springs not found	boone not found	mankato not found	brainerd not found	fort frances not found	kenora not found	thompson not found	qaanaaq not found	ushuaia not found	punta arenas not found	castro not found	ancud not found	lebu not found	pisco not found	hualmay not found	huarmey not found	san cristobal not found	puerto ayora not found	acajutla not found	san jose not found	champerico not found	la trinitaria not found	jonuta not found	sabancuy not found	celestun not found	morgan city not found	abbeville not found	monroe not found	pine bluff not found	batesville not found	rolla not found	quincy not found	cedar rapids not found	winona not found	superior not found	atikokan not found	sioux lookout not found	thompson not found	qaanaaq not found	ushuaia not found	punta arenas not found	castro not found	ancud not found	lebu not found	coquimbo not found	marcona not found	pisco not found	hualmay not found	huarmey not found	chicama not found	san cristobal not found	puerto ayora not found	santa cruz not found	la libertad not found	acajutla not found	conguaco not found	chisec not found	escarcega not found	hecelchakan not found	progreso not found	houma not found	chalmette not found	brandon not found	grenada not found	blytheville not found	waterloo not found	jacksonville not found	clinton not found	wisconsin rapids not found	merrill not found	thunder bay not found	sioux lookout not found	thompson not found	qaanaaq not found	ushuaia not found	punta arenas not found	castro not found	ancud not found	lebu not found	coquimbo not found	marcona not found	pisco not found	hualmay not found	huarmey not found	pimentel not found	sechura not found	san cristobal not found	puerto baquerizo moreno not found	nicoya not found	santa cruz not found	san rafael del sur not found	corinto not found	la florida not found	puerto cortes not found	san pedro not found	felipe carrillo puerto not found	panaba not found	estelle not found	pascagoula not found	fairhope not found	meridian not found	columbus not found	paris not found	henderson not found	urbana not found	elk grove village not found	manitowoc not found	marquette not found	terrace bay not found	geraldton not found	attawapiskat not found	thompson not found	qaanaaq not found	ushuaia not found	punta arenas not found	castro not found	ancud not found	lebu not found	coquimbo not found	marcona not found	pisco not found	hualmay not found	huarmey not found	chicama not found	sechura not found	paita not found	talara not found	san cristobal not found	burica not found	nicoya not found	santa cruz not found	granada not found	trojes not found	puerto castilla not found	savannah bight not found	cozumel not found	isla mujeres not found	mantua not found	saint pete beach not found	panama city not found	troy not found	gadsden not found	lebanon not found	radcliff not found	noblesville not found	granger not found	big rapids not found	escanaba not found	marathon not found	longlac not found	attawapiskat not found	clyde river not found	qaanaaq not found	ushuaia not found	punta arenas not found	castro not found	ancud not found	lebu not found	coquimbo not found	marcona not found	pisco not found	lima not found	hualmay not found	chimbote not found	chicama not found	sechura not found	paita not found	talara not found	salinas not found	manta not found	muisne not found	burica not found	buenos aires not found	san isidro not found	bluefields not found	rosita not found	barra patuca not found	santa fe not found	guane not found	bahia honda not found	south venice not found	clearwater not found	tallahassee not found	cordele not found	lawrenceville not found	knoxville not found	winchester not found	tipp city not found	adrian not found	bay city not found	thessalon not found	chapleau not found	hearst not found	attawapiskat not found	clyde river not found	qaanaaq not found	ushuaia not found	punta arenas not found	coihaique not found	castro not found	ancud not found	lebu not found	talcahuano not found	coquimbo not found	marcona not found	pisco not found	hualmay not found	huarmey not found	santiago de cao not found	pimentel not found	sechura not found	el alto not found	salinas not found	manta not found	muisne not found	la palma not found	remedios not found	bocas del toro not found	san andres not found	puerto cabezas not found	iralaya not found	george town not found	west bay not found	batabano not found	key west not found	naples not found	winston not found	lakeside not found	jesup not found	greenwood not found	boone not found	saint albans not found	zanesville not found	blenheim not found	goderich not found	little current not found	timmins not found	kapuskasing not found	attawapiskat not found	clyde river not found	qaanaaq not found	ushuaia not found	punta arenas not found	coihaique not found	castro not found	ancud not found	lebu not found	constitucion not found	coquimbo not found	antofagasta not found	marcona not found	pisco not found	lima not found	hualmay not found	chimbote not found	chicama not found	olmos not found	alamor not found	el triunfo not found	pedernales not found	esmeraldas not found	mosquera not found	la palma not found	guarare not found	portobelo not found	san andres not found	black river not found	bodden town not found	manicaragua not found	corralillo not found	aventura not found	sebastian not found	ormond beach not found	charleston not found	florence not found	high point not found	hollins not found	uniontown not found	erie not found	orangeville not found	sturgeon falls not found	kirkland lake not found	cochrane not found	moose factory not found	attawapiskat not found	iqaluit not found	clyde river not found	qaanaaq not found	ushuaia not found	punta arenas not found	coihaique not found	castro not found	ancud not found	lebu not found	talcahuano not found	valparaiso not found	coquimbo not found	taltal not found	antofagasta not found	marcona not found	pisco not found	chancay not found	huarmey not found	quiruvilca not found	chachapoyas not found	yantzaza not found	palora not found	cayambe not found	magui not found	litoral del san juan not found	mutis not found	el real de santa maria not found	ailigandi not found	tigre not found	bull savanna not found	black river not found	niquero not found	esmeralda not found	andros town not found	high rock not found	merritt island not found	georgetown not found	wilmington not found	rocky mount not found	culpeper not found	chambersburg not found	olean not found	colborne not found	deep river not found	malartic not found	matagami not found	moose factory not found	attawapiskat not found	iqaluit not found	clyde river not found	qaanaaq not found	ushuaia not found	punta arenas not found	coihaique not found	castro not found	ancud not found	valdivia not found	lebu not found	constitucion not found	valparaiso not found	coquimbo not found	taltal not found	antofagasta not found	tocopilla not found	camana not found	acari not found	marcona not found	subtanjalla not found	chicla not found	ambo not found	tocache not found	yurimaguas not found	barranca not found	palora not found	puerto asis not found	saladoblanco not found	tulua not found	salgar not found	tierralta not found	san onofre not found	puerto colombia not found	morant bay not found	el cobre not found	gibara not found	rock sound not found	dunmore town not found	marsh harbour not found	wilmington not found	havelock not found	elizabeth city not found	lexington park not found	coatesville not found	endicott not found	watertown not found	maniwaki not found	senneterre not found	chapais not found	moose factory not found	iqaluit not found	clyde river not found	qaanaaq not found	ushuaia not found	punta arenas not found	coihaique not found	castro not found	ancud not found	valdivia not found	lebu not found	talcahuano not found	constitucion not found	valparaiso not found	coquimbo not found	vallenar not found	taltal not found	antofagasta not found	tocopilla not found	ilo not found	camana not found	acari not found	tambo not found	ayna not found	satipo not found	pucallpa not found	requena not found	nauta not found	iquitos not found	puerto leguizamo not found	la macarena not found	acacias not found	florian not found	santa rosa del sur not found	bosconia not found	santa marta not found	riohacha not found	les cayes not found	baracoa not found	clarence town not found	cockburn town not found	marsh harbour not found	havelock not found	virginia beach not found	ocean city not found	point pleasant not found	kingston not found	glens falls not found	sainte-adele not found	la tuque not found	chapais not found	iqaluit not found	clyde river not found	qaanaaq not found	ushuaia not found	punta arenas not found	rio gallegos not found	coihaique not found	puerto montt not found	panguipulli not found	mulchen not found	parral not found	san antonio not found	la ligua not found	coquimbo not found	vallenar not found	taltal not found	antofagasta not found	tocopilla not found	iquique not found	ilo not found	lluta not found	santo tomas not found	pangoa not found	porto walter not found	cruzeiro do sul not found	ipixuna not found	iquitos not found	miraflores not found	calamar not found	puerto gaitan not found	paz de ariporo not found	san juan de colon not found	villa del rosario not found	uribia not found	manaure not found	pedernales not found	cap-haitien not found	cockburn harbour not found	cockburn town not found	marsh harbour not found	havelock not found	elizabeth city not found	virginia beach not found	brigantine not found	mastic beach not found	southbridge not found	haverhill not found	warwick not found	desbiens not found	dolbeau not found	chapais not found	iqaluit not found	clyde river not found	qaanaaq not found	ushuaia not found	punta arenas not found	rio gallegos not found	coihaique not found	san carlos de bariloche not found	neuquen not found	san clemente not found	machali not found	salamanca not found	vicuna not found	copiapo not found	diego de almagro not found	antofagasta not found	tocopilla not found	iquique not found	tacna not found	puno not found	macusani not found	iberia not found	manoel urbano not found	feijo not found	eirunepe not found	leticia not found	japura not found	mitu not found	cumaribo not found	cravo norte not found	barinas not found	carora not found	punto fijo not found	oranjestad not found	bani not found	bajos de haina not found	sosua not found	cockburn town not found	cockburn town not found	hamilton not found	nantucket not found	brewster not found	topsham not found	liniere not found	la malbaie not found	forestville not found	chute-aux-outardes not found	port-cartier not found	iqaluit not found	clyde river not found	narsaq not found	qaanaaq not found	ushuaia not found	rio gallegos not found	comodoro rivadavia not found	trelew not found	neuquen not found	san rafael not found	san juan not found	la rioja not found	diego de almagro not found	calama not found	uyuni not found	eucaliptus not found	coroico not found	rurrenabaque not found	cobija not found	rio branco not found	boca do acre not found	jutai not found	santo antonio do ica not found	tonantins not found	sao gabriel da cachoeira not found	inirida not found	puerto ayacucho not found	calabozo not found	tacarigua not found	kralendijk not found	rincon not found	guanica not found	rincon not found	samana not found	cockburn town not found	hamilton not found	nantucket not found	brewster not found	bar harbor not found	houlton not found	price not found	baie-comeau not found	port-cartier not found	sept-iles not found	iqaluit not found	pangnirtung not found	clyde river not found	narsaq not found	qaanaaq not found	ushuaia not found	rio gallegos not found	comodoro rivadavia not found	trelew not found	puerto madryn not found	general roca not found	santa rosa not found	mercedes not found	san luis not found	la rioja not found	catamarca not found	tucuman not found	jujuy not found	villazon not found	potosi not found	capinota not found	chimore not found	santa rosa not found	rodrigues alves not found	riberalta not found	pauini not found	carauari not found	fonte boa not found	santa isabel do rio negro not found	sao gabriel da cachoeira not found	inirida not found	puerto carreno not found	zaraza not found	altagracia de orituco not found	caraballeda not found	kralendijk not found	arroyo not found	patillas not found	san juan not found	hamilton not found	saint george not found	nantucket not found	shelburne not found	yarmouth not found	oromocto not found	new richmond not found	sept-iles not found	iqaluit not found	pangnirtung not found	clyde river not found	narsaq not found	qaanaaq not found	ushuaia not found	comodoro rivadavia not found	rawson not found	puerto madryn not found	viedma not found	santa rosa not found	general pico not found	rio cuarto not found	rio tercero not found	cordoba not found	santiago del estero not found	tucuman not found	libertador general san martin not found	yacuiba not found	monteagudo not found	mairana not found	ascension not found	san ramon not found	rodrigues alves not found	ariquemes not found	porto velho not found	canutama not found	coari not found	maraa not found	santa isabel do rio negro not found	boa vista not found	ciudad bolivar not found	cumana not found	la asuncion not found	barroualie not found	middle island not found	road town not found	hamilton not found	saint george not found	shelburne not found	liverpool not found	lunenburg not found	amherst not found	grande-riviere not found	havre-saint-pierre not found	iqaluit not found	pangnirtung not found	clyde river not found	narsaq not found	ushuaia not found	comodoro rivadavia not found	rawson not found	viedma not found	punta alta not found	bahia blanca not found	lincoln not found	venado tuerto not found	san francisco not found	rafaela not found	presidencia roque saenz pena not found	doctor pedro p. pena not found	mayor pablo lagerenza not found	pailon not found	san javier not found	rolim de moura not found	presidente medici not found	jaru not found	humaita not found	manicore not found	codajas not found	barcelos not found	boa vista not found	upata not found	point fortin not found	gouyave not found	canaries not found	vieux-habitants not found	codrington not found	the valley not found	hamilton not found	saint george not found	liverpool not found	halifax not found	antigonish not found	cap-aux-meules not found	havre-saint-pierre not found	saint-augustin not found	pangnirtung not found	upernavik not found	narsaq not found	ushuaia not found	rawson not found	viedma not found	tres arroyos not found	veinticinco de mayo not found	san pedro not found	parana not found	reconquista not found	resistencia not found	presidencia roque saenz pena not found	pozo colorado not found	filadelfia not found	mayor pablo lagerenza not found	san pedro not found	san rafael not found	vilhena not found	aripuana not found	novo aripuana not found	borba not found	manaus not found	boa vista not found	lethem not found	bartica not found	mabaruma not found	rio claro not found	scarborough not found	crab hill not found	saint-francois not found	codrington not found	the valley not found	hamilton not found	saint george not found	port hawkesbury not found	louisbourg not found	channel-port aux basques not found	saint-augustin not found	pangnirtung not found	upernavik not found	narsaq not found	ushuaia not found	rawson not found	viedma not found	necochea not found	mar del plata not found	dolores not found	carmelo not found	paysandu not found	bella union not found	cerrito not found	villa oliva not found	concepcion not found	san lazaro not found	fuerte olimpo not found	puerto quijarro not found	caceres not found	nova olimpia not found	vilhena not found	alta floresta not found	jacareacanga not found	maues not found	urucara not found	bonfim not found	ituni not found	linden not found	georgetown not found	mabaruma not found	oistins not found	bathsheba not found	crab hill not found	saint-francois not found	codrington not found	saint george not found	louisbourg not found	burgeo not found	deer lake not found	saint-augustin not found	maniitsoq not found	sisimiut not found	upernavik not found	narsaq not found	ushuaia not found	rawson not found	necochea not found	mar del plata not found	paso de carrasco not found	florida not found	tacuarembo not found	alegrete not found	posadas not found	abai not found	lima not found	bela vista not found	miranda not found	coxim not found	santo antonio do leverger not found	diamantino not found	alta floresta not found	jacareacanga not found	itaituba not found	juruti not found	oriximina not found	grand-santi not found	brokopondo not found	totness not found	georgetown not found	oistins not found	bathsheba not found	saint-francois not found	codrington not found	saint george not found	saint-pierre not found	harbour breton not found	springdale not found	saint anthony not found	nuuk not found	maniitsoq not found	sisimiut not found	upernavik not found	ushuaia not found	rawson not found	necochea not found	mar del plata not found	maldonado not found	rocha not found	melo not found	santa maria not found	santo augusto not found	santo antonio do sudoeste not found	altonia not found	rio brilhante not found	campo verde not found	coxim not found	guiratinga not found	jaciara not found	alta floresta not found	sao felix do xingu not found	santarem not found	monte alegre not found	prainha not found	camopi not found	grand-santi not found	mana not found	marienburg not found	oistins not found	bathsheba not found	saint-francois not found	codrington not found	saint george not found	saint-pierre not found	marystown not found	carbonear not found	hare bay not found	saint anthony not found	paamiut not found	nuuk not found	maniitsoq not found	sisimiut not found	kangaatsiaq not found	aasiaat not found	upernavik not found	ushuaia not found	necochea not found	mar del plata not found	maldonado not found	rocha not found	chuy not found	santa vitoria do palmar not found	rio grande not found	butia not found	tapejara not found	pinhao not found	barbosa ferraz not found	presidente venceslau not found	tres lagoas not found	jatai not found	aragarcas not found	mozarlandia not found	sao miguel do araguaia not found	formoso do araguaia not found	sao felix do xingu not found	altamira not found	porto de moz not found	mazagao not found	amapa not found	saint-georges not found	kourou not found	sinnamary not found	iracoubo not found	mana not found	bathsheba not found	saint-francois not found	codrington not found	saint george not found	saint-pierre not found	bay roberts not found	torbay not found	bonavista not found	saint anthony not found	paamiut not found	nuuk not found	maniitsoq not found	aasiaat not found	ilulissat not found	upernavik not found	ushuaia not found	mar del plata not found	rocha not found	chuy not found	rio grande not found	palmares do sul not found	tramandai not found	sao joaquim not found	mafra not found	terra roxa not found	pompeia not found	cardoso not found	goiatuba not found	goias not found	crixas not found	formoso do araguaia not found	miranorte not found	conceicao do araguaia not found	itupiranga not found	tucurui not found	oeiras do para not found	tucuma not found	amapa not found	saint-georges not found	cayenne not found	sinnamary not found	iracoubo not found	bathsheba not found	codrington not found	saint george not found	torbay not found	bonavista not found	saint anthony not found	paamiut not found	nuuk not found	qasigiannguit not found	ilulissat not found	upernavik not found	ushuaia not found	mar del plata not found	rocha not found	chuy not found	rio grande not found	cidreira not found	laguna not found	florianopolis not found	pontal do parana not found	capao bonito not found	ibate not found	miguelopolis not found	catalao not found	brasilia not found	cavalcante not found	parana not found	palmas not found	araguaina not found	ananas not found	paragominas not found	acara not found	curuca not found	salinopolis not found	amapa not found	saint-georges not found	cayenne not found	sinnamary not found	bathsheba not found	saint-francois not found	codrington not found	saint george not found	torbay not found	bonavista not found	nanortalik not found	qaqortoq not found	paamiut not found	nuuk not found	qasigiannguit not found	ilulissat not found	upernavik not found	ushuaia not found	mar del plata not found	rocha not found	chuy not found	rio grande not found	cidreira not found	laguna not found	florianopolis not found	peruibe not found	guaruja not found	pouso alegre not found	bambui not found	joao pinheiro not found	arinos not found	posse not found	taguatinga not found	morros not found	balsas not found	grajau not found	santa ines not found	maracacume not found	viseu not found	salinopolis not found	saint-georges not found	cayenne not found	sinnamary not found	bathsheba not found	codrington not found	saint george not found	torbay not found	bonavista not found	nanortalik not found	qaqortoq not found	ilulissat not found	upernavik not found	ushuaia not found	mar del plata not found	rocha not found	chuy not found	rio grande not found	cidreira not found	laguna not found	imbituba not found	ilhabela not found	mangaratiba not found	lima duarte not found	ibirite not found	diamantina not found	sao joao da ponte not found	carinhanha not found	ibotirama not found	bom jesus not found	urucui not found	colinas not found	coroata not found	sao jose de ribamar not found	cururupu not found	carutapera not found	salinopolis not found	saint-georges not found	cayenne not found	sinnamary not found	bathsheba not found	codrington not found	ribeira grande not found	torbay not found	nanortalik not found	qaqortoq not found	tasiilaq not found	ilulissat not found	upernavik not found	ushuaia not found	mar del plata not found	rocha not found	chuy not found	cidreira not found	laguna not found	imbituba not found	arraial do cabo not found	itaocara not found	manhuacu not found	malacacheta not found	taiobeiras not found	livramento not found	ibipeba not found	remanso not found	simplicio mendes not found	elesbao veloso not found	batalha not found	tutoia not found	cururupu not found	carutapera not found	cayenne not found	ponta do sol not found	ribeira grande not found	torbay not found	nanortalik not found	tasiilaq not found	ilulissat not found	upernavik not found	ushuaia not found	mar del plata not found	rocha not found	chuy not found	cidreira not found	laguna not found	arraial do cabo not found	armacao dos buzios not found	sao joao da barra not found	serra not found	montanha not found	itarantim not found	jitauna not found	baixa grande not found	jaguarari not found	ouricuri not found	taua not found	iraucuba not found	acarau not found	carutapera not found	cayenne not found	porto novo not found	ponta do sol not found	ribeira grande not found	torbay not found	nanortalik not found	tasiilaq not found	ilulissat not found	ushuaia not found	mar del plata not found	rocha not found	chuy not found	cidreira not found	laguna not found	arraial do cabo not found	sao joao da barra not found	vila velha not found	linhares not found	caravelas not found	belmonte not found	marau not found	entre rios not found	jeremoabo not found	flores not found	umarizal not found	beberibe not found	jardim not found	itarema not found	sao filipe not found	porto novo not found	ponta do sol not found	ribeira grande not found	nanortalik not found	tasiilaq not found	ushuaia not found	mar del plata not found	rocha not found	chuy not found	cidreira not found	laguna not found	arraial do cabo not found	sao joao da barra not found	vila velha not found	caravelas not found	belmonte not found	camacari not found	aracaju not found	coruripe not found	toritama not found	sao tome not found	macau not found	aquiraz not found	caucaia not found	trairi not found	itarema not found	sao filipe not found	porto novo not found	ponta do sol not found	ribeira grande not found	lagoa not found	nanortalik not found	tasiilaq not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	laguna not found	arraial do cabo not found	sao joao da barra not found	vila velha not found	caravelas not found	belmonte not found	conde not found	coruripe not found	maragogi not found	olinda not found	nisia floresta not found	touros not found	aquiraz not found	jardim not found	trairi not found	sao filipe not found	porto novo not found	ponta do sol not found	ribeira grande not found	lagoa not found	nanortalik not found	tasiilaq not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	arraial do cabo not found	sao joao da barra not found	guarapari not found	vila velha not found	caravelas not found	belmonte not found	coruripe not found	maragogi not found	sao jose da coroa grande not found	itamaraca not found	cabedelo not found	touros not found	sao filipe not found	ponta do sol not found	ribeira grande not found	lagoa not found	tasiilaq not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	arraial do cabo not found	sao joao da barra not found	vila velha not found	caravelas not found	belmonte not found	coruripe not found	maceio not found	maragogi not found	olinda not found	pitimbu not found	cabedelo not found	natal not found	touros not found	sao filipe not found	porto novo not found	ponta do sol not found	ribeira grande not found	lagoa not found	grindavik not found	olafsvik not found	bolungarvik not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	arraial do cabo not found	sao joao da barra not found	vila velha not found	caravelas not found	belmonte not found	maceio not found	maragogi not found	sao jose da coroa grande not found	olinda not found	pitimbu not found	cabedelo not found	nisia floresta not found	touros not found	sao filipe not found	porto novo not found	ponta do sol not found	ponta delgada not found	horta not found	lagoa not found	grindavik not found	olafsvik not found	bolungarvik not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	arraial do cabo not found	sao joao da barra not found	vila velha not found	caravelas not found	maceio not found	maragogi not found	sao jose da coroa grande not found	olinda not found	pitimbu not found	cabedelo not found	natal not found	touros not found	sao filipe not found	mindelo not found	ponta do sol not found	los llanos de aridane not found	vila franca do campo not found	ponta delgada not found	arrifes not found	praia da vitoria not found	lagoa not found	grindavik not found	olafsvik not found	bolungarvik not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	arraial do cabo not found	sao joao da barra not found	vila velha not found	caravelas not found	georgetown not found	bubaque not found	sao filipe not found	praia not found	ribeira brava not found	pombas not found	ponta do sol not found	los llanos de aridane not found	vila franca do campo not found	praia da vitoria not found	lagoa not found	grindavik not found	olafsvik not found	bolungarvik not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	arraial do cabo not found	sao joao da barra not found	vila velha not found	caravelas not found	georgetown not found	goderich not found	bubaque not found	praia not found	vila do maio not found	sal rei not found	santa maria not found	nouadhibou not found	los llanos de aridane not found	ponta do sol not found	vila franca do campo not found	praia da vitoria not found	dingle not found	vestmannaeyjar not found	grindavik not found	kopavogur not found	stykkisholmur not found	bolungarvik not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	arraial do cabo not found	jamestown not found	georgetown not found	goderich not found	bubaque not found	oussouye not found	gunjur not found	dakar not found	santa maria not found	nouadhibou not found	los llanos de aridane not found	ponta do sol not found	vila franca do campo not found	dingle not found	vestmannaeyjar not found	hvolsvollur not found	skagastrond not found	illoqqortoormiut not found	ushuaia not found	mar del plata not found	chuy not found	cidreira not found	arraial do cabo not found	jamestown not found	georgetown not found	bonthe not found	goderich not found	bubaque not found	oussouye not found	dakar not found	nouakchott not found	nouadhibou not found	adeje not found	los llanos de aridane not found	santa cruz de la palma not found	ponta do sol not found	camacha not found	vila franca do campo not found	muros not found	dingle not found	vestmannaeyjar not found	akureyri not found	husavik not found	illoqqortoormiut not found	ushuaia not found	cape town not found	jamestown not found	georgetown not found	mattru not found	bonthe not found	goderich not found	conakry not found	bubaque not found	canchungo not found	kahone not found	louga not found	nouakchott not found	nouadhibou not found	santa lucia not found	galdar not found	santa cruz de tenerife not found	machico not found	camacha not found	peniche not found	muros not found	dingle not found	westport not found	hofn not found	husavik not found	illoqqortoormiut not found	ushuaia not found	cape town not found	jamestown not found	georgetown not found	monrovia not found	mattru not found	bonthe not found	goderich not found	boffa not found	gabu not found	tambacounda not found	gollere not found	ndioum not found	atar not found	aguimes not found	puerto del rosario not found	teguise not found	porto santo not found	camacha not found	colares not found	peniche not found	muros not found	dingle not found	westport not found	hofn not found	husavik not found	illoqqortoormiut not found	hermanus not found	cape town not found	jamestown not found	georgetown not found	harper not found	buchanan not found	monrovia not found	robertsport not found	serabu not found	mamou not found	mali not found	kayes not found	maghama not found	bababe not found	atar not found	puerto del rosario not found	arrecife not found	teguise not found	asfi not found	aljezur not found	cascais not found	peniche not found	muros not found	carballo not found	bantry not found	dingle not found	westport not found	ballina not found	sorvag not found	hofn not found	husavik not found	illoqqortoormiut not found	hermanus not found	cape town not found	saldanha not found	jamestown not found	georgetown not found	harper not found	buchanan not found	koindu not found	tokonou not found	dinguiraye not found	bafoulabe not found	nioro not found	atar not found	tiznit not found	asfi not found	azimur not found	lagos not found	cascais not found	peniche not found	vila praia de ancora not found	carballo not found	ferrol not found	skibbereen not found	killorglin not found	westport not found	ballina not found	stornoway not found	sorvag not found	hofn not found	husavik not found	illoqqortoormiut not found	hermanus not found	cape town not found	saldanha not found	jamestown not found	georgetown not found	harper not found	zwedru not found	touba not found	odienne not found	kangaba not found	kolokani not found	nara not found	araouane not found	taoudenni not found	tiznit not found	tarudant not found	marrakesh not found	casablanca not found	faro not found	ferreira do alentejo not found	castanheira de pera not found	real not found	naron not found	cervo not found	penzance not found	kinsale not found	youghal not found	boyle not found	buncrana not found	stornoway not found	vagur not found	sorvag not found	vestmanna not found	klaksvik not found	husavik not found	illoqqortoormiut not found	hermanus not found	cape town not found	saldanha not found	jamestown not found	georgetown not found	tabou not found	sassandra not found	gagnoa not found	mankono not found	tingrela not found	koutiala not found	niono not found	sokolo not found	araouane not found	taoudenni not found	tarudant not found	marrakesh not found	mrirt not found	sidi qasim not found	barbate not found	azuaga not found	bejar not found	la baneza not found	aviles not found	plouzane not found	penzance not found	wexford not found	newry not found	bowmore not found	stornoway not found	vagur not found	klaksvik not found	husavik not found	illoqqortoormiut not found	barentsburg not found	hermanus not found	cape town not found	saldanha not found	jamestown not found	axim not found	jacqueville not found	adzope not found	dabakala not found	gaoua not found	solenzo not found	bandiagara not found	goundam not found	araouane not found	taoudenni not found	adrar not found	mrirt not found	tawnat not found	torrox not found	andujar not found	toledo not found	aranda de duero not found	santander not found	ploemeur not found	quimper not found	ivybridge not found	carmarthen not found	whitehaven not found	cumbernauld not found	golspie not found	stromness not found	klaksvik not found	barentsburg not found	hermanus not found	cape town not found	saldanha not found	luderitz not found	jamestown not found	axim not found	dunkwa not found	wenchi not found	wa not found	kokologo not found	djibo not found	tombouctou not found	araouane not found	taoudenni not found	adrar not found	nador not found	almeria not found	cehegin not found	cuenca not found	arnedo not found	hendaye not found	challans not found	rennes not found	octeville not found	cheltenham not found	keighley not found	eyemouth not found	fraserburgh not found	scalloway not found	brae not found	klaksvik not found	barentsburg not found	hermanus not found	cape town not found	saldanha not found	luderitz not found	jamestown not found	port-gentil not found	takoradi not found	cape coast not found	winneba not found	akropong not found	kpandae not found	yendi not found	koupela not found	dori not found	gao not found	kidal not found	tessalit not found	adrar not found	aflu not found	wahran not found	sidi ali not found	benidorm not found	burriana not found	barbastro not found	tonneins not found	angouleme not found	allonnes not found	fecamp not found	hertford not found	bridlington not found	whitley bay not found	peterhead not found	lerwick not found	brae not found	raudeberg not found	roald not found	barentsburg not found	hermanus not found	cape town not found	saldanha not found	luderitz not found	jamestown not found	gamba not found	omboue not found	port-gentil not found	anloga not found	ouidah not found	savalou not found	djougou not found	diapaga not found	ouallam not found	ayorou not found	kidal not found	tessalit not found	adrar not found	aflu not found	medea not found	santa eulalia del rio not found	calvia not found	berga not found	gaillac not found	gueret not found	saint-jean-de-braye not found	abbeville not found	lowestoft not found	great yarmouth not found	bridlington not found	visnes not found	solsvik not found	floro not found	raudeberg not found	roald not found	bud not found	barentsburg not found	hermanus not found	cape town not found	saldanha not found	luderitz not found	walvis bay not found	henties bay not found	namibe not found	soyo not found	gamba not found	omboue not found	port-gentil not found	yenagoa not found	warri not found	epe not found	oyo not found	nikki not found	jega not found	dogondoutchi not found	tahoua not found	kidal not found	tessalit not found	adrar not found	warqla not found	birin not found	tazmalt not found	tigzirt not found	mahon not found	palafrugell not found	ales not found	riorges not found	saint-andre-les-vergers not found	fourmies not found	monster not found	den helder not found	vigrestad not found	varhaug not found	solsvik not found	floro not found	raudeberg not found	roald not found	bud not found	sorland not found	barentsburg not found	hermanus not found	cape town not found	saldanha not found	luderitz not found	walvis bay not found	henties bay not found	namibe not found	luanda not found	mayumba not found	gamba not found	omboue not found	port-gentil not found	abonnema not found	yenagoa not found	agbor not found	ode not found	kontagora not found	gusau not found	madaoua not found	abalak not found	arlit not found	gat not found	warqla not found	tuggurt not found	constantine not found	mahon not found	la seyne-sur-mer not found	manosque not found	cran-gevrier not found	vesoul not found	clervaux not found	rheden not found	kollumerland not found	hvide sande not found	egersund not found	rosendal not found	nordfjordeid not found	bud not found	sistranda not found	sorland not found	barentsburg not found	hermanus not found	cape town not found	saldanha not found	luderitz not found	walvis bay not found	henties bay not found	opuwo not found	namibe not found	luanda not found	soyo not found	mayumba not found	gamba not found	omboue not found	port-gentil not found	luba not found	opobo not found	afikpo not found	makurdi not found	kafanchan not found	malumfashi not found	tessaoua not found	agadez not found	arlit not found	gat not found	warqla not found	duz not found	tawzar not found	manzil salim not found	carbonia not found	cabras not found	ajaccio not found	imperia not found	zermatt not found	kirchzarten not found	geisenheim not found	sassenberg not found	jever not found	hvide sande not found	kristiansand not found	amot not found	ovre ardal not found	sistranda not found	sorland not found	barentsburg not found	hermanus not found	cape town not found	saldanha not found	oranjemund not found	luderitz not found	walvis bay not found	henties bay not found	opuwo not found	namibe not found	benguela not found	luanda not found	soyo not found	loandjili not found	mayumba not found	gamba not found	kango not found	bata not found	edea not found	mbengwi not found	wukari not found	bauchi not found	azare not found	goure not found	tanout not found	agadez not found	arlit not found	gat not found	nalut not found	qabis not found	harqalah not found	manzil jamil not found	tortoli not found	porto-vecchio not found	lerici not found	sondrio not found	bad wurzach not found	werneck not found	bad salzdetfurth not found	neumunster not found	stilling not found	hirtshals not found	vikersund not found	folldal not found	olden not found	rorvik not found	sorland not found	barentsburg not found	bredasdorp not found	hermanus not found	cape town not found	saldanha not found	oranjemund not found	luderitz not found	walvis bay not found	henties bay not found	opuwo not found	namibe not found	benguela not found	luanda not found	soyo not found	loubomo not found	mbigou not found	booue not found	bitam not found	mfou not found	banyo not found	tignere not found	numan not found	damaturu not found	maine-soroa not found	goure not found	bilma not found	gat not found	awbari not found	mizdah not found	jadu not found	jarjis not found	tabulbah not found	marsala not found	anzio not found	cerveteri not found	bertinoro not found	valdobbiadene not found	grafing not found	wunsiedel not found	zerbst not found	bad doberan not found	frederiksvaerk not found	kungalv not found	skotterud not found	roros not found	klaebu not found	bronnoysund not found	sorland not found	gravdal not found	barentsburg not found	bredasdorp not found	hermanus not found	cape town not found	saldanha not found	oranjemund not found	luderitz not found	walvis bay not found	henties bay not found	khorixas not found	opuwo not found	lubango not found	caluquembe not found	lobito not found	sumbe not found	caxito not found	matadi not found	madingou not found	lekoni not found	okandja not found	sembe not found	batouri not found	betare oya not found	tchollire not found	guider not found	bama not found	mao not found	bilma not found	marzuq not found	sabha not found	mizdah not found	bani walid not found	tripoli not found	san lawrenz not found	cefalu not found	sorrento not found	sulmona not found	ancona not found	idrija not found	vorchdorf not found	kraluv dvur not found	lubben not found	wolgast not found	kristianstad not found	jonkoping not found	kristinehamn not found	ostersund not found	korgen not found	stamsund not found	stokmarknes not found	andenes not found	barentsburg not found	longyearbyen not found	bredasdorp not found	hermanus not found	cape town not found	saldanha not found	oranjemund not found	luderitz not found	rehoboth not found	karibib not found	outjo not found	ondangwa not found	ondjiva not found	caconda not found	huambo not found	malanje not found	camabatela not found	kasongo-lunda not found	brazzaville not found	gamboma not found	owando not found	ouesso not found	berberati not found	baoro not found	bol not found	lai not found	dourbali not found	moussoro not found	mao not found	faya not found	bilma not found	marzuq not found	sabha not found	hun not found	waddan not found	misratah not found	pachino not found	melito di porto salvo not found	lauria not found	vieste not found	knin not found	zagreb not found	berndorf not found	holice not found	wolsztyn not found	bialogard not found	karlskrona not found	linkoping not found	fagersta not found	bollnas not found	ostersund not found	rognan not found	kjopsvik not found	andenes not found	longyearbyen not found	bredasdorp not found	hermanus not found	cape town not found	vredendal not found	springbok not found	karasburg not found	keetmanshoop not found	mariental not found	gobabis not found	grootfontein not found	tsumeb not found	menongue not found	camacupa not found	malanje not found	kasongo-lunda not found	kikwit not found	bulungu not found	inongo not found	mbandaka not found	impfondo not found	mbaiki not found	bouca not found	moissala not found	goundi not found	bitkine not found	ati not found	faya not found	marzuq not found	waddan not found	surt not found	benghazi not found	locri not found	crotone not found	gallipoli not found	dubrovnik not found	gromiljak not found	szentlorinc not found	kolarovo not found	stepankovice not found	pleszew not found	koscierzyna not found	wladyslawowo not found	visby not found	uppsala not found	harnosand not found	ornskoldsvik not found	beisfjord not found	finnsnes not found	tromso not found	longyearbyen not found	bredasdorp not found	robertson not found	calvinia not found	karasburg not found	bokspits not found	aranos not found	gobabis not found	grootfontein not found	rundu not found	luena not found	saurimo not found	lucapa not found	tshikapa not found	mangai not found	inongo not found	boende not found	binga not found	bosobolo not found	grimari not found	ndele not found	am timan not found	oum hadjer not found	biltine not found	faya not found	jalu not found	awjilah not found	ajdabiya not found	benghazi not found	tukrah not found	methoni not found	lixourion not found	delvine not found	fushe-arrez not found	kosjeric not found	kanjiza not found	matranovak not found	wieliczka not found	lowicz not found	morag not found	primore not found	pavilosta not found	maarianhamina not found	kristiinankaupunki not found	umea not found	skelleftea not found	kiruna not found	lyngseidet not found	skjervoy not found	longyearbyen not found	bredasdorp not found	george not found	oudtshoorn not found	carnarvon not found	prieska not found	upington not found	tsabong not found	tshane not found	dekar not found	nokaneng not found	shakawe not found	kalabo not found	lumeje not found	luau not found	lucapa not found	kananga not found	mweka not found	lodja not found	boende not found	bumba not found	kembe not found	bria not found	ouadda not found	birao not found	adre not found	biltine not found	faya not found	jalu not found	darnah not found	koroni not found	kalavrita not found	kranea elassonos not found	sveti nikole not found	bogovina not found	ohaba lunga not found	levelek not found	rzeszow not found	siedlce not found	gizycko not found	plunge not found	salme not found	parainen not found	noormarkku not found	pietarsaari not found	boden not found	kautokeino not found	oksfjord not found	hammerfest not found	longyearbyen not found	bredasdorp not found	plettenberg bay not found	graaff-reinet not found	de aar not found	danielskuil not found	werda not found	dutlwe not found	tsienyane not found	maun not found	kachikau not found	senanga not found	kabompo not found	mwinilunga not found	kamina not found	kaniama not found	mbuji-mayi not found	lodja not found	yangambi not found	aketi not found	bondo not found	rafai not found	ouadda not found	birao not found	kutum not found	faya not found	jalu not found	bardiyah not found	tubruq not found	palaiokhora not found	ayia marina not found	rafina not found	sikea not found	velingrad not found	marsani not found	cenade not found	bocicoiu mare not found	zhovkva not found	zabinka not found	druskininkai not found	linkuva not found	tostamaa not found	lohja not found	kangasala not found	ylivieska not found	tornio not found	kautokeino not found	rypefjord not found	havoysund not found	longyearbyen not found	bredasdorp not found	kruisfontein not found	port elizabeth not found	cradock not found	bloemfontein not found	hoopstad not found	lichtenburg not found	boatlaname not found	moiyabana not found	nata not found	victoria falls not found	namwala not found	kasempa not found	solwezi not found	bukama not found	lubao not found	kampene not found	kindu not found	kisangani not found	buta not found	zemio not found	obo not found	raga not found	umm kaddadah not found	kutum not found	marawi not found	asyut not found	abnub not found	marsa matruh not found	bardiyah not found	koutsouras not found	astipalaia not found	piryion not found	canakkale not found	harmanli not found	daia not found	cernat not found	musenita not found	lanivtsi not found	pinsk not found	navahrudak not found	subate not found	torva not found	loviisa not found	jyvaskyla not found	muhos not found	rovaniemi not found	karasjok not found	honningsvag not found	longyearbyen not found	bredasdorp not found	kruisfontein not found	port elizabeth not found	port alfred not found	east london not found	butterworth not found	quthing not found	bethlehem not found	midrand not found	ellisras not found	tobane not found	bulawayo not found	sinazongwe not found	mazabuka not found	mpongwe not found	chililabombwe not found	mwense not found	manono not found	kabalo not found	uvira not found	kabare not found	butembo not found	wamba not found	yambio not found	tambura not found	waw not found	babanusah not found	umm kaddadah not found	marawi not found	tahta not found	abnub not found	matay not found	marsa matruh not found	karpathos not found	lardos not found	odemis not found	susurluk not found	ahtopol not found	dumbraveni not found	suceveni not found	drochia not found	chudniv not found	lyuban not found	minsk not found	zilupe not found	seredka not found	narva-joesuu not found	varkaus not found	kajaani not found	kemijarvi not found	mehamn not found	longyearbyen not found	kruisfontein not found	port elizabeth not found	port alfred not found	east london not found	umzimvubu not found	richmond not found	glencoe not found	breyten not found	tzaneen not found	beitbridge not found	shurugwi not found	chegutu not found	luangwa not found	mkushi not found	samfya not found	luwingu not found	kaputa not found	kalemie not found	rutana not found	kigali not found	kilembe not found	bunia not found	yei not found	yirol not found	ler not found	talawdi not found	abu zabad not found	bara not found	marawi not found	aswan not found	esna not found	asyut not found	matay not found	madinat sittah uktubar not found	rosetta not found	kumluca not found	dinar not found	bozuyuk not found	agva not found	sfantu gheorghe not found	kulevcha not found	zavallya not found	fastiv not found	lyubech not found	orsha not found	nevel not found	dno not found	lisiy nos not found	lakhdenpokhya not found	lieksa not found	kuusamo not found	kovdor not found	vadso not found	batsfjord not found	berlevag not found	mehamn not found	port elizabeth not found	port alfred not found	east london not found	umzimvubu not found	margate not found	ballitoville not found	ulundi not found	mhlume not found	phalaborwa not found	chiredzi not found	chipinge not found	marondera not found	mount darwin not found	katete not found	mpika not found	chinsali not found	sumbawanga not found	inyonga not found	masumbwe not found	muleba not found	lukaya not found	masindi not found	moyo not found	juba not found	malakal not found	marabba not found	umm jarr not found	umm durman not found	marawi not found	aswan not found	el balyana not found	abnub not found	suez not found	damietta not found	pafos not found	alanya not found	beysehir not found	gerede not found	zonguldak not found	zaozerne not found	bekhtery not found	kompaniyivka not found	drabiv not found	shchors not found	khislavichi not found	zapadnaya dvina not found	parfino not found	novaya ladoga not found	suoyarvi not found	muyezerskiy not found	zelenoborskiy not found	verkhnetulomskiy not found	pechenga not found	vardo not found	berlevag not found	port elizabeth not found	port alfred not found	east london not found	umzimvubu not found	margate not found	durban not found	richards bay not found	xai-xai not found	manjacaze not found	chipinge not found	dondo not found	chimoio not found	tete not found	lilongwe not found	mzimba not found	karonga not found	dunda not found	mgandu not found	igurubi not found	nyamuswa not found	port victoria not found	katakwi not found	kaabong not found	kapoeta not found	gambela not found	asosa not found	galgani not found	sinnar not found	wad rawah not found	barbar not found	aswan not found	safaga not found	hurghada not found	mizpe ramon not found	ashqelon not found	dromolaxia not found	silifke not found	aksaray not found	sungurlu not found	kastamonu not found	katsiveli not found	voyinka not found	sofiyivka not found	velyka bahachka not found	druzhba not found	betlitsa not found	sychevka not found	berezayka not found	boksitogorsk not found	shuya not found	nadvoitsy not found	umba not found	kirovsk not found	polyarnyy not found	skalistyy not found	vardo not found	berlevag not found	port elizabeth not found	port alfred not found	east london not found	umzimvubu not found	margate not found	scottsburgh not found	richards bay not found	xai-xai not found	inhambane not found	beira not found	quelimane not found	phalombe not found	mangochi not found	tingi not found	mahanje not found	ilula not found	msanga not found	magugu not found	magadi not found	rongai not found	amudat not found	lodwar not found	bako not found	gore not found	nedjo not found	bahir dar not found	doka not found	wagar not found	sinkat not found	sawakin not found	umm lajj not found	tabuk not found	wadi musa not found	jawa not found	riyaq not found	samandag not found	goksun not found	zile not found	bafra not found	ordzhonikidze not found	novyy svit not found	novomykolayivka not found	peresichna not found	fatezh not found	sosenskiy not found	volokolamsk not found	maksatikha not found	vytegra not found	pudozh not found	solovetskiy not found	tumannyy not found	vardo not found	port elizabeth not found	port alfred not found	east london not found	umzimvubu not found	margate not found	port shepstone not found	richards bay not found	inhambane not found	quelimane not found	mocuba not found	montepuez not found	masuguru not found	liwale not found	kisanga not found	lugoba not found	kisiwani not found	wote not found	maua not found	marsabit not found	mega not found	dilla not found	butajira not found	dejen not found	debre tabor not found	aksum not found	barentu not found	tawkar not found	sawakin not found	jiddah not found	umm lajj not found	tabuk not found	bayir not found	turayf not found	yabrud not found	manbij not found	malatya not found	susehri not found	ordu not found	divnomorskoye not found	primorsko-akhtarsk not found	vysoke not found	urazovo not found	volovo not found	brusyanskiy not found	fryazino not found	novyy nekouz not found	lipin bor not found	kargopol not found	onega not found	ostrovnoy not found	tumannyy not found	vardo not found	port elizabeth not found	port alfred not found	east london not found	umzimvubu not found	margate not found	richards bay not found	beloha not found	ampanihy not found	toliary not found	mocuba not found	angoche not found	nacala not found	pemba not found	lindi not found	kilindoni not found	sokoni not found	mombasa not found	witu not found	garissa not found	wajir not found	moyale not found	goba not found	robe not found	abomsa not found	korem not found	adwa not found	ginda not found	tawkar not found	mecca not found	umm lajj not found	sakakah not found	turayf not found	abu kamal not found	viransehir not found	ergani not found	bayburt not found	trabzon not found	kamennomostskiy not found	novoleushkovskaya not found	almaznyy not found	mitrofanovka not found	verkhnyaya khava not found	korablino not found	sobinka not found	danilov not found	kharovsk not found	shalakusha not found	kodino not found	severodvinsk not found	ostrovnoy not found	tumannyy not found	port alfred not found	east london not found	umzimvubu not found	margate not found	tsihombe not found	beloha not found	ampanihy not found	toliary not found	morondava not found	angoche not found	mocambique not found	nacala not found	moroni not found	madimba not found	kilindoni not found	chake chake not found	malindi not found	bur gabo not found	afmadu not found	dujuma not found	mandera not found	ginir not found	harer not found	dire dawa not found	asayita not found	edd not found	jizan not found	abha not found	mecca not found	buraydah not found	sakakah not found	hit not found	rawah not found	sinjar not found	siirt not found	horasan not found	naruja not found	dzheguta not found	gorodovikovsk not found	tsimlyansk not found	alekseyevskaya not found	rzhaksa not found	shatsk not found	nikologory not found	ostrovskoye not found	verkhovazhye not found	shenkursk not found	lukovetskiy not found	ostrovnoy not found	belushya guba not found	port alfred not found	east london not found	umzimvubu not found	margate not found	tsihombe not found	beloha not found	betioky not found	ankazoabo not found	morondava not found	miandrivazo not found	mahajanga not found	boueni not found	fomboni not found	mitsamiouli not found	micheweni not found	bur gabo not found	kismayo not found	barawe not found	xuddur not found	hargeysa not found	jibuti not found	jiblah not found	sayyan not found	najran not found	abha not found	riyadh not found	buraydah not found	baghdad not found	balad not found	irbil not found	hakkari not found	janfida not found	gori not found	sovetskaya not found	arshan not found	oktyabrskiy not found	danilovka not found	rtishchevo not found	kovylkino not found	dalneye konstantinovo not found	makaryev not found	nyuksenitsa not found	mirnyy not found	karpogory not found	kamenka not found	ostrovnoy not found	belushya guba not found	port alfred not found	east london not found	umzimvubu not found	tsihombe not found	ambovombe not found	amboasary not found	ihosy not found	miandrivazo not found	fenoarivo not found	mahajanga not found	bandrele not found	dzaoudzi not found	domoni not found	mitsamiouli not found	bur gabo not found	barawe not found	mogadishu not found	mahadday weyne not found	hobyo not found	odweyne not found	berbera not found	aden not found	lahij not found	sayyan not found	najran not found	riyadh not found	doha not found	mehran not found	mandali not found	baneh not found	azar shahr not found	istisu not found	bezhta not found	terekli-mekteb not found	komsomolskiy not found	chernyy yar not found	kamyshin not found	novyye burasy not found	bolshiye berezniki not found	vasilsursk not found	vetluga not found	kichmengskiy gorodok not found	krasnoborsk not found	leshukonskoye not found	mezen not found	belushya guba not found	port alfred not found	east london not found	tsihombe not found	taolanaro not found	vangaindrano not found	manakara not found	marolambo not found	anjozorobe not found	tsaratanana not found	ambanja not found	ambilobe not found	mutsamudu not found	barawe not found	mogadishu not found	jawhar not found	hobyo not found	garowe not found	bosaso not found	sayyan not found	najran not found	riyadh not found	buqayq not found	bayan not found	abadan not found	shush not found	alashtar not found	bijar not found	ardabil not found	imisli not found	khuchni not found	makhachkala not found	kamyzyak not found	tambovka not found	novouzensk not found	balakovo not found	bolshiye klyuchishchi not found	zvenigovo not found	tuzha not found	zarya not found	urdoma not found	blagoyevo not found	leshukonskoye not found	belushya guba not found	port alfred not found	east london not found	tsihombe not found	taolanaro not found	farafangana not found	mananjary not found	mahanoro not found	toamasina not found	mananara not found	sambava not found	ambilobe not found	victoria not found	mogadishu not found	hobyo not found	eyl not found	bandarbeyla not found	qandala not found	bereda not found	salalah not found	abu samrah not found	buqayq not found	bushehr not found	hendijan not found	masjed-e soleyman not found	arak not found	qazvin not found	astaneh-ye ashrafiyeh not found	zig not found	gilazi not found	fort-shevchenko not found	marfino not found	inderborskiy not found	ozinki not found	perelyub not found	novaya malykla not found	arsk not found	kumeny not found	raduzhnyy not found	mikun not found	koslan not found	ust-tsilma not found	naryan-mar not found	belushya guba not found	port alfred not found	east london not found	tsihombe not found	taolanaro not found	farafangana not found	saint-leu not found	andevoranto not found	ambodifototra not found	antalaha not found	sambava not found	ambilobe not found	victoria not found	hobyo not found	eyl not found	bandarbeyla not found	bereda not found	salalah not found	abu samrah not found	doha not found	khor not found	khormuj not found	kazerun not found	shahreza not found	kashan not found	damavand not found	fereydun kenar not found	gurgan not found	kuryk not found	shetpe not found	balykshi not found	inderborskiy not found	zachagansk not found	kurmanayevka not found	kamyshla not found	grakhovo not found	yukamenskoye not found	lesnoy not found	kortkeros not found	sindor not found	ust-tsilma not found	naryan-mar not found	belushya guba not found	port alfred not found	east london not found	taolanaro not found	saint-joseph not found	saint-pierre not found	saint-leu not found	le port not found	antalaha not found	sambava not found	victoria not found	hobyo not found	eyl not found	bandarbeyla not found	bargal not found	bereda not found	salalah not found	abu dhabi not found	bandar-e lengeh not found	gerash not found	fasa not found	meybod not found	semnan not found	damghan not found	bandar-e torkaman not found	balkanabat not found	zhanaozen not found	karaton not found	makat not found	chingirlau not found	perevolotskiy not found	priyutovo not found	agidel not found	kez not found	gayny not found	ust-kulom not found	sosnogorsk not found	shchelyayur not found	iskateley not found	belushya guba not found	port alfred not found	east london not found	taolanaro not found	saint-joseph not found	saint-philippe not found	sainte-suzanne not found	grand baie not found	cap malheureux not found	antalaha not found	sambava not found	victoria not found	eyl not found	bandarbeyla not found	bargal not found	bereda not found	salalah not found	nizwa not found	dubai not found	sharjah not found	qeshm not found	rafsanjan not found	bafq not found	tabas not found	shahrud not found	kalaleh not found	gazanjyk not found	beyneu not found	shubarkuduk not found	matveyevka not found	tolbazy not found	starobaltachevo not found	kondratovo not found	kerchevskiy not found	troitsko-pechorsk not found	nizhniy odes not found	puteyets not found	usinsk not found	iskateley not found	belushya guba not found	port alfred not found	east london not found	taolanaro not found	saint-philippe not found	souillac not found	roches noires not found	cap malheureux not found	victoria not found	bandarbeyla not found	bargal not found	salalah not found	ibra not found	ruwi not found	minab not found	jiroft not found	bam not found	ravar not found	tabas not found	sabzevar not found	buzmeyin not found	baherden not found	akdepe not found	kegayli not found	shubarshi not found	emba not found	khromtau not found	buribay not found	lomovka not found	bolsheustikinskoye not found	lysva not found	severnyy-kospashskiy not found	nyrob not found	vuktyl not found	usinsk not found	amderma not found	belushya guba not found	east london not found	taolanaro not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	grand gaube not found	cap malheureux not found	victoria not found	bandarbeyla not found	bargal not found	salalah not found	sur not found	qurayyat not found	chabahar not found	iranshahr not found	zabol not found	birjand not found	taybad not found	mashhad not found	kaka not found	hazorasp not found	mangit not found	karauzyak not found	kazalinsk not found	emba not found	dombarovskiy not found	krasnoyarskiy not found	uyskoye not found	nizhniy ufaley not found	nizhniy tagil not found	volchansk not found	polunochnoye not found	inta not found	amderma not found	belushya guba not found	east london not found	taolanaro not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	quatre cocos not found	grand gaube not found	victoria not found	ugoofaaru not found	kavaratti not found	salalah not found	sur not found	jiwani not found	gwadar not found	khash not found	mirabad not found	farah not found	herat not found	sarakhs not found	murgab not found	seydi not found	gazojak not found	kazalinsk not found	svetlyy not found	lisakovsk not found	bobrovka not found	martyush not found	verkhnyaya sinyachikha not found	gari not found	pelym not found	agirish not found	verkhnyaya inta not found	amderma not found	taolanaro not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	quatre cocos not found	grand gaube not found	victoria not found	thinadhoo not found	kudahuvadhoo not found	mahibadhoo not found	ugoofaaru not found	kavaratti not found	porbandar not found	sur not found	ormara not found	pasni not found	dalbandin not found	geresk not found	sahrak not found	dawlatabad not found	sayat not found	romitan not found	gazli not found	dzhusaly not found	kushmurun not found	borovskoy not found	kargapolye not found	turinsk not found	uray not found	zelenoborsk not found	igrim not found	muzhi not found	severnyy not found	amderma not found	taolanaro not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	quatre cocos not found	grand gaube not found	hithadhoo not found	thinadhoo not found	kudahuvadhoo not found	mahibadhoo not found	ugoofaaru not found	kavaratti not found	veraval not found	porbandar not found	dwarka not found	keti bandar not found	karachi not found	bela not found	surab not found	nushki not found	qandahar not found	panjab not found	sar-e pul not found	qarqin not found	aktash not found	nurota not found	shieli not found	tasbuget not found	zhezkazgan not found	derzhavinsk not found	esil not found	polovinnoye not found	uporovo not found	nizhnyaya tavda not found	lugovoy not found	oktyabrskoye not found	andra not found	labytnangi not found	kharp not found	sovetskiy not found	severnyy not found	amderma not found	taolanaro not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	quatre cocos not found	grand gaube not found	hithadhoo not found	thinadhoo not found	kudahuvadhoo not found	mahibadhoo not found	ugoofaaru not found	dhidhdhoo not found	kavaratti not found	ratnagiri not found	veraval not found	porbandar not found	dwarka not found	jati not found	sann not found	garhi khairo not found	harnai not found	sharan not found	gardan diwal not found	aybak not found	denau not found	zomin not found	chardara not found	kentau not found	zhezkazgan not found	atbasar not found	sergeyevka not found	armizonskoye not found	tobolsk not found	kondinskoye not found	oktyabrskoye not found	aksarka not found	sovetskiy not found	amderma not found	dikson not found	taolanaro not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	quatre cocos not found	hithadhoo not found	thinadhoo not found	kudahuvadhoo not found	mahibadhoo not found	ugoofaaru not found	dhidhdhoo not found	kavaratti not found	malwan not found	ratnagiri not found	diu not found	veraval not found	lalpur not found	diplo not found	chor not found	ubauro not found	barkhan not found	tank not found	azrow not found	andarab not found	leningradskiy not found	chkalovsk not found	lenger not found	zhanatas not found	atasu not found	astana not found	makinsk not found	krasnoarmeysk not found	ishim not found	vagay not found	gornopravdinsk not found	nadym not found	yar-sale not found	dikson not found	taolanaro not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	quatre cocos not found	hithadhoo not found	thinadhoo not found	kudahuvadhoo not found	mahibadhoo not found	ugoofaaru not found	dhidhdhoo not found	kavaratti not found	kankon not found	malwan not found	srivardhan not found	chinchani not found	dhola not found	patan not found	balotra not found	phalodi not found	mailsi not found	mitha tiwana not found	nowshera not found	chitral not found	karakendzha not found	stantsiya gorchakovo not found	talas not found	mikhaylovka not found	saryshagan not found	atasu not found	shakhtinsk not found	stepnogorsk not found	poltavka not found	tyukalinsk not found	tevriz not found	salym not found	cheuskiny not found	muravlenko not found	nadym not found	yar-sale not found	dikson not found	busselton not found	taolanaro not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	hithadhoo not found	viligili not found	hithadhoo not found	male not found	manadhoo not found	dhidhdhoo not found	kavaratti not found	kannangad not found	honavar not found	savantvadi not found	wai not found	ojhar not found	kavant not found	salumbar not found	raipur not found	bhadasar not found	ganganagar not found	kamoke not found	uri not found	gilgit not found	hunza not found	ozgon not found	toktogul not found	shu not found	saryshagan not found	gulshat not found	aktau not found	ereymentau not found	russkaya polyana not found	kolosovka not found	znamenskoye not found	surgut not found	muravlenko not found	pangody not found	yar-sale not found	dikson not found	busselton not found	saint-philippe not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	hithadhoo not found	viligili not found	muli not found	male not found	manavalakurichi not found	varkkallai not found	kochi not found	ponnampet not found	channagiri not found	hungund not found	tuljapur not found	deulgaon raja not found	bhikangaon not found	susner not found	tonk not found	narnaul not found	dirba not found	talwara not found	kargil not found	hunza not found	shache not found	kashi not found	kemin not found	boralday not found	balkhash not found	karkaralinsk not found	maykain not found	kachiry not found	ust-tarka not found	sedelnikovo not found	megion not found	novoagansk not found	gubkinskiy not found	novyy urengoy not found	tazovskiy not found	dikson not found	busselton not found	souillac not found	mahebourg not found	bambous virieux not found	grand river south east not found	hithadhoo not found	viligili not found	muli not found	galle not found	moratuwa not found	udankudi not found	sholavandan not found	pennagaram not found	kadiri not found	alampur not found	medak not found	digras not found	amla not found	bamora not found	antri not found	aligarh not found	haridwar not found	sarahan not found	leh not found	shache not found	kyzyl-suu not found	saryozek not found	ushtobe not found	ayagoz not found	semey not found	aksu not found	karasuk not found	severnoye not found	kedrovyy not found	strezhevoy not found	tarko-sale not found	urengoy not found	tazovskiy not found	dikson not found	busselton not found	mahebourg not found	bambous virieux not found	grand river south east not found	hithadhoo not found	matara not found	weligama not found	galle not found	anuradhapura not found	valvedditturai not found	pondicherry not found	nayudupeta not found	addanki not found	mahbubabad not found	mul not found	waraseoni not found	pawai not found	kurara not found	pawayan not found	bageshwar not found	gangotri not found	leh not found	shache not found	aksu not found	zharkent not found	sarkand not found	ayagoz not found	semey not found	mikhaylovskoye not found	pankrushikha not found	ubinskoye not found	kedrovyy not found	kargasok not found	strezhevoy not found	tarko-sale not found	urengoy not found	tazovskiy not found	dikson not found	busselton not found	mahebourg not found	bambous virieux not found	grand river south east not found	hithadhoo not found	matara not found	hambantota not found	batticaloa not found	mullaitivu not found	mamallapuram not found	kattivakkam not found	razole not found	chitrakonda not found	umarkot not found	bilaspur not found	sidhi not found	pratapgarh not found	bhinga not found	jumla not found	dharchula not found	joshimath not found	leh not found	aksu not found	kuche not found	yining not found	urdzhar not found	glubokoe not found	pospelikha not found	suzun not found	kolyvan not found	podgornoye not found	parabel not found	kargasok not found	krasnoselkup not found	karaul not found	dikson not found	busselton not found	bambous virieux not found	grand river south east not found	hithadhoo not found	hambantota not found	kalmunai not found	trincomalee not found	madras not found	amalapuram not found	yarada not found	srikakulam not found	udayagiri not found	sundargarh not found	daltenganj not found	sikandarpur not found	waling not found	pokhara not found	jumla not found	kuche not found	kuytun not found	karamay not found	kurchum not found	zyryanovsk not found	petropavlovskoye not found	pervomayskoye not found	kozhevnikovo not found	molchanovo not found	belyy yar not found	krasnoselkup not found	karaul not found	dikson not found	busselton not found	geraldton not found	carnarvon not found	bengkulu not found	hithadhoo not found	hambantota not found	wattegama not found	kalmunai not found	batticaloa not found	kattivakkam not found	yarada not found	narasannapeta not found	gopalpur not found	nimaparha not found	rairangpur not found	hesla not found	darbhanga not found	banepa not found	kathmandu not found	pokhara not found	jumla not found	korla not found	shihezi not found	baijiantan not found	zaysan not found	ust-koksa not found	gorno-altaysk not found	guryevsk not found	anzhero-sudzhensk not found	pervomayskoye not found	belyy yar not found	turukhansk not found	igarka not found	dudinka not found	dikson not found	albany not found	busselton not found	geraldton not found	carnarvon not found	bengkulu not found	padang not found	meulaboh not found	hambantota not found	kalmunai not found	port blair not found	puri not found	paradwip not found	haldia not found	kandi not found	kishanganj not found	mangan not found	lasa not found	korla not found	urumqi not found	altay not found	aktash not found	tashtagol not found	mezhdurechensk not found	suslovo not found	teguldet not found	turukhansk not found	snezhnogorsk not found	talnakh not found	dikson not found	albany not found	busselton not found	geraldton not found	carnarvon not found	bengkulu not found	padang not found	meulaboh not found	banda aceh not found	sabang not found	port blair not found	labutta not found	akyab not found	mathbaria not found	mirzapur not found	dhuburi not found	gasa not found	lasa not found	korla not found	urumqi not found	altay not found	mugur-aksy not found	abaza not found	sorsk not found	nazarovo not found	novobirilyussy not found	teya not found	turukhansk not found	svetlogorsk not found	talnakh not found	dikson not found	albany not found	busselton not found	geraldton not found	carnarvon not found	labuhan not found	bengkulu not found	padang not found	sibolga not found	meulaboh not found	banda aceh not found	sabang not found	port blair not found	labutta not found	akyab not found	bandarban not found	kamalpur not found	nongpoh not found	tawang not found	lasa not found	hami not found	ulaangom not found	chaa-khol not found	sayanskiy not found	divnogorsk not found	pirovskoye not found	teya not found	svetlogorsk not found	talnakh not found	dikson not found	albany not found	busselton not found	geraldton not found	carnarvon not found	palabuhanratu not found	labuhan not found	bengkulu not found	padang not found	sibolga not found	meulaboh not found	banda aceh not found	sabang not found	port blair not found	labutta not found	myanaung not found	minbu not found	falam not found	churachandpur not found	bokajan not found	ziro not found	along not found	lasa not found	yumen not found	hami not found	erzin not found	samagaltay not found	turan not found	koshurnikovo not found	shalinskoye not found	kazachinskoye not found	severo-yeniseyskiy not found	baykit not found	svetlogorsk not found	talnakh not found	khatanga not found	albany not found	busselton not found	geraldton not found	carnarvon not found	palabuhanratu not found	labuhan not found	bengkulu not found	padang not found	sibolga not found	meulaboh not found	sigli not found	sabang not found	ranong not found	mergui not found	dawei not found	pyapon not found	letpadan not found	pyinmana not found	mandalay not found	katha not found	khonsa not found	tezu not found	pasighat not found	along not found	yumen not found	hami not found	erzin not found	toora-khem not found	ilanskiy not found	motygino not found	baykit not found	tura not found	khatanga not found	albany not found	busselton not found	geraldton not found	carnarvon not found	palabuhanratu not found	labuhan not found	bengkulu not found	padang not found	sibolga not found	langsa not found	lhokseumawe not found	kathu not found	ranong not found	mergui not found	dawei not found	mudon not found	pa sang not found	mae hong son not found	lashio not found	banmo not found	myitkyina not found	tezu not found	xining not found	jiuquan not found	yumen not found	moron not found	kungurtug not found	nizhneudinsk not found	tayshet not found	boguchany not found	baykit not found	tura not found	khatanga not found	albany not found	busselton not found	geraldton not found	carnarvon not found	palabuhanratu not found	labuhan not found	bengkulu not found	padang not found	payakumbuh not found	rantauprapat not found	lumut not found	kuala kedah not found	ron phibun not found	ko samui not found	kui buri not found	bang len not found	khanu woralaksaburi not found	den chai not found	chiang rai not found	yunjinghong not found	simao not found	dali not found	panzhihua not found	yaan not found	xining not found	zhangye not found	jiuquan not found	hovd not found	moron not found	orlik not found	tulun not found	chunskiy not found	kodinsk not found	tura not found	khatanga not found	albany not found	busselton not found	geraldton not found	carnarvon not found	palabuhanratu not found	labuhan not found	pringsewu not found	bengkulu not found	sungaipenuh not found	sijunjung not found	sungai udang not found	kuala lipis not found	sungai kolok not found	yaring not found	ko samui not found	laem sing not found	sa kaeo not found	chaiyaphum not found	nam som not found	luang prabang not found	dien bien not found	zhoucheng not found	panzhihua not found	xichang not found	yaan not found	linqiong not found	linxia not found	xining not found	jinchang not found	hovd not found	bulgan not found	zakamensk not found	kyren not found	zima not found	bratsk not found	ust-ilimsk not found	vanavara not found	tura not found	khatanga not found	albany not found	busselton not found	geraldton not found	carnarvon not found	palabuhanratu not found	labuhan not found	pringsewu not found	baturaja not found	jambi not found	kijang not found	kota tinggi not found	cukai not found	kuala terengganu not found	ca mau not found	kampot not found	pousat not found	phrai bung not found	selaphum not found	seka not found	xam nua not found	lao cai not found	zhongshu not found	rongcheng not found	zhaotong not found	leshan not found	jiangyou not found	linxia not found	lanzhou not found	wuwei not found	jinchang not found	hovd not found	bulgan not found	kholtoson not found	bolshoy lug not found	osa not found	shestakovo not found	rudnogorsk not found	vanavara not found	tura not found	khatanga not found	albany not found	busselton not found	geraldton not found	carnarvon not found	kawalu not found	banjar not found	palabuhanratu not found	cilegon not found	metro not found	mentok not found	kijang not found	cukai not found	paka not found	bac lieu not found	can tho not found	kracheh not found	champasak not found	saravan not found	ha tinh not found	ninh binh not found	bac can not found	bose not found	anshun not found	tongzi not found	heyang not found	baoning not found	beidao not found	pingliang not found	yinchuan not found	shitanjing not found	haibowan not found	mandalgovi not found	ulaanbaatar not found	suhbaatar not found	istok not found	kachug not found	ust-kut not found	yerbogachen not found	khatanga not found	albany not found	busselton not found	geraldton not found	carnarvon not found	bambanglipuro not found	srandakan not found	kroya not found	kawalu not found	pamanukan not found	manggar not found	sungairaya not found	pemangkat not found	bac lieu not found	vung tau not found	phan thiet not found	da lat not found	play cu not found	da nang not found	dong hoi not found	cam pha not found	qinzhou not found	jinchengjiang not found	xiaoweizhai not found	tongzi not found	fuling not found	daxian not found	yuxia not found	pingliang not found	yinchuan not found	haibowan not found	mandalgovi not found	darhan not found	ulaanbaatar not found	bichura not found	onokhoy not found	khuzhir not found	kazachinskoye not found	kirensk not found	yerbogachen not found	aykhal not found	khatanga not found	albany not found	busselton not found	geraldton not found	carnarvon not found	karratha not found	bambanglipuro not found	srandakan not found	mlonggo not found	manggar not found	pangkalanbuun not found	pontianak not found	kuching not found	sibu not found	phan thiet not found	phan rang not found	nha trang not found	qui nhon not found	quang ngai not found	wanning not found	lingao not found	yashan not found	luorong not found	guilin not found	jishou not found	enshi not found	shiyan not found	weinan not found	yanan not found	dongsheng not found	hohhot not found	erenhot not found	darhan not found	ondorhaan not found	krasnyy chikoy not found	kizhinga not found	kurumkan not found	kichera not found	alekseyevsk not found	yerbogachen not found	aykhal not found	saskylakh not found	albany not found	busselton not found	geraldton not found	carnarvon not found	karratha not found	gondanglegi not found	kanigoro not found	tulungagung not found	lasem not found	pangkalanbuun not found	sri aman not found	sibu not found	bintulu not found	miri not found	phan rang not found	nha trang not found	qui nhon not found	wanning not found	qiongshan not found	tangping not found	huaicheng not found	yongzhou not found	loudi not found	nanhai not found	xiangfan not found	yima not found	linfen not found	taiyuan not found	hohhot not found	erenhot not found	baruun-urt not found	ondorhaan not found	kyra not found	mogzon not found	sosnovo-ozerskoye not found	yanchukan not found	sogdiondon not found	vitim not found	chernyshevskiy not found	aykhal not found	udachnyy not found	saskylakh not found	albany not found	busselton not found	kwinana not found	geraldton not found	carnarvon not found	karratha not found	denpasar not found	muncar not found	bondowoso not found	sumenep not found	banjarmasin not found	kualakapuas not found	kapit not found	miri not found	labuan not found	kota kinabalu not found	taburi not found	candawaga not found	qui nhon not found	wanning not found	zhuhai not found	yingcheng not found	xiongzhou not found	pingxiang not found	puqi not found	xinyang not found	xuchang not found	hebi not found	luancheng not found	datong not found	jining not found	erenhot not found	baruun-urt not found	aksha not found	makkaveyevo not found	bagdarin not found	severomuysk not found	mamakan not found	lensk not found	mirnyy not found	udachnyy not found	saskylakh not found	albany not found	collie not found	perth not found	northam not found	geraldton not found	carnarvon not found	karratha not found	praya not found	mataram not found	singaraja not found	martapura not found	barabai not found	loa janan not found	tarakan not found	limbang not found	kota kinabalu not found	balabac not found	panalingaan not found	tagusao not found	cabra not found	aloleng not found	catuday not found	jieshi not found	rongcheng not found	ganzhou not found	linchuan not found	huangmei not found	gushi not found	bozhou not found	yanggu not found	hengshui not found	mentougou not found	zhangjiakou not found	mujiayingzi not found	baruun-urt not found	zabaykalsk not found	sherlovaya gora not found	shilka not found	bukachacha not found	taksimo not found	kropotkin not found	lensk not found	suntar not found	almaznyy not found	nyurba not found	udachnyy not found	saskylakh not found	albany not found	northam not found	geraldton not found	roebourne not found	port hedland not found	waingapu not found	sumbawa not found	galesong not found	majene not found	balikpapan not found	bontang not found	tarakan not found	tawau not found	sandakan not found	rio tuba not found	aporawan not found	bacuit not found	cabra not found	aloleng not found	puro not found	davila not found	haimen not found	shima not found	sanming not found	shangrao not found	tunxi not found	chaohu not found	suicheng not found	nanma not found	binzhou not found	fengrun not found	mujiayingzi not found	chifeng not found	hailar not found	manzhouli not found	krasnokamensk not found	sretensk not found	ksenyevka not found	chara not found	suntar not found	nyurba not found	saskylakh not found	new norfolk not found	albany not found	esperance not found	northam not found	port hedland not found	broome not found	waingapu not found	ruteng not found	tanete not found	singkang not found	poso not found	palu not found	tarakan not found	manuk mangkaw not found	pandan niog not found	simbahan not found	osmena not found	salvacion not found	cabra not found	paitan not found	sinait not found	davila not found	tungkang not found	erhlin not found	rongcheng not found	lishui not found	fuyang not found	taixing not found	dongkan not found	jiaonan not found	longkou not found	qinhuangdao not found	chaoyang not found	chifeng not found	wulanhaote not found	hailar not found	nerchinskiy zavod not found	mogocha not found	khani not found	verkhnevilyuysk not found	zhigansk not found	saskylakh not found	new norfolk not found	albany not found	esperance not found	port hedland not found	broome not found	kupang not found	ende not found	maumere not found	katobu not found	kendari not found	luwuk not found	gorontalo not found	latung not found	tabialan not found	siocon not found	magdalena not found	caticlan not found	alabat not found	dumabato not found	awallan not found	basco not found	taitung not found	suao not found	keelung not found	wenling not found	dinghai not found	huilong not found	dafeng not found	wencheng not found	weihai not found	xiongyue not found	heishan not found	tongliao not found	wulanhaote not found	zalantun not found	genhe not found	yerofey pavlovich not found	khani not found	vilyuysk not found	zhigansk not found	tiksi not found	new norfolk not found	albany not found	esperance not found	yulara not found	broome not found	kupang not found	soe not found	atambua not found	katobu not found	kendari not found	luwuk not found	gorontalo not found	manado not found	sarangani not found	palimbang not found	munai not found	clarin not found	cataingan not found	caramoran not found	dicabisagan not found	basco not found	ishigaki not found	shenjiamen not found	huilong not found	yatou not found	dandong not found	fushun not found	zhengjiatun not found	tailai not found	gannan not found	alihe not found	tahe not found	skovorodino not found	zolotinka not found	serebryanyy bor not found	nizhniy kuranakh not found	kysyl-syr not found	zhigansk not found	tiksi not found	new norfolk not found	albany not found	esperance not found	yulara not found	broome not found	kununurra not found	soe not found	atambua not found	ambon not found	tidore not found	bitung not found	sarangani not found	lamidan not found	santa josefa not found	san benito not found	dapdap not found	gigmoto not found	pandan not found	dicabisagan not found	basco not found	hirara not found	yomitan not found	shenjiamen not found	fukue not found	seoul not found	huanren not found	erdaojiang not found	jiutai not found	zhaodong not found	keshan not found	nenjiang not found	ushumun not found	magdagachi not found	zolotinka not found	lebedinyy not found	tommot not found	berdigestyakh not found	sangar not found	zhigansk not found	tiksi not found	new norfolk not found	portland not found	mount gambier not found	port lincoln not found	esperance not found	flinders not found	yulara not found	kununurra not found	port keats not found	nguiu not found	atambua not found	ambon not found	amahai not found	tidore not found	ternate not found	sarangani not found	pundaguitan not found	kinablangan not found	union not found	sulangan not found	alugan not found	gigmoto not found	pandan not found	hirara not found	itoman not found	nishihara not found	nago not found	naze not found	fukue not found	seoul not found	linjiang not found	songjianghe not found	huangnihe not found	binzhou not found	cuiluan not found	tambovka not found	shimanovsk not found	zeya not found	tommot not found	mokhsogollokh not found	sangar not found	batagay-alyta not found	tiksi not found	hobart not found	new norfolk not found	portland not found	mount gambier not found	port lincoln not found	flinders not found	yulara not found	kununurra not found	port keats not found	nguiu not found	tual not found	amahai not found	sorong not found	ternate not found	san isidro not found	baculin not found	bacolod not found	sulangan not found	san policarpo not found	alugan not found	payo not found	itoman not found	nishihara not found	nago not found	naze not found	kaseda not found	ushibuka not found	maebaru not found	nagato not found	seoul not found	khasan not found	ningan not found	yilan not found	xinqing not found	novobureyskiy not found	fevralsk not found	chagda not found	nizhniy bestyakh not found	namtsy not found	batagay-alyta not found	tiksi not found	hobart not found	new norfolk not found	portland not found	mount gambier not found	port lincoln not found	flinders not found	yulara not found	alice springs not found	katherine not found	jabiru not found	nguiu not found	tual not found	sorong not found	kloulklubed not found	meyungs not found	san policarpo not found	gigmoto not found	nishihara not found	gushikawa not found	naze not found	kushima not found	shintomi not found	hikari not found	oda not found	izumo not found	khasan not found	shkotovo-22 not found	vozdvizhenka not found	baoqing not found	babstovo not found	tyrma not found	stoyba not found	tokur not found	chagda not found	amga not found	churapcha not found	borogontsy not found	verkhoyansk not found	batagay-alyta not found	tiksi not found	hobart not found	new norfolk not found	portland not found	mount gambier not found	port lincoln not found	flinders not found	yulara not found	alice springs not found	ngukurr not found	maningrida not found	tual not found	nabire not found	manokwari not found	kloulklubed not found	meyungs not found	nishihara not found	naze not found	kushima not found	nichinan not found	muroto not found	waki not found	tottori not found	vrangel not found	preobrazheniye not found	chuguyevka not found	dalnerechensk not found	smidovich not found	litovko not found	sofiysk not found	zlatoustovsk not found	chumikan not found	ust-maya not found	churapcha not found	khandyga not found	verkhoyansk not found	batagay not found	ust-kuyga not found	nizhneyansk not found	hobart not found	new norfolk not found	portland not found	mount gambier not found	victor harbor not found	port lincoln not found	port augusta not found	alice springs not found	mount isa not found	ngukurr not found	alyangula not found	galiwinku not found	tual not found	nabire not found	biak not found	kloulklubed not found	airai not found	nishihara not found	naze not found	muroto not found	shingu not found	kumano not found	sabae not found	wajima not found	olga not found	rudnaya pristan not found	vostok not found	mukhen not found	elban not found	berezovyy not found	chumikan not found	ayan not found	eldikan not found	dzhebariki-khaya not found	khandyga not found	batagay not found	ust-kuyga not found	nizhneyansk not found	hobart not found	new norfolk not found	portland not found	mount gambier not found	victor harbor not found	port pirie not found	port augusta not found	alice springs not found	mount isa not found	alyangula not found	nhulunbuy not found	merauke not found	kiunga not found	nabire not found	biak not found	airai not found	naze not found	shingu not found	oyama not found	tatsuno not found	ryotsu not found	oga not found	kamiiso not found	terney not found	svetlaya not found	gurskoye not found	gorin not found	mnogovershinnyy not found	ayan not found	solnechnyy not found	khandyga not found	batagay not found	deputatskiy not found	nizhneyansk not found	hobart not found	new norfolk not found	burnie not found	portland not found	mount gambier not found	murray bridge not found	broken hill not found	mount isa not found	alyangula not found	nhulunbuy not found	merauke not found	kiunga not found	vanimo not found	airai not found	naze not found	shingu not found	shimoda not found	tateyama not found	mitsukaido not found	nagai not found	tenno not found	kamiiso not found	yoichi not found	svetlaya not found	sovetskaya gavan not found	vysokogornyy not found	bogorodskoye not found	mnogovershinnyy not found	ayan not found	solnechnyy not found	ust-nera not found	khonuu not found	deputatskiy not found	nizhneyansk not found	hobart not found	new norfolk not found	burnie not found	warrnambool not found	hamilton not found	horsham not found	mildura not found	broken hill not found	mount isa not found	atherton not found	mareeba not found	daru not found	morehead not found	kiunga not found	ambunti not found	vanimo not found	airai not found	shimoda not found	tateyama not found	katsuura not found	hasaki not found	ishinomaki not found	miyako not found	shizunai not found	fukagawa not found	shebunino not found	ilinskiy not found	boshnyakovo not found	lazarev not found	okha not found	okhotsk not found	ust-nera not found	khonuu not found	deputatskiy not found	nizhneyansk not found	hobart not found	new norfolk not found	burnie not found	colac not found	geelong not found	swan hill not found	broken hill not found	roma not found	emerald not found	charters towers not found	atherton not found	mareeba not found	daru not found	balimo not found	mount hagen not found	angoram not found	wewak not found	aitape not found	lorengau not found	airai not found	shimoda not found	tateyama not found	katsuura not found	hasaki not found	kamaishi not found	miyako not found	kushiro not found	bihoro not found	novikovo not found	makarov not found	poronaysk not found	katangli not found	okha not found	okhotsk not found	artyk not found	ust-nera not found	khonuu not found	belaya gora not found	chokurdakh not found	hobart not found	new norfolk not found	ulverstone not found	burnie not found	warragul not found	corowa not found	griffith not found	dubbo not found	roma not found	emerald not found	charters towers not found	innisfail not found	cairns not found	port moresby not found	kerema not found	kainantu not found	madang not found	lorengau not found	airai not found	katsuura not found	hasaki not found	kamaishi not found	nemuro not found	yuzhno-kurilsk not found	otradnoye not found	vostok not found	poronaysk not found	katangli not found	ekhabi not found	okha not found	okhotsk not found	kadykchan not found	artyk not found	belaya gora not found	chokurdakh not found	hobart not found	launceston not found	lakes entrance not found	tumut not found	young not found	dubbo not found	narrabri not found	roma not found	emerald not found	moranbah not found	bowen not found	ayr not found	cairns not found	port moresby not found	popondetta not found	finschhafen not found	lorengau not found	airai not found	katsuura not found	hasaki not found	kamaishi not found	nemuro not found	kurilsk not found	vostok not found	ekhabi not found	arman not found	ust-omchug not found	kholodnyy not found	shirokiy not found	zyryanka not found	belaya gora not found	chokurdakh not found	bluff not found	hobart not found	lakes entrance not found	cooma not found	batemans bay not found	lithgow not found	mudgee not found	narrabri not found	moree not found	roma not found	biloela not found	mackay not found	bowen not found	innisfail not found	samarai not found	alotau not found	kandrian not found	kimbe not found	kavieng not found	lorengau not found	airai not found	katsuura not found	hasaki not found	nemuro not found	sentyabrskiy not found	vostok not found	magadan not found	arman not found	yagodnoye not found	zyryanka not found	chokurdakh not found	bluff not found	hobart not found	lakes entrance not found	batemans bay not found	ulladulla not found	sydney not found	taree not found	armidale not found	warwick not found	kingaroy not found	gladstone not found	yeppoon not found	mackay not found	bowen not found	samarai not found	alotau not found	kokopo not found	rabaul not found	kavieng not found	airai not found	katsuura not found	hasaki not found	nemuro not found	sentyabrskiy not found	vostok not found	oktyabrskiy not found	sobolevo not found	ola not found	orotukan not found	seymchan not found	zyryanka not found	srednekolymsk not found	chokurdakh not found	bluff not found	hobart not found	batemans bay not found	ulladulla not found	kiama not found	nelson bay not found	port macquarie not found	coffs harbour not found	gold coast not found	coolum beach not found	hervey bay not found	gladstone not found	yeppoon not found	mackay not found	samarai not found	buin not found	panguna not found	namatanai not found	kavieng not found	katsuura not found	hasaki not found	sentyabrskiy not found	severo-kurilsk not found	oktyabrskiy not found	sobolevo not found	ola not found	talaya not found	dukat not found	seymchan not found	srednekolymsk not found	chokurdakh not found	bluff not found	tuatapere not found	hobart not found	batemans bay not found	ulladulla not found	nelson bay not found	port macquarie not found	ballina not found	byron bay not found	kawana waters not found	hervey bay not found	bundaberg not found	yeppoon not found	samarai not found	gizo not found	kieta not found	namatanai not found	kavieng not found	katsuura not found	hasaki not found	sentyabrskiy not found	severo-kurilsk not found	oktyabrskiy not found	sobolevo not found	tigil not found	omsukchan not found	srednekolymsk not found	cherskiy not found	chokurdakh not found	bluff not found	tuatapere not found	te anau not found	ulladulla not found	nelson bay not found	port macquarie not found	ballina not found	byron bay not found	kawana waters not found	hervey bay not found	poum not found	kirakira not found	honiara not found	gizo not found	kieta not found	namatanai not found	kavieng not found	butaritari not found	hasaki not found	sentyabrskiy not found	severo-kurilsk not found	petropavlovsk-kamchatskiy not found	yelizovo not found	esso not found	tigil not found	palana not found	evensk not found	omsukchan not found	cherskiy not found	bluff not found	tuatapere not found	te anau not found	nelson bay not found	port macquarie not found	sawtell not found	byron bay not found	gold coast not found	koumac not found	poum not found	kirakira not found	honiara not found	buala not found	kieta not found	namatanai not found	butaritari not found	hasaki not found	sentyabrskiy not found	severo-kurilsk not found	petropavlovsk-kamchatskiy not found	milkovo not found	klyuchi not found	palana not found	evensk not found	cherskiy not found	bluff not found	tuatapere not found	te anau not found	port macquarie not found	ballina not found	byron bay not found	noumea not found	poya not found	voh not found	poum not found	kirakira not found	auki not found	buala not found	kieta not found	butaritari not found	hasaki not found	sentyabrskiy not found	severo-kurilsk not found	petropavlovsk-kamchatskiy not found	ust-kamchatsk not found	ossora not found	evensk not found	cherskiy not found	bluff not found	tuatapere not found	te anau not found	ahipara not found	noumea not found	bourail not found	voh not found	poum not found	luganville not found	lata not found	kirakira not found	auki not found	bairiki not found	butaritari not found	sentyabrskiy not found	severo-kurilsk not found	petropavlovsk-kamchatskiy not found	nikolskoye not found	ust-kamchatsk not found	ossora not found	kamenskoye not found	bilibino not found	cherskiy not found	pevek not found	bluff not found	tuatapere not found	te anau not found	wanaka not found	westport not found	ahipara not found	vao not found	noumea not found	bouloupari not found	fayaoue not found	vila not found	luganville not found	sola not found	lata not found	tabiauea not found	bairiki not found	butaritari not found	sentyabrskiy not found	severo-kurilsk not found	nikolskoye not found	tilichiki not found	kamenskoye not found	bilibino not found	pevek not found	bluff not found	otautau not found	wanaka not found	westport not found	ahipara not found	vao not found	tadine not found	we not found	vila not found	lakatoro not found	sola not found	lata not found	tabiauea not found	butaritari not found	severo-kurilsk not found	nikolskoye not found	tilichiki not found	kamenskoye not found	bilibino not found	pevek not found	bluff not found	kaitangata not found	milton not found	fairlie not found	hokitika not found	westport not found	karamea not found	ahipara not found	vao not found	tadine not found	isangel not found	vila not found	sola not found	lata not found	lolua not found	utiroa not found	tabiauea not found	buariki not found	butaritari not found	severo-kurilsk not found	nikolskoye not found	tilichiki not found	kamenskoye not found	pevek not found	bluff not found	kaitangata not found	dunedin not found	waitati not found	rakaia not found	reefton not found	takaka not found	okato not found	ahipara not found	vao not found	isangel not found	vila not found	sola not found	lolua not found	utiroa not found	temaraia not found	tabiauea not found	taburao not found	butaritari not found	nikolskoye not found	tilichiki not found	kamenskoye not found	komsomolskiy not found	pevek not found	bluff not found	kaitangata not found	dunedin not found	lincoln not found	christchurch not found	seddon not found	manaia not found	kawhia not found	dargaville not found	kaeo not found	vao not found	isangel not found	sola not found	asau not found	lolua not found	ijaki not found	utiroa not found	temaraia not found	rawannawi not found	butaritari not found	nikolskoye not found	beringovskiy not found	anadyr not found	komsomolskiy not found	pevek not found	bluff not found	kaitangata not found	dunedin not found	christchurch not found	waipawa not found	takapau not found	mamaku not found	whitianga not found	ngunguru not found	russell not found	kaeo not found	vao not found	isangel not found	asau not found	lolua not found	ijaki not found	tabukiniberu not found	rawannawi not found	butaritari not found	nikolskoye not found	beringovskiy not found	anadyr not found	leningradskiy not found	bluff not found	kaitangata not found	dunedin not found	christchurch not found	waipawa not found	otane not found	wairoa not found	ruatoria not found	whitianga not found	ngunguru not found	russell not found	kaeo not found	isangel not found	asau not found	lolua not found	rungata not found	rawannawi not found	butaritari not found	nikolskoye not found	beringovskiy not found	anadyr not found	leningradskiy not found	{'cod': 429, 'message': 'Your account is temporary blocked due to exceeding of requests limitation of your subscription type. Please choose the proper subscription http://openweathermap.org/price'}



```python
#filtering overdense sections, primarily coasts and islands
#should be implemented in citipy loop above to reduce OWP calls
#but makes for a giant unwieldy loop for jupyter notebook

latlng_list = []
cities_cut = []
cut = []
append = 0
dud = 0
copy = 0

for city in cities:
    if len(city) > 3:
        #rounds values to a round 3x value for categorizing
        lat = (city['lat'] // latstep) * latstep
        lng = (city['lng'] // lngstep) * lngstep
        if [lat, lng] not in latlng_list:
            #value area original move to dataset
            append += 1
            latlng_list.append([lat,lng])
            cities_cut.append(city)
        else:
            #value area already expressed move to dataset to
            #show what was cut
            cut.append(city)
            copy += 1
    else:
        #no weather data associated with city
        dud += 1
print(f'TRIM RESULT \t {append} Appended, \t {dud} Duds, \t {copy} Copies')
```

    TRIM RESULT 	 1499 Appended, 	 2210 Duds, 	 2251 Copies



```python
#cities filtered out of bulk dataset
df_cut = pd.DataFrame(cut)
```


```python
#all cities with data
df_uncut = pd.DataFrame(cities)
df_uncut = df_uncut.dropna()
df_uncut = df_uncut.drop_duplicates()
df_uncut
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>clouds</th>
      <th>country</th>
      <th>hum</th>
      <th>lat</th>
      <th>lng</th>
      <th>name</th>
      <th>temp</th>
      <th>wind</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>40.0</td>
      <td>to</td>
      <td>94.0</td>
      <td>-21.20</td>
      <td>-175.20</td>
      <td>vaini</td>
      <td>299.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1.0</td>
      <td>us</td>
      <td>93.0</td>
      <td>22.08</td>
      <td>-159.32</td>
      <td>kapaa</td>
      <td>294.150</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>4</th>
      <td>92.0</td>
      <td>ru</td>
      <td>100.0</td>
      <td>64.38</td>
      <td>-173.30</td>
      <td>provideniya</td>
      <td>274.078</td>
      <td>12.72</td>
    </tr>
    <tr>
      <th>5</th>
      <td>92.0</td>
      <td>ru</td>
      <td>84.0</td>
      <td>66.32</td>
      <td>-179.17</td>
      <td>egvekinot</td>
      <td>266.328</td>
      <td>3.30</td>
    </tr>
    <tr>
      <th>8</th>
      <td>40.0</td>
      <td>to</td>
      <td>94.0</td>
      <td>-18.65</td>
      <td>-173.98</td>
      <td>neiafu</td>
      <td>299.150</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>25</th>
      <td>64.0</td>
      <td>to</td>
      <td>100.0</td>
      <td>-19.80</td>
      <td>-174.35</td>
      <td>pangai</td>
      <td>299.628</td>
      <td>6.92</td>
    </tr>
    <tr>
      <th>33</th>
      <td>88.0</td>
      <td>ru</td>
      <td>100.0</td>
      <td>65.58</td>
      <td>-171.00</td>
      <td>lavrentiya</td>
      <td>272.653</td>
      <td>10.60</td>
    </tr>
    <tr>
      <th>37</th>
      <td>92.0</td>
      <td>nu</td>
      <td>94.0</td>
      <td>-19.06</td>
      <td>-169.92</td>
      <td>alofi</td>
      <td>298.150</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>43</th>
      <td>1.0</td>
      <td>us</td>
      <td>64.0</td>
      <td>41.37</td>
      <td>-73.41</td>
      <td>bethel</td>
      <td>280.150</td>
      <td>2.35</td>
    </tr>
    <tr>
      <th>58</th>
      <td>90.0</td>
      <td>us</td>
      <td>85.0</td>
      <td>71.29</td>
      <td>-156.79</td>
      <td>barrow</td>
      <td>262.150</td>
      <td>4.10</td>
    </tr>
    <tr>
      <th>66</th>
      <td>20.0</td>
      <td>us</td>
      <td>93.0</td>
      <td>21.39</td>
      <td>-158.15</td>
      <td>nanakuli</td>
      <td>292.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>69</th>
      <td>90.0</td>
      <td>us</td>
      <td>79.0</td>
      <td>64.50</td>
      <td>-165.41</td>
      <td>nome</td>
      <td>269.150</td>
      <td>4.60</td>
    </tr>
    <tr>
      <th>73</th>
      <td>88.0</td>
      <td>ck</td>
      <td>100.0</td>
      <td>-21.21</td>
      <td>-159.78</td>
      <td>avarua</td>
      <td>297.728</td>
      <td>8.67</td>
    </tr>
    <tr>
      <th>79</th>
      <td>1.0</td>
      <td>us</td>
      <td>88.0</td>
      <td>21.35</td>
      <td>-158.09</td>
      <td>makakilo city</td>
      <td>292.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>89</th>
      <td>40.0</td>
      <td>ws</td>
      <td>88.0</td>
      <td>-13.87</td>
      <td>-171.60</td>
      <td>lufilufi</td>
      <td>298.150</td>
      <td>2.60</td>
    </tr>
    <tr>
      <th>91</th>
      <td>1.0</td>
      <td>us</td>
      <td>82.0</td>
      <td>19.73</td>
      <td>-155.09</td>
      <td>hilo</td>
      <td>290.150</td>
      <td>2.60</td>
    </tr>
    <tr>
      <th>104</th>
      <td>1.0</td>
      <td>us</td>
      <td>59.0</td>
      <td>57.79</td>
      <td>-152.41</td>
      <td>kodiak</td>
      <td>274.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>110</th>
      <td>64.0</td>
      <td>pf</td>
      <td>100.0</td>
      <td>-16.48</td>
      <td>-151.75</td>
      <td>faanui</td>
      <td>298.653</td>
      <td>6.65</td>
    </tr>
    <tr>
      <th>113</th>
      <td>1.0</td>
      <td>us</td>
      <td>88.0</td>
      <td>21.32</td>
      <td>-158.01</td>
      <td>ewa beach</td>
      <td>292.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>123</th>
      <td>1.0</td>
      <td>us</td>
      <td>93.0</td>
      <td>20.88</td>
      <td>-156.68</td>
      <td>lahaina</td>
      <td>291.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>124</th>
      <td>20.0</td>
      <td>us</td>
      <td>82.0</td>
      <td>21.31</td>
      <td>-157.86</td>
      <td>honolulu</td>
      <td>292.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>125</th>
      <td>20.0</td>
      <td>us</td>
      <td>93.0</td>
      <td>21.50</td>
      <td>-158.02</td>
      <td>wahiawa</td>
      <td>292.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>133</th>
      <td>44.0</td>
      <td>pf</td>
      <td>100.0</td>
      <td>-16.52</td>
      <td>-151.75</td>
      <td>vaitape</td>
      <td>298.178</td>
      <td>7.45</td>
    </tr>
    <tr>
      <th>136</th>
      <td>1.0</td>
      <td>us</td>
      <td>93.0</td>
      <td>20.79</td>
      <td>-156.47</td>
      <td>kihei</td>
      <td>290.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>137</th>
      <td>1.0</td>
      <td>us</td>
      <td>93.0</td>
      <td>20.89</td>
      <td>-156.47</td>
      <td>kahului</td>
      <td>290.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>138</th>
      <td>20.0</td>
      <td>us</td>
      <td>82.0</td>
      <td>21.40</td>
      <td>-157.74</td>
      <td>kailua</td>
      <td>292.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>139</th>
      <td>20.0</td>
      <td>us</td>
      <td>82.0</td>
      <td>21.44</td>
      <td>-157.84</td>
      <td>ahuimanu</td>
      <td>292.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>142</th>
      <td>1.0</td>
      <td>us</td>
      <td>91.0</td>
      <td>60.55</td>
      <td>-151.26</td>
      <td>kenai</td>
      <td>257.150</td>
      <td>5.45</td>
    </tr>
    <tr>
      <th>154</th>
      <td>1.0</td>
      <td>us</td>
      <td>68.0</td>
      <td>59.64</td>
      <td>-151.55</td>
      <td>homer</td>
      <td>272.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>159</th>
      <td>0.0</td>
      <td>pf</td>
      <td>100.0</td>
      <td>-22.43</td>
      <td>-151.33</td>
      <td>moerai</td>
      <td>296.278</td>
      <td>8.15</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4479</th>
      <td>75.0</td>
      <td>in</td>
      <td>94.0</td>
      <td>24.20</td>
      <td>91.83</td>
      <td>kamalpur</td>
      <td>298.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>4480</th>
      <td>40.0</td>
      <td>in</td>
      <td>88.0</td>
      <td>25.90</td>
      <td>91.88</td>
      <td>nongpoh</td>
      <td>298.150</td>
      <td>1.05</td>
    </tr>
    <tr>
      <th>4481</th>
      <td>0.0</td>
      <td>in</td>
      <td>60.0</td>
      <td>27.58</td>
      <td>91.87</td>
      <td>tawang</td>
      <td>277.828</td>
      <td>0.50</td>
    </tr>
    <tr>
      <th>4483</th>
      <td>0.0</td>
      <td>cn</td>
      <td>70.0</td>
      <td>42.80</td>
      <td>93.45</td>
      <td>hami</td>
      <td>267.328</td>
      <td>2.62</td>
    </tr>
    <tr>
      <th>4484</th>
      <td>0.0</td>
      <td>mn</td>
      <td>62.0</td>
      <td>49.98</td>
      <td>92.07</td>
      <td>ulaangom</td>
      <td>248.778</td>
      <td>1.05</td>
    </tr>
    <tr>
      <th>4487</th>
      <td>40.0</td>
      <td>ru</td>
      <td>68.0</td>
      <td>55.96</td>
      <td>92.36</td>
      <td>divnogorsk</td>
      <td>271.150</td>
      <td>3.00</td>
    </tr>
    <tr>
      <th>4488</th>
      <td>92.0</td>
      <td>ru</td>
      <td>92.0</td>
      <td>57.63</td>
      <td>92.27</td>
      <td>pirovskoye</td>
      <td>269.253</td>
      <td>2.42</td>
    </tr>
    <tr>
      <th>4507</th>
      <td>20.0</td>
      <td>mm</td>
      <td>80.0</td>
      <td>18.28</td>
      <td>95.32</td>
      <td>myanaung</td>
      <td>299.528</td>
      <td>1.67</td>
    </tr>
    <tr>
      <th>4508</th>
      <td>0.0</td>
      <td>mm</td>
      <td>78.0</td>
      <td>20.18</td>
      <td>94.88</td>
      <td>minbu</td>
      <td>298.978</td>
      <td>2.05</td>
    </tr>
    <tr>
      <th>4509</th>
      <td>8.0</td>
      <td>mm</td>
      <td>96.0</td>
      <td>22.92</td>
      <td>93.68</td>
      <td>falam</td>
      <td>291.153</td>
      <td>0.32</td>
    </tr>
    <tr>
      <th>4510</th>
      <td>0.0</td>
      <td>in</td>
      <td>93.0</td>
      <td>24.33</td>
      <td>93.67</td>
      <td>churachandpur</td>
      <td>291.228</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>4511</th>
      <td>0.0</td>
      <td>in</td>
      <td>90.0</td>
      <td>26.02</td>
      <td>93.78</td>
      <td>bokajan</td>
      <td>292.128</td>
      <td>0.37</td>
    </tr>
    <tr>
      <th>4512</th>
      <td>56.0</td>
      <td>in</td>
      <td>94.0</td>
      <td>27.63</td>
      <td>93.83</td>
      <td>ziro</td>
      <td>286.778</td>
      <td>0.50</td>
    </tr>
    <tr>
      <th>4513</th>
      <td>20.0</td>
      <td>in</td>
      <td>88.0</td>
      <td>28.17</td>
      <td>94.77</td>
      <td>along</td>
      <td>288.828</td>
      <td>0.67</td>
    </tr>
    <tr>
      <th>4515</th>
      <td>0.0</td>
      <td>cn</td>
      <td>83.0</td>
      <td>40.28</td>
      <td>97.20</td>
      <td>yumen</td>
      <td>267.903</td>
      <td>4.77</td>
    </tr>
    <tr>
      <th>4517</th>
      <td>24.0</td>
      <td>ru</td>
      <td>51.0</td>
      <td>50.26</td>
      <td>95.16</td>
      <td>erzin</td>
      <td>251.503</td>
      <td>1.00</td>
    </tr>
    <tr>
      <th>4518</th>
      <td>20.0</td>
      <td>ru</td>
      <td>59.0</td>
      <td>50.60</td>
      <td>95.00</td>
      <td>samagaltay</td>
      <td>252.978</td>
      <td>1.05</td>
    </tr>
    <tr>
      <th>4519</th>
      <td>12.0</td>
      <td>ru</td>
      <td>67.0</td>
      <td>52.15</td>
      <td>93.92</td>
      <td>turan</td>
      <td>248.753</td>
      <td>0.77</td>
    </tr>
    <tr>
      <th>4520</th>
      <td>8.0</td>
      <td>ru</td>
      <td>54.0</td>
      <td>54.17</td>
      <td>93.30</td>
      <td>koshurnikovo</td>
      <td>252.128</td>
      <td>1.05</td>
    </tr>
    <tr>
      <th>4521</th>
      <td>24.0</td>
      <td>ru</td>
      <td>80.0</td>
      <td>55.72</td>
      <td>93.76</td>
      <td>shalinskoye</td>
      <td>266.603</td>
      <td>2.52</td>
    </tr>
    <tr>
      <th>4522</th>
      <td>92.0</td>
      <td>ru</td>
      <td>93.0</td>
      <td>57.70</td>
      <td>93.28</td>
      <td>kazachinskoye</td>
      <td>269.028</td>
      <td>2.20</td>
    </tr>
    <tr>
      <th>4523</th>
      <td>88.0</td>
      <td>ru</td>
      <td>78.0</td>
      <td>60.37</td>
      <td>93.04</td>
      <td>severo-yeniseyskiy</td>
      <td>258.903</td>
      <td>1.05</td>
    </tr>
    <tr>
      <th>4524</th>
      <td>88.0</td>
      <td>ru</td>
      <td>63.0</td>
      <td>61.67</td>
      <td>96.37</td>
      <td>baykit</td>
      <td>250.353</td>
      <td>1.60</td>
    </tr>
    <tr>
      <th>4527</th>
      <td>64.0</td>
      <td>ru</td>
      <td>62.0</td>
      <td>71.97</td>
      <td>102.50</td>
      <td>khatanga</td>
      <td>251.378</td>
      <td>3.75</td>
    </tr>
    <tr>
      <th>4538</th>
      <td>0.0</td>
      <td>id</td>
      <td>99.0</td>
      <td>5.38</td>
      <td>95.96</td>
      <td>sigli</td>
      <td>297.928</td>
      <td>1.95</td>
    </tr>
    <tr>
      <th>4540</th>
      <td>32.0</td>
      <td>th</td>
      <td>99.0</td>
      <td>9.97</td>
      <td>98.63</td>
      <td>ranong</td>
      <td>301.478</td>
      <td>2.35</td>
    </tr>
    <tr>
      <th>4542</th>
      <td>44.0</td>
      <td>mm</td>
      <td>94.0</td>
      <td>14.08</td>
      <td>98.20</td>
      <td>dawei</td>
      <td>298.578</td>
      <td>1.05</td>
    </tr>
    <tr>
      <th>4543</th>
      <td>20.0</td>
      <td>mm</td>
      <td>94.0</td>
      <td>16.28</td>
      <td>95.68</td>
      <td>pyapon</td>
      <td>299.528</td>
      <td>3.10</td>
    </tr>
    <tr>
      <th>4545</th>
      <td>0.0</td>
      <td>mm</td>
      <td>72.0</td>
      <td>19.73</td>
      <td>96.22</td>
      <td>pyinmana</td>
      <td>299.178</td>
      <td>2.37</td>
    </tr>
    <tr>
      <th>4546</th>
      <td>8.0</td>
      <td>mm</td>
      <td>83.0</td>
      <td>21.97</td>
      <td>96.08</td>
      <td>mandalay</td>
      <td>297.478</td>
      <td>1.92</td>
    </tr>
  </tbody>
</table>
<p>2243 rows × 8 columns</p>
</div>




```python
#cities remaining after cut
df_remain = pd.DataFrame(cities_cut)
df_remain = df_remain.dropna()
df_remain = df_remain.drop_duplicates()
df_remain
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>clouds</th>
      <th>country</th>
      <th>hum</th>
      <th>lat</th>
      <th>lng</th>
      <th>name</th>
      <th>temp</th>
      <th>wind</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>40</td>
      <td>to</td>
      <td>94</td>
      <td>-21.20</td>
      <td>-175.20</td>
      <td>vaini</td>
      <td>299.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>us</td>
      <td>93</td>
      <td>22.08</td>
      <td>-159.32</td>
      <td>kapaa</td>
      <td>294.150</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>2</th>
      <td>92</td>
      <td>ru</td>
      <td>100</td>
      <td>64.38</td>
      <td>-173.30</td>
      <td>provideniya</td>
      <td>274.078</td>
      <td>12.72</td>
    </tr>
    <tr>
      <th>3</th>
      <td>92</td>
      <td>ru</td>
      <td>84</td>
      <td>66.32</td>
      <td>-179.17</td>
      <td>egvekinot</td>
      <td>266.328</td>
      <td>3.30</td>
    </tr>
    <tr>
      <th>4</th>
      <td>40</td>
      <td>to</td>
      <td>94</td>
      <td>-18.65</td>
      <td>-173.98</td>
      <td>neiafu</td>
      <td>299.150</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>5</th>
      <td>64</td>
      <td>to</td>
      <td>100</td>
      <td>-19.80</td>
      <td>-174.35</td>
      <td>pangai</td>
      <td>299.628</td>
      <td>6.92</td>
    </tr>
    <tr>
      <th>6</th>
      <td>88</td>
      <td>ru</td>
      <td>100</td>
      <td>65.58</td>
      <td>-171.00</td>
      <td>lavrentiya</td>
      <td>272.653</td>
      <td>10.60</td>
    </tr>
    <tr>
      <th>7</th>
      <td>92</td>
      <td>nu</td>
      <td>94</td>
      <td>-19.06</td>
      <td>-169.92</td>
      <td>alofi</td>
      <td>298.150</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1</td>
      <td>us</td>
      <td>64</td>
      <td>41.37</td>
      <td>-73.41</td>
      <td>bethel</td>
      <td>280.150</td>
      <td>2.35</td>
    </tr>
    <tr>
      <th>9</th>
      <td>90</td>
      <td>us</td>
      <td>85</td>
      <td>71.29</td>
      <td>-156.79</td>
      <td>barrow</td>
      <td>262.150</td>
      <td>4.10</td>
    </tr>
    <tr>
      <th>10</th>
      <td>20</td>
      <td>us</td>
      <td>93</td>
      <td>21.39</td>
      <td>-158.15</td>
      <td>nanakuli</td>
      <td>292.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>11</th>
      <td>90</td>
      <td>us</td>
      <td>79</td>
      <td>64.50</td>
      <td>-165.41</td>
      <td>nome</td>
      <td>269.150</td>
      <td>4.60</td>
    </tr>
    <tr>
      <th>12</th>
      <td>88</td>
      <td>ck</td>
      <td>100</td>
      <td>-21.21</td>
      <td>-159.78</td>
      <td>avarua</td>
      <td>297.728</td>
      <td>8.67</td>
    </tr>
    <tr>
      <th>13</th>
      <td>40</td>
      <td>ws</td>
      <td>88</td>
      <td>-13.87</td>
      <td>-171.60</td>
      <td>lufilufi</td>
      <td>298.150</td>
      <td>2.60</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1</td>
      <td>us</td>
      <td>82</td>
      <td>19.73</td>
      <td>-155.09</td>
      <td>hilo</td>
      <td>290.150</td>
      <td>2.60</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1</td>
      <td>us</td>
      <td>59</td>
      <td>57.79</td>
      <td>-152.41</td>
      <td>kodiak</td>
      <td>274.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>16</th>
      <td>64</td>
      <td>pf</td>
      <td>100</td>
      <td>-16.48</td>
      <td>-151.75</td>
      <td>faanui</td>
      <td>298.653</td>
      <td>6.65</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1</td>
      <td>us</td>
      <td>93</td>
      <td>20.88</td>
      <td>-156.68</td>
      <td>lahaina</td>
      <td>291.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1</td>
      <td>us</td>
      <td>91</td>
      <td>60.55</td>
      <td>-151.26</td>
      <td>kenai</td>
      <td>257.150</td>
      <td>5.45</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1</td>
      <td>us</td>
      <td>68</td>
      <td>59.64</td>
      <td>-151.55</td>
      <td>homer</td>
      <td>272.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>20</th>
      <td>0</td>
      <td>pf</td>
      <td>100</td>
      <td>-22.43</td>
      <td>-151.33</td>
      <td>moerai</td>
      <td>296.278</td>
      <td>8.15</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0</td>
      <td>pf</td>
      <td>100</td>
      <td>-9.80</td>
      <td>-139.03</td>
      <td>atuona</td>
      <td>299.678</td>
      <td>8.07</td>
    </tr>
    <tr>
      <th>22</th>
      <td>1</td>
      <td>us</td>
      <td>84</td>
      <td>61.22</td>
      <td>-149.90</td>
      <td>anchorage</td>
      <td>260.150</td>
      <td>2.60</td>
    </tr>
    <tr>
      <th>23</th>
      <td>20</td>
      <td>us</td>
      <td>82</td>
      <td>64.86</td>
      <td>-147.80</td>
      <td>college</td>
      <td>248.150</td>
      <td>1.85</td>
    </tr>
    <tr>
      <th>24</th>
      <td>56</td>
      <td>pf</td>
      <td>78</td>
      <td>-17.83</td>
      <td>-149.27</td>
      <td>teahupoo</td>
      <td>298.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>25</th>
      <td>75</td>
      <td>us</td>
      <td>70</td>
      <td>39.01</td>
      <td>-77.43</td>
      <td>sterling</td>
      <td>284.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>26</th>
      <td>75</td>
      <td>us</td>
      <td>63</td>
      <td>42.16</td>
      <td>-72.33</td>
      <td>palmer</td>
      <td>276.150</td>
      <td>1.50</td>
    </tr>
    <tr>
      <th>27</th>
      <td>1</td>
      <td>us</td>
      <td>100</td>
      <td>40.60</td>
      <td>-124.16</td>
      <td>fortuna</td>
      <td>275.150</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>28</th>
      <td>90</td>
      <td>us</td>
      <td>100</td>
      <td>57.05</td>
      <td>-135.33</td>
      <td>sitka</td>
      <td>275.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>29</th>
      <td>90</td>
      <td>ca</td>
      <td>84</td>
      <td>68.22</td>
      <td>-135.01</td>
      <td>aklavik</td>
      <td>259.150</td>
      <td>5.10</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1469</th>
      <td>20</td>
      <td>ru</td>
      <td>89</td>
      <td>56.22</td>
      <td>88.12</td>
      <td>suslovo</td>
      <td>269.603</td>
      <td>2.80</td>
    </tr>
    <tr>
      <th>1470</th>
      <td>64</td>
      <td>ru</td>
      <td>88</td>
      <td>69.49</td>
      <td>88.40</td>
      <td>talnakh</td>
      <td>247.153</td>
      <td>1.52</td>
    </tr>
    <tr>
      <th>1471</th>
      <td>12</td>
      <td>id</td>
      <td>100</td>
      <td>5.56</td>
      <td>95.32</td>
      <td>banda aceh</td>
      <td>296.103</td>
      <td>1.22</td>
    </tr>
    <tr>
      <th>1472</th>
      <td>40</td>
      <td>bd</td>
      <td>83</td>
      <td>24.10</td>
      <td>90.10</td>
      <td>mirzapur</td>
      <td>298.150</td>
      <td>1.30</td>
    </tr>
    <tr>
      <th>1473</th>
      <td>20</td>
      <td>ru</td>
      <td>51</td>
      <td>50.35</td>
      <td>90.50</td>
      <td>mugur-aksy</td>
      <td>247.103</td>
      <td>0.92</td>
    </tr>
    <tr>
      <th>1474</th>
      <td>68</td>
      <td>ru</td>
      <td>83</td>
      <td>54.00</td>
      <td>90.25</td>
      <td>sorsk</td>
      <td>262.428</td>
      <td>1.60</td>
    </tr>
    <tr>
      <th>1475</th>
      <td>80</td>
      <td>ru</td>
      <td>83</td>
      <td>60.38</td>
      <td>92.63</td>
      <td>teya</td>
      <td>262.178</td>
      <td>1.37</td>
    </tr>
    <tr>
      <th>1476</th>
      <td>44</td>
      <td>id</td>
      <td>100</td>
      <td>-6.88</td>
      <td>112.21</td>
      <td>labuhan</td>
      <td>300.753</td>
      <td>3.32</td>
    </tr>
    <tr>
      <th>1477</th>
      <td>92</td>
      <td>id</td>
      <td>100</td>
      <td>1.74</td>
      <td>98.78</td>
      <td>sibolga</td>
      <td>294.228</td>
      <td>0.47</td>
    </tr>
    <tr>
      <th>1478</th>
      <td>20</td>
      <td>bd</td>
      <td>88</td>
      <td>22.20</td>
      <td>92.23</td>
      <td>bandarban</td>
      <td>300.150</td>
      <td>2.10</td>
    </tr>
    <tr>
      <th>1479</th>
      <td>0</td>
      <td>in</td>
      <td>60</td>
      <td>27.58</td>
      <td>91.87</td>
      <td>tawang</td>
      <td>277.828</td>
      <td>0.50</td>
    </tr>
    <tr>
      <th>1480</th>
      <td>0</td>
      <td>cn</td>
      <td>70</td>
      <td>42.80</td>
      <td>93.45</td>
      <td>hami</td>
      <td>267.328</td>
      <td>2.62</td>
    </tr>
    <tr>
      <th>1481</th>
      <td>0</td>
      <td>mn</td>
      <td>62</td>
      <td>49.98</td>
      <td>92.07</td>
      <td>ulaangom</td>
      <td>248.778</td>
      <td>1.05</td>
    </tr>
    <tr>
      <th>1482</th>
      <td>40</td>
      <td>ru</td>
      <td>68</td>
      <td>55.96</td>
      <td>92.36</td>
      <td>divnogorsk</td>
      <td>271.150</td>
      <td>3.00</td>
    </tr>
    <tr>
      <th>1483</th>
      <td>92</td>
      <td>ru</td>
      <td>92</td>
      <td>57.63</td>
      <td>92.27</td>
      <td>pirovskoye</td>
      <td>269.253</td>
      <td>2.42</td>
    </tr>
    <tr>
      <th>1484</th>
      <td>20</td>
      <td>mm</td>
      <td>80</td>
      <td>18.28</td>
      <td>95.32</td>
      <td>myanaung</td>
      <td>299.528</td>
      <td>1.67</td>
    </tr>
    <tr>
      <th>1485</th>
      <td>0</td>
      <td>mm</td>
      <td>78</td>
      <td>20.18</td>
      <td>94.88</td>
      <td>minbu</td>
      <td>298.978</td>
      <td>2.05</td>
    </tr>
    <tr>
      <th>1486</th>
      <td>0</td>
      <td>in</td>
      <td>93</td>
      <td>24.33</td>
      <td>93.67</td>
      <td>churachandpur</td>
      <td>291.228</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>1487</th>
      <td>0</td>
      <td>in</td>
      <td>90</td>
      <td>26.02</td>
      <td>93.78</td>
      <td>bokajan</td>
      <td>292.128</td>
      <td>0.37</td>
    </tr>
    <tr>
      <th>1488</th>
      <td>20</td>
      <td>in</td>
      <td>88</td>
      <td>28.17</td>
      <td>94.77</td>
      <td>along</td>
      <td>288.828</td>
      <td>0.67</td>
    </tr>
    <tr>
      <th>1489</th>
      <td>0</td>
      <td>cn</td>
      <td>83</td>
      <td>40.28</td>
      <td>97.20</td>
      <td>yumen</td>
      <td>267.903</td>
      <td>4.77</td>
    </tr>
    <tr>
      <th>1490</th>
      <td>24</td>
      <td>ru</td>
      <td>51</td>
      <td>50.26</td>
      <td>95.16</td>
      <td>erzin</td>
      <td>251.503</td>
      <td>1.00</td>
    </tr>
    <tr>
      <th>1491</th>
      <td>12</td>
      <td>ru</td>
      <td>67</td>
      <td>52.15</td>
      <td>93.92</td>
      <td>turan</td>
      <td>248.753</td>
      <td>0.77</td>
    </tr>
    <tr>
      <th>1492</th>
      <td>88</td>
      <td>ru</td>
      <td>63</td>
      <td>61.67</td>
      <td>96.37</td>
      <td>baykit</td>
      <td>250.353</td>
      <td>1.60</td>
    </tr>
    <tr>
      <th>1493</th>
      <td>64</td>
      <td>ru</td>
      <td>62</td>
      <td>71.97</td>
      <td>102.50</td>
      <td>khatanga</td>
      <td>251.378</td>
      <td>3.75</td>
    </tr>
    <tr>
      <th>1494</th>
      <td>32</td>
      <td>th</td>
      <td>99</td>
      <td>9.97</td>
      <td>98.63</td>
      <td>ranong</td>
      <td>301.478</td>
      <td>2.35</td>
    </tr>
    <tr>
      <th>1495</th>
      <td>44</td>
      <td>mm</td>
      <td>94</td>
      <td>14.08</td>
      <td>98.20</td>
      <td>dawei</td>
      <td>298.578</td>
      <td>1.05</td>
    </tr>
    <tr>
      <th>1496</th>
      <td>20</td>
      <td>mm</td>
      <td>94</td>
      <td>16.28</td>
      <td>95.68</td>
      <td>pyapon</td>
      <td>299.528</td>
      <td>3.10</td>
    </tr>
    <tr>
      <th>1497</th>
      <td>0</td>
      <td>mm</td>
      <td>72</td>
      <td>19.73</td>
      <td>96.22</td>
      <td>pyinmana</td>
      <td>299.178</td>
      <td>2.37</td>
    </tr>
    <tr>
      <th>1498</th>
      <td>8</td>
      <td>mm</td>
      <td>83</td>
      <td>21.97</td>
      <td>96.08</td>
      <td>mandalay</td>
      <td>297.478</td>
      <td>1.92</td>
    </tr>
  </tbody>
</table>
<p>1499 rows × 8 columns</p>
</div>




```python
#binning to get equal representation across latitudes allows more accurate histograms of weather data
#instead of false high densities because of high volume of cities in NA / EU / N. Asia
bins = [-60,-30,0,30,60,100]
binned = pd.cut(df_remain['lat'], bins, labels = range(len(bins)-1))
df_remain['lat_bin'] = binned

#min bin volume determines bin sample size if bin volume < 100 yields 500 samples max
#bin with fewest datapoints will not be sampled randomly in next cell... 
#all datapoints will be taken to boost overall sample size

sampler = df_remain.groupby('lat_bin')['temp'].count().min()
if sampler > 100:
    sampler = 100

print(sampler * (len(bins)-1), ' total sample population')
```

    295  total sample population



```python

df = pd.DataFrame({})
for i in range(len(bins)-1):
    lat_filter = df_remain['lat_bin'] == i
    #sample of smallest bin not random if bin volume < 100
    sub_df = df_remain[lat_filter].sample(n=sampler)
    df = df.append(sub_df)
print(len(df['name']))
df.head()

```

    295





<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>clouds</th>
      <th>country</th>
      <th>hum</th>
      <th>lat</th>
      <th>lng</th>
      <th>name</th>
      <th>temp</th>
      <th>wind</th>
      <th>lat_bin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1067</th>
      <td>0</td>
      <td>za</td>
      <td>80</td>
      <td>-30.86</td>
      <td>30.37</td>
      <td>margate</td>
      <td>296.403</td>
      <td>2.82</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1020</th>
      <td>0</td>
      <td>za</td>
      <td>75</td>
      <td>-33.59</td>
      <td>26.89</td>
      <td>port alfred</td>
      <td>292.728</td>
      <td>4.10</td>
      <td>0</td>
    </tr>
    <tr>
      <th>968</th>
      <td>0</td>
      <td>za</td>
      <td>14</td>
      <td>-30.65</td>
      <td>24.01</td>
      <td>de aar</td>
      <td>298.503</td>
      <td>5.85</td>
      <td>0</td>
    </tr>
    <tr>
      <th>388</th>
      <td>75</td>
      <td>ar</td>
      <td>61</td>
      <td>-41.15</td>
      <td>-71.31</td>
      <td>san carlos de bariloche</td>
      <td>282.150</td>
      <td>12.90</td>
      <td>0</td>
    </tr>
    <tr>
      <th>967</th>
      <td>0</td>
      <td>za</td>
      <td>26</td>
      <td>-32.25</td>
      <td>24.53</td>
      <td>graaff-reinet</td>
      <td>298.628</td>
      <td>2.20</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#overrepresents islands and coasts especially extremities
df_uncut.plot('lng','lat', kind = 'scatter',s = 1, figsize=(8, 5))
plt.title('Datapoint Spread Precut')


df_cut.plot('lng','lat', kind = 'scatter',s = 1, figsize=(8, 5))
plt.title('Removed Datapoints')


df_remain.plot('lng','lat', kind = 'scatter',s = 1, figsize=(8, 5))
plt.title('Datapoint Spread Trimmed')


df.plot('lng','lat', kind = 'scatter',s = 1, figsize=(8, 5))
plt.title('Datapoint Spread Sampled from Trimmed')
plt.show()
```


![png](output_10_0.png)



![png](output_10_1.png)



![png](output_10_2.png)



![png](output_10_3.png)



```python
gridsize = 25
bins=[0,3,6,9]

plt.hexbin(df_uncut['lng'], df_uncut['lat'], gridsize = gridsize, bins=bins)
plt.title('Precut')
plt.xlabel('Latitude')
plt.ylabel('Longitude')
plt.show()

plt.hexbin(df_cut['lng'], df_cut['lat'], gridsize = gridsize, bins=bins)
plt.title('Cut Data')
plt.xlabel('Latitude')
plt.ylabel('Longitude')
plt.show()


plt.hexbin(df_remain['lng'], df_remain['lat'], gridsize = gridsize, bins=bins)
plt.title('Postcut')
plt.xlabel('Latitude')
plt.ylabel('Longitude')
plt.show()
```


![png](output_11_0.png)



![png](output_11_1.png)



![png](output_11_2.png)



```python
plt.hist(df_remain['lat'], 6)
plt.title('Distribution of Trimmed Dataset')
plt.xlabel('Latitude')
plt.ylabel('Num of Datapoints')
plt.show()


plt.hist(df['lat'], 6)
plt.title('Distribution of Representative Sample')
plt.xlabel('Latitude')
plt.ylabel('Num of Datapoints')
plt.show()
```


![png](output_12_0.png)



![png](output_12_1.png)



```python
df_remain.plot('lat','temp', kind = 'scatter', s=.5, figsize=(10, 6))
plt.xlabel('Latitude')
plt.ylabel('Max Temperature øK')
plt.title('Max Temp vs Latitude; Trimmed Data')
plt.show()

df.plot('lat','temp', kind = 'scatter', s=2, figsize=(10, 6))
plt.xlabel('Latitude')
plt.ylabel('Max Temperature øK')
plt.title('Max Temp vs Latitude; Representative Sample from Trimmed Data')
plt.show()
```


![png](output_13_0.png)



![png](output_13_1.png)



```python
plt.hexbin(df_remain['lng'], df_remain['lat'], C = df_remain['temp'] gridsize = gridsize, bins=bins)
plt.title('Postcut')
plt.xlabel('Latitude')
plt.ylabel('Longitude')
plt.show()
```


```python
plt.pcolormesh(df_remain['lng'], df_remain['lat'], )
plt.show()
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-122-c5c992decdb2> in <module>()
    ----> 1 plt.pcolormesh(df_remain['lng'], df_remain['lat'], )
          2 plt.show()


    ~/anaconda/envs/pydata/lib/python3.6/site-packages/matplotlib/pyplot.py in pcolormesh(*args, **kwargs)
       3165                       mplDeprecation)
       3166     try:
    -> 3167         ret = ax.pcolormesh(*args, **kwargs)
       3168     finally:
       3169         ax._hold = washold


    ~/anaconda/envs/pydata/lib/python3.6/site-packages/matplotlib/__init__.py in inner(ax, *args, **kwargs)
       1708                     warnings.warn(msg % (label_namer, func.__name__),
       1709                                   RuntimeWarning, stacklevel=2)
    -> 1710             return func(ax, *args, **kwargs)
       1711         pre_doc = inner.__doc__
       1712         if pre_doc is None:


    ~/anaconda/envs/pydata/lib/python3.6/site-packages/matplotlib/axes/_axes.py in pcolormesh(self, *args, **kwargs)
       5623         allmatch = (shading == 'gouraud')
       5624 
    -> 5625         X, Y, C = self._pcolorargs('pcolormesh', *args, allmatch=allmatch)
       5626         Ny, Nx = X.shape
       5627         X = X.ravel()


    ~/anaconda/envs/pydata/lib/python3.6/site-packages/matplotlib/axes/_axes.py in _pcolorargs(funcname, *args, **kw)
       5244         else:
       5245             raise TypeError(
    -> 5246                 'Illegal arguments to %s; see help(%s)' % (funcname, funcname))
       5247 
       5248         Nx = X.shape[-1]


    TypeError: Illegal arguments to pcolormesh; see help(pcolormesh)



```python
df_remain.plot('lat', 'hum', kind = 'scatter', s=.5, figsize=(10, 6))
plt.xlabel('Latitude')
plt.ylabel('% Humidity')
plt.title('Latitude vs Humidity: Trimmed Data')
plt.show()

df.plot('lat', 'hum', kind = 'scatter', s=2, figsize=(10, 6))
plt.xlabel('Latitude')
plt.ylabel('% Humidity')
plt.title('Latitude vs Humidity: Representative Sample from Trimmed Data')
plt.show()
```


![png](output_16_0.png)



![png](output_16_1.png)



```python
plt.hexbin(df['lat'], df['hum'], gridsize = 20, bins=None)
plt.xlabel('Latitude')
plt.ylabel('% Humidity')
plt.title('Latitude vs Humidity Heatmap')
plt.show()
```


![png](output_17_0.png)



```python
plt.hist2d(df['lat'], df['hum'], bins=15)
plt.xlabel('Latitude')
plt.ylabel('% Humidity')
plt.show()
```


![png](output_18_0.png)



```python
df_remain.plot('lat','clouds', kind = 'scatter', s=.5,figsize=(10, 3))
plt.xlabel('Latitude')
plt.ylabel('% Cloud Cover')
plt.title('Latitude vs Cloud Cover; Trimmed Data')
plt.show()

df.plot('lat','clouds', kind = 'scatter', s=.5,figsize=(10, 3))
plt.xlabel('Latitude')
plt.ylabel('% Cloud Cover')
plt.title('Latitude vs Cloud Cover; Representative Sample from Trimmed Data')
plt.show()
```


![png](output_19_0.png)



![png](output_19_1.png)



```python
df_remain.plot('lng', 'lat', kind = 'scatter', s=df_remain['clouds']+.1 ,figsize=(10, 6))
plt.title('Cloud Cover Over Cities')
plt.show()
```


![png](output_20_0.png)



```python
df_remain.plot('lat', 'wind', kind = 'scatter', s=.25, figsize=(10, 4))
plt.xlabel('Latitude')
plt.ylabel('Windspeed')
plt.title('Latitude vs Windspeed; Trimmed Data')
plt.show()

df.plot('lat', 'wind', kind = 'scatter', s=2, figsize=(10, 4))
plt.xlabel('Latitude')
plt.ylabel('Windspeed')
plt.title('Latitude vs Windspeed; Representative Sample from Trimmed Data')
plt.show()
```


![png](output_21_0.png)



![png](output_21_1.png)



```python
plt.hexbin(df['lat'], df['wind'], gridsize = 20, bins=None)
plt.xlabel('Latitude')
plt.ylabel('Windspeed')
plt.show()
```


![png](output_22_0.png)


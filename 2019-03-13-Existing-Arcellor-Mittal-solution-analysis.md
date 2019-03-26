---
title: Existing Arcellor Mittal solution analysis
layout: post
author: pawel.niewiadomski
permalink: /existing-arcellor-mittal-solution-analysis/
source-id: 1gx3xmErojy1nRPJ8MaGDARxJaZaNLVqgynLBsnr5m9g
published: true
---
**Existing Arcellor Mittal solution analysis**:

1. Configuration

    1. Mysql db

    2. Version of hybris running:

#Fri May 12 11:41:11 GMT 2017

builddate=20170512 1140

version=6.4.0.0

    3. Spring version (core) 4.3.3.

    4. Accelerator version

#Sat Apr 22 20:33:34 UTC 2017

builddate=20170422 2033

version=6.3.0.0-SNAPSHOT

    5. B2B Accelerator version

#Thu May 04 16:28:16 UTC 2017

builddate=20170504 1628

releasedate=20170427 0956

version=6.4.0.0

    6. Backoffice - 6.4

    7. cockpits - 6.3

    8. Local.properties - for DEV no sites, no db params, no tomcat settings - strange local file without these params (the current is production one) 

2. Customize 

    9. Two spring files overriden:

        1. ext-integration\sap\masterdata\sapcustomerb2b\resources\sapcustomerb2b-spring.xml

        2. ext-integration\sap\synchronousOM\sapordermgmtb2bfacades\resources\sapordermgmtb2bfacades-spring.xml

    10. Impex for mediaconversion:

        3. deleteConvertedMediasJob

        4. mediaConversionJob

        5. extractMediaMetaDataJob

3. Custom extensions 26 in total (16+10) :

    11. amds: accelerator with 4 addons

        6. Amdscore

        7. Amdsbackoffice

        8. Amdscockpits

        9. Amdscommercewebservices

        10. Amdsinitialdata

        11. Amdstest

        12. Amdswsclient

        13. Amdsfacades

        14. Amdsfulfilmentprocess

        15. Amdsstorefront

        16. Amdsaccountsummariesaddon

        17. Amdscheckoutaddon

        18. Amdscommerceorgaddon

        19. Amdscustomerticketingaddon

        20. Mercanetcore

        21. updatedata

    12. ssc: b2b accelerator with 2 addons

        22. Ssccore

        23. Sscinitialdata

        24. Ssccockpits

        25. Ssctest

        26. Sscfulfilmentprocess

        27. Sscwsclient

        28. Sscfacades

        29. Sscstorefront

        30. Sscb2baddon

        31. sscearlyloginaddon

    13. Some extensions contain apparel/electronics demo files like amdscommerceorgadon

4. Build process

    14. Clean - SUCCESSFUL

 [echo] Removing link D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\smartedit/web/webroot/static-resources/dist/smartedit/css

 	[exec] Invalid switch - "web".

 	[exec] Result: 1

 	[echo] Removing link D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\smartedit/web/webroot/static-resources/dist/smartedit/js

 	[exec] Invalid switch - "web".

 	[exec] Result: 1

 	[echo] clean up of node modules symlink: D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\smartedit\node_modules

 	[echo] Removing link D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\personalizationsmartedit/web/webroot/css

 	[exec] Invalid switch - "web".

 	[exec] Result: 1

 	[echo] Removing link D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\personalizationsmartedit/web/webroot/personalizationsmartedit/js

 	[exec] Invalid switch - "web".

 	[exec] Result: 1

    15. Ant customize - SUCCESSFUL

  [taskdef] Could not load definitions from resource org/jacoco/ant/antlib.xml. It could not be found.

Duplicated project name in import. Project bindImpexTemplates defined first in D:\PROJ\MITTAL\ws_esteel\hybris\bin\custom\ssc\sscinitialdata\resources\sscinitialdata\ant\ant-bind-impex-template.xml and again in D:\PROJ\MITTAL\ws_esteel\hybris\bin\custom\amds\amdsinitialdata\resources\amdsinitialdata\ant\ant-bind-impex-template.xml

    16. Ant build

[testClassesScanner] Warning: you're using at least one deprecated extension!

[testClassesScanner] Please note that they may not be available in future releases.

[testClassesScanner]

[testClassesScanner] Deprecated extensions: [liveeditaddon]

 	[exec] Junction created for D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\personalizationsmartedit\buildArtifacts\static-resources <<===>> D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\smartedit\web\webroot\static-resources

 	[exec] Junction created for D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\personalizationsmartedit\buildArtifacts\seLibraries <<===>> D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\smartedit\seLibraries

 	[echo] FAILED to call grunt packageSkipTests on D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\personalizationsmartedit, node modules not found at D:\PROJ\MITTAL\ws_esteel\hybris\bin\ext-content\npmancillary\resources\npm\node_modules

    17. Hybris start

Wstaje bezproblemowo

    18. Init

Mają swoj patch system ale chyba nie tak elstyczny jak nasz - możliwe, że chcąc startować z tego pułapu, który dostaliśmy trzeba bedzie przeanalizować i skonsolidować wszystkie fixy które mają w swoich patchach do wersji 1.0.0 po naszej stronie a jest tego trochę. 

INFO   | jvm 1	| main	| 2019/03/14 14:12:58.295 | ERROR [hybrisHTTP38] (0000004R) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 3). Finally could not import 557 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 14:12:58.295 | INFO  [impex reader worker [cj:0000004R]] [ImpExWorker] Returning worker impex reader worker [cj:0000004R] to the pool

INFO   | jvm 1	| main	| 2019/03/14 14:12:58.397 | ERROR [hybrisHTTP38] [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000004R for further details

INFO   | jvm 1	| main	| 2019/03/14 14:12:58.397 | ERROR [hybrisHTTP38] [DefaultSetupImpexService] Importing [/amdsinitialdata/import/coredata/common/essential-data.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 14:13:03.368 | ERROR [ImpExWorker<1/16>] [FileLoaderValueTranslator] line 87 at main script: jar:com.arcelormittal.ssc.core.setup.CoreSystemSetup&/ssccore/import/cockpits/cmscockpit/structure-view/structure_contentPage2Template.vm

INFO   | jvm 1	| main	| 2019/03/14 14:13:03.368 | java.lang.IllegalArgumentException: Can not find entry /ssccore/import/cockpits/cmscockpit/structure-view/structure_contentPage2Template.vm using classloader of class com.arcelormittal.ssc.core.setup.CoreSystemSetup

INFO   | jvm 1	| main	| 2019/03/14 14:13:03.369 |     	at de.hybris.platform.commerceservices.impex.impl.FileLoaderValueTranslator.loadFromJarResource(FileLoaderValueTranslator.java:145) ~[commerceservicesserver.jar:?]

INFO  [hybrisHTTP38] (00000070) [Importer] Finished 2 pass in 0d 00h:00m:01s:345ms - processed: 784, dumped: 784 (last pass: 784)

ERROR [hybrisHTTP38] (00000070) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 784 lines![HY-123]

INFO  [impex reader worker [cj:00000070]] [ImpExWorker] Returning worker impex reader worker [cj:00000070] to the pool

ERROR [hybrisHTTP38] [DefaultImportService] Import has caused an error, see logs of cronjob with code=00000070 for further details

ERROR [hybrisHTTP38] [DefaultSetupImpexService] Importing [/amdsinitialdata/import/sampledata/contentCatalogs/AMDS-FR_ContentCatalog/cmsContent/products_content_fr.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 14:13:06.887 | ERROR [hybrisHTTP38] (00000053) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 16 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 14:13:06.887 | INFO  [impex reader worker [cj:00000053]] [ImpExWorker] Returning worker impex reader worker [cj:00000053] to the pool

INFO   | jvm 1	| main	| 2019/03/14 14:13:06.888 | ERROR [hybrisHTTP38] [DefaultImportService] Import has caused an error, see logs of cronjob with code=00000053 for further details

INFO   | jvm 1	| main	| 2019/03/14 14:13:06.888 | ERROR [hybrisHTTP38] [DefaultSetupImpexService] Importing [/amdsinitialdata/import/coredata/contentCatalogs/AMDS-FR_ContentCatalog/cms-content.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 14:13:07.202 | ERROR [hybrisHTTP38] (00000054) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 1 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 14:13:07.202 | INFO  [impex reader worker [cj:00000054]] [ImpExWorker] Returning worker impex reader worker [cj:00000054] to the pool

INFO   | jvm 1	| main	| 2019/03/14 14:13:07.202 | ERROR [hybrisHTTP38] [DefaultImportService] Import has caused an error, see logs of cronjob with code=00000054 for further details

INFO   | jvm 1	| main	| 2019/03/14 14:13:07.202 | ERROR [hybrisHTTP38] [DefaultSetupImpexService] Importing [/amdsinitialdata/import/coredata/contentCatalogs/AMDS-FR_ContentCatalog/cms-content_fr.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 14:11:54.961 | ERROR [hybrisHTTP38] (0000002N) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 271 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 14:11:55.061 | ERROR [hybrisHTTP38] [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000002N for further details

INFO   | jvm 1	| main	| 2019/03/14 14:11:55.061 | ERROR [hybrisHTTP38] [DefaultSetupImpexService] Importing [/amdscore/import/common/essential-data.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 14:12:02.990 | ERROR [hybrisHTTP38] (00000037) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 66 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 14:12:02.990 | INFO  [impex reader worker [cj:00000037]] [ImpExWorker] Returning worker impex reader worker [cj:00000037] to the pool

INFO   | jvm 1	| main	| 2019/03/14 14:12:03.091 | ERROR [hybrisHTTP38] [DefaultImportService] Import has caused an error, see logs of cronjob with code=00000037 for further details

INFO   | jvm 1	| main	| 2019/03/14 14:12:03.091 | ERROR [hybrisHTTP38] [DefaultSetupImpexService] Importing [/amdscore/import/common/categories-classifications.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 14:13:38.408 | ERROR [impex reader worker [cj:00000061]] [ImpExWorker] unexpected error reading : unexpected char 1 after cell end at 3565 in line 110 : ';;AmdsConditionsEnlevementTextParagraph;"<h2><str

dises en agence</strong></h2><p><strong>1. </strong><strong>D&eacute;placements</strong></p><p>&nbsp;&middot; Circuler avec prudence sur le site.</p><p>&middot; Portez les EPI si vous entrez dans l&rsquo;atelier (casque mis &agrave; votre dispo

ant d&rsquo;entrer votre v&eacute;hicule dans l&rsquo;atelier,</p><p>&middot; Interdiction&nbsp;:</p><p>o D&rsquo;acc&eacute;der au stock,</p><p>o De fumer dans les halls</p><p>o De&nbsp;consommer ou d&rsquo;&ecirc;tre sous l&rsquo;emprise de l

INFO   | jvm 1	| main	| 2019/03/14 14:14:10.795 | WARN  [impex result worker [cj:0000006R]] [ImpExImportReader] line 3 at main script: dumped unresolved line ValueLine[unresolvable:no existing item found for update,line 3 at main script,null,HeaderDescriptor[line 2 at main script, update, CMSLinkComponent, {}, [c

atalogVersion, uid, linkName] ],{1=ValueEntry(''=AMDS-FR_ContentCatalog/Staged(8796126052953),unresolved=false,ignore=false), 2=ValueEntry('Carre_Barre_AluminiumCategoryLink'=Carre_Barre_AluminiumCategoryLink,unresolved=false,ignore=false), 3=ValueEntry('CarrĂ©'=null,unresolved=null,ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 14:14:10.795 | INFO  [impex result worker [cj:0000006R]] [ImpExWorker] Returning worker impex result worker [cj:0000006R] to the pool

INFO   | jvm 1	| main	| 2019/03/14 14:14:10.795 | INFO  [hybrisHTTP38] (0000006R) [Importer] Finished 2 pass in 0d 00h:00m:00s:003ms - processed: 1, dumped: 1 (last pass: 1)

INFO   | jvm 1	| main	| 2019/03/14 14:14:10.795 | ERROR [hybrisHTTP38] (0000006R) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 1 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 14:14:10.795 | INFO  [impex reader worker [cj:0000006R]] [ImpExWorker] Returning worker impex reader worker [cj:0000006R] to the pool

INFO   | jvm 1	| main	| 2019/03/14 14:14:10.795 | ERROR [hybrisHTTP38] [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000006R for further details

INFO   | jvm 1	| main	| 2019/03/14 14:14:10.795 | ERROR [hybrisHTTP38] [DefaultSetupImpexService] Importing [/amdsinitialdata/import/sampledata/contentCatalogs/AMDS-FR_ContentCatalog/cmsContent/menu_fr.impex]... FAILED

    19. Init ssc

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.168 | WARN  [impex result worker [cj:0000001W]] (ssc) [ImpExImportReader] line 4 at main script: dumped unresolved line ValueLine[unresolvable:Exception : line 34: cannot update 8796093186080 with values ItemAttributeMap[ registry:  null, type: <null>, data: {active=tru

e, fallbacklanguages=[8796093186080->fr]} ] due to fallback languages cycle detected for 8796093186080->fr and [8796093186080->fr], Exception : line 4: cannot update 8796093186080 with values ItemAttributeMap[ registry:  null, type: <null>, data: {active=true, fallbacklanguages=[8796093186080->fr]} ] due to fallback la

nguages cycle detected for 8796093186080->fr and [8796093186080->fr],line 4 at main script,null,HeaderDescriptor[line 2 at main script, insert_update, Language, {}, [isocode, fallbackLanguages, active] ],{1=ValueEntry('fr'=fr,unresolved=false,ignore=false), 2=ValueEntry('fr'=[8796093186080->fr],unresolved=false,ignore=

false), 3=ValueEntry(''=true,unresolved=false,ignore=false), 4=ValueEntry(''=null,unresolved=null,ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.168 | INFO  [ImpExWorker<10/16>] [ImpExWorker] Returning worker impex worker 10/16 [cj:0000001W] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.168 | INFO  [impex result worker [cj:0000001W]] [ImpExWorker] Returning worker impex result worker [cj:0000001W] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.168 | INFO  [ImpExWorker<7/16>] [ImpExWorker] Returning worker impex worker 7/16 [cj:0000001W] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.168 | INFO  [ImpExWorker<0/16>] [ImpExWorker] Returning worker impex worker 0/16 [cj:0000001W] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.169 | INFO  [ImpExWorker<14/16>] [ImpExWorker] Returning worker impex worker 14/16 [cj:0000001W] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.169 | INFO  [hybrisHTTP18] (ssc) (0000001W) [Importer] Finished 2 pass in 0d 00h:00m:00s:005ms - processed: 2, dumped: 2 (last pass: 2)

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.169 | ERROR [hybrisHTTP18] (ssc) (0000001W) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 2 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.169 | INFO  [impex reader worker [cj:0000001W]] [ImpExWorker] Returning worker impex reader worker [cj:0000001W] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.169 | ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000001W for further details

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.169 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/ssccore/import/common/essential-data.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.483 | WARN  [impex result worker [cj:0000001X]] (ssc) [ImpExImportReader] line 4 at main script: dumped unresolved line ValueLine[unresolvable:no existing item found for update,line 4 at main script,null,HeaderDescriptor[line 2 at main script, update, Currency, {}, [iso

code, name] ],{1=ValueEntry('JPY'=JPY,unresolved=false,ignore=false), 2=ValueEntry('Japanese Yen'=null,unresolved=null,ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.483 | INFO  [impex result worker [cj:0000001X]] [ImpExWorker] Returning worker impex result worker [cj:0000001X] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.483 | INFO  [hybrisHTTP18] (ssc) (0000001X) [Importer] Finished 2 pass in 0d 00h:00m:00s:006ms - processed: 2, dumped: 2 (last pass: 2)

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.483 | ERROR [hybrisHTTP18] (ssc) (0000001X) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 2 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.484 | INFO  [impex reader worker [cj:0000001X]] [ImpExWorker] Returning worker impex reader worker [cj:0000001X] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.585 | ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000001X for further details

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.585 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/ssccore/import/common/essential-data_en.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.586 | INFO  [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/ssccore/import/common/essential-data_de.impex]...

..

INFO   | jvm 1	| main	| 2019/03/14 16:56:37.899 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/ssccore/import/common/essential-data_de.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.612 | WARN  [impex result worker [cj:00000029]] (ssc) [ImpExImportReader] line 17 at main script: dumped unresolved line ValueLine[,line 17 at main script,ConversionGroup,HeaderDescriptor[line 15 at main script, insert_update, ConversionGroup, {}, [code, name, supported

Formats] ],{1=ValueEntry('<ignore>SSCBannerImageConversionGroup'=null,unresolved=null,ignore=true), 2=ValueEntry('<ignore>Groupe de conversion pour les banniďż˝re SSC'=null,unresolved=null,ignore=true), 3=ValueEntry('widescreen,mobile,tablet,desktop'=null,unresolved=true,reason:cannot resolve value 'widescreen,mobile,t

ablet,desktop' for attribute 'supportedFormats',ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.612 | INFO  [ImpExWorker<10/16>] [ImpExWorker] Returning worker impex worker 10/16 [cj:00000029] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.612 | WARN  [impex result worker [cj:00000029]] (ssc) [ImpExImportReader] line 16 at main script: dumped unresolved line ValueLine[,line 16 at main script,ConversionGroup,HeaderDescriptor[line 15 at main script, insert_update, ConversionGroup, {}, [code, name, supported

Formats] ],{1=ValueEntry('<ignore>SSCConversionGroup'=null,unresolved=null,ignore=true), 2=ValueEntry('<ignore>Groupe de conversion pour SSC'=null,unresolved=null,ignore=true), 3=ValueEntry('1200Wx1200H,515Wx515H,365Wx246H,300Wx300H,160Wx160H,96Wx96H,65Wx65H,30Wx30H'=null,unresolved=true,reason:cannot resolve value '12

00Wx1200H,515Wx515H,365Wx246H,300Wx300H,160Wx160H,96Wx96H,65Wx65H,30Wx30H' for attribute 'supportedFormats',ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.613 | INFO  [impex result worker [cj:00000029]] [ImpExWorker] Returning worker impex result worker [cj:00000029] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.613 | INFO  [hybrisHTTP18] (ssc) (00000029) [Importer] Finished 2 pass in 0d 00h:00m:00s:130ms - processed: 13, dumped: 13 (last pass: 13)

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.613 | ERROR [hybrisHTTP18] (ssc) (00000029) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 13 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.613 | INFO  [impex reader worker [cj:00000029]] [ImpExWorker] Returning worker impex reader worker [cj:00000029] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.613 | ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=00000029 for further details

INFO   | jvm 1	| main	| 2019/03/14 16:57:10.613 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/ssccore/import/common/themes.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.152 | INFO  [hybrisHTTP18] (ssc) [Initialization] Creating essential data for amdscore ...

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.152 | INFO  [hybrisHTTP18] (ssc) [ImpExSystemSetup] importing resource : /impex/essentialdataJobs.impex

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.465 | WARN  [impex result worker [cj:00000036-ImpEx-Import]] (ssc) [ImpExImportReader] line 5 at main script: dumped unresolved line ValueLine[unresolvable:cannot create due to unresolved mandatory/initial columns| column 2: could not resolve item for AMDS-UPSellImportJ

ob,line 5 at main script,null,HeaderDescriptor[line 2 at main script, insert_update, CronJob, {}, [code, job, singleExecutable, sessionLanguage] ],{1=ValueEntry('AMDS-UPSellImportCronJob'=AMDS-UPSellImportCronJob,unresolved=false,ignore=false), 2=ValueEntry('AMDS-UPSellImportJob'=null,unresolved=true,reason:could not r

esolve item for AMDS-UPSellImportJob,ignore=false), 3=ValueEntry('false'=false,unresolved=false,ignore=false), 4=ValueEntry('fr'=8796093186080->fr,unresolved=false,ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.465 | WARN  [impex result worker [cj:00000036-ImpEx-Import]] (ssc) [ImpExImportReader] line 4 at main script: dumped unresolved line ValueLine[unresolvable:cannot create due to unresolved mandatory/initial columns| column 2: could not resolve item for AMDS-MediaImportJo

b,line 4 at main script,null,HeaderDescriptor[line 2 at main script, insert_update, CronJob, {}, [code, job, singleExecutable, sessionLanguage] ],{1=ValueEntry('AMDS-MediaImportCronJob'=AMDS-MediaImportCronJob,unresolved=false,ignore=false), 2=ValueEntry('AMDS-MediaImportJob'=null,unresolved=true,reason:could not resol

ve item for AMDS-MediaImportJob,ignore=false), 3=ValueEntry('false'=false,unresolved=false,ignore=false), 4=ValueEntry('fr'=8796093186080->fr,unresolved=false,ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.465 | INFO  [impex result worker [cj:00000036-ImpEx-Import]] [ImpExWorker] Returning worker impex result worker [cj:00000036-ImpEx-Import] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.466 | INFO  [hybrisHTTP18] (ssc) (00000036-ImpEx-Import) [Importer] Finished 2 pass in 0d 00h:00m:00s:007ms - processed: 3, dumped: 3 (last pass: 3)

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.466 | INFO  [impex reader worker [cj:00000036-ImpEx-Import]] [ImpExWorker] Returning worker impex reader worker [cj:00000036-ImpEx-Import] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.466 | WARN  [hybrisHTTP18] (ssc) (00000036-ImpEx-Import) [Importer] Import aborted after 0d 00h:00m:00s:181ms

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.466 | ERROR [hybrisHTTP18] (ssc) (00000036-ImpEx-Import) [ImpExImportJob] Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 3 lines!

INFO   | jvm 1	| main	| 2019/03/14 16:58:49.466 | ERROR [hybrisHTTP18] (ssc) [ImpExManager] Import has caused an error, see logs of cronjob with code=00000036-ImpEx-Import for further details

INFO   | jvm 1	| main	| 2019/03/14 16:59:28.494 | INFO  [impex result worker [cj:0000004X]] [ImpExWorker] Returning worker impex result worker [cj:0000004X] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:59:28.494 | INFO  [hybrisHTTP18] (ssc) (0000004X) [Importer] Finished 3 pass in 0d 00h:00m:00s:003ms - processed: 1, dumped: 1 (last pass: 1)

INFO   | jvm 1	| main	| 2019/03/14 16:59:28.494 | ERROR [hybrisHTTP18] (ssc) (0000004X) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 3). Finally could not import 1 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 16:59:28.494 | INFO  [impex reader worker [cj:0000004X]] [ImpExWorker] Returning worker impex reader worker [cj:0000004X] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:59:28.494 | ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000004X for further details

INFO   | jvm 1	| main	| 2019/03/14 16:59:28.495 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/coredata/contentCatalogs/sscContentCatalog/email-content.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:59:35.574 | ERROR [hybrisHTTP18] (ssc) (00000057) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 1 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 16:59:35.574 | INFO  [impex reader worker [cj:00000057]] [ImpExWorker] Returning worker impex reader worker [cj:00000057] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:59:35.575 | ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=00000057 for further details

INFO   | jvm 1	| main	| 2019/03/14 16:59:35.575 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/coredata/stores/ssc/solr_en.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:59:35.676 | INFO  [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/coredata/stores/ssc/solr_fr.impex]...

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.651 | ERROR [impex reader worker [cj:0000005H]] (ssc) [ImpExWorker] unexpected error reading : reached EOF and got odd number of '"'! File is corrupt. Error starts in line: ";INH;";0.025;Pouce (inch);Inch" and occurs somewhere in the following lines.

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.651 | de.hybris.platform.impex.jalo.ImpExException: reached EOF and got odd number of '"'! File is corrupt. Error starts in line: ";INH;";0.025;Pouce (inch);Inch" and occurs somewhere in the following lines.

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 |     	at de.hybris.platform.impex.jalo.ImpExReader.tryToReadNextLineForImporting(ImpExReader.java:2060) ~[impexserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 |     	at de.hybris.platform.impex.jalo.ImpExReader.readLine(ImpExReader.java:1906) ~[impexserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 |     	at de.hybris.platform.impex.jalo.imp.ImpExImportReader.readLine(ImpExImportReader.java:500) ~[impexserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 |     	at de.hybris.platform.impex.jalo.imp.MultiThreadedImpExImportReader.readLineFromWorker(MultiThreadedImpExImportReader.java:363) ~[impexserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 |     	at de.hybris.platform.impex.jalo.imp.ImpExReaderWorker.perform(ImpExReaderWorker.java:41) [impexserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 |     	at de.hybris.platform.impex.jalo.imp.ImpExWorker.run(ImpExWorker.java:89) [impexserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 |     	at de.hybris.platform.util.threadpool.PoolableThread.internalRun(PoolableThread.java:208) [coreserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 |     	at de.hybris.platform.core.threadregistry.RegistrableThread.run(RegistrableThread.java:135) [coreserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.652 | Caused by: java.lang.IllegalStateException: reached EOF and got odd number of '"'! File is corrupt. Error starts in line: ";INH;";0.025;Pouce (inch);Inch" and occurs somewhere in the following lines.

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.653 |     	at de.hybris.platform.util.CSVReader.readNextLine(CSVReader.java:374) ~[coreserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.653 |     	at de.hybris.platform.impex.jalo.ImpExReader.tryToReadNextLineForImporting(ImpExReader.java:2056) ~[impexserver.jar:?]

INFO   | jvm 1	| main	| 2019/03/14 16:59:40.653 |     	... 7 more

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.582 | WARN  [impex result worker [cj:0000005K]] (ssc) [ImpExImportReader] line 5 at main script: dumped unresolved line ValueLine[unresolvable:no existing item found for update,line 5 at main script,null,HeaderDescriptor[line 2 at main script, update, Category, {}, [cod

e, catalogversion, name] ],{1=ValueEntry('Noire_Tole'=Noire_Tole,unresolved=false,ignore=false), 2=ValueEntry(''=sscProductCatalog/Staged(8796125856345),unresolved=false,ignore=false), 3=ValueEntry('Noire'=null,unresolved=null,ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.582 | WARN  [impex result worker [cj:0000005K]] (ssc) [ImpExImportReader] line 4 at main script: dumped unresolved line ValueLine[unresolvable:no existing item found for update,line 4 at main script,null,HeaderDescriptor[line 2 at main script, update, Category, {}, [cod

e, catalogversion, name] ],{1=ValueEntry('Decapee_Tole'=Decapee_Tole,unresolved=false,ignore=false), 2=ValueEntry(''=sscProductCatalog/Staged(8796125856345),unresolved=false,ignore=false), 3=ValueEntry('DĂ©capĂ©e'=null,unresolved=null,ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.582 | WARN  [impex result worker [cj:0000005K]] (ssc) [ImpExImportReader] line 3 at main script: dumped unresolved line ValueLine[unresolvable:no existing item found for update,line 3 at main script,null,HeaderDescriptor[line 2 at main script, update, Category, {}, [cod

e, catalogversion, name] ],{1=ValueEntry('Larmee_Tole'=Larmee_Tole,unresolved=false,ignore=false), 2=ValueEntry(''=sscProductCatalog/Staged(8796125856345),unresolved=false,ignore=false), 3=ValueEntry('LarmĂ©e'=null,unresolved=null,ignore=false)}]

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.583 | INFO  [impex result worker [cj:0000005K]] [ImpExWorker] Returning worker impex result worker [cj:0000005K] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.583 | INFO  [hybrisHTTP18] (ssc) (0000005K) [Importer] Finished 2 pass in 0d 00h:00m:00s:004ms - processed: 3, dumped: 3 (last pass: 3)

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.583 | ERROR [hybrisHTTP18] (ssc) (0000005K) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 3 lines![HY-123]

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.583 | INFO  [impex reader worker [cj:0000005K]] [ImpExWorker] Returning worker impex reader worker [cj:0000005K] to the pool

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.684 | ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000005K for further details

INFO   | jvm 1	| main	| 2019/03/14 16:59:41.684 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/productCatalogs/sscProductCatalog/categories_fr.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:59:50.177 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/productCatalogs/sscProductCatalog/categories-classifications.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:59:51.550 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/productCatalogs/sscProductCatalog/suppliers-media.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:59:55.143 | ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=00000062 for further details

INFO   | jvm 1	| main	| 2019/03/14 16:59:55.143 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/productCatalogs/sscProductCatalog/multi-d/dimension-products.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:59:56.345 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/productCatalogs/sscProductCatalog/multi-d/dimension-products-media.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:59:57.276 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/productCatalogs/sscProductCatalog/multi-d/dimension-products-stock-levels.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 16:59:57.917 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/productCatalogs/sscProductCatalog/multi-d/dimension-products-pos-stocklevels.impex]... FAILED

INFO   | jvm 1	| main	| 2019/03/14 17:00:04.860 | ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/contentCatalogs/sscContentCatalog/cms-responsive-content.impex]... FAILED

INFO  [ImpExWorker<9/16>] [ImpExWorker] Returning worker impex worker 9/16 [cj:0000006K] to the pool

INFO  [ImpExWorker<2/16>] [ImpExWorker] Returning worker impex worker 2/16 [cj:0000006K] to the pool

INFO  [impex result worker [cj:0000006K]] [ImpExWorker] Returning worker impex result worker [cj:0000006K] to the pool

INFO  [ImpExWorker<15/16>] [ImpExWorker] Returning worker impex worker 15/16 [cj:0000006K] to the pool

INFO  [ImpExWorker<12/16>] [ImpExWorker] Returning worker impex worker 12/16 [cj:0000006K] to the pool

INFO  [hybrisHTTP18] (ssc) (0000006K) [Importer] Finished 2 pass in 0d 00h:00m:00s:004ms - processed: 4, dumped: 4 (last pass: 4)

ERROR [hybrisHTTP18] (ssc) (0000006K) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 4 lines![HY-123]

INFO  [impex reader worker [cj:0000006K]] [ImpExWorker] Returning worker impex reader worker [cj:0000006K] to the pool

ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000006K for further details

E

WARN  [impex result worker [cj:0000006Q]] (ssc) [ImpExImportReader] line 3 at main script: dumped unresolved line ValueLine[unresolvable:error finding existing item : column='target' value='FE1', | column 2: could not resolve item for FE1,line 3 at main script,null,HeaderDescriptor[line 2 at main script, insert_update, BaseStore2WarehouseRel, {}, [source, target] ],{1=ValueEntry('ssc'=8796093056989,unresolved=false,ignore=false), 2=ValueEntry('FE1'=null,unresolved=true,reason:could not resolve item for FE1,ignore=false)}]

INFO  [ImpExWorker<8/16>] [ImpExWorker] Returning worker impex worker 8/16 [cj:0000006Q] to the pool

INFO  [ImpExWorker<7/16>] [ImpExWorker] Returning worker impex worker 7/16 [cj:0000006Q] to the pool

INFO  [impex result worker [cj:0000006Q]] [ImpExWorker] Returning worker impex result worker [cj:0000006Q] to the pool

INFO  [hybrisHTTP18] (ssc) (0000006Q) [Importer] Finished 2 pass in 0d 00h:00m:00s:004ms - processed: 1, dumped: 1 (last pass: 1)

INFO  [ImpExWorker<15/16>] [ImpExWorker] Returning worker impex worker 15/16 [cj:0000006Q] to the pool

ERROR [hybrisHTTP18] (ssc) (0000006Q) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 1 lines![HY-123]

INFO  [impex reader worker [cj:0000006Q]] [ImpExWorker] Returning worker impex reader worker [cj:0000006Q] to the pool

ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000006Q for further details

ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/stores/ssc/warehouses.impex]... FAILED

INFO  [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/sscinitialdata/import/sampledata/productCatalogs/sscProductCatalog/reviews.impex]...

INFO  [hybrisHTTP18] (ssc) [Initialization] Creating project data for ssctest ...

WARN  [hybrisHTTP18] (ssc) [AbstractSystemSetup] Missing setup parameter for key [createTestData], falling back to defined default [true]

INFO  [hybrisHTTP18] (ssc) [TestDataSystemSetup] Creating Test Users...

INFO  [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/ssctest/import/qa-test-users.impex]...

INFO  [hybrisHTTP18] (ssc) [DefaultImportService] Starting import synchronous using cronjob with code=0000007F

INFO  [hybrisHTTP18] (ssc) (0000007F) [ImpExImportJob] Starting multi-threaded ImpEx cronjob "ImpEx-Import" (16 threads)

INFO  [hybrisHTTP18] (ssc) (0000007F) [MultiThreadedImpExImportReader] Trying to allocate required threads.

INFO  [hybrisHTTP18] (ssc) (0000007F) [MultiThreadedImpExImportReader] Required threads have been allocated.

INFO  [hybrisHTTP18] (ssc) (0000007F) [MultiThreadedImpExImportReader] added worker impex worker 0/16 [cj:0000007F]

INFO  [hybrisHTTP18] (ssc) (0000007F) [MultiThreadedImpExImportReader] Started ImpEx reader worker impex reader worker [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 1/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 2/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 3/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 4/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 5/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 6/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 7/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 8/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 9/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 10/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 11/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 12/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 13/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 14/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] added worker impex worker 15/16 [cj:0000007F]

INFO  [impex reader worker [cj:0000007F]] (ssc) [MultiThreadedImpExImportReader] Allocated 15 new ones of 16 ImpEx workers.

WARN  [ImpExWorker<6/16>] (ssc) [ReflectionAttributeAccess] line 66 at main script: extension amdscore not installed, cannot call attribute accessor for Address.requiresPostalCodeValidation:java.lang.Boolean[rwoSRp]

WARN  [ImpExWorker<15/16>] (ssc) [ReflectionAttributeAccess] line 67 at main script: extension amdscore not installed, cannot call attribute accessor for Address.requiresPostalCodeValidation:java.lang.Boolean[rwoSRp]

WARN  [ImpExWorker<2/16>] (ssc) [ReflectionAttributeAccess] line 65 at main script: extension amdscore not installed, cannot call attribute accessor for Address.requiresPostalCodeValidation:java.lang.Boolean[rwoSRp]

WARN  [ImpExWorker<1/16>] (ssc) [ReflectionAttributeAccess] line 70 at main script: extension amdscore not installed, cannot call attribute accessor for Address.requiresPostalCodeValidation:java.lang.Boolean[rwoSRp]

WARN  [ImpExWorker<11/16>] (ssc) [ReflectionAttributeAccess] line 64 at main script: extension amdscore not installed, cannot call attribute accessor for Address.requiresPostalCodeValidation:java.lang.Boolean[rwoSRp]

WARN  [ImpExWorker<7/16>] (ssc) [ReflectionAttributeAccess] line 69 at main script: extension amdscore not installed, cannot call attribute accessor for Address.requiresPostalCodeValidation:java.lang.Boolean[rwoSRp]

WARN  [ImpExWorker<8/16>] (ssc) [ReflectionAttributeAccess] line 68 at main script: extension amdscore not installed, cannot call attribute accessor for Address.requiresPostalCodeValidation:java.lang.Boolean[rwoSRp]

WARN  [ImpExWorker<4/16>] (ssc) [ReflectionAttributeAccess] line 105 at main script: extension amdscore not installed, cannot call attribute accessor for Order.sapPlacedOrderError:java.lang.Boolean[rwSRp]

WARN  [impex reader worker [cj:0000007F]] (ssc) [ReflectionAttributeAccess] line 106 at main script: extension amdscore not installed, cannot call attribute accessor for Address.heading:java.lang.String[rwoSRp]

WARN  [impex reader worker [cj:0000007F]] (ssc) [ReflectionAttributeAccess] line 106 at main script: extension sapmodel not installed, cannot call attribute accessor for Address.sapAddressUsage:java.lang.String[rwoSCRp]

WARN  [impex reader worker [cj:0000007F]] (ssc) [ReflectionAttributeAccess] line 106 at main script: extension sapmodel not installed, cannot call attribute accessor for Address.sapAddressUsageCounter:java.lang.String[rwoSCRp]

WARN  [impex reader worker [cj:0000007F]] (ssc) [ReflectionAttributeAccess] line 106 at main script: extension sapmodel not installed, cannot call attribute accessor for Address.sapCustomerID:java.lang.String[rwoSCRp]

INFO  [impex result worker [cj:0000007F]] [ImpExWorker] Returning worker impex result worker [cj:0000007F] to the pool

INFO  [hybrisHTTP18] (ssc) (0000007F) [Importer] Finished 2 pass in 0d 00h:00m:00s:013ms - processed: 49, dumped: 49 (last pass: 49)

ERROR [hybrisHTTP18] (ssc) (0000007F) [CronJobErrorHandler] de.hybris.platform.impex.jalo.ImpExException: Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 49 lines![HY-123]

INFO  [impex reader worker [cj:0000007F]] [ImpExWorker] Returning worker impex reader worker [cj:0000007F] to the pool

ERROR [hybrisHTTP18] (ssc) [DefaultImportService] Import has caused an error, see logs of cronjob with code=0000007F for further details

ERROR [hybrisHTTP18] (ssc) [DefaultSetupImpexService] Importing [/ssctest/import/qa-test-users.impex]... FAILED

INFO  [hybrisHTTP18] (ssc) [Initialization] Creating project data for amdscommercewebservices ...

INFO  [hybrisHTTP18] (ssc) [ImpExSystemSetup] importing resource : /impex/projectdata-amdscommercewebservices.impex

WARN  [impex result worker [cj:0000007U-ImpEx-Import]] (ssc) [ImpExImportReader] line 18 at main script: dumped unresolved line ValueLine[unresolvable:error finding existing item : column='cronJob' value='oldCartRemovalCronJob', | column 1: cannot resolve value 'oldCartRemovalCronJob' for attribute 'cronJob',line 18 at main script,null,HeaderDescriptor[line 17 at main script, insert_update, Trigger, {}, [cronJob, second, minute, hour, day, month, year, relative, active, maxAcceptableDelay] ],{1=ValueEntry('oldCartRemovalCronJob'=null,unresolved=true,reason:cannot resolve value 'oldCartRemovalCronJob' for attribute 'cronJob',ignore=false), 2=ValueEntry('0'=null,unresolved=null,ignore=false), 3=ValueEntry('30'=null,unresolved=null,ignore=false), 4=ValueEntry('3'=null,unresolved=null,ignore=false), 5=ValueEntry('-1'=null,unresolved=null,ignore=false), 6=ValueEntry('-1'=null,unresolved=null,ignore=false), 7=ValueEntry('-1'=null,unresolved=null,ignore=false), 8=ValueEntry('false'=null,unresolved=null,ignore=false), 9=ValueEntry('true'=null,unresolved=null,ignore=false), 10=ValueEntry('-1'=null,unresolved=null,ignore=false)}]

INFO  [ImpExWorker<1/16>] [ImpExWorker] Returning worker impex worker 1/16 [cj:0000007U-ImpEx-Import] to the pool

INFO  [impex result worker [cj:0000007U-ImpEx-Import]] [ImpExWorker] Returning worker impex result worker [cj:0000007U-ImpEx-Import] to the pool

INFO  [hybrisHTTP18] (ssc) (0000007U-ImpEx-Import) [Importer] Finished 2 pass in 0d 00h:00m:00s:013ms - processed: 6, dumped: 6 (last pass: 6)

INFO  [impex reader worker [cj:0000007U-ImpEx-Import]] [ImpExWorker] Returning worker impex reader worker [cj:0000007U-ImpEx-Import] to the pool

WARN  [hybrisHTTP18] (ssc) (0000007U-ImpEx-Import) [Importer] Import aborted after 0d 00h:00m:00s:100ms

ERROR [hybrisHTTP18] (ssc) (0000007U-ImpEx-Import) [ImpExImportJob] Can not resolve any more lines ... Aborting further passes (at pass 2). Finally could not import 6 lines!

ERROR [hybrisHTTP18] (ssc) [ImpExManager] Import has caused an error, see logs of cronjob with code=0000007U-ImpEx-Import for further details

INFO  [hybrisHTTP18] (ssc) [Initialization] Creating project data for previewpersonalizationweb …

ERROR [hybrisHTTP18] (ssc) [CockpitModuleComponentDefinitionService] Could not delete deployed resources, reason:

java.io.IOException: Unable to delete file: D:\PROJ\MITTAL\ws_esteel\hybris\data\backoffice\widgetlib\deployed\voucherbackoffice.jar

    	at org.apache.commons.io.FileUtils.forceDelete(FileUtils.java:2279) ~[commons-io-2.4.jar:2.4]

    	at org.apache.commons.io.FileUtils.cleanDirectory(FileUtils.java:1653) ~[commons-io-2.4.jar:2.4]

    	at com.hybris.cockpitng.modules.core.impl.CockpitModuleComponentDefinitionService.fetchExternalWidgets(CockpitModuleComponentDefinitionService.java:98) ~[?:?]

    	at com.hybris.cockpitng.modules.core.impl.CockpitModuleComponentDefinitionService.reloadDefinitions(CockpitModuleComponentDefinitionService.java:75) ~[?:?]

    	at com.hybris.cockpitng.util.impl.DefaultWidgetUtils.refreshWidgetLibrary(DefaultWidgetUtils.java:70) ~[?:?]

    	at com.hybris.backoffice.config.DefaultBackofficeStartupHandler.resetBackofficeWidgetsConfiguration(DefaultBackofficeStartupHandler.java:72) ~[?:?]

    	at com.hybris.backoffice.config.DefaultBackofficeStartupHandler.lambda$0(DefaultBackofficeStartupHandler.java:57) ~[?:?]

    	at com.hybris.backoffice.events.AbstractBackofficeEventListener.onEvent(AbstractBackofficeEventListener.java:56) [backofficeserver.jar:?]

    	at de.hybris.platform.servicelayer.event.impl.AbstractEventListener.onApplicationEvent(AbstractEventListener.java:65) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.event.impl.AbstractEventListener.onApplicationEvent(AbstractEventListener.java:1) [coreserver.jar:?]

    	at org.springframework.context.event.SimpleApplicationEventMulticaster.invokeListener(SimpleApplicationEventMulticaster.java:166) [spring-context-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.context.event.SimpleApplicationEventMulticaster.multicastEvent(SimpleApplicationEventMulticaster.java:138) [spring-context-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.context.support.AbstractApplicationContext.publishEvent(AbstractApplicationContext.java:382) [spring-context-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.context.support.AbstractApplicationContext.publishEvent(AbstractApplicationContext.java:336) [spring-context-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.spring.ctx.CloseAwareApplicationContext.publishEvent(CloseAwareApplicationContext.java:107) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.event.impl.SpringEventSender.sendEvent(SpringEventSender.java:33) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.event.impl.PlatformClusterEventSender.sendEvent(PlatformClusterEventSender.java:60) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.event.impl.DefaultEventService.publishEvent(DefaultEventService.java:75) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.internal.jalo.ServicelayerManager.notifyInitializationEnd(ServicelayerManager.java:286) [coreserver.jar:?]

    	at de.hybris.platform.core.Initialization.doInitializeImpl(Initialization.java:609) [coreserver.jar:?]

    	at de.hybris.platform.core.Initialization.access$5(Initialization.java:465) [coreserver.jar:?]

    	at de.hybris.platform.core.Initialization$5.call(Initialization.java:786) [coreserver.jar:?]

    	at de.hybris.platform.core.Initialization$5.call(Initialization.java:1) [coreserver.jar:?]

    	at de.hybris.platform.core.system.InitializationLockHandler.performLocked(InitializationLockHandler.java:80) [coreserver.jar:?]

    	at de.hybris.platform.core.Initialization.doInitialize(Initialization.java:818) [coreserver.jar:?]

    	at de.hybris.platform.hac.facade.impl.DefaultInitUpdateFacade.executeInitUpdate(DefaultInitUpdateFacade.java:69) [classes/:?]

    	at de.hybris.platform.hac.controller.platform.InitUpdateController.initExecuteWrap(InitUpdateController.java:106) [classes/:?]

    	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[?:1.8.0_152]

    	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[?:1.8.0_152]

    	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[?:1.8.0_152]

    	at java.lang.reflect.Method.invoke(Method.java:498) ~[?:1.8.0_152]

    	at org.springframework.web.method.support.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:221) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.method.support.InvocableHandlerMethod.invokeForRequest(InvocableHandlerMethod.java:136) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:114) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:827) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:738) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:85) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:963) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:897) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:970) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:872) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at javax.servlet.http.HttpServlet.service(HttpServlet.java:650) [servlet-api.jar:?]

    	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:846) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at javax.servlet.http.HttpServlet.service(HttpServlet.java:731) [servlet-api.jar:?]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:303) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:52) [tomcat7-websocket.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.sitemesh.webapp.contentfilter.ContentBufferingFilter.bufferAndPostProcess(ContentBufferingFilter.java:169) [sitemesh-3.0-alpha-2.jar:?]

    	at org.sitemesh.webapp.contentfilter.ContentBufferingFilter.doFilter(ContentBufferingFilter.java:126) [sitemesh-3.0-alpha-2.jar:?]

    	at org.sitemesh.config.ConfigurableSiteMeshFilter.doFilter(ConfigurableSiteMeshFilter.java:163) [sitemesh-3.0-alpha-2.jar:?]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.springframework.web.multipart.support.MultipartFilter.doFilterInternal(MultipartFilter.java:122) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:317) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.access.intercept.FilterSecurityInterceptor.invoke(FilterSecurityInterceptor.java:127) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.access.intercept.FilterSecurityInterceptor.doFilter(FilterSecurityInterceptor.java:91) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.access.ExceptionTranslationFilter.doFilter(ExceptionTranslationFilter.java:115) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.session.SessionManagementFilter.doFilter(SessionManagementFilter.java:137) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.AnonymousAuthenticationFilter.doFilter(AnonymousAuthenticationFilter.java:111) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.rememberme.RememberMeAuthenticationFilter.doFilter(RememberMeAuthenticationFilter.java:150) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.servletapi.SecurityContextHolderAwareRequestFilter.doFilter(SecurityContextHolderAwareRequestFilter.java:169) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.savedrequest.RequestCacheAwareFilter.doFilter(RequestCacheAwareFilter.java:63) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.www.BasicAuthenticationFilter.doFilterInternal(BasicAuthenticationFilter.java:158) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.AbstractAuthenticationProcessingFilter.doFilter(AbstractAuthenticationProcessingFilter.java:200) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.logout.LogoutFilter.doFilter(LogoutFilter.java:121) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.csrf.CsrfFilter.doFilterInternal(CsrfFilter.java:100) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.header.HeaderWriterFilter.doFilterInternal(HeaderWriterFilter.java:66) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.context.request.async.WebAsyncManagerIntegrationFilter.doFilterInternal(WebAsyncManagerIntegrationFilter.java:56) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.context.SecurityContextPersistenceFilter.doFilter(SecurityContextPersistenceFilter.java:105) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.access.channel.ChannelProcessingFilter.doFilter(ChannelProcessingFilter.java:157) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy.doFilterInternal(FilterChainProxy.java:214) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy.doFilter(FilterChainProxy.java:177) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.web.filter.DelegatingFilterProxy.invokeDelegate(DelegatingFilterProxy.java:346) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.DelegatingFilterProxy.doFilter(DelegatingFilterProxy.java:262) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.springframework.web.filter.HiddenHttpMethodFilter.doFilterInternal(HiddenHttpMethodFilter.java:77) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:301) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$StatisticsGatewayFilter.doFilter(AbstractPlatformFilterChain.java:390) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.SecureMediaFilter.doFilter(SecureMediaFilter.java:108) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.DataSourceSwitchingFilter.doFilter(DataSourceSwitchingFilter.java:70) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.SessionFilter.doFilter(SessionFilter.java:99) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.RedirectWhenSystemIsNotInitializedFilter.processWhenNotInitialized(RedirectWhenSystemIsNotInitializedFilter.java:129) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.RedirectWhenSystemIsNotInitializedFilter.doFilter(RedirectWhenSystemIsNotInitializedFilter.java:106) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.Log4JFilter.doFilter(Log4JFilter.java:44) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.session.HybrisSpringSessionFilter.doFilter(HybrisSpringSessionFilter.java:69) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain.processStandardFilterChain(AbstractPlatformFilterChain.java:201) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain.doFilterInternal(AbstractPlatformFilterChain.java:179) [coreserver.jar:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.DelegatingFilterProxy.invokeDelegate(DelegatingFilterProxy.java:346) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.DelegatingFilterProxy.doFilter(DelegatingFilterProxy.java:262) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:197) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at de.hybris.platform.servicelayer.web.XSSFilter.processPatternsAndDoFilter(XSSFilter.java:358) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.XSSFilter.doFilter(XSSFilter.java:306) [coreserver.jar:?]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:218) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:110) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:169) [catalina.jar:7.0.75]

    	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:103) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:116) [catalina.jar:7.0.75]

    	at org.apache.catalina.valves.AccessLogValve.invoke(AccessLogValve.java:962) [catalina.jar:7.0.75]

    	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:452) [catalina.jar:7.0.75]

    	at org.apache.coyote.http11.AbstractHttp11Processor.process(AbstractHttp11Processor.java:1087) [tomcat-coyote.jar:7.0.75]

    	at org.apache.coyote.AbstractProtocol$AbstractConnectionHandler.process(AbstractProtocol.java:637) [tomcat-coyote.jar:7.0.75]

    	at org.apache.tomcat.util.net.JIoEndpoint$SocketProcessor.run(JIoEndpoint.java:318) [tomcat-coyote.jar:7.0.75]

    	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149) [?:1.8.0_152]

    	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624) [?:1.8.0_152]

    	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61) [tomcat-coyote.jar:7.0.75]

    	at java.lang.Thread.run(Thread.java:748) [?:1.8.0_152]

    20. AMDF Storefront:

--

![image alt text]({{ site.url }}/public/zhVisFitu2T7aod2alknCw_img_0.png)

--

ERROR [hybrisHTTP26] [SolrSearchRequestResponsePopulator] Exception while executing SOLR search

de.hybris.platform.solrfacetsearch.search.FacetSearchException: No bean named 'ProductPointOfServiceValueProvider' is defined

    	at de.hybris.platform.solrfacetsearch.search.impl.DefaultFacetSearchStrategy.search(DefaultFacetSearchStrategy.java:165) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.solrfacetsearch.search.impl.DefaultFacetSearchService.search(DefaultFacetSearchService.java:89) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.solrfacetsearch.search.impl.DefaultFacetSearchService.search(DefaultFacetSearchService.java:78) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.commerceservices.search.solrfacetsearch.populators.SolrSearchRequestResponsePopulator.populate(SolrSearchRequestResponsePopulator.java:71) [commerceservicesserver.jar:?]

    	at de.hybris.platform.commerceservices.search.solrfacetsearch.populators.SolrSearchRequestResponsePopulator.populate(SolrSearchRequestResponsePopulator.java:1) [commerceservicesserver.jar:?]

    	at de.hybris.platform.converters.impl.AbstractPopulatingConverter.populate(AbstractPopulatingConverter.java:73) [platformservicesserver.jar:?]

    	at de.hybris.platform.commerceservices.converter.impl.AbstractPopulatingConverter.convert(AbstractPopulatingConverter.java:37) [commerceservicesserver.jar:?]

    	at com.arcelormittal.amds.ecom.core.services.impl.AMDSSolrProductSearchService.doSearch(AMDSSolrProductSearchService.java:49) [amdscoreserver.jar:?]

    	at de.hybris.platform.commerceservices.search.solrfacetsearch.impl.DefaultSolrProductSearchService.categorySearch(DefaultSolrProductSearchService.java:130) [commerceservicesserver.jar:?]

    	at de.hybris.platform.commerceservices.search.solrfacetsearch.impl.DefaultSolrProductSearchService.categorySearch(DefaultSolrProductSearchService.java:1) [commerceservicesserver.jar:?]

    	at de.hybris.platform.commercefacades.search.solrfacetsearch.impl.DefaultSolrProductSearchFacade$4.execute(DefaultSolrProductSearchFacade.java:182) [commercefacadesserver.jar:?]

    	at de.hybris.platform.commercefacades.search.solrfacetsearch.impl.DefaultSolrProductSearchFacade$4.execute(DefaultSolrProductSearchFacade.java:1) [commercefacadesserver.jar:?]

    	at de.hybris.platform.commerceservices.threadcontext.impl.DefaultThreadContextService.executeInContext(DefaultThreadContextService.java:51) [commerceservicesserver.jar:?]

    	at de.hybris.platform.commercefacades.search.solrfacetsearch.impl.DefaultSolrProductSearchFacade.categorySearch(DefaultSolrProductSearchFacade.java:175) [commercefacadesserver.jar:?]

    	at de.hybris.platform.acceleratorstorefrontcommons.controllers.pages.AbstractCategoryPageController$CategorySearchEvaluator.doSearch(AbstractCategoryPageController.java:284) [classes/:?]

    	at com.arcelormittal.amds.ecom.storefront.controllers.pages.CategoryPageController.performSearchAndGetResultsPage(CategoryPageController.java:117) [classes/:?]

    	at com.arcelormittal.amds.ecom.storefront.controllers.pages.CategoryPageController.category(CategoryPageController.java:71) [classes/:?]

    	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[?:1.8.0_152]

    	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62) ~[?:1.8.0_152]

    	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[?:1.8.0_152]

    	at java.lang.reflect.Method.invoke(Method.java:498) ~[?:1.8.0_152]

    	at org.springframework.web.method.support.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:221) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.method.support.InvocableHandlerMethod.invokeForRequest(InvocableHandlerMethod.java:136) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:114) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:827) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:738) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:85) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:963) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:897) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:970) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.servlet.FrameworkServlet.doGet(FrameworkServlet.java:861) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at javax.servlet.http.HttpServlet.service(HttpServlet.java:624) [servlet-api.jar:?]

    	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:846) [spring-webmvc-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at javax.servlet.http.HttpServlet.service(HttpServlet.java:731) [servlet-api.jar:?]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:303) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:301) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$StatisticsGatewayFilter.doFilter(AbstractPlatformFilterChain.java:390) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.WebAppMediaFilter.doFilter(WebAppMediaFilter.java:140) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.CustomerLocationRestorationFilter.doFilterInternal(CustomerLocationRestorationFilter.java:52) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.CartRestorationFilter.doFilterInternal(CartRestorationFilter.java:88) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.AMDSValidationCGAndPPDFliter.doFilterInternal(AMDSValidationCGAndPPDFliter.java:126) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.AnonymousCheckoutFilter.doFilterInternal(AnonymousCheckoutFilter.java:36) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:317) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.access.intercept.FilterSecurityInterceptor.invoke(FilterSecurityInterceptor.java:127) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.access.intercept.FilterSecurityInterceptor.doFilter(FilterSecurityInterceptor.java:91) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.access.ExceptionTranslationFilter.doFilter(ExceptionTranslationFilter.java:115) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.session.SessionManagementFilter.doFilter(SessionManagementFilter.java:137) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.AnonymousAuthenticationFilter.doFilter(AnonymousAuthenticationFilter.java:111) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.rememberme.RememberMeAuthenticationFilter.doFilter(RememberMeAuthenticationFilter.java:150) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.servletapi.SecurityContextHolderAwareRequestFilter.doFilter(SecurityContextHolderAwareRequestFilter.java:169) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.savedrequest.RequestCacheAwareFilter.doFilter(RequestCacheAwareFilter.java:63) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.AbstractAuthenticationProcessingFilter.doFilter(AbstractAuthenticationProcessingFilter.java:200) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.authentication.logout.LogoutFilter.doFilter(LogoutFilter.java:121) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.header.HeaderWriterFilter.doFilterInternal(HeaderWriterFilter.java:66) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.context.request.async.WebAsyncManagerIntegrationFilter.doFilterInternal(WebAsyncManagerIntegrationFilter.java:56) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.context.SecurityContextPersistenceFilter.doFilter(SecurityContextPersistenceFilter.java:105) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.access.channel.ChannelProcessingFilter.doFilter(ChannelProcessingFilter.java:157) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy$VirtualFilterChain.doFilter(FilterChainProxy.java:331) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy.doFilterInternal(FilterChainProxy.java:214) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at org.springframework.security.web.FilterChainProxy.doFilter(FilterChainProxy.java:177) [spring-security-web-4.1.3.RELEASE.jar:4.1.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.personalizationservices.filter.CxPersonalizationFilter.doFilterInternal(CxPersonalizationFilter.java:66) [personalizationservicesserver.jar:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.FileUploadFilter.doFilterInternal(FileUploadFilter.java:51) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.UrlEncoderFilter.doFilterInternal(UrlEncoderFilter.java:74) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.StorefrontFilter.doFilterInternal(StorefrontFilter.java:89) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.cms.CMSSiteFilter.doFilterInternal(CMSSiteFilter.java:100) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.RequestLoggerFilter.doFilterInternal(RequestLoggerFilter.java:71) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at com.arcelormittal.amds.ecom.storefront.filters.AcceleratorAddOnFilter.doFilter(AcceleratorAddOnFilter.java:90) [classes/:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.SessionFilter.doFilter(SessionFilter.java:99) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.Log4JFilter.doFilter(Log4JFilter.java:44) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain$InternalFilterChain.doFilter(AbstractPlatformFilterChain.java:271) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain.processStandardFilterChain(AbstractPlatformFilterChain.java:201) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.AbstractPlatformFilterChain.doFilterInternal(AbstractPlatformFilterChain.java:179) [coreserver.jar:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at com.arcelormittal.amds.ecom.storefront.filters.UrlPathFilter.doFilterInternal(UrlPathFilter.java:82) [classes/:?]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.DelegatingFilterProxy.invokeDelegate(DelegatingFilterProxy.java:346) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.DelegatingFilterProxy.doFilter(DelegatingFilterProxy.java:262) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:52) [tomcat7-websocket.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:197) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at com.arcelormittal.amds.ecom.storefront.filters.AcceleratorAddOnFilter.doFilter(AcceleratorAddOnFilter.java:90) [classes/:?]

    	at org.springframework.web.filter.DelegatingFilterProxy.invokeDelegate(DelegatingFilterProxy.java:346) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.web.filter.DelegatingFilterProxy.doFilter(DelegatingFilterProxy.java:262) [spring-web-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at de.hybris.platform.servicelayer.web.XSSFilter.processPatternsAndDoFilter(XSSFilter.java:358) [coreserver.jar:?]

    	at de.hybris.platform.servicelayer.web.XSSFilter.doFilter(XSSFilter.java:306) [coreserver.jar:?]

    	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:241) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:208) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:218) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:110) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:169) [catalina.jar:7.0.75]

    	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:103) [catalina.jar:7.0.75]

    	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:116) [catalina.jar:7.0.75]

    	at org.apache.catalina.valves.AccessLogValve.invoke(AccessLogValve.java:962) [catalina.jar:7.0.75]

    	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:452) [catalina.jar:7.0.75]

    	at org.apache.coyote.http11.AbstractHttp11Processor.process(AbstractHttp11Processor.java:1087) [tomcat-coyote.jar:7.0.75]

    	at org.apache.coyote.AbstractProtocol$AbstractConnectionHandler.process(AbstractProtocol.java:637) [tomcat-coyote.jar:7.0.75]

    	at org.apache.tomcat.util.net.JIoEndpoint$SocketProcessor.run(JIoEndpoint.java:318) [tomcat-coyote.jar:7.0.75]

    	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1149) [?:1.8.0_152]

    	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:624) [?:1.8.0_152]

    	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61) [tomcat-coyote.jar:7.0.75]

    	at java.lang.Thread.run(Thread.java:748) [?:1.8.0_152]

Caused by: org.springframework.beans.factory.NoSuchBeanDefinitionException: No bean named 'ProductPointOfServiceValueProvider' is defined

    	at org.springframework.beans.factory.support.DefaultListableBeanFactory.getBeanDefinition(DefaultListableBeanFactory.java:677) ~[spring-beans-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.beans.factory.support.AbstractBeanFactory.getMergedLocalBeanDefinition(AbstractBeanFactory.java:1180) ~[spring-beans-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:284) ~[spring-beans-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:202) ~[spring-beans-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:275) ~[spring-beans-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:197) ~[spring-beans-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:1076) ~[spring-context-4.3.3.RELEASE.jar:4.3.3.RELEASE]

    	at de.hybris.platform.solrfacetsearch.provider.impl.DefaultValueProviderSelectionStrategy.getValueProvider(DefaultValueProviderSelectionStrategy.java:61) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.solrfacetsearch.search.impl.DefaultFieldNameTranslator.translateFromProperty(DefaultFieldNameTranslator.java:197) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.solrfacetsearch.search.impl.DefaultFieldNameTranslator.getFieldInfos(DefaultFieldNameTranslator.java:147) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.solrfacetsearch.search.impl.populators.FacetSearchResultFacetsPopulator.buildFacets(FacetSearchResultFacetsPopulator.java:186) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.solrfacetsearch.search.impl.populators.FacetSearchResultFacetsPopulator.populate(FacetSearchResultFacetsPopulator.java:111) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.solrfacetsearch.search.impl.populators.FacetSearchResultFacetsPopulator.populate(FacetSearchResultFacetsPopulator.java:1) ~[solrfacetsearchserver.jar:?]

    	at de.hybris.platform.converters.impl.AbstractPopulatingConverter.populate(AbstractPopulatingConverter.java:73) ~[platformservicesserver.jar:?]

    	at de.hybris.platform.commerceservices.converter.impl.AbstractPopulatingConverter.convert(AbstractPopulatingConverter.java:37) ~[commerceservicesserver.jar:?]

    	at de.hybris.platform.solrfacetsearch.search.impl.DefaultFacetSearchStrategy.search(DefaultFacetSearchStrategy.java:155) ~[solrfacetsearchserver.jar:?]

  Analizai itemów:

1. Amdscore-items.xml

<table>
  <tr>
    <td>Itemtype</td>
    <td>parent</td>
    <td>attributes</td>
    <td>deployment</td>
    <td>idx</td>
    <td>notes</td>
  </tr>
  <tr>
    <td>Product</td>
    <td>n/a</td>
    <td>amdsDimension:localized:Media
amdsDetailedDescription
amdsTechnicalInfo
amdsOurAdvices
amdsStockLevelThreshold
inPromotion
amdsTitle</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSPriceCoefficient
</td>
    <td>GenericItem</td>
    <td>amdsClientType:AMDSClientType
amdsPriceCoefficient</td>
    <td>AMDSPriceCoefficients
10400</td>
    <td>N</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSPointRelais</td>
    <td>GenericItem</td>
    <td>pointRelaisAddress:Address</td>
    <td>AMDSPointsRelais
10460</td>
    <td>N</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSWeightInterval</td>
    <td>GenericItem</td>
    <td>idInterval
lowerBound
upperBound
intervalPrice</td>
    <td>AMDSWeightIntervals
10470</td>
    <td>y</td>
    <td></td>
  </tr>
  <tr>
    <td>MediaContainer</td>
    <td>n/a</td>
    <td>amdsOrder (is type of int not Integer)
amdsPointOfService:PointOfService</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSStockNotification</td>
    <td>n/a</td>
    <td>productCode
email
pointOfServiceName (shouldn't be POS ref instead)?
baseSite:BaseSite</td>
    <td>AMDSStockNotification
10471</td>
    <td>y</td>
    <td></td>
  </tr>
  <tr>
    <td>AbstractOrder</td>
    <td>n/a</td>
    <td>amdsOrderWeight
amdsPointRelais:PointOfService
amdsPointOfService:PointOfService
transferTime</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>CMSNavigationNode</td>
    <td>n/a</td>
    <td>picture:localized:Media</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSDeliv
eryBlackItem</td>
    <td>GenericItem (indirectly)</td>
    <td>zipCode
Country
deliveryMode:ZoneDeliveryMode</td>
    <td>AMDSDeliveryBlackItem
1520 ← low typecode</td>
    <td>y</td>
    <td></td>
  </tr>
  <tr>
    <td>OpeningDay</td>
    <td>n/a</td>
    <td>openingTimePM:Date
closingTimePM:Date</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>ApparelProduct
ApparelStyleVariantProduct
ApparelSizeVariantProduct
ElectronicsColorVariantProduct</td>
    <td>n/a</td>
    <td>What for??</td>
    <td>n/a</td>
    <td>n/a</td>
    <td>What for??</td>
  </tr>
  <tr>
    <td>AMDSProductAddToCartComponent</td>
    <td>SimpleCMSComponent</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSArcelorMittalEtVousComponent</td>
    <td>RotatingImagesComponent</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSResponsiveCategoryImageBannerComponent</td>
    <td>BannerComponent</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSMyCompanyBannerPrimaryComponent</td>
    <td>BannerComponent</td>
    <td>banners:CompanyBannerSecondaryComponentList</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSMyCompanyBannerSecondaryComponent</td>
    <td>BannerComponent</td>
    <td>icon:Media
backgroundColor (colo defined as HYBRIS.LONG_STRING why?)</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSMyAccountBannerComponent</td>
    <td>BannerComponent</td>
    <td>icon:Media
bckgrounMobileImage:Media
backgroundColor (colo defined as HYBRIS.LONG_STRING why?)
</td>
    <td>As parent</td>
    <td>n/a</td>
    <td>DRY violation</td>
  </tr>
  <tr>
    <td>AMDSMyAccountBlockComponent</td>
    <td>BannerComponent</td>
    <td>component1:AMDSMyAccountBannerComponent
component2:AMDSMyAccountBannerComponent
component3:AMDSMyAccountBannerComponent
component4:AMDSMyAccountBannerComponent
component5:AMDSMyAccountBannerComponent</td>
    <td>As parent</td>
    <td>n/a</td>
    <td>Strange composition</td>
  </tr>
  <tr>
    <td>AMDSArcelorMittalEtVousBannerComponent</td>
    <td>BannerComponent</td>
    <td>icon:Media
backgroundColor (colo defined as HYBRIS.LONG_STRING why?)</td>
    <td>As parent</td>
    <td>n/a</td>
    <td>DRY violation</td>
  </tr>
  <tr>
    <td>AMDSArcelorMittalEtVousBlockComponent</td>
    <td>BannerComponent</td>
    <td>component1:AMDSArcelorMittalEtVousBannerComponent
component2:AMDSArcelorMittalEtVousBannerComponent
component3:AMDSArcelorMittalEtVousBannerComponent</td>
    <td>As parent</td>
    <td>n/a</td>
    <td>Strange composition</td>
  </tr>
  <tr>
    <td>AMDSHomePageBannerSearchBoxComponent</td>
    <td>SimpleResponsiveBannerComponent</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Category</td>
    <td>n/a</td>
    <td>amdsOurAdvices
amdsDetailedDescription</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AmdsRegisterQuestion</td>
    <td>GenericItem</td>
    <td>amdsCode
amdsRegisterQuestionText</td>
    <td>AmdsRegisterQuestion
10500</td>
    <td>N</td>
    <td></td>
  </tr>
  <tr>
    <td>B2BUnit</td>
    <td>n/a</td>
    <td>amdsCompanyName
amdsAdministrationName
amdsClientType:AMDSClientType
amdsNonClientType:AMDSNonClientType
sapDeliveryBlocked
attachmentAgency:PointOfService</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>B2BCustomer</td>
    <td>n/a</td>
    <td>amdsFirstName
amdsLastName
amdsMobilePhone
amdsFixedPhone
amdsFunction
registredInTheWebShop
amdsFirstSecurityQuestion
amdsFirstSecurityResponse
amdsSecondSecurityQuestion
amdsSecondSecurityResponse
amdsThirdSecurityQuestion
amdsThirdSecurityResponse
amdsCGVenteValidationTime
amdsCGUtilisationValidationTime
amdsPolitiqueDPValidationTime
isCreatedFromHybris
promoSubChecked
newsLetterSubChecked
amdsAccountActivationTime</td>
    <td>n/a</td>
    <td>n/a</td>
    <td>Quite many attributes - maybe should be refactored to other entities?</td>
  </tr>
  <tr>
    <td>AMDSZipCode</td>
    <td>GenericItem (indirectly)</td>
    <td>postalCode
country:Country
Does postalCode have to be HYBRIS.LONG_STRING?
</td>
    <td>AmdsZipCode
10206</td>
    <td>Y</td>
    <td>Is such model not present OOTB?</td>
  </tr>
  <tr>
    <td>DeliveryModeSupportedPostalCodes</td>
    <td>GenericItem (indirectly)</td>
    <td>supportedPostalCode</td>
    <td>DelivModSuppPostCode
10216</td>
    <td>n/a</td>
    <td>Look like created just for m2n relation TB checked</td>
  </tr>
  <tr>
    <td>UpdatedPasswordProcess</td>
    <td>StoreFrontCustomerProcess</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSStoreFrontCustomerProcess</td>
    <td>StoreFrontCustomerProcess</td>
    <td>token</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Address</td>
    <td>n/a</td>
    <td>Heading 
requiresPostalCodeValidation

Does heading have to be HYBRIS.LONG_STRING?</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Cart</td>
    <td>n/a</td>
    <td>deliveryComment
taxRate

Why not to use OOTB taxes?</td>
    <td>n/a</td>
    <td>n/a</td>
    <td>In comment the intention is to extend AbstractOrder but Cart is extended instead.</td>
  </tr>
  <tr>
    <td>Order</td>
    <td>n/a</td>
    <td>deliveryComment
sapOrderCode
sapPlacedOrderError</td>
    <td>n/a</td>
    <td>n/a</td>
    <td>n comment the intention is to extend AbstractOrder but Cart is extended instead.</td>
  </tr>
  <tr>
    <td>AbstractOrderEntry</td>
    <td>n/a</td>
    <td>amdsDynamicSourcingEntries:AMDSDynamicSourcingEntryList
transferTime (integer for time?)</td>
    <td>n/a</td>
    <td>n/a</td>
    <td>Put deliveryComment here?</td>
  </tr>
  <tr>
    <td>CMSAgencyRestriction</td>
    <td>AbstractRestriction</td>
    <td>agency:PointOfService</td>
    <td>As parent</td>
    <td>N</td>
    <td>naming Agency vs PointOfService</td>
  </tr>
  <tr>
    <td>FooterNavigationComponent</td>
    <td>n/a</td>
    <td>amdsContactArea:CMSParagraphComponent
banners:BannerComponentList</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>ClassificationAttribute</td>
    <td>n/a</td>
    <td>Visible
hmcIndexField - no hmc used</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSStockNotificationProcess</td>
    <td>StoreFrontProcess</td>
    <td>customer:B2BCustomer
Email
productID
productName
language:Language
pointOfServiceName - why not to use ref</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSMailingAbandonedCartsProcess</td>
    <td>StoreFrontProcess</td>
    <td>cart:Cart</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSChangingDeliveryAddressProcess</td>
    <td>StoreFrontProcess</td>
    <td>customer:B2BCustomer
deliveryAddress:Address
language:Language
pointOfServiceName - why not to use ref</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>PointOfService</td>
    <td>n/a</td>
    <td>Activated
idClientVdc
deliveryPartnerType:PointOfServiceTypeEnum</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Warehouse</td>
    <td>n/a</td>
    <td>onlineProductCatalogVersion:CatalogVersion</td>
    <td>n/a</td>
    <td>n/a</td>
    <td>Need to see what for</td>
  </tr>
  <tr>
    <td>AMDSAdminRegionalGroup</td>
    <td>UserGroup</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSSupportAgencyGroup</td>
    <td>CsAgentGroup</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSDynamicSourcingEntry</td>
    <td>GenericItem (indirectly)</td>
    <td>warehouse:Warehouse</td>
    <td>amdsDynamicSourcingEntry
10221</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSDynamicSourcing</td>
    <td>n/a</td>
    <td>Source:Warehouse
Target:Warehouse
priority
transferTime - why integer for time?
threshold</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Zone</td>
    <td>n/a</td>
    <td>zoneName</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSZoneDeliveryModeValue</td>
    <td>GenericItem</td>
    <td>Currency:currency
Minimum
Value
zone</td>
    <td>amdsZoneDeliModeValues
10219</td>
    <td>Y</td>
    <td></td>
  </tr>
  <tr>
    <td>ZoneDeliveryMode</td>
    <td>n/a</td>
    <td>supportedMaximumLength
supportedMaximumWeight</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>OrderProcess</td>
    <td>n/a</td>
    <td>notSupportedDeliveryMode
notSupportedDeliveryModeMessages:NotSupportedDeliveryModeMessages</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSB2BApprovalProcess</td>
    <td>B2BApprovalProcess</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSFavoriteList</td>
    <td>GenericItem</td>
    <td>Name
Description
default</td>
    <td>AMDSFavoriteList
10510</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>AMDSFavoriteListEntry</td>
    <td>GenericItem</td>
    <td>Product:product
addedDate</td>
    <td>AMDSFavoriteListEntry
10520</td>
    <td>n/a</td>
    <td></td>
  </tr>
</table>


2. Amdsaccountsummariesaddon - no items

3. Amdsbackoffice - no items

4. Amdscheckoutaddon - no items

5. Amdscockpits - no items

6. Amdscommerceorgaddon - no items

7. Amdscommercewebservices

<table>
  <tr>
    <td>ProductExpressUpdateCleanerCronJob</td>
    <td>CronJob</td>
    <td>queueTimeLimit</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>OldCartRemovalCronJob</td>
    <td>CronJob</td>
    <td>sites:BaseSiteCollection
cartRemovalAge
anonymousCartRemovalAge
</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
</table>


8. Amdscustomerticketingaddon - no items

9. Amdsfacades - no items

10. amdsfulfilmentprocess

<table>
  <tr>
    <td>ConsignmentProcess</td>
    <td>n/a</td>
    <td>Done
waitingForConsignment
warehouseConsignmentState:warehouseConsignmentState</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
</table>


11. Amdsinitialdata - no items

12. Amdsstorefront - no items

13. Amdstest - no items

14. Amdswsclient - no items

15. Mercanetcore - no items

16. Updatedata 

<table>
  <tr>
    <td>FileEntry</td>
    <td>GenericItem (indirectly)</td>
    <td>file:Media
Status:StatusFileEnum
errorMessage
</td>
    <td>FileEntry
31992</td>
    <td>N</td>
    <td></td>
  </tr>
  <tr>
    <td>UpdateReleaseExecution</td>
    <td>n/a</td>
    <td>Release
revisionNumber
executionDate
executionUser:User</td>
    <td>UpdateReleaseExecution
31993</td>
    <td>N</td>
    <td></td>
  </tr>
</table>


17. ssccore

<table>
  <tr>
    <td>SSCProduct</td>
    <td>Product</td>
    <td>sscAMDSProductId</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Order</td>
    <td>n/a</td>
    <td>sscGPAOOrderCode
sscPlacedOrderErrorCode
sscPlacedOrderErrorMessages</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Address</td>
    <td>n/a</td>
    <td>sscIsValidGPAO
sscIsVisible
sscCode</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Country</td>
    <td>n/a</td>
    <td>sscWeightMin
sscWeightMax</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>B2BUnit</td>
    <td>n/a</td>
    <td>sscIsExternal
sscIsBlocked</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>PriceRow</td>
    <td>n/a</td>
    <td>manufacturingUnit:Warehouse</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>Warehouse</td>
    <td>n/a</td>
    <td>sapCode</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>StockLevel</td>
    <td>n/a</td>
    <td>sscSalesUnit</td>
    <td>n/a</td>
    <td></td>
    <td></td>
  </tr>
</table>


18. Sscb2baddon - not a good place for defining items

<table>
  <tr>
    <td>SSCReorderAction</td>
    <td>SimpleCMSAction</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>SSCApproveOrderAction</td>
    <td>SimpleCMSAction</td>
    <td>No attributes, not abstract, no jalo additional impl in class </td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
</table>


19. Ssccockpits - no items

20. sscearlyloginadon

<table>
  <tr>
    <td>CMSSecurePortalRestriction</td>
    <td>AbstractRestriction</td>
    <td>Description - dynamic->cmsSecurePortalRestrictionDynamicDescription</td>
    <td>As parent</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>CMSSite</td>
    <td>n/a</td>
    <td>requiresAuthentication
enableRegistration</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>B2BRegistration</td>
    <td>n/a</td>
    <td>cmsSite:CMSSite
language:Language
currencyCurrency
baseStore:BaseStore
title:Title
Name
Email
Position
Telephone
telephoneExtension
companyName
companyAddressStreet
companyAddressStreetLine2
companyAddressCity
companyAddressPostalCode
companyAddressRegion:Region
companyAddressCountry:Country
Message
rejectReason
defaultB2BUnit:B2BUnit

Looks like to many attributes which maybe have a suitable entity OOTB</td>
    <td>B2bregistration
10040</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>B2BRegistrationProcess</td>
    <td>StoreFrontCustomerProcess</td>
    <td>registration:B2BRegistration</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>B2BRegistrationApprovedProcess</td>
    <td>B2BRegistrationProcess</td>
    <td>passwordResetToken</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td>B2BRegistrationRejectedProcess</td>
    <td>B2BRegistrationProcess</td>
    <td>rejectReason this attribute seems to duplicate the indirect attribute of B2Bregistration which is an attribute of parent process</td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
</table>


21. Sscfacades - no items

22. Sscfulfilmentprocess - no items

23. Sscinitialdata - no items

24. Sscstorefront - no items

25. ssc test - no items

26. Sscwsdata - no items

<table>
  <tr>
    <td></td>
    <td>n/a</td>
    <td></td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>n/a</td>
    <td></td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>n/a</td>
    <td></td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>n/a</td>
    <td></td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>n/a</td>
    <td></td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>n/a</td>
    <td></td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>n/a</td>
    <td></td>
    <td>n/a</td>
    <td>n/a</td>
    <td></td>
  </tr>
</table>



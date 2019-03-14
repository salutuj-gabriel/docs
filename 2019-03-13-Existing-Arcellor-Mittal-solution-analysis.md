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

    19. Update

  


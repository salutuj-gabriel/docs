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

![image alt text]({{ site.url }}/public/zhVisFitu2T7aod2alknCw_img_0.png)

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

  


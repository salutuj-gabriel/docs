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

    18. Init

    19. Update

  


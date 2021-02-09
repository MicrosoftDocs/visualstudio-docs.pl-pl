---
title: '&lt;Application — &gt; element (Programowanie Office w Visual Studio)'
description: Dowiedz się, w jaki sposób element aplikacji przestrzeni nazw vstav3 otacza opis rozwiązań pakietu Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 895a695f1de56c3041ad1723f1b6b30356c839df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900919"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;Application — &gt; element (Programowanie Office w Visual Studio)
  `application`Element `vstav3` przestrzeni nazw otacza opis rozwiązań pakietu Office. Elementy podrzędne są różne w przypadku dostosowań na poziomie dokumentu i dodatków narzędzi VSTO.

## <a name="syntax-for-document-level-customizations"></a>Składnia dla dostosowań na poziomie dokumentu

```xml
<application>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</application>
```

## <a name="syntax-for-application-level-add-ins"></a>Składnia dodatków na poziomie aplikacji

```xml
<application>
  <customization
    id
    <appAddin
      application
      loadBehavior
      keyName>
    <friendlyName></friendlyName>
    <description></description>
    <formRegions></formRegions>
  </customization>
</application>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `application`Element `vstav3` obszaru nazw jest węzłem, który otacza wszystkie informacje specyficzne dla dostosowania, które znajdują się w `vstov4` przestrzeni nazw.

 `application`Element nie ma żadnych atrybutów.

 `application`Element ma następujący element.

### <a name="customization"></a>Dostosowywanie
 Rola `customization` elementu w `vstov3` przestrzeni nazw jest definiowana w [&#60;dostosowania&#62; elementu &#40;programowanie Office w&#41;programu Visual Studio ](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `application` element w rozwiązaniu pakietu Office na poziomie dokumentu wdrożonym przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:document
        solutionId="73e" />
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `application` element w rozwiązaniu pakietu Office na poziomie aplikacji wdrożonym przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:appAddIn
        application="Outlook"
        loadBehavior="3"
        keyName="ContosoOutlookAddIn">
        <vstov4:friendlyName>
          ContosoOutlookAddIn
        </vstov4:friendlyName>
        <vstov4:description>
          ContosoOutlookAddIn - Outlook VSTO Add-in
          created with Visual Studio Tools for Office
        </vstov4:description>
        <vstov4:formRegions>
          <vstov4:formRegion
              name="OutlookAddIn1.FormRegion1">
            <vstov4:messageClass name="IPM.Note" />
            <vstov4:messageClass name="IPM.Contact" />
            <vstov4:messageClass name="IPM.Appointment" />
          </vstov4:formRegion>
        </vstov4:formRegions>
      </vstov4:appAddIn>
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
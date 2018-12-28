---
title: '&lt;Aplikacja&gt; — element (Office development w programie Visual Studio)'
titleSuffix: ''
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0668d3fce722633a10be82c5f7fcd1a0556a4e3b
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802712"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;Aplikacja&gt; — element (Office development w programie Visual Studio)
  `application` Elementu `vstav3` przestrzeni nazw opakowuje opis rozwiązań pakietu Office. Elementy podrzędne są różne dla dostosowywania poziomie dokumentu i dodatków narzędzi VSTO.

## <a name="syntax-for-document-level-customizations"></a>Składnia dla dostosowywania poziomie dokumentu

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

## <a name="syntax-for-application-level-add-ins"></a>Składnia dla dodatków poziomu aplikacji

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

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `application` Elementu `vstav3` przestrzeń nazw jest węzeł, który otacza wszystkie informacje dotyczące dostosowywania, który jest zawarty w `vstov4` przestrzeni nazw.

 `application` Element nie ma żadnych atrybutów.

 `application` Element ma następujący element.

### <a name="customization"></a>Dostosowywanie
 Rola `customization` element `vstov3` przestrzeń nazw została zdefiniowana w [ &#60;dostosowywania&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `application` elementu w rozwiązaniach pakietu Office poziomu dokumentu wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `application` elementu w dodatku poziomu aplikacji rozwiązania do pakietu Office wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
---
title: '&lt;element customizations &gt; (Programowanie Office w Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58d88f865e5f220000bf021b548e4b9c4b8745f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64790007"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;element customizations &gt; (Programowanie Office w Visual Studio)
  `customizations`Element `vstov4` przestrzeni nazw zawiera wszystkie informacje dotyczące instalowania i ładowania poszczególnych rozwiązań pakietu Office.

## <a name="syntax-for-document-level-customizations"></a>Składnia dla dostosowań na poziomie dokumentu

```xml
<customizations>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</customizations>
```

## <a name="syntax-for-vsto-add-ins"></a>Składnia dodatków narzędzi VSTO

```xml
<customizations>
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
</customizations>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `customizations`Element zawiera określone informacje dotyczące poszczególnych rozwiązań pakietu Office. Ten element musi należeć do następującej przestrzeni nazw: `vstov4=urn:schemas-microsoft-com:vsto.v4` . Elementy podrzędne zestawu muszą również znajdować się w tej przestrzeni nazw.

 `customizations`Element nie ma żadnych atrybutów.

 `customizations`Element ma następujący element podrzędny.

### <a name="customization"></a>Dostosowywanie
 Wymagany. `customization`Element w `vstov4` przestrzeni nazw jest zdefiniowany w [&#60;dostosowania&#62; elementu &#40;programowanie Office w&#41;programu Visual Studio ](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Przykład dostosowania na poziomie dokumentu

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `customizations` element do dostosowania na poziomie dokumentu.

> [!NOTE]
> Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:document
      solutionId="73e" />
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="example-of-a-vsto-add-in"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `customizations` element dodatku VSTO. Jest to dodatek narzędzi VSTO dla programu Outlook, który obejmuje regiony formularzy. Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
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
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
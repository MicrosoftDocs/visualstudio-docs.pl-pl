---
title: '&lt;&gt;element dostosowania (Programowanie Office w Visual Studio)'
description: Dowiedz się, w jaki sposób element Customization przestrzeni nazw vstov4 opisuje określone rozwiązanie pakietu Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f50b441393e9d07dcd0b409248f199484022654
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844117"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;&gt;element dostosowania (Programowanie Office w Visual Studio)
  `customization`Element `vstov4` przestrzeni nazw opisuje określone rozwiązanie pakietu Office. Elementy podrzędne są różne w przypadku dostosowań na poziomie dokumentu i dodatków narzędzi VSTO.

## <a name="syntax-for-document-level-customizations"></a>Składnia dla dostosowań na poziomie dokumentu

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>Składnia dodatków narzędzi VSTO

```xml
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
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `customization`Element zawiera informacje dotyczące dostosowywania. Ten element musi należeć do następującej przestrzeni nazw: `vstov4=urn:schemas-microsoft-com:vsto.v4` . Istnieje jeden `customization` element dla każdego rozwiązania pakietu Office. Na przykład w przypadku wdrażania trzech rozwiązań pakietu Office w ramach wdrożenia obejmującego wiele projektów istnieją trzy `customization` elementy w manifeście aplikacji.

 Elementy podrzędne zestawu muszą również znajdować się w tej przestrzeni nazw.

 `customization`Element ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`id`|Wymagane dla wdrożenia z obsługą kilku projektów. `id`Element jednoznacznie identyfikuje rozwiązanie pakietu Office.|

### <a name="document-level-customizations"></a>Document-Level dostosowania
 `customization`Element ma następujący element podrzędny.

#### <a name="document"></a>dokument
 `document`Element w `vstov4` przestrzeni nazw jest zdefiniowany w [&#60;dokumentu&#62; elementu &#40;programowanie Office w&#41;Visual Studio ](../vsto/document-element-office-development-in-visual-studio.md).

### <a name="vsto-add-ins"></a>Dodatki narzędzi VSTO
 `customization`Element ma następujący element podrzędny.

#### <a name="appaddin"></a>appAddin
 `appAddin`Element w `vstov4` przestrzeni nazw jest zdefiniowany w [&#60;appAddin&#62; elementu &#40;programowanie Office w&#41;programu Visual Studio ](../vsto/appaddin-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Przykład dostosowania na poziomie dokumentu

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `customization` element do dostosowania na poziomie dokumentu. Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `customization` element dodatku VSTO. Jest to dodatek narzędzi VSTO dla programu Outlook, który obejmuje regiony formularzy. Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
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
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
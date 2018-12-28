---
title: '&lt;Dostosowywanie&gt; — element (Office development w programie Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: a93c5fcd5b8863a4f0f80e48caa915a11e092587
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802215"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;Dostosowywanie&gt; — element (Office development w programie Visual Studio)
  `customization` Elementu `vstov4` przestrzeni nazw w tym artykule opisano konkretnego rozwiązania pakietu Office. Elementy podrzędne są różne dla dostosowywania poziomie dokumentu i dodatków narzędzi VSTO.

## <a name="syntax-for-document-level-customizations"></a>Składnia dla dostosowywania poziomie dokumentu

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>Składnia dla dodatków narzędzi VSTO

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

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `customization` Element zawiera informacje dotyczące dostosowywania. Ten element musi znajdować się w następującej przestrzeni nazw: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Istnieje `customization` elementu dla każdego rozwiązania pakietu Office. Na przykład, jeśli wdrożono trzy rozwiązań pakietu Office w ramach wdrożenia wielu projektów, dostępne są trzy `customization` elementów w manifeście aplikacji.

 Elementy podrzędne zestawu również musi być w tej przestrzeni nazw.

 `customization` Element ma atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`id`|Wymagane do wdrożenia wielu projektów. `id` Element unikatowo identyfikuje rozwiązań pakietu Office.|

### <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentu
 `customization` Element ma następujący element podrzędny.

#### <a name="document"></a>dokument
 `document` Element `vstov4` przestrzeń nazw została zdefiniowana w [ &#60;dokumentu&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).

### <a name="vsto-add-ins"></a>Dodatków narzędzi VSTO
 `customization` Element ma następujący element podrzędny.

#### <a name="appaddin"></a>appAddin
 `appAddin` Element `vstov4` przestrzeń nazw została zdefiniowana w [ &#60;appAddin&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Przykład dostosowywania poziomie dokumentu

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `customization` element dla dostosowywania poziomie dokumentu. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `customization` element dla dodatku narzędzi VSTO. Jest to dodatek narzędzi VSTO dla programu Outlook, która obejmuje regionów formularzy w. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

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
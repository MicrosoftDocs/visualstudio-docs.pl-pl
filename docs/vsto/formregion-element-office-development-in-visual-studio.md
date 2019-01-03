---
title: '&lt;elementu formRegion&gt; — element (Office development w programie Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86aa6b715a99c962a2f0fd627dd6d3fb7618108a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987696"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;elementu formRegion&gt; — element (Office development w programie Visual Studio)
  `formRegion` Elementu `vstov4` obszar nazw identyfikuje programu Microsoft Office Outlook regionu formularza, który jest skojarzony z dodatku narzędzi VSTO.

## <a name="syntax"></a>Składnia

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `formRegion` Elementu `vstov4` obszar nazw identyfikuje region formularza, który jest skojarzony z dodatku narzędzi VSTO dla programu Outlook. Jest wymagane tylko dla dodatków narzędzi VSTO dla programu Outlook, obejmujących regionów formularza.

 Może istnieć wiele `formRegion` elementy zdefiniowane wewnątrz `formRegions` element dla pojedynczego dodatku narzędzi VSTO.

 `formRegion` Element ma atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagana. Określa nazwę regionu formularza.|

 `formRegion` Element ma następujących elementów podrzędnych.

### <a name="messageclass"></a>Klasa_wiadomości
 `messageClass` Element identyfikuje formularza programu Outlook, który jest skojarzony z regionu formularza.

 `messageClass` Element ma atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagana. Identyfikuje formularz, który jest skojarzony z regionu formularza.|

## <a name="example"></a>Przykład
 W poniższym przykładzie kodu pokazano `formRegion` elementu w manifeście aplikacji dla dodatku narzędzi VSTO dla programu Outlook wdrażane za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Istnieją trzy klasy wiadomości, skojarzone z tym regionem jeden formularz. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
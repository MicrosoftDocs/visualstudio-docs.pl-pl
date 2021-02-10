---
title: '&lt;formRegions — &gt; element (Programowanie Office w Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a1a718c6a247528788d91e9c1f30ad636acb7ab9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970338"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions — &gt; element (Programowanie Office w Visual Studio)
  `formRegions`Element `vstov4` przestrzeni nazw Microsoft Office zawiera regiony formularzy programu Outlook, które są skojarzone z dodatkiem narzędzi VSTO.

## <a name="syntax"></a>Składnia

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `formRegions`Element `vstov4` przestrzeni nazw zawiera wszystkie `formRegion` elementy dodatku narzędzi VSTO dla programu Outlook. Jest to wymagane tylko w przypadku dodatków VSTO programu Outlook, które obejmują regiony formularzy.

 `formRegions`W manifeście aplikacji może być zdefiniowany tylko jeden element.

 `formRegions`Element nie ma żadnych atrybutów.

 `formRegions`Element ma następujący element.

### <a name="formregion"></a>formRegion
 Wymagane dla dodatków VSTO programu Outlook obejmujących regiony formularzy. `formRegion`Element jest zdefiniowany w [&#60;FormRegion&#62; elementu &#40;Programowanie Office w&#41;programu Visual Studio ](../vsto/formregion-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `formRegions` element w manifeście aplikacji dla rozwiązania Office na poziomie aplikacji wdrożonego za pomocą programu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
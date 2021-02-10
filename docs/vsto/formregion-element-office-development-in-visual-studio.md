---
title: '&lt;formRegion — &gt; element (Programowanie Office w Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 469b041ac879753e5fe4be0f9bd739be1030a942
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970393"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion — &gt; element (Programowanie Office w Visual Studio)
  `formRegion`Element `vstov4` przestrzeni nazw identyfikuje region formularza programu Outlook Microsoft Office, który jest skojarzony z dodatkiem VSTO.

## <a name="syntax"></a>Składnia

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `formRegion`Element `vstov4` przestrzeni nazw identyfikuje region formularza skojarzony z dodatkiem VSTO programu Outlook. Jest to wymagane tylko w przypadku dodatków VSTO programu Outlook, które obejmują regiony formularzy.

 W `formRegion` obrębie elementu można zdefiniować wiele elementów `formRegions` dla jednego dodatku VSTO.

 `formRegion`Element ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagane. Określa nazwę regionu formularza.|

 `formRegion`Element ma następujące elementy podrzędne.

### <a name="messageclass"></a>messageClass
 `messageClass`Element identyfikuje formularz programu Outlook skojarzony z regionem formularza.

 `messageClass`Element ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagane. Identyfikuje formularz, który jest skojarzony z regionem formularza.|

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `formRegion` element w manifeście aplikacji dla dodatku VSTO programu Outlook wdrożonego przy użyciu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Z tym jednym regionem formularza są skojarzone trzy klasy komunikatów. Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Zobacz też

- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
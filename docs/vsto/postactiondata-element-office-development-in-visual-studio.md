---
title: '&lt;postActionData — &gt; element (Programowanie Office)'
description: Element postActionData przestrzeni nazw vstav3 określa dane skojarzone z każdą akcją po wdrożeniu, która jest uruchamiana po zainstalowaniu rozwiązań pakietu Office.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a75f61c6d1f80a127f49d96c4e3f4910c66dd8aa
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470069"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;postActionData — &gt; element (Programowanie Office)
  `postActionData`Element `vstav3` przestrzeni nazw określa dane skojarzone z każdą akcją po wdrożeniu, która jest uruchamiana po zainstalowaniu rozwiązań pakietu Office.

## <a name="syntax"></a>Składnia

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `postActionData`Element jest opcjonalny i znajduje się w `vstav3` przestrzeni nazw. Istnieje jeden `postActionData` element zdefiniowany w manifeście aplikacji dla każdej akcji wykonywanej po wdrożeniu.

 `postActions`Element nie ma żadnych atrybutów.

 `postActions` nie ma elementów podrzędnych.

## <a name="post-deployment-action-example"></a>Przykład akcji wykonywanej po wdrożeniu

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `postAction` element w manifeście aplikacji dla rozwiązania pakietu Office wdrożonego za pomocą programu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)

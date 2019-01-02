---
title: '&lt;postactiondata —&gt; — element (Office development w programie Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f27cf59f157c0760ea0c204a8c079dd4616777da
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947273"
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postactiondata —&gt; — element (Office development w programie Visual Studio)
  `postActionData` Elementu `vstav3` przestrzeń nazw określa dane skojarzone z dowolną akcję po wdrożeniu, która jest uruchamiana po zainstalowaniu rozwiązania dla pakietu Office.

## <a name="syntax"></a>Składnia

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `postActionData` Element jest opcjonalny, a w `vstav3` przestrzeni nazw. Istnieje `postActionData` elementu zdefiniowanego w manifeście aplikacji dla każdej akcji po wdrożeniu.

 `postActions` Element nie ma żadnych atrybutów.

 `postActions` nie ma elementów podrzędnych.

## <a name="post-deployment-action-example"></a>Przykład akcję powdrożeniową

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `postAction` elementu w manifeście aplikacji dla rozwiązań pakietu Office, wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)

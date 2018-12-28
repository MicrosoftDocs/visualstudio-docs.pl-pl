---
title: '&lt;customhostspecified —&gt; — element (Office development w programie Visual Studio)'
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
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f1209460448b02cfb05329c8c3f487f6ef444649
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802614"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customhostspecified —&gt; — element (Office development w programie Visual Studio)
  `customHostSpecified` Element wskazuje, że to rozwiązanie nie jest autonomiczną aplikację. Rozwiązania dla pakietu Office zawierają składniki, które są hostowane wewnątrz aplikacji Microsoft Office.

## <a name="syntax"></a>Składnia

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `customHostSpecified` Element jest wymagany dla rozwiązań pakietu Office. Tego elementu jest `co.v1` przestrzeni nazw i określa, że to wdrożenie zawiera składnik, który zostanie wdrożony wewnątrz niestandardowego hosta, a nie jest autonomiczną aplikacją.

 Ten element jest pierwszy element podrzędny `<entrypoint>` elementu w manifeście aplikacji. Może być brak elementów podrzędnych w tym `<entrypoint>` element lub [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zgłosi błąd sprawdzania poprawności podczas instalacji.

 Ten element ma żadnych atrybutów i Brak elementów podrzędnych.

## <a name="example"></a>Przykład
 W poniższym przykładzie kodu pokazano `customHostSpecified` elementu w manifeście aplikacji dla rozwiązań pakietu Office. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
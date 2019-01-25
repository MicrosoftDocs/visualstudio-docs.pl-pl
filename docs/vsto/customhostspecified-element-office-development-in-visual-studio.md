---
title: '&lt;customhostspecified —&gt; — element (Office development w programie Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26597796c99d3ab8740812819cf3aa5568e2985b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874383"
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
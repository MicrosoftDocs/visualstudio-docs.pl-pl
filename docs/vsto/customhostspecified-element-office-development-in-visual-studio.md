---
title: '&lt;customHostSpecified — &gt; element (Programowanie Office w Visual Studio)'
description: Dowiedz się, w jaki sposób element customHostSpecified wskazuje, że to rozwiązanie nie jest aplikacją autonomiczną.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
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
ms.openlocfilehash: e8327c6e154f051f5ce79d41ceaa696e330c794f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848134"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified — &gt; element (Programowanie Office w Visual Studio)
  `customHostSpecified`Element wskazuje, że to rozwiązanie nie jest aplikacją autonomiczną. Rozwiązania pakietu Office zawierają składniki hostowane w aplikacjach Microsoft Office.

## <a name="syntax"></a>Składnia

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `customHostSpecified`Element jest wymagany dla rozwiązań pakietu Office. Ten element znajduje się w `co.v1` przestrzeni nazw i określa, że to wdrożenie zawiera składnik, który zostanie wdrożony w ramach hosta niestandardowego i nie jest aplikacją autonomiczną.

 Ten element jest elementem podrzędnym pierwszego `<entrypoint>` elementu w manifeście aplikacji. W tym elemencie nie mogą istnieć żadne inne elementy podrzędne `<entrypoint>` lub podczas [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] instalacji wystąpi błąd walidacji.

 Ten element nie ma atrybutów ani elementów podrzędnych.

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `customHostSpecified` element w manifeście aplikacji dla rozwiązania pakietu Office. Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
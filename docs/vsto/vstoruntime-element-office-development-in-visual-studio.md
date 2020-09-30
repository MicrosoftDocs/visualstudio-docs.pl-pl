---
title: '&lt;vstoRuntime — &gt; element (Programowanie Office w Visual Studio)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffebff9e5cee8666d1b178fca09262ecd45c99b1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584363"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime — &gt; element (Programowanie Office w Visual Studio)
  `vstoRuntime`Element `vstav3` przestrzeni nazw zawiera obsługiwaną wersję Visual Studio Tools dla środowiska uruchomieniowego pakietu Office dla określonego rozwiązania pakietu Office.

## <a name="syntax"></a>Składnia

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `vstoRuntime`Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw. Jeśli rozwiązanie pakietu Office obsługuje dwie wersje Visual Studio Tools dla środowiska uruchomieniowego pakietu Office, istnieją dwa `vstoRuntime` elementy w manifeście aplikacji.

 `vstoRuntime`Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`release`|Wymagany. Wersja wydania Visual Studio Tools dla środowiska uruchomieniowego pakietu Office.|
|`version`|Wymagany. Numer wersji Visual Studio Tools dla środowiska uruchomieniowego pakietu Office.|
|`supportUrl`|Opcjonalny. Link do lokalizacji instalacji Visual Studio Tools dla środowiska uruchomieniowego pakietu Office.|

 `vstoRuntime` nie ma elementów.

## <a name="example"></a>Przykład
 Poniższy przykład kodu ilustruje `vstoRuntime` element w manifeście aplikacji dla rozwiązania pakietu Office wdrożonego za pomocą programu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)

---
title: '&lt;vstoruntime —&gt; — element (Office development w programie Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c5562bdfa8c9cce8e9490392ad81a7e2e697160c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930703"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoruntime —&gt; — element (Office development w programie Visual Studio)
  `vstoRuntime` Elementu `vstav3` przestrzeń nazw zawiera obsługiwanej wersji programu Visual Studio Tools for Office runtime dla określonych rozwiązań pakietu Office.

## <a name="syntax"></a>Składnia

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `vstoRuntime` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw. Jeśli rozwiązanie Office obsługuje dwie wersje programu Visual Studio Tools dla pakietu Office runtime, istnieją dwa `vstoRuntime` elementów w manifeście aplikacji.

 `vstoRuntime` Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`release`|Wymagana. Wydanej wersji programu Visual Studio Tools for Office runtime.|
|`version`|Wymagana. Numer wersji programu Visual Studio Tools for Office runtime.|
|`supportUrl`|Opcjonalna. Link do lokalizacji instalacji programu Visual Studio Tools for Office runtime.|

 `vstoRuntime` nie ma żadnych elementów.

## <a name="example"></a>Przykład
 W poniższym przykładzie kodu pokazano `vstoRuntime` elementu w manifeście aplikacji dla rozwiązań pakietu Office, wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)

---
title: '&lt;punkt wejścia&gt; — element (Office development w programie Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd3da83a25a05690e56d229f61ee709473171dd7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62799776"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;punkt wejścia&gt; — element (Office development w programie Visual Studio)
  Każdy `entryPoint` elementu `vstav3` obszar nazw identyfikuje zestaw dostosowania, który powinien zostać uruchomiony, jeśli to [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aplikacja jest zainstalowana.

## <a name="syntax"></a>Składnia

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `entryPoint` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw.

 Każdy `entryPoint` element może zawierać tylko jeden zestaw dostosowania. Może istnieć wiele `entryPoint` elementy zdefiniowane w manifeście aplikacji.

 `entryPoint` Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`class`|Wymagana. Identyfikuje zestaw dostosowania do wykonania. Składnia dla tego atrybutu jest *NamespaceName.ClassName*.|

 `entryPoint` ma następujący element.

### <a name="assemblyidentity"></a>assemblyIdentity
 Wymagana. `assemblyIdentity` Element `vstav3` przestrzeni nazw, który odwołuje się do istniejącego `assemblyIdentity` element [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] manifestu aplikacji.

 Rola `assemblyIdentity` i jego atrybuty jest zdefiniowany w [ &#60;assemblyIdentity&#62; elementu &#40;aplikacji ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-application.md).

## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `entryPoint` elementów w aplikacji manifestu dla rozwiązań Office poziomie dokumentu, wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:entryPoint
  class="ContosoExcelWorkbook.ThisWorkbook">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet1">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet2">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet3">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `entryPoint` elementu w manifeście aplikacji dla rozwiązań pakietu Office dodatku poziomu aplikacji wdrożonych za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
---
description: Każdy element punktu wejścia w przestrzeni nazw vstav3 identyfikuje zestaw dostosowywania, który powinien być uruchamiany podczas instalacji tej aplikacji ClickOnce.
title: '&lt;entryPoint — &gt; element (Programowanie Office w Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 581274ea58dafa8021cb456a0c7cb1e6bf98da32
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223722"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;entryPoint — &gt; element (Programowanie Office w Visual Studio)
  Każdy `entryPoint` element `vstav3` przestrzeni nazw identyfikuje zestaw dostosowywania, który powinien być uruchamiany podczas instalacji tej [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aplikacji.

## <a name="syntax"></a>Składnia

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `entryPoint`Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw.

 Każdy `entryPoint` element może zawierać tylko jeden zestaw dostosowywania. `entryPoint`W manifeście aplikacji może być zdefiniowanych wiele elementów.

 `entryPoint`Element ma następujące atrybuty.

|Atrybut|Opis|
|---------------|-----------------|
|`class`|Wymagane. Identyfikuje zestaw dostosowywania do wykonania. Składnia tego atrybutu jest *NamespaceName. ClassName*.|

 `entryPoint` ma następujący element.

### <a name="assemblyidentity"></a>assemblyIdentity
 Wymagane. `assemblyIdentity`Element w `vstav3` przestrzeni nazw odwołuje się do istniejącego `assemblyIdentity` elementu w [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] manifeście aplikacji.

 Rola `assemblyIdentity` i jej atrybuty są zdefiniowane w [&#60;assemblyIdentity&#62; elementu &#40;aplikacji ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-application.md).

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `entryPoint` elementy w manifeście aplikacji dla rozwiązań pakietu Office na poziomie dokumentu wdrożonych przy użyciu programu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="description"></a>Opis
 Poniższy przykład kodu ilustruje `entryPoint` element w manifeście aplikacji dla rozwiązania Office na poziomie aplikacji wdrożonego za pomocą programu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Ten przykład kodu jest częścią większego przykładu dostępnego w [manifestach aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

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

## <a name="see-also"></a>Zobacz też

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)

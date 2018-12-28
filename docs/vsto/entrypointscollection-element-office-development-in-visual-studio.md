---
title: '&lt;entrypointscollection —&gt; — element (Office development w programie Visual Studio)'
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
- <entryPointsCollection> element
- application manifests [Office development in Visual Studio], <entryPointsCollection> element
- entryPointsCollection element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 473168bea81b28de70b46baab6c3a1c7f3f0ea2e
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803702"
---
# <a name="ltentrypointscollectiongt-element-office-development-in-visual-studio"></a>&lt;entrypointscollection —&gt; — element (Office development w programie Visual Studio)
  `entryPointsCollection` Elementu `vstav3` przestrzeń nazw zawiera wszystkie `entryPoints` elementy związane z rozwiązań pakietu Office.

## <a name="syntax"></a>Składnia

```xml
<entryPointsCollection>
  <entryPoints>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
    <entryPoint>
    </entryPoint>
  </entryPoints>
</entryPointsCollection>
```

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `entryPointsCollection` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw. Elementy podrzędne również musi być w tej przestrzeni nazw. Jest tylko jedna `entryPointsCollection` elementu zdefiniowanego w manifeście aplikacji.

 `entryPointsCollection` Element nie ma żadnych atrybutów.

 `entryPointsCollection` zawiera następujące elementy.

### <a name="entrypoints"></a>punkty wejścia
 Wymagana. Rola `entryPoints` element `vstav3` przestrzeń nazw została zdefiniowana w [ &#60;punkty wejścia&#62; elementu &#40;programowanie Office w Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `entryPointsCollection` elementu w manifeście aplikacji wdrożone za pomocą rozwiązania poziomu dokumentu [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:entryPointsCollection>
    <vstav3:entryPoints>
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
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
```

## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `entryPointsCollection` elementu w manifeście aplikacji dla rozwiązań pakietu dodatku poziomu aplikacji wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoOutlookAddIn.ThisAddIn">
        <assemblyIdentity
          name="ContosoOutlookAddIn"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
```

## <a name="multi-project-deployment-example"></a>Przykład wdrożenia wielu projektów

### <a name="description"></a>Opis
 W poniższym przykładzie kodu pokazano `entryPointsCollection` elementu w manifeście aplikacji do wdrożenia wielu projektów z dwóch rozwiązań pakietu Office. Ten przykład kodu jest częścią większego przykładu przewidzianego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Kod

```xml
<vstav3:entryPointsCollection>
      <vstav3:entryPoints
        id="ContosoExcel">
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
      </vstav3:entryPoints>
      <vstav3:entryPoints
        id="ContosoOutlook">
        <vstav3:entryPoint
          class="ContosoOutlookAddIn.ThisAddIn">
          <assemblyIdentity
            name="ContosoOutlookAddIn"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
      </vstav3:entryPoints>
    </vstav3:entryPointsCollection>
```

## <a name="see-also"></a>Zobacz także

- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
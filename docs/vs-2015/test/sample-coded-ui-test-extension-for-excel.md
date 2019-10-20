---
title: Przykładowe rozszerzenie kodowanego testu interfejsu użytkownika dla programu Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c6075f9f95f7dc1d21db91936cf35c76f9b2e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672229"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Przykładowe rozszerzenie kodowanych testów UI dla programu Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Składnik rozszerzenia przykładu jest uruchamiany w procesie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kodowanego testu interfejsu użytkownika i jest nieco hierarchiczny z klasą `ExtensionPackage` na podstawie. Klasy `TechnologyManager`, `ActionFilter` i `PropertyProvider` znajdują się na następnym poziomie, z elementami kontrolnymi na najwyższym poziomie.

 ![Architektura rozszerzenia testu programu Excel](../test/media/excel-extarch.png "Excel_ExtArch") Architektura rozszerzeń programu Excel

## <a name="extension-points"></a>Punkty rozszerzenia
 Klasy te reprezentują punkty rozszerzenia, które są implementowane w przykładzie w celu włączenia kodowanego testowania interfejsu użytkownika dla [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

### <a name="extensionpackage"></a>ExtensionPackage
 Dziedziczone z klasy <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, jest to punkt wejścia dla rozszerzenia kodowanego testowania interfejsu użytkownika. Zaimplementowanie tej klasy abstrakcyjnej daje wewnętrzny dostęp do struktury testowanych interfejsów użytkownika do niestandardowego Menedżera technologii testów interfejsu użytkownika, dostawcy właściwości testu interfejsu użytkownika i filtru akcji testu interfejsu użytkownika w celu przetestowania nowego interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Klasa ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Dziedziczone z klasy <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, ta klasa zawiera Menedżera technologii do nagrywania i odtwarzania testów. Aby uzyskać więcej informacji, zobacz [Klasa TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Dziedziczone z klasy [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) , ta Klasa dostarcza klasę bazową do agregowania wyników testu podobnego do pojedynczego wyniku testu. Aby uzyskać więcej informacji, zobacz [Klasa ActionFilter](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Elementy technologii
 Klasa bazowa dziedziczona z klasy <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> stanowi podstawę dla elementów technologicznych w testach interfejsu użytkownika, które mogą być rejestrowane i odtwarzane. Aby uzyskać więcej informacji, zobacz [klasy elementów](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Dziedziczone z klasy <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>, ta Klasa dostarcza klasę bazową do obsługi właściwości elementów interfejsu użytkownika dla nagrywania i odtwarzania testów. Aby uzyskać więcej informacji, zobacz [Klasa PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [ExtensionPackage, klasa](../test/sample-excel-extension-extensionpackage-class.md)
- [TechnologyManager, klasa](../test/sample-excel-extension-technologymanager-class.md)
- [ActionFilter, klasa](../test/sample-excel-extension-actionfilter-class.md)
- [Klasy elementów](../test/sample-excel-extension-element-classes.md)
- [PropertyProvider, klasa](../test/sample-excel-extension-propertyprovider-class.md)

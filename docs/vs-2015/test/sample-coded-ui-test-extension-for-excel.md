---
title: Przykładowe rozszerzenie kodowanych testów UI dla programu Excel | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e8e3bebc82ffc2f714a6418afdb73de9092aab55
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158204"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Przykładowe rozszerzenie kodowanych testów UI dla programu Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Składnik rozszerzenia przykładu, który jest uruchamiany w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proces kodowanego testu interfejsu użytkownika i jest nieco hierarchiczne z `ExtensionPackage` klasę podstawową. `TechnologyManager`, `ActionFilter`, I `PropertyProvider` klasy są przy następnym poziomie, z elementami kontroli na najwyższym poziomie.  
  
 ![Architektura rozszerzenia Test w programie Excel](../test/media/excel-extarch.png "Excel_ExtArch")  
Architektura rozszerzenia programu Excel  
  
## <a name="extension-points"></a>Punkty rozszerzenia  
 Te klasy reprezentują punkty rozszerzenia, które są implementowane w przykładzie, aby umożliwić kodowanych testów dla interfejsu użytkownika [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
### <a name="extensionpackage"></a>ExtensionPackage  
 Odziedziczone po <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> klasy, jest to punkt wejścia dla kodowanych testów rozszerzenia interfejsu użytkownika. Implementowanie ta klasa ogólna zapewnia coded UI testowania wewnętrznego dostęp do niestandardowych Menedżer ds. testów interfejsu użytkownika, Dostawca właściwości testu interfejsu użytkownika i filtr akcji testu interfejsu użytkownika do testowania nowego interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [klasa ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md).  
  
### <a name="technologymanager"></a>TechnologyManager  
 Odziedziczone po <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> klasy, ta klasa udostępnia Menedżera technologii do odtwarzania i nagrywania testu. Aby uzyskać więcej informacji, zobacz [klasa TechnologyManager](../test/sample-excel-extension-technologymanager-class.md).  
  
### <a name="actionfilter"></a>ActionFilter  
 Odziedziczone po <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> klasy, ta klasa udostępnia klasę bazową dla agregacji wyniki akcji testowych podobne do wyniku testu w jednym. Aby uzyskać więcej informacji, zobacz [klasa ActionFilter](../test/sample-excel-extension-actionfilter-class.md).  
  
### <a name="technology-elements"></a>Elementy technologii  
 Odziedziczone po klasie podstawowej <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> klasy stanowi podstawę technologii elementów, które mogą być rejestrowane i odtwarzać testy interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [klasami](../test/sample-excel-extension-element-classes.md).  
  
### <a name="propertyprovider"></a>PropertyProvider  
 Odziedziczone po <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> klasy, ta klasa udostępnia klasę bazową do obsługi właściwości elementów interfejsu użytkownika do odtwarzania i nagrywania testu. Aby uzyskać więcej informacji, zobacz [klasa PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Klasa ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md)   
 [Klasa TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)   
 [Klasa ActionFilter](../test/sample-excel-extension-actionfilter-class.md)   
 [Klasy elementów](../test/sample-excel-extension-element-classes.md)   
 [PropertyProvider, klasa](../test/sample-excel-extension-propertyprovider-class.md)

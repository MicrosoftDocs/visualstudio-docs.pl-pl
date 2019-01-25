---
title: 'Przykładowe rozszerzenie programu Excel: Klasa ExtensionPackage | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 668913d231115e955cc50df10de045eab3d4ac92
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792024"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Przykładowe rozszerzenie programu Excel: ExtensionPackage — Klasa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta klasa rozszerza <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> klasy i zapewnia punkt wejścia dla kodowanego testu interfejsu użytkownika, która jest testowana [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] arkusza.  
  
## <a name="assembly-attribute"></a>Atrybutu zestawu  
 Plik rozpoczyna się od atrybutu zestawu, który identyfikuje zestaw jako rozszerzenie testu interfejsu użytkownika.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Ten atrybut deklaruje nazwę klasy bazowej, nazwa klasy pakietu i w pełni kwalifikowaną nazwę klasy dla klasy pakietu rozszerzenia niestandardowego.  
  
## <a name="simple-properties"></a>Proste właściwości  
 Ta klasa posiada właściwości, które dostarczają wartości, które są używane przez kodowanych testów interfejsu użytkownika do identyfikujących i opisujących rozszerzenie i zestawu. Zobacz komentarze kodu, aby uzyskać więcej informacji.  
  
## <a name="getservice-method"></a>Metoda GetService  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> Metodą jest punktem pojedynczy wpis, używane przez kodowanych testów interfejsu użytkownika, aby uzyskać dostęp do Menedżera technologii, Dostawca właściwości i filtr akcji, określonych przez klasę bazową dla każdego obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Rozszerzanie kodowanych testów interfejsu użytkownika i rejestrowanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

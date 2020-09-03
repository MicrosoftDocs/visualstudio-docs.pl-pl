---
title: 'Przykładowe rozszerzenie programu Excel: Klasa ExtensionPackage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1c1f4c746fa505b50bab9caa7a516a2abc77f69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672209"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Przykładowe rozszerzenie programu Excel: klasa ExtensionPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta Klasa rozszerza <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> klasę i udostępnia punkt wejścia dla kodowanego testu interfejsu użytkownika, który testuje [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] Arkusz.

## <a name="assembly-attribute"></a>Atrybut zestawu
 Plik rozpoczyna się od atrybutu zestawu, który identyfikuje zestaw jako rozszerzenie testu interfejsu użytkownika.

```
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
    "ExcelExtensionPackage",
    typeof(
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]
```

 Ten atrybut deklaruje nazwę klasy bazowej, nazwę klasy pakietu oraz w pełni kwalifikowaną nazwę klasy niestandardowego pakietu rozszerzenia.

## <a name="simple-properties"></a>Proste właściwości
 Ta klasa ma właściwości, które dostarczają wartości, które są używane przez kodowane środowisko testowania interfejsu użytkownika do identyfikowania i opisywania rozszerzenia oraz zestawu. Aby uzyskać więcej informacji, zobacz Komentarze do kodu.

## <a name="getservice-method"></a>GetService — Metoda
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A>Metoda jest pojedynczym punktem wejścia używanym przez zakodowaną strukturę testowania interfejsu użytkownika w celu uzyskania dostępu do Menedżera technologii, dostawcy właściwości i filtru akcji, jak określono przez klasę bazową dla każdego obiektu.

## <a name="see-also"></a>Zobacz też
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> [Rozszerzanie zakodowanych testów interfejsu użytkownika i nagrywanie akcji obsługujących program Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

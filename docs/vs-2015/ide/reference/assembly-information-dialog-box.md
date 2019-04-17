---
title: Informacje o zestawie — okno dialogowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 616a46b4d8349bd2c385fda0dd36e6dc69fa60af
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663875"
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Informacje o zestawie** okno dialogowe służy do określania wartości [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] globalnej atrybuty, które są przechowywane w pliku AssemblyInfo tworzone automatycznie w projekcie. W **Eksploratora rozwiązań**, plik znajduje się w **mój projekt** w węźle [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (kliknij **Pokaż wszystkie pliki** do jego wyświetlania); znajduje się w obszarze  **Właściwości** w [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Aby uzyskać więcej informacji na temat atrybutów zestawu, zobacz [atrybuty](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Aby otworzyć to okno dialogowe, wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **aplikacji** kartę. Na **aplikacji** kliknij **informacje o zestawie** przycisku.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Tytuł**  
 Określa tytuł manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Opis**  
 Określa opcjonalny opis do manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Firmy**  
 Określa nazwę firmy na potrzeby manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Produkt**  
 Określa nazwę produktu do manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Określa informacje o prawach autorskich do manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Znak towarowy**  
 Określa znakiem towarowym firmy do manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Wersja zestawu**  
 Określa numer wersji zestawu. Odnosi się do <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Wersja pliku**  
 Określa numer wersji, która instruuje kompilator, aby użyć określonej wersji dla zasobu wersji pliku systemu Win32. Odnosi się do <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Unikatowy identyfikator GUID, który identyfikuje zestaw. Podczas tworzenia projektu Visual Studio generuje identyfikator GUID dla zestawu. Odnosi się do <xref:System.Guid>.  
  
 **Język neutralny**  
 Określa, które kultury obsługuje zestawu. Odnosi się do <xref:System.Resources.NeutralResourcesLanguageAttribute>. Wartość domyślna to **(Brak)**.  
  
 **Wprowadź zestawu widoczne dla modelu COM**  
 Określa, czy typy w zestawie będzie dostępna dla modelu COM. Odnosi się do <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>Zobacz też  
 [Strona aplikacji, Projektant projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Atrybuty](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)

---
title: Informacje o zestawie — Okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c5420839d97fb62797d0f739ce62da4d14b340b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744885"
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe
**Informacje o zestawie** okno dialogowe służy do określania wartości atrybutów globalnej .NET Framework, które są przechowywane w pliku AssemblyInfo tworzone automatycznie w projekcie. W **Eksploratora rozwiązań**, plik znajduje się w **mój projekt** w węźle [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (kliknij **Pokaż wszystkie pliki** do jego wyświetlania); znajduje się w obszarze  **Właściwości** w [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Aby uzyskać więcej informacji na temat atrybutów zestawu, zobacz [atrybuty](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Aby otworzyć to okno dialogowe, wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **aplikacji** kartę. Na **aplikacji** kliknij **informacje o zestawie** przycisku.

## <a name="uielement-list"></a>Lista elementów UI
 **Tytuł** Określa tytuł manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTitleAttribute>.

 **Opis** określa opcjonalny opis do manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyDescriptionAttribute>.

 **Firma** Określa nazwę firmy na potrzeby manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCompanyAttribute>.

 **Produkt** Określa nazwę produktu do manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyProductAttribute>.

 **O prawach autorskich** określa informacje o prawach autorskich do manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCopyrightAttribute>.

 **Znak towarowy** określa znakiem towarowym firmy do manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTrademarkAttribute>.

 **Wersja zestawu** Określa wersję zestawu. Odnosi się do <xref:System.Reflection.AssemblyVersionAttribute>.

 **Wersja pliku** Określa numer wersji, która instruuje kompilator, aby użyć określonej wersji dla zasobu wersji pliku systemu Win32. Odnosi się do <xref:System.Reflection.AssemblyFileVersionAttribute>.

 **Identyfikator GUID** Unikatowy identyfikator GUID, który identyfikuje zestaw. Podczas tworzenia projektu Visual Studio generuje identyfikator GUID dla zestawu. Odnosi się do <xref:System.Guid>.

 **Niezależny od języka** Określa, które obsługuje zestaw kultury. Odnosi się do <xref:System.Resources.NeutralResourcesLanguageAttribute>. Wartość domyślna to **(Brak)** .

 **Wprowadź zestawu widoczne dla modelu COM** Określa, czy typy w zestawie będzie dostępna dla modelu COM. Odnosi się do <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

## <a name="see-also"></a>Zobacz też

- [Strona aplikacji, Projektant projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atrybuty](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
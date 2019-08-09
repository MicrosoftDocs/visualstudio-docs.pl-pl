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
ms.openlocfilehash: c36fbacfde97eb42b1feab3e9097a731437cce4e
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68870766"
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe

Okno dialogowe informacje o zestawie służy do określania wartości .NET Framework globalnych atrybutów zestawu, które są przechowywane w pliku AssemblyInfo tworzonym automatycznie przy użyciu projektu. W Eksplorator rozwiązań, plik AssemblyInfo znajduje się w węźle **My Project** dla Visual Basic projektów (kliknij przycisk **Pokaż wszystkie pliki** , aby go wyświetlić). W C# przypadku projektów znajduje się ona w obszarze **Właściwości**. Aby uzyskać więcej informacji, zobacz [atrybutyC#()](/dotnet/csharp/programming-guide/concepts/attributes/index).

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** wybierz polecenie **Właściwości**. Na stronie **aplikacja** wybierz przycisk **Informacje o zestawie** .

## <a name="uielement-list"></a>Lista elementów UIElement

**Tytuły**\
Określa tytuł manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyTitleAttribute>do.

**Zharmonizowan**\
Określa opcjonalny opis manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyDescriptionAttribute>do.

**Przedsiębiorstwo**\
Określa nazwę firmy dla manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyCompanyAttribute>do.

Możesz ustawić lub zmienić wartość domyślną dla firmy w rejestrze. Wyszukaj wartość **RegisteredOrganization** w obszarze **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** lub **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** klucz, w zależności od używanej wersji systemu Windows.

**Iloczyn**\
Określa nazwę produktu dla manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyProductAttribute>do.

**Prawo**\
Określa informacje o prawach autorskich dla manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyCopyrightAttribute>do.

**Handlowych**\
Określa znak towarowy dla manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyTrademarkAttribute>do.

**Wersja zestawu**\
Określa numer wersji zestawu. Odnosi się <xref:System.Reflection.AssemblyVersionAttribute>do.

**Wersja pliku**\
Określa numer wersji, który instruuje kompilator, aby używał określonej wersji dla zasobu wersji plików Win32. Odnosi się <xref:System.Reflection.AssemblyFileVersionAttribute>do.

**IDENT**\
Unikatowy identyfikator GUID, który identyfikuje zestaw. Podczas tworzenia projektu program Visual Studio generuje identyfikator GUID dla zestawu. Odnosi się <xref:System.Guid>do.

**Język neutralny**\
Określa kulturę obsługiwaną przez zestaw. Odnosi się <xref:System.Resources.NeutralResourcesLanguageAttribute>do. Wartość domyślna to **(brak)** .

**Ustaw zestaw COM jako widoczny**\
Określa, czy typy w zestawie będą dostępne dla modelu COM. Odnosi się <xref:System.Runtime.InteropServices.ComVisibleAttribute>do.

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atrybuty](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)

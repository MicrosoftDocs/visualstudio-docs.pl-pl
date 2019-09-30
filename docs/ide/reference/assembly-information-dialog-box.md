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
ms.openlocfilehash: 411a9b1150961307a2a8ed3cdfae9842fb56701c
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71681623"
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe

Okno dialogowe informacje o zestawie służy do określania wartości .NET Framework globalnych atrybutów zestawu, które są przechowywane w pliku AssemblyInfo tworzonym automatycznie przy użyciu projektu. W Eksplorator rozwiązań, plik AssemblyInfo znajduje się w węźle **My Project** dla Visual Basic projektów (kliknij przycisk **Pokaż wszystkie pliki** , aby go wyświetlić). W C# przypadku projektów znajduje się ona w obszarze **Właściwości**. Aby uzyskać więcej informacji, zobacz [atrybutyC#()](/dotnet/csharp/programming-guide/concepts/attributes/index).

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** wybierz polecenie **Właściwości**. Na stronie **aplikacja** wybierz przycisk **Informacje o zestawie** .

## <a name="uielement-list"></a>Lista elementów UIElement

**Tytuł**\
Określa tytuł manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyTitleAttribute>do.

**Opis**\
Określa opcjonalny opis manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyDescriptionAttribute>do.

@No__t **firmy**— 1
Określa nazwę firmy dla manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyCompanyAttribute>do.

Możesz ustawić lub zmienić wartość domyślną dla firmy w rejestrze. Wyszukaj wartość **RegisteredOrganization** w obszarze **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** lub **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** klucz, w zależności od używanej wersji systemu Windows.

@No__t **produktu**— 1
Określa nazwę produktu dla manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyProductAttribute>do.

**Prawa autorskie**\
Określa informacje o prawach autorskich dla manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyCopyrightAttribute>do.

**Znak towarowy**\
Określa znak towarowy dla manifestu zestawu. Odnosi się <xref:System.Reflection.AssemblyTrademarkAttribute>do.

**Wersja zestawu**\
Określa numer wersji zestawu. Odnosi się <xref:System.Reflection.AssemblyVersionAttribute>do.

**Wersja pliku**\
Określa numer wersji, który instruuje kompilator, aby używał określonej wersji dla zasobu wersji plików Win32. Odnosi się <xref:System.Reflection.AssemblyFileVersionAttribute>do.

**IDENTYFIKATOR GUID**\
Unikatowy identyfikator GUID, który identyfikuje zestaw. Podczas tworzenia projektu program Visual Studio generuje identyfikator GUID dla zestawu. Odnosi się <xref:System.Guid>do.

@No__t **języka neutralnego**-1
Określa kulturę obsługiwaną przez zestaw. Odnosi się <xref:System.Resources.NeutralResourcesLanguageAttribute>do. Wartość domyślna to **(brak)** .

**Ustaw zestaw com jako widoczny**\
Określa, czy typy w zestawie będą dostępne dla modelu COM. Odnosi się <xref:System.Runtime.InteropServices.ComVisibleAttribute>do.

> [!NOTE]
> Aby uzyskać więcej informacji na temat ustawiania tych właściwości podczas generowania pakietu NuGet w bibliotece klas .NET Framework, zobacz [Konfigurowanie właściwości projektu dla pakietu](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atrybuty](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)

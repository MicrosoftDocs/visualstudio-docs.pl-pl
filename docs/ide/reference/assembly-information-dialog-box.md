---
title: Informacje o zestawie — Okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88d86c077cf129632c78d6266e7c8146325b78fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651904"
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe

Okno dialogowe informacje o zestawie służy do określania wartości .NET Framework globalnych atrybutów zestawu, które są przechowywane w pliku AssemblyInfo tworzonym automatycznie przy użyciu projektu. W Eksplorator rozwiązań, plik AssemblyInfo znajduje się w węźle **My Project** dla Visual Basic projektów (kliknij przycisk **Pokaż wszystkie pliki** , aby go wyświetlić). W C# przypadku projektów znajduje się ona w obszarze **Właściwości**. Aby uzyskać więcej informacji, zobacz [atrybutyC#()](/dotnet/csharp/programming-guide/concepts/attributes/index).

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** wybierz polecenie **Właściwości**. Na stronie **aplikacja** wybierz przycisk **Informacje o zestawie** .

## <a name="uielement-list"></a>Lista elementów UIElement

@No__t_1 **tytułu**
Określa tytuł manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTitleAttribute>.

@No__t_1 **opisu**
Określa opcjonalny opis manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyDescriptionAttribute>.

@No__t_1 **firmy**
Określa nazwę firmy dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCompanyAttribute>.

Możesz ustawić lub zmienić wartość domyślną dla firmy w rejestrze. Wyszukaj wartość **RegisteredOrganization** w obszarze **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** lub **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** klucz, w zależności od używanej wersji systemu Windows.

@No__t_1 **produktu**
Określa nazwę produktu dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyProductAttribute>.

**Prawa autorskie** \
Określa informacje o prawach autorskich dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCopyrightAttribute>.

**Znak towarowy** \
Określa znak towarowy dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTrademarkAttribute>.

@No__t_1 **wersji zestawu**
Określa numer wersji zestawu. Odnosi się do <xref:System.Reflection.AssemblyVersionAttribute>.

**Wersja pliku** \
Określa numer wersji, który instruuje kompilator, aby używał określonej wersji dla zasobu wersji plików Win32. Odnosi się do <xref:System.Reflection.AssemblyFileVersionAttribute>.

**Identyfikator GUID** \
Unikatowy identyfikator GUID, który identyfikuje zestaw. Podczas tworzenia projektu program Visual Studio generuje identyfikator GUID dla zestawu. Odnosi się do <xref:System.Guid>.

@No__t_1 **języka neutralnego**
Określa kulturę obsługiwaną przez zestaw. Odnosi się do <xref:System.Resources.NeutralResourcesLanguageAttribute>. Wartość domyślna to **(brak)** .

**Ustaw \ widoczny dla zestawu com**
Określa, czy typy w zestawie będą dostępne dla modelu COM. Odnosi się do <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Aby uzyskać więcej informacji na temat ustawiania tych właściwości podczas generowania pakietu NuGet w bibliotece klas .NET Framework, zobacz [Konfigurowanie właściwości projektu dla pakietu](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atrybuty](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)

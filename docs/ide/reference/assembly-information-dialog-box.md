---
title: Informacje o zestawie — Okno dialogowe
description: Dowiedz się więcej na temat okna dialogowego Informacje o zestawie i sposobu jego użycia, aby określić wartości .NET Framework globalnych atrybutów zestawu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee8738d06c0f02adb6f5e6352d2006e0133c66ef
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871343"
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe

Okno dialogowe informacje o zestawie służy do określania wartości .NET Framework globalnych atrybutów zestawu, które są przechowywane w pliku AssemblyInfo tworzonym automatycznie przy użyciu projektu. W Eksplorator rozwiązań, plik AssemblyInfo znajduje się w węźle **My Project** dla Visual Basic projektów (kliknij przycisk **Pokaż wszystkie pliki** , aby go wyświetlić). W przypadku projektów C# znajduje się ona w obszarze **Właściwości**. Aby uzyskać więcej informacji, zobacz [atrybuty (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** wybierz polecenie **Właściwości**. Na stronie **aplikacja** wybierz przycisk **Informacje o zestawie** .

## <a name="uielement-list"></a>Lista elementów UIElement

**Tytuły**\
Określa tytuł manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTitleAttribute> .

**Zharmonizowan**\
Określa opcjonalny opis manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyDescriptionAttribute> .

**Przedsiębiorstwo**\
Określa nazwę firmy dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCompanyAttribute> .

Możesz ustawić lub zmienić wartość domyślną dla firmy w rejestrze. Poszukaj wartości **RegisteredOrganization** w kluczu **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** lub **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion** , w zależności od używanej wersji systemu Windows.

**Iloczyn**\
Określa nazwę produktu dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyProductAttribute> .

**Prawo**\
Określa informacje o prawach autorskich dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCopyrightAttribute> .

**Handlowych**\
Określa znak towarowy dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTrademarkAttribute> .

**Wersja zestawu**\
Określa numer wersji zestawu. Odnosi się do <xref:System.Reflection.AssemblyVersionAttribute> .

**Wersja pliku**\
Określa numer wersji, który instruuje kompilator, aby używał określonej wersji dla zasobu wersji plików Win32. Odnosi się do <xref:System.Reflection.AssemblyFileVersionAttribute> .

**IDENT**\
Unikatowy identyfikator GUID, który identyfikuje zestaw. Podczas tworzenia projektu program Visual Studio generuje identyfikator GUID dla zestawu. Odnosi się do <xref:System.Guid> .

**Język neutralny**\
Określa kulturę obsługiwaną przez zestaw. Odnosi się do <xref:System.Resources.NeutralResourcesLanguageAttribute> . Wartość domyślna to **(brak)**.

**Ustaw zestaw COM jako widoczny**\
Określa, czy typy w zestawie będą dostępne dla modelu COM. Odnosi się do <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

> [!NOTE]
> Aby uzyskać więcej informacji na temat ustawiania tych właściwości podczas generowania pakietu NuGet w bibliotece klas .NET Framework, zobacz [Konfigurowanie właściwości projektu dla pakietu](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atrybuty](/previous-versions/z0w1kczw(v=vs.140))
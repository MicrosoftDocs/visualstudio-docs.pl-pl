---
title: Informacje o zestawie — Okno dialogowe
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
ms.openlocfilehash: ae70a2bf989b73dedc5becaac6f4b49bd0108730
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595790"
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe

Okno dialogowe Informacje o zestawie służy do określania wartości atrybutów globalnego zestawu programu .NET Framework, które są przechowywane w pliku AssemblyInfo utworzonym automatycznie za pomocą projektu. W Eksploratorze rozwiązań plik AssemblyInfo znajduje się w węźle **Mój projekt** dla projektów języka Visual Basic (kliknij przycisk **Pokaż wszystkie pliki,** aby go wyświetlić). W przypadku projektów języka C# znajduje się w obszarze **Właściwości**. Aby uzyskać więcej informacji, zobacz [Atrybuty (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie w menu **Projekt** wybierz polecenie **Właściwości**. Na stronie **Aplikacja** wybierz przycisk **Informacje o zestawie.**

## <a name="uielement-list"></a>Lista UIElement

**Tytuł**\
Określa tytuł manifestu zestawu. Odpowiada <xref:System.Reflection.AssemblyTitleAttribute>.

**Opis**\
Określa opcjonalny opis manifestu złożenia. Odpowiada <xref:System.Reflection.AssemblyDescriptionAttribute>.

**Firmy**\
Określa nazwę firmy dla manifestu zestawu. Odpowiada <xref:System.Reflection.AssemblyCompanyAttribute>.

W rejestrze można ustawić lub zmienić wartość domyślną dla firmy. Poszukaj wartości **RegisteredOrganization** pod **kluczem Komputer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** lub **Komputer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion,** w zależności od wersji systemu Windows.

**Produktu**\
Określa nazwę produktu manifestu zestawu. Odpowiada <xref:System.Reflection.AssemblyProductAttribute>.

**Prawa autorskie**\
Określa informację o prawach autorskich dla manifestu zestawu. Odpowiada <xref:System.Reflection.AssemblyCopyrightAttribute>.

**Znakiem towarowym**\
Określa znak towarowy dla manifestu zestawu. Odpowiada <xref:System.Reflection.AssemblyTrademarkAttribute>.

**Wersja montażowa**\
Określa numer wersji zestawu. Odpowiada <xref:System.Reflection.AssemblyVersionAttribute>.

**Wersja pliku**\
Określa numer wersji, który nakazuje kompilatorowi użycie określonej wersji dla zasobu wersji pliku Win32. Odpowiada <xref:System.Reflection.AssemblyFileVersionAttribute>.

**Identyfikator guid**\
Unikatowy identyfikator GUID identyfikujący zestaw. Podczas tworzenia projektu visual studio generuje identyfikator GUID dla zestawu. Odpowiada <xref:System.Guid>.

**Język neutralny**\
Określa, która kultura obsługuje zestaw. Odpowiada <xref:System.Resources.NeutralResourcesLanguageAttribute>. Wartość domyślna **to (Brak)**.

**Spraw, aby zestaw COM-Visible**\
Określa, czy typy w zestawie będą dostępne dla com. Odpowiada <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Aby uzyskać więcej informacji na temat ustawiania tych właściwości podczas generowania pakietu NuGet w bibliotece klas .NET Framework, zobacz [Konfigurowanie właściwości projektu dla pakietu](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Zobacz też

- [Strona aplikacji, Projektant projektu (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Atrybuty](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)

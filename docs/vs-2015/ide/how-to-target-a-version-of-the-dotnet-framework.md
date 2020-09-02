---
title: 'Instrukcje: docelowa wersja .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7aae21e2c959939262b88db3b90367c4860d8a74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670620"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Porady: wersja docelowa platformy .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie opisano, jak ukierunkować tworzony projekt na konkretną wersję .NET Framework i jak zmienić wersję docelową w istniejących projektach Visual Basic, Visual C# lub Visual F#.

> [!IMPORTANT]
> Aby uzyskać informacje o sposobie zmiany wersji docelowej dla projektów języka C++, zobacz [How to: Modify The Target Framework and platform zestaw narzędzi](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

 **W tym temacie**

- [Kierowanie do wersji podczas tworzenia projektu](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)

- [Zmiana wersji docelowej](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)

## <a name="targeting-a-version-when-you-create-a-project"></a><a name="bkmk_new"></a> Kierowanie do wersji podczas tworzenia projektu
 Podczas tworzenia projektu, docelowa wersja .NET Framework określa szablony, których można użyć.

> [!NOTE]
> W wersjach Express programu Visual Studio należy najpierw utworzyć projekt, a następnie zmienić element docelowy, ponieważ [Zmiana wersji docelowej](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) opisano w dalszej części tego tematu.

#### <a name="to-target-a-version-when-you-create-a-project"></a>Aby ukierunkować tworzony projekt na konkretną wersję

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

2. Na liście u góry okna dialogowego **Nowy projekt** wybierz wersję .NET Framework, do której projekt ma być przeznaczony.

    > [!NOTE]
    > Zwykle, tylko jedna wersja .NET Framework jest instalowana razem z Visual Studio. Jeśli chcesz utworzyć projekt dla innej wersji, najpierw się upewnij, że jest ona zainstalowana. Zobacz Omówienie wieloskładnikowego [programu Visual Studio](../ide/visual-studio-multi-targeting-overview.md).

3. Na liście zainstalowanych szablonów wybierz typ projektu, który chcesz utworzyć, nazwij projekt, a następnie wybierz przycisk **OK** .

     Lista szablonów pokazuje tylko projekty, które są obsługiwane przez wybraną przez użytkownika wersję .NET Framework.

## <a name="changing-the-target-version"></a><a name="bkmk_existing"></a> Zmiana wersji docelowej
 Dostosowanej wersji .NET Framework można zmienić w projekcie Visual Basic, Visual C# lub Visual F#, wykonując czynności opisane w poniższej procedurze.

#### <a name="to-change-the-targeted-version"></a>Aby zmienić wersję docelową

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, który chcesz zmienić, a następnie wybierz polecenie **Właściwości**.

     ![Właściwości Eksplorator rozwiązań programu Visual Studio](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")

    > [!IMPORTANT]
    > Aby uzyskać informacje o sposobie zmiany wersji docelowej dla projektów języka C++, zobacz [How to: Modify The Target Framework and platform zestaw narzędzi](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

2. W lewej kolumnie okna właściwości wybierz kartę **aplikacja** .

     ![Karta aplikacji dla właściwości aplikacji Visual Studio](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Po utworzeniu aplikacji ze sklepu Windows nie można zmienić wersji dostosowanej systemu Windows ani .NET Framework.

3. Z listy **platforma docelowa** wybierz żądaną wersję.

4. W wyświetlonym oknie dialogowym weryfikacji wybierz przycisk **tak** .

     Projekt zostaje wyładowany Gdy się ponownie ładuje, jest ukierunkowany na wybraną wersję .NET Framework.

    > [!NOTE]
    > Jeśli kod zawiera odwołania do innej wersji platformy .NET Framework niż docelowa, podczas kompilacji lub uruchamiania kodu mogą się pojawić komunikaty o błędach. Aby usunąć te błędy, należy zmodyfikować odwołania. Zobacz [Rozwiązywanie problemów .NET Framework określania błędów](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Zobacz też
 [Omówienie wielu elementów docelowych programu Visual Studio](../ide/visual-studio-multi-targeting-overview.md) [.NET Framework wiele obiektów docelowych dla projektów sieci Web ASP.NET](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) [Rozwiązywanie problemów .NET Framework z błędami docelowymi](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md) [strony aplikacji, Strona aplikacji Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) [, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [Konfigurowanie projektów](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526) [jak modyfikować platformę docelową i zestaw narzędzi platformy](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)

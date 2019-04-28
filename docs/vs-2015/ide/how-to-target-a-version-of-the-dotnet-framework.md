---
title: 'Instrukcje: Docelowa wersja systemu .NET Framework | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a815a7ee13b415220c41189b6b060d893e8ef8e8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435140"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Instrukcje: Docelowa wersja systemu .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym dokumencie opisano, jak ukierunkować tworzony projekt na konkretną wersję .NET Framework i jak zmienić wersję docelową w istniejących projektach Visual Basic, Visual C# lub Visual F#.  
  
> [!IMPORTANT]
> Aby uzyskać informacje o zmienianiu docelowej wersji dla projektów w języku C++, zobacz [jak: Modyfikowanie platformy docelowej i zestawu narzędzi platformy](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
 **W tym temacie**  
  
- [Przeznaczone dla wersji, podczas tworzenia projektu](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
- [Zmiana wersji docelowej](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
## <a name="bkmk_new"></a> Przeznaczone dla wersji, podczas tworzenia projektu  
 Podczas tworzenia projektu, docelowa wersja .NET Framework określa szablony, których można użyć.  
  
> [!NOTE]
> W wersjach Express programu Visual Studio, należy najpierw utworzyć projekt najpierw, a następnie zmienić docelową, jako [zmiana wersji docelowej](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) opisano w dalszej części tego tematu.  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>Aby ukierunkować tworzony projekt na konkretną wersję  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. Na liście u góry **nowy projekt** okno dialogowe, wybierz wersję programu .NET Framework, dla której projekt do obiektu docelowego.  
  
    > [!NOTE]
    > Zwykle, tylko jedna wersja .NET Framework jest instalowana razem z Visual Studio. Jeśli chcesz utworzyć projekt dla innej wersji, najpierw się upewnij, że jest ona zainstalowana. Zobacz [programu Visual Studio Wielowersyjnością kodu – Przegląd](../ide/visual-studio-multi-targeting-overview.md).  
  
3. Na liście zainstalowanych szablonów wybierz typ projektu, który chcesz utworzyć, nadaj projektowi nazwę, a następnie wybierz **OK** przycisku.  
  
     Lista szablonów pokazuje tylko projekty, które są obsługiwane przez wybraną przez użytkownika wersję .NET Framework.  
  
## <a name="bkmk_existing"></a> Zmiana wersji docelowej  
 Można zmienić wersję docelową .NET Framework w języku Visual Basic, Visual C#, lub Visual F# projekt, korzystając z następującej procedury.  
  
#### <a name="to-change-the-targeted-version"></a>Aby zmienić wersję docelową  
  
1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz zmienić, a następnie wybierz **właściwości**.  
  
     ![Visual Studio Solution Explorer Properties](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    > Aby uzyskać informacje o zmienianiu docelowej wersji dla projektów w języku C++, zobacz [jak: Modyfikowanie platformy docelowej i zestawu narzędzi platformy](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
2. W lewej kolumnie okna właściwości wybierz **aplikacji** kartę.  
  
     ![Visual Studio właściwości aplikacji kartę](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    > Po utworzeniu aplikacji Windows Store, nie można zmienić wersję docelową .NET Framework lub Windows.  
  
3. W **platformę docelową** wybierz wersję, która ma.  
  
4. W oknie dialogowym weryfikacji wybierz **tak** przycisku.  
  
     Projekt zostaje wyładowany Gdy się ponownie ładuje, jest ukierunkowany na wybraną wersję .NET Framework.  
  
    > [!NOTE]
    > Jeśli kod zawiera odwołania do innej wersji platformy .NET Framework niż docelowa, podczas kompilacji lub uruchamiania kodu mogą się pojawić komunikaty o błędach. Aby usunąć te błędy, należy zmodyfikować odwołania. Zobacz [Rozwiązywanie problemów z błędami obiektów docelowych w programie .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Program Visual Studio Wielowersyjnością kodu – Przegląd](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET framework Wielowersyjność kodu dla projektów sieci Web platformy ASP.NET](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Rozwiązywanie problemów z błędami obiektów docelowych w programie .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Konfigurowanie projektów](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Instrukcje: modyfikowanie platformy docelowej i zestawu narzędzi platformy](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)

---
title: Docelowa wersja .NET Framework
ms.date: 02/06/2018
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc8a808ba3a5da46b4dbe3be3aa00921ea869cb6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954091"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Instrukcje: Określanie wersji docelowej programu .NET Framework

W tym dokumencie opisano, jak odwoływać się do wersji programu .NET Framework, po utworzeniu projektu i jak zmienić wersję docelową w istniejących projektach Visual Basic, C#, lub Visual F# projektu.

> [!IMPORTANT]
> Aby uzyskać informacje o zmienianiu docelowej wersji dla projektów w języku C++, zobacz [jak: Modyfikowanie docelowego framework i zestaw narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="to-target-a-version-when-you-create-a-project"></a>Aby ukierunkować tworzony projekt na konkretną wersję

Podczas tworzenia projektu dostępne wersje programu .NET Framework są zależne od które wersje są zainstalowane, a następnie wybrany szablon w **nowy projekt** okno dialogowe.

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

1. Na liście zainstalowanych szablonów wybierz typ projektu, który chcesz utworzyć, a następnie wprowadź nazwę dla projektu.

1. Z **Framework** listy rozwijanej w dolnej części **nowy projekt** okno dialogowe, wybierz wersję programu .NET Framework, dla której projekt do obiektu docelowego.

    Lista platform pokazuje tylko wersje, które mają zastosowanie do szablonu, która została wybrana. Niektórych typach projektów, takich jak .NET Core, nie wymagają .NET Framework. W takich przypadkach **Framework** listy rozwijanej jest ukryty.

    ![W ramach listy rozwijanej w oknie dialogowym Nowy projekt](media/vside-newproject-framework.png)

1. Wybierz **OK** przycisku.

## <a name="to-change-the-targeted-version"></a>Aby zmienić wersję docelową

Można zmienić wersję docelową .NET Framework w języku Visual Basic, C#, lub Visual F# projekt, korzystając z następującej procedury.

Aby uzyskać informacje o zmienianiu docelowej wersji dla projektów w języku C++, zobacz [jak: Modyfikowanie docelowego framework i zestaw narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz zmienić, a następnie wybierz **właściwości**.

    ![Właściwości Eksploratora rozwiązania programu Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. W lewej kolumnie **właściwości** oknie Wybierz **aplikacji** kartę.

    ![Karta usługi Visual Studio właściwości aplikacji](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Po utworzeniu aplikacji platformy uniwersalnej systemu Windows, nie można zmienić wersję docelową .NET Framework lub Windows.

1. W **platformę docelową** wybierz wersję, która ma.

1. W oknie dialogowym weryfikacji wybierz **tak** przycisku.

    Projekt zostaje wyładowany Gdy się ponownie ładuje, jest ukierunkowany na wybraną wersję .NET Framework.

    > [!NOTE]
    > Jeśli kod zawiera odwołania do innej wersji platformy .NET Framework niż docelowa, podczas kompilacji lub uruchamiania kodu mogą się pojawić komunikaty o błędach. Aby usunąć te błędy, należy zmodyfikować odwołania. Zobacz [Framework .NET Rozwiązywanie problemów z błędami obiektów docelowych](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Zobacz także

- [Visual Studio wielowersyjnością kodu — Przegląd](../ide/visual-studio-multi-targeting-overview.md)
- [Rozwiązywanie problemów z błędami obiektów docelowych w .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Instrukcje: Modyfikowanie docelowego framework i zestaw narzędzi platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
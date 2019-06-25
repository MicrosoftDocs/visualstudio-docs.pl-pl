---
title: Docelowa wersja platformy .NET
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET [Visual Studio]
- .NET version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c316610fc007e3e8642567c01a5172feb461bda
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747119"
---
# <a name="how-to-target-a-version-of-net"></a>Instrukcje: Docelowa wersja programu .NET

W tym artykule opisano, jak pod kątem określonej wersji programu .NET Framework, po utworzeniu projektu .NET Framework. Opisano również, jak zmienić wersję docelową w istniejących projektach Visual Basic, C#, lub F# projektu.

> [!IMPORTANT]
> Aby uzyskać informacje o zmienianiu docelowej wersji dla projektów w języku C++, zobacz [jak: Modyfikowanie docelowego framework i zestaw narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Określanie wersji docelowej po utworzeniu projektu

Kiedy tworzysz projekt programu .NET Framework, na które wersje są zainstalowane i szablonu wybranego projektu zależą od dostępnych wersji oprogramowania .NET Framework.

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

1. Wybierz szablon .NET Framework dla typu projektu, który chcesz utworzyć.

1. Z **Framework** listy rozwijanej w dolnej części okna dialogowego Wybierz wersję programu .NET Framework, dla której projekt do obiektu docelowego.

   Lista platform pokazuje tylko wersje, które mają zastosowanie do szablonu, która została wybrana.

   > [!NOTE]
   > Niektórych typach projektów, takich jak .NET Core, nie są wyświetlane **Framework** listy rozwijanej.

   ::: moniker range="vs-2017"

   ![W ramach listy rozwijanej w oknie dialogowym Nowy projekt programu Visual Studio 2017](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Selektor Framework w 2019 programu VS](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Kontynuuj [Tworzenie projektu](create-new-project.md).

## <a name="change-the-targeted-version"></a>Zmiana wersji docelowej

Można zmienić wersję docelową .NET w języku Visual Basic, C#, lub F# projekt, korzystając z następującej procedury.

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz zmienić, a następnie wybierz **właściwości**.

    ![Właściwości Eksploratora rozwiązania programu Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. W lewej kolumnie **właściwości** oknie Wybierz **aplikacji** kartę.

    ![Karta usługi Visual Studio właściwości aplikacji](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Po utworzeniu aplikacji platformy uniwersalnej systemu Windows, nie można zmienić wersji docelowej systemu Windows lub .NET.

1. W **platformę docelową** wybierz wersję, która ma.

1. W oknie dialogowym weryfikacji wybierz **tak** przycisku.

    Projekt zostaje wyładowany Gdy się ponownie ładuje, jest przeznaczona dla wersji programu .NET, która została wybrana.

    > [!NOTE]
    > Jeśli kod zawiera odwołania do innej wersji platformy .NET niż ta, którą namierzyłeś, komunikaty o błędach może pojawić się podczas kompilacji lub uruchamiania kodu. Aby usunąć te błędy, należy zmodyfikować odwołania. Zobacz [Rozwiązywanie problemów z błędami obiektów docelowych platformy .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Zobacz także

- [Framework celem — omówienie](../ide/visual-studio-multi-targeting-overview.md)
- [Rozwiązywanie problemów z błędami obiektów docelowych w .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Instrukcje: Modyfikowanie docelowego framework i zestaw narzędzi platformy (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)
---
title: Docelowa wersja .NET Framework
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8bdcade321c3660e89ab6b7cf6e0b79471b393
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548666"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Instrukcje: Określanie wersji docelowej programu .NET Framework

W tym artykule opisano, jak można odwoływać się do wersji programu .NET Framework podczas tworzenia projektu. Opisano również, jak zmienić wersję docelową w istniejących projektach Visual Basic, C#, lub F# projektu.

> [!IMPORTANT]
> Aby uzyskać informacje o zmienianiu docelowej wersji dla projektów w języku C++, zobacz [jak: Modyfikowanie docelowego framework i zestaw narzędzi platformy](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Określanie wersji docelowej po utworzeniu projektu

Podczas tworzenia projektu, zależą od dostępne wersje programu .NET Framework, na które wersje są zainstalowane i szablonu wybranego projektu.

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

1. Wybierz szablon dla typu projektu, który chcesz utworzyć. Wprowadź nazwę dla projektu.

1. Z **Framework** listy rozwijanej w dolnej części okna dialogowego Wybierz wersję programu .NET Framework, dla której projekt do obiektu docelowego.

   Lista platform pokazuje tylko wersje, które mają zastosowanie do szablonu, która została wybrana. Niektórych typach projektów, takich jak .NET Core, nie wymagają .NET Framework. W takich przypadkach **Framework** listy rozwijanej jest ukryty.

   ::: moniker range="vs-2017"

   ![W ramach listy rozwijanej w oknie dialogowym Nowy projekt](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Selektor Framework w 2019 programu VS](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Kontynuuj [Tworzenie projektu](create-new-project.md).

## <a name="change-the-targeted-version"></a>Zmiana wersji docelowej

Można zmienić wersję docelową .NET Framework w języku Visual Basic, C#, lub F# projekt, korzystając z następującej procedury.

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
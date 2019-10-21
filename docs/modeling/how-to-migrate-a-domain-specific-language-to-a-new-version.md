---
title: 'Porady: migracja języka specyficznego dla domeny do nowej wersji'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9678bf0c98774a504f17e9ea74197f82d9ba7ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605372"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Porady: migracja języka specyficznego dla domeny do nowej wersji
Można migrować projekty, które definiują i używają języka specyficznego dla domeny do [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] z wersji [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dystrybuowanej za pomocą [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Narzędzie migracji jest dostępne jako część [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Narzędzie konwertuje projekty i rozwiązania programu Visual Studio, które używają lub definiują narzędzia DSL.

 Narzędzie migracji należy uruchomić jawnie: nie jest uruchamiane automatycznie podczas otwierania rozwiązania w programie Visual Studio. Informacje na temat narzędzia i szczegółowe wskazówki można znaleźć w tej ścieżce:

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Przed przeprowadzeniem migracji projektów DSL
 Narzędzie migracji modyfikuje pliki projektu programu Visual Studio ( **. csproj**) i pliki rozwiązań ( **. sln**).

#### <a name="to-prepare-projects-for-migration"></a>Aby przygotować projekty do migracji.

- Upewnij się, że pliki **. csproj** i **. sln** mogą być zapisywane. Jeśli znajdują się pod kontrolą źródła, upewnij się, że są wyewidencjonowane.

- Utwórz kopię folderów, które mają zostać zmigrowane.

## <a name="migrating-a-collection-of-projects"></a>Migrowanie kolekcji projektów

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Aby migrować projekty i rozwiązania DSL do programu Visual Studio 2010

1. Uruchom narzędzie migracji DSL.

   - Możesz kliknąć dwukrotnie narzędzie w Eksploratorze Windows (lub Eksploratorze plików) lub uruchomić narzędzie z wiersza polecenia. To narzędzie znajduje się w tej lokalizacji:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Wybierz folder, który zawiera rozwiązania i projekty, które chcesz przekonwertować.

   - Wprowadź ścieżkę w polu u góry narzędzia, lub kliknij przycisk **Przeglądaj**.

     Narzędzie migracji Wyświetla drzewo projektów, które definiują lub używają językami DSL. Drzewo zawiera wszystkie projekty, które używają zestawów **Microsoft. VisualStudio. Modeling. SDK** lub **TextTemplating** .

3. Przejrzyj Drzewo projektów i usuń zaznaczenie projektów, które nie mają być konwertowane.

   - Wybierz projekt lub rozwiązanie, aby wyświetlić listę zmian wprowadzonych przez narzędzie.

       > [!NOTE]
       > Pola wyboru, które pojawiają się obok nazw folderów, nie mają żadnego wpływu. Należy rozwinąć foldery, aby sprawdzić projekty i rozwiązania.

4. Przekonwertuj projekty.

   1. Kliknij przycisk **Konwertuj**.

        Przed konwersją każdego pliku projektu kopia _projektu_ **. csproj** jest zapisywana jako _Project_ **. vs2008. csproj**

        Kopia każdego _rozwiązania_ **. sln** jest zapisywana jako _rozwiązanie_ **. vs2008. sln**

   2. Zbadaj wszystkie zgłoszone konwersje zakończone niepowodzeniem.

        Błędy są raportowane w oknie tekstowym. Ponadto widok drzewa przedstawia czerwoną flagę dla każdego węzła, którego konwersja nie powiodła się. Możesz kliknąć ten węzeł, aby uzyskać więcej informacji o tym błędzie.

5. **Przekształć wszystkie szablony** w rozwiązaniach zawierających pomyślnie przekonwertowane projekty.

   1. Otwórz rozwiązanie.

   2. Kliknij przycisk **Przekształć wszystkie szablony** w nagłówku Eksplorator rozwiązań.

       > [!NOTE]
       > Ten krok może być niezbędny. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować transformację wszystkie szablony](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Aktualizowanie niestandardowego kodu w przekonwertowanych projektach.

   - Spróbuj skompilować projekty i zbadać wszystkie błędy.

   - Przetestuj projektanta.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też

- [Powiązane wpisy w blogu](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
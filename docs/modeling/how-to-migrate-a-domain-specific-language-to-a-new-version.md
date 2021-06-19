---
title: 'How to: Migrate a Domain-Specific Language project (3.03.2017: migrowanie projektu języka Domain-Specific'
description: Zawiera informacje na temat sposobu migrowania projektu języka specyficznego dla domeny do najnowszej wersji programu Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 8119f465e32d3754dc446524286e0a2c12dedc40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387193"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Porady: migracja języka specyficznego dla domeny do nowej wersji
Można migrować projekty, które definiują język specyficzny dla domeny i używają go do programu , z wersji [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] programu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dystrybuowanej za pomocą programu [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 Narzędzie do migracji jest udostępniane w ramach usługi [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . Narzędzie konwertuje projekty Visual Studio rozwiązania, które używają lub definiują narzędzia DSL.

 Narzędzie migracji należy uruchomić jawnie: nie jest ono uruchamiane automatycznie po otwarciu rozwiązania w Visual Studio. Narzędzie i szczegółowy dokument ze wskazówkami można znaleźć w tej ścieżce:

 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Przed migracją projektów DSL
 Narzędzie do migracji modyfikuje pliki Visual Studio projektu **(csproj)** i pliki rozwiązań **(sln).**

#### <a name="to-prepare-projects-for-migration"></a>Aby przygotować projekty do migracji.

- Upewnij się, że można zapisywać pliki **csproj** i **sln.** Jeśli są one pod kontrolą źródła, upewnij się, że zostały wyewidencjonowane.

- Zrób kopię folderów, które mają być migrowane.

## <a name="migrating-a-collection-of-projects"></a>Migrowanie kolekcji projektów

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Aby przeprowadzić migrację projektów DSL i rozwiązań do Visual Studio 2010

1. Uruchom narzędzie migracji DSL.

   - Możesz kliknąć dwukrotnie narzędzie w Eksplorator Windows (lub Eksplorator plików) lub uruchomić narzędzie z wiersza polecenia. Narzędzie znajduje się w tej lokalizacji:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Wybierz folder zawierający rozwiązania i projekty, które chcesz przekonwertować.

   - Wprowadź ścieżkę w polu w górnej części narzędzia lub kliknij przycisk **Przeglądaj.**

     Narzędzie do migracji wyświetla drzewo projektów, które definiują lub używają plików DSL. Drzewo zawiera każdy projekt, który używa zestawów **Microsoft.VisualStudio.Modeling.Sdk** **lub TextTemplating.**

3. Przejrzyj drzewo projektów i usuń zaznaczenie projektów, których nie chcesz konwertować.

   - Wybierz projekt lub rozwiązanie, aby wyświetlić listę zmian wprowadzonych przez narzędzie.

       > [!NOTE]
       > Pola wyboru wyświetlane obok nazw folderów nie mają żadnego efektu. Należy rozwinąć foldery, aby sprawdzić projekty i rozwiązania.

4. Przekonwertuj projekty.

   1. Kliknij przycisk **Konwertuj**.

        Przed konwersją każdego pliku projektu kopia pliku **csproj** projektu jest zapisywana jako _projekt_**.vs2008.csproj**

        Kopia pliku **sln każdego** rozwiązania jest zapisywana jako _rozwiązanie_**.vs2008.sln**

   2. Zbadaj wszystkie zgłoszone konwersje, które zakończyły się niepowodzeniem.

        Błędy są zgłaszane w oknie tekstowym. Ponadto widok drzewa pokazuje czerwoną flagę w każdym węźle, który nie może przekonwertować. Możesz kliknąć węzeł, aby uzyskać więcej informacji na temat tego błędu.

5. **Przekształć wszystkie** szablony w rozwiązaniach zawierających pomyślnie przekonwertowane projekty.

   1. Otwórz rozwiązanie.

   2. Kliknij przycisk **Przekształć wszystkie** szablony w nagłówku Eksplorator rozwiązań.

       > [!NOTE]
       > Ten krok można zbędć. Aby uzyskać więcej informacji, zobacz How to Automate Transform All Templates (Jak [zautomatyzować przekształcanie wszystkich szablonów).](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))

6. Zaktualizuj kod niestandardowy w przekonwertowanych projektach.

   - Spróbuj skompilować projekty i zbadać wszelkie błędy.

   - Przetestuj projektanta.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też

- [Powiązane wpisy w blogu](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
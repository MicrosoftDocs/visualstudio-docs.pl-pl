---
title: 'Instrukcje: Migrowanie języka specyficznego dla domeny do nowej wersji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45f7b38f7dbb6ea470b2d9e186dc8e6bf4b33b1e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657327"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Porady: migracja języka specyficznego dla domeny do nowej wersji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można migrować projekty, które definiują i używają języka specyficznego dla domeny do [!INCLUDE[vs2010](../includes/vs2010-md.md)] z wersji [!INCLUDE[dsl](../includes/dsl-md.md)] dystrybuowanej za pomocą [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 Narzędzie migracji jest dostępne jako część [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]. Narzędzie konwertuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekty i rozwiązania, które używają lub definiują narzędzia DSL.

 Narzędzie migracji należy uruchomić jawnie: nie jest uruchamiane automatycznie podczas otwierania rozwiązania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Informacje na temat narzędzia i szczegółowe wskazówki można znaleźć w tej ścieżce:

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Przed przeprowadzeniem migracji projektów DSL
 Narzędzie migracji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modyfikuje pliki projektu (**csproj**) i pliki rozwiązań ( **. sln**).

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
       > Ten krok może być niezbędny. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować transformację wszystkie szablony](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6. Aktualizowanie niestandardowego kodu w przekonwertowanych projektach.

   - Spróbuj skompilować projekty i zbadać wszystkie błędy.

   - Przetestuj projektanta.

## <a name="see-also"></a>Zobacz też
 [Nowości dotyczące wizualizacji i modelowania SDK](../misc/what-s-new-in-visualization-and-modeling-sdk.md)

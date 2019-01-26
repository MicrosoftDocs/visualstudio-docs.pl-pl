---
title: 'Instrukcje: Migracja języka specyficznego dla domeny do nowej wersji'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: c2ff1a820e5ac8492b627ac61ddfa234c71b5890
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932340"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Instrukcje: Migracja języka specyficznego dla domeny do nowej wersji
Projekty definiowanie i korzystanie z języka specyficznego dla domeny, które można migrować [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] z wersji [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] który zostało rozpowszechniać za pomocą [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Narzędzie migracji jest dostarczana jako część [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. Narzędzie konwertuje projektów programu Visual Studio i rozwiązania, które używane lub zdefiniować narzędzia DSL.

 Należy uruchomić narzędzie do migracji jawnie: go nie został uruchomiony automatycznie po otwarciu rozwiązania w programie Visual Studio. Narzędzia i główny dokument zawierający szczegółowe wskazówki można znaleźć w tej ścieżce:

 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Przed przeprowadzeniem migracji projektów języka DSL
 Narzędzie migracji modyfikuje pliki projektu programu Visual Studio (**.csproj**) i pliki rozwiązania (**.sln**).

#### <a name="to-prepare-projects-for-migration"></a>Aby przygotować projekty do migracji.

-   Upewnij się, że **.csproj** i **.sln** można zapisywać pliki. Jeśli znajdują się pod kontrolą źródła, upewnij się, że ich są wyewidencjonowane.

-   Utwórz kopię foldery, które zamierzasz migrować.

## <a name="migrating-a-collection-of-projects"></a>Migrowanie kolekcji projektów

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Aby przeprowadzić migrację DSL projekty i rozwiązania Visual Studio 2010

1. Uruchom narzędzie do migracji DSL.

   -   Kliknij dwukrotnie narzędzie w Eksploratorze Windows (lub Eksploratora plików) lub uruchomić narzędzie z wiersza polecenia. Narzędzie znajduje się w tej lokalizacji:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Wybierz folder, który zawiera rozwiązania i projekty, które chcesz przekonwertować.

   - Wprowadź ścieżkę, w polu u góry strony, narzędzia, lub kliknij przycisk **Przeglądaj**.

     Narzędzie migracji wyświetli drzewa projektów, które zdefiniować lub używać języków DSL. Drzewo obejmuje każdego projektu, który używa **Microsoft.VisualStudio.Modeling.Sdk** lub **texttemplating jest** zestawów.

3. Przegląd drzewa projektów i usuń zaznaczenie pola wyboru projektów, których nie chcesz konwertować.

   -   Wybierz projekt lub rozwiązanie, aby wyświetlić listę zmian, które spowoduje, że narzędzie.

       > [!NOTE]
       >  Pola wyboru, które pojawiają się obok nazwy folderów nie mają wpływu. Należy rozwinąć foldery, aby sprawdzić, projekty i rozwiązania.

4. Konwertowanie projektów.

   1.  Kliknij przycisk **przekonwertować**.

        Zanim każdy plik projektu jest konwertowany, kopię _projektu_**.csproj** zostanie zapisany jako _projektu_**. vs2008.csproj**

        Kopia każdego _rozwiązania_**.sln** zostanie zapisany jako _rozwiązania_**. vs2008.sln**

   2.  Badanie zakończone niepowodzeniem konwersje, które są zgłaszane.

        Błędy są zgłaszane w oknie tekstowym. Ponadto widok drzewa pokazuje czerwona flaga w każdym węźle, w której nie można przekonwertować. Możesz kliknąć węzeł, aby uzyskać więcej informacji na temat tego błędu.

5. **Transformuj wszystkie szablony** rozwiązania zawierającego pomyślnie przekonwertowany projektów.

   1.  Otwórz rozwiązanie.

   2.  Kliknij przycisk **Przekształć wszystkie szablony** przycisku w nagłówku Eksploratora rozwiązań.

       > [!NOTE]
       >  Ten krok można wprowadzić niepotrzebne. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować Przekształć wszystkie szablony](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Zaktualizuj niestandardowy kod w projektach przekonwertowana.

   -   Spróbuj kompilować projekty i zbadać wszelkie błędy.

   -   Przetestuj projektanta.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Zobacz też

- [Wpisy w blogu pokrewne](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
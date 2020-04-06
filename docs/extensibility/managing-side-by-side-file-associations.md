---
title: Zarządzanie skojarzeniami plików side-by-side | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702762"
---
# <a name="manage-side-by-side-file-associations"></a>Zarządzanie skojarzeniami plików obok siebie

Jeśli vspackage udostępnia skojarzenia plików, należy zdecydować, jak obsługiwać instalacje side-by-side, w którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] określona wersja powinna być wywoływana, aby otworzyć plik. Niezgodne formaty plików potęgują problem.

Użytkownicy oczekują, że nowa wersja produktu będzie zgodna z wcześniejszymi wersjami, dzięki czemu istniejące pliki mogą być ładowane w nowej wersji bez utraty danych. W idealnym przypadku vsPackage można zarówno załadować i zapisać formaty plików z wcześniejszych wersji. Jeśli to nie prawda, należy zaoferować uaktualnienie formatu pliku do nowej wersji vsPackage. Wadą tego podejścia jest to, że uaktualniony plik nie może być otwarty we wcześniejszej wersji.

Aby uniknąć tego problemu, można zmienić rozszerzenia, gdy formaty plików staną się niezgodne. Na przykład w wersji 1 programu VSPackage można użyć rozszerzenia, *.mypkg10*, a wersja 2 może użyć rozszerzenia. *.mypkg20*. Ta różnica identyfikuje VSPackage, który otwiera określonego pliku. Jeśli dodasz nowsze pakiety VSPackages do listy programów skojarzonych ze starym rozszerzeniem, użytkownicy mogą kliknąć plik prawym przyciskiem myszy i wybrać jego otwarcie w nowszym programie VSPackage. W tym momencie vsPackage może zaoferować uaktualnienie pliku do nowego formatu lub otworzyć plik i zachować zgodność z wcześniejszymi wersjami VSPackage.

> [!NOTE]
> Można połączyć te podejścia. Na przykład można zaoferować zgodność z powrotem, ładując starszy plik i oferują uaktualnienie formatu pliku, gdy użytkownik go zapisze.

## <a name="face-the-problem"></a>Zmierz się z problemem

Jeśli chcesz, aby wiele pakietów VSPackages obok siebie używało tego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] samego rozszerzenia, musisz wybrać wersję, która jest skojarzona z rozszerzeniem. Oto dwie alternatywy:

- Otwórz plik w najnowszej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wersji zainstalowanej na komputerze użytkownika.

   W tym podejściu instalator jest odpowiedzialny za określenie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] najnowszej wersji i w tym, że we wpisie rejestru napisanym dla skojarzenia plików. W pakiecie Instalatora Windows można dołączyć akcje niestandardowe, aby ustawić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]właściwość wskazującą najnowszą wersję programu .

  > [!NOTE]
  > W tym kontekście "najnowsza" oznacza "najnowszą obsługiwana wersja". Te wpisy instalatora nie będą automatycznie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]wykrywać kolejnej wersji programu . Wpisy w [wykrywaniu wymagań systemowych](../extensibility/internals/detecting-system-requirements.md) i [w poleceniach, które muszą być uruchamiane po instalacji,](../extensibility/internals/commands-that-must-be-run-after-installation.md) są podobne do tych przedstawionych tutaj i są wymagane do obsługi dodatkowych wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   Następujące wiersze w tabeli CustomAction ustawiają właściwość DEVENV_EXE_LATEST jako właściwość ustawioną przez tabele AppSearch i RegLocator omówione w [poleceniach, które muszą być uruchamiane po instalacji](../extensibility/internals/commands-that-must-be-run-after-installation.md). Wiersze w tabeli InstallExecuteSequence zaplanować akcje niestandardowe na początku sekwencji wykonywania. Wartości w kolumnie Condition sprawiają, że logika działa:

  - Visual Studio .NET 2002 jest najnowszą wersją, jeśli jest to jedyna obecna wersja.

  - Visual Studio .NET 2003 jest najnowszą wersją tylko wtedy, gdy jest obecny i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie jest obecny.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]jest najnowszą wersją, jeśli jest to jedyna obecna wersja.

    Wynik netto jest taki, że DEVENV_EXE_LATEST zawiera ścieżkę najnowszej wersji devenv.exe.

  **Wiersze tabeli CustomAction określające najnowszą wersję programu Visual Studio**

  |Akcja|Typ|Element źródłowy|Środowisko docelowe|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Instalowanie wierszy tabeli sekwencjonowania, które określają najnowszą wersję programu Visual Studio**

  |Akcja|Warunek|Sequence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 I NIE (DEVENV_EXE_2003 LUB DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 a nie DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Właściwości DEVENV_EXE_LATEST w tabeli Rejestru pakietu Instalatora Windows można zapisać wartość domyślną **klucza HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand** ,[DEVENV_EXE_LATEST] "%1"

- Uruchom program współdzielonego uruchamiania, który może dokonać najlepszego wyboru z dostępnych wersji VSPackage.

   Twórcy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wybrali to podejście do obsługi złożonych wymagań wielu formatów rozwiązań i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]projektów, które wynikają z wielu wersji . W tym podejściu można zarejestrować program uruchamiania jako program obsługi rozszerzenia. Launcher sprawdza plik i decyduje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] która wersja i VSPackage może obsłużyć tego konkretnego pliku. Na przykład jeśli użytkownik otworzy plik, który został ostatnio zapisany przez określoną wersję vsPackage, launcher może [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]uruchomić, że VSPackage w pasującej wersji programu . Ponadto użytkownik może skonfigurować program uruchamiający, aby zawsze uruchamiał najnowszą wersję. Program uruchamiający może również monitować użytkownika o uaktualnienie formatu pliku. Jeśli format pliku zawiera numer wersji, program uruchamiający może poinformować użytkownika, jeśli format pliku pochodzi z wersji późniejszej niż jeden lub więcej zainstalowanych pakietów VSPackages.

   Program uruchamiający powinien znajdować się w składniku Instalatora Windows, który jest współużytkował wszystkie wersje programu VSPackage. Ten proces zapewnia, że najnowsza wersja jest zawsze zainstalowana i nie jest usuwana, dopóki nie zostaną odinstalowane wszystkie wersje programu VSPackage. W ten sposób skojarzenia plików i inne wpisy rejestru składnika launcher są zachowywane, nawet jeśli jedna wersja vspackage jest odinstalowany.

## <a name="uninstall-and-file-associations"></a>Odinstalowywanie i skojarzenia plików

Odinstalowanie pakietu VSPackage, który zapisuje wpisy rejestru dla skojarzeń plików, powoduje usunięcie skojarzeń plików. W związku z tym rozszerzenie nie ma skojarzonych programów. Instalator Windows nie "odzyskuje" wpisów rejestru, które zostały dodane po zainstalowaniu programu VSPackage. Oto kilka sposobów na naprawienie skojarzeń plików użytkownika:

- Użyj składnika udostępnionego uruchamiania, jak opisano wcześniej.

- Poinstruuj użytkownika, aby uruchomić naprawę wersji VSPackage, że użytkownik chce być właścicielem skojarzenia plików.

- Podaj oddzielny program wykonywalny, który przepisuje odpowiednie wpisy rejestru.

- Podaj stronę opcji konfiguracji lub okno dialogowe, które pozwala użytkownikom wybrać skojarzenia plików i odzyskać utracone skojarzenia. Poinstruuj użytkowników, aby uruchamiali go po dezinstalacji.

## <a name="see-also"></a>Zobacz też

- [Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)

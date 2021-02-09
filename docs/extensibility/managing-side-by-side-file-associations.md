---
title: Zarządzanie skojarzeniami plików Side-by-Side | Microsoft Docs
description: Jeśli pakietu VSPackage zapewnia skojarzenia plików, zdecyduj, jak obsługiwać instalacje równoległe, w których konkretna wersja programu Visual Studio otwiera plik.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 157e8b4b4d7a00845fb76e0105414879cb1f472d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924856"
---
# <a name="manage-side-by-side-file-associations"></a>Zarządzaj skojarzeniami plików obok siebie

Jeśli pakietu VSPackage udostępnia skojarzenia plików, należy zdecydować, jak obsługiwać instalacje równoległe, w których konkretna wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powinna zostać wywołana, aby otworzyć plik. Niezgodne formaty plików pozostały problem.

Użytkownicy oczekują, że nowa wersja produktu będzie zgodna ze starszymi wersjami, dzięki czemu istniejące pliki mogą zostać załadowane do nowej wersji bez utraty danych. W idealnym przypadku pakietu VSPackage może ładować i zapisywać formaty plików z wcześniejszych wersji. Jeśli to nie jest prawda, należy zastanowić się, aby uaktualnić format pliku do nowej wersji pakietu VSPackage. Minusem do tego podejścia polega na tym, że uaktualniony plik nie może zostać otwarty w starszej wersji.

Aby uniknąć tego problemu, można zmienić rozszerzenia, gdy formaty plików staną się niezgodne. Na przykład, wersja 1 pakietu VSPackage może używać rozszerzenia, *. mypkg10*, a wersja 2 może korzystać z rozszerzenia, *. mypkg20*. Ta różnica wskazuje pakietu VSPackage, który otwiera określony plik. Jeśli dodasz nowsze pakietów VSPackage do listy programów skojarzonych ze starym rozszerzeniem, użytkownicy będą mogli kliknąć plik prawym przyciskiem myszy, a następnie otworzyć go w nowszej pakietu VSPackage. W tym momencie pakietu VSPackage może oferować uaktualnienie pliku do nowego formatu lub otworzyć plik i zachować zgodność z wcześniejszymi wersjami pakietu VSPackage.

> [!NOTE]
> Te podejścia można połączyć. Można na przykład zaoferować zgodność z poprzednimi wersjami przez załadowanie starszego pliku i oferowanie uaktualnienia formatu pliku, gdy użytkownik go zapisuje.

## <a name="face-the-problem"></a>Zaczołowie problemu

Jeśli chcesz, aby wiele równoległych pakietów VSPackage używać tego samego rozszerzenia, musisz wybrać wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , która jest skojarzona z rozszerzeniem. Poniżej przedstawiono dwie alternatywy:

- Otwórz plik w najnowszej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowanej na komputerze użytkownika.

   W tym podejściu Instalator jest odpowiedzialny za określenie najnowszej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i dołączenie go do wpisu rejestru zarejestrowanego dla skojarzenia pliku. W pakiecie Instalator Windows można uwzględnić niestandardowe akcje, aby ustawić właściwość, która wskazuje najnowszą wersję programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  > [!NOTE]
  > W tym kontekście "Najnowsza" oznacza "Najnowsza obsługiwana wersja". Te wpisy Instalatora nie będą automatycznie wykrywać kolejnej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Wpisy [wykrywające wymagania systemowe](../extensibility/internals/detecting-system-requirements.md) i w [poleceniach, które muszą zostać uruchomione po instalacji](../extensibility/internals/commands-that-must-be-run-after-installation.md) , są podobne do przedstawionych tutaj i są wymagane do obsługi dodatkowych wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   Następujące wiersze w tabeli "AppSearch" mają ustawioną właściwość DEVENV_EXE_LATEST tak, aby była właściwością ustawioną przez RegLocatore tabele, które są opisane w [poleceniach, które muszą zostać uruchomione po instalacji](../extensibility/internals/commands-that-must-be-run-after-installation.md). Wiersze w tabeli InstallExecuteSequence Zaplanuj akcje niestandardowe wcześniej w sekwencji wykonywania. Wartości w kolumnie warunek sprawiają, że działanie logiki:

  - Program Visual Studio .NET 2002 to Najnowsza wersja, jeśli jest to jedyna aktualna wersja.

  - Program Visual Studio .NET 2003 to Najnowsza wersja, która jest obecna i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie jest obecna.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest to Najnowsza wersja, jeśli jest jedyną obecną wersją.

    Wynikiem jest to, że DEVENV_EXE_LATEST zawiera ścieżkę do najnowszej wersji devenv.exe.

  **Wiersze tabeli kodu, które określają najnowszą wersję programu Visual Studio**

  |Akcja|Typ|Element źródłowy|Cel|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallExecuteSequence wiersze tabeli, które określają najnowszą wersję programu Visual Studio**

  |Akcja|Warunek|Sequence|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002, A NIE (DEVENV_EXE_2003 LUB DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003, A NIE DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Możesz użyć właściwości DEVENV_EXE_LATEST w tabeli rejestru pakietu Instalator Windows, aby zapisać wartość domyślną klucza **HKEY_CLASSES_ROOT *ProgID* ShellOpenCommand** , [DEVENV_EXE_LATEST] "%1"

- Uruchom współużytkowany program do uruchamiania, który może wybrać najlepszy wybór spośród dostępnych wersji pakietu VSPackage.

   Deweloperzy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wybierają takie podejście, aby obsłużyć złożone wymagania wielu formatów rozwiązań i projektów, które wynikają z wielu wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . W ramach tego podejścia należy zarejestrować program do uruchamiania jako procedurę obsługi rozszerzenia. Usługa uruchamiania analizuje plik i decyduje, która wersja programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i pakietu VSPackage może obsłużyć ten konkretny plik. Na przykład, jeśli użytkownik otworzy plik, który był ostatnio zapisywany przez określoną wersję pakietu VSPackage, uruchomienie tego programu może spowodować, że pakietu VSPackage w zgodnej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Ponadto użytkownik może skonfigurować program uruchamiający, aby zawsze uruchomił najnowszą wersję. Moduł uruchamiający może również monitować użytkownika o uaktualnienie formatu pliku. Jeśli format pliku zawiera numer wersji, program uruchamiający może poinformować użytkownika, jeśli format pliku pochodzi z wersji nowszej niż co najmniej jeden z zainstalowanych pakietów VSPackage.

   Program uruchamiający powinien znajdować się w składniku Instalator Windows, który jest współużytkowany ze wszystkimi wersjami pakietu VSPackage. Ten proces zapewnia, że Najnowsza wersja jest zawsze zainstalowana i nie jest usuwana do momentu odinstalowania wszystkich wersji pakietu VSPackage. W ten sposób skojarzenia plików i inne wpisy rejestru składnika uruchamiania są zachowywane nawet wtedy, gdy jedna wersja pakietu VSPackage zostanie odinstalowana.

## <a name="uninstall-and-file-associations"></a>Odinstalowywanie i skojarzenia plików

Dezinstalacja pakietu VSPackage, która zapisuje wpisy rejestru dla skojarzeń plików, usuwa skojarzenia plików. W związku z tym rozszerzenie nie ma skojarzonych programów. Instalator Windows nie "Odzyskaj" wpisów rejestru, które zostały dodane podczas instalacji pakietu VSPackage. Oto kilka sposobów, aby naprawić skojarzenia plików użytkownika:

- Użyj współużytkowanego składnika uruchamiania, jak opisano wcześniej.

- Poinstruuj użytkownika, aby uruchomił naprawę wersji pakietu VSPackage, którą użytkownik chce skojarzyć z skojarzeniem pliku.

- Podaj oddzielny program wykonywalny, który ponownie zapisuje odpowiednie wpisy rejestru.

- Podaj stronę opcji konfiguracji lub okno dialogowe, które umożliwia użytkownikom wybieranie skojarzeń plików i odzyskiwanie utraconych skojarzeń. Poinstruuj użytkowników, aby uruchomili ją po odinstalowaniu.

## <a name="see-also"></a>Zobacz też

- [Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Rejestrowanie czasowników dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)

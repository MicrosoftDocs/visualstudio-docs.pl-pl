---
title: Zarządzanie skojarzenia plików Side-by-Side | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fdee9d9b3d96c97ba738d974ff9691417068121e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826945"
---
# <a name="manage-side-by-side-file-associations"></a>Zarządzaj skojarzeniami plików side-by-side
Jeśli Twoje pakietu VSPackage udostępnia skojarzenia plików, należy zdecydować, jak obsługiwać instalacje side-by-side, w którym konkretnej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] powinny być używane w celu otwarcia pliku. Niezgodnych formatów pliku złożone problem.  
  
 Użytkownicy oczekują nową wersję produktu, aby zapewnić ich zgodność z wcześniejszymi wersjami, tak, aby istniejące pliki mogą być ładowane w nowej wersji bez utraty danych. W idealnym przypadku Twojego pakietu VSPackage można zarówno obciążenia i zapisać formatów plików starszych wersji. Jeśli nie jest to wartość true, powinno oferować się uaktualnienie formatu pliku do nowej wersji usługi pakietu VSPackage. Wadą tego podejścia jest to, że uaktualniony plik nie można otworzyć w starszej wersji.  
  
 Aby uniknąć tego problemu, możesz zmienić rozszerzenia formatów plików stają się niezgodne. Na przykład użyć rozszerzenia i wersji 1 z pakietu VSPackage *.mypkg10*i w wersji 2 można użyć rozszerzenia, *.mypkg20*. Różnica ta identyfikuje pakietu VSPackage, który spowoduje otwarcie danego pliku. Jeśli dodasz nowszych pakietów VSPackage do listy programów, które są skojarzone z rozszerzeniem stare użytkowników można kliknij plik prawym przyciskiem myszy i wybierz opcję otworzyć go w nowszej pakietu VSPackage. W tym momencie Twojego pakietu VSPackage zaoferować uaktualnić go do nowego formatu lub Otwórz plik i zachować zgodność z wcześniejszymi wersjami pakietu VSPackage.  
  
> [!NOTE]
>  Można połączyć te podejścia. Można na przykład oferty zgodności z poprzednimi wersjami, ładując starszy plik i ofertę uaktualnienia format pliku, gdy użytkownik zapisuje go.  
  
## <a name="face-the-problem"></a>Problem z rozpoznawania twarzy  
 Jeśli chcesz, aby wiele VSPackages side-by-side, aby użyć tego samego rozszerzenia, należy wybrać wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] skojarzony z rozszerzeniem. Poniżej przedstawiono dwa warianty:  
  
- Otwórz plik w najnowszej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane na komputerze użytkownika.  
  
   W tym podejściu jest odpowiedzialny za sprawdzenie najnowszą wersję Instalatora [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i, w tym we wpisie rejestru napisane dla skojarzenia plików. Pakiet Instalatora Windows może zawierać akcje niestandardowe można ustawić właściwości, która wskazuje najnowszą wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
  > [!NOTE]
  >  W tym kontekście "najnowsza" oznacza "najnowszą obsługiwaną wersję." Te wpisy Instalatora nie wykryje automatycznie późniejszych wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Wpisy w [wykrywanie wymagań systemowych](../extensibility/internals/detecting-system-requirements.md) i [polecenia, musi być uruchamiania po instalacji](../extensibility/internals/commands-that-must-be-run-after-installation.md) są podobne do tych przedstawionych w tym miejscu i są wymagane do obsługi dodatkowych wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
   Następujące wiersze w tabeli Akcja niestandardowa ustaw właściwość DEVENV_EXE_LATEST, aby mieć ustawioną właściwość, AppSearch powoduje niepoprawne obcięcie oraz tabele RegLocator omówionych w [polecenia uruchamiane po zakończeniu instalacji](../extensibility/internals/commands-that-must-be-run-after-installation.md). Wiersze w tabeli InstallExecuteSequence zaplanować akcje niestandardowe wcześnie w kolejności wykonania. Wartości w upewnij kolumny stan pracy logiki:  
  
  - Visual Studio .NET 2002 jest najnowsza wersja, jeśli jest tylko bieżącej wersji.  
  
  - Visual Studio .NET 2003 jest najnowsza wersja, tylko wtedy, gdy jest obecny i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie jest obecny.  
  
  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest najnowsza wersja, jeśli jest tylko bieżącej wersji.  
  
    Wynikiem jest, że DEVENV_EXE_LATEST zawiera ścieżkę do najnowszej wersji devenv.exe.  
  
  ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Akcja niestandardowa wiersze tabeli, które określają najnowszą wersję programu Visual Studio  
  
  |Akcja|Typ|Źródło|Cel|  
  |------------|----------|------------|------------|  
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
  ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>InstallExecuteSequence wiersze tabeli, które określają najnowszą wersję programu Visual Studio  
  
  |Akcja|Warunek|Sekwencja|  
  |------------|---------------|--------------|  
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 I NOT (DEVENV_EXE_2003 LUB DEVENV_EXE_2005)|410|  
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 I NIE DEVENV_EXE_2005|420|  
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
   Właściwość DEVENV_EXE_LATEST w tabeli w rejestrze pakietu Instalatora Windows służy do zapisywania **HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand** wartości domyślnej klucza [DEVENV_EXE_LATEST] "%1"  
  
- Uruchom program uruchamiania udostępnionego, który może zgłaszać najlepszym wyborem z dostępnych wersji pakietu VSPackage.  
  
   Deweloperzy [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wybrana opcja to podejście do obsługi złożonych wymaganiach, wiele formatów rozwiązań i projektów, które są wynikiem wielu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. W przypadku tej metody należy zarejestrować program uruchamianie jako procedury obsługi rozszerzenia. Uruchom okno sprawdza plik i decyduje o wyborze wersji z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i usługi pakietu VSPackage może obsługiwać tego określonego pliku. Na przykład, jeśli użytkownik otwiera plik, który został ostatnio zapisany przez określoną wersję usługi pakietu VSPackage, Uruchom okno można uruchomić tego pakietu VSPackage w zgodnej wersji elementu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Ponadto użytkownik może skonfigurować uruchamianie można zawsze uruchomić najnowszą wersję. Uruchamianie programu można również monitowania użytkownika o uaktualnienie formatu pliku. Jeśli format pliku zawiera numer wersji, Uruchom okno może informuje użytkownika, jeśli jest w formacie pliku z wersji, która jest nowsza niż co najmniej jedną z zainstalowanych pakietów VSPackage.  
  
   Uruchom okno powinna mieć składnik Instalatora Windows, który jest udostępniany ze wszystkimi wersjami usługi pakietu VSPackage. Ten proces sprawia, że się, że najnowsza wersja będzie zawsze instalowana i nie zostanie usunięty, dopóki nie zostaną odinstalowane wszystkie wersje usługi pakietu VSPackage. W ten sposób skojarzenia plików i inne wpisy rejestru składnika uruchamiania zostaną zachowane nawet w przypadku odinstalowania jedną wersję pakietu VSPackage.  
  
## <a name="uninstall-and-file-associations"></a>Odinstaluj i skojarzenia plików  
 Odinstalowywanie pakietów VSPackage, który zapisuje wpisy rejestru dla skojarzenia plików spowoduje usunięcie skojarzenia plików. Dlatego rozszerzenie ma nie skojarzone z nim programy. Instalator Windows nie "Odzyskiwanie" wpisy rejestru, które zostały dodane po zainstalowaniu pakietu VSPackage. Poniżej przedstawiono niektóre sposoby naprawienia skojarzenia plików użytkownika:  
  
-   Użyj składnika uruchamiania udostępnionego, jak opisano wcześniej.  
  
-   Poinstruuj użytkownika, aby uruchomić naprawę wersję pakietu VSPackage, które użytkownik chce do kojarzenia plików.  
  
-   Podaj oddzielny program wykonywalny, który ponownie zapisuje wpisy rejestru odpowiednie.  
  
-   Podaj konfiguracji opcje strony lub okna dialogowego pole, które umożliwia użytkownikom wybieranie skojarzenia plików i odzyskać utracone skojarzenia. Poinstruować użytkowników, aby uruchomić go po dezinstalacji.  
  
## <a name="see-also"></a>Zobacz także  
 [Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)
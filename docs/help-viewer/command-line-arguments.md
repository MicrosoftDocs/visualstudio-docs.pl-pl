---
title: Argumenty wiersza polecenia dla Menedżera zawartości pomocy
ms.date: 11/01/2017
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9bead01c6440d5232a91a5e8fe2007b3e30340c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631979"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Argumenty wiersza polecenia dla Menedżera zawartości pomocy

Możesz określić sposób wdrażania lokalnej zawartości pomocy i zarządzania nią za pomocą argumentów wiersza polecenia dla Menedżera zawartości pomocy (*HlpCtntMgr. exe*). Należy uruchomić skrypty dla tego narzędzia wiersza polecenia z uprawnieniami administratora i nie można uruchamiać tych skryptów jako usługi. Za pomocą tego narzędzia można wykonać następujące zadania:

- Dodaj lub Aktualizuj lokalną zawartość pomocy z dysku lub z chmury.

- Usuń lokalną zawartość pomocy.

- Przenieś lokalny magazyn zawartości pomocy.

- Dodawanie, aktualizowanie, usuwanie lub przenoszenie lokalnej zawartości pomocy w trybie dyskretnym.

Składnia:

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

Na przykład:

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

>[!NOTE]
> Nazwa katalogu to VisualStudio15 zarówno dla programu Visual Studio 2017, jak i Visual Studio 2019. Może to być nieoczekiwane, ale jest to spowodowane tym, że ten sam podgląd pomocy jest używany zarówno w przypadku wersji programu Visual Studio.

## <a name="switches-and-arguments"></a>Przełączniki i argumenty

W poniższej tabeli zdefiniowano przełączniki i argumenty, których można użyć do narzędzia wiersza polecenia dla Menedżera zawartości pomocy:

|Przełącznik|Wymagany?|Argumenty|
|------------|---------------|---------------|
|/operation|Tak|-   **Install**— dodaje książki z określonego źródła instalacji do magazynu zawartości lokalnej.<br />     Ten przełącznik wymaga argumentu/booklist, argumentu/sourceURI lub obu tych wartości. Jeśli nie określisz argumentu/sourceURI, domyślny identyfikator URI programu Visual Studio jest używany jako źródło instalacji. Jeśli nie określisz argumentu/booklist, zostaną zainstalowane wszystkie książki na/sourceUri.<br />-   **Uninstall**— usuwa książki określone przez użytkownika z lokalnego magazynu zawartości.<br />     Ten przełącznik wymaga argumentu/booklist lub argumentu/sourceURI.  Jeśli określisz argument/sourceURI, wszystkie książki zostaną usunięte, a argument/booklist zostanie zignorowany.<br />-   **Move**— przenosi magazyn lokalny do określonej ścieżki. Domyślna ścieżka do lokalnego magazynu jest ustawiana jako katalog w obszarze *% ProgramData%*<br />     Ten przełącznik wymaga argumentów/locationPath i/catalogName. Komunikaty o błędach będą rejestrowane w dzienniku zdarzeń w przypadku określenia ścieżki, która jest nieprawidłowa lub jeśli dysk nie zawiera wystarczającej ilości wolnego miejsca do przechowywania zawartości.<br />-   **Refresh**--aktualizuje tematy, które uległy zmianie od czasu ich instalacji lub niedawno zaktualizowane.<br />     Ten przełącznik wymaga argumentu/sourceURI.|
|/catalogName|Tak|Określa nazwę wykazu zawartości. W przypadku programu Visual Studio 2017 i Visual Studio 2019 jest to VisualStudio15.|
|wymaganego/locale.|Nie|Określa ustawienia regionalne produktu, które są używane do wyświetlania zawartości i zarządzania nią dla bieżącego wystąpienia podglądu pomocy. Można na przykład określić `EN-US` dla Stany Zjednoczone angielskiej.<br /><br /> Jeśli nie określisz ustawień regionalnych, zostanie użyta wartość ustawienia regionalne systemu operacyjnego. Jeśli nie można określić ustawień regionalnych, `EN-US` jest używany.<br /><br /> W przypadku określenia ustawień regionalnych, które nie są prawidłowe, komunikat o błędzie jest rejestrowany w dzienniku zdarzeń.|
|/e|Nie|Podniesienie poziomu Menedżera zawartości pomocy do uprawnień administracyjnych, jeśli bieżący użytkownik ma poświadczenia administracyjne.|
|/sourceURI|Nie|Określa adres URL, z którego zainstalowano zawartość (interfejs API usługi) lub ścieżkę do pliku instalacyjnego zawartości ( *. msha*). Adres URL może wskazywać na grupę produktów (węzeł najwyższego poziomu) lub do książek produktu (węzeł poziomu liścia) w punkcie końcowym stylu programu Visual Studio 2010. Nie musisz zawierać ukośnika (/) na końcu adresu URL. Jeśli dołączysz końcowy ukośnik, będzie on odpowiednio obsługiwany.<br /><br /> Komunikat o błędzie jest rejestrowany w dzienniku zdarzeń, jeśli określisz plik, który nie został znaleziony, jest nieprawidłowy lub niedostępny lub jeśli połączenie z Internetem nie jest dostępne lub jest przerywane w trakcie zarządzania zawartością.|
|/vendor|Nie|Określa dostawcę zawartości produktu, który zostanie usunięty (na przykład `Microsoft`). Domyślnym argumentem tego przełącznika jest Microsoft.|
|/productName|Nie|Określa nazwę produktu dla ksiąg, które zostaną usunięte. Nazwa produktu jest identyfikowana w plikach *HelpContentSetup. msha* lub *Books. html* dostarczanych z zawartością. Książki można usuwać tylko z jednego produktu jednocześnie. Aby usunąć książki z wielu produktów, należy wykonać wiele instalacji.|
|/booklist|Nie|Określa nazwy książek, które mają być zarządzane, rozdzielone spacjami. Wartości muszą być zgodne z nazwami książek wymienionymi na nośniku instalacyjnym programu.<br /><br /> Jeśli ten argument nie zostanie określony, zostaną zainstalowane wszystkie zalecane książki dla określonego produktu w/sourceURI.<br /><br /> Jeśli nazwa książki zawiera jedną lub więcej spacji, należy ująć ją w podwójne cudzysłowy ("), aby lista została odpowiednio ograniczona.<br /><br /> Komunikaty o błędach będą rejestrowane w przypadku określenia/sourceURI, który jest nieprawidłowy lub nieosiągalny.|
|/skuId.|Nie|Określa jednostkę magazynową (SKU) produktu ze źródła instalacji i filtruje książki, które identyfikuje przełącznik/SourceURI.|
|/membership|Nie|-   **minimum**— instaluje minimalny zestaw zawartości pomocy w oparciu o jednostkę SKU określoną za pomocą przełącznika/skuId. Mapowanie między jednostką SKU a zestawem zawartości jest uwidocznione w interfejsie API usługi.<br />-   **zalecane**— instaluje zestaw zalecanych książek dla jednostki SKU określonej przy użyciu argumentu/skuId. Źródłem instalacji jest interfejs API usługi lub *. MSHA*.<br />-   **pełna**— instaluje cały zbiór książek dla jednostki SKU określonej przy użyciu argumentu/skuId. Źródłem instalacji jest interfejs API usługi lub *. MSHA*.|
|/locationpath|Nie|Określa folder domyślny dla lokalnej zawartości pomocy. Tego przełącznika należy używać tylko w celu instalowania lub przenoszenia zawartości. W przypadku określenia tego przełącznika należy również określić przełącznik/Silent.|
|/silent|Nie|Instaluje lub usuwa zawartość pomocy bez monitowania użytkownika ani wyświetlania żadnego interfejsu użytkownika, łącznie z ikoną w obszarze powiadomień o stanie. Dane wyjściowe są rejestrowane w pliku w katalogu *% temp%* . **Ważne:**  Aby zainstalować zawartość dyskretnie, należy użyć cyfrowo podpisanych plików *cab* , nie plików *. mshc* .|
|/launchingApp|Nie|Definiuje kontekst aplikacji i katalogu, gdy Podgląd pomocy jest uruchamiany bez aplikacji nadrzędnej. Argumenty dla tego przełącznika to *NazwaFirmy*, *ProductName*i *versionNumber* (na przykład `/launchingApp Microsoft,VisualStudio,16.0`).<br /><br /> Jest to wymagane do zainstalowania zawartości za pomocą parametru/Silent.|
|/wait *s*|Nie|Wstrzymuje operacje instalowania, odinstalowywania i odświeżania. Jeśli operacja jest już w toku dla wykazu, proces będzie oczekiwać na podaną liczbę sekund, aby kontynuować. Aby czekać w nieskończoność, użyj wartości 0.|
|/?|Nie|Wyświetla listę przełączników i ich opisów dla narzędzia wiersza polecenia dla Menedżera zawartości pomocy.|

### <a name="exit-codes"></a>Kody zakończenia

Po uruchomieniu narzędzia wiersza polecenia dla Menedżera zawartości pomocy w trybie dyskretnym zwraca następujące kody zakończenia:

```
Success = 0,

FailureToElevate = 100
InvalidCmdArgs = 101,
FailOnFetchingOnlineContent = 110,
FailOnFetchingContentFromDisk = 120,
FailOnFetchingInstalledBooks = 130,
NoBooksToUninstall = 200,
NoBooksToInstall = 300,
FailOnUninstall = 400,
FailOnInstall = 500,
FailOnMove = 600,
FailOnUpdate = 700,
FailOnRefresh = 800,
Cancelled = 900,
Others = 999,
ContentManagementDisabled = 1200,
OnlineHelpPreferenceDisabled = 1201
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```

## <a name="see-also"></a>Zobacz także

- [Podręcznik administratora podglądu pomocy](../help-viewer/administrator-guide.md)
- [Przesłonięcia Menedżera zawartości pomocy](../help-viewer/behavior-overrides.md)
- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)
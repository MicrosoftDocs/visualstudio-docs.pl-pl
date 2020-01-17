---
title: Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak użyć parametrów wiersza polecenia, aby kontrolować lub dostosować instalację programu Visual Studio.
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7210a2834dda749cfe1d89b9093cd627b7c0ae1b
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114357"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio

Podczas instalowania programu Visual Studio z poziomu wiersza polecenia można użyć różnych parametrów wiersza polecenia do kontrolowania lub dostosowywania instalacji. W wierszu polecenia należy wykonać następujące czynności:

- Rozpocznij instalację z określonymi opcjami wstępnie wybrane.
- Zautomatyzuj proces instalacji.
- Tworzenie pamięci podręcznej (układ) plików instalacyjnych do późniejszego użycia.

Opcje wiersza polecenia są używane w połączeniu z programem inicjującym Instalatora, czyli małym (1 MB) plikiem inicjującym proces pobierania. Program inicjujący jest pierwszy plik wykonywalny, który jest uruchamiany, gdy można pobrać z witryny Visual Studio.

::: moniker range="vs-2017"

Aby uzyskać program inicjujący dla programu Visual Studio 2017, zobacz stronę pobierania [**poprzednich wersji programu Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/) , aby uzyskać szczegółowe informacje o tym, jak to zrobić.

::: moniker-end

::: moniker range="vs-2019"

Aby uzyskać bezpośredni link do najnowszej wersji program inicjujący dla wydanie produktu, który instalujesz, użyj następujących linków:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Plik programu inicjującego powinien być zgodny z jedną z następujących nazw plików lub być podobny:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Jeśli wcześniej pobrano plik inicjujący i chcesz sprawdzić jego wersję, poniżej przedstawiono sposób. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inicjującego, wybierz polecenie **Właściwości**, wybierz kartę **szczegóły** , a następnie Wyświetl numer **wersji produktu** . Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz stronę [numery kompilacji i daty wydania programu Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

## <a name="command-line-parameters"></a>Parametry wiersza polecenia

 Visual Studio, parametry wiersza polecenia jest rozróżniana wielkość liter.

> Składnia: `vs_enterprise.exe [command] <options>...`

Zastąp `vs_enterprise.exe` w zależności od wersji produktu, którą instalujesz. (Alternatywnie możesz użyć `vs_installer.exe`.)

>[!TIP]
> Aby uzyskać więcej przykładów użycia wiersza polecenia do instalowania programu Visual Studio, zobacz stronę [przykładów parametrów wiersza polecenia](command-line-parameter-examples.md) .

::: moniker range="vs-2017"

| **Polecenie** | **Opis** |
| ----------------------- | --------------- |
| (pusty) | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | **Nowość w wersji 15,9**: Eksportuje zaznaczenie instalacji do pliku konfiguracji instalacji. **Uwaga**: można używać tylko z vs_installer. exe. |

::: moniker-end

::: moniker range="vs-2019"

| **Polecenie** | **Opis** |
| ----------------------- | --------------- |
| (pusty) | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | Eksportuje zaznaczenie instalacji do pliku konfiguracji instalacji. **Uwaga**: można używać tylko z vs_installer. exe. |

::: moniker-end

## <a name="install-options"></a>Opcje instalacji

::: moniker range="vs-2017"

| **Opcję instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalogu instalacyjnego dla wystąpienia wykonywane działania. W przypadku polecenia install jest **opcjonalnie** i zainstalowanym wystąpieniem. W przypadku innych poleceń jest **wymagane** i zainstalowanym uprzednio zainstalowanego wystąpienia. |
| `--addProductLang <language-locale>` | **Opcjonalnie**: podczas instalacji lub zmodyfikować działanie, ta wartość określa pakiety językowe interfejsu użytkownika, które są instalowane z produktem. Może występować wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie występuje instalacja używa ustawień regionalnych komputera. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalnie**: podczas instalacji lub zmodyfikować działanie, ta wartość określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Może występować wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie**: obciążenia lub identyfikatory składników do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie na składnikach zalecane lub opcjonalne. Można kontrolować dodatkowych składników przy użyciu `--includeRecommended` i/lub `--includeOptional`. Aby dołączyć wielu obciążeń i składników, powtórz `--add` polecenia (na przykład `--add Workload1 --add Workload2`). Aby uzyskać bardziej szczegółowej kontroli można dołączyć `;includeRecommended` lub `;includeOptional` identyfikator (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Możesz powtórzyć tę opcję, zgodnie z potrzebami.|
| `--remove <one or more workload or component IDs>` | **Opcjonalnie**: obciążenia lub identyfikatory składników do usunięcia. Aby uzyskać więcej informacji, zobacz nasze [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Możesz powtórzyć tę opcję, zgodnie z potrzebami.|
| `--in <path>` | **Opcjonalnie**: identyfikator URI lub ścieżkę do pliku odpowiedzi.  |
| `--all` | **Opcjonalnie**: Określa, czy zainstalować wszystkie obciążenia i składniki dla produktu. |
| `--allWorkloads` | **Opcjonalnie**: instaluje wszystkich obciążeń i składników, nie zalecanych lub dodatkowych składników. |
| `--includeRecommended` | **Opcjonalnie**: obejmuje składniki zalecane dla dowolnych obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalnie**: obejmuje składniki opcjonalne dla dowolnych obciążeń, które są zainstalowane, ale nie na składnikach zalecane. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`.  |
| `--quiet, -q` | **Opcjonalne**: nie wyświetlaj interfejsu użytkownika podczas instalacji. |
| `--passive, -p` | **Opcjonalnie**: Wyświetl interfejs użytkownika, ale nie Żądaj żadnej interakcji z użytkownikiem. |
| `--norestart` | **Opcjonalnie**: Jeśli jest obecny, polecenia z `--passive` lub `--quiet` nie będą automatycznie ponownie uruchamiać maszyny (jeśli to konieczne).  To jest ignorowana, jeśli żadna `--passive` ani `--quiet` zostały określone.  |
| `--nickname <name>` | **Opcjonalnie**: definiuje pseudonim w celu przypisania do zainstalowanego produktu. Pseudonim nie może być dłuższy niż 10 znaków.  |
| `--productKey` | **Opcjonalnie**: Określa klucz produktu na potrzeby zainstalowany produkt. Składa się z 25 znaków alfanumerycznych w formacie `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` lub `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Wyświetl w trybie offline wersję tej strony. |
| `--config <path>` | **Opcjonalnie** i **Nowość w wersji 15.9**: podczas instalacji lub zmodyfikować działanie, ta wartość określa obciążeń i składników, aby dodać opartego na pliku konfiguracji instalacji wcześniej zapisany. Ta operacja jest dodatkiem i nie usuwa żadnego obciążenia ani składnika, jeśli nie znajdują się w pliku. Ponadto elementy, które nie mają zastosowania do produktu, nie zostaną dodane. Podczas operacji eksportowania Określa lokalizację do zapisania pliku konfiguracji instalacji. |

::: moniker-end

::: moniker range="vs-2019"

| **Opcję instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalogu instalacyjnego dla wystąpienia wykonywane działania. W przypadku polecenia install jest **opcjonalnie** i zainstalowanym wystąpieniem. W przypadku innych poleceń jest **wymagane** i zainstalowanym uprzednio zainstalowanego wystąpienia. |
| `--addProductLang <language-locale>` | **Opcjonalnie**: podczas instalacji lub zmodyfikować działanie, ta wartość określa pakiety językowe interfejsu użytkownika, które są instalowane z produktem. Może występować wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie występuje instalacja używa ustawień regionalnych komputera. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalnie**: podczas instalacji lub zmodyfikować działanie, ta wartość określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Może występować wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie**: obciążenia lub identyfikatory składników do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie na składnikach zalecane lub opcjonalne. Można kontrolować dodatkowych składników przy użyciu `--includeRecommended` i/lub `--includeOptional`. Aby dołączyć wielu obciążeń i składników, powtórz `--add` polecenia (na przykład `--add Workload1 --add Workload2`). Aby uzyskać bardziej szczegółowej kontroli można dołączyć `;includeRecommended` lub `;includeOptional` identyfikator (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Możesz powtórzyć tę opcję, zgodnie z potrzebami.|
| `--remove <one or more workload or component IDs>` | **Opcjonalnie**: obciążenia lub identyfikatory składników do usunięcia. Aby uzyskać więcej informacji, zobacz nasze [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Możesz powtórzyć tę opcję, zgodnie z potrzebami.|
| `--in <path>` | **Opcjonalnie**: identyfikator URI lub ścieżkę do pliku odpowiedzi.  |
| `--all` | **Opcjonalnie**: Określa, czy zainstalować wszystkie obciążenia i składniki dla produktu. |
| `--allWorkloads` | **Opcjonalnie**: instaluje wszystkich obciążeń i składników, nie zalecanych lub dodatkowych składników. |
| `--includeRecommended` | **Opcjonalnie**: obejmuje składniki zalecane dla dowolnych obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalnie**: obejmuje składniki opcjonalne dla dowolnych obciążeń, które są zainstalowane, ale nie na składnikach zalecane. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`.  |
| `--quiet, -q` | **Opcjonalne**: nie wyświetlaj interfejsu użytkownika podczas instalacji. |
| `--passive, -p` | **Opcjonalnie**: Wyświetl interfejs użytkownika, ale nie Żądaj żadnej interakcji z użytkownikiem. |
| `--norestart` | **Opcjonalnie**: Jeśli jest obecny, polecenia z `--passive` lub `--quiet` nie będą automatycznie ponownie uruchamiać maszyny (jeśli to konieczne).  To jest ignorowana, jeśli żadna `--passive` ani `--quiet` zostały określone.  |
| `--nickname <name>` | **Opcjonalnie**: definiuje pseudonim w celu przypisania do zainstalowanego produktu. Pseudonim nie może być dłuższy niż 10 znaków.  |
| `--productKey` | **Opcjonalnie**: Określa klucz produktu na potrzeby zainstalowany produkt. Składa się z 25 znaków alfanumerycznych w formacie `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` lub `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Wyświetl w trybie offline wersję tej strony. |
| `--config <path>` | **Opcjonalne**: podczas operacji instalacji lub modyfikacji program określa obciążenia i składniki do dodania na podstawie wcześniej zapisanego pliku konfiguracji instalacji. Ta operacja jest dodatkiem i nie usuwa żadnego obciążenia ani składnika, jeśli nie znajdują się w pliku. Ponadto elementy, które nie mają zastosowania do produktu, nie zostaną dodane. Podczas operacji eksportowania Określa lokalizację do zapisania pliku konfiguracji instalacji. |

::: moniker-end

> [!IMPORTANT]
> Podczas określania wielu obciążeń i składników należy powtórzyć `--add` lub `--remove` przełącznik wiersza polecenia dla każdego elementu.

## <a name="layout-options"></a>Opcje układu

::: moniker range="vs-2017"

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog do utworzenia w trybie offline instalować pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [utworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalnie**: używany z `--layout` przygotować offline instalowanie pamięci podręcznej przy użyciu pakietów zasobów przy użyciu określonego języki. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie**: obciążenia lub identyfikatory składników do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie na składnikach zalecane lub opcjonalne. Można kontrolować dodatkowych składników przy użyciu `--includeRecommended` i/lub `--includeOptional`. Aby uzyskać bardziej szczegółowej kontroli można dołączyć `;includeRecommended` lub `;includeOptional` identyfikator (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. <br/>**Uwaga**: Jeśli `--add` jest używany, tylko określony obciążeń i składników oraz ich zależności są pobierane. Jeśli nie określono `--add`, wszystkie obciążenia i składniki zostaną pobrane do układu.|
| `--includeRecommended` | **Opcjonalnie**: obejmuje składniki zalecane dla dowolnych obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalnie**: obejmuje zalecanym *i* składniki opcjonalne dla dowolnych obciążeń, które są uwzględniane w układzie. Obciążenia są określane za pomocą `--add`.  |
| `--keepLayoutVersion` | **Nowość w wersji 15.3, opcjonalnie**: Zastosuj zmiany do układu bez aktualizowania wersji układu. |
| `--verify` | **Nowość w wersji 15.3, opcjonalnie**: Sprawdź zawartość układu. Są wyświetlane wszystkie pliki niepoprawne lub nieobecne. |
| `--fix` | **Nowość w wersji 15.3, opcjonalnie**: Sprawdź zawartość układu. Jeśli pliki są uszkodzone lub ich brakuje, są one pobierane. Dostęp do Internetu jest wymagany do napraw układu. |
| `--clean <one or more paths to catalogs>` | **Nowość w wersji 15.3, opcjonalnie**: usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Opcje zaawansowane instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalnie**: identyfikator kanału dla tego wystąpienia do zainstalowania. Jest to wymagane przez polecenie instalacji i ignorowane dla innych poleceń, jeśli określono `--installPath`. |
| `--channelUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu kanału. Jeśli aktualizacje nie są potrzebne, `--channelUri` może wskazywać na nieistniejący plik (na przykład--identyfikator channeluri C:\doesntExist.chman). Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu kanału do użycia podczas instalacji. Identyfikator URI określony przez `--channelUri` (który musi być określony, gdy `--installChannelUri` określono) służy do wykrywania aktualizacji. Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu katalogu do użycia podczas instalacji. Jeśli zostanie określony, menedżera kanałów próbuje pobrać manifestu katalogu z tego identyfikatora URI, przed rozpoczęciem korzystania z identyfikatora URI w manifeście kanału instalacji. Ten parametr jest używany do obsługi instalacji w trybie offline, w której pamięci podręcznej układu zostanie utworzona z katalogu produktów już pobrane. Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--productId <id>` | **Opcjonalnie** identyfikator produktu dla tego wystąpienia, który zostanie zainstalowany. Jest to wstępne wypełnienie w normalnych warunkach instalacji. |
| `--wait` | **Opcjonalnie**: proces będzie czekać, aż do zakończenia instalacji, zanim zwróci kod zakończenia. Jest to przydatne podczas instalacji automatyzację, gdzie jeden musi czekać na instalacji na zakończenie obsługi kod powrotny od tej instalacji. |
| `--locale <language-locale>` | **Opcjonalnie**: zmianę języka wyświetlania interfejsu użytkownika Instalatora, sam. Ustawienia zostaną utrwalone. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--cache` | **Nowość w 15.2 opcjonalne**: Jeśli jest obecny, pakiety zostaną zachowane po zainstalowaniu dla kolejnych naprawy. Zastępuje to ustawienie ma być używany dla kolejnych instalacji, napraw lub modyfikacji zasad globalnych. Domyślne zasady to do pamięci podręcznej pakietów. To jest ignorowany dla polecenia dezinstalacji. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--nocache` | **Nowość w 15.2 opcjonalne**: Jeśli jest obecny, pakiety zostaną usunięte po zainstalować lub naprawić. Zostaną one pobrane ponownie tylko w razie konieczności i usunięte ponownie po użyciu. Zastępuje to ustawienie ma być używany dla kolejnych instalacji, napraw lub modyfikacji zasad globalnych. Domyślne zasady to do pamięci podręcznej pakietów. To jest ignorowany dla polecenia dezinstalacji. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Nowość w 15.2 opcjonalne**: Jeśli jest obecny, zapobiega sam aktualizacji, gdy określono quiet Instalator. Instalator spowoduje niepowodzenie polecenia i zwróci kod zakończenia różny od zera, jeśli noUpdateInstaller jest określony za pomocą cichy, gdy wymagana jest aktualizacja Instalatora. |
| `--noWeb` | **Nowość w 15,3, opcjonalnie**: Jeśli jest obecny, Instalator programu Visual Studio używa plików z katalogu układu do zainstalowania programu Visual Studio. Jeśli użytkownik spróbuje zainstalować składniki, które nie znajdują się w układzie, instalacja nie powiedzie się.  Aby uzyskać więcej informacji, zobacz [wdrażania z instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne**: ten przełącznik nie zatrzymuje sprawdzania dostępności aktualizacji przez Instalatora programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Kontrolowanie aktualizacji dla wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Nowość w wersji 15.7 opcjonalne**: używany do określenia ścieżki instalacji niestandardowej instalacji. Obsługiwana ścieżka, których nazwy są udostępniane, pamięci podręcznej i instalacji. |
| `--path cache=<path>` | **Nowość w wersji 15.7 opcjonalne**: korzysta z lokalizacji, należy określić, aby pobrać pliki instalacyjne. Tę lokalizację można ustawić tylko przy pierwszym jest zainstalowany program Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nowość w wersji 15.7 opcjonalne**: zawiera pliki udostępnione dla instalacji programu Visual Studio side-by-side. Niektóre narzędzia i zestawy SDK zainstalować lokalizacji na tym dysku, podczas gdy inne mogą zastąpić to ustawienie i instalowane na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: To można ustawić tylko raz, w pierwszym, który jest zainstalowany program Visual Studio. |
| `--path install=<path>` | **Nowość w wersji 15.7 opcjonalne**: odpowiednikiem `–-installPath`. W szczególności `--installPath "C:\VS"` i `--path install="C:\VS"` są równoważne. Można używać tylko jednego z tych poleceń jednocześnie. |

::: moniker-end

::: moniker range="vs-2019"

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog do utworzenia w trybie offline instalować pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [utworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalnie**: używany z `--layout` przygotować offline instalowanie pamięci podręcznej przy użyciu pakietów zasobów przy użyciu określonego języki. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie**: obciążenia lub identyfikatory składników do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie na składnikach zalecane lub opcjonalne. Można kontrolować dodatkowych składników przy użyciu `--includeRecommended` i/lub `--includeOptional`. Aby uzyskać bardziej szczegółowej kontroli można dołączyć `;includeRecommended` lub `;includeOptional` identyfikator (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. <br/>**Uwaga**: Jeśli `--add` jest używany, tylko określony obciążeń i składników oraz ich zależności są pobierane. Jeśli nie określono `--add`, wszystkie obciążenia i składniki zostaną pobrane do układu.|
| `--includeRecommended` | **Opcjonalnie**: obejmuje składniki zalecane dla dowolnych obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalnie**: obejmuje zalecanym *i* składniki opcjonalne dla dowolnych obciążeń, które są uwzględniane w układzie. Obciążenia są określane za pomocą `--add`.  |
| `--keepLayoutVersion` | **Opcjonalne**: Zastosuj zmiany do układu bez aktualizowania wersji układu. |
| `--verify` | **Opcjonalne**: Sprawdź zawartość układu. Są wyświetlane wszystkie pliki niepoprawne lub nieobecne. |
| `--fix` | **Opcjonalne**: Sprawdź zawartość układu.  Jeśli pliki są uszkodzone lub ich brakuje, są one pobierane. Dostęp do Internetu jest wymagany do napraw układu. |
| `--clean <one or more paths to catalogs>` | **Opcjonalne**: usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Opcje zaawansowane instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalnie**: identyfikator kanału dla tego wystąpienia do zainstalowania. Jest to wymagane przez polecenie instalacji i ignorowane dla innych poleceń, jeśli określono `--installPath`. |
| `--channelUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu kanału. Jeśli aktualizacje nie są potrzebne, `--channelUri` może wskazywać na nieistniejący plik (na przykład--identyfikator channeluri C:\doesntExist.chman). Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu kanału do użycia podczas instalacji. Identyfikator URI określony przez `--channelUri` (który musi być określony, gdy `--installChannelUri` określono) służy do wykrywania aktualizacji. Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu katalogu do użycia podczas instalacji. Jeśli zostanie określony, menedżera kanałów próbuje pobrać manifestu katalogu z tego identyfikatora URI, przed rozpoczęciem korzystania z identyfikatora URI w manifeście kanału instalacji. Ten parametr jest używany do obsługi instalacji w trybie offline, w której pamięci podręcznej układu zostanie utworzona z katalogu produktów już pobrane. Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--productId <id>` | **Opcjonalnie** identyfikator produktu dla tego wystąpienia, który zostanie zainstalowany. Jest to wstępne wypełnienie w normalnych warunkach instalacji. |
| `--wait` | **Opcjonalnie**: proces będzie czekać, aż do zakończenia instalacji, zanim zwróci kod zakończenia. Jest to przydatne podczas instalacji automatyzację, gdzie jeden musi czekać na instalacji na zakończenie obsługi kod powrotny od tej instalacji. |
| `--locale <language-locale>` | **Opcjonalnie**: zmianę języka wyświetlania interfejsu użytkownika Instalatora, sam. Ustawienia zostaną utrwalone. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--cache` | **Opcjonalnie**: Jeśli jest obecny, pakiety będą przechowywane po zainstalowaniu do kolejnych napraw. Zastępuje to ustawienie ma być używany dla kolejnych instalacji, napraw lub modyfikacji zasad globalnych. Domyślne zasady to do pamięci podręcznej pakietów. To jest ignorowany dla polecenia dezinstalacji. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--nocache` | **Opcjonalnie**: Jeśli jest obecny, pakiety zostaną usunięte po zainstalowaniu lub naprawieniu. Zostaną one pobrane ponownie tylko w razie konieczności i usunięte ponownie po użyciu. Zastępuje to ustawienie ma być używany dla kolejnych instalacji, napraw lub modyfikacji zasad globalnych. Domyślne zasady to do pamięci podręcznej pakietów. To jest ignorowany dla polecenia dezinstalacji. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Opcjonalnie**: Jeśli jest obecny, zapobiega aktualizacji samego Instalatora po określeniu cichym. Instalator spowoduje niepowodzenie polecenia i zwróci kod zakończenia różny od zera, jeśli noUpdateInstaller jest określony za pomocą cichy, gdy wymagana jest aktualizacja Instalatora. |
| `--noWeb` | **Opcjonalnie**: Jeśli jest obecny, Instalator programu Visual Studio używa plików w katalogu układu do instalowania programu Visual Studio. Jeśli użytkownik spróbuje zainstalować składniki, które nie znajdują się w układzie, instalacja nie powiedzie się.  Aby uzyskać więcej informacji, zobacz [wdrażania z instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne**: ten przełącznik nie zatrzymuje sprawdzania dostępności aktualizacji przez Instalatora programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Kontrolowanie aktualizacji dla wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md). **Nowość w 16.3.5**: ten przełącznik uniemożliwia błędy i poprawia wydajność przy użyciu instalacji i aktualizacji w trybie offline.|
| `--path <name>=<path>` | **Opcjonalne**: służy do określania niestandardowych ścieżek instalacji dla instalacji. Obsługiwana ścieżka, których nazwy są udostępniane, pamięci podręcznej i instalacji. |
| `--path cache=<path>` | **Opcjonalnie**: używa określonej lokalizacji do pobrania plików instalacyjnych. Tę lokalizację można ustawić tylko przy pierwszym jest zainstalowany program Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Opcjonalne**: zawiera udostępnione pliki do instalacji obok siebie w programie Visual Studio. Niektóre narzędzia i zestawy SDK zainstalować lokalizacji na tym dysku, podczas gdy inne mogą zastąpić to ustawienie i instalowane na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: To można ustawić tylko raz, w pierwszym, który jest zainstalowany program Visual Studio. |
| `--path install=<path>` | **Opcjonalne**: równoważne `–-installPath`. W szczególności `--installPath "C:\VS"` i `--path install="C:\VS"` są równoważne. Można używać tylko jednego z tych poleceń jednocześnie. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Lista identyfikatorów obciążenia i identyfikatory składników

Aby uzyskać listę identyfikatorów obciążeń i składników posortowanych przez program Visual Studio, zobacz stronę [obciążenia i identyfikatory składników programu Visual Studio](workload-and-component-ids.md) .

## <a name="list-of-language-locales"></a>Listę ustawień regionalnych języka

| **Ustawienia regionalne na język** | **Język** |
| ----------------------- | --------------- |
| CS-cz | czeski |
| De-de. | niemiecki |
| En-us | angielski |
| Es-es | Hiszpański |
| Fr-fr | francuski |
| IT-it | Włoski |
| Ja-jp | japoński |
| Ko-kr | koreański |
| Pl-pl | polski |
| pt-br | Portugalski (Brazylia) |
| Ru-ru | rosyjski |
| Wersja turecka | turecki |
| Nazwy zh-cn | Chiński (uproszczony) |
| Nazwy zh-tw | Chiński (tradycyjny) |

## <a name="error-codes"></a>Kody błędów

W zależności od wyniku operacji `%ERRORLEVEL%` zmienna środowiskowa jest ustawiony na jedną z następujących wartości:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Każda operacja generuje kilka plików dziennika w `%TEMP%` katalogu, który wskazuje postęp instalacji. Folder posortować według daty i poszukać plików, które zaczynają się od `dd_bootstrapper`, `dd_client`, i `dd_setup` dla programu inicjującego i instalację aplikacji Instalatora aparatu, odpowiednio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

- [Przykłady parametrów wiersza polecenia dla instalacji programu Visual Studio](command-line-parameter-examples.md)
- [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Zautomatyzowana instalacja programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)

---
title: Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak użyć parametrów wiersza polecenia, aby kontrolować lub dostosować instalację programu Visual Studio.
ms.date: 02/12/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 371574ad6c49d4601b571c2378c57fd399e6e715
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "57983078"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio

Po zainstalowaniu programu Visual Studio z poziomu wiersza polecenia można użyć różnych parametrów wiersza polecenia do kontrolowania lub dostosować instalację. W wierszu polecenia należy wykonać następujące czynności:

- Rozpocznij instalację z określonymi opcjami wstępnie wybrane.
- Zautomatyzuj proces instalacji.
- Tworzenie pamięci podręcznej (układ) plików instalacyjnych do późniejszego użycia.

Opcje wiersza polecenia są używane w połączeniu z program inicjujący Instalatora, który jest plikiem mała liczba godzin (około 1MB), który inicjuje proces pobierania. Program inicjujący jest pierwszy plik wykonywalny, który jest uruchamiany, gdy można pobrać z witryny Visual Studio. Aby uzyskać bezpośredni link do najnowszej wersji program inicjujący dla wydanie produktu, który instalujesz, użyj następujących linków:

- [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)

## <a name="command-line-parameters"></a>Parametry wiersza polecenia

 Visual Studio, parametry wiersza polecenia jest rozróżniana wielkość liter.

> Składnia: `vs_enterprise.exe [command] <options>...`

(Zastąp `vs_enterprise.exe` jako właściwe dla wersji produktu instalujesz.)

>[!TIP]
> Aby uzyskać więcej przykładów jak zainstalować program Visual Studio za pomocą wiersza polecenia, zobacz [przykładowe parametry wiersza polecenia](command-line-parameter-examples.md) strony.

| **Polecenie** | **Opis** |
| ----------------------- | --------------- |
| (pusty) | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | **Nowość w wersji 15.9**: Eksportuje wybór instalacji do pliku konfiguracji instalacji. **Uwaga**: Należy używać tylko z vs_installer.exe. |

## <a name="install-options"></a>Opcje instalacji

| **Opcję instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalogu instalacyjnego dla wystąpienia wykonywane działania. W przypadku polecenia install jest **opcjonalnie** i zainstalowanym wystąpieniem. W przypadku innych poleceń jest **wymagane** i zainstalowanym uprzednio zainstalowanego wystąpienia. |
| `--addProductLang <language-locale>` | **Opcjonalnie**: Podczas instalacji lub zmodyfikować działanie, ta wartość określa pakiety językowe interfejsu użytkownika, które są instalowane z produktem. Może występować wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie występuje instalacja używa ustawień regionalnych komputera. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalnie**: Podczas instalacji lub zmodyfikować działanie, ta wartość określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Może występować wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie**: Obciążenia lub identyfikatory składników do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie na składnikach zalecane lub opcjonalne. Można kontrolować dodatkowych składników przy użyciu `--includeRecommended` i/lub `--includeOptional`. Aby dołączyć wielu obciążeń i składników, powtórz `--add` polecenia (na przykład `--add Workload1 --add Workload2`). Aby uzyskać bardziej szczegółowej kontroli można dołączyć `;includeRecommended` lub `;includeOptional` identyfikator (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Możesz powtórzyć tę opcję, zgodnie z potrzebami.|
| `--remove <one or more workload or component IDs>` | **Opcjonalnie**: Obciążenia lub identyfikatory składników do usunięcia. Aby uzyskać więcej informacji, zobacz nasze [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Możesz powtórzyć tę opcję, zgodnie z potrzebami.|
| `--in <path>` | **Opcjonalnie**: Identyfikator URI lub ścieżka do pliku odpowiedzi.  |
| `--all` | **Opcjonalnie**: Określa, czy zainstalować wszystkie obciążenia i składniki dla produktu. |
| `--allWorkloads` | **Opcjonalnie**: Instaluje wszystkich obciążeń i składników, nie zalecanych lub dodatkowych składników. |
| `--includeRecommended` | **Opcjonalnie**: Zawiera składniki zalecane dla dowolnych obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalnie**: Zawiera składniki opcjonalne dla dowolnych obciążeń, które są zainstalowane, ale nie na składnikach zalecane. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`.  |
| `--quiet, -q` | **Opcjonalnie**: Nie wyświetla żadnego interfejsu użytkownika podczas wykonywania instalacji. |
| `--passive, -p` | **Opcjonalnie**: Wyświetlanie interfejsu użytkownika, ale nie poprosić interakcji użytkownika. |
| `--norestart` | **Opcjonalnie**: Jeśli jest obecny, polecenia za pomocą `--passive` lub `--quiet` nie uruchamia automatycznie ponownie komputera (w razie potrzeby).  To jest ignorowana, jeśli żadna `--passive` ani `--quiet` zostały określone.  |
| `--nickname <name>` | **Opcjonalnie**: Definiuje pseudonim w celu przypisania do zainstalowanego produktu. Pseudonim nie może być dłuższa niż 10 znaków.  |
| `--productKey` | **Opcjonalnie**: Definiuje klucz produktu na potrzeby zainstalowany produkt. Składa się z 25 alfanumeryczne znaki w formacie `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` lub `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Wyświetl w trybie offline wersję tej strony. |
| `--config <path>` | **Opcjonalnie** i **nowego w programie 15.9**: Podczas instalacji lub zmodyfikować działanie, ta wartość określa obciążeń i składników, aby dodać opartego na pliku konfiguracji instalacji wcześniej zapisany. Ta operacja jest dodatku i nie spowoduje usunięcia dowolnych obciążeń lub składników, jeśli nie istnieją w pliku. Ponadto elementy, których nie można zastosować do produktu nie zostanie dodany. Podczas operacji eksportowania Określa lokalizację do zapisania pliku konfiguracji instalacji. |

> [!IMPORTANT]
> Podczas określania wielu obciążeń i składników, należy powtórzyć `--add` lub `--remove` przełącznik wiersza polecenia dla każdego elementu.

## <a name="layout-options"></a>Opcje układu

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog do utworzenia w trybie offline instalować pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [utworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalnie**: Używane z `--layout` przygotować offline instalowanie pamięci podręcznej przy użyciu pakietów zasobów przy użyciu określonego języki. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie**: Obciążenia lub identyfikatory składników do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie na składnikach zalecane lub opcjonalne. Można kontrolować dodatkowych składników przy użyciu `--includeRecommended` i/lub `--includeOptional`. Aby uzyskać bardziej szczegółowej kontroli można dołączyć `;includeRecommended` lub `;includeOptional` identyfikator (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. <br/>**Uwaga**: Jeśli `--add` jest używany, tylko określony obciążeń i składników oraz ich zależności są pobierane. Jeśli `--add` nie zostanie określony, wszystkie obciążenia i składniki, które są pobierane do układu.|
| `--includeRecommended` | **Opcjonalnie**: Zawiera składniki zalecane dla dowolnych obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalnie**: Zawiera zalecane *i* składniki opcjonalne dla dowolnych obciążeń, które są uwzględniane w układzie. Obciążenia są określane za pomocą `--add`.  |
| `--keepLayoutVersion` | **Nowość w wersji 15.3, opcjonalnie**: Zastosuj zmiany do układu bez aktualizowania wersji układu. |
| `--verify` | **Nowość w wersji 15.3, opcjonalnie**: Sprawdź zawartość układu. Są wyświetlane wszystkie pliki niepoprawne lub nieobecne. |
| `--fix` | **Nowość w wersji 15.3, opcjonalnie**: Sprawdź zawartość układu.  Jeśli pliki znajdują się być uszkodzony lub nie ma, są ponownego pobrania ich. Dostęp do Internetu jest wymagany do napraw układu. |
| `--clean <one or more paths to catalogs>` | **Nowość w wersji 15.3, opcjonalnie**: Usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Opcje zaawansowane instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalnie**: Identyfikator kanału dla tego wystąpienia do zainstalowania. Jest to wymagane dla polecenia install ignorowany dla innych poleceń, jeśli `--installPath` jest określony. |
| `--channelUri <uri>` | **Opcjonalnie**: Identyfikator URI manifestu kanału. Jeśli aktualizacje nie są potrzebne `--channelUri` może wskazywać plik nie istnieje. (na przykład--channelUri C:\doesntExist.chman) Może być używany dla polecenia install; jest on ignorowany dla pozostałych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalnie**: Identyfikator URI manifestu kanału, do użycia podczas instalacji. Identyfikator URI określony przez `--channelUri` (który musi być określony, gdy `--installChannelUri` określono) służy do wykrywania aktualizacji. Może być używany dla polecenia install; jest on ignorowany dla pozostałych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalnie**: Identyfikator URI manifestu katalogu, do użycia podczas instalacji. Jeśli zostanie określony, menedżera kanałów próbuje pobrać manifestu katalogu z tego identyfikatora URI, przed rozpoczęciem korzystania z identyfikatora URI w manifeście kanału instalacji. Ten parametr jest używany do obsługi instalacji w trybie offline, w której pamięci podręcznej układu zostanie utworzona z katalogu produktów już pobrane. Może być używany dla polecenia install; jest on ignorowany dla pozostałych poleceń. |
| `--productId <id>` | **Opcjonalnie** identyfikator produktu dla tego wystąpienia, który zostanie zainstalowany. To są wstępnie wypełnione w warunkach normalnej instalacji. |
| `--wait` | **Opcjonalnie**: Proces będzie czekać, aż do zakończenia instalacji, zanim zwróci kod zakończenia. Jest to przydatne podczas instalacji automatyzację, gdzie jeden musi czekać na instalacji na zakończenie obsługi kod powrotny od tej instalacji. |
| `--locale <language-locale>` | **Opcjonalnie**: Zmień język wyświetlania interfejsu użytkownika Instalatora, sam. Ustawienia zostaną utrwalone. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--cache` | **Nowość w 15.2 opcjonalne**: Jeśli jest obecny, pakiety zostaną zachowane po zainstalowaniu dla kolejnych naprawy. Zastępuje to ustawienie ma być używany dla kolejnych instalacji, napraw lub modyfikacji zasad globalnych. Domyślne zasady to do pamięci podręcznej pakietów. To jest ignorowany dla polecenia dezinstalacji. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--nocache` | **Nowość w 15.2 opcjonalne**: Jeśli jest obecny, pakiety zostaną usunięte po zainstalować lub naprawić. Tylko wtedy, gdy są potrzebne, a następnie ponownie usunięte użycia będzie można ponownie pobrać. Zastępuje to ustawienie ma być używany dla kolejnych instalacji, napraw lub modyfikacji zasad globalnych. Domyślne zasady to do pamięci podręcznej pakietów. To jest ignorowany dla polecenia dezinstalacji. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Nowość w 15.2 opcjonalne**: Jeśli jest obecny, uniemożliwia Instalator aktualizowanie sam, gdy określono cichy. Instalator spowoduje niepowodzenie polecenia i zwróci kod zakończenia różny od zera, jeśli noUpdateInstaller jest określony za pomocą cichy, gdy wymagana jest aktualizacja Instalatora. |
| `--noWeb` | **Nowość w wersji 15.3, opcjonalnie**: Jeśli jest obecny, Instalator programu Visual Studio używa pliki w katalogu układu do instalacji programu Visual Studio. Jeśli użytkownik próbuje zainstalować składniki, które nie są w układzie, instalacja kończy się niepowodzeniem.  Aby uzyskać więcej informacji, zobacz [wdrażania z instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne**: Ten przełącznik nie zatrzymuje instalację programu Visual Studio z sprawdzania dostępności aktualizacji. Aby uzyskać więcej informacji, zobacz [kontrolowania aktualizacji z wdrożeniami programu Visual Studio sieciowymi programami wykorzystującymi](controlling-updates-to-visual-studio-deployments.md).|
| `--path <name>=<path>` | **Nowość w wersji 15.7 opcjonalne**: Służy do określania ścieżki instalacji niestandardowej instalacji. Obsługiwana ścieżka, których nazwy są udostępniane, pamięci podręcznej i instalacji. |
| `--path cache=<path>` | **Nowość w wersji 15.7 opcjonalne**: Używa lokalizacji, należy określić, aby pobrać pliki instalacyjne. Tę lokalizację można ustawić tylko przy pierwszym jest zainstalowany program Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nowość w wersji 15.7 opcjonalne**: Zawiera pliki udostępnione dla instalacji programu Visual Studio side-by-side. Niektóre narzędzia i zestawy SDK zainstalować lokalizacji na tym dysku, podczas gdy inne mogą zastąpić to ustawienie i instalowane na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: To można ustawić tylko raz, w pierwszym, który jest zainstalowany program Visual Studio. |
| `--path install=<path>` | **Nowość w wersji 15.7 opcjonalne**: Odpowiednikiem `–-installPath`. W szczególności `--installPath "C:\VS"` i `--path install="C:\VS"` są równoważne. Tylko jeden z nich może służyć w danym momencie. |

## <a name="list-of-workload-ids-and-component-ids"></a>Lista identyfikatorów obciążenia i identyfikatory składników

Aby uzyskać listę obciążenia i identyfikatorów składników, posortowane według produktu Visual Studio, zobacz [identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md) strony.

## <a name="list-of-language-locales"></a>Listę ustawień regionalnych języka

| **Ustawienia regionalne na język** | **Język** |
| ----------------------- | --------------- |
| CS-cz | czeski |
| De-de. | niemiecki |
| En-us | Angielski |
| Es-es | Hiszpański |
| Fr-fr | Francuski |
| IT-it | Włoski |
| Ja-jp | japoński |
| Ko-kr | koreański |
| Pl-pl | polski |
| pt-br | Portugalski (Brazylia) |
| Ru-ru | Rosyjski |
| Wersja turecka | turecki |
| Nazwy zh-cn | Chiński (uproszczony) |
| Nazwy zh-tw | Chiński — tradycyjny |

## <a name="error-codes"></a>Kody błędów

W zależności od wyniku operacji `%ERRORLEVEL%` zmienna środowiskowa jest ustawiony na jedną z następujących wartości:

| **Wartość** | **wynik** |
| --------- | ---------- |
| 0 | Operacja została ukończona pomyślnie |
| 1602 | Operacja została anulowana |
| 3010 | Operacja ukończona pomyślnie, ale instalacja wymaga ponownego uruchomienia, zanim będzie można jej używać. |
| 5004 | Operacja została anulowana |
| 5007 | Operacja została zablokowana — komputer nie spełnia wymagań |
| Inne | Wystąpił błąd warunek — Sprawdź dzienniki Aby uzyskać więcej informacji |

Każda operacja generuje kilka plików dziennika w `%TEMP%` katalogu, który wskazuje postęp instalacji. Folder posortować według daty i poszukać plików, które zaczynają się od `dd_bootstrapper`, `dd_client`, i `dd_setup` dla programu inicjującego i instalację aplikacji Instalatora aparatu, odpowiednio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

- [Przykładowe parametry wiersza polecenia do zainstalowania programu Visual Studio](command-line-parameter-examples.md)
- [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Zautomatyzowana instalacja programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
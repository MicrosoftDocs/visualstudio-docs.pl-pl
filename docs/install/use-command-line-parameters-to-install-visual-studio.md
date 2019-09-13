---
title: Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak użyć parametrów wiersza polecenia, aby kontrolować lub dostosować instalację programu Visual Studio.
ms.date: 09/11/2019
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
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1f9e5d1dadd9caf95b8e6cb8e5fec70daf984ac9
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913244"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio

Podczas instalowania programu Visual Studio z poziomu wiersza polecenia można użyć różnych parametrów wiersza polecenia do kontrolowania lub dostosowywania instalacji. W wierszu polecenia należy wykonać następujące czynności:

- Rozpocznij instalację z określonymi opcjami wstępnie wybrane.
- Zautomatyzuj proces instalacji.
- Tworzenie pamięci podręcznej (układ) plików instalacyjnych do późniejszego użycia.

Opcje wiersza polecenia są używane w połączeniu z programem inicjującym Instalatora, czyli małym (1 MB) plikiem inicjującym proces pobierania. Program inicjujący jest pierwszy plik wykonywalny, który jest uruchamiany, gdy można pobrać z witryny Visual Studio. Aby uzyskać bezpośredni link do najnowszej wersji program inicjujący dla wydanie produktu, który instalujesz, użyj następujących linków:

::: moniker range="vs-2017"

- [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end

## <a name="command-line-parameters"></a>Parametry wiersza polecenia

 Visual Studio, parametry wiersza polecenia jest rozróżniana wielkość liter.

> Składnia: `vs_enterprise.exe [command] <options>...`

Zastąp `vs_enterprise.exe` odpowiednie dla instalowanej wersji produktu. (Alternatywnie można użyć `vs_installer.exe`.)

>[!TIP]
> Aby uzyskać więcej przykładów użycia wiersza polecenia do instalowania programu Visual Studio, zobacz stronę [przykładów parametrów wiersza polecenia](command-line-parameter-examples.md) .

| **Polecenie** | **Opis** |
| ----------------------- | --------------- |
| (pusty) | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | **Nowość w wersji 15,9**: Eksportuje zaznaczenie instalacji do pliku konfiguracji instalacji. **Uwaga**: Można go używać tylko z vs_installer. exe. |

## <a name="install-options"></a>Opcje instalacji

| **Opcję instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalogu instalacyjnego dla wystąpienia wykonywane działania. W przypadku polecenia install jest **opcjonalnie** i zainstalowanym wystąpieniem. W przypadku innych poleceń jest **wymagane** i zainstalowanym uprzednio zainstalowanego wystąpienia. |
| `--addProductLang <language-locale>` | **Opcjonalne**: Podczas operacji instalacji lub modyfikacji określa pakiety językowe interfejsu użytkownika, które są zainstalowane w produkcie. Może występować wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie występuje instalacja używa ustawień regionalnych komputera. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalne**: Podczas operacji instalacji lub modyfikacji określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Może występować wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalne**: Co najmniej jeden identyfikator obciążenia lub składnika do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie na składnikach zalecane lub opcjonalne. Można kontrolować dodatkowych składników przy użyciu `--includeRecommended` i/lub `--includeOptional`. Aby dołączyć wielu obciążeń i składników, powtórz `--add` polecenia (na przykład `--add Workload1 --add Workload2`). Aby uzyskać bardziej szczegółowej kontroli można dołączyć `;includeRecommended` lub `;includeOptional` identyfikator (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Możesz powtórzyć tę opcję, zgodnie z potrzebami.|
| `--remove <one or more workload or component IDs>` | **Opcjonalne**: Co najmniej jeden identyfikator obciążenia lub składnika do usunięcia. Aby uzyskać więcej informacji, zobacz nasze [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. Możesz powtórzyć tę opcję, zgodnie z potrzebami.|
| `--in <path>` | **Opcjonalne**: Identyfikator URI lub ścieżka do pliku odpowiedzi.  |
| `--all` | **Opcjonalne**: Czy instalować wszystkie obciążenia i składniki produktu. |
| `--allWorkloads` | **Opcjonalne**: Instaluje wszystkie obciążenia i składniki, brak zalecanych lub opcjonalnych składników. |
| `--includeRecommended` | **Opcjonalne**: Zawiera zalecane składniki dla wszystkich obciążeń, które są zainstalowane, ale nie opcjonalne składniki. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalne**: Obejmuje opcjonalne składniki dla wszelkich zainstalowanych obciążeń, ale nie zalecanych składników. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`.  |
| `--quiet, -q` | **Opcjonalne**: Podczas przeprowadzania instalacji nie są wyświetlane żadne interfejsy użytkownika. |
| `--passive, -p` | **Opcjonalne**: Wyświetl interfejs użytkownika, ale nie Żądaj żadnej interakcji z użytkownikiem. |
| `--norestart` | **Opcjonalne**: Jeśli jest obecny, polecenia `--passive` z `--quiet` lub nie będą automatycznie ponownie uruchamiać komputera (jeśli to konieczne).  To jest ignorowana, jeśli żadna `--passive` ani `--quiet` zostały określone.  |
| `--nickname <name>` | **Opcjonalne**: Definiuje pseudonim do przypisania do zainstalowanego produktu. Pseudonim nie może być dłuższa niż 10 znaków.  |
| `--productKey` | **Opcjonalne**: Definiuje klucz produktu do użycia w przypadku zainstalowanego produktu. Składa się z 25 alfanumeryczne znaki w formacie `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` lub `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Wyświetl w trybie offline wersję tej strony. |
| `--config <path>` | **Opcjonalne** i **nowe w 15,9**: Podczas operacji instalacji lub modyfikacji program określa obciążenia i składniki do dodania na podstawie wcześniej zapisanego pliku konfiguracji instalacji. Ta operacja jest dodatku i nie spowoduje usunięcia dowolnych obciążeń lub składników, jeśli nie istnieją w pliku. Ponadto elementy, których nie można zastosować do produktu nie zostanie dodany. Podczas operacji eksportowania Określa lokalizację do zapisania pliku konfiguracji instalacji. |

> [!IMPORTANT]
> Podczas określania wielu obciążeń i składników należy powtórzyć `--add` przełącznik wiersza polecenia lub `--remove` dla każdego elementu.

## <a name="layout-options"></a>Opcje układu

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog do utworzenia w trybie offline instalować pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [utworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalne**: Używany z `--layout` programem w celu przygotowania pamięci podręcznej instalacji w trybie offline z pakietami zasobów z określonymi językami. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalne**: Co najmniej jeden identyfikator obciążenia lub składnika do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie na składnikach zalecane lub opcjonalne. Można kontrolować dodatkowych składników przy użyciu `--includeRecommended` i/lub `--includeOptional`. Aby uzyskać bardziej szczegółowej kontroli można dołączyć `;includeRecommended` lub `;includeOptional` identyfikator (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenia i identyfikatory składników](workload-and-component-ids.md) strony. <br/>**Uwaga**: Jeśli `--add` jest używany, pobierane są tylko określone obciążenia i składniki oraz ich zależności. Jeśli `--add` nie zostanie określony, wszystkie obciążenia i składniki, które są pobierane do układu.|
| `--includeRecommended` | **Opcjonalne**: Zawiera zalecane składniki dla wszystkich obciążeń, które są zainstalowane, ale nie opcjonalne składniki. Obciążenia są określane za pomocą `--allWorkloads` lub `--add`. |
| `--includeOptional` | **Opcjonalne**: Obejmuje składniki zalecane *i* opcjonalne dla wszelkich obciążeń uwzględnionych w układzie. Obciążenia są określane za pomocą `--add`.  |
| `--keepLayoutVersion` | **Nowość w 15,3, opcjonalnie**: Zastosuj zmiany do układu bez aktualizowania wersji układu. |
| `--verify` | **Nowość w 15,3, opcjonalnie**: Sprawdź zawartość układu. Są wyświetlane wszystkie pliki niepoprawne lub nieobecne. |
| `--fix` | **Nowość w 15,3, opcjonalnie**: Sprawdź zawartość układu.  Jeśli pliki znajdują się być uszkodzony lub nie ma, są ponownego pobrania ich. Dostęp do Internetu jest wymagany do napraw układu. |
| `--clean <one or more paths to catalogs>` | **Nowość w 15,3, opcjonalnie**: Usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Opcje zaawansowane instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalne**: Identyfikator kanału dla wystąpienia, które ma zostać zainstalowane. Jest to wymagane dla polecenia install ignorowany dla innych poleceń, jeśli `--installPath` jest określony. |
| `--channelUri <uri>` | **Opcjonalne**: Identyfikator URI manifestu kanału. Jeśli aktualizacje nie są odpowiednie, `--channelUri` mogą wskazywać na nieistniejący plik (na przykład--identyfikator channeluri C:\doesntExist.Chman). Może być używany dla polecenia install; jest on ignorowany dla pozostałych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalne**: Identyfikator URI manifestu kanału do użycia podczas instalacji. Identyfikator URI określony przez `--channelUri` (który musi być określony, gdy `--installChannelUri` określono) służy do wykrywania aktualizacji. Może być używany dla polecenia install; jest on ignorowany dla pozostałych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalne**: Identyfikator URI manifestu wykazu do użycia podczas instalacji. Jeśli zostanie określony, menedżera kanałów próbuje pobrać manifestu katalogu z tego identyfikatora URI, przed rozpoczęciem korzystania z identyfikatora URI w manifeście kanału instalacji. Ten parametr jest używany do obsługi instalacji w trybie offline, w której pamięci podręcznej układu zostanie utworzona z katalogu produktów już pobrane. Może być używany dla polecenia install; jest on ignorowany dla pozostałych poleceń. |
| `--productId <id>` | **Opcjonalnie** identyfikator produktu dla tego wystąpienia, który zostanie zainstalowany. To są wstępnie wypełnione w warunkach normalnej instalacji. |
| `--wait` | **Opcjonalne**: Proces zaczeka na ukończenie instalacji przed zwróceniem kodu zakończenia. Jest to przydatne podczas instalacji automatyzację, gdzie jeden musi czekać na instalacji na zakończenie obsługi kod powrotny od tej instalacji. |
| `--locale <language-locale>` | **Opcjonalne**: Zmień język wyświetlania interfejsu użytkownika dla samego Instalatora. Ustawienia zostaną utrwalone. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) sekcji na tej stronie.|
| `--cache` | **Nowość w 15,2, opcjonalnie**: Jeśli jest obecny, pakiety będą przechowywane po zainstalowaniu do kolejnych napraw. Zastępuje to ustawienie ma być używany dla kolejnych instalacji, napraw lub modyfikacji zasad globalnych. Domyślne zasady to do pamięci podręcznej pakietów. To jest ignorowany dla polecenia dezinstalacji. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--nocache` | **Nowość w 15,2, opcjonalnie**: Jeśli jest obecny, pakiety zostaną usunięte po zainstalowaniu lub naprawieniu. Tylko wtedy, gdy są potrzebne, a następnie ponownie usunięte użycia będzie można ponownie pobrać. Zastępuje to ustawienie ma być używany dla kolejnych instalacji, napraw lub modyfikacji zasad globalnych. Domyślne zasady to do pamięci podręcznej pakietów. To jest ignorowany dla polecenia dezinstalacji. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Nowość w 15,2, opcjonalnie**: Jeśli jest obecny, zapobiega aktualizacji samego Instalatora po określeniu cichym. Instalator spowoduje niepowodzenie polecenia i zwróci kod zakończenia różny od zera, jeśli noUpdateInstaller jest określony za pomocą cichy, gdy wymagana jest aktualizacja Instalatora. |
| `--noWeb` | **Nowość w 15,3, opcjonalnie**: Jeśli jest obecny, Instalator programu Visual Studio używa plików z katalogu układu do zainstalowania programu Visual Studio. Jeśli użytkownik spróbuje zainstalować składniki, które nie znajdują się w układzie, instalacja nie powiedzie się.  Aby uzyskać więcej informacji, zobacz [wdrażania z instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne**: Ten przełącznik nie zatrzymuje sprawdzania dostępności aktualizacji przez Instalatora programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Kontrolowanie aktualizacji dla wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md).|
| `--path <name>=<path>` | **Nowość w 15,7, opcjonalnie**: Służy do określania niestandardowych ścieżek instalacji dla instalacji. Obsługiwana ścieżka, których nazwy są udostępniane, pamięci podręcznej i instalacji. |
| `--path cache=<path>` | **Nowość w 15,7, opcjonalnie**: Używa określonej lokalizacji do pobrania plików instalacyjnych. Tę lokalizację można ustawić tylko przy pierwszym jest zainstalowany program Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nowość w 15,7, opcjonalnie**: Zawiera pliki udostępnione dla równoległych instalacji programu Visual Studio. Niektóre narzędzia i zestawy SDK zainstalować lokalizacji na tym dysku, podczas gdy inne mogą zastąpić to ustawienie i instalowane na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: Tę wartość można ustawić tylko raz i po raz pierwszy, gdy program Visual Studio jest zainstalowany. |
| `--path install=<path>` | **Nowość w 15,7, opcjonalnie**: `–-installPath`Odpowiednik. W szczególności `--installPath "C:\VS"` i `--path install="C:\VS"` są równoważne. Tylko jeden z nich może służyć w danym momencie. |

## <a name="list-of-workload-ids-and-component-ids"></a>Lista identyfikatorów obciążenia i identyfikatory składników

Aby uzyskać listę identyfikatorów obciążeń i składników posortowanych przez program Visual Studio, zobacz stronę [obciążenia i identyfikatory składników programu Visual Studio](workload-and-component-ids.md) .

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

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Każda operacja generuje kilka plików dziennika w `%TEMP%` katalogu, który wskazuje postęp instalacji. Folder posortować według daty i poszukać plików, które zaczynają się od `dd_bootstrapper`, `dd_client`, i `dd_setup` dla programu inicjującego i instalację aplikacji Instalatora aparatu, odpowiednio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

- [Przykłady parametrów wiersza polecenia dla instalacji programu Visual Studio](command-line-parameter-examples.md)
- [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Zautomatyzowana instalacja programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)

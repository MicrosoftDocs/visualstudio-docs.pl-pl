---
title: Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak za pomocą parametrów wiersza polecenia kontrolować lub dostosowywać instalację programu Visual Studio.
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
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d5bea30b8a046be55ba49a1cc1dbf12e3093585f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935665"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio

Podczas instalowania programu Visual Studio z poziomu wiersza polecenia można użyć różnych parametrów wiersza polecenia do kontrolowania lub dostosowywania instalacji. W wierszu polecenia można wykonać następujące czynności:

- Uruchom instalację z pewnymi wybranymi opcjami.
- Automatyzowanie procesu instalacji.
- Utwórz pamięć podręczną (układ) plików instalacyjnych do późniejszego użycia.

Opcje wiersza polecenia są używane w połączeniu z programem inicjującym Instalatora, czyli małym (1 MB) plikiem inicjującym proces pobierania. Program inicjujący to pierwszy plik wykonywalny, który jest uruchamiany podczas pobierania z witryny programu Visual Studio.

::: moniker range="vs-2017"

Aby uzyskać program inicjujący dla programu Visual Studio 2017, zobacz stronę pobierania [**poprzednich wersji programu Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/) , aby uzyskać szczegółowe informacje o tym, jak to zrobić.

::: moniker-end

::: moniker range="vs-2019"

Skorzystaj z poniższych linków, aby uzyskać bezpośredni link do najnowszej wersji programu inicjującego dla instalowanej wersji produktu:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Społeczność programu Visual Studio 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Plik programu inicjującego powinien być zgodny z jedną z następujących nazw plików lub być podobny:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Jeśli wcześniej pobrano plik inicjujący i chcesz sprawdzić jego wersję, poniżej przedstawiono sposób. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inicjującego, wybierz polecenie **Właściwości**, wybierz kartę **szczegóły** , a następnie Wyświetl numer **wersji produktu** . Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz stronę [numery kompilacji i daty wydania programu Visual Studio](visual-studio-build-numbers-and-release-dates.md) .

## <a name="command-line-parameters"></a>Parametry wiersza polecenia

 W parametrach wiersza polecenia programu Visual Studio nie jest rozróżniana wielkość liter.

> Obowiązuje `vs_enterprise.exe [command] <options>...`

Zastąp `vs_enterprise.exe` odpowiednie dla instalowanej wersji produktu. (Alternatywnie można użyć `vs_installer.exe` .)

>[!TIP]
> Aby uzyskać więcej przykładów użycia wiersza polecenia do instalowania programu Visual Studio, zobacz stronę [przykładów parametrów wiersza polecenia](command-line-parameter-examples.md) .

::: moniker range="vs-2017"

| **Polecenie** | **Opis** |
| ----------------------- | --------------- |
| puste | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | **Nowość w wersji 15,9**: Eksportuje zaznaczenie instalacji do pliku konfiguracji instalacji. **Uwaga**: można używać tylko z vs_installer.exe. |

::: moniker-end

::: moniker range="vs-2019"

| **Polecenie** | **Opis** |
| ----------------------- | --------------- |
| puste | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | Eksportuje zaznaczenie instalacji do pliku konfiguracji instalacji. **Uwaga**: można używać tylko z vs_installer.exe. |

::: moniker-end

## <a name="install-options"></a>Opcje instalacji

::: moniker range="vs-2017"

| **Opcja instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalog instalacji wystąpienia, na którym ma być wykonywane działanie. W przypadku polecenia install jest to **opcjonalne** i polega na tym, że wystąpienie zostanie zainstalowane. W przypadku innych poleceń jest to **wymagane** i polega na tym, że wcześniej zainstalowane wystąpienie zostało zainstalowane. |
| `--addProductLang <language-locale>` | **Opcjonalne**: podczas operacji instalacji lub modyfikacji program określa pakiety językowe interfejsu użytkownika, które są zainstalowane w produkcie. Może pojawić się wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie istnieje, instalacja używa ustawień regionalnych komputera. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [listy ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalne**: podczas operacji instalacji lub modyfikacji określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Może pojawić się wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [listy ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalne**: co najmniej jeden identyfikator obciążenia lub składnika do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie są to zalecane ani opcjonalne składniki. Dodatkowe składniki można kontrolować globalnie przy użyciu `--includeRecommended` i/lub `--includeOptional` . Aby uwzględnić wiele obciążeń lub składników, należy powtórzyć `--add` polecenie (na przykład `--add Workload1 --add Workload2` ). Aby uzyskać dokładniejszą kontrolę, można dołączyć `;includeRecommended` lub `;includeOptional` do identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional` ). Aby uzyskać więcej informacji, zobacz stronę [obciążenia i identyfikatory składników](workload-and-component-ids.md) . Tę opcję można powtórzyć w razie potrzeby.|
| `--remove <one or more workload or component IDs>` | **Opcjonalne**: co najmniej jeden identyfikator obciążenia lub składnika do usunięcia. Aby uzyskać więcej informacji, zobacz nasze strony dotyczące [obciążeń i identyfikatorów składników](workload-and-component-ids.md) . Tę opcję można powtórzyć w razie potrzeby.|
| `--in <path>` | **Opcjonalnie**: identyfikator URI lub ścieżka do pliku odpowiedzi.  |
| `--all` | **Opcjonalne**: czy instalować wszystkie obciążenia i składniki produktu. |
| `--allWorkloads` | **Opcjonalnie**: instaluje wszystkie obciążenia i składniki, brak zalecanych lub opcjonalnych składników. |
| `--includeRecommended` | **Opcjonalne**: zawiera zalecane składniki dla wszelkich obciążeń, które są zainstalowane, ale nie opcjonalne składniki. Obciążenia są określane przy użyciu `--allWorkloads` lub `--add` . |
| `--includeOptional` | **Opcjonalne**: zawiera opcjonalne składniki dla wszelkich zainstalowanych obciążeń, ale nie zalecanych składników. Obciążenia są określane przy użyciu `--allWorkloads` lub `--add` .  |
| `--quiet, -q` | **Opcjonalne**: nie wyświetlaj interfejsu użytkownika podczas instalacji. |
| `--passive, -p` | **Opcjonalnie**: Wyświetl interfejs użytkownika, ale nie Żądaj żadnej interakcji z użytkownikiem. |
| `--norestart` | **Opcjonalnie**: Jeśli jest obecny, polecenia z `--passive` lub `--quiet` nie będą automatycznie ponownie uruchamiać maszyny (jeśli to konieczne).  Ta operacja jest ignorowana, jeśli nie `--passive` określono żadnego ani `--quiet` .  |
| `--nickname <name>` | **Opcjonalnie**: definiuje pseudonim do przypisania do zainstalowanego produktu. Pseudonim nie może być dłuższy niż 10 znaków.  |
| `--productKey` | **Opcjonalnie**: definiuje klucz produktu do użycia w przypadku zainstalowanego produktu. Składa się z 25 znaków alfanumerycznych w formacie `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` lub `xxxxxxxxxxxxxxxxxxxxxxxxx` . |
| `--help, --?, -h, -?` | Wyświetl wersję offline tej strony. |
| `--config <path>` | **Opcjonalne** i **Nowość w 15,9**: podczas operacji instalacji lub modyfikacji, określa obciążenia i składniki do dodania na podstawie wcześniej zapisanego pliku konfiguracji instalacji. Ta operacja jest dodatkiem i nie usuwa żadnego obciążenia ani składnika, jeśli nie znajdują się w pliku. Ponadto elementy, które nie mają zastosowania do produktu, nie zostaną dodane. Podczas operacji eksportowania Określa lokalizację, w której ma zostać zapisany plik konfiguracji instalacji. |

::: moniker-end

::: moniker range="vs-2019"

| **Opcja instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalog instalacji wystąpienia, na którym ma być wykonywane działanie. W przypadku polecenia install jest to **opcjonalne** i polega na tym, że wystąpienie zostanie zainstalowane. W przypadku innych poleceń jest to **wymagane** i polega na tym, że wcześniej zainstalowane wystąpienie zostało zainstalowane. |
| `--addProductLang <language-locale>` | **Opcjonalne**: podczas operacji instalacji lub modyfikacji program określa pakiety językowe interfejsu użytkownika, które są zainstalowane w produkcie. Może pojawić się wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie istnieje, instalacja używa ustawień regionalnych komputera. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [listy ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalne**: podczas operacji instalacji lub modyfikacji określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Może pojawić się wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [listy ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalne**: co najmniej jeden identyfikator obciążenia lub składnika do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie są to zalecane ani opcjonalne składniki. Dodatkowe składniki można kontrolować globalnie przy użyciu `--includeRecommended` i/lub `--includeOptional` . Aby uwzględnić wiele obciążeń lub składników, należy powtórzyć `--add` polecenie (na przykład `--add Workload1 --add Workload2` ). Aby uzyskać dokładniejszą kontrolę, można dołączyć `;includeRecommended` lub `;includeOptional` do identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional` ). Aby uzyskać więcej informacji, zobacz stronę [obciążenia i identyfikatory składników](workload-and-component-ids.md) . Tę opcję można powtórzyć w razie potrzeby.|
| `--remove <one or more workload or component IDs>` | **Opcjonalne**: co najmniej jeden identyfikator obciążenia lub składnika do usunięcia. Aby uzyskać więcej informacji, zobacz nasze strony dotyczące [obciążeń i identyfikatorów składników](workload-and-component-ids.md) . Tę opcję można powtórzyć w razie potrzeby.|
| `--in <path>` | **Opcjonalnie**: identyfikator URI lub ścieżka do pliku odpowiedzi.  |
| `--all` | **Opcjonalne**: czy instalować wszystkie obciążenia i składniki produktu. |
| `--allWorkloads` | **Opcjonalnie**: instaluje wszystkie obciążenia i składniki, brak zalecanych lub opcjonalnych składników. |
| `--includeRecommended` | **Opcjonalne**: zawiera zalecane składniki dla wszelkich obciążeń, które są zainstalowane, ale nie opcjonalne składniki. Obciążenia są określane przy użyciu `--allWorkloads` lub `--add` . |
| `--includeOptional` | **Opcjonalne**: zawiera opcjonalne składniki dla wszelkich zainstalowanych obciążeń, ale nie zalecanych składników. Obciążenia są określane przy użyciu `--allWorkloads` lub `--add` .  |
| `--quiet, -q` | **Opcjonalne**: nie wyświetlaj interfejsu użytkownika podczas instalacji. |
| `--passive, -p` | **Opcjonalnie**: Wyświetl interfejs użytkownika, ale nie Żądaj żadnej interakcji z użytkownikiem. |
| `--norestart` | **Opcjonalnie**: Jeśli jest obecny, polecenia z `--passive` lub `--quiet` nie będą automatycznie ponownie uruchamiać maszyny (jeśli to konieczne).  Ta operacja jest ignorowana, jeśli nie `--passive` określono żadnego ani `--quiet` .  |
| `--nickname <name>` | **Opcjonalnie**: definiuje pseudonim do przypisania do zainstalowanego produktu. Pseudonim nie może być dłuższy niż 10 znaków.  |
| `--productKey` | **Opcjonalnie**: definiuje klucz produktu do użycia w przypadku zainstalowanego produktu. Składa się z 25 znaków alfanumerycznych w formacie `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` lub `xxxxxxxxxxxxxxxxxxxxxxxxx` . |
| `--help, --?, -h, -?` | Wyświetl wersję offline tej strony. |
| `--config <path>` | **Opcjonalne**: podczas operacji instalacji lub modyfikacji program określa obciążenia i składniki do dodania na podstawie wcześniej zapisanego pliku konfiguracji instalacji. Ta operacja jest dodatkiem i nie usuwa żadnego obciążenia ani składnika, jeśli nie znajdują się w pliku. Ponadto elementy, które nie mają zastosowania do produktu, nie zostaną dodane. Podczas operacji eksportowania Określa lokalizację, w której ma zostać zapisany plik konfiguracji instalacji. |

::: moniker-end

> [!IMPORTANT]
> Podczas określania wielu obciążeń i składników należy powtórzyć `--add` `--remove` przełącznik wiersza polecenia lub dla każdego elementu.

## <a name="layout-options"></a>Opcje układu

::: moniker range="vs-2017"

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog, w którym ma zostać utworzona pamięć podręczna instalacji w trybie offline. Aby uzyskać więcej informacji, zobacz [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalne**: służy `--layout` do przygotowywania pamięci podręcznej instalacji w trybie offline z pakietami zasobów z określonymi językami. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [listy ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalne**: co najmniej jeden identyfikator obciążenia lub składnika do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie są to zalecane ani opcjonalne składniki. Dodatkowe składniki można kontrolować globalnie przy użyciu `--includeRecommended` i/lub `--includeOptional` . Aby uzyskać dokładniejszą kontrolę, można dołączyć `;includeRecommended` lub `;includeOptional` do identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional` ). Aby uzyskać więcej informacji, zobacz stronę [obciążenia i identyfikatory składników](workload-and-component-ids.md) . <br/>**Uwaga**: Jeśli `--add` jest używany, pobierane są tylko określone obciążenia i składniki oraz ich zależności. Jeśli `--add` nie zostanie określony, wszystkie obciążenia i składniki są pobierane do układu.|
| `--includeRecommended` | **Opcjonalne**: zawiera zalecane składniki dla wszelkich obciążeń, które są zainstalowane, ale nie opcjonalne składniki. Obciążenia są określane przy użyciu `--allWorkloads` lub `--add` . |
| `--includeOptional` | **Opcjonalne**: zawiera zalecane *i* opcjonalne składniki dla wszelkich obciążeń uwzględnionych w układzie. Obciążenia są określane przy użyciu `--add` .  |
| `--keepLayoutVersion` | **Nowość w 15,3, opcjonalnie**: Zastosuj zmiany do układu bez aktualizowania wersji układu. |
| `--verify` | **Nowość w 15,3, opcjonalnie**: Sprawdź zawartość układu. Wyświetlane są wszystkie uszkodzone lub brakujące pliki. |
| `--fix` | **Nowość w 15,3, opcjonalnie**: Sprawdź zawartość układu. Jeśli pliki są uszkodzone lub ich brakuje, są one pobierane. Do naprawienia układu wymagany jest dostęp do Internetu. |
| `--clean <one or more paths to catalogs>` | **Nowość w 15,3, opcjonalne**: usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Zaawansowane opcje instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalnie**: Identyfikator kanału dla wystąpienia, które ma zostać zainstalowane. Jest to wymagane przez polecenie instalacji i ignorowane dla innych poleceń, jeśli `--installPath` jest określony. |
| `--channelUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu kanału. Jeśli aktualizacje nie są potrzebne, `--channelUri` mogą wskazywać na nieistniejący plik (na przykład--identyfikator channeluri C:\doesntExist.Chman). Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu kanału do użycia podczas instalacji. Identyfikator URI określony przez `--channelUri` (który musi być określony, jeśli `--installChannelUri` jest określony) służy do wykrywania aktualizacji. Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu wykazu do użycia podczas instalacji. Jeśli ta wartość jest określona, Menedżer kanałów próbuje pobrać manifest wykazu z tego identyfikatora URI przed użyciem identyfikatora URI w manifeście kanału instalacji. Ten parametr służy do obsługi instalacji w trybie offline, gdzie pamięć podręczna układu zostanie utworzona przy użyciu już pobranego katalogu produktów. Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--productId <id>` | **Opcjonalne** Identyfikator produktu dla wystąpienia, które zostanie zainstalowane. Jest to wstępne wypełnienie w normalnych warunkach instalacji. |
| `--wait` | **Opcjonalnie**: proces będzie oczekiwać do momentu zakończenia instalacji przed zwróceniem kodu zakończenia. Jest to przydatne w przypadku automatyzowania instalacji, w których należy poczekać na zakończenie instalacji, aby obsłużyć kod powrotny z tej instalacji. |
| `--locale <language-locale>` | **Opcjonalne**: Zmień język wyświetlania interfejsu użytkownika dla samego Instalatora. Ustawienie zostanie utrwalone. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [listy ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--cache` | **Nowość w 15,2, opcjonalnie**: Jeśli jest obecny, pakiety będą przechowywane po zainstalowaniu do kolejnych napraw. Zastępuje globalne ustawienie zasad, które będzie używane do kolejnych instalacji, napraw lub modyfikacji. Domyślną zasadą jest buforowanie pakietów. Ta wartość jest ignorowana dla polecenia Uninstall. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietów,](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--nocache` | **Nowość w 15,2, opcjonalnie**: Jeśli jest obecny, pakiety zostaną usunięte po zainstalowaniu lub naprawieniu. Zostaną one pobrane ponownie tylko w razie konieczności i usunięte ponownie po użyciu. Zastępuje globalne ustawienie zasad, które będzie używane do kolejnych instalacji, napraw lub modyfikacji. Domyślną zasadą jest buforowanie pakietów. Ta wartość jest ignorowana dla polecenia Uninstall. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietów,](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Nowość w 15,2, opcjonalnie**: Jeśli jest obecny, zapobiega aktualizacji samego Instalatora po określeniu cichym. Instalator nie będzie mógł wykonać polecenia i zwróci niezerowy kod zakończenia, jeśli noUpdateInstaller jest określony z cichym, gdy wymagana jest aktualizacja Instalatora. |
| `--noWeb` | **Nowość w 15,3, opcjonalnie**: Jeśli jest obecny, Instalator programu Visual Studio używa plików z katalogu układu do zainstalowania programu Visual Studio. Jeśli użytkownik spróbuje zainstalować składniki, które nie znajdują się w układzie, instalacja nie powiedzie się.  Aby uzyskać więcej informacji, zobacz [wdrażanie z poziomu instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne**: ten przełącznik nie zatrzymuje sprawdzania dostępności aktualizacji przez Instalatora programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Kontrolowanie aktualizacji dla wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Nowość w 15,7, opcjonalnie**: służy do określania niestandardowych ścieżek instalacji dla instalacji. Obsługiwane nazwy ścieżek są udostępniane, pamięci podręcznej i instalują. |
| `--path cache=<path>` | **Nowość w 15,7, opcjonalnie**: używa określonej lokalizacji do pobrania plików instalacyjnych. Tę lokalizację można ustawić tylko podczas pierwszego zainstalowania programu Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nowość w 15,7, opcjonalnie**: zawiera pliki udostępnione do instalacji obok siebie programu Visual Studio. Niektóre narzędzia i zestawy SDK są instalowane w lokalizacji na tym dysku, a niektóre inne mogą zastąpić to ustawienie i zainstalować je na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: to ustawienie można ustawić tylko raz i po raz pierwszy, gdy program Visual Studio jest zainstalowany. |
| `--path install=<path>` | **Nowość w 15,7, opcjonalnie**: odpowiednik `–-installPath` . W `--installPath "C:\VS"` `--path install="C:\VS"` odróżnieniu od siebie i są równoważne. Można używać tylko jednego z tych poleceń jednocześnie. |

::: moniker-end

::: moniker range="vs-2019"

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog, w którym ma zostać utworzona pamięć podręczna instalacji w trybie offline. Aby uzyskać więcej informacji, zobacz [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalne**: służy `--layout` do przygotowywania pamięci podręcznej instalacji w trybie offline z pakietami zasobów z określonymi językami. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [listy ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalne**: co najmniej jeden identyfikator obciążenia lub składnika do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie są to zalecane ani opcjonalne składniki. Dodatkowe składniki można kontrolować globalnie przy użyciu `--includeRecommended` i/lub `--includeOptional` . Aby uzyskać dokładniejszą kontrolę, można dołączyć `;includeRecommended` lub `;includeOptional` do identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional` ). Aby uzyskać więcej informacji, zobacz stronę [obciążenia i identyfikatory składników](workload-and-component-ids.md) . <br/>**Uwaga**: Jeśli `--add` jest używany, pobierane są tylko określone obciążenia i składniki oraz ich zależności. Jeśli `--add` nie zostanie określony, wszystkie obciążenia i składniki są pobierane do układu.|
| `--includeRecommended` | **Opcjonalne**: zawiera zalecane składniki dla wszelkich obciążeń, które są zainstalowane, ale nie opcjonalne składniki. Obciążenia są określane przy użyciu `--allWorkloads` lub `--add` . |
| `--includeOptional` | **Opcjonalne**: zawiera zalecane *i* opcjonalne składniki dla wszelkich obciążeń uwzględnionych w układzie. Obciążenia są określane przy użyciu `--add` .  |
| `--keepLayoutVersion` | **Opcjonalne**: Zastosuj zmiany do układu bez aktualizowania wersji układu. |
| `--verify` | **Opcjonalne**: Sprawdź zawartość układu. Wyświetlane są wszystkie uszkodzone lub brakujące pliki. |
| `--fix` | **Opcjonalne**: Sprawdź zawartość układu.  Jeśli pliki są uszkodzone lub ich brakuje, są one pobierane. Do naprawienia układu wymagany jest dostęp do Internetu. |
| `--clean <one or more paths to catalogs>` | **Opcjonalne**: usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Zaawansowane opcje instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalnie**: Identyfikator kanału dla wystąpienia, które ma zostać zainstalowane. Jest to wymagane przez polecenie instalacji i ignorowane dla innych poleceń, jeśli `--installPath` jest określony. |
| `--channelUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu kanału. Jeśli aktualizacje nie są potrzebne, `--channelUri` mogą wskazywać na nieistniejący plik (na przykład--identyfikator channeluri C:\doesntExist.Chman). Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu kanału do użycia podczas instalacji. Identyfikator URI określony przez `--channelUri` (który musi być określony, jeśli `--installChannelUri` jest określony) służy do wykrywania aktualizacji. Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalnie**: identyfikator URI manifestu wykazu do użycia podczas instalacji. Jeśli ta wartość jest określona, Menedżer kanałów próbuje pobrać manifest wykazu z tego identyfikatora URI przed użyciem identyfikatora URI w manifeście kanału instalacji. Ten parametr służy do obsługi instalacji w trybie offline, gdzie pamięć podręczna układu zostanie utworzona przy użyciu już pobranego katalogu produktów. Ta wartość może być używana w przypadku polecenia install; jest on ignorowany dla innych poleceń. |
| `--productId <id>` | **Opcjonalne** Identyfikator produktu dla wystąpienia, które zostanie zainstalowane. Jest to wstępne wypełnienie w normalnych warunkach instalacji. |
| `--wait` | **Opcjonalnie**: proces będzie oczekiwać do momentu zakończenia instalacji przed zwróceniem kodu zakończenia. Jest to przydatne w przypadku automatyzowania instalacji, w których należy poczekać na zakończenie instalacji, aby obsłużyć kod powrotny z tej instalacji. |
| `--locale <language-locale>` | **Opcjonalne**: Zmień język wyświetlania interfejsu użytkownika dla samego Instalatora. Ustawienie zostanie utrwalone. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [listy ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--cache` | **Opcjonalnie**: Jeśli jest obecny, pakiety będą przechowywane po zainstalowaniu do kolejnych napraw. Zastępuje globalne ustawienie zasad, które będzie używane do kolejnych instalacji, napraw lub modyfikacji. Domyślną zasadą jest buforowanie pakietów. Ta wartość jest ignorowana dla polecenia Uninstall. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietów,](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--nocache` | **Opcjonalnie**: Jeśli jest obecny, pakiety zostaną usunięte po zainstalowaniu lub naprawieniu. Zostaną one pobrane ponownie tylko w razie konieczności i usunięte ponownie po użyciu. Zastępuje globalne ustawienie zasad, które będzie używane do kolejnych instalacji, napraw lub modyfikacji. Domyślną zasadą jest buforowanie pakietów. Ta wartość jest ignorowana dla polecenia Uninstall. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietów,](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Opcjonalnie**: Jeśli jest obecny, zapobiega aktualizacji samego Instalatora po określeniu cichym. Instalator nie będzie mógł wykonać polecenia i zwróci niezerowy kod zakończenia, jeśli noUpdateInstaller jest określony z cichym, gdy wymagana jest aktualizacja Instalatora. |
| `--noWeb` | **Opcjonalnie**: Jeśli jest obecny, Instalator programu Visual Studio używa plików w katalogu układu do instalowania programu Visual Studio. Jeśli użytkownik spróbuje zainstalować składniki, które nie znajdują się w układzie, instalacja nie powiedzie się.  Aby uzyskać więcej informacji, zobacz [wdrażanie z poziomu instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne**: ten przełącznik nie zatrzymuje sprawdzania dostępności aktualizacji przez Instalatora programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Kontrolowanie aktualizacji dla wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md). **Nowość w 16.3.5**: ten przełącznik uniemożliwia błędy i poprawia wydajność przy użyciu instalacji i aktualizacji w trybie offline.|
| `--path <name>=<path>` | **Opcjonalne**: służy do określania niestandardowych ścieżek instalacji dla instalacji. Obsługiwane nazwy ścieżek są udostępniane, pamięci podręcznej i instalują. |
| `--path cache=<path>` | **Opcjonalnie**: używa określonej lokalizacji do pobrania plików instalacyjnych. Tę lokalizację można ustawić tylko podczas pierwszego zainstalowania programu Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Opcjonalne**: zawiera udostępnione pliki do instalacji obok siebie w programie Visual Studio. Niektóre narzędzia i zestawy SDK są instalowane w lokalizacji na tym dysku, a niektóre inne mogą zastąpić to ustawienie i zainstalować je na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: to ustawienie można ustawić tylko raz i po raz pierwszy, gdy program Visual Studio jest zainstalowany. |
| `--path install=<path>` | **Opcjonalne**: równoważne `–-installPath` . W `--installPath "C:\VS"` `--path install="C:\VS"` odróżnieniu od siebie i są równoważne. Można używać tylko jednego z tych poleceń jednocześnie. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Lista identyfikatorów obciążeń i identyfikatorów składników

Aby uzyskać listę identyfikatorów obciążeń i składników posortowanych przez program Visual Studio, zobacz stronę [obciążenia i identyfikatory składników programu Visual Studio](workload-and-component-ids.md) .

## <a name="list-of-language-locales"></a>Lista ustawień regionalnych języka

| **Język — ustawienia regionalne** | **Język** |
| ----------------------- | --------------- |
| Cs — cz | Czeski |
| De-de | Niemiecki |
| Pl-US | Angielski |
| ES-es | Hiszpański |
| Fr — fr | Francuski |
| IT | Włoski |
| Ja-JP | japoński |
| Ko — kr | Koreański |
| Pl-pl | Polski |
| Pt-br | Portugalski (Brazylia) |
| Ru — RU | Rosyjski |
| TR-tr | Turecki |
| Zh-CN | Chiński – uproszczony |
| Zh-tw | Chiński – tradycyjny |

## <a name="error-codes"></a>Kody błędów

W zależności od wyniku operacji `%ERRORLEVEL%` zmienna środowiskowa jest ustawiana na jedną z następujących wartości:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Każda operacja generuje kilka plików dziennika w `%TEMP%` katalogu, które wskazują postęp instalacji. Posortuj folder według daty i Wyszukaj pliki, które zaczynają się od `dd_bootstrapper` , `dd_client` i `dd_setup` odpowiednio do programu inicjującego, aplikacji Instalatora i aparatu instalacji.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Przykłady parametrów wiersza polecenia dla instalacji programu Visual Studio](command-line-parameter-examples.md)
- [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Zautomatyzowana instalacja programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)

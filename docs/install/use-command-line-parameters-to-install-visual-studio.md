---
title: Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak używać parametrów wiersza polecenia do kontrolowania lub dostosowywania instalacji programu Visual Studio.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114357"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio

Podczas instalowania programu Visual Studio z wiersza polecenia można użyć różnych parametrów wiersza polecenia do kontrolowania lub dostosowywania instalacji. Z wiersza polecenia można wykonać następujące czynności:

- Rozpocznij instalację z wybranymi opcjami.
- Zautomatyzuj proces instalacji.
- Utwórz pamięć podręczną (układ) plików instalacyjnych do późniejszego użycia.

Opcje wiersza polecenia są używane w połączeniu z programem inicjowania konfiguracji, który jest małym plikiem (1 MB), który inicjuje proces pobierania. Program inichowany jest pierwszym plikiem wykonywalnym, który jest uruchamiany podczas pobierania z witryny programu Visual Studio.

::: moniker range="vs-2017"

Aby uzyskać program uruchamiany dla programu Visual Studio 2017, zobacz stronę pobierania [**poprzednich wersji programu Visual Studio,**](https://visualstudio.microsoft.com/vs/older-downloads/) aby uzyskać szczegółowe informacje na ten temat.

::: moniker-end

::: moniker range="vs-2019"

Skorzystaj z następujących linków, aby uzyskać bezpośredni link do najnowszego programu inikusującego dla instalowanej wersji produktu:

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Społeczność programu Visual Studio 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


Plik bootstrapper powinien być zgodny lub podobny do jednej z następujących nazw plików:

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>Jeśli wcześniej pobrano plik boottrappera i chcesz zweryfikować jego wersję, oto jak to zrobić. W systemie Windows otwórz Eksploratora plików, kliknij prawym przyciskiem myszy plik programu inikuscyjny, wybierz polecenie **Właściwości**, wybierz kartę **Szczegóły,** a następnie wyświetl numer **wersji produktu.** Aby dopasować tę liczbę do wersji programu Visual Studio, zobacz [numery kompilacji programu Visual Studio i daty wydania](visual-studio-build-numbers-and-release-dates.md) strony.

## <a name="command-line-parameters"></a>Parametry wiersza polecenia

 Parametry wiersza polecenia programu Visual Studio są niewrażliwe na wielkości liter.

> Składni:`vs_enterprise.exe [command] <options>...`

Wymień `vs_enterprise.exe` odpowiednio wersję produktu, którą instalujesz. (Alternatywnie można użyć `vs_installer.exe`.)

>[!TIP]
> Aby uzyskać więcej przykładów użycia wiersza polecenia do zainstalowania programu Visual Studio, zobacz [przykłady parametrów wiersza polecenia.](command-line-parameter-examples.md)

::: moniker range="vs-2017"

| **Polecenie** | **Opis** |
| ----------------------- | --------------- |
| (puste) | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | **Nowość w wersji 15.9**: Eksportuje wybór instalacji do pliku konfiguracji instalacji. **Uwaga:** Może być używany tylko z vs_installer.exe. |

::: moniker-end

::: moniker range="vs-2019"

| **Polecenie** | **Opis** |
| ----------------------- | --------------- |
| (puste) | Instaluje produkt. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | Eksportuje wybór instalacji do pliku konfiguracji instalacji. **Uwaga:** Może być używany tylko z vs_installer.exe. |

::: moniker-end

## <a name="install-options"></a>Opcje instalacji

::: moniker range="vs-2017"

| **Opcja instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalog instalacji dla wystąpienia do działania. Dla polecenia install jest to **opcjonalne** i jest, gdzie wystąpienie zostanie zainstalowane. W przypadku innych poleceń jest to **wymagane** i jest to miejsce, w którym zainstalowano wcześniej zainstalowane wystąpienie. |
| `--addProductLang <language-locale>` | **Opcjonalnie:** Podczas operacji instalacji lub modyfikowania określa pakiety językowe interfejsu użytkownika, które są zainstalowane w produkcie. Może pojawić się wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie jest obecny, instalacja używa ustawień regionalnych urządzenia. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalnie:** Podczas operacji instalacji lub modyfikowania określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Może pojawić się wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie:** Co najmniej jedno obciążenie lub identyfikatory składników do dodania. Zainstalowane są wymagane składniki artefaktu, ale nie są to składniki zalecane lub opcjonalne. Można sterować dodatkowymi `--includeRecommended` komponentami `--includeOptional`globalnie za pomocą i/lub . Aby uwzględnić wiele obciążeń lub `--add` składników, powtórz `--add Workload1 --add Workload2`polecenie (na przykład ). W przypadku formantu z drobniejszymi ziarnistymi można `;includeRecommended` dołączyć lub `;includeOptional` do identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenie i identyfikatory składników](workload-and-component-ids.md) strony. W razie potrzeby można powtórzyć tę opcję.|
| `--remove <one or more workload or component IDs>` | **Opcjonalnie:** Co najmniej jedno obciążenie lub identyfikatory składników do usunięcia. Aby uzyskać więcej informacji, zobacz naszą stronę [Obciążenia i identyfikatory składników.](workload-and-component-ids.md) W razie potrzeby można powtórzyć tę opcję.|
| `--in <path>` | **Opcjonalnie**: Identyfikator URI lub ścieżka do pliku odpowiedzi.  |
| `--all` | **Opcjonalnie:** Czy zainstalować wszystkie obciążenia i składniki dla produktu. |
| `--allWorkloads` | **Opcjonalnie:** Instaluje wszystkie obciążenia i składniki, bez zalecanych lub opcjonalnych składników. |
| `--includeRecommended` | **Opcjonalnie:** Zawiera zalecane składniki dla wszystkich obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określone za `--allWorkloads` pomocą `--add`lub . |
| `--includeOptional` | **Opcjonalnie:** Zawiera składniki opcjonalne dla wszystkich obciążeń, które są zainstalowane, ale nie zalecane składniki. Obciążenia są określone za `--allWorkloads` pomocą `--add`lub .  |
| `--quiet, -q` | **Opcjonalnie:** Nie wyświetlaj żadnego interfejsu użytkownika podczas instalacji. |
| `--passive, -p` | **Opcjonalnie:** Wyświetla interfejs użytkownika, ale nie żądaj żadnej interakcji od użytkownika. |
| `--norestart` | **Opcjonalnie:** Jeśli jest `--passive` obecny, polecenia z lub `--quiet` nie automatycznie ponownie uruchomić komputer (jeśli to konieczne).  Jest to ignorowane, `--passive` `--quiet` jeśli ani nie są określone.  |
| `--nickname <name>` | **Opcjonalnie**: Definiuje pseudonim przypisywany do zainstalowanego produktu. Pseudonim nie może być dłuższy niż 10 znaków.  |
| `--productKey` | **Opcjonalnie:** Definiuje klucz produktu używany dla zainstalowanego produktu. Składa się z 25 znaków alfanumeryczne w `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx`formacie lub . |
| `--help, --?, -h, -?` | Wyświetl wersję tej strony w trybie offline. |
| `--config <path>` | **Opcjonalne** i **nowe w 15.9**: Podczas operacji instalacji lub modyfikowania określa obciążenia i składniki do dodania na podstawie wcześniej zapisanego pliku konfiguracji instalacji. Ta operacja jest addytywny i nie usunie żadnego obciążenia lub składnika, jeśli nie są one obecne w pliku. Ponadto elementy, które nie mają zastosowania do produktu, nie zostaną dodane. Podczas operacji eksportowania określa lokalizację zapisywania pliku konfiguracji instalacji. |

::: moniker-end

::: moniker range="vs-2019"

| **Opcja instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Katalog instalacji dla wystąpienia do działania. Dla polecenia install jest to **opcjonalne** i jest, gdzie wystąpienie zostanie zainstalowane. W przypadku innych poleceń jest to **wymagane** i jest to miejsce, w którym zainstalowano wcześniej zainstalowane wystąpienie. |
| `--addProductLang <language-locale>` | **Opcjonalnie:** Podczas operacji instalacji lub modyfikowania określa pakiety językowe interfejsu użytkownika, które są zainstalowane w produkcie. Może pojawić się wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Jeśli nie jest obecny, instalacja używa ustawień regionalnych urządzenia. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalnie:** Podczas operacji instalacji lub modyfikowania określa pakiety językowe interfejsu użytkownika, które mają zostać usunięte z produktu. Może pojawić się wiele razy w wierszu polecenia, aby dodać wiele pakietów językowych. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie:** Co najmniej jedno obciążenie lub identyfikatory składników do dodania. Zainstalowane są wymagane składniki artefaktu, ale nie są to składniki zalecane lub opcjonalne. Można sterować dodatkowymi `--includeRecommended` komponentami `--includeOptional`globalnie za pomocą i/lub . Aby uwzględnić wiele obciążeń lub `--add` składników, powtórz `--add Workload1 --add Workload2`polecenie (na przykład ). W przypadku formantu z drobniejszymi ziarnistymi można `;includeRecommended` dołączyć lub `;includeOptional` do identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeRecommended;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenie i identyfikatory składników](workload-and-component-ids.md) strony. W razie potrzeby można powtórzyć tę opcję.|
| `--remove <one or more workload or component IDs>` | **Opcjonalnie:** Co najmniej jedno obciążenie lub identyfikatory składników do usunięcia. Aby uzyskać więcej informacji, zobacz naszą stronę [Obciążenia i identyfikatory składników.](workload-and-component-ids.md) W razie potrzeby można powtórzyć tę opcję.|
| `--in <path>` | **Opcjonalnie**: Identyfikator URI lub ścieżka do pliku odpowiedzi.  |
| `--all` | **Opcjonalnie:** Czy zainstalować wszystkie obciążenia i składniki dla produktu. |
| `--allWorkloads` | **Opcjonalnie:** Instaluje wszystkie obciążenia i składniki, bez zalecanych lub opcjonalnych składników. |
| `--includeRecommended` | **Opcjonalnie:** Zawiera zalecane składniki dla wszystkich obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określone za `--allWorkloads` pomocą `--add`lub . |
| `--includeOptional` | **Opcjonalnie:** Zawiera składniki opcjonalne dla wszystkich obciążeń, które są zainstalowane, ale nie zalecane składniki. Obciążenia są określone za `--allWorkloads` pomocą `--add`lub .  |
| `--quiet, -q` | **Opcjonalnie:** Nie wyświetlaj żadnego interfejsu użytkownika podczas instalacji. |
| `--passive, -p` | **Opcjonalnie:** Wyświetla interfejs użytkownika, ale nie żądaj żadnej interakcji od użytkownika. |
| `--norestart` | **Opcjonalnie:** Jeśli jest `--passive` obecny, polecenia z lub `--quiet` nie automatycznie ponownie uruchomić komputer (jeśli to konieczne).  Jest to ignorowane, `--passive` `--quiet` jeśli ani nie są określone.  |
| `--nickname <name>` | **Opcjonalnie**: Definiuje pseudonim przypisywany do zainstalowanego produktu. Pseudonim nie może być dłuższy niż 10 znaków.  |
| `--productKey` | **Opcjonalnie:** Definiuje klucz produktu używany dla zainstalowanego produktu. Składa się z 25 znaków alfanumeryczne w `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx`formacie lub . |
| `--help, --?, -h, -?` | Wyświetl wersję tej strony w trybie offline. |
| `--config <path>` | **Opcjonalnie:** Podczas operacji instalacji lub modyfikowania określa to obciążenia i składniki do dodania na podstawie wcześniej zapisanego pliku konfiguracji instalacji. Ta operacja jest addytywny i nie usunie żadnego obciążenia lub składnika, jeśli nie są one obecne w pliku. Ponadto elementy, które nie mają zastosowania do produktu, nie zostaną dodane. Podczas operacji eksportowania określa lokalizację zapisywania pliku konfiguracji instalacji. |

::: moniker-end

> [!IMPORTANT]
> Określając wiele obciążeń i składników, należy `--add` powtórzyć `--remove` przełącznik wiersza polecenia lub dla każdego elementu.

## <a name="layout-options"></a>Opcje układu

::: moniker range="vs-2017"

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog do utworzenia pamięci podręcznej instalacji w trybie offline. Aby uzyskać więcej informacji, zobacz [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalnie:** `--layout` Służy do przygotowania pamięci podręcznej instalacji w trybie offline z pakietami zasobów o określonym języku. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie:** Co najmniej jedno obciążenie lub identyfikatory składników do dodania. Zainstalowane są wymagane składniki artefaktu, ale nie są to składniki zalecane lub opcjonalne. Można sterować dodatkowymi `--includeRecommended` komponentami `--includeOptional`globalnie za pomocą i/lub . W przypadku formantu z drobniejszymi ziarnistymi można `;includeRecommended` dołączyć lub `;includeOptional` do identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenie i identyfikatory składników](workload-and-component-ids.md) strony. <br/>**Uwaga:** `--add` Jeśli jest używany, pobierane są tylko określone obciążenia i składniki oraz ich zależności. Jeśli `--add` nie jest określony, wszystkie obciążenia i składniki są pobierane do układu.|
| `--includeRecommended` | **Opcjonalnie:** Zawiera zalecane składniki dla wszystkich obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określone za `--allWorkloads` pomocą `--add`lub . |
| `--includeOptional` | **Opcjonalnie:** Zawiera zalecane *i* opcjonalne składniki dla wszystkich obciążeń uwzględnionych w układzie. Obciążenia są określone `--add`za pomocą .  |
| `--keepLayoutVersion` | **Nowość w wersji 15.3, opcjonalnie:** Zastosuj zmiany w układzie bez aktualizowania wersji układu. |
| `--verify` | **Nowość w 15.3, opcjonalnie:** Sprawdź zawartość układu. Zostaną wyświetlone uszkodzone lub brakujące pliki. |
| `--fix` | **Nowość w 15.3, opcjonalnie:** Sprawdź zawartość układu. Jeśli jakiekolwiek pliki są uszkodzone lub brakuje, są one ponownie pobrać. Aby naprawić układ, wymagany jest dostęp do Internetu. |
| `--clean <one or more paths to catalogs>` | **Nowość w wersji 15.3, opcjonalna:** Usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Zaawansowane opcje instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalnie**: Identyfikator kanału dla wystąpienia, które ma zostać zainstalowane. Jest to wymagane dla polecenia install i ignorowane `--installPath` dla innych poleceń, jeśli jest określony. |
| `--channelUri <uri>` | **Opcjonalnie:** Identyfikator URI manifestu kanału. Jeśli aktualizacje nie `--channelUri` są pożądane, można wskazać nieistniejący plik (na przykład --channelUri C:\doesntExist.chman). Może to być używane dla polecenia install; jest ignorowany dla innych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalnie:** Identyfikator URI manifestu kanału do użycia w instalacji. Identyfikator URI `--channelUri` określony przez (który `--installChannelUri` musi być określony, gdy jest określony) jest używany do wykrywania aktualizacji. Może to być używane dla polecenia install; jest ignorowany dla innych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalnie:** Identyfikator URI manifestu katalogu do użycia w instalacji. Jeśli określono, menedżer kanału próbuje pobrać manifest katalogu z tego identyfikatora URI przed użyciem identyfikatora URI w manifeście kanału instalacyjnego. Ten parametr jest używany do obsługi instalacji w trybie offline, gdzie zostanie utworzona pamięć podręczna układu z już pobranym katalogiem produktów. Może to być używane dla polecenia install; jest ignorowany dla innych poleceń. |
| `--productId <id>` | **Opcjonalnie** Identyfikator produktu dla wystąpienia, które zostanie zainstalowane. Jest to wstępnie wypełnione w normalnych warunkach instalacji. |
| `--wait` | **Opcjonalnie:** Proces będzie czekać, aż instalacja zostanie zakończona przed zwróceniem kodu zakończenia. Jest to przydatne podczas automatyzacji instalacji, w których trzeba czekać na zakończenie instalacji, aby obsłużyć kod zwrotny z tej instalacji. |
| `--locale <language-locale>` | **Opcjonalnie**: Zmień język wyświetlania interfejsu użytkownika dla samego instalatora. Ustawienie będzie zachowywane. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--cache` | **Nowość w 15.2, opcjonalnie**: Jeśli jest obecna, pakiety będą przechowywane po zainstalowaniu do kolejnych napraw. Zastępuje to globalne ustawienie zasad, które ma być używane do kolejnych instalacji, napraw lub modyfikacji. Domyślną zasadą jest buforowanie pakietów. Jest to ignorowane dla polecenia odinstalowywania. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietu,](disable-or-move-the-package-cache.md) aby uzyskać więcej informacji. |
| `--nocache` | **Nowość w 15.2, opcjonalnie**: Jeśli jest obecna, pakiety zostaną usunięte po zainstalowaniu lub naprawie. Zostaną one pobrane ponownie tylko wtedy, gdy jest to konieczne i usunięte ponownie po użyciu. Zastępuje to globalne ustawienie zasad, które ma być używane do kolejnych instalacji, napraw lub modyfikacji. Domyślną zasadą jest buforowanie pakietów. Jest to ignorowane dla polecenia odinstalowywania. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietu,](disable-or-move-the-package-cache.md) aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Nowość w 15.2, opcjonalnie:** Jeśli jest obecna, uniemożliwia instalatorowi aktualizację, gdy określono ciszę. Instalator nie powiodą się polecenie i zwróci kod zakończenia niezerowy, jeśli noUpdateInstaller jest określony z cichą, gdy wymagana jest aktualizacja instalatora. |
| `--noWeb` | **Nowość w wersji 15.3, opcjonalnie:** Jeśli jest obecna, instalator programu Visual Studio używa plików w katalogu układu do zainstalowania programu Visual Studio. Jeśli użytkownik próbuje zainstalować składniki, które nie są w układzie, instalacja kończy się niepowodzeniem.  Aby uzyskać więcej informacji, zobacz [Wdrażanie z instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne:** Ten przełącznik nie uniemożliwia konfiguracji programu Visual Studio sprawdzania dostępności aktualizacji. Aby uzyskać więcej informacji, zobacz [Aktualizacje sterowania wdrożeniami programu Visual Studio opartymi na sieci.](controlling-updates-to-visual-studio-deployments.md) |
| `--path <name>=<path>` | **Nowy w 15.7, opcjonalnie:** Służy do określania niestandardowych ścieżek instalacji dla instalacji. Obsługiwane nazwy ścieżek są współużytkowane, buforowane i instalowane. |
| `--path cache=<path>` | **Nowość w 15.7, opcjonalnie:** Używa określonej lokalizacji do pobierania plików instalacyjnych. Tę lokalizację można ustawić tylko przy pierwszym zainstalowaniu programu Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Nowość w wersji 15.7, opcjonalna:** Zawiera udostępnione pliki dla instalacji programu Visual Studio side-by-side. Niektóre narzędzia i zestawY SDK instalują się w lokalizacji na tym dysku, podczas gdy inne mogą zastąpić to ustawienie i zainstalować na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: To można ustawić tylko raz i po raz pierwszy, że program Visual Studio jest zainstalowany. |
| `--path install=<path>` | **Nowość w 15.7, opcjonalnie:** Odpowiednik `–-installPath`. W szczególności `--installPath "C:\VS"` `--path install="C:\VS"` i są równoważne. Jednocześnie można użyć tylko jednego z tych poleceń. |

::: moniker-end

::: moniker range="vs-2019"

| **Opcje układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog do utworzenia pamięci podręcznej instalacji w trybie offline. Aby uzyskać więcej informacji, zobacz [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcjonalnie:** `--layout` Służy do przygotowania pamięci podręcznej instalacji w trybie offline z pakietami zasobów o określonym języku. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie:** Co najmniej jedno obciążenie lub identyfikatory składników do dodania. Zainstalowane są wymagane składniki artefaktu, ale nie są to składniki zalecane lub opcjonalne. Można sterować dodatkowymi `--includeRecommended` komponentami `--includeOptional`globalnie za pomocą i/lub . W przypadku formantu z drobniejszymi ziarnistymi można `;includeRecommended` dołączyć lub `;includeOptional` do identyfikatora (na przykład `--add Workload1;includeRecommended` lub `--add Workload2;includeOptional`). Aby uzyskać więcej informacji, zobacz [obciążenie i identyfikatory składników](workload-and-component-ids.md) strony. <br/>**Uwaga:** `--add` Jeśli jest używany, pobierane są tylko określone obciążenia i składniki oraz ich zależności. Jeśli `--add` nie jest określony, wszystkie obciążenia i składniki są pobierane do układu.|
| `--includeRecommended` | **Opcjonalnie:** Zawiera zalecane składniki dla wszystkich obciążeń, które są zainstalowane, ale nie składniki opcjonalne. Obciążenia są określone za `--allWorkloads` pomocą `--add`lub . |
| `--includeOptional` | **Opcjonalnie:** Zawiera zalecane *i* opcjonalne składniki dla wszystkich obciążeń uwzględnionych w układzie. Obciążenia są określone `--add`za pomocą .  |
| `--keepLayoutVersion` | **Opcjonalnie**: Zastosuj zmiany do układu bez aktualizowania wersji układu. |
| `--verify` | **Opcjonalnie**: Sprawdź zawartość układu. Zostaną wyświetlone uszkodzone lub brakujące pliki. |
| `--fix` | **Opcjonalnie**: Sprawdź zawartość układu.  Jeśli jakiekolwiek pliki są uszkodzone lub brakuje, są one ponownie pobrać. Aby naprawić układ, wymagany jest dostęp do Internetu. |
| `--clean <one or more paths to catalogs>` | **Opcjonalnie:** Usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Zaawansowane opcje instalacji** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalnie**: Identyfikator kanału dla wystąpienia, które ma zostać zainstalowane. Jest to wymagane dla polecenia install i ignorowane `--installPath` dla innych poleceń, jeśli jest określony. |
| `--channelUri <uri>` | **Opcjonalnie:** Identyfikator URI manifestu kanału. Jeśli aktualizacje nie `--channelUri` są pożądane, można wskazać nieistniejący plik (na przykład --channelUri C:\doesntExist.chman). Może to być używane dla polecenia install; jest ignorowany dla innych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalnie:** Identyfikator URI manifestu kanału do użycia w instalacji. Identyfikator URI `--channelUri` określony przez (który `--installChannelUri` musi być określony, gdy jest określony) jest używany do wykrywania aktualizacji. Może to być używane dla polecenia install; jest ignorowany dla innych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalnie:** Identyfikator URI manifestu katalogu do użycia w instalacji. Jeśli określono, menedżer kanału próbuje pobrać manifest katalogu z tego identyfikatora URI przed użyciem identyfikatora URI w manifeście kanału instalacyjnego. Ten parametr jest używany do obsługi instalacji w trybie offline, gdzie zostanie utworzona pamięć podręczna układu z już pobranym katalogiem produktów. Może to być używane dla polecenia install; jest ignorowany dla innych poleceń. |
| `--productId <id>` | **Opcjonalnie** Identyfikator produktu dla wystąpienia, które zostanie zainstalowane. Jest to wstępnie wypełnione w normalnych warunkach instalacji. |
| `--wait` | **Opcjonalnie:** Proces będzie czekać, aż instalacja zostanie zakończona przed zwróceniem kodu zakończenia. Jest to przydatne podczas automatyzacji instalacji, w których trzeba czekać na zakończenie instalacji, aby obsłużyć kod zwrotny z tej instalacji. |
| `--locale <language-locale>` | **Opcjonalnie**: Zmień język wyświetlania interfejsu użytkownika dla samego instalatora. Ustawienie będzie zachowywane. Aby uzyskać więcej informacji, zobacz [listę ustawień regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--cache` | **Opcjonalnie**: Jeśli jest obecny, pakiety będą przechowywane po zainstalowaniu do kolejnych napraw. Zastępuje to globalne ustawienie zasad, które ma być używane do kolejnych instalacji, napraw lub modyfikacji. Domyślną zasadą jest buforowanie pakietów. Jest to ignorowane dla polecenia odinstalowywania. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietu,](disable-or-move-the-package-cache.md) aby uzyskać więcej informacji. |
| `--nocache` | **Opcjonalnie**: Jeśli jest obecny, pakiety zostaną usunięte po zainstalowaniu lub naprawie. Zostaną one pobrane ponownie tylko wtedy, gdy jest to konieczne i usunięte ponownie po użyciu. Zastępuje to globalne ustawienie zasad, które ma być używane do kolejnych instalacji, napraw lub modyfikacji. Domyślną zasadą jest buforowanie pakietów. Jest to ignorowane dla polecenia odinstalowywania. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietu,](disable-or-move-the-package-cache.md) aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Opcjonalnie:** Jeśli jest obecny, uniemożliwia instalatorowi aktualizowanie się po określeniu ciszy. Instalator nie powiodą się polecenie i zwróci kod zakończenia niezerowy, jeśli noUpdateInstaller jest określony z cichą, gdy wymagana jest aktualizacja instalatora. |
| `--noWeb` | **Opcjonalnie:** Jeśli jest obecny, instalator programu Visual Studio używa plików w katalogu układu do zainstalowania programu Visual Studio. Jeśli użytkownik próbuje zainstalować składniki, które nie są w układzie, instalacja kończy się niepowodzeniem.  Aby uzyskać więcej informacji, zobacz [Wdrażanie z instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne:** Ten przełącznik nie uniemożliwia konfiguracji programu Visual Studio sprawdzania dostępności aktualizacji. Aby uzyskać więcej informacji, zobacz [Aktualizacje sterowania wdrożeniami programu Visual Studio opartymi na sieci.](controlling-updates-to-visual-studio-deployments.md) **Nowość w 16.3.5**: Ten przełącznik zapobiega błędom i poprawia wydajność dzięki instalacjom i aktualizacjom offline.|
| `--path <name>=<path>` | **Opcjonalnie:** Służy do określania niestandardowych ścieżek instalacji. Obsługiwane nazwy ścieżek są współużytkowane, buforowane i instalowane. |
| `--path cache=<path>` | **Opcjonalnie**: Używa określonej lokalizacji do pobierania plików instalacyjnych. Tę lokalizację można ustawić tylko przy pierwszym zainstalowaniu programu Visual Studio. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Opcjonalnie**: Zawiera udostępnione pliki dla instalacji programu Visual Studio side-by-side. Niektóre narzędzia i zestawY SDK instalują się w lokalizacji na tym dysku, podczas gdy inne mogą zastąpić to ustawienie i zainstalować na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br><br>Ważne: To można ustawić tylko raz i po raz pierwszy, że program Visual Studio jest zainstalowany. |
| `--path install=<path>` | **Opcjonalnie**: `–-installPath`Odpowiednik . W szczególności `--installPath "C:\VS"` `--path install="C:\VS"` i są równoważne. Jednocześnie można użyć tylko jednego z tych poleceń. |

::: moniker-end

## <a name="list-of-workload-ids-and-component-ids"></a>Lista identyfikatorów obciążenia i identyfikatorów składników

Aby uzyskać listę identyfikatorów obciążenia i składników posortowanych według produktu programu Visual Studio, zobacz stronę [Obciążenia i identyfikatory składników programu Visual Studio.](workload-and-component-ids.md)

## <a name="list-of-language-locales"></a>Lista ustawień regionalnych języka

| **Ustawienia regionalne języka** | **Język** |
| ----------------------- | --------------- |
| Cs-cz | Czeski |
| De-de (de-de) | Niemiecki |
| En-us | Polski |
| Es-y | Hiszpański |
| Fr-fr | Francuski |
| It-it | Włoski |
| Ja-jp (ja-jp) | Japoński |
| Ko-kr | Koreański |
| Pl-pl | Polski |
| Pt-br | Portugalski (Brazylia) |
| Ru-ru (ru) | Rosyjski |
| Tr-tr | Turecki |
| Zh-cn (zh) | Chiński - Uproszczony |
| Zh-tw (zh-tw) | Chiński - Tradycyjny |

## <a name="error-codes"></a>Kody błędów

W zależności od wyniku operacji `%ERRORLEVEL%` zmienna środowiskowa jest ustawiona na jedną z następujących wartości:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Każda operacja generuje kilka plików `%TEMP%` dziennika w katalogu, które wskazują postęp instalacji. Sortuj folder według daty i `dd_bootstrapper` `dd_client`poszukaj plików, które zaczynają się od programu , oraz `dd_setup` odpowiednio dla programu inichowania, aplikacji instalacyjnej i aparatu konfiguracji.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Przykłady parametrów wiersza polecenia dla instalacji programu Visual Studio](command-line-parameter-examples.md)
- [Tworzenie instalacji programu Visual Studio w trybie offline](create-an-offline-installation-of-visual-studio.md)
- [Zautomatyzowana instalacja programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)

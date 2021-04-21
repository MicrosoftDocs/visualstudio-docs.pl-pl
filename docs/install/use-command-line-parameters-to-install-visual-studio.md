---
title: Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak za pomocą parametrów wiersza polecenia kontrolować lub dostosowywać Visual Studio instalacji.
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 23c83611e7663d35b229517f1e0224eb4ae7bb57
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800812"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio

Podczas instalowania Visual Studio programowo lub z wiersza polecenia można użyć różnych parametrów wiersza polecenia, aby kontrolować lub dostosowywać instalację, aby wykonać następujące czynności:

- Rozpocznij instalację na kliencie z pewnymi wstępnie wybranymi opcjami i zachowaniami.
- Zautomatyzuj proces instalacji.
- Utwórz lub utrzymuj układ sieciowy plików produktów w celu instalowania lub aktualizowania maszyn klienckich.

Opcje wiersza polecenia mogą być używane z programem inicjatora konfiguracji, czyli małym plikiem (około 1 MB), który inicjuje proces pobierania, lub pakietem aktualizacji administratora, który jest [wdrażany](https://catalog.update.microsoft.com)w katalogu Microsoft Update . 

::: moniker range="vs-2017"

Aby uzyskać program inicjujący dla programu Visual Studio 2017 w wersji 15.9, przejdź do strony [**programu Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/) poprzednich wersji i pobierz jeden z następujących plików programu inicjjącego:

| Wersja | Pod nazwą |
|-------------|-----------------------|
|Visual Studio Enterprise 2017 w wersji 15.9 | vs_enterprise.exe |
|Visual Studio Professional 2017 w wersji 15.9 | vs_professional.exe |
|Visual Studio Build Tools 2017 w wersji 15.9  | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Program inicjujący programu Visual Studio 2019 można uzyskać na stronie pobierania programu [Visual Studio](https://visualstudio.microsoft.com/downloads) lub na stronie wydań programu [Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) dla wybranej wersji i Visual Studio. Plik instalacyjny — lub program inicjujący — będzie odpowiadać lub być podobny do jednego z następujących:

| Wersja                    | Plik                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)     |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019) |
| Visual Studio 2019 Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)     |
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)  |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjujący i chcesz sprawdzić, jaka jest jego wersja, oto jak to zrobić. W systemie Windows otwórz Eksplorator plików kliknij prawym przyciskiem myszy plik programu  inicjjącego, wybierz pozycję **Właściwości,** wybierz kartę Szczegóły, a następnie wyświetl **numer wersji** produktu. Aby dopasować tę liczbę do wersji Visual Studio, zapoznaj się z Visual Studio [kompilacji i datami wydania.](visual-studio-build-numbers-and-release-dates.md)

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Jeśli wcześniej pobrano plik programu inicjujący i chcesz sprawdzić jego wersję, oto jak to zrobić. W systemie Windows otwórz Eksplorator plików kliknij prawym przyciskiem myszy plik programu  inicjjącego, wybierz pozycję **Właściwości,** wybierz kartę Szczegóły, a następnie wyświetl **numer wersji** produktu. Aby dopasować tę liczbę do wersji Visual Studio, zobacz stronę Visual Studio [2019.](https://docs.microsoft.com/visualstudio/releases/2019/history)

::: moniker-end

Aktualizację administratora można uzyskać, przechodząc do katalogu [Microsoft Update,](https://catalog.update.microsoft.com)wyszukaj aktualizację, którą chcesz zainstalować, i naciśnij przycisk Pobierz. Aktualizacje administratora zakładają, że Visual Studio jest już zainstalowany na komputerze. Zastosowanie aktualizacji administratora nie spowoduje zainicjowania zupełnie nowej instalacji.

## <a name="bootstrapper-commands-and-command-line-parameters"></a>Polecenia programu inicjujące i parametry wiersza polecenia

Podczas wywołania Visual Studio inicjatora programowo w celu zainstalowania produktu lub utrzymania układu, pierwszym parametrem jest polecenie (czasownik), które opisuje operację do wykonania. Kolejne opcjonalne parametry wiersza polecenia, które są poprzedzone dwoma kreskami (--), jeszcze bardziej definiują sposób, w jaki ta operacja ma się zdarzyć. W Visual Studio wiersza polecenia nie jest uwzględniania liter, a dodatkowe przykłady można znaleźć na stronie Przykłady parametrów [wiersza](command-line-parameter-examples.md) polecenia.

Przykład składni: `vs_enterprise.exe [command] <optional parameters>...`

| **Polecenia** | **Opis** |
| ----------------------- | --------------- |
| (puste) | Domyślne polecenie instaluje produkt i jest używane do wszystkich operacji konserwacji układu. |
| `modify` | Modyfikuje zainstalowany produkt. |
| `update` | Aktualizuje zainstalowany produkt. |
| `repair` | Naprawia zainstalowany produkt. |
| `uninstall` | Odinstalowuje zainstalowany produkt. |
| `export` | Eksportuje wybór instalacji do pliku konfiguracji instalacji. **Uwaga:** Można jej używać tylko z vs_installer.exe. |


| **Parametry** | **Opis** |
| ----------------------- | --------------- |
| `--installPath <dir>` | W przypadku domyślnego polecenia instalacji ten parametr ma wartość **Optional (Opcjonalnie)** i opisuje miejsce, w którym wystąpienie zostanie zainstalowane na komputerze klienckim. W przypadku innych poleceń, takich jak aktualizowanie lub modyfikowanie, ten parametr ma wartość **Wymagane** i określa katalog instalacyjny wystąpienia, na którym będzie działać. |
| `--add <one or more workload or component IDs>` | **Opcjonalnie:** podczas instalowania lub modyfikowania polecenia ten powtarzalny parametr określa co najmniej jeden identyfikator obciążenia lub składnika do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie są to składniki zalecane ani opcjonalne. Dodatkowe składniki można kontrolować globalnie przy użyciu `--includeRecommended` parametrów `--includeOptional` i/lub . Aby uwzględnić wiele obciążeń lub składników, powtórz `--add` polecenie (na przykład `--add Workload1 --add Workload2` ). W celu precyzyjnej kontroli można dołączyć lub `;includeRecommended` `;includeOptional` do identyfikatora (na przykład lub `--add Workload1;includeRecommended` `--add Workload2;includeRecommended;includeOptional` ). Aby uzyskać więcej informacji, zobacz [stronę Identyfikatory obciążeń i](workload-and-component-ids.md) składników. |
| `--remove <one or more workload or component IDs>` | **Opcjonalnie:** podczas modyfikowania ten powtarzalny parametr określa co najmniej jeden identyfikator obciążenia lub składnika do usunięcia. Uzupełnia i zachowuje się podobnie do `--add` parametru . |
| `--addProductLang <language-locale>` | **Opcjonalnie:** podczas instalowania lub modyfikowania polecenia ten powtarzalny parametr określa pakiety językowe interfejsu użytkownika, które powinny zostać zainstalowane z produktem. Jeśli nie jest obecny, instalacja używa pakietu językowego odpowiadającego ustawieniach regionalnych komputera. Aby uzyskać więcej informacji, zobacz [sekcję Lista ustawieniach regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--removeProductLang <language-locale>` | **Opcjonalnie:** podczas instalowania lub modyfikowania polecenia ten powtarzalny parametr określa pakiety językowe interfejsu użytkownika, które powinny zostać usunięte z produktu.  Uzupełnia i zachowuje się podobnie do `--addProductLang` parametru . |
| `--in <path>` | **Opcjonalnie:** URI lub ścieżka do pliku [odpowiedzi,](automated-installation-with-response-file.md) który może zawierać ustawienia konfiguracji. |
| `--all` | **Opcjonalnie:** podczas instalacji lub modyfikowania polecenia ten parametr powoduje zainstalowanie wszystkich obciążeń i składników produktu. |
| `--allWorkloads` | **Opcjonalnie:** podczas instalacji lub modyfikowania polecenia ten parametr instaluje wszystkie obciążenia i składniki, ale nie zaleca ani nie zawiera składników opcjonalnych. |
| `--includeRecommended` | **Opcjonalnie:** podczas instalacji lub modyfikowania polecenia ten parametr zawiera zalecane składniki dla wszystkich zainstalowanych obciążeń, ale nie składników opcjonalnych. Obciążenia są określane za pomocą lub `--allWorkloads` `--add` . |
| `--includeOptional` | **Opcjonalnie:** podczas instalacji lub modyfikowania polecenia ten parametr zawiera opcjonalne składniki dla wszystkich zainstalowanych obciążeń, ale nie zalecanych składników. Obciążenia są określane za pomocą lub `--allWorkloads` `--add` .  |
| `--quiet, -q` | **Opcjonalnie:** używany z dowolnym poleceniem, ten parametr zapobiega wyświetlaniu dowolnego interfejsu użytkownika podczas wykonywania polecenia. |
| `--passive, -p` | **Opcjonalnie:** ten parametr powoduje, że interfejs użytkownika jest wyświetlany w sposób nieinterakcyjny. Ten parametr wyklucza się wzajemnie z parametru (i w rzeczywistości zastępuje `--quiet` go).  |
| `--norestart` | **Opcjonalnie:** ten parametr musi być sparowany z parametrami `--passive` lub `--quiet` .  Podczas instalacji, aktualizacji lub modyfikowania polecenia dodanie `--norestart` parametru spowoduje opóźnienie wszelkie niezbędne ponowne uruchomienie. |
| `--force` | **Opcjonalnie:** ten parametr wymusza zamknięcie Visual Studio nawet wtedy, Visual Studio proces jest w użyciu. |
| `--installWhileDownloading` | **Opcjonalnie:** podczas instalacji, aktualizacji lub modyfikowania polecenia ten parametr Visual Studio zarówno pobieranie, jak i instalowanie produktu równolegle. Jest to środowisko domyślne. |
| `--downloadThenInstall` | **Opcjonalnie:** podczas instalowania, aktualizowania lub modyfikowania polecenia ten parametr wymusza Visual Studio pobrania wszystkich plików przed ich zainstalowaniem. Wyklucza się ona z `--installWhileDownloading` parametru . |
| `--nickname <name>` | **Opcjonalnie:** podczas polecenia instalacji ten parametr definiuje pseudonim, który ma zostać przypisany do zainstalowanego produktu. Pseudonim nie może być dłuższy niż 10 znaków.  |
| `--productKey` | **Opcjonalnie:** podczas instalacji tego parametru definiuje klucz produktu do użycia dla zainstalowanego produktu. Składa się z 25 znaków alfanumerycznych w formacie `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` lub `xxxxxxxxxxxxxxxxxxxxxxxxx` . |
| `--help, --?, -h, -?` | Wyświetla wersję tej strony w trybie offline. |
| `--config <path>` | **Opcjonalnie:** podczas operacji instalowania lub modyfikowania określa się obciążenia i składniki do dodania na podstawie wcześniej zapisanego pliku konfiguracji instalacji. Ta operacja jest addycyjna i nie spowoduje usunięcia żadnego obciążenia ani składnika, jeśli nie ma ich w pliku. Ponadto elementy, które nie mają zastosowania do produktu, nie zostaną dodane. Podczas operacji eksportu określa to lokalizację zapisania pliku konfiguracji instalacji. |


> [!IMPORTANT]
> W przypadku określania wielu różnych obciążeń, składników lub języków należy powtórzyć przełącznik wiersza polecenia `--add` lub `--remove` dla każdego elementu.

## <a name="layout-command-and-command-line-parameters"></a>Polecenie układu i parametry wiersza polecenia
We wszystkich operacjach zarządzania układem założono, że polecenie jest domyślną instaluj (puste). Dlatego wszystkie operacje zarządzania układem powinny rozpoczynać się od początkowego wymaganego `--layout` parametru.  W poniższej tabeli opisano inne parametry, których można użyć do utworzenia lub zaktualizowania układu przy użyciu wiersza polecenia.

| **Parametry układu** | **Opis** |
| ----------------------- | --------------- |
| `--layout <dir>` | Określa katalog do utworzenia lub zaktualizowania pamięci podręcznej instalacji w trybie offline. Aby uzyskać więcej informacji, [zobacz Create a network-based installation of Visual Studio](create-a-network-installation-of-visual-studio.md)(Tworzenie instalacji sieciowej Visual Studio ).|
| `--lang <one or more language-locales>` | **Opcjonalnie:** używany z programem w celu przygotowania pamięci podręcznej instalacji w trybie offline z `--layout` pakietami zasobów z określonymi językami. Aby uzyskać więcej informacji, zobacz [sekcję Lista ustawieniach regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--add <one or more workload or component IDs>` | **Opcjonalnie:** co najmniej jeden identyfikator obciążenia lub składnika do dodania. Wymagane składniki artefaktu są zainstalowane, ale nie są to składniki zalecane ani opcjonalne. Dodatkowe składniki można kontrolować globalnie przy użyciu `--includeRecommended` i/lub `--includeOptional` . W celu precyzyjnej kontroli można dołączyć lub `;includeRecommended` `;includeOptional` do identyfikatora (na przykład lub `--add Workload1;includeRecommended` `--add Workload2;includeOptional` ). Aby uzyskać więcej informacji, zobacz [stronę Identyfikatory obciążeń i](workload-and-component-ids.md) składników. <br/>**Uwaga:** jeśli jest używany, pobierane są tylko określone obciążenia i `--add` składniki oraz ich zależności. Jeśli `--add` nie zostanie określony, wszystkie obciążenia i składniki zostaną pobrane do układu.|
| `--includeRecommended` | **Opcjonalnie:** zawiera zalecane składniki dla wszystkich zainstalowanych obciążeń, ale nie składników opcjonalnych. Obciążenia są określane za pomocą lub `--allWorkloads` `--add` . |
| `--includeOptional` | **Opcjonalnie:** zawiera zalecane *i opcjonalne* składniki dla wszystkich obciążeń uwzględnionych w układzie. Obciążenia są określane za pomocą `--add` .  |
| `--keepLayoutVersion` | **Opcjonalnie:** zastosuj zmiany do układu bez aktualizowania wersji układu. |
| `--verify` | **Opcjonalnie:** sprawdź zawartość układu. Zostaną wyświetlone wszystkie uszkodzone lub brakujące pliki. |
| `--fix` | **Opcjonalnie:** sprawdź zawartość układu.  Jeśli jakiekolwiek pliki są uszkodzone lub brakuje, są one ponownie ładowane. Aby naprawić układ, wymagany jest dostęp do Internetu. |
| `--clean <one or more paths to catalogs>` | **Opcjonalnie:** usuwa stare wersje składników z układu, który został zaktualizowany do nowszej wersji. |

| **Zaawansowane parametry układu** | **Opis** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcjonalnie:** identyfikator kanału dla wystąpienia do zainstalowania. Jest to wymagane w przypadku polecenia instalacji i ignorowane w przypadku innych poleceń, jeśli `--installPath` jest określony. |
| `--channelUri <uri>` | **Opcjonalnie:** URI manifestu kanału. Jeśli aktualizacje nie są chętne, może wskazać nieistniejący plik (na przykład `--channelUri` --channelUri C:\doesntExist.chman). Może to służyć do instalacji polecenia; Jest on ignorowany w przypadku innych poleceń. |
| `--installChannelUri <uri>` | **Opcjonalnie:** URI manifestu kanału do użycia podczas instalacji. Do wykrywania aktualizacji jest używany określony przez wartość URI (który należy określić, gdy `--channelUri` `--installChannelUri` jest określony). Może to służyć do instalacji polecenia; Jest on ignorowany w przypadku innych poleceń. |
| `--installCatalogUri <uri>` | **Opcjonalnie:** URI manifestu wykazu do użycia podczas instalacji. Jeśli zostanie określony, menedżer kanałów spróbuje pobrać manifest wykazu z tego URI przed użyciem wartości URI w manifeście kanału instalacji. Ten parametr jest używany do obsługi instalacji w trybie offline, w której pamięć podręczna układu zostanie utworzona z już pobranym katalogiem produktów. Może to służyć do instalacji polecenia; Jest on ignorowany w przypadku innych poleceń. |
| `--productId <id>` | **Opcjonalnie:** identyfikator produktu dla wystąpienia, które zostanie zainstalowane. Jest to wstępnie wypełniane w normalnych warunkach instalacji. |
| `--wait` | **Opcjonalnie:** proces będzie czekać na ukończenie instalacji przed zwróceniem kodu zakończenia. Jest to przydatne podczas automatyzowania instalacji, w których trzeba poczekać na zakończenie instalacji w celu obsługi kodu powrotu z tej instalacji. |
| `--locale <language-locale>` | **Opcjonalnie:** zmień język wyświetlania interfejsu użytkownika dla samego instalatora. Ustawienie zostanie utrwalone. Aby uzyskać więcej informacji, zobacz [sekcję Lista ustawieniach regionalnych języka](#list-of-language-locales) na tej stronie.|
| `--cache` | **Opcjonalnie:** jeśli są obecne, pakiety będą przechowywane po zainstalowaniu do kolejnych napraw. Zastępuje to ustawienie zasad globalnych, które mają być używane podczas kolejnych instalacji, napraw lub modyfikacji. Domyślne zasady to buforowanie pakietów. Jest to ignorowane w przypadku polecenia dezinstalacji. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietów,](disable-or-move-the-package-cache.md) aby uzyskać więcej informacji. |
| `--nocache` | **Opcjonalnie:** jeśli jest obecny, pakiety zostaną usunięte po zainstalowaniu lub naprawie. Zostaną one pobrane ponownie tylko w razie potrzeby i usunięte ponownie po użyciu. Zastępuje to ustawienie zasad globalnych, które ma być używane w przypadku kolejnych instalacji, napraw lub modyfikacji. Domyślne zasady to buforowanie pakietów. Jest to ignorowane w przypadku polecenia dezinstalacji. Przeczytaj, jak [wyłączyć lub przenieść pamięć podręczną pakietów,](disable-or-move-the-package-cache.md) aby uzyskać więcej informacji. |
| `--noUpdateInstaller` | **Opcjonalnie:** Jeśli jest obecny, instalator nie może aktualizować się, gdy określono wartość "cichy". Instalator zakończy się niepowodzeniem z poleceniem i zwróci kod zakończenia o wartości niezerowej, jeśli określono wartość noUpdateInstaller z wartością cichą, gdy wymagana jest aktualizacja instalatora. |
| `--noWeb` | **Opcjonalnie:** jeśli występuje, Visual Studio używa plików w katalogu układu do instalowania Visual Studio. Jeśli użytkownik spróbuje zainstalować składniki, które nie są w układzie, instalacja zakończy się niepowodzeniem.  Aby uzyskać więcej informacji, zobacz [Wdrażanie z instalacji sieciowej](create-a-network-installation-of-visual-studio.md). <br/><br/> **Ważne:** ten przełącznik nie Visual Studio sprawdzania aktualizacji przez instalatora. Aby uzyskać więcej informacji, zobacz [Kontrolowanie aktualizacji sieciowych wdrożeń Visual Studio sieciowych.](controlling-updates-to-visual-studio-deployments.md) |
| `--path <name>=<path>` | **Opcjonalnie:** służy do określania niestandardowych ścieżek instalacji. Obsługiwane nazwy ścieżek to współdzielona, buforowa i instalowana. |
| `--path cache=<path>` | **Opcjonalnie:** używa lokalizacji, która jest określana do pobierania plików instalacyjnych. Tę lokalizację można ustawić tylko przy pierwszym zainstalowaniu Visual Studio instalacji. Przykład: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Opcjonalnie:** zawiera pliki udostępnione do instalacji obok siebie Visual Studio instalacji. Niektóre narzędzia i zestawy SDK są zainstalowane w lokalizacji na tym dysku, a inne mogą zastąpić to ustawienie i zainstalować je na innym dysku. Przykład: `--path shared="C:\VS\shared"` <br/><br/>**Ważne:** tę wartość można ustawić tylko raz i przy pierwszym zainstalowaniu Visual Studio instalacji. |
| `--path install=<path>` | **Opcjonalnie:** równoważne `–-installPath` . W szczególności `--installPath "C:\VS"` i `--path install="C:\VS"` są równoważne. Jednocześnie można używać tylko jednego z tych poleceń. |

## <a name="administrator-update-command-and-command-line-parameters"></a>Administrator zaktualizuj polecenie i parametry wiersza polecenia
Jeśli pobierasz aktualizację administratora z katalogu [Microsoft Update do](https://catalog.update.microsoft.com) katalogu instalacyjnego na komputerze klienckim, możesz po prostu kliknąć dwukrotnie plik, aby zastosować aktualizację. Możesz również otworzyć okno polecenia i przekazać niektóre z poniższych parametrów, aby zmienić domyślne zachowanie. 

Jeśli wdrażasz aktualizację administratora za pośrednictwem programu Microsoft Endpoint Manager (SCCM), możesz zmodyfikować pakiet, aby dostosować zachowanie przy użyciu poniższych parametrów. Parametry można również kontrolować za pomocą pliku konfiguracji na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [Metody konfigurowania aktualizacji administratora](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)

Pamiętaj, że wszystkie parametry aktualizacji administratora są uruchamiane w kontekście aktualizacji.

| **Parametry aktualizacji administratora** | **Opis** |
| ----------------------- | --------------- |
| `--installerUpdateArgs [optional parameters]` | Ten parametr działa jako "tablica pass-through" określonych parametrów, które są istotne dla scenariuszy aktualizacji administratora. Opcjonalne parametry, które są włączone w tym celu, to: <br/><br/> `--quiet`: jest to domyślne środowisko aktualizacji administratora i znajduje się tutaj, aby uzyskać pełną listę. <br/> `--passive`: ten parametr zastępuje `--quiet` parametr .  Powoduje to, że interfejs użytkownika jest wyświetlany w sposób nieinterakcyjny. <br/>`--norestart`: ten parametr musi być używany w połączeniu z albo lub i powoduje, że wszelkie niezbędne ponowne uruchomienia `--quiet` `--passive` są opóźnione. <br/>`--noWeb`: ten parametr Visual Studio sprawdzania w Internecie, czy nie ma aktualizacji produktu. <br/>`--force`: ten parametr wymusza zamknięcie Visual Studio, nawet jeśli Visual Studio jest w użyciu. Tego parametru należy używać z rozwagą, ponieważ może to spowodować utratę pracy. Ten parametr musi być używany w kontekście użytkownika. <br/>`--installWhileDownloading`: ten parametr Visual Studio pobieranie i instalowanie produktu równolegle. Jest to domyślne środowisko aktualizacji dla administratorów i jest wymienione tutaj, aby uzyskać pełną kompletność. <br/>`--downloadThenInstall`: ten parametr wymusza Visual Studio pobierania wszystkich plików przed ich zainstalowaniem. Wyklucza się ona z `--installWhileDownloading` parametru . |
| `--checkPendingReboot` | Aktualizacja zostanie przerwana, jeśli na maszynie istnieje oczekujące ponowne uruchomienie, niezależnie od tego, która aplikacja ją spowodowała. Wartość domyślna to nie sprawdzanie oczekujących ponownych uruchomień. |


Przykład składni: `visualstudioupdate-16.9.0to16.9.4.exe --installerUpdateArgs=--force,--noWeb --checkPendingReboot`

## <a name="list-of-workload-ids-and-component-ids"></a>Lista identyfikatorów obciążeń i identyfikatorów składników

Aby uzyskać listę identyfikatorów obciążeń i składników posortowanych według produktu Visual Studio, zobacz stronę Visual Studio [identyfikatorów](workload-and-component-ids.md) obciążeń i składników.

## <a name="list-of-language-locales"></a>Lista ustawieniach regionalnych języka

| **Ustawienia językowe** | **Język** |
| ----------------------- | --------------- |
| Cs-cz | Czeski |
| De-de | Niemiecki |
| Pl-pl | Angielski |
| Es-es | Hiszpański |
| z o.o. | Francuski |
| It-it | Włoski |
| Ja-jp | japoński |
| Ko-kr | Koreański |
| Pl-pl | Polski |
| Pt-br | Portugalski (Brazylia) |
| Ru-ru | Rosyjski |
| Tr-tr | Turecki |
| Zh-cn | Chiński – uproszczony |
| Zh-tw | Chiński – tradycyjny |

## <a name="error-codes"></a>Kody błędów

W zależności od wyniku operacji zmienna `%ERRORLEVEL%` środowiskowa jest ustawiana na jedną z następujących wartości:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Każda operacja generuje kilka plików dziennika w `%TEMP%` katalogu, które wskazują postęp instalacji. Posortuj folder według daty i poszukaj plików, które zaczynają się od , i odpowiednio dla programu inicjjącego, aplikacji instalatora i `dd_bootstrapper` `dd_client` aparatu `dd_setup` instalacji.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Przykłady parametrów wiersza polecenia Visual Studio instalacji](command-line-parameter-examples.md)
- [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Zautomatyzowana instalacja programu Visual Studio przy użyciu pliku odpowiedzi](automated-installation-with-response-file.md)
- [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)

---
title: Obszary robocze języka R
description: Jak kontrolować miejsce, w którym jest uruchamiany kod języka R, za pomocą obszarów roboczych w programie Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 97ce4f226c39a20ad41c5977f800aa178450c69c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409665"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Kontrolowanie, gdzie kod R jest uruchamiany z obszarami roboczymi

Obszar roboczy w R Tools for Visual Studio (RTVS) pozwala konfigurować miejsce uruchomienia sesji języka R, co może wystąpić na komputerach lokalnych i zdalnych. Celem jest umożliwienie pracy z porównywalnym interfejsem użytkownika, co zapewnia możliwość skorzystania z potencjalnie zaawansowanych komputerów opartych na chmurze.

Aby otworzyć okno **obszary robocze** , użyj polecenia **R Tools** > **Windows** > **Workspaces** lub naciśnij **klawisze CTRL**+**9**.

![Okno obszarów roboczych w R Tools for Visual Studio (program VS2017)](media/workspaces-window.png)

W tym oknie zielony znacznik wyboru wskazuje aktywny obszar roboczy, z którym powiązana jest RTVS. Wybranie niebieską strzałką powoduje ustawienie aktywnego obszaru roboczego. Ikona Ustawienia (koła zębate) po prawej stronie każdego obszaru roboczego umożliwia zmianę nazwy, lokalizacji i argumentów wiersza polecenia. Czerwona litera X usuwa ręcznie dodany obszar roboczy.

## <a name="save-and-reset-a-workspace"></a>Zapisywanie i resetowanie obszaru roboczego

Domyślnie RTVS nie zapisuje stanu obszaru roboczego po zamknięciu i ponownym otwarciu projektu. Możesz jednak zmienić to zachowanie, korzystając z [opcji obszaru roboczego](options-for-r-tools-in-visual-studio.md#workspace).

Polecenie **R Tools** > **Session** > **Reset** i przycisk Resetuj pasek narzędzi w oknie interaktywnym również resetuje stan obszaru roboczego w dowolnym momencie. W obszarze zdalne obszary robocze Zresetuj program usuwa profil użytkownika utworzony podczas pierwszego połączenia z serwerem zdalnym, co skutecznie usuwa wszystkie pliki, które zostały w nim zebrane.

## <a name="local-workspaces"></a>Lokalne obszary robocze

Na liście lokalne obszary robocze są wyświetlane wszystkie interpretery języka R, które zostały zainstalowane na komputerze.

Po uruchomieniu programu Visual Studio próbuje automatycznie wykryć wszystkie wersje języka R, które zostały zainstalowane, przeglądając klucz rejestru **HKEY_LOCAL_MACHINE \software\r-core\\** . Ponieważ ten test jest wykonywany tylko podczas uruchamiania, należy ponownie uruchomić program Visual Studio po zainstalowaniu nowego interpretera języka R.

RTVS może nie wykryć interpretera języka R, który jest instalowany w sposób niestandardowym (na przykład podczas zwykłego kopiowania plików do folderu zamiast uruchamiania Instalatora). W takim przypadku należy ręcznie utworzyć nowy lokalny obszar roboczy języka R w następujący sposób:

1. W oknie obszary robocze Wybierz przycisk **Dodaj** .
1. Wprowadź nazwę nowego obszaru roboczego.
1. Wprowadź ścieżkę do głównego folderu R, który jest taki, który zawiera folder *bin* z interpreterem, a także wszelkie opcjonalne argumenty wiersza polecenia do przekazania do interpretera, gdy RTVS go uruchamia.
1. Po zakończeniu wybierz pozycję **Zapisz** .

![Dodawanie nowego obszaru roboczego](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Zdalne obszary robocze

Zdalne obszary robocze umożliwiają łączenie się z sesją języka R na komputerze zdalnym. (Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md) , aby skonfigurować w tym celu komputer).

Program Visual Studio nie wykrywa automatycznie zdalnych obszarów roboczych, dlatego należy dodać je ręcznie przy użyciu przycisku **Dodaj** w oknie obszary robocze zgodnie z opisem w poprzedniej sekcji. W takim przypadku wprowadź identyfikator URI komputera zdalnego zamiast ścieżki lokalnej.

> [!Important]
> Zdalne obszary robocze są identyfikowane za pomocą identyfikatora URI, który *musi korzystać z protokołu HTTPS* w celu zapewnienia prywatności i integralności komunikacji z komputerem zdalnym. Program Visual Studio nie może nawiązać połączenia z komputerem zdalnym, który nie obsługuje protokołu HTTPS.

> [!Note]
> Zdalne obszary robocze są efektywnie w wersji zapoznawczej. Pracujemy nad lepszą implementacją problemu z synchronizacją plików dla przyszłej wersji i zachęcamy do Twoich pomysłów i opinii.

## <a name="remote-workspace-logon"></a>Zdalne logowanie do obszaru roboczego

Aby zalogować się do zdalnego obszaru roboczego, należy użyć nazwy użytkownika i hasła.

### <a name="logon-to-windows-workspace"></a>Logowanie do obszaru roboczego systemu Windows

Jeśli komputer zdalny jest skonfigurowany do korzystania z konta domeny, można użyć logowania do domeny w celu uzyskania dostępu do zdalnego obszaru roboczego. Jeśli tak nie jest, należy użyć formatu `machine-name\username`, aby zalogować się przy użyciu konta komputera na maszynie zdalnej.

### <a name="logon-to-linux-workspace"></a>Logowanie do obszaru roboczego systemu Linux

Aby zalogować się do konta systemu Linux, użyj formatu `<<unix>>\username`. Jeśli na przykład masz konto o nazwie `ruser`, wpisz nazwę użytkownika jako `<<unix>>\ruser`.

## <a name="switch-between-workspaces"></a>Przełączanie między obszarami roboczymi

RTVS jest powiązana tylko z jednym obszarem roboczym naraz. Powiązany obszar roboczy jest wskazywany przez niewielki zielony znacznik wyboru w oknie obszary robocze. Domyślnie program RTVS tworzy powiązanie z ostatnim otwartym lokalnym obszarem roboczym w poprzedniej sesji.

Aby zmienić aktywny obszar roboczy, wybierz niebieską strzałkę obok żądanego obszaru roboczego. W ten sposób zostanie wyświetlony komunikat z prośbą o zapisanie sesji, zakończenie bieżącego obszaru roboczego, a następnie przełączenie na nowy.

> [!Tip]
> Aby wyłączyć monit zapisywania, wybierz polecenie **R Tools** > **Opcje** i ustaw opcję **Pokaż okno dialogowe potwierdzenia przed przełączeniem obszarów roboczych** , aby `No`. Zobacz [Opcje obszaru roboczego](options-for-r-tools-in-visual-studio.md#workspace).

Jeśli podjęto próbę przełączenia do lokalnego obszaru roboczego, który został odinstalowany lub do zdalnego obszaru roboczego, który jest niedostępny, RTVS może nie być powiązany z żadnym obszarem roboczym. W związku z tym po wprowadzeniu kodu w oknie interaktywnym może zostać wyświetlony błąd lub spróbuj uruchomić kod w inny sposób:

![Błąd w przypadku braku powiązania obszaru roboczego z RTVS](media/workspaces-disconnected-interactive-window.png)

Aby rozwiązać ten stan, przejdź do innego obszaru roboczego w oknie obszary robocze. Jeśli żadne obszary robocze nie są dostępne, należy zainstalować interpreter języka R. Możesz również spróbować ponownie uruchomić program Visual Studio, jeśli zainstalowano interpreter, gdy program Visual Studio jest uruchomiony.

### <a name="switch-to-a-remote-workspace"></a>Przełącz do zdalnego obszaru roboczego

RTVS poprosi o poświadczenia podczas pierwszego połączenia ze zdalnym obszarem roboczym, a następnie buforuje te poświadczenia (przy użyciu bezpiecznego blokowania systemu Windows) na potrzeby kolejnych sesji. Komunikacja z serwerem zdalnym jest następnie wykonywana bezpiecznie za pośrednictwem protokołu HTTPS (co jest wymagane).

W zależności od konfiguracji serwera podczas łączenia się z nimi może zostać wyświetlone ostrzeżenie o certyfikacie "certyfikat zabezpieczeń przedstawiony przez zdalne usługi języka R nie pozwala nam udowodnić, że rzeczywiście nawiązujesz połączenie z maszyną (nazwa)".

![Ostrzeżenie o certyfikacie z podpisem własnym podczas nawiązywania połączenia ze zdalnym obszarem roboczym](media/workspaces-remote-self-signed-certificate-warning.png)

Certyfikat to dokument przedstawiony RTVS przez komputer, z którym próbujesz nawiązać połączenie. Certyfikat zawiera pole, które identyfikuje identyfikator URI danego komputera. Ostrzeżenie jest wyświetlane, gdy RTVS wykrywa niezgodność identyfikatora URI w certyfikacie oraz identyfikator URI używany do nawiązywania połączenia z komputerem, co oznacza, że zabezpieczenia serwera mogły zostać naruszone.

To ostrzeżenie pojawia się również wtedy, gdy *certyfikat* z podpisem własnym został użyty do włączenia protokołu HTTPS na komputerze zdalnym zamiast używania go od zaufanego dostawcy. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Katalogi na komputerach lokalnych i zdalnych

Domyślnie po rozpoczęciu nowego interpretera języka R w lokalnym obszarze roboczym bieżący katalog roboczy jest *%USERPROFILE%\Documents*. Katalog można zmienić w dowolnym momencie za pomocą poleceń **R Tools** > **katalogu roboczego** lub klikając prawym przyciskiem myszy projekt w programie Visual Studio Eksplorator rozwiązań i wybierając polecenia, takie jak **Ustaw katalog roboczy w tym miejscu**.

Gdy po raz pierwszy łączysz się z komputerem zdalnym, RTVS automatycznie tworzy profil użytkownika na podstawie Twoich poświadczeń, co spowoduje ustawienie katalogu roboczego do folderu *dokumenty* w tym profilu. Ten folder jest używany dla wszystkich kolejnych sesji zdalnych, które używają tych samych poświadczeń.

W związku z tym dokładna lokalizacja, w której działa kod, może się różnić w zależności od lokalnych i zdalnych obszarów roboczych. W kodzie, a następnie zawsze używaj ścieżek względnych do plików danych, tak aby kod był przenośny między obszarami roboczymi.

Należy również pamiętać, że ze zdalnymi obszarami roboczymi wszystkie pliki w katalogu roboczym pozostają w różnych sesjach dla tego samego profilu użytkownika. Jak wspomniano wcześniej, można usunąć te pliki przy użyciu polecenia **R Tools** > **Session** > **Reset** (lub przycisku resetowania w oknie interaktywnym) podczas korzystania ze zdalnego obszaru roboczego. To polecenie ponownie usuwa profil użytkownika z serwera, który zostanie odtworzony po ponownym nawiązaniu połączenia.

## <a name="copy-project-files-to-remote-workspaces"></a>Kopiuj pliki projektu do zdalnych obszarów roboczych

Podczas pracy z projektami R w programie Visual Studio komputer lokalny zawsze ma najnowsze pliki projektu nawet wtedy, gdy używasz zdalnego obszaru roboczego. Oznacza to, że w przypadku otwarcia projektu w programie Visual Studio (zwykle jest to otwieranie rozwiązania zawierającego ten projekt), RTVS zakłada, że zawartość projektu znajduje się w całości na komputerze lokalnym. Zdalny obszar roboczy to w efekcie tylko tymczasowy Host dla plików projektu i wszystkie dane wyjściowe z kodu. Oznacza to, że na przykład podczas ładowania pliku przy użyciu `source` w oknie interaktywnym, ten plik musi już znajdować się na komputerze zdalnym w podanym przez Ciebie ścieżce lub musi znajdować się w bieżącym katalogu roboczym zdalnego interpretera języka R (ustawianym za pomocą funkcji `setwd()`).

Pliki są kopiowane na serwer zdalny w następujący sposób:

- Aby zdalnie współpracować z plikami za pomocą okna interaktywnego, należy najpierw skopiować je ręcznie, klikając prawym przyciskiem myszy pliki (lub projekt) w Eksplorator rozwiązań i wybierając **Źródło wybrane**. W przypadku poszczególnych plików są one kopiowane do katalogu roboczego na serwerze programu; podczas kopiowania projektu RTVS tworzy folder dla projektu.

- Możesz również kopiować pliki, wybierając pozycję w Eksplorator rozwiązań a następnie wybierając pozycję **źródłowe wybrane pliki**. Ta akcja spowoduje załadowanie ich do okna interaktywnego i jego uruchomienie. Jeśli sesja jest podłączona do komputera zdalnego, pliki są najpierw kopiowane.

- Gdy RTVS jest powiązany ze zdalnym obszarem roboczym i naciśniesz klawisz **F5**, wybierz pozycję **Debuguj** > **Rozpocznij debugowanie**lub w inny sposób Rozpocznij uruchamianie kodu, RTVS domyślnie automatycznie kopiuje plik projektu do zdalnego obszaru roboczego (zobacz poniżej, aby kontrolować to zachowanie).

- Wszystkie pliki, które już istnieją na serwerze, są zastępowane.

> [!Note]
> Ponieważ RTVS nie może niezawodnie przechwycić wszystkich wywołań funkcji R, wywoływanie funkcji, takich jak `source()` lub `runApp()` (w przypadku aplikacji Shiny) w oknie interaktywnym *nie kopiuje plików* do zdalnego obszaru roboczego.

[Właściwości projektu](r-projects-in-visual-studio.md#project-properties) kontrolują, czy RTVS kopiuje pliki, gdy projekt jest uruchomiony, i dokładnie te pliki są kopiowane. Aby otworzyć tę stronę, wybierz polecenie menu właściwości **projektu** >  **(nazwa)** lub kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Właściwości**.

![Karta Uruchamianie właściwości projektu z ustawieniami transferu plików](media/workspaces-remote-file-transfer-filter-settings.png)

W tym miejscu Właściwość **transfer Files on Run** określa, czy RTVS kopiuje pliki projektu automatycznie. **Pliki do przesłania** wartości następnie filtrują dokładnie te pliki, które są transferowane. Wartość domyślna to tylko kopiowanie *. R*, *. Pliki RMD*, *. SQL*, *. MD*i *. cpp* . Takie zachowanie pozwala uniknąć przypadkowego kopiowania dużych plików danych na serwer przy każdym uruchomieniu.

## <a name="copy-files-from-a-remote-workspace"></a>Kopiowanie plików ze zdalnego obszaru roboczego

Jeśli skrypt języka R generuje pliki na serwerze, można skopiować te pliki z powrotem do klienta przy użyciu funkcji `rtvs::fetch_file`. Ta funkcja akceptuje co najmniej ścieżkę zdalną do pliku, który chcesz skopiować na komputer, i opcjonalnie ścieżkę docelową na komputerze. Jeśli ścieżka nie zostanie określona, plik jest kopiowany do folderu *%USERPROFILE%\Downloads* .

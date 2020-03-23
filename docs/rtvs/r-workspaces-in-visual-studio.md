---
title: Obszary robocze R
description: Jak kontrolować, gdzie kod języka R jest uruchamiany przy użyciu obszarów roboczych w programie Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 97ce4f226c39a20ad41c5977f800aa178450c69c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302652"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Sterowanie miejscem pracy kodu R z obszarami roboczymi

Obszar roboczy w programie R Tools for Visual Studio (RTVS) umożliwia skonfigurowanie, gdzie jest uruchamiana sesja języka R, co może mieć miejsce zarówno na komputerach lokalnych, jak i zdalnych. Celem jest umożliwienie pracy nad porównywalnym doświadczeniem użytkownika, co daje możliwość korzystania z potencjalnie bardziej zaawansowanych komputerów w chmurze.

Aby otworzyć okno **Obszary robocze,** użyj polecenia **R Tools** > **Windows** > **Workspaces** lub naciśnij klawisz **Ctrl**+**9**.

![Okno obszary robocze w programie R Tools for Visual Studio (VS2017)](media/workspaces-window.png)

W tym oknie zielony znacznik wyboru wskazuje aktywny obszar roboczy, z którym jest powiązany RTVS. Wybranie niebieskiej strzałki powoduje ustawienie aktywnego obszaru roboczego. Ikona ustawień (koła zębatego) po prawej stronie każdego obszaru roboczego umożliwia zmianę jego nazwy, lokalizacji i argumentów wiersza polecenia. Czerwony znak X usuwa ręcznie dodany obszar roboczy.

## <a name="save-and-reset-a-workspace"></a>Zapisywanie i resetowanie obszaru roboczego

Domyślnie RTVS nie zapisuje stanu obszaru roboczego po zamknięciu i ponownym otwarciu projektu. Można to jednak zmienić za pomocą [opcji Obszaru roboczego](options-for-r-tools-in-visual-studio.md#workspace).

Polecenie **R Tools** > **Session** > **Reset** i przycisk resetowania paska narzędzi w oknie interaktywnym również resetują stan obszaru roboczego w dowolnym momencie. W przypadku zdalnych obszarów roboczych resetowanie powoduje usunięcie profilu użytkownika utworzonego podczas pierwszego nawiązania połączenia z serwerem zdalnym, co skutecznie usuwa wszystkie zgromadzone tam pliki.

## <a name="local-workspaces"></a>Lokalne obszary robocze

Na liście Lokalne obszary robocze są wyświetlane wszystkie interpretery R zainstalowane na komputerze.

Po uruchomieniu programu Visual Studio próbuje automatycznie wykryć wszystkie wersje języka R, które zostały zainstalowane, patrząc za pośrednictwem klucza rejestru **HKEY_LOCAL_MACHINE\Software\R-Core.\\ ** Ponieważ ta kontrola jest wykonywana tylko podczas uruchamiania, należy ponownie uruchomić program Visual Studio, jeśli zainstalujesz nowy interpreter języka R.

RTVS może nie wykryć interpretera języka R, który jest instalowany w niestandardowy sposób (na przykład podczas kopiowania plików do folderu zamiast uruchamiania instalatora). W takim przypadku ręcznie utwórz nowy lokalny obszar roboczy R w następujący sposób:

1. Wybierz przycisk **Dodaj** w oknie Obszary robocze.
1. Wprowadź nazwę nowego obszaru roboczego.
1. Wprowadź ścieżkę do folderu głównego R, który zawiera folder *bin* z interpreterem, wraz z opcjonalnymi argumentami wiersza polecenia, które mają być przekazywać do tłumacza po uruchomieniu RTVS.
1. Po zakończeniu wybierz pozycję **Zapisz**.

![Dodawanie nowego obszaru roboczego](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Zdalne obszary robocze

Zdalne obszary robocze umożliwiają łączenie się z sesją R na komputerze zdalnym. (Zobacz [Konfigurowanie zdalnych obszarów roboczych,](setting-up-remote-r-workspaces.md) aby dowiedzieć się, jak skonfigurować komputer w tym celu).

Program Visual Studio nie wykrywa automatycznie zdalnych obszarów roboczych, dlatego należy dodać je ręcznie za pomocą przycisku **Dodaj** w oknie Obszary robocze, jak opisano w poprzedniej sekcji. W takim przypadku wprowadź identyfikator URI komputera zdalnego, a nie ścieżkę lokalną.

> [!Important]
> Zdalne obszary robocze są identyfikowane przez identyfikator URI, który *musi używać protokołu HTTPS,* aby zapewnić prywatność i integralność komunikacji z komputerem zdalnym. Program Visual Studio nie może połączyć się z komputerem zdalnym, który nie obsługuje protokołu HTTPS.

> [!Note]
> Zdalne obszary robocze są skutecznie w wersji zapoznawczej. Pracujemy nad lepszą implementacją problemu synchronizacji plików w przyszłej wersji i witamy Twoje pomysły i opinie.

## <a name="remote-workspace-logon"></a>Logowanie do zdalnego obszaru roboczego

Aby zalogować się do zdalnego obszaru roboczego, należy użyć nazwy użytkownika i hasła.

### <a name="logon-to-windows-workspace"></a>Logowanie do obszaru roboczego systemu Windows

Jeśli komputer zdalny jest skonfigurowany do używania konta domeny, można użyć logowania domeny, aby uzyskać dostęp do zdalnego obszaru roboczego. Jeśli tak nie jest, musisz `machine-name\username` użyć formatu do logowania przy użyciu konta komputera na komputerze zdalnym.

### <a name="logon-to-linux-workspace"></a>Logowanie do obszaru roboczego Systemu Linux

Aby zalogować się do `<<unix>>\username` formatu konta linux. Na przykład, jeśli masz konto `ruser`według nazwy, należy wpisać nazwę użytkownika jako `<<unix>>\ruser`.

## <a name="switch-between-workspaces"></a>Przełączanie między obszarami roboczymi

RTVS jest powiązany tylko z jednym obszarem roboczym naraz. Powiązany obszar roboczy jest wskazywany przez małe zielone pole wyboru w oknie Obszary robocze. Domyślnie RTVS wiąże się z ostatnim otwartym lokalnym obszarem roboczym w poprzedniej sesji.

Aby zmienić aktywny obszar roboczy, zaznacz niebieską strzałkę obok żądanego obszaru roboczego. W ten sposób monituje o zapisanie sesji, kończy bieżący obszar roboczy, a następnie przełącza się na nowy.

> [!Tip]
> Aby wyłączyć wiersz zapisywania, wybierz polecenie**Opcje** **narzędzi** > R i ustaw okno `No` **dialogowe Pokaż potwierdzenie przed przełączeniem obszarów roboczych** na . Zobacz [Opcje obszaru roboczego](options-for-r-tools-in-visual-studio.md#workspace).

Jeśli spróbujesz przełączyć się do lokalnego obszaru roboczego, który został odinstalowany, lub do zdalnego obszaru roboczego, który jest niedostępny, RTVS może nie być powiązany z żadnym obszarem roboczym. W rezultacie może pojawić się błąd po wprowadzeniu kodu w oknie interaktywnym lub spróbuj uruchomić kod w inny sposób:

![Błąd, gdy żaden obszar roboczy nie jest powiązany z RTVS](media/workspaces-disconnected-interactive-window.png)

Aby to poprawić, przełącz się do innego obszaru roboczego w oknie Obszary robocze. Jeśli nie są dostępne żadne obszary robocze, należy zainstalować interpreter R. Można również spróbować ponownego uruchomienia programu Visual Studio, jeśli zainstalowano interpreter podczas uruchamiania programu Visual Studio.

### <a name="switch-to-a-remote-workspace"></a>Przełączanie do zdalnego obszaru roboczego

Usługa RTVS monituje o podanie poświadczeń podczas pierwszego połączenia ze zdalnym obszarem roboczym, a następnie buforuje te poświadczenia (przy użyciu bezpiecznego programu Windows Credential Locker) w późniejszych sesjach. Komunikacja z serwerem zdalnym odbywa się bezpiecznie za pośrednictwem protokołu HTTPS (co jest wymagane).

W zależności od konfiguracji serwera podczas łączenia może zostać wyświetlone ostrzeżenie o certyfikacie: "Certyfikat zabezpieczeń przedstawiony przez usługi Zdalne usługi R nie pozwala nam udowodnić, że rzeczywiście łączysz się z komputerem (nazwą)".

![Ostrzeżenie o certyfikatie z podpisem własnym podczas łączenia się ze zdalnym obszarem roboczym](media/workspaces-remote-self-signed-certificate-warning.png)

Certyfikat jest dokumentem przedstawionym RTVS przez komputer, z którego próbujesz się połączyć. Certyfikat zawiera pole identyfikujące identyfikator URI tego komputera. Ostrzeżenie pojawia się, gdy RTVS wykryje niezgodność między identyfikatorem URI w certyfikacie a identyfikatorem URI używanym do łączenia się z komputerem, co wskazuje, że zabezpieczenia serwera mogły zostać naruszone.

Jednak to ostrzeżenie pojawia się również wtedy, gdy *certyfikat z podpisem własnym* został użyty do włączenia protokołu HTTPS na komputerze zdalnym, a nie z certyfikatem zaufanego dostawcy. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Katalogi na komputerach lokalnych i zdalnych

Domyślnie po uruchomieniu nowego interpretera R w lokalnym obszarze roboczym bieżący katalog roboczy to *%userprofile%\Documents*. Katalog można zmienić w dowolnym momencie za pomocą poleceń **R Tools** > **Working Directory** lub klikając prawym przyciskiem myszy projekt w Eksploratorze rozwiązań programu Visual Studio i wybierając polecenia, takie jak Ustaw katalog **roboczy tutaj.**

Podczas pierwszego połączenia z komputerem zdalnym rtvs automatycznie tworzy profil użytkownika na podstawie poświadczeń, który ustawia katalog roboczy na folder *dokumenty* w tym profilu. Ten folder jest używany dla wszystkich kolejnych sesji zdalnych, które używają tych samych poświadczeń.

W rezultacie dokładna lokalizacja, w której uruchamia się kod, może się różnić między lokalnymi i zdalnymi obszarami roboczymi. W kodzie, a następnie zawsze używać ścieżek względnych do plików danych i tak, aby kod jest przenośny w różnych obszarach roboczych.

Należy również zauważyć, że w przypadku zdalnych obszarów roboczych wszystkie pliki w katalogu roboczym pozostają w miejscu w sesjach dla tego samego profilu użytkownika. Jak wspomniano wcześniej, można usunąć te pliki za pomocą polecenia **R Tools** > **Session** > **Reset** (lub przycisku resetowania w oknie interaktywnym) podczas korzystania ze zdalnego obszaru roboczego. To polecenie ponownie usuwa profil użytkownika z serwera, który jest odtwarzany po ponownym połączeniu.

## <a name="copy-project-files-to-remote-workspaces"></a>Kopiowanie plików projektu do zdalnych obszarów roboczych

Podczas pracy z projektami języka R w programie Visual Studio komputer lokalny zawsze ma najnowsze pliki projektu, nawet jeśli używasz zdalnego obszaru roboczego. Oznacza to, że po otwarciu projektu w programie Visual Studio (co zazwyczaj oznacza otwarcie rozwiązania zawierającego ten projekt), RTVS zakłada, że zawartość projektu znajdują się całkowicie na komputerze lokalnym. Zdalny obszar roboczy jest w efekcie tylko tymczasowym hostem dla plików projektu i wszelkich danych wyjściowych z kodu. Oznacza to na przykład, że podczas `source` ładowania pliku przy użyciu w oknie interaktywnym, ten plik musi już znajdować się na komputerze zdalnym w podanej `setwd()` ścieżce lub musi znajdować się w bieżącym katalogu roboczym zdalnego interpretera języka R (ustawiony z funkcją).

Pliki są kopiowane na serwer zdalny w następujący sposób:

- Aby zdalnie pracować z plikami za pośrednictwem okna interaktywnego, należy najpierw skopiować je ręcznie, klikając je prawym przyciskiem myszy, klikając te pliki (lub projekt) w Eksploratorze rozwiązań i wybierając pozycję **Źródło wybrane**. W przypadku pojedynczych plików są one kopiowane do katalogu roboczego na serwerze; podczas kopiowania projektu RTVS tworzy folder dla projektu.

- Można również kopiować pliki, wybierając następnie w Eksploratorze rozwiązań, a następnie wybierając **pozycję Źródło wybrane pliki .** Ta akcja ładuje je do okna interaktywnego i uruchamia je tam. Jeśli sesja jest podłączona do komputera zdalnego, pliki są tam najpierw kopiowane.

- Gdy RTVS jest powiązany ze zdalnym obszarem roboczym i naciśniesz **klawisz F5**, wybierz **opcję Debugowanie** > **rozpocznij debugowanie**lub w inny sposób rozpoczniesz uruchamianie kodu, RTVS domyślnie automatycznie kopiuje plik projektu do zdalnego obszaru roboczego (zobacz poniżej, aby dowiedzieć się, jak kontrolować to zachowanie).

- Wszystkie pliki, które już istnieją na serwerze są zastępowane.

> [!Note]
> Ponieważ RTVS nie może niezawodnie przechwycić wszystkich wywołań funkcji R, wywoływanie funkcji, takich jak `source()` lub `runApp()` (dla błyszczących aplikacji) w oknie interaktywnym, *nie* kopiuje plików do zdalnego obszaru roboczego.

[Właściwości projektu](r-projects-in-visual-studio.md#project-properties) określają, czy RTVS kopiuje pliki po uruchomieniu projektu i które dokładnie pliki są kopiowane. Aby otworzyć tę stronę, wybierz polecenie menu **Właściwości projektu** > **(nazwa)** lub kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Właściwości**.

![Karta Uruchamianie właściwości projektu z ustawieniami transferu plików](media/workspaces-remote-file-transfer-filter-settings.png)

W tym miejscu **właściwość Transfer files on run** określa, czy RTVS automatycznie kopiuje pliki projektu. Następnie filtruje dokładnie które pliki są przesyłane, wartość **plików do przesyłania.** Domyślnie jest to tylko kopiowanie *. R*, *. Rmd*, *.sql*, *.md*i *.cpp.* To zachowanie pozwala uniknąć przypadkowego kopiowania dużych plików danych na serwer przy każdym uruchomieniu.

## <a name="copy-files-from-a-remote-workspace"></a>Kopiowanie plików ze zdalnego obszaru roboczego

Jeśli skrypt języka R generuje pliki na serwerze, można skopiować `rtvs::fetch_file` te pliki z powrotem do klienta przy użyciu funkcji. Ta funkcja akceptuje co najmniej zdalną ścieżkę do pliku, który chcesz skopiować na komputer, oraz opcjonalnie ścieżkę docelową na komputerze. Jeśli ścieżka nie zostanie określona, plik zostanie skopiowany do folderu *%userprofile%\Downloads.*

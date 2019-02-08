---
title: Obszary robocze R
description: Jak kontrolować, którym jest uruchamiany kod R przy użyciu obszarów roboczych w programie Visual Studio.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 97ce4f226c39a20ad41c5977f800aa178450c69c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948150"
---
# <a name="control-where-r-code-runs-with-workspaces"></a>Kontrolki, w którym jest uruchamiany kod R z obszarami roboczymi

Obszar roboczy w R Tools for Visual Studio (RTVS) umożliwia skonfigurowanie, którym sesji języka R jest uruchamiany, która może się zdarzyć, na komputerach lokalnych i zdalnych. Celem jest umożliwienie użytkownikowi pracować nad przy użyciu interfejsu użytkownika porównywalne, co daje możliwość wykorzystać potencjalnie wydajniejszych komputerów opartych na chmurze.

Aby otworzyć **obszary robocze** oknie, użyj **R Tools** > **Windows** > **obszary robocze** polecenie i naciśnij klawisz **Ctrl**+**9**.

![Obszary robocze okna R Tools for Visual Studio (VS2017)](media/workspaces-window.png)

W tym oknie zielony znacznik wyboru wskazuje aktywnego obszaru roboczego, z którym powiązany jest RTVS. Wybranie niebieską strzałką ustawienie aktywnego obszaru roboczego. Ikona ustawienia (koło zębate) z prawej strony każdego obszaru roboczego umożliwia zmianę jego nazwę, lokalizację i argumenty wiersza polecenia. Czerwony znak X spowoduje usunięcie ręcznie dodanych obszaru roboczego.

## <a name="save-and-reset-a-workspace"></a>Zapisz i resetowaniu obszaru roboczego

Domyślnie RTVS nie zostanie zapisany stan obszaru roboczego po zamknięciu i ponownym otwarciu projektu. Można zmienić to zachowanie, jednak za pomocą [opcji obszaru roboczego](options-for-r-tools-in-visual-studio.md#workspace).

**R Tools** > **sesji** > **resetowania** polecenia i resetowania przycisk paska narzędzi w oknie interaktywnym także zresetować stan obszaru roboczego w dowolnym czas. Za pomocą zdalnych obszarów roboczych Resetowanie usuwa utworzony, jeśli najpierw nawiązywania połączenia z serwera zdalnego, co skutecznie spowoduje usunięcie wszystkich plików, które ma współdzielenia profilu użytkownika.

## <a name="local-workspaces"></a>Lokalne obszary robocze

Na liście lokalne obszary robocze zostaną wyświetlone wszystkie interpreterów języka R, zainstalowanych na komputerze.

Po uruchomieniu programu Visual Studio podejmie próbę automatycznego wykrycia, wszystkie wersje języka R, który jest zainstalowany, przeglądając **HKEY_LOCAL_MACHINE\Software\R Core\\**  klucza rejestru. To sprawdzenie odbywa się tylko przy uruchamianiu, dlatego musisz ponownie program Visual Studio po zainstalowaniu nowego interpreter języka R.

RTVS może nie wykrywać interpreter języka R, które jest instalowane w sposób niestandardowy (na przykład, jeśli po prostu kopiowanie plików do folderu, zamiast uruchamiania Instalatora). W takim przypadku ręcznie utworzyć nowego lokalnego obszaru roboczego języka R w następujący sposób:

1. Wybierz **Dodaj** przycisk w oknie obszarów roboczych.
1. Wprowadź nazwę dla nowego obszaru roboczego.
1. Wprowadź ścieżkę do folderu głównego języka R jest tą, która zawiera *bin* folder z interpreter, oraz opcjonalne argumenty wiersza polecenia, aby przekazać do interpretera po jej uruchomieniu przez RTVS.
1. Wybierz **Zapisz** po zakończeniu.

![Dodawanie nowego obszaru roboczego](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Zdalne obszary robocze

Zdalne obszary robocze pozwalają połączyć się z sesją R na komputerze zdalnym. (Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md) dotyczące sposobu konfigurowania komputera do tego celu.)

Program Visual Studio nie jest wykrywany zdalnych obszarów roboczych, więc należy dodać je ręcznie przy użyciu **Dodaj** znajdujący się w oknie obszarów roboczych, zgodnie z opisem w poprzedniej sekcji. W takich przypadkach wprowadź identyfikator URI na komputerze zdalnym, a nie ścieżką lokalną.

> [!Important]
> Zdalne obszary robocze są identyfikowane przez identyfikator URI, *musi używać protokołu HTTPS* aby zapewnić ochronę prywatności i integralności komunikacji z komputerem zdalnym. Program Visual Studio nie może połączyć się z komputerem zdalnym, który nie obsługuje protokołu HTTPS.

> [!Note]
> Zdalne obszary robocze są efektywne w wersji zapoznawczej. Firma Microsoft pracuje nad lepszej realizacji problemu synchronizacja plików w przyszłej wersji i Witamy swoje pomysły i opinie.

## <a name="remote-workspace-logon"></a>Logowania zdalnego obszaru roboczego

Należy użyć nazwy użytkownika i hasła do logowania do zdalnego obszaru roboczego.

### <a name="logon-to-windows-workspace"></a>Zaloguj się do obszaru roboczego Windows

Jeśli komputer zdalny jest skonfigurowana do używania konta domeny, umożliwia logowanie do domeny dostępu zdalnego obszaru roboczego. Jeśli nie, a następnie należy użyć `machine-name\username` format, aby zalogować się przy użyciu konta komputera na komputerze zdalnym.

### <a name="logon-to-linux-workspace"></a>Zaloguj się do obszaru roboczego systemu Linux

Aby zalogować się do używanie konta linux `<<unix>>\username` formatu. Na przykład, jeśli masz konto według nazwy `ruser`, a następnie wpisz nazwę użytkownika jako `<<unix>>\ruser`.

## <a name="switch-between-workspaces"></a>Przełączanie między obszarami roboczymi

RTVS jest powiązana tylko z jednym obszarem roboczym jednocześnie. Powiązane obszar roboczy jest wskazywany przez małe zielony znacznik wyboru w oknie obszarów roboczych. Domyślnie RTVS wiąże się z ostatnich Otwórz lokalnego obszaru roboczego w poprzedniej sesji.

Aby zmienić aktywnego obszaru roboczego, wybierz niebieską strzałką obok żądanego obszaru roboczego. Ten sposób wyświetli monit o zapisanie sesję, kończy bieżący obszar roboczy, a następnie przełącza się na nową.

> [!Tip]
> Można wyłączyć zapisywanie monit, wybierz opcję **R Tools** > **opcje** poleceń i ustaw **Pokaż okno dialogowe potwierdzenia przed przełączeniem obszary robocze** możliwość `No`. Zobacz [opcji obszaru roboczego](options-for-r-tools-in-visual-studio.md#workspace).

Jeśli spróbujesz przełączyć się do lokalnego obszaru roboczego, który został odinstalowany, lub do zdalnego obszaru roboczego, który jest niedostępny, RTVS może nie być powiązany z dowolnym obszarze roboczym. W rezultacie zostanie wyświetlony błąd, podczas wprowadzania kodu w oknie interaktywnym lub podjęta próba uruchomienia kodu, w przeciwnym razie:

![Wystąpił błąd podczas żadnego obszaru roboczego jest powiązany z RTVS](media/workspaces-disconnected-interactive-window.png)

Aby rozwiązać ten problem, przełącz się do innego obszaru roboczego w oknie obszarów roboczych. Jeśli dostępnych żadnych obszarów roboczych, musisz zainstalować interpreter języka R. Można też spróbować ponownie uruchomić program Visual Studio, jeśli po zainstalowaniu tłumacza podczas uruchamiania programu Visual Studio.

### <a name="switch-to-a-remote-workspace"></a>Przełącz się do zdalnego obszaru roboczego

RTVS wyświetli monit o podanie poświadczeń przy pierwszym połączeniu zdalnego obszaru roboczego, a następnie buforuje te poświadczenia (przy użyciu bezpiecznego skrytki na poświadczenia Windows) nowszym sesji. Komunikacja z serwerem zdalnym następnie odbywa się bezpiecznie za pośrednictwem protokołu HTTPS (jest to wymagane).

W zależności od konfiguracji serwera mogą pojawić się ostrzeżenie dotyczące certyfikatu podczas nawiązywania połączenia z tym odczytów "certyfikat zabezpieczeń przedstawiony przez Remote R Services pozwala nam potwierdzenie, że w rzeczywistości łączysz się komputera (nazwa)."

![Ostrzeżenie certyfikatu z podpisem własnym podczas nawiązywania połączenia zdalnego obszaru roboczego](media/workspaces-remote-self-signed-certificate-warning.png)

Certyfikat jest dokumentem prezentująca RTVS komputera, na którym próbujesz nawiązać połączenie. Certyfikat zawiera pole, które identyfikuje identyfikator URI tego komputera. Ostrzeżenie jest wyświetlane, gdy RTVS wykryje niezgodność identyfikatora URI w certyfikacie i identyfikator URI używany do połączenia z komputerem, wskazujący, że zabezpieczenia serwera może zabezpieczenia mogły zostać naruszone.

Jednak to ostrzeżenie pojawia się również Jeśli *certyfikatu z podpisem własnym* został użyty do włączania protokołu HTTPS na komputerze zdalnym, a nie przy użyciu jednej z zaufanego dostawcę. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

## <a name="directories-on-local-and-remote-computers"></a>Katalogi na komputerach lokalnych i zdalnych

Domyślnie po uruchomieniu nowego interpreter języka R w lokalnym obszarze roboczym Twojego bieżącego katalogu roboczego jest *%USERPROFILE%\Documents*. Można zmienić katalogu w każdej chwili **R Tools** > **katalog roboczy** polecenia, lub przez kliknięcie prawym przyciskiem myszy projekt w Eksploratorze rozwiązań w usłudze Visual Studio i wybraniu poleceń, takich jak  **Ustaw katalog roboczy, w tym miejscu**.

Podczas pierwszego połączenia z komputerem zdalnym, RTVS automatycznie tworzy oparte na swoje poświadczenia do profilu użytkownika, który określa katalog roboczy na *dokumenty* folder, w ramach tego profilu. Ten folder jest używany dla wszystkich kolejnych sesji zdalnych, które używają tych samych poświadczeń.

W wyniku dokładną lokalizację, w którym jest uruchamiany kod może różnić się między obszarami roboczymi lokalnych i zdalnych. W swoim kodzie następnie zawsze używać ścieżki względne do plików danych i takie tak, aby Twój kod będzie przeniesiony w obszarach roboczych.

Należy pamiętać, że za pomocą zdalnych obszarów roboczych, wszystkie pliki w katalogu roboczym, pozostają we wszystkich sesjach dla tego samego profilu użytkownika. Jak wspomniano wcześniej, możesz usunąć te pliki przy użyciu **R Tools** > **sesji** > **resetowania** polecenie (lub przycisk Resetuj w Okno interaktywne) podczas korzystania ze zdalnego obszaru roboczego. To polecenie usuwa ponownie profilu użytkownika z serwera, który zostaje odtworzone po ponownym połączeniu.

## <a name="copy-project-files-to-remote-workspaces"></a>Skopiuj pliki projektu do zdalnych obszarów roboczych

Podczas pracy z projekty języka R w programie Visual Studio, komputer lokalny ma zawsze najnowsze pliki projektu nawet wtedy, gdy używasz zdalnego obszaru roboczego. Oznacza to po otwarciu projektu w programie Visual Studio (co zwykle oznacza, że podczas otwierania rozwiązania zawierającego projekt) RTVS przyjęto założenie, zawartość projektu znajdują się na komputerze lokalnym całkowicie. Zdalny obszar roboczy jest w efekcie tylko tymczasowe hosta dla plików projektu i wszystkie dane wyjściowe z kodu. Oznacza to, na przykład, że podczas ładowania pliku przy użyciu `source` w oknie interaktywnym, ten plik musi już być na komputerze zdalnym w ścieżce podasz, lub musi być w bieżącym katalogu roboczym zdalnego interpretera języka R (zestaw z `setwd()`</c2>funkcji).

Pliki są kopiowane do serwera zdalnego:

- Aby pracować z plików zdalnie za pomocą okna interaktywnego, należy najpierw skopiować je ręcznie w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy tych plików (lub projektu) i wybierając pozycję **wybrane źródło**. Dla poszczególnych plików zostaną skopiowane do katalogu roboczego na serwerze; Podczas kopiowania projektu, RTVS tworzy folder dla projektu.

- Możesz również kopiować pliki wybraniu, a następnie w oknie Eksploratora rozwiązań, a następnie wybierając **pliki źródłowe zaznaczone (s)**. Ta akcja ładuje je do okna interaktywnego i wykonuje na nich dostępne. Jeśli sesja jest podłączony do komputera zdalnego, pliki są kopiowane istnieje najpierw.

- Kiedy RTVS jest powiązany z obszarem roboczym zdalnego i naciśnięciu klawisza **F5**, wybierz opcję **debugowania** > **Rozpocznij debugowanie**, lub w przeciwnym razie Rozpocznij uruchamianie kodu, RTVS domyślnie Kopiuje plik projektu do zdalnego obszaru roboczego automatycznie (patrz poniżej sposób kontrolowania tego zachowania).

- Wszystkie pliki, które już istnieją na serwerze zostaną zastąpione.

> [!Note]
> Ponieważ RTVS niezawodnie nie może przechwycić wszystkie wywołania funkcji języka R, wywoływanie funkcji takich jak `source()` lub `runApp()` (dla aplikacji Shiny) w oknie interaktywnym jest *nie* skopiuj pliki do zdalnego obszaru roboczego.

[Właściwości projektu](r-projects-in-visual-studio.md#project-properties) formant czy RTVS kopiuje pliki, gdy projekt jest przebiegu i dokładnie pliki, które są kopiowane. Aby otworzyć tę stronę, wybierz **projektu** > **właściwości (nazwa)** polecenie menu lub kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz pozycję **właściwości**.

![Właściwości projektu kartę transferu pliku parametrów uruchomieniowych](media/workspaces-remote-file-transfer-filter-settings.png)

W tym miejscu **transferu plików przy uruchomieniu** właściwość określa, czy RTVS automatycznie kopiuje pliki projektu. **Plików do transferu** następnie wartość filtry dokładnie pliki, które są przenoszone. Wartość domyślna to można skopiować tylko *. R*, *. RMD*, *.sql*, *MD*, i *.cpp* plików. To zachowanie zapobiega przypadkowo kopiowanie duże pliki danych na serwerze przy użyciu każdego uruchomienia.

## <a name="copy-files-from-a-remote-workspace"></a>Skopiuj pliki ze zdalnego obszaru roboczego

Jeśli skrypt języka R generuje pliki na serwerze, możesz skopiować te pliki do klienta przy użyciu `rtvs::fetch_file` funkcji. Ta funkcja akceptuje co najmniej, zdalne ścieżki do pliku, który chcesz skopiować na komputer oraz, opcjonalnie, ścieżkę docelową na komputerze. Jeśli nie określisz ścieżki, plik zostanie skopiowany do Twojej *%userprofile%\Downloads* folderu.

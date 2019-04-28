---
title: Synchronizowanie zmian między XCode i Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c71a4d7c-120e-4559-a114-3a99c4b860a9
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 42352ba4c5260c4b13a4cb3c6875d3469efcf404
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62573392"
---
# <a name="sync-changes-between-xcode-and-visual-studio"></a>Synchronizacja zmian między XCode i Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Języka Microsoft Visual C++ dla opracowywania aplikacji mobilnych składnika obejmuje funkcje zdalnego synchronizowania pracy między danym Komputerem a Twojego komputera Mac. Gdy są skojarzone maszyny i programu Visual Studio na komputerze Mac, nowe opcje są dostępne dla systemu iOS projektów aplikacji w programie Visual Studio można użyć, aby otworzyć projekt w programie XCode, Przenieś swój kod między XCode i Visual Studio i oczyścić katalog tymczasowy projektu XCode.

 Aby użyć opcji komputer zdalny, projekt musi być projektu aplikacji systemu iOS, a Visual Studio muszą być skojarzone z Twojego komputera Mac. Aby uzyskać wymagania wstępne i instrukcje dotyczące sposobu pary komputera Mac, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilacji przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="the-remote-machine-menu"></a>W menu maszyny zdalnej
 W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy na projekt aplikacji systemu iOS, aby wyświetlić menu kontekstowe. Wybierz **maszyny zdalnej** element, aby wyświetlić dostępne opcje zdalnego.

 ![Element menu komputera zdalnego, w Eksploratorze rozwiązań](../cross-platform/media/cppmdd-u2-remotemachine-menu.jpg "CPPMDD_U2_RemoteMachine_Menu")

 Te polecenia pozwalają otworzyć projekt w programie XCode, przenoszenie lokalne zmiany lub całego projektu programu Visual Studio i XCode i oczyścić plików tymczasowych na komputerze zdalnym.

### <a name="open-in-xcode"></a>Otwórz w programie XCode
 Aby otworzyć projekt w narzędziu XCode z programu Visual Studio na **maszyny zdalnej** podmenu, wybierz **Otwórz w programie XCode** można otworzyć wybranego projektu na sparowanym komputerze zdalnym. Serwer vcremote służy do środowiska XCode na komputerze Mac Otwórz i przejdź do katalogu tymczasowego, utworzony na komputerze Mac, który zawiera kopię projektu. Program Visual Studio pojawia się okno dialogowe, które zawiera katalog tymczasowy używany dla projektu. Akcje wykonywane na komputerze zdalnym są także wyświetlane w **dane wyjściowe** okna w programie Visual Studio. Aby je wyświetlić, konieczne może być wybierz **Visual C++ maszyny zdalnej** w **Pokaż dane wyjściowe z** listy rozwijanej w górnej części **dane wyjściowe** okna.

 ![W oknie danych wyjściowych zawiera akcje maszyny zdalnej. ](../cross-platform/media/cppmdd-u2-remotemachine-output.png "CPPMDD_U2_RemoteMachine_Output")

 Na komputerze Mac można użyć narzędzia XCode do edytowania kodu i zasobów, scenorysy i akcji. W programie Visual Studio projekt aplikacji systemu iOS jest oznaczony za pomocą "Otwarte w środowisku XCode" wskazują, że zmiany mogą być dokonywane na komputerze zdalnym. Po zakończeniu edycji ściąganie z lokalizacji zdalnej lub przyrostowe ściąganie z poleceń zdalnych można użyć do skopiowania zmiany do projektu programu Visual Studio.

### <a name="push-to-remote-and-incremental-push-to-remote"></a>Wypchnij do zdalnego i przyrostowe Wypychanie do lokalizacji zdalnej
 Jeśli zostały wprowadzone zmiany do projektu aplikacji systemu iOS w programie Visual Studio, Wypychanie do zdalnego i przyrostowe Wypychanie do poleceń zdalnych może służyć do przenoszenia plików projektu zmienione na sparowanym komputerze zdalnym. Wypychanie do polecenia zdalnego kopiuje wszystkie pliki projektu do maszyny zdalnej. Tylko przyrostowe Wypychanie do polecenia zdalnego kopiuje zmienionych plików do maszyny zdalnej. W przypadku dużych projektów z niewielkich zmian przyrostowych polecenie pozwala zaoszczędzić czas i przepustowości.

 Aby skopiować pliki projektu z Twoim komputerem Mac w programie Visual Studio w **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz **maszyny zdalnej** a następnie wybierz opcję **Wypychanie do lokalizacji zdalnej** lub **przyrostowe Wypychanie do lokalizacji zdalnej** można skopiować pliki projektu w programie Visual Studio na komputerze Mac.

### <a name="pull-from-remote-and-incremental-pull-from-remote"></a>Korzystaj z zdalnego i przyrostowe ściąganie z lokalizacji zdalnej
 Po wprowadzeniu zmian do projektu w programie XCode cofnąć zmiany do programu Visual Studio w celu synchronizowania projektów.

 Aby skopiować pliki projektu na komputerze Mac, w programie Visual Studio w **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz **maszyny zdalnej** a następnie wybierz opcję **ściąganie z lokalizacji zdalnej** lub **przyrostowe ściąganie z lokalizacji zdalnej** do kopiowania plików projektu na komputerze Mac w programie Visual Studio.

### <a name="clean-remote"></a>Wyczyść maszynę zdalną
 Polecenia Wyczyść zdalnego służy do usuwania plików w katalogu projektu tymczasowego na komputerze zdalnym. Zawartość katalogu, w tym wszystkie pliki źródłowe lub produktów kompilacji, są usuwane na komputerze Mac. Upewnij się, że zostały zsynchronizowane wszelkie zmiany, które chcesz zachować powrót do programu Visual Studio przy użyciu ściągnięcia ze zdalnej lub przyrostowe ściąganie ze zdalnej, zanim użyjesz polecenia Wyczyść zdalnego.

 Aby oczyścić katalog tymczasowy projektu, na komputerze zdalnym, w programie Visual Studio w **Eksploratora rozwiązań** okna, kliknij prawym przyciskiem myszy projekt aplikacji systemu iOS, aby otworzyć menu kontekstowe. Wybierz **maszyny zdalnej** i wybierz polecenie **czyste zdalnego** można usunąć pliki w katalogu projektu na komputerze Mac.

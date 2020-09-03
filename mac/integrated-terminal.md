---
title: Visual Studio dla komputerów Mac — Terminal zintegrowany
description: Visual Studio dla komputerów Mac zapewnia zintegrowane środowisko programistyczne do kompilowania aplikacji .NET w systemie macOS, w tym ASP.NET Core witryn sieci Web i projektów platformy Xamarin dla systemów iOS, Android, Mac i Xamarin. Forms.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: d362938e8f0075591ea5d4ed8461d11395680b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "84185204"
---
# <a name="integrated-terminal"></a>Zintegrowany terminal
W Visual Studio dla komputerów Mac można otworzyć zintegrowane okno terminalu, rozpoczynając od katalogu głównego rozwiązania. Terminal może być przydatny dla różnych rodzajów sytuacji — uruchamiania zadań frontonu (na przykład: npm, NG lub Vue), zarządzania kontenerami, uruchamiania zaawansowanych poleceń git, wykonywania poleceń Entity Framework, wyświetlania danych wyjściowych interfejsu wiersza polecenia dotnet, dodawania pakietów NuGet i innych. 

Aby otworzyć Terminal:
- Użyj skrótu klawiaturowego **Ctrl +** , aby pokazać lub ukryć okno terminalu.
- Użyj **View** \> **Pads** \> menu **terminala** widoku.
- Użyj polecenia **terminalu** na pasku wyszukiwania.

![* Visual Studio dla komputerów Mac zintegrowany terminal natychmiast po uruchomieniu. *](media/integrated-terminal-intro.png)

Domyślnie po uruchomieniu terminalu zostanie:
- Ustaw katalog roboczy na ścieżkę bieżącego rozwiązania.
- Załaduj domyślną powłokę systemową.

## <a name="search"></a>Wyszukiwanie
Zawartość okna terminalu można przeszukiwać za pomocą menu **wyszukaj > Znajdź...** .

![* Środowisko wyszukiwania w Visual Studio dla komputerów Mac zintegrowanym terminalu *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Skróty klawiaturowe terminalu
|Polecenia|Skróty klawiaturowe|
|-|-|
|Pokaż/Ukryj okno terminalu|**CTRL + '**|
|Utwórz nowe wystąpienie terminalu|**CTRL + '**|
|Przewiń stronę w górę|**PageUp**|
|Przewiń stronę w dół|**PageDown**|
|Przechodzenie między poprzednio używanymi poleceniami|**↑**, **↓**|
|Zwiększ rozmiar czcionki|**⌘ +**|
|Zmniejsz rozmiar czcionki|**⌘-**|

## <a name="multiple-instances"></a>Wiele wystąpień
W dowolnym momencie może być uruchomionych wiele wystąpień terminalu. Nowe wystąpienie można utworzyć przy użyciu skrótu klawiaturowego **Ctrl + '** . Możesz przełączać się między wystąpieniami, klikając kartę dla każdego wystąpienia lub używając skrótu **Ctrl + Tab** , aby użyć okna dialogowego selektora okna.

![* Wiele wystąpień terminalu w Visual Studio dla komputerów Mac *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Dostosowywanie okna terminalu
### <a name="configuring-the-terminal-font"></a>Konfigurowanie czcionki terminalu
Możesz zmienić czcionkę i rozmiar używanej zawartości terminalu w okienku preferencje > środowisko > czcionki. Domyślnie czcionka będzie taka sama jak zawartość konsoli wyjściowej, przy użyciu regularnego Menlo, size 11. Można ją ustawić na dowolną czcionkę, niezależnie od czcionki edytora.

![* Dostosowanie ustawień czcionki dla terminalu zintegrowanego *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Używanie dostosowań terminalu systemu
Zintegrowany terminal używa tych samych ustawień domyślnych i konfiguracji co terminal systemu macOS. Oznacza to, że dostosowania terminala (ZSH, zsh, itp.) działają również w zintegrowanym terminalu.

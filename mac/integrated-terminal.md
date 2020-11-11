---
title: Visual Studio dla komputerów Mac — Terminal zintegrowany
description: Praca z zintegrowanym terminalem w Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: f91c2b1c3f06f8f1fbe54e32fde70b9fe88c5f5d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492875"
---
# <a name="integrated-terminal"></a>Zintegrowany terminal
W Visual Studio dla komputerów Mac można otworzyć zintegrowane okno terminalu, rozpoczynając od katalogu głównego rozwiązania. Terminal może być przydatny dla różnych rodzajów sytuacji — uruchamiania zadań frontonu (na przykład: npm, NG lub Vue), zarządzania kontenerami, uruchamiania zaawansowanych poleceń git, wykonywania poleceń Entity Framework, wyświetlania danych wyjściowych interfejsu wiersza polecenia dotnet, dodawania pakietów NuGet i innych. 

Aby otworzyć Terminal:
- Użyj skrótu klawiaturowego **Ctrl +** , aby pokazać lub ukryć okno terminalu.
- Użyj menu **Widok** \> **terminalu** .
- Użyj polecenia **terminalu** na pasku wyszukiwania.

![* Visual Studio dla komputerów Mac zintegrowany terminal natychmiast po uruchomieniu. *](media/integrated-terminal-intro.png)

Domyślnie po uruchomieniu terminalu zostanie:
- Ustaw katalog roboczy na ścieżkę bieżącego rozwiązania.
- Załaduj domyślną powłokę systemową.

## <a name="search"></a>Wyszukaj
Zawartość okna terminalu można przeszukiwać za pomocą menu **wyszukaj > Znajdź...** .

![* Środowisko wyszukiwania w Visual Studio dla komputerów Mac zintegrowanym terminalu *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Skróty klawiaturowe terminalu
|Polecenia|Skróty klawiaturowe|
|-|-|
|Pokaż/Ukryj okno terminalu|**CTRL + '**|
|Utwórz nowe wystąpienie terminalu|**CTRL + '**|
|Przewiń stronę w górę|**PageUp**|
|Przewiń stronę w dół|**PageDown**|
|Przechodzenie między poprzednio używanymi poleceniami|**↑** , **↓**|
|Zwiększ rozmiar czcionki|**⌘ +**|
|Zmniejsz rozmiar czcionki|**⌘-**|

## <a name="multiple-instances"></a>Wiele wystąpień
W dowolnym momencie może być uruchomionych wiele wystąpień terminalu. Nowe wystąpienie można utworzyć przy użyciu skrótu klawiaturowego **Ctrl + '** . Możesz przełączać się między wystąpieniami, klikając kartę dla każdego wystąpienia lub używając skrótu **Ctrl + Tab** , aby użyć okna dialogowego selektora okna.

![* Wiele wystąpień terminalu w Visual Studio dla komputerów Mac *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Dostosowywanie okna terminalu
### <a name="configuring-the-terminal-font"></a>Konfigurowanie czcionki terminalu
Możesz zmienić czcionkę i rozmiar używanej zawartości terminalu w okienku preferencje > środowisko > czcionki. Domyślnie czcionka będzie taka sama jak Okno Dane wyjściowe zawartości, przy użyciu regularnego Menlo o rozmiarze 11. Można ją ustawić na dowolną czcionkę, niezależnie od czcionki edytora.

![* Dostosowanie ustawień czcionki dla terminalu zintegrowanego *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Używanie dostosowań terminalu systemu
Zintegrowany terminal używa tych samych ustawień domyślnych i konfiguracji co terminal systemu macOS. Oznacza to, że dostosowania terminala (ZSH, zsh, itp.) działają również w zintegrowanym terminalu.

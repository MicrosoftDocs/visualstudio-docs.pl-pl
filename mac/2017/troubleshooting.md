---
title: Rozwiązywanie problemów
description: Typowe problemy i rozwiązania dla programu Visual Studio dla komputerów Mac użytkowników.
ms.topic: troubleshooting
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 3a5ea59e6f98891cd113ccad9a74038ca52cccf8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62987004"
---
# <a name="troubleshooting"></a>Rozwiązywanie problemów

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Wyświetlanie dzienników w programie Visual Studio dla komputerów Mac

Dzienniki można znaleźć, przechodząc do **Pomoc > Otwórz katalog dzienników** elementu menu, jak przedstawiono poniżej:

![Otwórz element menu katalogu dziennika](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Wyświetlanie wyjątków

Gdy zostaje przechwycony wyjątek, pojawi się bąbelków wyjątku. Aby wyświetlić więcej szczegółów, wybierz **Wyświetl szczegóły** przycisku:

![Wyświetl szczegółowe informacje o wyjątku](media/troubleshooting-image2.png)

Spowoduje to wyświetlenie **Pokaż szczegóły** okno dialogowe, podając więcej informacji na temat wyjątku:

![Pokaż okno dialogowe szczegółów](media/troubleshooting-image3.png)

Ważne sekcje okno dialogowe, które są numerowane powyżej opisano szczegółowo poniżej:

1. Typ wyjątku, który pokazuje Pełna nazwa typu wyjątku, że są przestrzegane.
2. Komunikat wyjątku pokazuje wartość właściwości komunikatu obiekt wyjątku.
3. Typ wyjątek wewnętrzny, który zawiera pełną nazwę typu wyjątku dla aktualnie wybranego wyjątku w widoku drzewa wyjątek wewnętrzny.
4. Komunikat wyjątku wewnętrznego, zawiera wartość właściwości komunikat o wyjątku wybranego w widoku drzewa wyjątek wewnętrzny.
5. Wyświetl ślad stosu. To może zostać zwinięty przy użyciu strzałek ujawnienie i zawiera wpisy ramki stosu.
6. Przykład wpisy niebędący kodem użytkownika.
7. Przykład wpisów kodu użytkownika.
8. Właściwości widoku, który zawiera wszystkie właściwości i pola wyjątku. To może zostać zwinięty przy użyciu strzałek ujawnienie.
9. Widok drzewa, wyjątek wewnętrzny. Wybierz wyjątków wewnętrznych, w tym widoku za pomocą klawiatury strzałek w górę/w dół lub za pomocą myszy lub dotykowej.
10. Domyślnie jest ono ustawione na co **Debuguj tylko kod projektu** ustawiono opcję w ustawieniach debugera. Zaznaczenie tego pola spowoduje włączenie cały kod niezwiązany z użytkownikiem zwinąć w jednym wierszu w stacktrace.
11. Przycisk kopiowania, aby skopiować `exception.ToString()` dane wyjściowe do Schowka.

Należy pamiętać, że niektóre sekcje te są widoczne tylko, gdy wyjątek ma wyjątek wewnętrzny.

## <a name="see-also"></a>Zobacz także

- [Zasoby dla rozwiązywania problemów z błędami środowiska IDE (Visual Studio Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)
---
title: Rozwiązywanie problemów
description: Typowe problemy i rozwiązania dla użytkowników programu Visual Studio dla komputerów Mac.
ms.topic: troubleshooting
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: b0f10e1f70349126ab48c41efc40f982212836f1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67691885"
---
# <a name="troubleshooting"></a>Rozwiązywanie problemów

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Wyświetlanie dzienników w programie Visual Studio dla komputerów Mac

Dzienniki można znaleźć, przeglądając pozycję menu **Pomoc > Otwórz katalog dziennika,** jak pokazano poniżej:

![Otwórz element menu katalogu Dziennika](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Wyświetlanie wyjątków

Po przechowaniu wyjątku pojawia się dymek wyjątku. Aby wyświetlić więcej szczegółów, wybierz przycisk **Wyświetl szczegóły:**

![Zobacz więcej szczegółów na temat wyjątku](media/troubleshooting-image2.png)

Spowoduje to wyświetlenie okna dialogowego **Pokaż szczegóły,** zawierającego więcej informacji dotyczących wyjątku:

![Okno dialogowe Pokaż szczegóły](media/troubleshooting-image3.png)

Ważne sekcje okna dialogowego, które są ponumerowane powyżej, są szczegółowo opisane poniżej:

1. Typ wyjątku, który pokazuje pełną nazwę typu wyjątku, który jest obserwowany.
2. Komunikat wyjątku, który pokazuje wartość Message właściwości obiektu wyjątku.
3. Wewnętrzny typ wyjątku, który pokazuje pełną nazwę typu wyjątku dla aktualnie wybranego wyjątku w widoku drzewa wyjątków inner.
4. Komunikat wyjątek wewnętrzny, pokazuje wartość Message właściwości wybranego wyjątku w widoku drzewa wyjątku wewnętrznego.
5. Widok stacktrace. Może to być zwinięte za pomocą strzałki ujawnienia i zawiera wpisy ramek stosu.
6. Przykład wpisów kodu niebędącego użytkownikiem.
7. Przykład wpisów kodu użytkownika.
8. Widok właściwości, który pokazuje wszystkie właściwości i pola wyjątku. To może być zwinięte za pomocą strzałki ujawnienia.
9. Wewnętrzny widok drzewa wyjątków. Wybierz wewnętrzne wyjątki w tym widoku za pomocą klawiatury w górę / w dół strzałki lub za pomocą myszy lub gładzika.
10. Domyślnie jest to ustawione na to, co **kod projektu debugowania tylko** opcja w ustawieniach debugera jest ustawiona. Zaznaczenie tego pola spowoduje, że cały kod niebędący użytkownikiem zwinie się w jeden wiersz w stacktrace.
11. Przycisk kopiowania, `exception.ToString()` aby skopiować dane wyjściowe do schowka.

Należy zauważyć, że niektóre z tych sekcji są widoczne tylko wtedy, gdy wyjątek ma wyjątek wewnętrzny.

## <a name="see-also"></a>Zobacz też

- [Zasoby dotyczące rozwiązywania problemów z błędami IDE (Visual Studio w systemie Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)
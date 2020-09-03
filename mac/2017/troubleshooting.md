---
title: Rozwiązywanie problemów
description: Typowe problemy i rozwiązania dla użytkowników Visual Studio dla komputerów Mac.
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 6073e0bf2a601bf5183798a1df4fd835d0b93427
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985164"
---
# <a name="troubleshooting"></a>Rozwiązywanie problemów

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Wyświetlanie dzienników w Visual Studio dla komputerów Mac

Dzienniki można znaleźć, przechodząc do menu **pomoc > Otwórz katalog dziennika** , jak pokazano poniżej:

![Otwórz element menu katalogu dziennika](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Wyświetlanie wyjątków

Gdy zostanie przechwycony wyjątek, pojawi się bąbelkowy wyjątek. Aby wyświetlić więcej szczegółów, wybierz przycisk **Wyświetl szczegóły** :

![Wyświetl więcej szczegółów dotyczących wyjątku](media/troubleshooting-image2.png)

Spowoduje to wyświetlenie okna dialogowego **Pokaż szczegóły** , w którym znajdują się więcej informacji na temat wyjątku:

![Pokaż okno dialogowe szczegółów](media/troubleshooting-image3.png)

Ważne sekcje okna dialogowego, które są ponumerowane powyżej, opisano szczegółowo poniżej:

1. Typ wyjątku, który wyświetla pełną nazwę zaobserwowanego typu wyjątku.
2. Komunikat o wyjątku, który pokazuje wartość właściwości Message obiektu Exception.
3. Wewnętrzny typ wyjątku, który wyświetla pełną nazwę typu wyjątku dla aktualnie wybranego wyjątku w wewnętrznym widoku drzewa wyjątków.
4. Komunikat o wyjątku wewnętrznym pokazuje wartość właściwości komunikat wybranego wyjątku w wewnętrznym widoku drzewa wyjątków.
5. Widok ślad stosu. Można to zwinąć za pośrednictwem strzałki ujawniania i zawiera pozycje ramki stosu.
6. Przykład wpisów kodu niezwiązanych z użytkownikiem.
7. Przykład wpisów kodu użytkownika.
8. Widok właściwości, w którym są wyświetlane wszystkie właściwości i pola wyjątku. Można to zwinąć za pomocą strzałki ujawniania.
9. Wewnętrzny widok drzewa wyjątków. Wybierz wyjątki wewnętrzne w tym widoku za pomocą strzałek w górę/w dół lub z myszą lub Trackpad.
10. Domyślnie jest to ustawienie opcja **tylko kod projektu debugowania** w ustawieniach debugera jest ustawiona na. Zaznaczenie tego pola spowoduje, że cały kod niebędący użytkownikiem będzie zwijany do jednego wiersza w ślad stosu.
11. Przycisk kopiowania, aby skopiować `exception.ToString()` dane wyjściowe do Schowka.

Należy zauważyć, że niektóre z tych sekcji są widoczne tylko wtedy, gdy wyjątek ma wewnętrzny wyjątek.

## <a name="see-also"></a>Zobacz też

- [Zasoby rozwiązywania problemów z błędami IDE (Visual Studio w systemie Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)
---
title: Krok 7. Zachować widoczność par
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0114800d2f968db79215afffab34fdd701bf0656
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946434"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7. Zachować widoczność par
Gra działa dobrze, dopóki gracz wybiera tylko pary ikon, które nie są zgodne. Rozważmy jednak, co się powinno zdarzyć, gdy gracz wybierze pasującą parę. Zamiast ukrywania okien przez włączanie czasomierza (za pomocą <xref:System.Windows.Forms.Timer.Start> metoda), gra powinna się zresetować, aby go jest już rejestrowanie informacji o wszystkich etykiet używających `firstClicked` i `secondClicked` odwoływać się do zmiennych, bez resetowania kolory dla dwóch etykiet, które zostały wybrane.

## <a name="to-keep-pairs-visible"></a>Aby zachować widoczność par

1.  Dodaj następujący kod `if` instrukcję, aby `label_Click()` metody obsługi zdarzeń, pod koniec kodu, tuż nad instrukcją uruchomienia czasomierza. Przyjrzyj się kodowi podczas dodawania go do programu. Zastanów się, jak działa kod.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     W pierwszym wierszu `if` dodanej instrukcji sprawdza, czy ikona w pierwszej etykiecie, którą wybrał gracz, jest taka sama, jak ikona w drugiej etykiety. Jeśli ikony są identyczne, program wykonuje trzy instrukcje między nawiasami klamrowymi w C# lub trzy instrukcje w `if` instrukcji w języku Visual Basic. Pierwsze dwie instrukcje resetują `firstClicked` i `secondClicked` zmienne odwołania, tak aby ich już przechowywać informacji o dowolne etykiety. (Być może rozpoznajesz te dwie instrukcje z czasomierza <xref:System.Windows.Forms.Timer.Tick> programu obsługi zdarzeń.) Trzecia instrukcja to instrukcja `return` instrukcję, która mówi programowi, aby pominąć resztę instrukcji w metodzie bez ich wykonania.

     Jeśli Programowanie w języku Visual C#, być może zauważono, że część kodu używa pojedynczego znaku równości (`=`), podczas gdy inne instrukcje używają dwóch znaków równości (`==`). Zastanów się, dlaczego `=` jest używana w niektórych miejscach, ale `==` jest używana w innych miejscach.

     To jest dobry przykład, który pokazuje różnicę. Dokładnie Przeanalizuj kod w nawiasach w `if` instrukcji.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Następnie Przyjrzyj się bliżej pierwszej instrukcji w bloku kodu po `if` instrukcji.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Pierwsza z tych dwóch instrukcji sprawdza, czy dwie ikony są takie same. Ponieważ dwie wartości są porównywane, program Visual C# używa `==` operatora równości. Druga instrukcja faktycznie zmienia wartość (o nazwie *przypisania*), ustawiając `firstClicked` zmienną odwołania do `null` je zresetować. Dlatego używa `=` operator przypisania zamiast tego. Visual C# stosuje `=` do ustawiania wartości, a `==` do porównania. Visual Basic stosuje `=` zarówno przypisanie zmiennej, jak i porównań.

2.  Zapisz i uruchom program, a następnie zacznij wybierać ikony na formularzu. Jeśli wybierzesz parę, która nie pasuje, wyzwala się zdarzenie czasomierza Takt i obie ikony znikają. Jeśli wybierzesz pasującą parę nowy `if` wykonuje instrukcję, a instrukcja return spowoduje, że metoda pominie kod uruchamiający czasomierz, tak że ikony pozostaną widoczne, jak pokazano na poniższej ilustracji.

     ![Gra tworzona w ramach tego samouczka](../ide/media/express_finishedgame.png)
**gra w dopasowywanie** z widocznymi parami ikon

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy gracz wygrał](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodaj czasomierz](../ide/step-6-add-a-timer.md).

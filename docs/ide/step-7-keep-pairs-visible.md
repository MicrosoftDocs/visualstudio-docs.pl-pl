---
title: Krok 7. Zachowywanie widoczności par
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0216d778278f02f7fc63630f4ff6ce90c755e3c
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118649"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7. Zachowywanie widoczności par
Gra działa dobrze, dopóki gracz wybiera tylko pary ikon, które nie są zgodne. Rozważmy jednak, co się powinno zdarzyć, gdy gracz wybierze pasującą parę. Zamiast sprawiać, że ikony znikają, włączając czasomierz (przy użyciu <xref:System.Windows.Forms.Timer.Start> metody), gra powinna zostać zresetowana tak, aby nie śledzić żadnych etykiet `firstClicked` przy użyciu i `secondClicked` zmiennych odwołania, bez resetowania kolory dla dwóch wybranych etykiet.

## <a name="to-keep-pairs-visible"></a>Aby zachować widoczność par

1. Dodaj następującą `if` instrukcję `label_Click()` do metody obsługi zdarzeń, blisko końca kodu tuż powyżej instrukcji, w której uruchomiono czasomierz. Przyjrzyj się kodowi podczas dodawania go do programu. Zastanów się, jak działa kod.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     Pierwszy wiersz `if` właśnie dodanej instrukcji sprawdza, czy ikona w pierwszej etykiecie, którą wybiera gracz, jest taka sama jak ikona w drugiej etykiecie. Jeśli ikony są identyczne, program wykonuje trzy instrukcje między nawiasami klamrowymi w C# lub trzech `if` instrukcjach w instrukcji Visual Basic. Pierwsze dwie instrukcje resetują `firstClicked` zmienne i `secondClicked` , aby nie śledzić żadnej etykiety. (Można rozpoznać te dwie instrukcje z programu obsługi <xref:System.Windows.Forms.Timer.Tick> zdarzeń czasomierza). Trzecia instrukcja to `return` instrukcja, która informuje program, aby pominąć pozostałe instrukcje w metodzie bez ich wykonywania.

     W przypadku programowania w C#wizualizacji, można zauważyć, że część kodu używa pojedynczego znaku równości (`=`), podczas gdy inne instrukcje używają dwóch znaków równości (`==`). Rozważmy `=` , dlaczego jest używany w niektórych `==` miejscach, ale jest używany w innych miejscach.

     To jest dobry przykład, który pokazuje różnicę. Zanotuj uważnie kod między nawiasami w `if` instrukcji.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Następnie poszukaj blisko pierwszej instrukcji w bloku kodu po `if` instrukcji.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Pierwsza z tych dwóch instrukcji sprawdza, czy dwie ikony są takie same. Ponieważ dwie wartości są porównywane, program Visual C# używa `==` operatora równości. Druga instrukcja faktycznie zmienia wartość (nazywane *przypisaniem*), ustawiając `firstClicked` zmienną `null` odwołania równą do resetowania. Dlatego używa `=` operatora przypisania zamiast tego. C# Wizualizacja `=` używa do ustawiania wartości i `==` porównywania ich. Visual Basic używa `=` zarówno do przypisywania zmiennych, jak i porównywania.

2. Zapisz i uruchom program, a następnie zacznij wybierać ikony na formularzu. Jeśli wybierzesz parę, która nie pasuje, wyzwala się zdarzenie czasomierza Takt i obie ikony znikają. W przypadku wybrania pary zgodnej, Nowa `if` instrukcja zostanie wykonana, a instrukcja return powoduje, że metoda pominie kod, który uruchamia czasomierz, więc ikony pozostaną widoczne, jak pokazano na poniższej ilustracji.

     ![Gra, którą tworzysz w tym samouczku](../ide/media/express_finishedgame.png)
,**dopasowuje grę** z widocznymi parami ikon

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy odtwarzacz został](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)wygrany.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6. Dodawanie czasomierza](../ide/step-6-add-a-timer.md).

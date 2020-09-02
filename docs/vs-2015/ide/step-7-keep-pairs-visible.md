---
title: Krok 7. zachowanie widoczności par | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d7981ca81839cc8d0959cf5ae75c6d9a001d39a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646946"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7. Zachowanie widoczności par
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gra działa dobrze, dopóki gracz wybiera tylko pary ikon, które nie są zgodne. Rozważmy jednak, co się powinno zdarzyć, gdy gracz wybierze pasującą parę. Zamiast sprawiać, że ikony są znikane przez włączenie czasomierza (przy użyciu `Start()` metody), gra powinna zostać zresetowana tak, aby nie śledzić żadnych etykiet przy użyciu `firstClicked` i `secondClicked` zmiennych odwołania, bez resetowania kolorów dla dwóch wybranych etykiet.

### <a name="to-keep-pairs-visible"></a>Aby zachować widoczność par

1. Dodaj następującą `if` instrukcję do `label_Click()` metody obsługi zdarzeń, blisko końca kodu tuż powyżej instrukcji, w której uruchomiono czasomierz. Przyjrzyj się kodowi podczas dodawania go do programu. Zastanów się, jak działa kod.

     [!code-csharp[VbExpressTutorial4Step7#9](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs#9)]
     [!code-vb[VbExpressTutorial4Step7#9](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb#9)]

     Pierwszy wiersz `if` właśnie dodanej instrukcji sprawdza, czy ikona w pierwszej etykiecie, którą wybiera gracz, jest taka sama jak ikona w drugiej etykiecie. Jeśli ikony są identyczne, program wykonuje trzy instrukcje między nawiasami klamrowymi w języku C# lub trzy instrukcje `if` w instrukcji w Visual Basic. Pierwsze dwie instrukcje resetują `firstClicked` zmienne i, `secondClicked` aby nie śledzić żadnej etykiety. (Można rozpoznać te dwie instrukcje z programu obsługi zdarzeń taktu czasomierza). Trzecia instrukcja to `return` instrukcja, która informuje program, aby pominąć pozostałe instrukcje w metodzie bez ich wykonywania.

     W przypadku programowania w języku Visual C# można zauważyć, że część kodu używa pojedynczego znaku równości ( `=` ), podczas gdy inne instrukcje używają dwóch znaków równości ( `==` ). Rozważmy, dlaczego `=` jest używany w niektórych miejscach, ale `==` jest używany w innych miejscach.

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

     Pierwsza z tych dwóch instrukcji sprawdza, czy dwie ikony są takie same. Ponieważ dwie wartości są porównywane, program Visual C# używa `==` operatora równości. Druga instrukcja faktycznie zmienia wartość (nazywane *przypisaniem*), ustawiając `firstClicked` zmienną odwołania równą `null` do resetowania. Dlatego używa `=` operatora przypisania zamiast tego. Program Visual C# używa `=` do ustawiania wartości i `==` porównywania ich. Visual Basic używa `=` zarówno do przypisywania zmiennych, jak i porównywania.

2. Zapisz i uruchom program, a następnie zacznij wybierać ikony na formularzu. Jeśli wybierzesz parę, która nie pasuje, wyzwala się zdarzenie czasomierza Takt i obie ikony znikają. W przypadku wybrania pary zgodnej, Nowa `if` instrukcja zostanie wykonana, a instrukcja return powoduje, że metoda pominie kod, który uruchamia czasomierz, więc ikony pozostaną widoczne, jak pokazano na poniższej ilustracji.

     ![Gra utworzona w tym samouczku](../ide/media/express-finishedgame.png "Express_FinishedGame") Gra w dopasowywanie z widocznymi parami ikon

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy odtwarzacz wykupił](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md).

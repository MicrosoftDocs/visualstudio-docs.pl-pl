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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646946"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7. Zachowanie widoczności par
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gra działa dobrze, dopóki gracz wybiera tylko pary ikon, które nie są zgodne. Rozważmy jednak, co się powinno zdarzyć, gdy gracz wybierze pasującą parę. Zamiast sprawiać, że ikony znikają, włączając czasomierz (przy użyciu metody `Start()`), gra należy zresetować, tak aby nie śledził już żadnych etykiet przy użyciu `firstClicked` i `secondClicked` zmiennych odwołania, bez resetowania kolorów dla obu tych elementów. wybrane etykiety.

### <a name="to-keep-pairs-visible"></a>Aby zachować widoczność par

1. Dodaj następującą instrukcję `if` do metody obsługi zdarzeń `label_Click()`, pod koniec kodu tuż przed instrukcją uruchomienia czasomierza. Przyjrzyj się kodowi podczas dodawania go do programu. Zastanów się, jak działa kod.

     [!code-csharp[VbExpressTutorial4Step7#9](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs#9)]
     [!code-vb[VbExpressTutorial4Step7#9](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb#9)]

     Pierwszy wiersz właśnie dodanej instrukcji `if` sprawdza, czy ikona w pierwszej etykiecie wybrana przez odtwarzacz jest taka sama jak ikona w drugiej etykiecie. Jeśli ikony są identyczne, program wykonuje trzy instrukcje między nawiasami klamrowymi w C# lub trzy instrukcje w instrukcji `if` w Visual Basic. Pierwsze dwie instrukcje resetują `firstClicked` i `secondClicked` zmiennych odwołania, aby nie śledzili żadnej etykiety. (Można rozpoznać te dwie instrukcje z programu obsługi zdarzeń taktu czasomierza). Trzecia instrukcja jest instrukcją `return`, która informuje program, aby pominąć pozostałe instrukcje w metodzie bez wykonywania tych czynności.

     W przypadku programowania w C#wizualizacji, można zauważyć, że część kodu używa pojedynczego znaku równości (`=`), podczas gdy inne instrukcje używają dwóch znaków równości (`==`). Rozważ, dlaczego `=` jest używana w niektórych miejscach, ale `==` jest używana w innych miejscach.

     To jest dobry przykład, który pokazuje różnicę. Zanotuj uważnie kod między nawiasami w instrukcji `if`.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Następnie poszukaj blisko pierwszej instrukcji w bloku kodu po instrukcji `if`.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Pierwsza z tych dwóch instrukcji sprawdza, czy dwie ikony są takie same. Ponieważ dwie wartości są porównywane, program Visual C# używa operatora równości `==`. Druga instrukcja faktycznie zmienia wartość (nazywane *przypisaniem*), ustawiając zmienną odwołania `firstClicked` równą `null`, aby ją zresetować. Dlatego używa zamiast tego operatora przypisania `=`. Wizualizacja C# używa `=` do ustawiania wartości i `==` do ich porównania. Visual Basic używa `=` do przypisywania zmiennych i porównywania.

2. Zapisz i uruchom program, a następnie zacznij wybierać ikony na formularzu. Jeśli wybierzesz parę, która nie pasuje, wyzwala się zdarzenie czasomierza Takt i obie ikony znikają. W przypadku wybrania pary zgodnej z nową instrukcją `if`, a instrukcja return powoduje, że metoda pominie kod, który uruchamia czasomierz, więc ikony pozostaną widoczne, jak pokazano na poniższej ilustracji.

     ![Gra utworzona w tym samouczku](../ide/media/express-finishedgame.png "Express_FinishedGame") Gra w dopasowywanie z widocznymi parami ikon

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 8: Dodaj metodę, aby sprawdzić, czy odtwarzacz wykupił](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md).

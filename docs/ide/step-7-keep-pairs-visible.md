---
title: Krok 7. Zachowywanie widoczności par
description: Dowiedz się, jak dodać instrukcję if, a jeśli gracz wybierze pasującą parę ikon, ikony pozostaną widoczne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 341d0e54af991390a3ff5146a29d9e66ad7c737e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214151"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7. Zachowywanie widoczności par
Gra działa dobrze, dopóki gracz wybiera tylko pary ikon, które nie są zgodne. Rozważmy jednak, co się powinno zdarzyć, gdy gracz wybierze pasującą parę. Zamiast sprawiać, że ikony są znikane przez włączenie czasomierza (przy użyciu <xref:System.Windows.Forms.Timer.Start> metody), gra powinna zostać zresetowana tak, aby nie śledzić żadnych etykiet przy użyciu `firstClicked` i `secondClicked` zmiennych odwołania, bez resetowania kolorów dla dwóch wybranych etykiet.

## <a name="to-keep-pairs-visible"></a>Aby zachować widoczność par

1. Dodaj następującą `if` instrukcję do `label_Click()` metody obsługi zdarzeń, blisko końca kodu tuż powyżej instrukcji, w której uruchomiono czasomierz. Przyjrzyj się kodowi podczas dodawania go do programu. Zastanów się, jak działa kod.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb" id="Snippet9":::

     > [!IMPORTANT]
     > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu w języku C# lub fragment kodu Visual Basic.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Pierwszy wiersz `if` właśnie dodanej instrukcji sprawdza, czy ikona w pierwszej etykiecie, którą wybiera gracz, jest taka sama jak ikona w drugiej etykiecie. Jeśli ikony są identyczne, program wykonuje trzy instrukcje między nawiasami klamrowymi w języku C# lub trzy instrukcje `if` w instrukcji w Visual Basic. Pierwsze dwie instrukcje resetują `firstClicked` zmienne i, `secondClicked` aby nie śledzić żadnej etykiety. (Można rozpoznać te dwie instrukcje z <xref:System.Windows.Forms.Timer.Tick> programu obsługi zdarzeń czasomierza). Trzecia instrukcja to `return` instrukcja, która informuje program, aby pominąć pozostałe instrukcje w metodzie bez ich wykonywania.

     W przypadku programowania w języku C# można zauważyć, że część kodu używa pojedynczego znaku równości ( `=` ), podczas gdy inne instrukcje używają dwóch znaków równości ( `==` ). Rozważmy, dlaczego `=` jest używany w niektórych miejscach, ale `==` jest używany w innych miejscach.

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

     Pierwsza z tych dwóch instrukcji sprawdza, czy dwie ikony są takie same. Ponieważ dwie wartości są porównywane, program C# używa `==` operatora równości. Druga instrukcja faktycznie zmienia wartość (nazywane *przypisaniem*), ustawiając `firstClicked` zmienną odwołania równą `null` do resetowania. Dlatego używa `=` operatora przypisania zamiast tego. Język C# używa `=` do ustawiania wartości i `==` porównywania ich. Visual Basic używa `=` zarówno do przypisywania zmiennych, jak i porównywania.

2. Zapisz i uruchom program, a następnie zacznij wybierać ikony na formularzu. Jeśli wybierzesz parę, która nie pasuje, wyzwala się zdarzenie czasomierza Takt i obie ikony znikają. W przypadku wybrania pary zgodnej, Nowa `if` instrukcja zostanie wykonana, a instrukcja return powoduje, że metoda pominie kod, który uruchamia czasomierz, więc ikony pozostaną widoczne, jak pokazano na poniższej ilustracji.

     ![Gra tworzona w ramach tego samouczka](../ide/media/express_finishedgame.png)<br/>
***Pasująca gra** _ _with widocznych par ikon *

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 8: Dodaj metodę, aby sprawdzić, czy odtwarzacz wykupił](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md).

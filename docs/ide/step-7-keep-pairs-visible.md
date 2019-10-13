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
ms.openlocfilehash: 025e388185651e6b2effb0f53345f2e145e101b3
ms.sourcegitcommit: a5a54b147e772dc39e519da74ec41a0c25d99628
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72289592"
---
# <a name="step-7-keep-pairs-visible"></a>Krok 7. Zachowywanie widoczności par
Gra działa dobrze, dopóki gracz wybiera tylko pary ikon, które nie są zgodne. Rozważmy jednak, co się powinno zdarzyć, gdy gracz wybierze pasującą parę. Zamiast sprawiać, że ikony są znikane przez włączenie czasomierza (przy użyciu metody <xref:System.Windows.Forms.Timer.Start>), gra powinna zostać zresetowana tak, aby nie śledzić żadnych etykiet przy użyciu zmiennych odwołania `firstClicked` i `secondClicked`, bez resetowania kolorów dwóch wybrane etykiety.

## <a name="to-keep-pairs-visible"></a>Aby zachować widoczność par

1. Dodaj następującą instrukcję `if` do metody obsługi zdarzeń `label_Click()`, blisko końca kodu tuż powyżej instrukcji, w której uruchomiono czasomierz. Przyjrzyj się kodowi podczas dodawania go do programu. Zastanów się, jak działa kod.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Pierwszy wiersz właśnie dodanej instrukcji `if` sprawdza, czy ikona w pierwszej etykiecie wybrana przez odtwarzacz jest taka sama jak ikona w drugiej etykiecie. Jeśli ikony są identyczne, program wykonuje trzy instrukcje między nawiasami klamrowymi w C# lub trzy instrukcje w instrukcji `if` w Visual Basic. Pierwsze dwie instrukcje resetują zmienne odwołania `firstClicked` i `secondClicked`, aby nie śledzić żadnej etykiety. (Można rozpoznać te dwie instrukcje z procedury obsługi zdarzeń <xref:System.Windows.Forms.Timer.Tick> czasomierza.) Trzecia instrukcja to `return` instrukcji, która informuje program, aby pominąć resztę instrukcji w metodzie bez wykonywania tych czynności.

     W przypadku programowania w C#wizualizacji, można zauważyć, że część kodu używa pojedynczego znaku równości (`=`), podczas gdy inne instrukcje używają dwóch znaków równości (`==`). Rozważ, dlaczego `=` jest używana w niektórych miejscach, ale `==` jest używana w innych miejscach.

     To jest dobry przykład, który pokazuje różnicę. Zapoznaj się z dokładnym kodem między nawiasami w instrukcji `if`.

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

     Pierwsza z tych dwóch instrukcji sprawdza, czy dwie ikony są takie same. Ponieważ dwie wartości są porównywane, program Visual C# używa operatora równości `==`. Druga instrukcja faktycznie zmienia wartość (nazywane *przypisaniem*), ustawiając zmienną odwołania `firstClicked` równą `null`, aby zresetować ją. Dlatego używa zamiast tego operatora przypisania `=`. Wizualizacja C# używa `=` do ustawiania wartości i `==`, aby je porównać. Visual Basic używa `=` do przypisywania zmiennych i porównywania.

2. Zapisz i uruchom program, a następnie zacznij wybierać ikony na formularzu. Jeśli wybierzesz parę, która nie pasuje, wyzwala się zdarzenie czasomierza Takt i obie ikony znikają. W przypadku wybrania pary pasującej Nowa instrukcja `if` wykonuje instrukcję, a instrukcja return powoduje pominięcie kodu, który uruchamia czasomierz, więc ikony pozostają widoczne, jak pokazano na poniższej ilustracji.

     ![Game utworzone w tym samouczku @ no__t-1<br/>
**Gra w dopasowywanie** z widocznymi parami ikon

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [Step 8: Dodaj metodę, aby sprawdzić, czy odtwarzacz wygrał @ no__t-0.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Step 6: Dodaj czasomierz @ no__t-0.

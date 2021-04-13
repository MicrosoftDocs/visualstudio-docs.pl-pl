---
title: Krok 8. Dodawanie metody sprawdzania, czy gracz wygrał
description: Dowiedz się, jak dodać metodę, aby określić, czy gracz wygrał.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 931e39a4f3cf87fe2d147d90f2111c9a9db3faeb
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297005"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Krok 8. Dodawanie metody sprawdzania, czy gracz wygrał
Utworzyłeś zabawną grę, ale wymaga ona jeszcze jednej rzeczy. Gra powinna zakończyć się, gdy gracz usługi WINS, więc musisz dodać metodę, `CheckForWinner()` Aby sprawdzić, czy odtwarzacz wykupił.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Aby dodać metodę w celu sprawdzenia, czy gracz wygrał

1. Dodaj `CheckForWinner()` metodę do dolnej części kodu poniżej `timer1_Tick()` procedury obsługi zdarzeń, jak pokazano w poniższym kodzie.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

      > [!IMPORTANT]
      > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu w języku C# lub fragment kodu Visual Basic.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     Metoda używa innej `foreach` pętli w języku C# lub `For Each` pętli w Visual Basic do przechodzenia przez każdą etykietę w <xref:System.Windows.Forms.TableLayoutPanel> . Używa operatora równości ( `==` w języku C# i `=` w Visual Basic), aby sprawdzić kolor ikon każdej etykiety, aby sprawdzić, czy jest on zgodny z tłem. Jeśli kolory są zgodne, ikona pozostaje niewidoczna, a gracz nie dopasował wszystkich pozostałych ikon. W takim przypadku program używa `return` instrukcji, aby pominąć resztę metody. Jeśli pętla przechodzi przez wszystkie etykiety bez wykonywania `return` instrukcji, oznacza to, że wszystkie ikony w formularzu zostały dopasowane. Program wyświetli element MessageBox, który congratulate gracz na wygranie, a następnie wywoła metodę formularza, `Close()` Aby zakończyć grę.

2. Następnie należy <xref:System.Windows.Forms.Control.Click> wywołać nową metodę obsługi zdarzeń etykiety `CheckForWinner()` . Pamiętaj, że program sprawdza zwycięzcę natychmiast po pokazaniu drugiej ikony, którą wybierze gracz. Wyszukaj wiersz, w którym ustawisz kolor drugiej wybranej ikony, a następnie Wywołaj `CheckForWinner()` metodę bezpośrednio po tym, jak pokazano w poniższym kodzie.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

3. Zapisz i uruchom program. Zagraj w grę i dopasuj wszystkie ikony. Gdy wygrasz, program wyświetli element **MessageBox** gratulacjami (jak pokazano na poniższym zrzucie ekranu), a następnie zamknie to pole.

     ![Gra w dopasowywanie z MessageBox](../ide/media/express_tut4step8.png)<br/>
***Gra pasująca** _ _With * ***MessageBox***

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 9: Wypróbuj inne funkcje](../ide/step-9-try-other-features.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 7. Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md).

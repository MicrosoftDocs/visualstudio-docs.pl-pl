---
title: Pisanie kodu dla dodatkowych przycisków i pola wyboru
description: Dowiedz się, jak napisać kod dla dodatkowych przycisków i pola wyboru w samouczku Tworzenie obrazu przeglądarki.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 29d4dc70195d4c98653bc8503a079f462a502809
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214372"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru

Teraz wszystko jest gotowe do wykonania innych czterech metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz poznać większość z tego samouczka, wpisz kod i użyj funkcji IntelliSense.

Ten kod dodaje funkcję do przycisków, które zostały dodane wcześniej. Bez tego kodu przyciski nie wykonują żadnych czynności. Przyciski używają kodu w swoich <xref:System.Windows.Forms.Control.Click> zdarzeniach (a pole wyboru używa <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzenia) do wykonywania różnych czynności podczas aktywowania kontrolek. Na przykład `clearButton_Click` zdarzenie (lub `ClearButton_Click` ), które aktywuje się po wybraniu przycisku **Wyczyść obraz** , powoduje wymazanie bieżącego obrazu przez ustawienie jego właściwości **Image** na **wartość null** (lub **Nothing**). Każde zdarzenie w kodzie zawiera komentarze objaśniające, jak działa kod.

> [!TIP]
> Najlepszym rozwiązaniem jest zawsze Dodawanie komentarzy do kodu. Komentarze są informacjami dla osoby, które mają być odczytane, i warto pamiętać o tym, aby kod był zrozumiały. Wszystkie elementy w wierszu komentarza są ignorowane przez aplikację. W języku C# można skomentować wiersz, wpisując dwa ukośniki do przodu (//), a w Visual Basic komentarz wiersza, zaczynając od pojedynczego cudzysłowu (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Jak napisać kod dla dodatkowych przycisków i pola wyboru

Dodaj następujący kod do pliku kodu **Form1** (*Form1. cs* lub *Form1. vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet2":::

  :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet2":::

> [!NOTE]
> Kod może nie wyświetlać liter "camelCase".

## <a name="next-steps"></a>Następne kroki

* Aby przejść do następnego kroku samouczka, zobacz **[krok 11. Uruchamianie aplikacji i wypróbuj inne funkcje](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Zobacz też

* [Samouczek 2: Tworzenie kwizu matematycznego z limitem czasu](tutorial-2-create-a-timed-math-quiz.md)
* [Samouczek 3: Tworzenie gry w dopasowywanie](tutorial-3-create-a-matching-game.md)

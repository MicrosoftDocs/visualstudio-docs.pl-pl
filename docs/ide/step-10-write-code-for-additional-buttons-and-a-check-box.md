---
title: Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19c82238a0379e6b94e82bb1e34f20282ff4654f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930171"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru
Teraz możesz przystąpić do wykonania czterech pozostałych metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz dowiedzieć się maksymalnie dużo z tego samouczka, wpisz kod i korzystać z technologii IntelliSense.

 Ten kod dodaje funkcje do dodanych wcześniej przycisków. Bez tego kodu przyciski nie robią niczego. Przyciski używają kodu w ich <xref:System.Windows.Forms.Control.Click> zdarzenia (a pola wyboru używają <xref:System.Windows.Forms.CheckBox.CheckedChanged> zdarzeń) do różnych akcji podczas aktywacji formantów. Na przykład `clearButton_Click` zdarzenia, które uaktywnia się po wybraniu **Wyczyść obraz** przycisk, partycje powoduje usunięcie bieżącego obrazu poprzez ustawienie jego **obraz** właściwość **null**(ewentualnie **nic**). Każde zdarzenie w kodzie zawiera komentarze objaśniające, co dany kod realizuje.

 ![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# -5 wideo](http://go.microsoft.com/fwlink/?LinkId=205206). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.

> [!NOTE]
>  Najlepszym rozwiązaniem jest: Zawsze komentarz w kodzie. Komentarze są informacjami dla osoby, które można odczytać i poświęcić czas na zrozumienie kodu. Wszystko w wierszu komentarza jest ignorowane przez program. W języku Visual C# wiersz komentarza tworzy się przez wpisanie dwóch ukośników na początku (/ /), a w języku Visual Basic wiersz komentarza tworzy się, zaczynając od pojedynczego cudzysłowu (').

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Aby napisać kod dla dodatkowych przycisków i pola wyboru

-   Dodaj następujący kod, aby Twoje **Form1** pliku z kodem (*Form1.cs* lub *Form1.vb*). Wybierz **VB** kartę, aby wyświetlić kod języka Visual Basic.

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

-   Aby przejść do następnego kroku samouczka, zobacz [krok 11: Uruchamianie programu i próbowanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md).

-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: Przejrzyj, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

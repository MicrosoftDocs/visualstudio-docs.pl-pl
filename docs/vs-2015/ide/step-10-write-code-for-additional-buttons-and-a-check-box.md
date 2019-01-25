---
title: Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58e50e7d70c485a4a49564ec0a57ba03b74e4a85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786028"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Teraz możesz przystąpić do wykonania czterech pozostałych metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz dowiedzieć się maksymalnie dużo z tego samouczka, wpisz kod i korzystać z technologii IntelliSense.  
  
 Ten kod dodaje funkcje do dodanych wcześniej przycisków. Bez tego kodu przyciski nie robią niczego. Przyciski używają kodu w ich `Click` zdarzenia (a pola wyboru używają `CheckChanged` zdarzeń) do różnych akcji podczas aktywacji formantów. Na przykład `clearButton_Click` zdarzenia, które uaktywnia się po wybraniu **Wyczyść obraz** przycisk, partycje powoduje usunięcie bieżącego obrazu poprzez ustawienie jego `Image` właściwości `null` (lub `nothing`). Każde zdarzenie w kodzie zawiera komentarze objaśniające, co dany kod realizuje.  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# — wideo 5](http://go.microsoft.com/fwlink/?LinkId=205206). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
> [!NOTE]
>  Najlepszym rozwiązaniem jest: Zawsze komentarz w kodzie. Komentarze są informacjami dla osoby, które można odczytać i poświęcić czas na zrozumienie kodu. Wszystko w wierszu komentarza jest ignorowane przez program. W języku Visual C# wiersz komentarza tworzy się przez wpisanie dwóch ukośników na początku (/ /), a w języku Visual Basic wiersz komentarza tworzy się, zaczynając od pojedynczego cudzysłowu (').  
  
### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Aby napisać kod dla dodatkowych przycisków i pola wyboru  
  
-   Dodaj następujący kod do pliku kodu formularza Form1 (Form1.cs lub Form1.vb). Wybierz **VB** kartę, aby wyświetlić kod języka Visual Basic.  
  
     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 11: Uruchamianie programu i próbowanie innych funkcji](../ide/step-11-run-your-program-and-try-other-features.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: Przejrzyj, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

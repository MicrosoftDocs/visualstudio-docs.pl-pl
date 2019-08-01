---
title: Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10d1dcd4cb4a4dfca76d8af3fe6690076d91c72c
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416684"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru
Teraz wszystko jest gotowe do wykonania innych czterech metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz poznać większość z tego samouczka, wpisz kod i użyj funkcji IntelliSense.

 Ten kod dodaje funkcję do przycisków, które zostały dodane wcześniej. Bez tego kodu przyciski nie wykonują żadnych czynności. Przyciski używają kodu w swoich <xref:System.Windows.Forms.Control.Click> zdarzeniach (a pole wyboru <xref:System.Windows.Forms.CheckBox.CheckedChanged> używa zdarzenia) do wykonywania różnych czynności podczas aktywowania kontrolek. Na `clearButton_Click` przykład zdarzenie, które aktywuje się po wybraniu przycisku **Wyczyść obraz** , powoduje wymazanie bieżącego obrazu przez ustawienie jego właściwości **Image** na **wartość null** (lub **Nothing**). Każde zdarzenie w kodzie zawiera komentarze objaśniające, jak działa kod.

 ![link do wideo](../data-tools/media/playvideo.gif)dla wersji wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [samouczek 1: Utwórz przeglądarkę obrazów w C# pliku wideo 5.](http://go.microsoft.com/fwlink/?LinkId=205206) Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

> [!NOTE]
> Najlepszym rozwiązaniem jest: Zawsze Skomentuj swój kod. Komentarze są informacjami dla osoby, które mają być odczytane, i warto pamiętać o tym, aby kod był zrozumiały. Wszystkie elementy w wierszu komentarza są ignorowane przez program. W wizualizacji C#możesz dodać komentarz do wiersza, wpisując dwa ukośniki do przodu (//), a w Visual Basic skomentować linię, zaczynając od pojedynczego cudzysłowu (').

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Aby napisać kod dla dodatkowych przycisków i pola wyboru

- Dodaj następujący kod do pliku kodu **Form1** (*Form1.cs* lub *Form1. vb*). Wybierz kartę **VB** , aby wyświetlić kod Visual Basic.

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 11: Uruchom program i wypróbuj inne funkcje](../ide/step-11-run-your-program-and-try-other-features.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: Przejrzyj, Skomentuj i Przetestuj swój kod](../ide/step-9-review-comment-and-test-your-code.md).

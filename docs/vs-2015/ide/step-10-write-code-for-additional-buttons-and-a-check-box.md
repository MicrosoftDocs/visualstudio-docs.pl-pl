---
title: Krok 10. Pisanie kodu dla dodatkowych przycisków i pola wyboru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75081ae9c1183b470cd3197589cbf4134fe4a97b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667329"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10. Zapisywanie kodu dla dodatkowych przycisków i pola wyboru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Teraz wszystko jest gotowe do wykonania innych czterech metod. Możesz skopiować i wkleić ten kod, ale jeśli chcesz poznać większość z tego samouczka, wpisz kod i użyj funkcji IntelliSense.

 Ten kod dodaje funkcję do przycisków, które zostały dodane wcześniej. Bez tego kodu przyciski nie wykonują żadnych czynności. Przyciski używają kodu w swoich zdarzeniach `Click` (i pole wyboru używa zdarzenia `CheckChanged`) do wykonywania różnych czynności podczas aktywowania kontrolek. Na przykład zdarzenie `clearButton_Click`, które aktywuje się po wybraniu przycisku **Wyczyść obraz** , powoduje wymazanie bieżącego obrazu przez ustawienie jego właściwości `Image` na `null` (lub `nothing`). Każde zdarzenie w kodzie zawiera komentarze objaśniające, jak działa kod.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 5](http://go.microsoft.com/fwlink/?LinkId=205216) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# pliku wideo 5](http://go.microsoft.com/fwlink/?LinkId=205206). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

> [!NOTE]
> Najlepszym rozwiązaniem jest zawsze Dodawanie komentarzy do kodu. Komentarze są informacjami dla osoby, które mają być odczytane, i warto pamiętać o tym, aby kod był zrozumiały. Wszystkie elementy w wierszu komentarza są ignorowane przez program. W wizualizacji C#możesz dodać komentarz do wiersza, wpisując dwa ukośniki do przodu (//), a w Visual Basic skomentować linię, zaczynając od pojedynczego cudzysłowu (').

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Aby napisać kod dla dodatkowych przycisków i pola wyboru

- Dodaj następujący kod do pliku kodu Form1 (Form1.cs lub Form1. vb). Wybierz kartę **VB** , aby wyświetlić kod Visual Basic.

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 11. Uruchamianie programu i wypróbuj inne funkcje](../ide/step-11-run-your-program-and-try-other-features.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 9: przeglądanie, komentowanie i testowanie kodu](../ide/step-9-review-comment-and-test-your-code.md).

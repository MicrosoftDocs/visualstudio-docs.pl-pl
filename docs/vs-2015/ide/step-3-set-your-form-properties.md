---
title: Krok 3. Ustawianie właściwości formularza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d5f3f02e89e77b63420d4a04062d7b661c0c9f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671813"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3. Ustawienie właściwości formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następnie użyj okna **Właściwości** , aby zmienić wygląd formularza.

 ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [Samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic — wideo 1](http://go.microsoft.com/fwlink/?LinkId=205209) lub [Samouczek 1: Tworzenie przeglądarki obrazów w C# wideo 1](http://go.microsoft.com/fwlink/?LinkId=205199). Te filmy wideo korzystają ze starszej wersji programu Visual Studio, więc istnieją niewielkie różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednak koncepcje i procedury działają podobnie w bieżącej wersji programu Visual Studio.

### <a name="to-set-your-form-properties"></a>Aby ustawić właściwości formularza

1. Upewnij się, że szukasz Projektant formularzy systemu Windows. W zintegrowanym środowisku programistycznym (IDE) programu Visual Studio wybierz kartę **Form1.cs [Design]** (lub kartę **Form1. vb [Design]** w Visual Basic).

2. Wybierz dowolne miejsce wewnątrz formularza **Form1** , aby go zaznaczyć. Sprawdź okno **Właściwości** , które teraz powinno być wyświetlane właściwości formularza. Formularze mają różne właściwości. Na przykład można ustawić kolor pierwszego planu i tła, tekst tytułu, który pojawia się w górnej części formularza, rozmiar formularza i inne właściwości.

   > [!NOTE]
   > Jeśli okno **Właściwości** nie zostanie wyświetlone, Zatrzymaj program, wybierając kwadratowy przycisk **Zatrzymaj debugowanie** na pasku narzędzi lub po prostu Zamknij okno. Jeśli program jest zatrzymany i nadal nie widzisz okna **Właściwości** , na pasku menu wybierz **Widok**, **okno właściwości**.

3. Po wybraniu formularza Znajdź właściwość **tekst** w oknie **Właściwości** . W zależności od tego, jak lista jest sortowana, może być konieczne przewinięcie w dół. Wybierz **tekst**, wpisz **Podgląd obrazów**, a następnie wybierz klawisz ENTER.  Formularz powinien teraz mieć **obraz** tekstu na pasku tytułu, a okno **Właściwości** powinno wyglądać podobnie do poniższej ilustracji.

    ![Okno właściwości](../ide/media/express-edittextproperty.png "Express_EditTextProperty") okno Właściwości

   > [!NOTE]
   > Właściwości mogą być uporządkowane według kategorii lub widoku alfabetycznego. Można przełączać się między tymi dwoma widokami za pomocą przycisków w oknie **Właściwości** . W tym samouczku łatwiej jest znaleźć właściwości w widoku alfabetycznym.

4. Wróć do Projektant formularzy systemu Windows. Wybierz prawy dolny uchwyt przeciągania, czyli mały biały kwadrat w prawym dolnym rogu formularza i pojawia się w następujący sposób.

    ![Przeciągnij uchwyt](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag") Przeciągnij uchwyt

    Przeciągnij uchwyt, aby zmienić rozmiar formularza, tak aby forma była szersza i nieco większa.

5. Sprawdź okno **Właściwości** i Zauważ, że właściwość **size** została zmieniona. Właściwość **size** zmienia się za każdym razem, gdy zmieniany jest rozmiar formularza. Spróbuj przeciągnąć uchwyt formularza, aby zmienić jego rozmiar na rozmiar formularza około 550, 350 (nie musi być dokładne), który powinien być dobrze przydatny dla tego projektu. Alternatywnie można wprowadzić wartości bezpośrednio we właściwości **size** , a następnie wybrać klawisz ENTER.

6. Uruchom ponownie program. Pamiętaj, że możesz użyć dowolnej z poniższych metod, aby uruchomić program.

   - Wybierz klawisz **F5** .

   - Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie**.

   - Na pasku narzędzi wybierz przycisk **Rozpocznij debugowanie** , który pojawia się w następujący sposób.

      ![Przycisk paska narzędzi Rozpocznij debugowanie](../ide/media/express-icondebug.png "Express_IconDebug") Przycisk paska narzędzi Rozpocznij debugowanie

     Tak jak wcześniej, środowisko IDE kompiluje i uruchamia program, a okno pojawia się.

7. Przed przejściem do następnego kroku Zatrzymaj program, ponieważ środowisko IDE nie pozwala na zmianę programu w trakcie jego działania. Pamiętaj, że możesz użyć dowolnej z poniższych metod, aby zatrzymać program.

   - Na pasku narzędzi wybierz przycisk **Zatrzymaj debugowanie** .

   - Na pasku menu wybierz **Debuguj**, **Zatrzymaj debugowanie**.

   - Wybierz przycisk X w górnym rogu okna **Form1** .

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 4. układ formularza przy użyciu formantu TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2. Uruchamianie programu](../ide/step-2-run-your-program.md).

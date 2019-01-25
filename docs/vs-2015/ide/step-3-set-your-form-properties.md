---
title: Krok 3. Ustawianie właściwości formularza | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d4a93dfca4681f93d0d2a5c45b189fd34c8dccca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782252"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3. Ustawianie właściwości formularza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następnie użyj **właściwości** okna, aby zmienić wygląd formularza.  
  
 ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo")wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 1](http://go.microsoft.com/fwlink/?LinkId=205209) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# — wideo 1](http://go.microsoft.com/fwlink/?LinkId=205199). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.  
  
### <a name="to-set-your-form-properties"></a>Aby ustawić właściwości formularza  
  
1. Upewnij się, że szukasz na Windows Forms Designer. W programie Visual Studio zintegrowane środowisko programistyczne (IDE), wybierz **Form1.cs [projekt]** karty (lub **Form1.vb [projekt]** kartę w języku Visual Basic).  
  
2. Wybierz dowolne miejsce wewnątrz formularza **Form1** aby go zaznaczyć. Przyjrzyj się **właściwości** okna, które powinno teraz pokazywać właściwości dla formularza. Formularze mają różne właściwości. Na przykład można ustawić pierwszego planu i kolor tła, tekst tytułu, który pojawia się w górnej części formularza, rozmiar formularza i inne właściwości.  
  
   > [!NOTE]
   >  Jeśli **właściwości** okno nie jest wyświetlane, Zatrzymaj program, wybierając kwadratowy **Zatrzymaj debugowanie** znajdujący się na pasku narzędzi lub zamknij okno. Jeśli program został zatrzymany, i nadal nie widzisz **właściwości** okna, na pasku menu wybierz **widoku**, **okno właściwości**.  
  
3. Po wybraniu formularza Znajdź **tekstu** właściwość **właściwości** okna. W zależności od tego, jak lista jest sortowana konieczne może być przewinięcie w dół. Wybierz **tekstu**, typ **Picture Viewer**, a następnie wybierz klawisz ENTER.  Formularz powinien mieć teraz tekst **Picture Viewer** na pasku tytułu, a **właściwości** okno powinno wyglądać podobnie do poniższej ilustracji.  
  
    ![Okno właściwości](../ide/media/express-edittextproperty.png "Express_EditTextProperty")  
   Okno właściwości  
  
   > [!NOTE]
   >  Właściwości można porządkować według widoku kategorii lub alfabetycznego. Możesz przełączać się między tymi dwoma widokami, korzystając z przycisków w **właściwości** okna. W tym samouczku jest łatwiej znaleźć właściwości za pomocą widoku alfabetycznie.  
  
4. Wróć do programu Windows Forms Designer. Wybierz formularz przeciągnij prawy dolny uchwyt, który jest białym kwadracikiem w dolnym rogu formularza i pojawia się w następujący sposób.  
  
    ![Przeciągnij uchwyt](../ide/media/express-bottomrt-drag.png "Express_BottomRT_Drag")  
   Przeciągnij uchwyt  
  
    Przeciągnij uchwyt, aby zmienić rozmiar formularza, aby formularz był szerszy i trochę wyższy.  
  
5. Przyjrzyj się **właściwości** okna i zwróć uwagę, że **rozmiar** właściwości została zmieniona. **Rozmiar** właściwość zmienia za każdym razem, możesz zmienić rozmiar formularza. Spróbuj przeciągnąć uchwyt formularza, aby zmienić jego rozmiar o około 550, 350 (nie trzeba być dokładnym), co powinno zadziałać dla tego projektu. Alternatywnie, można wprowadzić wartości bezpośrednio we **rozmiar** właściwości, a następnie naciśnij klawisz ENTER.  
  
6. Ponownie uruchom program. Należy pamiętać, że można użyć dowolnej z następujących metod, aby uruchomić program.  
  
   - Wybierz **F5** klucza.  
  
   - Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie**.  
  
   - Na pasku narzędzi wybierz **Rozpocznij debugowanie** przycisku, który wygląda następująco.  
  
      ![Rozpocznij debugowanie przycisku paska narzędzi](../ide/media/express-icondebug.png "Express_IconDebug")  
     Pasek narzędzi rozpoczęcia debugowania  
  
     Podobnie jak przedtem środowisko IDE kompiluje i uruchamia Twój program i zostanie wyświetlone okno.  
  
7. Przed przejściem do następnego kroku, zatrzymuje program, ponieważ IDE nie pozwoli zmienić programu, gdy jest uruchomiona. Należy pamiętać, że można użyć dowolnej z następujących metod, aby zatrzymać program.  
  
   -   Na pasku narzędzi wybierz **Zatrzymaj debugowanie** przycisku.  
  
   -   Na pasku menu wybierz **debugowania**, **Zatrzymaj debugowanie**.  
  
   -   Kliknij przycisk X w prawym górnym rogu **Form1** okna.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [krok 4: Określić układ formularza z formantem TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Uruchom Program](../ide/step-2-run-your-program.md).

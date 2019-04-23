---
title: Krok 3. Ustawianie właściwości formularza
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a26d6f72cee0f2718e84a9e2b671c2be7977bbd5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096247"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3. Ustawianie właściwości formularza
Następnie użyj **właściwości** okna, aby zmienić wygląd formularza.

 ![Link do wideo](../data-tools/media/playvideo.gif)wersja wideo tego tematu, zobacz [samouczek 1: Tworzenie przeglądarki obrazów w Visual Basic – wideo 1](http://go.microsoft.com/fwlink/?LinkId=205209) lub [samouczek 1: Tworzenie przeglądarki obrazów w C# -1 wideo](http://go.microsoft.com/fwlink/?LinkId=205199). W tych filmach wideo użyj wcześniejszej wersji programu Visual Studio, więc istnieją drobne różnice w niektórych poleceniach menu i innych elementach interfejsu użytkownika. Jednakże pojęcia i procedury działają podobnie w bieżącej wersji programu Visual Studio.

## <a name="to-set-your-form-properties"></a>Aby ustawić właściwości formularza

1. Pamiętaj, żeby widzieć **Windows Forms Designer**. W programie Visual Studio zintegrowane środowisko programistyczne (IDE), wybierz **Form1.cs [projekt]** karty (lub **Form1.vb [projekt]** kartę w języku Visual Basic).

2. Wybierz dowolne miejsce wewnątrz formularza **Form1** aby go zaznaczyć. Przyjrzyj się **właściwości** okna, które powinno teraz pokazywać właściwości dla formularza. Formularze mają różne właściwości. Na przykład można ustawić pierwszego planu i kolor tła, tekst tytułu, który pojawia się w górnej części formularza, rozmiar formularza i inne właściwości.

   > [!NOTE]
   >  Jeśli **właściwości** okno nie jest wyświetlane, Zatrzymaj program, wybierając kwadratowy **Zatrzymaj debugowanie** znajdujący się na pasku narzędzi lub zamknij okno. Jeśli program został zatrzymany, i nadal nie widzisz **właściwości** okna, na pasku menu wybierz **widoku** > **okno właściwości**.

3. Po wybraniu formularza Znajdź **tekstu** właściwość **właściwości** okna. W zależności od tego, jak lista jest sortowana konieczne może być przewinięcie w dół. Wybierz **tekstu**, typ **Picture Viewer**, a następnie wybierz **Enter**.  Formularz powinien mieć teraz tekst **Picture Viewer** na pasku tytułu, a **właściwości** okno powinno wyglądać podobnie do poniższej ilustracji.

    ![Okno właściwości](../ide/media/express_edittextproperty.png)
   **właściwości** okna

   > [!NOTE]
   >  Właściwości można porządkować według **kategorii** lub **alfabetycznie** widoku. Możesz przełączać się między tymi dwoma widokami, korzystając z przycisków w **właściwości** okna. W tym samouczku jest łatwiej znaleźć właściwości za pomocą **alfabetycznie** widoku.

4. Wróć do **Windows Forms Designer**. Wybierz formularz przeciągnij prawy dolny uchwyt, który jest białym kwadracikiem w dolnym rogu formularza i pojawia się w następujący sposób.

    ![Przeciągnij uchwyt](../ide/media/express_bottomrt_drag.png) przeciągnij uchwyt

    Przeciągnij uchwyt, aby zmienić rozmiar formularza, aby formularz był szerszy i trochę wyższy.

5. Przyjrzyj się **właściwości** okna i zwróć uwagę, że **rozmiar** właściwości została zmieniona. **Rozmiar** właściwość zmienia za każdym razem, możesz zmienić rozmiar formularza. Spróbuj przeciągnąć uchwyt formularza, aby zmienić jego rozmiar o około **550, 350** (nie trzeba być dokładnym), co powinno zadziałać dla tego projektu. Alternatywnie, można wprowadzić wartości bezpośrednio we **rozmiar** właściwości, a następnie wybierz **Enter** klucza.

6. Ponownie uruchom program. Należy pamiętać, że można użyć dowolnej z następujących metod, aby uruchomić program.

   - Wybierz **F5** klucza.

   - Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.

   - Na pasku narzędzi wybierz **Rozpocznij debugowanie** przycisku, który wygląda następująco.

      ![Rozpocznij debugowanie przycisku paska narzędzi](../ide/media/express_icondebug.png)
     **Rozpocznij debugowanie** przycisku paska narzędzi

     Podobnie jak przedtem środowisko IDE kompiluje i uruchamia Twój program i zostanie wyświetlone okno.

7. Przed przejściem do następnego kroku, zatrzymuje program, ponieważ IDE nie pozwoli zmienić programu, gdy jest uruchomiona. Należy pamiętać, że można użyć dowolnej z następujących metod, aby zatrzymać program.

   - Na pasku narzędzi wybierz **Zatrzymaj debugowanie** przycisku.

   - Na pasku menu wybierz **debugowania** > **Zatrzymaj debugowanie**.

   - Wybierz **X** przycisk w prawym górnym rogu **Form1** okna.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 4: Określić układ formularza z formantem TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 2: Uruchom program](../ide/step-2-run-your-program.md).

---
title: Krok 5. Dodawanie odwołań do etykiet
description: Dowiedz się, jak dodać odwołania do etykiet do formularza.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 393f71c3360371122e86dc078aaa97c6963db325
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296277"
---
# <a name="step-5-add-label-references"></a>Krok 5. Dodawanie odwołań do etykiet
Program musi śledzić, które kontrolki etykiet wybiera gracz. W tej chwili program pokazuje wszystkie etykiety wybrane przez gracza. Ale zaraz to zmienimy. Po wybraniu pierwszej etykiety program powinien wyświetlać ikonę etykiety. Po wybraniu drugiej etykiety program powinien wyświetlić obie ikony przez krótki czas i potem ponownie je ukryć. Program będzie teraz śledził, który formant Etykieta jest wybierany jako pierwszy, a który jest wybierany drugi przy użyciu *zmiennych odwołania*.

## <a name="to-add-label-references"></a>Aby dodać odwołania do etykiet

1. Dodaj odwołania do etykiet do formularza przy użyciu następującego kodu.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet5":::

     > [!IMPORTANT]
     > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu w języku C# lub fragment kodu Visual Basic.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Te zmienne odwołania wyglądają podobnie do instrukcji użytych wcześniej do dodawania obiektów (takich jak <xref:System.Windows.Forms.Timer> obiekty, <xref:System.Collections.Generic.List%601> obiekty i <xref:System.Random> obiekty) do formularza. Jednak te instrukcje nie powodują, że dwie kontrolki dodatkowej etykiety są wyświetlane w formularzu, ponieważ nie ma `new` słowa kluczowego użytego w żadnej z dwóch instrukcji. Bez `new` słowa kluczowego, żaden obiekt nie jest tworzony. Dlatego `firstClicked` i `secondClicked` są nazywane zmiennymi odwołania: po prostu śledzą obiekty etykiet (lub odwołują się do nich).

     Gdy zmienna nie śledzi obiektu, jest ustawiona na specjalną wartość zarezerwowaną: `null` w języku C# i `Nothing` w Visual Basic. Tak więc, gdy program zostanie uruchomiony, obie `firstClicked` i `secondClicked` są ustawione na `null` lub `Nothing` , co oznacza, że zmienne nie śledzą niczego.

2. Zmodyfikuj <xref:System.Windows.Forms.Control.Click> procedurę obsługi zdarzeń, aby używała nowej `firstClicked` zmiennej Reference. Usuń ostatnią instrukcję z `label_Click()` metody obsługi zdarzeń ( `clickedLabel.ForeColor = Color.Black;` ) i Zastąp ją następującą `if` instrukcją. (Pamiętaj, aby dołączyć komentarz i całą `if` instrukcję).

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet6":::

3. Zapisz i uruchom program. Wybierz jeden z formantów etykiet, pojawi się jego ikona.

4. Wybierz następny formant etykiety i zauważ, że nic się nie dzieje. Program śledzi już pierwszą etykietę, którą wybrał gracz, tak więc `firstClicked` nie jest równa `null` w języku C# lub `Nothing` w Visual Basic. Gdy `if` instrukcja sprawdzi, `firstClicked` czy jest równa `null` lub `Nothing` , stwierdza, że nie, i nie wykonuje instrukcji w `if` instrukcji. Dlatego tylko pierwsza wybrana ikona powoduje zmianę czerni, a inne ikony są niewidoczne, jak pokazano na poniższej ilustracji.

     ![Gra w dopasowywanie pokazująca jedną ikonę](../ide/media/express_tut4step5.png)<br/>
***Gra pasująca** _ _showing jedną ikonę *

     Tę sytuację należy rozwiązać w następnym kroku samouczka, dodając kontrolkę **czasomierz** .

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 6: Dodawanie czasomierza](../ide/step-6-add-a-timer.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 4. Dodawanie obsługi zdarzeń kliknięcia do każdej etykiety](../ide/step-4-add-a-click-event-handler-to-each-label.md).

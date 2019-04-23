---
title: Krok 6. Dodaj czasomierz
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9c1585555c4c8039687bc514338fc86b61a7002
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050708"
---
# <a name="step-6-add-a-timer"></a>Krok 6. Dodaj czasomierz
Następnie dodaj <xref:System.Windows.Forms.Timer> formantu do gry w dopasowywanie. Czasomierz czeka określoną liczbę milisekund, a następnie uruchamia zdarzenie, określane jako *znaczników*. Jest to przydatne dla rozpoczęcia czynności lub regularnego powtarzania czynności. W tym przypadku, będziesz używał czasomierza, aby umożliwić graczom wybór dwóch ikon, a jeśli ikony nie będą pasowały, ukryć te dwie ikony po krótkiej chwili.

## <a name="to-add-a-timer"></a>Aby dodać czasomierz

1. Z przybornika w **Windows Forms Designer**, wybierz **czasomierza** (w **składniki** kategorii), a następnie wybierz **Enter** klucza, lub Kliknij dwukrotnie czasomierz, aby dodać format czasomierza do formularza. Ikona czasomierza, o nazwie **Timer1**, powinien pojawić się w przestrzeni poniżej formularza, jak pokazano na poniższej ilustracji.

     ![Czasomierz](../ide/media/express_timer.png)
**czasomierza**

    > [!NOTE]
    >  Jeśli przybornik jest pusty, należy wybrać Projektant formularzy, a nie kod związany z formularzem, przed otwarciem przybornika.

2. Wybierz **Timer1** ikonę, aby wybrać czasomierz. W **właściwości** okna, przejdź z wyświetlania zdarzeń do wyświetlania właściwości. Następnie należy skonfigurować czasomierz **interwał** właściwości **750**, ale pozostawić jego **włączone** właściwością **False**. **Interwał** właściwość mówi czasomierzowi, o ile ma czekać między *impulsów*, lub kiedy jego <xref:System.Windows.Forms.Timer.Tick> zdarzeń. Wartość 750 mówi czasomierzowi, aby czekał trzy czwarte sekundy (750 milisekund), zanim uruchomi zdarzenie Taktu. Wywołasz <xref:System.Windows.Forms.Timer.Start> metodę, aby uruchomić timer tylko wtedy, gdy gracz wybierze drugą etykietę.

3. Czasomierz wybierz ikonę kontrolki w **Windows Forms Designer** , a następnie wybierz **Enter** klucza, lub kliknij dwukrotnie czasomierz, aby dodać pusty program obsługi zdarzeń taktu. Zastąp kod następującym kodem lub ręcznie wprowadź następujący kod do programu obsługi zdarzeń.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

     Program obsługi zdarzeń taktu wykonuje trzy rzeczy: Po pierwsze, sprawdza, czy czasomierz nie jest uruchomiony, wywołując <xref:System.Windows.Forms.Timer.Stop> metody. Następnie wykorzystuje dwie zmienne odniesienia, `firstClicked` i `secondClicked`, aby ponownie ukryć ikony dwóch etykiet, które wybrał gracz. Na koniec resetuje `firstClicked` i `secondClicked` odwoływać się do zmiennych do `null` w języku Visual C# i `Nothing` w języku Visual Basic. Ten krok jest ważny, ponieważ w ten sposób program się resetuje. Teraz go jest nie rejestrowanie informacji o dowolnej <xref:System.Windows.Forms.Label> kontrolek, a jego gracz jest gotowy do ponownie wybrać etykietę.

    > [!NOTE]
    >  Obiekt czasomierza ma `Start()` metodę, która uruchamia czasomierz, i `Stop()` metody, która go zatrzymuje. Po ustawieniu czasomierza **włączone** właściwości **True** w **właściwości** oknie zacznie jak należy jak najszybciej rozpoczyna się program. Ale gdy pozostawisz równa **False**, nie rozpoczyna odliczania, dopóki nie jego `Start()` metoda jest wywoływana. Normalnie, czasomierz wyzwala zdarzenie taktu cyklicznie wielokrotnie, za pomocą **interwał** właściwości w celu określenia liczby milisekund między taktami. Być może zauważono, jak czasomierza `Stop()` metoda jest wywoływana wewnątrz zdarzenia takt. To przestawia czasomierz w *tryb jednego zadziałania*, co oznacza, że w przypadku `Start()` metoda jest wywoływana, jego czeka przez określony interwał, wyzwala pojedyncze zdarzenie taktu i się zatrzymuje.

4. Aby wyświetlić działa nowy czasomierz, przejdź do edytora kodu, a następnie dodaj następujący kod do górnej i dolnej części `label_Click()` metody obsługi zdarzeń. (Dodajesz `if` instrukcji na górze i trzy instrukcje na dole, pozostała część metody pozostaje taka sama.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Kod w górnej części metody sprawdza, czy czasomierz został uruchomiony, sprawdzając wartość **włączone** właściwości. Dzięki temu, jeśli gracz wybierze pierwszy, a druga etykieta kontrolki i uruchomi się czasomierz, wybranie trzeciej etykiety nie spowoduje żadnego efektu.

     Kod w dolnej części metody ustawia `secondClicked` zmienną odwołania do śledzenia drugi formant etykiety, aby wybrał gracz, a następnie ustawia kolor ikony etykiety na czarny, aby stał się widoczny. Następnie uruchamia czasomierz w trybie jednego zadziałania, tak że czeka on 750 milisekund, a następnie uruchamia pojedyncze zdarzenie Taktu. Program obsługi zdarzeń takt czasomierza ukrywa dwie ikony i resetuje `firstClicked` i `secondClicked` zmienne odwołania, aby formularz był gracz jest gotowy do wyboru innej pary ikon.

5. Zapisz i uruchom program. Wybierz ikonę, stanie się widoczna.

6. Wybierz inną ikonę. Pojawi się ona na chwilę, a następnie obie ikony znikną. Powtórz to wiele razy. Formularz teraz śledzi pierwszą i drugą wybraną ikonę i używa czasomierza, aby wstrzymać przed zniknięciem ikon.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [kroku 7: Zachować widoczność par](../ide/step-7-keep-pairs-visible.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md).

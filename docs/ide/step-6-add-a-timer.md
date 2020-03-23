---
title: 'Krok 6: Dodaj timer'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23d050df688d4d1efec75245e6f48d748464170c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579314"
---
# <a name="step-6-add-a-timer"></a>Krok 6: Dodaj timer
Następnie należy dodać <xref:System.Windows.Forms.Timer> formant do pasującej gry. Czasomierz czeka określoną liczbę milisekund, a następnie uruchamia zdarzenie, określane jako *znacznik*. Jest to przydatne dla rozpoczęcia czynności lub regularnego powtarzania czynności. W tym przypadku, będziesz używał czasomierza, aby umożliwić graczom wybór dwóch ikon, a jeśli ikony nie będą pasowały, ukryć te dwie ikony po krótkiej chwili.

## <a name="to-add-a-timer"></a>Aby dodać czasomierz

1. W przyborniku w **programie Windows Forms Designer**wybierz pozycję **Timer** (w kategorii **Składniki),** a następnie wybierz klawisz **Enter** lub kliknij dwukrotnie czasomierz, aby dodać kontrolkę czasomierza do formularza. Ikona timera o nazwie **Timer1**powinna pojawić się w spacji pod formularzem, jak pokazano na poniższej ilustracji.

     ![Czasomierz](../ide/media/express_timer.png)<br/>
***Czasomierz***

    > [!NOTE]
    > Jeśli przybornik jest pusty, należy wybrać Projektant formularzy, a nie kod związany z formularzem, przed otwarciem przybornika.

2. Wybierz ikonę **Timer1,** aby wybrać czasomierz. W oknie **Właściwości** przełącz się z wyświetlania zdarzeń na wyświetlanie właściwości. Następnie ustaw właściwość **Interval czasomierza** na **750**, ale pozostaw jej właściwość **Enabled** ustawioną na **Fałsz**. **Interval** Właściwość informuje czasomierz, jak długo czekać między *znacznikami*lub kiedy wyzwala jego <xref:System.Windows.Forms.Timer.Tick> zdarzenia. Wartość 750 mówi czasomierzowi, aby czekał trzy czwarte sekundy (750 milisekund), zanim uruchomi zdarzenie Taktu. Wywołasz metodę, <xref:System.Windows.Forms.Timer.Start> aby uruchomić czasomierz tylko wtedy, gdy gracz wybierze drugą etykietę.

3. Wybierz ikonę formantu czasomierza w **projektancie formularzy windowsowych,** a następnie wybierz klawisz **Enter** lub kliknij dwukrotnie czasomierz, aby dodać pusty program obsługi zdarzeń Tick. Zastąp kod następującym kodem lub ręcznie wprowadź następujący kod do programu obsługi zdarzeń.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > Użyj formantu języka programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu języka C# lub fragment kodu języka Visual Basic.<br><br>![Sterowanie językiem programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Program obsługi zdarzeń Tick wykonuje trzy czynności: Najpierw upewnia się, <xref:System.Windows.Forms.Timer.Stop> że czasomierz nie jest uruchomiony przez wywołanie metody. Następnie używa dwóch zmiennych `firstClicked` referencyjnych i `secondClicked`, aby ikony dwóch etykiet, które gracz wybrał ponownie niewidoczne. Na koniec resetuje `firstClicked` i `secondClicked` odwołań `null` zmiennych w `Nothing` języku C# i visual basic. Ten krok jest ważny, ponieważ w ten sposób program się resetuje. Teraz nie śledzi żadnych <xref:System.Windows.Forms.Label> kontroli i jest gotowy, aby gracz ponownie wybrał etykietę.

    > [!NOTE]
    > Obiekt Timer ma `Start()` metodę, która uruchamia czasomierz i `Stop()` metodę, która go zatrzymuje. Po ustawieniu timera **Enabled** właściwość **true** w oknie **Właściwości,** zaczyna tykać natychmiast po rozpoczęciu programu. Ale po pozostawieniu go ustawionego na **False**, `Start()` nie zaczyna tykać, dopóki jego metoda nie zostanie wywołana. Zwykle czasomierz uruchamia jego Tick zdarzenia w kółko, za pomocą **Interval** właściwości, aby określić, ile milisekund czekać między znacznikami. Być może zauważyłeś, jak metoda `Stop()` czasomierza jest wywoływana wewnątrz Tick zdarzenia. To stawia timer w *trybie jednego strzału,* co oznacza, że gdy `Start()` metoda jest wywoływana, czeka na określony interwał, wyzwala pojedyncze zdarzenie Tick, a następnie zatrzymuje.

4. Aby wyświetlić nowy czasomierz w akcji, przejdź do edytora kodu i `label_Click()` dodaj następujący kod do górnej i dolnej części metody obsługi zdarzeń. (Dodajesz instrukcję `if` u góry i trzy instrukcje na dole; reszta metody pozostaje taka sama).)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Kod w górnej części metody sprawdza, czy czasomierz został uruchomiony przez sprawdzenie wartości **Enabled** właściwości. W ten sposób, jeśli gracz wybierze pierwszą i drugą kontrolkę Label i rozpocznie się timer, wybranie trzeciej etykiety nic nie zrobi.

     Kod w dolnej części metody `secondClicked` ustawia zmienną odniesienia do śledzenia drugiego Label kontroli, że gracz wybrał, a następnie ustawia kolor ikony tej etykiety na czarny, aby było widoczne. Następnie uruchamia czasomierz w trybie jednego zadziałania, tak że czeka on 750 milisekund, a następnie uruchamia pojedyncze zdarzenie Taktu. Program obsługi zdarzeń tick czasomierza ukrywa dwie ikony i resetuje zmienne `firstClicked` i `secondClicked` odwołania, dzięki czemu formularz jest gotowy do odtwarzacza, aby wybrać inną parę ikon.

5. Zapisz i uruchom program. Wybierz ikonę, stanie się widoczna.

6. Wybierz inną ikonę. Pojawi się ona na chwilę, a następnie obie ikony znikną. Powtórz to wiele razy. Formularz teraz śledzi pierwszą i drugą wybraną ikonę i używa czasomierza, aby wstrzymać przed zniknięciem ikon.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[Krok 7: Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [Krok 5: Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md).

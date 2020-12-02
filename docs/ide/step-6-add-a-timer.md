---
title: Krok 6. Dodawanie czasomierza
description: Dowiedz się, jak dodać <xref:System.Windows.Forms.Timer> kontrolkę do odpowiedniej gry.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
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
ms.openlocfilehash: 2684b197fc32b33081c8ecdfa8139b3c8f14e752
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480554"
---
# <a name="step-6-add-a-timer"></a>Krok 6. Dodawanie czasomierza
Następnie Dodaj <xref:System.Windows.Forms.Timer> kontrolkę do pasującej gry. Czasomierz czeka określoną liczbę milisekund, a następnie uruchamia zdarzenie, nazywane *znacznikiem*. Jest to przydatne dla rozpoczęcia czynności lub regularnego powtarzania czynności. W tym przypadku, będziesz używał czasomierza, aby umożliwić graczom wybór dwóch ikon, a jeśli ikony nie będą pasowały, ukryć te dwie ikony po krótkiej chwili.

## <a name="to-add-a-timer"></a>Aby dodać czasomierz

1. Z przybornika w **Projektant formularzy systemu Windows** wybierz **czasomierz** (w kategorii **składniki** ), a następnie wybierz klawisz **Enter** lub kliknij dwukrotnie czasomierz, aby dodać kontrolkę czasomierza do formularza. Ikona czasomierza o nazwie **Timer1** powinna pojawić się w miejscu poniżej formularza, jak pokazano na poniższej ilustracji.

     ![Czasomierz](../ide/media/express_timer.png)<br/>
**_Czasomierz_* _

    > [!NOTE]
    > Jeśli przybornik jest pusty, należy wybrać Projektant formularzy, a nie kod związany z formularzem, przed otwarciem przybornika.

2. Wybierz ikonę _ *Timer1**, aby wybrać czasomierz. W oknie **Właściwości** Przełącz się z wyświetlania zdarzeń, aby wyświetlić właściwości. Następnie ustaw właściwość **Interwał** czasomierza na **750**, ale pozostaw Właściwość **Enabled** ustawioną na **wartość false**. Właściwość **Interval** informuje czasomierz, jak długo czekać między *taktami* lub kiedy wyzwala <xref:System.Windows.Forms.Timer.Tick> zdarzenie. Wartość 750 mówi czasomierzowi, aby czekał trzy czwarte sekundy (750 milisekund), zanim uruchomi zdarzenie Taktu. Wywołasz metodę, <xref:System.Windows.Forms.Timer.Start> Aby uruchomić czasomierz dopiero po wybraniu drugiej etykiety przez odtwarzacz.

3. Wybierz ikonę sterowania czasomierzem w **Projektant formularzy systemu Windows** a następnie wybierz klawisz **Enter** lub kliknij dwukrotnie czasomierz, aby dodać pustą procedurę obsługi zdarzeń taktu. Zastąp kod następującym kodem lub ręcznie wprowadź następujący kod do programu obsługi zdarzeń.

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > Użyj kontrolki język programowania w prawym górnym rogu tej strony, aby wyświetlić fragment kodu w języku C# lub fragment kodu Visual Basic.<br><br>![Kontrolka języka programowania dla Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Program obsługi zdarzeń taktuje trzy rzeczy: najpierw sprawdza, czy czasomierz nie jest uruchomiony, wywołując <xref:System.Windows.Forms.Timer.Stop> metodę. Następnie używa dwóch zmiennych odwołań `firstClicked` i `secondClicked` , aby ikony dwóch etykiet, które gracz wybrał niewidoczny. Na koniec resetuje `firstClicked` `secondClicked` zmienne i odwołania do `null` języka C# i `Nothing` w Visual Basic. Ten krok jest ważny, ponieważ w ten sposób program się resetuje. Teraz nie śledzi żadnej <xref:System.Windows.Forms.Label> kontrolki i jest gotowa do ponownego wybrania etykiety przez odtwarzacz.

    > [!NOTE]
    > Obiekt Timer ma `Start()` metodę, która uruchamia czasomierz, i `Stop()` metodę, która go zatrzyma. Gdy właściwość **Enabled** czasomierza zostanie ustawiona na **wartość true** w oknie **Właściwości** , zaczyna się ona od razu po rozpoczęciu programu. Jednak po ustawieniu na **wartość false** nie zaczyna się taktować do momentu `Start()` wywołania metody. Zwykle czasomierz wyzwala zdarzenia taktu w czasie i ponownie za pomocą właściwości **Interval** , aby określić liczbę milisekund oczekiwania między taktami. Można zauważyć, jak `Stop()` Metoda Timer jest wywoływana wewnątrz zdarzenia takt. Powoduje to przełączenie czasomierza w *tryb jednego zastrzelonego*, co oznacza, że kiedy `Start()` Metoda jest wywoływana, czeka na określony interwał, wyzwala zdarzenie pojedynczego taktu, a następnie kończy działanie.

4. Aby wyświetlić nowy czasomierz w akcji, przejdź do edytora kodu i Dodaj następujący kod na górze i u dołu `label_Click()` metody obsługi zdarzeń. (Dodawane są dwie `if` instrukcje do góry i trzy instrukcje do dołu; reszta metody pozostaje taka sama.)

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     Kod w górnej części metody sprawdza, czy czasomierz został uruchomiony, sprawdzając wartość właściwości **włączone** . Dzięki temu, jeśli gracz wybierze pierwszą i drugą kontrolkę etykieta i rozpocznie się uruchamianie czasomierza, wybranie trzeciej etykiety nie spowoduje nic więcej. Zapobiega to również szybkiemu kliknięciu trzeciego czasu, zanim gra zostanie przygotowana do następnego kliknięcia. 

     Kod w dolnej części metody ustawia `secondClicked` zmienną referencyjną, aby śledzić drugą kontrolkę etykieta, którą wybiera gracz, a następnie ustawia kolor ikony etykiety na czarny, aby był widoczny. Następnie uruchamia czasomierz w trybie jednego zadziałania, tak że czeka on 750 milisekund, a następnie uruchamia pojedyncze zdarzenie Taktu. Procedura obsługi zdarzeń taktu czasomierza ukrywa dwie ikony i resetuje `firstClicked` zmienne i `secondClicked` , dzięki czemu formularz jest gotowy do wybrania innej pary ikon.

5. Zapisz i uruchom program. Wybierz ikonę, stanie się widoczna.

6. Wybierz inną ikonę. Pojawi się ona na chwilę, a następnie obie ikony znikną. Powtórz to wiele razy. Formularz teraz śledzi pierwszą i drugą wybraną ikonę i używa czasomierza, aby wstrzymać przed zniknięciem ikon.

## <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz **[krok 7. Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md)**.

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5. Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md).

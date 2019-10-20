---
title: Krok 6. Dodawanie czasomierza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6a2d47a66cdedfc191212a178221712de6aefa61
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671701"
---
# <a name="step-6-add-a-timer"></a>Krok 6. Dodawanie czasomierza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następnie Dodaj kontrolkę **Timer** do odpowiedniej gry. Czasomierz czeka określoną liczbę milisekund, a następnie uruchamia zdarzenie, nazywane *znacznikiem*. Jest to przydatne dla rozpoczęcia czynności lub regularnego powtarzania czynności. W tym przypadku, będziesz używał czasomierza, aby umożliwić graczom wybór dwóch ikon, a jeśli ikony nie będą pasowały, ukryć te dwie ikony po krótkiej chwili.

### <a name="to-add-a-timer"></a>Aby dodać czasomierz

1. Z przybornika w Projektant formularzy systemu Windows wybierz **czasomierz** (w kategorii **składniki** ), a następnie wybierz klawisz ENTER lub kliknij dwukrotnie czasomierz, aby dodać kontrolkę czasomierza do formularza. Ikona czasomierza o nazwie **Timer1**powinna pojawić się w miejscu poniżej formularza, jak pokazano na poniższej ilustracji.

     ![Czasomierz](../ide/media/express-timer.png "Express_Timer") Licz

    > [!NOTE]
    > Jeśli przybornik jest pusty, należy wybrać Projektant formularzy, a nie kod związany z formularzem, przed otwarciem przybornika.

2. Wybierz ikonę **Timer1** , aby wybrać czasomierz. W oknie **Właściwości** Przełącz się z wyświetlania zdarzeń, aby wyświetlić właściwości. Następnie ustaw właściwość **Interwał** czasomierza na **750**, ale pozostaw Właściwość **Enabled** ustawioną na **wartość false**. Właściwość **Interval** określa czasomierz czas oczekiwania między *taktami*lub wyzwala zdarzenie taktu. Wartość 750 mówi czasomierzowi, aby czekał trzy czwarte sekundy (750 milisekund), zanim uruchomi zdarzenie Taktu. Wywołasz metodę `Start()`, aby uruchomić czasomierz dopiero po wybraniu drugiej etykiety przez odtwarzacz.

3. Wybierz ikonę sterowania czasomierzem w Projektant formularzy systemu Windows a następnie wybierz klawisz ENTER lub kliknij dwukrotnie czasomierz, aby dodać pustą procedurę obsługi zdarzeń **taktu** . Zastąp kod następującym kodem lub ręcznie wprowadź następujący kod do programu obsługi zdarzeń.

     [!code-csharp[VbExpressTutorial4Step6#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial4Step6#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#7)]

     Procedura obsługi zdarzeń taktu składa się z trzech rzeczy: najpierw sprawdza, czy czasomierz nie jest uruchomiony, wywołując metodę `Stop()`. Następnie używa dwóch zmiennych referencyjnych, `firstClicked` i `secondClicked`, aby ikony dwóch etykiet, które gracz wybrał niewidoczny. Na koniec resetuje `firstClicked` i `secondClicked` zmiennych odwołania, aby `null` w wizualizacji C# i `Nothing` w Visual Basic. Ten krok jest ważny, ponieważ w ten sposób program się resetuje. Teraz nie śledzi żadnych formantów `Label` i jest gotowy do ponownego wybrania etykiety przez odtwarzacz.

    > [!NOTE]
    > Obiekt `Timer` ma metodę `Start()`, która uruchamia czasomierz, i metodę `Stop()`, która go zatrzyma. Gdy właściwość **Enabled** czasomierza zostanie ustawiona na **wartość true** w oknie **Właściwości** , zaczyna się ona od razu po rozpoczęciu programu. Jednak po ustawieniu na **wartość false**nie zaczyna się taktować do momentu wywołania metody `Start()`. Zwykle czasomierz wyzwala zdarzenia taktu w czasie i ponownie za pomocą właściwości **Interval** , aby określić liczbę milisekund oczekiwania między taktami. Można zauważyć, jak Metoda `Stop()` czasomierza jest wywoływana wewnątrz zdarzenia takt. Powoduje to przełączenie czasomierza do *jednego trybu zastrzelonego*, co oznacza, że gdy metoda `Start()` jest wywoływana, czeka na określony interwał, wyzwala zdarzenie pojedynczego taktu, a następnie kończy działanie.

4. Aby wyświetlić nowy czasomierz w akcji, przejdź do edytora kodu i Dodaj następujący kod na górze i u dołu metody obsługi zdarzeń `label_Click()`. (Dodawana jest instrukcja `if` do góry i trzy instrukcje do dołu; reszta metody pozostaje taka sama.)

     [!code-csharp[VbExpressTutorial4Step6#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial4Step6#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#8)]

     Kod w górnej części metody sprawdza, czy czasomierz został uruchomiony, sprawdzając wartość właściwości **włączone** . Dzięki temu, jeśli gracz wybierze pierwszej i drugiej kontrolki `Label` i rozpocznie się uruchamianie czasomierza, wybranie trzeciej etykiety nie spowoduje nic więcej.

     Kod w dolnej części metody ustawia zmienną odniesienia `secondClicked`, aby śledzić drugą kontrolkę `Label`, którą wybiera gracz, a następnie ustawia kolor ikony etykiety na czarny, aby był widoczny. Następnie uruchamia czasomierz w trybie jednego zadziałania, tak że czeka on 750 milisekund, a następnie uruchamia pojedyncze zdarzenie Taktu. Procedura obsługi zdarzeń taktu czasomierza ukrywa dwie ikony i resetuje `firstClicked` i `secondClicked` zmiennych odwołania, dzięki czemu formularz będzie gotowy do wybrania innej pary ikon.

5. Zapisz i uruchom program. Wybierz ikonę, stanie się widoczna.

6. Wybierz inną ikonę. Pojawi się ona na chwilę, a następnie obie ikony znikną. Powtórz to wiele razy. Formularz teraz śledzi pierwszą i drugą wybraną ikonę i używa czasomierza, aby wstrzymać przed zniknięciem ikon.

### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć

- Aby przejść do następnego kroku samouczka, zobacz [krok 7. Zachowaj widoczne pary](../ide/step-7-keep-pairs-visible.md).

- Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5. Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md).

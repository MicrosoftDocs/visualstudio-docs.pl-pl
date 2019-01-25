---
title: Krok 6. Dodaj czasomierz | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 31116171a15a7a38b76451777faaed35dc8b1e52
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795290"
---
# <a name="step-6-add-a-timer"></a>Krok 6. Dodawanie czasomierza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Następnie dodaj **czasomierza** formantu do gry w dopasowywanie. Czasomierz czeka określoną liczbę milisekund, a następnie uruchamia zdarzenie, określane jako *znaczników*. Jest to przydatne dla rozpoczęcia czynności lub regularnego powtarzania czynności. W tym przypadku, będziesz używał czasomierza, aby umożliwić graczom wybór dwóch ikon, a jeśli ikony nie będą pasowały, ukryć te dwie ikony po krótkiej chwili.  
  
### <a name="to-add-a-timer"></a>Aby dodać czasomierz  
  
1.  Z przybornika w programie Windows Forms Designer wybierz **czasomierza** (w **składniki** kategorii) a następnie naciśnij klawisz ENTER lub kliknij dwukrotnie czasomierz, aby dodać format czasomierza do formularza. Ikona czasomierza, o nazwie **Timer1**, powinien pojawić się w przestrzeni poniżej formularza, jak pokazano na poniższej ilustracji.  
  
     ![Timer](../ide/media/express-timer.png "Express_Timer")  
Czasomierz  
  
    > [!NOTE]
    >  Jeśli przybornik jest pusty, należy wybrać Projektant formularzy, a nie kod związany z formularzem, przed otwarciem przybornika.  
  
2.  Wybierz **Timer1** ikonę, aby wybrać czasomierz. W **właściwości** okna, przejdź z wyświetlania zdarzeń do wyświetlania właściwości. Następnie należy skonfigurować czasomierz **interwał** właściwości **750**, ale pozostawić jego **włączone** właściwością **False**. **Interwał** właściwość mówi czasomierzowi, o ile ma czekać między *impulsów*, lub kiedy ma wyzwolić zdarzenie taktu. Wartość 750 mówi czasomierzowi, aby czekał trzy czwarte sekundy (750 milisekund), zanim uruchomi zdarzenie Taktu. Wywołasz `Start()` metodę, aby uruchomić timer tylko wtedy, gdy gracz wybierze drugą etykietę.  
  
3.  Wybierz licznik kontrolować ikonę w programie Windows Forms Designer, a następnie naciśnij klawisz ENTER lub kliknij dwukrotnie czasomierz, aby dodać pusty **znaczników** programu obsługi zdarzeń. Zastąp kod następującym kodem lub ręcznie wprowadź następujący kod do programu obsługi zdarzeń.  
  
     [!code-csharp[VbExpressTutorial4Step6#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial4Step6#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#7)]  
  
     Program obsługi zdarzeń taktu wykonuje trzy rzeczy: Po pierwsze, sprawdza, czy czasomierz nie jest uruchomiony, wywołując `Stop()` metody. Następnie wykorzystuje dwie zmienne odniesienia, `firstClicked` i `secondClicked`, aby ponownie ukryć ikony dwóch etykiet, które wybrał gracz. Na koniec resetuje `firstClicked` i `secondClicked` odwoływać się do zmiennych do `null` w języku Visual C# i `Nothing` w języku Visual Basic. Ten krok jest ważny, ponieważ w ten sposób program się resetuje. Teraz go jest nie rejestrowanie informacji o dowolnej `Label` kontrolek, a jego gracz jest gotowy do ponownie wybrać etykietę.  
  
    > [!NOTE]
    >  A `Timer` obiekt ma `Start()` metodę, która uruchamia czasomierz, i `Stop()` metody, która go zatrzymuje. Po ustawieniu czasomierza **włączone** właściwości **True** w **właściwości** oknie zacznie jak należy jak najszybciej rozpoczyna się program. Ale gdy pozostawisz równa **False**, nie rozpoczyna odliczania, dopóki nie jego `Start()` metoda jest wywoływana. Normalnie, czasomierz wyzwala zdarzenie taktu cyklicznie wielokrotnie, za pomocą **interwał** właściwości w celu określenia liczby milisekund między taktami. Być może zauważono, jak czasomierza `Stop()` metoda jest wywoływana wewnątrz zdarzenia takt. To przestawia czasomierz w *tryb jednego zadziałania*, co oznacza, że w przypadku `Start()` metoda jest wywoływana, jego czeka przez określony interwał, wyzwala pojedyncze zdarzenie taktu i się zatrzymuje.  
  
4.  Aby wyświetlić działa nowy czasomierz, przejdź do edytora kodu, a następnie dodaj następujący kod do górnej i dolnej części `label_Click()` metody obsługi zdarzeń. (Dodajesz `if` instrukcji na górze i trzy instrukcje na dole, pozostała część metody pozostaje taka sama.)  
  
     [!code-csharp[VbExpressTutorial4Step6#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial4Step6#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#8)]  
  
     Kod w górnej części metody sprawdza, czy czasomierz został uruchomiony, sprawdzając wartość **włączone** właściwości. Dzięki temu, jeśli gracz wybierze pierwszy i drugi `Label` kontrolek i uruchomi się czasomierz, wybranie trzeciej etykiety nie spowoduje żadnego efektu.  
  
     Kod w dolnej części metody ustawia `secondClicked` zmienną odwołania na śledzenie drugiego `Label` formant czy wybrał gracz, a następnie ustawia kolor ikony etykiety na czarny, aby stał się widoczny. Następnie uruchamia czasomierz w trybie jednego zadziałania, tak że czeka on 750 milisekund, a następnie uruchamia pojedyncze zdarzenie Taktu. Program obsługi zdarzeń takt czasomierza ukrywa dwie ikony i resetuje `firstClicked` i `secondClicked` zmienne odwołania, aby formularz był gracz jest gotowy do wyboru innej pary ikon.  
  
5.  Zapisz i uruchom program. Wybierz ikonę, stanie się widoczna.  
  
6.  Wybierz inną ikonę. Pojawi się ona na chwilę, a następnie obie ikony znikną. Powtórz to wiele razy. Formularz teraz śledzi pierwszą i drugą wybraną ikonę i używa czasomierza, aby wstrzymać przed zniknięciem ikon.  
  
### <a name="to-continue-or-review"></a>Aby kontynuować lub przeglądnąć  
  
-   Aby przejść do następnego kroku samouczka, zobacz [kroku 7: Zachować widoczność par](../ide/step-7-keep-pairs-visible.md).  
  
-   Aby powrócić do poprzedniego kroku samouczka, zobacz [krok 5: Dodawanie odwołań do etykiet](../ide/step-5-add-label-references.md).

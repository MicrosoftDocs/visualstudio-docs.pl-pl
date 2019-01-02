---
title: Wyświetl odbiorników zdarzeń DOM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DOM events, viewing [Windows Store apps]
- event listeners, viewing [Windows Store apps]
ms.assetid: d5b679e7-87dd-4cec-9176-883db6ff0781
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0554d3ac1ea0de9f3f7143c5a1d9f2221a52b87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820418"
---
# <a name="view-dom-event-listeners"></a>Podgląd odbiorników zdarzeń DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 **Zdarzenia** karta Narzędzia DOM Explorer zawiera zdarzenia, które są skojarzone z elementem modelu DOM. Każdy najwyższy węzeł w **zdarzenia** karta reprezentuje zdarzenie z aktywnych subskrybentów. Najwyższy węzeł zawiera węzły podrzędne, które reprezentują detektory zdarzenia zarejestrowane dla określonego zdarzenia. Oprócz wyświetlania detektorów zdarzeń, ta karta służy do przejdź do lokalizacji odbiornik zdarzeń w kodzie JavaScript. Informacje przedstawione w tym temacie dotyczą aplikacji Store przy użyciu języków HTML i JavaScript.

 Na liście **zdarzenia** karta jest dynamiczny. Jeśli dodasz odbiornik zdarzeń, gdy aplikacja jest uruchomiona, nowy odbiornik zdarzenia będą tam wyświetlane. Aby uzyskać informacje dotyczące dodawania i usuwania detektorów zdarzeń, zobacz [porady dotyczące rozwiązywania problemów z odbiornikiem zdarzeń](#Tips) w tym temacie.

> [!NOTE]
>  Odbiorniki zdarzeń dla elementów kodu, które nie są elementy modelu DOM, takich jak `xhr`, nie pojawiają się na **zdarzenia** kartę.

## <a name="view-event-listeners-for-dom-elements"></a>Widok detektorów zdarzeń elementów dom.
 W tym przykładzie przedstawiono aplikację Windows Phone Store. Tu funkcji Eksploratora DOM opisane w tym miejscu są również obsługiwane dla aplikacji Windows Store.

#### <a name="to-view-event-listeners"></a>Aby wyświetlić odbiornikiem zdarzeń

1.  W programie Visual Studio należy utworzyć aplikację języka JavaScript, która używa szablon projektu aplikacja Pivot Windows Phone.

2.  Za pomocą szablonu Otwórz w programie Visual Studio, wybierz **Emulator 8.1 WVGA 4 w 512MB** na liście rozwijanej na pasku narzędzi debugowania w debugerze:

     ![Wybieranie obiektu docelowego debugowania](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3.  Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.

4.  W uruchomionej aplikacji, przejdź do **sekcja 3** element przestawny.

5.  Przełącz się do programu Visual Studio (Alt + Tab lub F12).

6.  W Eksploratorze DOM, wybierz `Find` w prawym górnym rogu.

7.  Typ `ListView`, a następnie naciśnij klawisz Enter.

8.  W razie potrzeby wybierz **dalej** przycisk, aby znaleźć `DIV` elementu, który reprezentuje `ListView` kontroli (ten element ma `data-win-control` wartość `WinJS.UI.ListView`).

     `DIV` Element powinny teraz być zaznaczone w programie DOM Explorer.

9. Wybierz **zdarzenia** karty w okienku po prawej stronie narzędzia DOM Explorer.

     Można przeglądać zdarzenia, które mają aktywnych subskrybentów `DIV` elementu, jak pokazano poniżej.

     ![Karta zdarzeń Eksploratora DOM](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Aby zlokalizować detektorów zdarzeń dla tych zdarzeń, wybierz skojarzone linków do plików JavaScript.

11. Szybkie identyfikowanie detektorów zdarzeń dla elementów nadrzędnych w hierarchii modelu DOM, wybierz element nadrzędny w dolnej części Eksploratora DOM na liście hierarchii.

     ![Wybieranie elementów nadrzędnych w hierarchii modelu DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     **Zdarzenia** karta przedstawia detektorów zdarzeń dla każdego elementu wybranego na liście hierarchii.

###  <a name="Tips"></a> Porady dotyczące rozwiązywania problemów z odbiornikiem zdarzeń
 W niektórych scenariuszach aplikacji detektorów zdarzeń musi być jawnie usunięte za pomocą [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Użyj **zdarzenia** kartę w Eksploratorze DOM, aby sprawdzić, czy odbiorniki zdarzeń zostały usunięte z elementów DOM podczas uruchamiania kodu. Poniżej przedstawiono kilka wskazówek, aby pomóc rozwiązać tego rodzaju problemy:

-   Aplikacje korzystające z modelu nawigacji jednej strony można zaimplementować w programie Visual Studio [szablony projektów](http://msdn.microsoft.com/library/windows/apps/hh758331.aspx), nie jest zazwyczaj konieczne jest usunięcie detektory zdarzenia zarejestrowane dla obiektów, takich jak elementy modelu DOM, które są częścią strony. W tym scenariuszu elementu modelu DOM i jego skojarzone ze zdarzeniem odbiorników mają ten sam okres istnienia i mogą być zebranych elementów bezużytecznych.

-   Jeśli okres istnienia obiektu lub DOM element różni się od odbiornika skojarzone ze zdarzeniem, być może trzeba wywołać `removeEventListener` metody. Na przykład, jeśli używasz `window.onresize` zdarzeń, może być konieczne usunięcie odbiornik zdarzeń, jeśli przejdziesz do innej strony, gdzie obsługi zdarzeń.

-   Jeśli `removeEventListener` nie powiedzie się usunąć określony odbiornik, może być wprowadzenie nazywany w innym wystąpieniu obiektu. Możesz użyć [bind — metoda (Function)](/visualstudio/scripting-docs/javascript/reference/bind-method-function-javascript) metodę, aby rozwiązać ten problem, po dodaniu odbiornika.

-   Aby usunąć odbiornik zdarzeń, który został dodany za pomocą [bind — metoda (Function)](/visualstudio/scripting-docs/javascript/reference/bind-method-function-javascript) lub korzystając z funkcją anonimową, przechowywać wystąpienie funkcji po dodaniu odbiornika. Oto jeden ze sposobów, aby bezpiecznie korzystać z tego wzorca:

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     Użyj poniższego kodu, zamiast przechowywania odwołań do powiązanych funkcji, nie będzie można jawnie usunąć odbiornik zdarzeń:

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

-   Nie można usunąć odbiornik zdarzeń za pomocą `removeEventListener` Jeśli została dodana przy użyciu `obj.on<eventname>` atrybutów, takich jak `window.onresize = handlerFunc`.

-   Użyj analizatora pamięci JavaScript do [pamięci JavaScript](../profiling/javascript-memory.md) w swojej aplikacji. Odbiorniki zdarzeń, które muszą zostać jawnie usunięte mogą być wyświetlane jako przeciek pamięci.

## <a name="see-also"></a>Zobacz też

- [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)
- [Debugowanie stylów CSS przy użyciu eksploratora modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)
- [Debugowanie układu przy użyciu eksploratora modelu DOM](../debugger/debug-layout-using-dom-explorer.md)
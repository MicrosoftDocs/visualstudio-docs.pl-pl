---
title: Wyświetlanie odbiorników zdarzeń DOM | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 64d4892080aaf0cf04e4b208b1a0bdb7a7a4480d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693575"
---
# <a name="view-dom-event-listeners"></a>Podgląd odbiorników zdarzeń DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 Na karcie **zdarzenia** dom Explorer są wyświetlane zdarzenia skojarzone z elementem modelu DOM. Każdy węzeł najwyższego poziomu na karcie **zdarzenia** reprezentuje zdarzenie, które ma aktywnych subskrybentów. Górny węzeł zawiera podwęzły reprezentujące zarejestrowane detektory zdarzeń dla określonego zdarzenia. Oprócz wyświetlania detektorów zdarzeń można użyć tej karty, aby przejść do lokalizacji odbiornika zdarzeń w kodzie JavaScript. Informacje przedstawione w tym temacie mają zastosowanie do aplikacji ze sklepu przy użyciu języka HTML i języka JavaScript.

 Lista na karcie **zdarzenia** jest dynamiczna. Jeśli dodasz odbiornik zdarzeń, gdy aplikacja jest uruchomiona, pojawi się nowy odbiornik zdarzeń. Aby uzyskać informacje na temat dodawania i usuwania detektorów zdarzeń, zobacz [porady dotyczące rozwiązywania problemów z odbiornikami zdarzeń](#Tips) w tym temacie.

> [!NOTE]
> Detektory zdarzeń dla elementów kodu, które nie są elementami DOM, takich jak `xhr` , nie są wyświetlane na karcie **zdarzenia** .

## <a name="view-event-listeners-for-dom-elements"></a>Wyświetl detektory zdarzeń dla elementów DOM
 Ten przykład przedstawia aplikację ze sklepu Windows Phone. Funkcje DOM Explorer opisane tutaj są również obsługiwane w przypadku aplikacji ze sklepu Windows.

#### <a name="to-view-event-listeners"></a>Aby wyświetlić detektory zdarzeń

1. W programie Visual Studio Utwórz aplikację JavaScript, która używa szablonu projektu aplikacji Windows Phone Pivot.

2. Po otwarciu szablonu w programie Visual Studio wybierz pozycję **Emulator 8,1 WVGA (4IN 512 MB** na liście rozwijanej na pasku narzędzi debugowania w debugerze:

     ![Wybieranie elementu docelowego debugowania](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")

3. Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.

4. W uruchomionej aplikacji przejdź do **sekcji 3** elementu przestawnego.

5. Przejdź do programu Visual Studio (Alt + Tab lub F12).

6. W DOM Explorer wybierz `Find` w prawym górnym rogu.

7. Wpisz `ListView` polecenie, a następnie naciśnij klawisz ENTER.

8. W razie potrzeby wybierz przycisk **dalej** , aby znaleźć `DIV` element reprezentujący `ListView` formant (ten element ma `data-win-control` wartość `WinJS.UI.ListView` ).

     `DIV`Element powinien być teraz wybrany w Dom Explorer.

9. Wybierz kartę **zdarzenia** w okienku po prawej stronie dom Explorer.

     Teraz można zobaczyć zdarzenia, które mają aktywnych subskrybentów `DIV` elementu, jak pokazano tutaj.

     ![Karta zdarzeń DOM Explorer](../debugger/media/js-dom-events.png "JS_DOM_Events")

10. Aby zlokalizować detektory zdarzeń dla tych zdarzeń, wybierz powiązane z nimi linki plików JavaScript.

11. Aby szybko zidentyfikować detektory zdarzeń dla elementów nadrzędnych w hierarchii modelu DOM, wybierz element nadrzędny na liście hierarchia u dołu DOM Explorer.

     ![Wybieranie elementów nadrzędnych w hierarchii modelu DOM](../debugger/media/js-dom-breadcrumbs.png "JS_DOM_Breadcrumbs")

     Na karcie **zdarzenia** są wyświetlane detektory zdarzeń dla każdego elementu wybranego na liście hierarchia.

### <a name="tips-for-resolving-issues-with-event-listeners"></a><a name="Tips"></a> Porady dotyczące rozwiązywania problemów z odbiornikami zdarzeń
 W niektórych scenariuszach aplikacji detektory zdarzeń muszą być jawnie usunięte przy użyciu [removeEventListener](https://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx). Użyj karty **zdarzenia** w Dom Explorer, aby sprawdzić, czy detektory zdarzeń zostały usunięte z elementów modelu dom podczas uruchamiania kodu. Oto kilka porad ułatwiających rozwiązanie tego typu problemów:

- W przypadku aplikacji korzystających z modelu nawigacji jednostronicowej wdrożonego w [szablonach projektu](https://msdn.microsoft.com/library/windows/apps/hh758331.aspx)programu Visual Studio nie jest zazwyczaj konieczne usuwanie detektorów zdarzeń zarejestrowanych dla obiektów, takich jak elementy dom, które są częścią strony. W tym scenariuszu element DOM i skojarzone z nim detektory zdarzeń mają ten sam okres istnienia i mogą być zbierane jako elementy bezużyteczne.

- Jeśli okres istnienia elementu DOM lub obiekt różni się od skojarzonego odbiornika zdarzeń, może być konieczne wywołanie `removeEventListener` metody. Na przykład jeśli używasz `window.onresize` zdarzenia, może być konieczne usunięcie odbiornika zdarzeń, Jeśli opuścisz stronę, na której obsłużysz wydarzenie.

- Jeśli `removeEventListener` usunięcie określonego odbiornika zakończy się niepowodzeniem, może on być wywoływany w innym wystąpieniu obiektu. Można użyć metody [bind (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) , aby rozwiązać ten problem po dodaniu odbiornika.

- Aby usunąć odbiornik zdarzeń, który został dodany przy użyciu [metody bind (funkcja)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) lub za pomocą funkcji anonimowej, należy przechowywać wystąpienie funkcji po dodaniu odbiornika. Oto jeden ze sposobów bezpiecznego użycia tego wzorca:

    ```javascript
    // You could use the following code within the constructor function of an object, or
    // in the ready function of a PageControl object (Store app).
    this.storedHandler = this._handlerFunc.bind(this);
    elem.addEventListener('mouseup', this.storedHandler);

    // In this example, add the following code in the PageControl object's unload function.
    elem.removeEventListener('mouseup', this.storedHandler);

    ```

     Jeśli użyjesz poniższego kodu zamiast przechowywania odwołania do funkcji powiązanej, nie będzie można jawnie usunąć odbiornika zdarzeń:

    ```javascript
    // Avoid this pattern. No reference to the bound function is available.
    elem.addEventListener('mouseup', this._handlerFunc.bind(this));
    ```

- Nie można usunąć odbiornika zdarzeń przy użyciu `removeEventListener` , jeśli został dodany przy użyciu `obj.on<eventname>` atrybutu, takiego jak `window.onresize = handlerFunc` .

- Użyj analizatora pamięci JavaScript do obsługi [pamięci JavaScript](../profiling/javascript-memory.md) w aplikacji. Detektory zdarzeń, które muszą zostać jawnie usunięte, mogą pojawić się jako przeciek pamięci.

## <a name="see-also"></a>Zobacz też

- [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)
- [Debugowanie stylów CSS przy użyciu eksploratora modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)
- [Debugowanie układu przy użyciu eksploratora modelu DOM](../debugger/debug-layout-using-dom-explorer.md)
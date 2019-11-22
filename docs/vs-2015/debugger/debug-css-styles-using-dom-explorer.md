---
title: Debugowanie stylów CSS przy użyciu DOM Explorer | Microsoft Docs
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
- CSS styles [Windows Store apps], debugging
- CSS rules [Windows Store apps], debugging
- CSS debugging [Windows Store apps]
- debugging, CSS rules [Windows Store apps]
- HTML debugging [Windows Store apps]
ms.assetid: 2dfef7c6-7db2-4550-b694-783b0e535cea
caps.latest.revision: 47
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9f07fc064a87910f59f5734d4d635aa3b5d6b77
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299498"
---
# <a name="debug-css-styles-using-dom-explorer"></a>Debugowanie stylów CSS przy użyciu eksploratora modelu DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Gdy debugujesz aplikacje ze sklepu Windows, Windows Phone aplikacje ze sklepu i aplikacje utworzone przy użyciu Visual Studio Tools dla Apache Cordova, można wyświetlać i zmieniać reguły CSS dla wybranych elementów DOM i ich elementów podrzędnych.  
  
 Karty **Style** i **obliczenia** w Dom Explorer pokazują reguły CSS, które mają zastosowanie do wybranego elementu. Reguły są wyświetlane zgodnie z kolejnością ich specyficzności określoną przez reguły pierwszeństwa CSS. Reguły znajdujące się u góry selektora lub stylu na karcie (najbardziej specyficzne reguły) będą stosowane do wybranego elementu jako ostatnie, a reguły znajdujące się u dołu selektora lub stylu będą stosowane jako pierwsze. Gdy reguły są stosowane, zastępują uprzednio zastosowane reguły.  
  
 Karty **Style**, **obliczone**i **zmiany** zapewniają różne widoki informacji o stylu.  
  
- Karta **Style** służy do wyświetlania reguł uporządkowanych według nazwy selektora CSS, takiej jak `html, body`. Za pomocą tej karty można także włączać i wyłączać określone style, ręcznie edytować wartości oraz zobaczyć wyniki wprowadzenia tych zmian.  
  
- Użyj karty **obliczanej** , aby wyświetlić obliczone wartości stylu. Na przykład ustawienie rozmiaru równego 1em spowoduje, że wartość obliczona przez program Internet Explorer będzie wynosić 16px. Style na tej karcie są zorganizowane według nazwy stylu, takiej jak `height`. Za pomocą tej karty można także włączać i wyłączać określone style, ręcznie edytować wartości oraz zobaczyć wyniki wprowadzenia tych zmian.  
  
    > [!NOTE]
    > W Visual Studio 2013 Update 2 informacje podane na karcie **śledzenie** zostały scalone z kartą **obliczaną** , a karta **śledzenie** została usunięta.  
  
- Skorzystaj z karty **zmiany** (tylko aplikacje do sklepu Windows i Windows Phone sklepu), aby identyfikować i śledzić style CSS, które zostały zmienione podczas sesji debugowania.  
  
> [!TIP]
> Zmiany wprowadzane do stylów w **stylach** i kartach **obliczanych** nie są trwałe. Zostaną one utracone po zakończeniu debugowania. Aby zmienić kod źródłowy i załadować ponownie strony bez zatrzymywania i ponownego uruchamiania debugera, Odśwież aplikację przy użyciu przycisku ![przycisku Odśwież aplikację systemu Windows](../debugger/media/js-refresh.png "JS_Refresh") (**Odśwież aplikację systemu**Windows) na pasku narzędzi **debugowania** (tylko aplikacje Sklepu Windows i Windows Phone sklepu). Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="example-of-fixing-a-css-rule"></a>Przykład poprawiania reguły CSS  
 W tym przykładzie pokazano, jak sprawdzić reguły CSS i zdebugować problem ze stylem. Na potrzeby tego przykładu Załóżmy, że chcesz zmienić kolor czcionki używanej do wyświetlania tytułów grup w szablonie [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] Split App.  
  
> [!NOTE]
> W tym przykładzie przedstawiono aplikację ze sklepu Windows, ale wszystkie DOM Explorer funkcje są również stosowane do aplikacji Windows Phone Store i, z wyjątkiem karty zmiany, aplikacja utworzona przy użyciu Visual Studio Tools dla Apache Cordova.  
  
#### <a name="to-view-and-change-css-rules"></a>Aby wyświetlić i zmienić reguły CSS  
  
1. W programie Visual Studio Utwórz aplikację [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] przy użyciu języków JavaScript i HTML w szablonie projektu rozdzielonej aplikacji.  
  
2. W **Eksplorator rozwiązań**Otwórz element Items. css. (Element items.css znajduje się w folderze stron).  
  
3. Zamień następujący kod CSS:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
    }  
    ```  
  
     na kod:  
  
    ```css  
    .itemspage .itemslist .item {  
        -ms-grid-columns: 1fr;  
        -ms-grid-rows: 1fr 90px;  
        display: -ms-grid;  
        height: 250px;  
        width: 250px;  
        color: #ff6a00;  
    }  
    ```  
  
     Spowoduje to dodanie stylu określającego kolor #ff6a00 (pomarańczowy) dla każdego elementu na liście. Selektor CSS, `.itemspage .itemslist .item`, wskazuje zestaw nazw klas dla elementów DIV w Items. html, które są wyświetlane jako elementy zagnieżdżone w dynamicznym modelu DOM. Element `item` DIV określa elementy listy.  
  
4. Z listy rozwijanej na pasku narzędzi **debugowania** wybierz pozycję **symulator** (wartość domyślna to**komputer lokalny** ).  
  
     ![Wybierz listę obiektów docelowych debugowania](../debugger/media/js-select-target.png "JS_Select_Target")  
  
5. Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
     Po zakończeniu ładowania aplikacji sprawdź nagłówki elementów listy, takie jak **tytuł grupy: 1**. Kolor pozostał niezmieniony, więc próba zastosowania koloru pomarańczowego do tytułów nie powiodła się. Wyjaśnimy, co zostało źle zrobione, i wprowadzimy odpowiednie poprawki, używając kart CSS w Eksploratorze DOM.  
  
    > [!TIP]
    > Gdy aplikacja zostanie wyświetlona w symulatorze, umieść okno symulatora obok okna programu Visual Studio, co umożliwi natychmiastowe zobaczenie wyników wybrania opcji wprowadzenia zmian w stylach CSS.  
  
6. Przejdź do programu Visual Studio, a następnie kliknij pozycję **Wybierz element** w Dom Explorer (lub naciśnij klawisze CTRL + B). Spowoduje to zmianę trybu zaznaczania, dzięki czemu będzie można zaznaczyć element, klikając go, i przenieść aplikację na pierwszy plan. Jednym kliknięciem można powrócić do poprzedniego trybu. Oto przycisk **Wybierz element** . ![Przycisk wyboru elementu w DOM Explorer](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button ")  
  
    > [!TIP]
    > Elementy HTML można także zaznaczać bezpośrednio w Eksploratorze DOM. Aby uzyskać więcej informacji na temat wybierania elementów, zobacz [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7. W symulatorze Umieść kursor nad tytułem pierwszego elementu na liście, **tytuł grupy: 1**, w lewym panelu strony głównej. Tytuł jest wyróżniony, tak jak pokazano poniżej:  
  
     ![Korzystanie z przycisku Wybierz element](../debugger/media/js-css-select-element.png "JS_CSS_Select_Element")  
  
    > [!NOTE]
    > Emulator Windows Phone tylko częściowo obsługuje wyróżnianie elementów przez przesuwanie.  
  
8. Kliknij wyróżniony tytuł. Eksplorator DOM automatycznie zaznaczy odpowiedni element HTML, który wygląda podobnie do tego.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Po zaznaczeniu elementu H4 w Eksploratorze DOM na jego kartach są widoczne reguły skojarzone z elementem H4. Karta **obliczona** jest pokazana tutaj z otwartą właściwością `color`:  
  
     ![Karta style śledzenia w DOM Explorer](../debugger/media/js-css-styles.png "JS_CSS_Styles")  
  
     Ten widok zawiera przydatne informacje o regułach, które są skojarzone ze stylem `color`, na przykład następujące:  
  
    - Selektor CSS, który został zmodyfikowany w elemencie Items. CSS, `.itemspage .itemslist .item`, nie jest używany w obliczeniu stylu końcowego (pojawia się w tekście przekreślonym). Niektóre inne wystąpienia stylu `color` również nie są używane.  
  
        > [!TIP]
        > Pełne nazwy selektorów o dłuższych nazwach są wyświetlane w etykietkach narzędzia.  
  
    - Końcowa obliczona wartość CSS, `rgba(255, 255, 255, 0.87)`, jest ustawiana w odniesieniu do następującego selektora CSS: `.itemspage .itemslist .item .item-overlay .item-title`, która jest również zdefiniowana w Items. css.  
  
        > [!TIP]
        > Teraz, gdy wiemy, gdzie jest ustawiony kolor, wiemy także, gdzie możemy go zmienić. Zmiany można też testować w Eksploratorze DOM bez odświeżania aplikacji, tak jak pokazano w kolejnych krokach.  
  
9. Wyczyść pole wyboru pierwszego wystąpienia stylu `color`, który jest przeznaczony dla selektora `.itemspage .itemslist .item .item-overlay .item-title`. Teraz w symulatorze zobaczysz, że kolor tytułów elementów zmieni się na pomarańczowy, zgodnie z oczekiwaniami, a selektor modyfikowany w CSS `.itemspage .itemslist .item`, nie jest już przesłonięty (oznacza to, że nie ma już zastosowanego tekstu przekreślenia). Oto karta **obliczana** po usunięciu zaznaczenia pola wyboru.  
  
     ![Karta obliczana po aktualizacji stylu CSS](../debugger/media/js-css-styles-fixed.png "JS_CSS_Styles_Fixed")  
  
10. Wybierz kartę **zmiany** .  
  
     Karta **zmiany** umożliwia identyfikowanie i śledzenie zmian stylów wprowadzonych podczas sesji debugowania. Na poniższej ilustracji przedstawiono selektor `.itemspage .itemslist .item .item-overlay .item-title` na karcie **zmiany** , który został teraz zastąpiony.  
  
     ![Karta zmiany w DOM Explorer](../debugger/media/js-css-styles-changes.png "JS_CSS_Styles_Changes")  
  
11. Możesz również ręcznie edytować wartości stylów CSS i wyświetlać wyniki bezpośrednio przy użyciu karty **Style** .  
  
12. Wybierz kartę **Style** .  
  
13. Otwórz selektor stylów `.itemspage .itemslist .item .item-overlay .item-title`.  
  
14. Wybierz pierwsze wystąpienie stylu `color`, a następnie kliknij dwukrotnie wartość właściwości `rgb(255, 255, 255, 0.87)`.  
  
15. Użyj klawiatury, aby zmodyfikować tę wartość. Zmień go na `rgb(255, 255, 0, 0.87)`, a następnie naciśnij klawisz ENTER. Kolory wszystkich tytułów elementów zostały zmienione w symulatorze na żółty.  
  
16. Aby wprowadzić zmiany w źródłowym pliku CSS, kliknij link **Items. css** na karcie **Style** . Spowoduje to otwarcie pliku Items. CSS, gdzie można zmienić wartość stylu `color` w kodzie aplikacji. Aby odświeżyć aplikację bez zatrzymywania i ponownego uruchamiania debugera, kliknij przycisk ![Odśwież aplikację systemu Windows](../debugger/media/js-refresh.png "JS_Refresh") (**Odśwież aplikację systemu Windows**) na pasku narzędzi **debugowanie** .  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debugowanie układu przy użyciu DOM Explorer](../debugger/debug-layout-using-dom-explorer.md)   
 [Wyświetl odbiorniki zdarzeń DOM](../debugger/view-dom-event-listeners.md)   
 [Pomoc techniczna i ułatwienia dostępu](https://go.microsoft.com/fwlink/?LinkId=253502)

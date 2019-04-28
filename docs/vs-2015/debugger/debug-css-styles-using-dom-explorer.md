---
title: Debugowanie stylów CSS przy użyciu narzędzia DOM Explorer | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 05d8cafce91fa55c515457b9f44779a06586387a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409499"
---
# <a name="debug-css-styles-using-dom-explorer"></a>Debugowanie stylów CSS przy użyciu eksploratora modelu DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Podczas debugowania aplikacji Windows Store, Windows Phone Store aplikacje i aplikacje utworzone przy użyciu programu Visual Studio Tools for Apache Cordova, można wyświetlić i zmienić reguły CSS dla wybranych elementów DOM i ich elementów podrzędnych.  
  
 **Style** i **obliczane** kart w Eksploratorze DOM widoczne reguły CSS, które są stosowane do wybranego elementu. Reguły są wyświetlane zgodnie z kolejnością ich specyficzności określoną przez reguły pierwszeństwa CSS. Reguły znajdujące się u góry selektora lub stylu na karcie (najbardziej specyficzne reguły) będą stosowane do wybranego elementu jako ostatnie, a reguły znajdujące się u dołu selektora lub stylu będą stosowane jako pierwsze. Gdy reguły są stosowane, zastępują uprzednio zastosowane reguły.  
  
 **Style**, **obliczane**, i **zmiany** karty zapewniają różne widoki informacji o stylu.  
  
- Użyj **style** kartę, aby wyświetlić reguły, uporządkowane według nazwy selektora CSS, takich jak `html, body`. Za pomocą tej karty można także włączać i wyłączać określone style, ręcznie edytować wartości oraz zobaczyć wyniki wprowadzenia tych zmian.  
  
- Użyj **obliczane** kartę, aby wyświetlić obliczonych wartości stylu. Na przykład ustawienie rozmiaru równego 1em spowoduje, że wartość obliczona przez program Internet Explorer będzie wynosić 16px. Style na tej karcie są zorganizowane według nazw stylów, takich jak `height`. Za pomocą tej karty można także włączać i wyłączać określone style, ręcznie edytować wartości oraz zobaczyć wyniki wprowadzenia tych zmian.  
  
    > [!NOTE]
    > W programie Visual Studio 2013 Update 2, informacje są podawane w **śledzenia** kartę został połączony z **obliczane** karcie i **śledzenia** karty zostały usunięte.  
  
- Użyj **zmiany** kartę (tylko aplikacje Windows Store i Windows Phone Store) umożliwia identyfikowanie i śledzenie stylów CSS, które zostały zmienione w podczas sesji debugowania.  
  
> [!TIP]
> Zmiany wprowadzone do stylów w **style** i **obliczane** karty są trwałe. Zostaną one utracone po zakończeniu debugowania. Aby zmienić kod źródłowy i ponownie załadować strony bez zatrzymywania i ponownego uruchamiania debugera, Odśwież aplikację za pomocą ![przycisku aplikacji Windows Odśwież](../debugger/media/js-refresh.png "JS_Refresh") przycisk (**Windows Odśwież aplikację** ) na **debugowania** paska narzędzi (tylko aplikacje Windows Store i Windows Phone Store). Aby uzyskać więcej informacji, zobacz [odświeżanie aplikacji (JavaScript)](../debugger/refresh-an-app-javascript.md).  
  
## <a name="example-of-fixing-a-css-rule"></a>Przykład poprawiania reguły CSS  
 W tym przykładzie pokazano, jak sprawdzić reguły CSS i zdebugować problem ze stylem. Na przykład załóżmy, że chcesz zmienić kolor czcionki używanej w celu wyświetlania tytułów grup w [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] szablonu Podziel aplikację.  
  
> [!NOTE]
> W tym przykładzie przedstawiono aplikację Windows Store, ale wszystkie funkcje narzędzia DOM Explorer pokazano również się do aplikacji Windows Phone Store, z wyjątkiem kartę zmian, aplikacja utworzona za pomocą programu Visual Studio Tools for Apache Cordova.  
  
#### <a name="to-view-and-change-css-rules"></a>Aby wyświetlić i zmienić reguły CSS  
  
1. W programie Visual Studio, należy utworzyć [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji przy użyciu języków JavaScript i HTML w szablonie projektu Podziel aplikację.  
  
2. W **Eksploratora rozwiązań**, otwórz element items.css. (Element items.css znajduje się w folderze stron).  
  
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
  
     Spowoduje to dodanie stylu określającego kolor #ff6a00 (pomarańczowy) dla każdego elementu na liście. Selektor CSS `.itemspage .itemslist .item`, wskazuje zestaw nazw klas elementów DIV w items.html, które są wyświetlane jako elementy zagnieżdżone na żywo modelu DOM. `item` DIV element określa elementy listy.  
  
4. Wybierz **symulator** na liście rozwijanej na **debugowania** paska narzędzi (**komputera lokalnego** jest wartością domyślną).  
  
     ![Wybierz opcję debugowania listy docelowej](../debugger/media/js-select-target.png "JS_Select_Target")  
  
5. Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
     Po zakończeniu ładowania aplikacji, poszukaj na nagłówki elementów listy, takich jak **tytuł grupy: 1**. Kolor pozostał niezmieniony, więc próba zastosowania koloru pomarańczowego do tytułów nie powiodła się. Wyjaśnimy, co zostało źle zrobione, i wprowadzimy odpowiednie poprawki, używając kart CSS w Eksploratorze DOM.  
  
    > [!TIP]
    > Gdy aplikacja zostanie wyświetlona w symulatorze, umieść okno symulatora obok okna programu Visual Studio, co umożliwi natychmiastowe zobaczenie wyników wybrania opcji wprowadzenia zmian w stylach CSS.  
  
6. Przełącz się do programu Visual Studio, a następnie kliknij przycisk **zaznacz Element** w Eksploratorze DOM (albo naciśnij klawisze Ctrl + B). Spowoduje to zmianę trybu zaznaczania, dzięki czemu będzie można zaznaczyć element, klikając go, i przenieść aplikację na pierwszy plan. Jednym kliknięciem można powrócić do poprzedniego trybu. Oto **zaznacz Element** przycisku. ![Wybierz przycisk Element w Eksploratorze DOM](../debugger/media/js-dom-select-element-button.png "JS_DOM_Select_Element_Button")  
  
    > [!TIP]
    > Elementy HTML można także zaznaczać bezpośrednio w Eksploratorze DOM. Aby uzyskać więcej informacji dotyczących zaznaczania elementów, zobacz [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md).  
  
7. W symulatorze, umieść kursor na tytule pierwszego elementu na liście **tytuł grupy: 1**, w lewym panelu strony głównej. Tytuł jest wyróżniony, tak jak pokazano poniżej:  
  
     ![Za pomocą przycisku Wybierz Element](../debugger/media/js-css-select-element.png "JS_CSS_Select_Element")  
  
    > [!NOTE]
    > Emulator Windows Phone obsługuje tylko częściowo wyróżniania elementów przez zatrzymanie wskaźnika myszy.  
  
8. Kliknij wyróżniony tytuł. Eksplorator DOM automatycznie zaznaczy odpowiedni element HTML, który wygląda podobnie do tego.  
  
    ```html  
    <h4 class="item-title">Group Title: 1</h4>  
    ```  
  
     Po zaznaczeniu elementu H4 w Eksploratorze DOM na jego kartach są widoczne reguły skojarzone z elementem H4. **Obliczane** karty są wyświetlane tutaj przy użyciu `color` otwartą właściwość:  
  
     ![Karta stylów śledzenia w Eksploratorze DOM](../debugger/media/js-css-styles.png "JS_CSS_Styles")  
  
     Ten widok zawiera użyteczne informacje o regułach, które są skojarzone z `color` stylu, takich jak następujące:  
  
    - Selektor CSS zmodyfikowany w pliku items.css `.itemspage .itemslist .item`, nie jest używany w finalnych obliczeniach stylu (zostanie przekreślonego tekstu). Kilka innych wystąpień `color` styl również nie są używane.  
  
        > [!TIP]
        > Pełne nazwy selektorów o dłuższych nazwach są wyświetlane w etykietkach narzędzia.  
  
    - Ostateczna obliczona wartość CSS — `rgba(255, 255, 255, 0.87)`, jest ustawiona specjalnie dla selektora CSS: `.itemspage .itemslist .item .item-overlay .item-title`, który również jest zdefiniowany w pliku items.css.  
  
        > [!TIP]
        > Teraz, gdy wiemy, gdzie jest ustawiony kolor, wiemy także, gdzie możemy go zmienić. Zmiany można też testować w Eksploratorze DOM bez odświeżania aplikacji, tak jak pokazano w kolejnych krokach.  
  
9. Usuń zaznaczenie pola wyboru dla pierwszego wystąpienia `color` stylu, który dotyczy `.itemspage .itemslist .item .item-overlay .item-title` selektora. Teraz w symulatorze widać kolor elementu tytuły wszystkich zmieniony na pomarańczowy, zamierzamy, a selektor zmodyfikowany w pliku CSS `.itemspage .itemslist .item`, jest już zastępowany (oznacza to, że nie ma już przekreślonego tekstu). Oto **obliczane** karcie po wyczyszczeniu pola wyboru.  
  
     ![Na karcie obliczane po zaktualizowaniu stylu CSS](../debugger/media/js-css-styles-fixed.png "JS_CSS_Styles_Fixed")  
  
10. Wybierz **zmiany** kartę.  
  
     Użyj **zmiany** kartę umożliwia identyfikowanie i śledzenie zmian stylów, wprowadzonych podczas sesji debugowania. Poniższa ilustracja przedstawia `.itemspage .itemslist .item .item-overlay .item-title` selektorze **zmiany** kartę, która obecnie został zastąpiony.  
  
     ![Na karcie zmiany Eksploratora DOM](../debugger/media/js-css-styles-changes.png "JS_CSS_Styles_Changes")  
  
11. Możesz także ręcznie edytować wartości stylów CSS i od razu zobaczyć wyniki za pomocą **style** kartę.  
  
12. Wybierz **style** kartę.  
  
13. Otwórz `.itemspage .itemslist .item .item-overlay .item-title` selektor stylu.  
  
14. Wybierz pozycję pierwszego wystąpienia `color` stylu, a następnie kliknij dwukrotnie wartość właściwości `rgb(255, 255, 255, 0.87)`.  
  
15. Użyj klawiatury, aby zmodyfikować tę wartość. Zmień ją na `rgb(255, 255, 0, 0.87)`, a następnie naciśnij klawisz Enter. Kolory wszystkich tytułów elementów zostały zmienione w symulatorze na żółty.  
  
16. Aby wprowadzić zmiany w źródłowym pliku CSS, kliknij przycisk **pliku items.css** link **style** kartę. Spowoduje to otwarcie pliku items.css, w którym można zmienić wartość `color` stylu w kodzie aplikacji. Aby odświeżyć aplikację bez zatrzymywania i ponownego uruchamiania debugera, kliknij przycisk ![przycisku aplikacji Windows Odśwież](../debugger/media/js-refresh.png "JS_Refresh") (**aplikacji Windows Odśwież**) przycisku na **Debugowania** paska narzędzi.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debugowanie układu przy użyciu Eksploratora modelu DOM](../debugger/debug-layout-using-dom-explorer.md)   
 [Podgląd odbiorników zdarzeń DOM](../debugger/view-dom-event-listeners.md)   
 [Pomoc techniczna i dostępność](http://go.microsoft.com/fwlink/?LinkId=253502)

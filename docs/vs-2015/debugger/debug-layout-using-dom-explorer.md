---
title: Debugowanie układu przy użyciu DOM Explorer | Microsoft Docs
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
- box model [Windows Store apps], viewing
- debugging layout [Windows Store apps]
- layout, debugging [Windows Store apps]
ms.assetid: ded6566d-fc29-49a7-8029-dee8e50fe733
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a3c9b3a6ae2ed11e8512f8cf8857d27b3d0043b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850076"
---
# <a name="debug-layout-using-dom-explorer"></a>Debugowanie układu przy użyciu eksploratora modelu DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Na karcie **układ** dom Explorer jest wyświetlany [model pola CSS](https://www.w3.org/TR/CSS2/box.html) dla wybranego elementu w [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji, aplikacja Windows Phone Store lub aplikacja utworzona przy użyciu Visual Studio Tools dla Apache Cordova. Ta reprezentacja wizualna modelu Box służy do identyfikowania i modyfikowania wartości związanych z układem, które wpływają na wygląd elementów.  
  
> [!TIP]
> Zmiany wprowadzane na karcie **Układ** nie są trwałe. Możesz wprowadzać trwałe zmiany w kodzie źródłowym, a następnie odświeżyć aplikację przy użyciu przycisku **Odśwież aplikację systemu** Windows (tylko aplikacje Sklepu windows i Windows Phone sklepu) na pasku narzędzi Debugowanie. W ten sposób można uniknąć ponownego uruchomienia debugera.  
  
 Aby użyć DOM Explorer do modyfikowania aspektów układu, które nie są wyświetlane w modelu Box, zobacz [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) oraz [debugowanie stylów css przy użyciu dom Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="example-of-fixing-a-layout-issue"></a>Przykład rozwiązywania problemu z układem  
 Ten przykład pokazuje, jak wybrać element listy w szablonie Hub/Pivot, interpretując wartości modelu Box, które znajdują się na karcie **Układ** , a następnie zmienić jedną z wartości właściwości w celu rozwiązania problemu układu.  
  
#### <a name="to-fix-the-layout-issue"></a>Aby rozwiązać problem z układem  
  
1. W programie Visual Studio Utwórz nową aplikację ze sklepu, która używa szablonu projektu Hub/Pivot.  
  
2. W folderze Shared pages\hub Otwórz plik Hub. css.  
  
3. Zamień następujący kod CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     z tym kodem CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4. Wybierz projekt nazwa_aplikacji. WindowsPhone lub projekt nazwa_aplikacji. Windows w Eksplorator rozwiązań, a następnie wybierz pozycję **Ustaw jako projekt startowy** z menu skrótów dla projektu.  
  
5. W zależności od projektu startowego wybierz pozycję **Emulator 8,1 WVGA (4 cala 512 MB** lub **symulatora** na liście rozwijanej na pasku narzędzi debugowania (wartość domyślna to**komputer lokalny** ).  
  
     ![Wybieranie elementu docelowego debugowania](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6. Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
7. Otwórz sekcję 4 przez przewijanie lub szybkie przesuwanie.  
  
    > [!TIP]
    > Umieść emulator telefonu lub symulatora bezpośrednio obok okna programu Visual Studio, dzięki czemu możesz natychmiast zobaczyć wyniki wybranych opcji i zmian w stylach CSS.  
  
     Gdy sekcja 4 ładuje, można zobaczyć, że dolne obrazy nie wyglądają w prawo. Każdy obraz elementu jest obcinany w połowie (z brakującą połową).  
  
8. Przejdź do programu Visual Studio i wybierz **pozycję Wybierz element** w Dom Explorer (lub naciśnij klawisze CTRL + B). Spowoduje to zmianę trybu zaznaczania, dzięki czemu będzie można zaznaczyć element, klikając go, i przenieść aplikację na pierwszy plan. Jednym kliknięciem można powrócić do poprzedniego trybu.  
  
    > [!TIP]
    > Możesz również użyć klawiszy strzałek lub innych metod do zaznaczania elementów HTML bezpośrednio w DOM Explorer. Aby uzyskać więcej informacji na temat wybierania elementów, zobacz [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. W emulatorze lub symulatorze telefonu zaznacz szarą prawą połowę jednego z obrazów, które są obcinane w połowie. Wyróżnianie pojawia się wokół zaznaczonego elementu, jak pokazano poniżej w emulatorze Windows Phone:  
  
     ![Wybieranie elementu DOM](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    > Symulator obsługuje przesuwanie nad elementami, aby pokazać wyróżnianie pól wokół elementów DOM przed wybraniem jednego. Emulator Windows Phone nie obsługuje tej funkcji.  
  
     Po wybraniu elementu DOM DOM Explorer automatycznie wybiera odpowiedni element IMG w programie Visual Studio. Element wybrany w DOM Explorer wygląda następująco:  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. Kliknij kartę **Układ** . Na tej karcie jest wyświetlany model Box wybranego elementu, jak pokazano poniżej w emulatorze Windows Phone.  
  
     ![Karta układ DOM Explorer](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Ten widok udostępnia przydatne informacje dotyczące elementu:  
  
    - Kolory odpowiadają wyróżnieniu pola, które pojawia się w symulatorze, gdy przesuwa się nad elementami. Niebieski kolor reprezentuje \<img> Wymiary elementu. Kolor Tan reprezentuje wartości marginesu.  
  
    - Zostanie ustawiony lewy margines (margines lewy), który wskazuje na przyczynę problemu, ponieważ pasuje do objawu (czarny po lewej stronie obrazów).  
  
    - Pola pokazujące wartości 0 pikseli (na przykład obramowanie i uzupełnienie) sugerują, że odpowiednie właściwości CSS prawdopodobnie nie są ustawione.  
  
11. Aby zobaczyć, jak jest stosowana reguła z lewej strony, wybierz kartę **obliczoną** i poszukaj w obszarze reguła lewej krawędzi. Można zobaczyć, że ta reguła jest ustawiona z wartością 5em, ale obliczoną wartością jest 66.66 px lub 146.66 pikseli, w zależności od urządzenia docelowego.  
  
    > [!TIP]
    > Karta **obliczona** pokazuje, że w selektorze CSS jest ustawiona lewa strona z marginesem `..hubpage .hub. section4 .sub-image-row img` , którą można znaleźć w pliku Hub. css. W tej aplikacji demonstracyjnej, w której należy wprowadzić poprawkę.  
  
     Możesz również użyć karty **Układ** do testowania modyfikacji wartości układu.  
  
12. Na karcie **Układ** wybierz pozycję **66,66** lub **146,66**, która zostanie wyświetlona w polu **margines** po lewej stronie pola.  
  
13. Wpisz polecenie `0` i naciśnij klawisz Enter. (Możesz również zmienić wartość za pomocą klawiszy Strzałka w górę i Strzałka w dół).  
  
14. Zaznacz inne \<img> elementy w Dom Explorer i zmień ich wartości w lewym marginesie na 0.  
  
15. Przejdź do emulatora telefonu lub symulatora. Zaktualizowane lewe marginesy zostały zastosowane do obrazów sekcji 4. Te wartości są również aktualizowane na karcie **obliczonej** w ramach reguły lewej marginesu.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki Start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debugowanie stylów CSS przy użyciu DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Podgląd odbiorników zdarzeń DOM](../debugger/view-dom-event-listeners.md)

---
title: Debugowanie układu przy użyciu narzędzia DOM Explorer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ba06e6a8ba95887c0cc6b6acfd14cef10ff03798
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787761"
---
# <a name="debug-layout-using-dom-explorer"></a>Debugowanie układu przy użyciu eksploratora modelu DOM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 **Układ** karta Narzędzia DOM Explorer pokazuje [modelu pudełkowego CSS](http://go.microsoft.com/fwlink/?LinkID=238778) dla wybranego elementu w [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] app, aplikacji Windows Phone Store lub aplikacja utworzona za pomocą programu Visual Studio Tools for Apache Cordova. Ta wizualnej reprezentacji modelu pudełkowego służy do identyfikowania i zmodyfikuj wartości związane z układem, które wpływają na wygląd elementów.  
  
> [!TIP]
>  Zmiany wprowadzone w oknie **układ** karty nie są trwałe. Można wprowadzić trwałe zmiany do kodu źródłowego, a następnie Odśwież aplikację za pomocą **aplikacji Windows Odśwież** przycisku (tylko aplikacje Windows Store i Windows Phone Store) na pasku narzędzi debugowania. Dzięki temu można uniknąć ponownego uruchamiania debugera.  
  
 Aby użyć narzędzia DOM Explorer, aby zmodyfikować aspektów układu, które nie są wyświetlane w modelu pudełkowego, zobacz [Szybki Start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md) i [stylów CSS debugowania przy użyciu narzędzia DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
## <a name="example-of-fixing-a-layout-issue"></a>Przykład poprawiania problem układu  
 W tym przykładzie pokazano, jak wybierz element listy w szablonie Centrum/obrotu, interpretowania wartości modelu pola, znajdujące się na **układ** kartę, a następnie zmień jedną z wartości właściwości, aby rozwiązać problem układu.  
  
#### <a name="to-fix-the-layout-issue"></a>Aby rozwiązać ten problem, układ  
  
1.  W programie Visual Studio Utwórz nową aplikację Store, który używa szablonu projektu Centrum/obrotu.  
  
2.  W folderze udostępnionym pages\hub Otwórz hub.css.  
  
3.  Zamień następujący kod CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
    }  
    ```  
  
     kod CSS:  
  
    ```css  
    .hubpage .hub .section4 .sub-image-row img {  
        height: 95px;  
        width: 130px;  
        margin-left: 5em;  
    }  
    ```  
  
4.  Wybierz projekt appName.WindowsPhone lub projektu appName.Windows w Eksploratorze rozwiązań, a następnie wybierz **Ustaw jako projekt startowy** z menu skrótów dla projektu.  
  
5.  W zależności od Twój projekt startowy wybierają **Emulator 8.1 WVGA 4 cala 512 MB** lub **symulator** na liście rozwijanej na pasku narzędzi debugowania (**komputera lokalnego** jest wartością domyślną wartość).  
  
     ![Wybieranie obiektu docelowego debugowania](../debugger/media/js-dom-debug-target-emu.png "JS_DOM_Debug_Target_Emu")  
  
6.  Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
7.  Otwórz przewijania lub flicking sekcja 4.  
  
    > [!TIP]
    >  Pozycja prawo emulatora telefonu lub symulatora obok okna programu Visual Studio, dzięki czemu można natychmiast zobaczyć wyniki wyborów i zmiany wprowadzone w stylach CSS.  
  
     Po załadowaniu sekcji 4, zobaczysz niższe obrazy wyglądają niewłaściwie. Każdy element pojawi się wycinania połowę (z lewej połowie brakujący).  
  
8.  Przejdź do programu Visual Studio i wybierz **zaznacz Element** w Eksploratorze DOM (albo naciśnij klawisze Ctrl + B). Spowoduje to zmianę trybu zaznaczania, dzięki czemu będzie można zaznaczyć element, klikając go, i przenieść aplikację na pierwszy plan. Jednym kliknięciem można powrócić do poprzedniego trybu.  
  
    > [!TIP]
    >  Aby wybrać elementy HTML bezpośrednio w Eksploratorze DOM, można użyć klawiszy strzałek lub innych metod. Aby uzyskać więcej informacji dotyczących zaznaczania elementów, zobacz [Szybki Start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md).  
  
9. W emulatorze telefonu lub symulator wybierz szary prawej połowie ekranu jeden z obrazów, które są skrócił się o połowę. Wyróżnianie pojawia się wokół wybranego elementu, jak pokazano w Emulator Windows Phone:  
  
     ![Wybieranie elementu DOM](../debugger/media/js-css-layout-select.png "JS_CSS_Layout_Select")  
  
    > [!TIP]
    >  Symulator obsługuje, przenosząc kursor myszy nad elementy, aby pokazać pole wyróżnienie wokół elementów DOM, można wybrać. Emulator Windows Phone nie obsługuje tego.  
  
     Po wybraniu elementu DOM, Eksplorator DOM automatycznie zaznaczy odpowiedni element IMG w programie Visual Studio. Elementu zaznaczonego w Eksploratorze DOM wygląda następująco:  
  
    ```html  
    <img src="ms-appx://guid/images/gray.png>   
    </img>  
    ```  
  
10. Kliknij przycisk **układ** kartę. Ta karta przedstawia model pola wybranego elementu, jak pokazano w Emulator Windows Phone.  
  
     ![Układ karcie Eksploratora DOM](../debugger/media/js-css-layout.png "JS_CSS_Layout")  
  
     Ten widok zawiera pewne przydatne informacje dotyczące elementu:  
  
    -   Kolory odpowiadają wyróżnienia pola, który pojawia się w symulatorze, po najechaniu kursorem na elementy. Reprezentuje kolor niebieski \<img > wymiarów elementu. Tan kolor reprezentuje wartości marginesów.  
  
    -   Lewy margines (lewym marginesie) jest ustawiona, który wskazówki na przyczynę problemu, ponieważ pasuje objawów (czarne po lewej stronie obrazów).  
  
    -   Pola, które wyświetla wartości 0 pikseli (na przykład obramowanie i dopełnienie) sugeruje, że prawdopodobnie nie są ustawione odpowiednie właściwości CSS.  
  
11. Aby zobaczyć sposób zastosowania reguły lewy margines, wybierz **obliczane** kartę i sprawdź w obszarze reguła lewy margines. Widać, że ta zasada została ustawiona za pomocą wartości 5em obliczoną wartością jest jednak 66.66px lub 146.66px, w zależności od urządzenia docelowego.  
  
    > [!TIP]
    >  **Obliczane** karta pokazuje, że reguła lewy margines jest ustawiony w `..hubpage .hub. section4 .sub-image-row img` selektora CSS, znaleziono w hub.css. W tej wersji demonstracyjnej aplikacji to, gdzie musisz wprowadzić poprawkę.  
  
     Można również użyć **układ** kartę, aby przetestować modyfikacje wartościom układu.  
  
12. W **układ** karty, wybierz opcję **66.66** lub **146.66**, który pojawia się w **margines** pole po lewej stronie pola.  
  
13. Typ `0` i naciśnij klawisz Enter. (Umożliwia także klawiszy Strzałka w górę i Strzałka w dół na zmianę wartości.)  
  
14. Wybierz inny \<img > elementów w Eksploratorze DOM i zmień ich lewy margines wartości na 0.  
  
15. Przełącz się do emulatora telefonu lub symulatora. Zaktualizowane wartości lewy margines zostały zastosowane do obrazów sekcja 4. Te wartości są aktualizowane w **obliczane** kartę w obszarze reguła lewy margines.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki Start: Debugowanie HTML i CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Debugowanie stylów CSS przy użyciu Eksploratora modelu DOM](../debugger/debug-css-styles-using-dom-explorer.md)   
 [Wyświetlanie odbiorników zdarzeń DOM](../debugger/view-dom-event-listeners.md)




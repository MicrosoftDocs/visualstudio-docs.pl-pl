---
title: 'Instrukcje: Śledzenie kodu przez dostosowania paska przewijania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 11df0e3ca4e8b9c814bf91735d48bb091c711068
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788209"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Instrukcje: Śledzenie kodu przez dostosowania paska przewijania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas pracy z plikami kodu długo może być trudny do wszystko, co należy wziąć pod uwagę. Można dostosować paska przewijania, okna kodu, które umożliwiają ptaka co się dzieje w kodzie.  
  
### <a name="to-show-annotations-on-the-scroll-bar"></a>Aby wyświetlić adnotacje paska przewijania  
  
1.  Na pasku przewijania można skonfigurować do pokazywania zmian w kodzie, punkty przerwania, błędy i zakładek.  
  
     Otwórz **paska przewijania** Strona opcji (**narzędzia, opcje, Edytor tekstu. Wszystkie języki** lub określonego języka lub typ **paska przewijania** w oknie szybkiego uruchamiania).  
  
2.  Wybierz **Pokaż adnotacje na pionowym pasku przewijania**, następnie wybierz pozycję adnotacji mają być wyświetlane. ( **Znaczniki** opcja powoduje dołączenie punkty przerwania i zakładki.)  
  
3.  Teraz wypróbuj działanie rozwiązania. Otwórz plik kodu duże i Zastąp coś, co występuje w kilku miejscach w pliku. Pasek przewijania pokazuje wpływ zamiany, dzięki czemu można wycofywanie zmian użytkownika, jeśli coś, czego nie powinny mieć zastąpiony.  
  
     Poniżej przedstawiono wygląd paska przewijania po wyszukiwanie ciągu. Należy zauważyć, że są wyświetlane wszystkie wystąpienia ciągu.  
  
     ![Pasek przewijania, po zakończeniu wyszukiwania ciągu. ](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")  
  
     Oto pasek przewijania po zastąpieniu wszystkie wystąpienia ciągu. Od razu można zobaczyć, że operacja spowodowała pewne problemy.  
  
     ![Pasek przewijania, zastępując ciąg z błędami](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")  
  
### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Aby ustawić tryb wyświetlania dla paska przewijania  
  
1.  Na pasku przewijania ma dwa tryby, tryb paska (ustawienie domyślne) i tryb mapy. Pasek tryb po prostu wyświetla wskaźniki adnotacji paska przewijania. W trybie mapy wiersze kodu są reprezentowane na pasku przewijania. Można wybrać, jak szeroki są one oraz czy występują podstawowy kod gdy wskaźnik myszy znajduje się na nich. Po kliknięciu lokalizacji paska przewijania, kursor przesuwa się do tej lokalizacji w kodzie. Zwinięte regiony są zacieniowane w różny sposób. są one rozszerzona, gdy klikniesz dwukrotnie.  
  
     Na **paska przewijania** Opcje strony, wybierz opcję **tryb użyj paska dla pionowego paska przewijania** lub **tryb Użyj mapy dla pionowego paska przewijania**. Możesz wybrać szerokość w **Przegląd źródła** listy rozwijanej.  
  
     Poniżej przedstawiono przykładowe wyszukiwanie wygląd mapy tryb jest włączony i szerokość jest ustawiony na średni:  
  
     ![Pasek przewijania w trybie mapy](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")  
  
2.  W trybie mapę, aby włączyć Podgląd kodu podczas przesuwania kursora w górę i w dół na pasku przewijania, wybierz **Pokaż etykietki narzędzia w wersji zapoznawczej** opcji. Oto jak wygląda:  
  
     ![Pasek przewijania z etykietka narzędzia](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")  
  
     Jeśli chcesz zachować tryb mapy przewijanie zachowanie i etykietki narzędzi w wersji zapoznawczej, ale nie chcesz zobaczyć Przegląd kodu źródłowego, możesz ustawić **Przegląd źródła** do **poza**.

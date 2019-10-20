---
title: 'Instrukcje: śledzenie kodu przez dostosowanie paska przewijania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a852b0e5ac6c6a677caab97279a0b0cb0299d27f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670635"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Instrukcje: śledzenie kodu przez dostosowanie paska przewijania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas pracy z długimi plikami kodu może być trudno zachować wszystko. Możesz dostosować pasek przewijania okna kod, aby dać ci wgląd w oczy dotyczące tego, co dzieje się w kodzie.

### <a name="to-show-annotations-on-the-scroll-bar"></a>Aby pokazać adnotacje na pasku przewijania

1. Pasek przewijania można skonfigurować tak, aby pokazywał zmiany kodu, punkty przerwania, błędy i zakładki.

     Otwórz stronę opcje **paska przewijania** (**menu Narzędzia, opcje Edytor tekstu. Wszystkie języki** lub określony język lub wpisz **pasek przewijania** w oknie szybkie uruchamianie).

2. Wybierz pozycję **Pokaż adnotacje na pionowym pasku przewijania**, a następnie wybierz Adnotacje, które chcesz zobaczyć. ( **Znaczniki** opcji obejmują punkty przerwania i zakładki).

3. Wypróbuj teraz. Otwórz plik dużego kodu i Zastąp coś, co występuje w kilku miejscach w pliku. Pasek przewijania pokazuje efekt zamian, dzięki czemu można cofnąć zmiany, jeśli zamienisz coś, czego nie trzeba.

     Oto jak wygląda pasek przewijania po wyszukiwaniu ciągu. Zwróć uwagę, że wyświetlane są wszystkie wystąpienia ciągu.

     ![Pasek przewijania po wyszukiwaniu ciągu.](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")

     Poniżej znajduje się pasek przewijania po zastąpieniu wszystkich wystąpień ciągu. Możesz sprawdzić, czy operacja spowodowała pewne problemy.

     ![Pasek przewijania po zamianie ciągu z błędami](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")

### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Aby ustawić tryb wyświetlania paska przewijania

1. Pasek przewijania ma dwa tryby, tryb paska (domyślny) i tryb mapowania. Tryb paska po prostu wyświetla wskaźniki adnotacji na pasku przewijania. W trybie mapy wiersze kodu są reprezentowane na pasku przewijania. Można wybrać, jak szerokie są i czy mają być wyświetlane bazowe kod po umieszczeniu na nich wskaźnika. Gdy klikniesz lokalizację na pasku przewijania, kursor zostanie przeniesiony do tej lokalizacji w kodzie. Zwinięte regiony są zacienione inaczej. są one rozwijane po dwukrotnym kliknięciu.

     Na stronie opcje **paska przewijania** wybierz opcję **Użyj trybu paska dla pionowego paska przewijania** lub **Użyj trybu mapy dla pionowego paska przewijania**. Możesz wybrać szerokość z listy rozwijanej **Przegląd źródła** .

     Oto jak wygląda przykład wyszukiwania, gdy tryb mapy jest włączony, a szerokość jest ustawiona na Średni:

     ![Pasek przewijania w trybie mapy](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")

2. W trybie mapy, aby włączyć podgląd kodu po przesunięciu kursora w górę i w dół paska przewijania, wybierz opcję **Pokaż etykietkę narzędzia podglądu** . Oto jak wygląda:

     ![Pasek przewijania z etykietką narzędzia](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")

     Jeśli chcesz zachować zachowanie przewijania w trybie mapy i wyświetlić etykietkę narzędzia, ale nie chcesz zobaczyć przeglądu kodu źródłowego, możesz ustawić pozycję **Przegląd źródła** na **off**.

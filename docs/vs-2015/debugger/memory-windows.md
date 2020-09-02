---
title: Okna pamięci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e60f9b3c9acf1377139fee27486bb10251d8804a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158470"
---
# <a name="memory-windows"></a>Okno pamięci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **pamięci** zapewnia widok ilości miejsca w pamięci używanej przez aplikację. Okno **czujka** **, okno dialogowe** **QuickWatch** , okna **zmiennych i ustawienia regionalne** wyświetlają zawartość zmiennych, które są przechowywane w określonych lokalizacjach w pamięci. Jednak okno **pamięci** pokazuje obraz o dużej skali. Ten widok może być wygodny do badania dużych fragmentów danych (np. buforów lub dużych ciągów), które nie są dobrze wyświetlane w innych oknach. Jednak okno **pamięci** nie jest ograniczone do wyświetlania danych. Wyświetla wszystko w obszarze pamięci, niezależnie od tego, czy zawartość to dane, kod czy losowe bity elementów bezużytecznych w nieprzydzielonej pamięci.  
  
 Okno **pamięci** jest dostępne tylko wtedy, gdy w oknie dialogowym **Opcje** jest**włączone debugowanie na** poziomie adresu. Okno **pamięci** nie jest dostępne dla skryptów ani SQL, które są językami, które nie rozpoznają koncepcji pamięci.  
  
## <a name="opening-a-memory-window"></a>Otwieranie okna pamięci  
  
#### <a name="to-open-a-memory-window"></a>Aby otworzyć okno pamięci  
  
1. Rozpocznij debugowanie, jeśli nie jest jeszcze w trybie debugowania.  
  
2. W menu **Debuguj** wskaż pozycję **Windows**. Następnie wskaż polecenie **pamięć** , a następnie kliknij pozycję **pamięć 1**, **pamięć 2**, **pamięć 3**lub **4**. (Wersje niższego poziomu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mają tylko jedno okno **pamięci** . Jeśli używasz jednej z tych wersji, po prostu kliknij pozycję **pamięć**.  
  
## <a name="paging-in-the-memory-window"></a>Stronicowanie w oknie pamięci  
 Okno **pamięci** ma pionowy pasek przewijania, który działa w sposób niestandardowym. Przestrzeń adresowa nowoczesnego komputera jest bardzo duża i można ją łatwo uzyskać, pobierając kciuk paska przewijania i przeciągając go do lokalizacji losowej. Z tego powodu kciuk jest "ładowany" i zawsze pozostaje w środku paska przewijania. W aplikacjach kodu natywnego można wyłączać się w górę lub w dół, ale nie można przewijać w dowolny sposób.  
  
 Wyższe adresy pamięci są wyświetlane u dołu okna. Aby wyświetlić wyższy adres, przewiń w dół, nie w górę.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Na stronę w górę lub w dół w pamięci  
  
1. Na stronę w dół (przejdź do wyższego adresu pamięci) kliknij przycisk pod kciukem na pionowym pasku przewijania.  
  
2. Aby Page Up (przejść do niższego adresu pamięci), kliknij powyżej kciuka pionowego paska przewijania.  
  
## <a name="selecting-a-memory-location"></a>Wybieranie lokalizacji pamięci  
 Jeśli chcesz natychmiast przenieść do wybranej lokalizacji w pamięci, możesz to zrobić przy użyciu operacji przeciągania i upuszczania lub edytując wartość w polu **adres** . Pole **adres** akceptuje nie tylko wartości liczbowe, ale również wyrażenia, które obliczają adresy. Domyślnie okno **pamięci** traktuje wyrażenie **adresu** jako wyrażenie dynamiczne, które jest obliczane w trakcie wykonywania programu. Wyrażenia na żywo mogą być bardzo przydatne. Na przykład można użyć ich do wyświetlenia pamięci, która jest wskaźnikiem.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Aby wybrać lokalizację pamięci przez przeciąganie i upuszczanie  
  
1. W dowolnym oknie Wybierz adres pamięci lub zmienną wskaźnika, która zawiera adres pamięci.  
  
2. Przeciągnij adres lub wskaźnik do okna **pamięci** .  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Aby wybrać lokalizację pamięci, edytując  
  
1. W oknie **pamięć** wybierz pole **adres** .  
  
2. Wpisz lub wklej adres, który chcesz zobaczyć, a następnie naciśnij klawisz **Enter**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Zmiana sposobu wyświetlania informacji w oknie pamięci  
 Możesz dostosować sposób, w jaki okno **pamięci** wyświetla zawartość pamięci. Domyślnie zawartość pamięci jest wyświetlana jako liczba całkowita jednobajtowa w formacie szesnastkowym, a liczba kolumn jest określana automatycznie przez bieżącą szerokość okna.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Aby zmienić format zawartości pamięci  
  
1. Kliknij prawym przyciskiem myszy okno **pamięci** .  
  
2. Wybierz odpowiedni format.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Aby zmienić liczbę kolumn w oknie pamięci  
  
1. Na pasku narzędzi u góry okna **pamięci** Znajdź listę **kolumny** .  
  
2. Z listy **kolumny** wybierz liczbę kolumn, które mają być wyświetlane, lub wybierz opcję **Automatyczne** dopasowanie automatyczne, aby dopasować szerokość okna.  
  
   Jeśli nie chcesz, aby zawartość okna **pamięci** była zmieniana podczas wykonywania programu, możesz wyłączyć ocenę wyrażenia na żywo.  
  
#### <a name="to-toggle-live-evaluation"></a>Aby włączyć ocenę na żywo  
  
1. Kliknij prawym przyciskiem myszy okno **pamięci** .  
  
2. W menu skrótów kliknij polecenie **Oblicz automatycznie**.  
  
    Jeśli Ocena na żywo jest włączona, opcja zostanie wybrana, a kliknięcie jej spowoduje wyłączenie oceny na żywo. Jeśli Ocena na żywo jest wyłączona, opcja nie jest zaznaczona, a kliknięcie jej spowoduje włączenie oceny na żywo.  
  
   Pasek narzędzi można ukryć lub wyświetlić u góry okna **pamięci** . Nie będziesz mieć dostępu do pola adresu lub innych narzędzi, o ile pasek narzędzi jest ukryty.  
  
#### <a name="to-toggle-the-toolbar"></a>Aby przełączyć pasek narzędzi  
  
1. Kliknij prawym przyciskiem myszy okno **pamięci** .  
  
2. W menu skrótów kliknij polecenie **Pokaż pasek narzędzi**.  
  
     Pasek narzędzi pojawia się lub znika, w zależności od jego poprzedniego stanu.  
  
## <a name="following-a-pointer-through-memory"></a>Po wskaźniku do pamięci  
 W aplikacjach kodu natywnego można używać nazw rejestrów jako wyrażeń dynamicznych. Na przykład możesz użyć wskaźnika stosu, aby postępować zgodnie ze stosem.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Aby podążać za wskaźnikiem za pomocą pamięci  
  
1. W polu **adres** okna **pamięci** wpisz wyrażenie wskaźnika. Zmienna wskaźnika musi znajdować się w bieżącym zakresie. W zależności od języka może być konieczne jego wypróbowanie.  
  
2. Naciśnij klawisz **Enter**.  
  
     Teraz, gdy użyjesz polecenia wykonywania, takiego jak **Step**, wyświetlany adres pamięci zostanie automatycznie zmieniony, gdy wskaźnik zmieni się.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)

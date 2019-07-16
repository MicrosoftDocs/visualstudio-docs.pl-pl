---
title: Windows pamięci | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158470"
---
# <a name="memory-windows"></a>Okno pamięci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Pamięci** okna zapewnia wgląd w to obszar pamięci, który jest używany przez aplikację. **Obejrzyj** oknie **QuickWatch** okno dialogowe **automatyczne** oknie i **lokalne** okno Pokaż zawartość zmiennych, które są przechowywaną w określonej lokalizacji w pamięci. Ale **pamięci** okno zawiera obraz na dużą skalę. Ten widok może być wygodną badanie dużej części danych (buforów lub dużych ciągów, na przykład), które nie są wyświetlane poprawnie w innych oknach. Jednak **pamięci** okno nie jest ograniczona do wyświetlania danych. Wyświetla wszystkie elementy w obszarze pamięci czy zawartość jest dane, kod lub losowych bity wyrzucania elementów w pamięci nieprzypisane.  
  
 **Pamięci** okno jest dostępne tylko wtedy, gdy debugowanie na poziomie adresów jest włączone w **opcje** okno dialogowe**debugowanie** węzła. **Pamięci** okno nie jest dostępne dla skryptu lub SQL, które są języki, które nie rozpoznają koncepcji pamięci.  
  
## <a name="opening-a-memory-window"></a>Otwierając okno pamięci  
  
#### <a name="to-open-a-memory-window"></a>Aby otworzyć okno pamięci  
  
1. Uruchom profilowanie, jeśli nie jesteś już w trybie debugowania.  
  
2. W **debugowania** menu wskaż **Windows**. Następnie wskaż **pamięci** a następnie kliknij przycisk **pamięci 1**, **pamięci 2**, **3 pamięci**, lub **pamięci 4**. (Niższe wersje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mieć tylko jeden **pamięci** okna. Jeśli używasz jednego z tych wersji, wystarczy kliknąć **pamięci**.)  
  
## <a name="paging-in-the-memory-window"></a>Stronicowanie w oknie pamięci  
 **Pamięci** okno ma pionowy pasek przewijania, który działa w sposób niestandardowy. Przestrzeń adresowa nowoczesnych komputera jest bardzo duże, a użytkownik może łatwo giną Przechwytywanie przycisku przewijania suwaka, a następnie przeciągając go do losowo wybranej lokalizacji. Z tego powodu uchwytu jest "obciążony" i zawsze pozostaje w środkowej części paska przewijania. W aplikacjach kodu macierzystego można stronę w górę lub w dół, ale nie można swobodnie Przewiń o.  
  
 Wyższe adresy pamięci są wyświetlane w dolnej części okna. Aby wyświetlić adres wyższe, przewiń w dół, nie rozmiarze.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Stronę w górę lub w dół w pamięci  
  
1. Na stronie szczegółów (przeniesienie na wyższe adresu pamięci), kliknij w obszarze przycisku przewijania w pionowy pasek przewijania.  
  
2. Stronę w górę (przeniesienie na niższym adresu pamięci), kliknij powyżej przycisku suwaka pionowy pasek przewijania.  
  
## <a name="selecting-a-memory-location"></a>Wybieranie lokalizacji w pamięci  
 Jeśli chcesz przechodzić bezpośrednio do wybranej lokalizacji w pamięci, możesz to zrobić przy użyciu operacji przeciągania i upuszczania lub też edytując wartość **adres** pole. **Adres** w polu można nie tylko wartości liczbowe, ale także wyrażeń, które dają adresów. Domyślnie **pamięci** traktuje okna **adres** wyrażenia jako wyrażenia na żywo jest ponownie oceniane, gdy program jest wykonywana. Wyrażenia na żywo mogą być bardzo przydatne. Na przykład umożliwia im wyświetlanie pamięci, która jest korzystały wskaźnik.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Aby wybrać lokalizację pamięci przez przeciąganie i upuszczanie  
  
1. W dowolnym oknie Wybierz pamięci adres lub wskaźnik zmienna, która zawiera adres pamięci.  
  
2. Przeciągnij adres lub wskaźnik do **pamięci** okna.  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Aby wybrać lokalizację pamięci, edytując  
  
1. W **pamięci** wybierz **adres** pole.  
  
2. Wpisz lub wklej adres, aby zobaczyć, a następnie naciśnij klawisz **ENTER**.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Zmienia sposób Wyświetla informacje okna pamięci  
 Można dostosować sposób **pamięci** okno wyświetla zawartość pamięci. Domyślnie zawartość pamięci są wyświetlane jako jedna bajtowe liczby całkowite w formacie szesnastkowym, a liczba kolumn jest określana automatycznie przez bieżący szerokość okna.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Aby zmienić format zawartość pamięci  
  
1. Kliknij prawym przyciskiem myszy **pamięci** okna.  
  
2. Wybierz żądany format.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Aby zmienić liczbę kolumn w oknie pamięci  
  
1. Na pasku narzędzi u góry **pamięci** oknie Znajdź **kolumn** listy.  
  
2. W **kolumn** , wybierz liczbę kolumn, które chcesz wyświetlić, lub zaznacz na liście **automatycznie** automatycznego dostosowania do Dopasuj szerokość okna.  
  
   Jeśli nie chcesz, aby zawartość **pamięci** wykonuje okna, aby zmienić jako program, można wyłączyć oceny wyrażenia na żywo.  
  
#### <a name="to-toggle-live-evaluation"></a>Aby przełączyć na żywo oceny  
  
1. Kliknij prawym przyciskiem myszy **pamięci** okna.  
  
2. W menu skrótów kliknij **automatycznie Oblicz ponownie**.  
  
    Jeśli ocena na żywo jest włączona, zostanie wybrana opcja, a kliknięcie powoduje wyłączenie oceny na żywo. Jeśli oceny na żywo jest wyłączona, nie zaznaczono opcji, a następnie klikając go Włącza obliczanie na żywo.  
  
   Można ukryć lub wyświetlić pasek narzędzi w górnej części **pamięci** okna. Nie masz dostępu do adresu pola lub innych narzędzi, tak długo, jak pasek narzędzi jest ukryty.  
  
#### <a name="to-toggle-the-toolbar"></a>Aby przełączyć na pasku narzędzi  
  
1. Kliknij prawym przyciskiem myszy **pamięci** okna.  
  
2. W menu skrótów kliknij **Pokaż pasek narzędzi**.  
  
     Pasek narzędzi pojawi się lub znika, w zależności od poprzedniego stanu.  
  
## <a name="following-a-pointer-through-memory"></a>Śledzenie wskaźnika za pomocą pamięci  
 W aplikacji kod macierzysty można użyć nazw rejestrów jako wyrażenia na żywo. Na przykład można użyć wskaźnik stosu do wykonania na stosie.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Aby podążał za wskaźnikiem za pośrednictwem pamięci  
  
1. W **pamięci** okna **adres** wpisz wyrażenie wskaźnika. Zmienna wskaźnika musi być w bieżącym zakresie. W zależności od języka może być konieczne odwołania do niego.  
  
2. Naciśnij klawisz **ENTER**.  
  
     Teraz, kiedy używasz polecenia wykonywania takich jak **kroku**, adres pamięci, która jest wyświetlana automatycznie zmieni się zgodnie ze zmianami wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)

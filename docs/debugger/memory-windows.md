---
title: Wyświetlanie pamięci dla zmiennych w debugerze | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdf8e5fc5ee0ac34b4c295f6cc593e0a93b548ae
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257267"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Używanie okien pamięci w debugerze programu Visual Studio (C#, C++, Visual Basic F#)

Podczas debugowania, **pamięci** okno pokazuje aplikacja używa miejsce w pamięci. 

Debugera, takie jak **Obejrzyj**, **Autos**, **lokalne**i **QuickWatch** okna dialogowego dowiesz się, zmienne, które są przechowywane w określonych lokalizacje w pamięci. **Pamięci** okno przedstawia ogólny obraz. Widok pamięci jest wygodne w przypadku badanie dużej części danych (buforów lub dużych ciągów, na przykład), które nie są wyświetlane poprawnie w innych oknach. 

**Pamięci** okno nie jest ograniczona do wyświetlania danych. Wyświetla wszystkie elementy w obszarze pamięci, włącznie z danymi, kodu i losowe bity wyrzucania elementów w pamięci nieprzypisane.  

**Pamięci** okno nie jest dostępna dla skryptu lub debugowania SQL. Te języki nie rozpoznają koncepcji pamięci.  
  
## <a name="open-a-memory-window"></a>Otwórz okno pamięci  
  
Inne okna debugera, takie jak **pamięci** systemu windows są dostępne tylko podczas sesji debugowania. 

>[!IMPORTANT]
>Aby włączyć **pamięci** systemu windows, **Włącz debugowanie na poziomie adresów** należy wybrać w **narzędzia** > **opcje** (lub **Debugowania** > **opcje**) > **debugowania** > **ogólne**. 

**Aby otworzyć okno pamięci**
  
1. Upewnij się, że **Włącz debugowanie na poziomie adresów** wybrano **narzędzia** > **opcje** (lub **debugowania**  >  **Opcje**) > **debugowania** > **ogólne**. 
   
1. Rozpocznij debugowanie wybierając zielona strzałka, naciskając klawisz **F5**, lub wybierając **debugowania** > **Rozpocznij debugowanie**.  
   
2. W obszarze **debugowania** > **Windows** > **pamięci**, wybierz opcję **pamięci 1**, **pamięci 2**, **Pamięci 3**, lub **pamięci 4**. (Niektóre wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oferować tylko jeden **pamięci** okna.)  

## <a name="move-around-in-the-memory-window"></a>Poruszanie się w oknie pamięci  

Przestrzeni adresowej komputera jest duży i mogą łatwo utracić swoje miejsce, przewijając w **pamięci** okna. 

Wyższe adresy pamięci są wyświetlane w dolnej części okna. Aby wyświetlić adres wyższe, przewiń w dół. Aby wyświetlić adres niższy, przewiń w górę.  

Możesz natychmiast przejść do określonego adresu w **pamięci** okna przy użyciu przeciągania i upuszczania lub wprowadzając adres w **adres** pola. **Adres** polu można podawać adresów alfanumeryczne i wyrażeń, które dają adresów, takich jak `e.User.NonroamableId`. 

Aby wymusić natychmiastowe ponownej oceny wyrażenia w **adres** wybierz zaokrąglone strzałkę **automatycznie Oblicz ponownie** ikony. 

Domyślnie **pamięci** traktuje okna **adres** wyrażenia jako wyrażenia na żywo, które są ponownie oceniane jako uruchomienia aplikacji. Wyrażenia na żywo mogą być przydatne, na przykład, aby wyświetlić pamięci, która jest korzystały zmiennej wskaźnika.  

**Przeciągnij i upuść, aby przejść do lokalizacji w pamięci:**  
   
1. W dowolnym oknie debugera wybierz adres pamięci lub zmiennej wskaźnika, który zawiera adres pamięci.  
   
2. Przeciąganie i upuszczanie adres lub wskaźnika w **pamięci** okna. Pojawi się w tym adresem **adres** pola i **pamięci** okna dostosowuje się do tego adresu jest wyświetlana u góry. 
  
**Aby przejść do lokalizacji w pamięci, wprowadzając ją w polu adresu:**
  
- Wpisz lub wklej adres lub wyrażenia w **adres** pole i naciśnij klawisz **Enter**, lub wybierz go z listy rozwijanej w **adres** pola. **Pamięci** okna dostosowuje się do tego adresu jest wyświetlana u góry.
  
## <a name="customize-the-memory-window"></a>Dostosowywanie okna pamięci 

Domyślnie zawartość pamięci są wyświetlane jako 1-bajtowe liczby całkowite w formacie szesnastkowym, a szerokość okna określa liczbę kolumn. Można dostosować sposób **pamięci** okno wyświetla zawartość pamięci.  
  
**Aby zmienić format zawartości pamięci:**  
  
-  Kliknij prawym przyciskiem myszy **pamięci** okna, a następnie wybierz formaty, które mają z menu kontekstowego.  
  
**Aby zmienić liczbę kolumn w oknie pamięci:**
  
- Wybierz strzałkę listy rozwijanej obok pozycji **kolumn** pola, a następnie wybierz liczbę kolumn do wyświetlenia lub wybierz **automatycznie** automatycznego dostosowania oparte na szerokość okna.  
  
Jeśli nie chcesz, aby zawartość **pamięci** okna, aby zmienić co aplikacja zostanie uruchomiona, można wyłączyć oceny wyrażenia na żywo. 

**Aby przełączyć na żywo oceny:**  
  
- Kliknij prawym przyciskiem myszy **pamięci** okna, a następnie wybierz **automatycznie Oblicz ponownie** w menu kontekstowym. 

  >[!NOTE]
  >Na żywo wyrażenie oceny jest przełącznik i jest domyślnie, więc wybranie **automatycznie Oblicz ponownie** wyłączenie rejestrowania. Wybieranie **automatycznie Oblicz ponownie** ponownie włącza je ponownie. 
  
Można ukryć lub wyświetlić pasek narzędzi w górnej części **pamięci** okna. Nie będziesz mieć dostęp do **adres** pól lub innych narzędzi, gdy pasek narzędzi jest ukryty.  
  
**Aby przełączać wyświetlanie paska narzędzi:**  
  
- Kliknij prawym przyciskiem myszy **pamięci** okna, a następnie wybierz **Pokaż pasek narzędzi** w menu kontekstowym. Pasek narzędzi pojawi się lub znika, w zależności od poprzedniego stanu.  
  
## <a name="follow-a-pointer-through-memory"></a>Podążał za wskaźnikiem za pośrednictwem pamięci  

W aplikacji kod macierzysty można użyć nazw rejestrów jako wyrażenia na żywo. Na przykład można użyć wskaźnik stosu do wykonania na stosie.  
  
**Aby podążał za wskaźnikiem za pośrednictwem pamięci:**
  
1. W **pamięci** okna **adres** wprowadź wyrażenie wskaźnika, który znajduje się w bieżącym zakresie. W zależności od języka może być konieczne odwołania do niego.  
  
2. Naciśnij klawisz **wprowadź**.  
   
   Kiedy używasz polecenia debug takich jak **kroku**, adres pamięci, wyświetlana w **adres** pól i w górnej części **pamięci** okno automatycznie zmienia się, gdy wskaźnik myszy zmiany.  
  
## <a name="see-also"></a>Zobacz także  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
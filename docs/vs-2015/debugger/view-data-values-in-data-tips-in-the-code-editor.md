---
title: Wyświetlanie wartości danych w poradach dotyczących danych w edytorze kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c6c6407c038c7d6847db073c1f00c103d9483e78
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039118"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Podgląd wartości danych w poradach dotyczących danych w edytorze kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataTips zapewniają wygodny sposób wyświetlania informacji na temat zmiennych w programie podczas debugowania. DataTips działa tylko w trybie przerwania i tylko w przypadku zmiennych, które znajdują się w bieżącym zakresie wykonywania.  
  
 W [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]DataTips, które można przypiąć do określonej lokalizacji w pliku źródłowym i poruszać się na podstawie wszystkich [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] systemu windows.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Aby wyświetlić etykietki danych (tylko w trybie przerwania)  
  
1. W oknie źródła umieść wskaźnik myszy na dowolnej zmiennej w bieżącym zakresie.  
  
    Pojawi się DataTip.  
  
   > [!NOTE]
   >  Porady dotyczące danych są zawsze obliczane w kontekście, w przypadku, gdy wykonanie programu jest zawieszone, a nie w przypadku, gdy kursor znajduje się. Po umieszczeniu wskaźnika myszy nad zmienną w innej funkcji o tej samej nazwie jako zmiennej, która znajduje się w bieżącym kontekście, wartość zmiennej w innych funkcji jest wyświetlany jako wartość zmiennej w bieżącym kontekście.  
  
2. DataTip zniknie po usunięciu wskaźnika myszy. Aby przypiąć DataTip pozostaje otwarty, kliknij przycisk **Przypnij do źródła** ikony, lub  
  
   - Kliknij prawym przyciskiem myszy na zmiennej, a następnie kliknij przycisk **Przypnij do źródła**.  
  
     Przypiętych etykietki danych zostanie zamknięte po zakończeniu sesji debugowania.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Odepnij poradzie dotyczącej danych i liczb zmiennoprzecinkowych  
  
- Etykietki danych przypięte, kliknij **Odepnij od źródła** ikony.  
  
     Ikona zmiany kodu pin nieprzypięte pozycji. DataTip jest teraz wyświetlany powyżej wszelkie otwarte okna. Zmiennoprzecinkowe DataTip zamyka podczas kończenia sesji debugowania.  
  
### <a name="to-repin-a-floating-datatip"></a>Aby repin zmiennoprzecinkowy etykietki danych  
  
- W poradzie dotyczącej danych kliknij ikonę pinezki.  
  
     Ikona zmiany kodu pin przypiętych pozycji. Jeśli DataTip jest poza oknem źródła, ikonę pinezki jest wyłączona i nie można przypiąć DataTip.  
  
### <a name="to-close-a-datatip"></a>Aby zamknąć etykietki danych  
  
- Umieść wskaźnik myszy nad etykietki danych, a następnie kliknij przycisk **Zamknij** ikony.  
  
### <a name="to-close-all-datatips"></a>Aby zamknąć wszystkie etykietki danych  
  
- Na **debugowania** menu, kliknij przycisk **wyczyść wszystkie etykietki danych**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Aby zamknąć wszystkie etykietki danych dla określonego pliku  
  
- Na **debugowania** menu, kliknij przycisk **wyczyść wszystkie etykietki danych przypięte do** *pliku*.  
  
## <a name="expanding-and-editing-information"></a>Rozwijanie i edytowanie informacji o  
 Korzystanie z DataTips, aby rozwinąć tablica, struktury lub obiekt, aby wyświetlić jego składowe. Można również edytować wartość zmiennej w poradzie dotyczącej danych.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Aby rozwinąć zmiennej, aby zobaczyć jego elementy  
  
- W DataTip, umieść wskaźnik myszy **+** logowania, która znajduje się przed nazwę zmiennej.  
  
     Zmienna rozwijany, aby wyświetlić jego elementy w postaci drzewa.  
  
     Po rozwinięciu zmiennej, można przenieść w górę i w dół za pomocą klawiszy strzałek na klawiaturze. Alternatywnie można użyć myszy.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Aby edytować wartość zmiennej za pomocą etykietki danych  
  
1. W poradzie dotyczącej danych kliknij wartość. Ta opcja jest wyłączona dla wartości tylko do odczytu.  
  
2. Wpisz nową wartość, a następnie naciśnij klawisz ENTER.  
  
## <a name="making-a-datatip-transparent"></a>Ustawianie etykietki danych przezroczystości  
 Jeśli chcesz wyświetlić kod, który znajduje się za etykietki danych, istnieje możliwość DataTip tymczasowo przezroczysty. To nie dotyczy DataTips, które są przypięte lub zmiennoprzecinkową.  
  
#### <a name="to-make-a-datatip-transparent"></a>Aby przezroczyste etykietki danych  
  
- W DataTip naciśnij klawisz CTRL.  
  
     DataTip pozostanie przezroczyste, tak długo, jak przytrzymaj wciśnięty klawisz CTRL.  
  
## <a name="visualizing-complex-data-types"></a>Wizualizacji złożonych typów danych  
 Jeśli ikona lupy pojawi się obok nazwy zmiennej w poradzie dotyczącej danych, co najmniej jeden [Tworzenie niestandardowych Wizualizatorów](../debugger/create-custom-visualizers-of-data.md) są dostępne dla zmiennych typu danych. Korzystanie z wizualizatora, aby wyświetlić informacje w sposób bardziej zrozumiały, zwykle graficznego.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Aby wyświetlić zawartość zmiennej za pomocą wizualizatora  
  
- Kliknij ikonę lupy, aby wybrać Wizualizator domyślna dla typu danych.  
  
     —lub—  
  
     Wyskakujące strzałki obok visualizer, aby wybrać z listy odpowiedni wizualizatorów typu danych.  
  
     Informacje wyświetlane wizualizatora.  
  
## <a name="adding-information-to-a-watch-window"></a>Dodawanie informacji do okna czujki  
 Jeśli chcesz obejrzeć zmiennej w dalszym ciągu można dodać zmienną **Obejrzyj** poradzie dotyczącej danych w oknie Pomoc.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Aby dodać zmienną w oknie czujki  
  
- Kliknij prawym przyciskiem myszy etykietki danych, a następnie kliknij przycisk **Dodaj czujkę**.  
  
     Zmienna jest dodawany do **Obejrzyj** okna. Jeśli używasz wersji, która obsługuje wiele **Obejrzyj** systemu windows, zmienna jest dodawany do **Czujka 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Importowanie i eksportowanie etykietki danych  
 Możesz wyeksportować etykietek danych do pliku XML, które mogą być udostępniane przez współpracowników lub edytować za pomocą edytora tekstów.  
  
#### <a name="to-export-datatips"></a>Aby wyeksportować etykietek danych  
  
1. Polecenie menu Debuguj **Eksportuj etykietki danych**.  
  
     **Eksportuj etykietki danych** pojawi się okno dialogowe.  
  
2. Przejdź do lokalizacji, w którym chcesz zapisać plik XML, wpisz nazwę dla pliku przy użyciu standardowych plikowych technik **nazwy pliku** , a następnie kliknij przycisk **OK**.  
  
#### <a name="to-import-datatips"></a>Aby zaimportować etykietek danych  
  
1. Polecenie menu Debuguj **Importuj etykietki danych**.  
  
     **Importuj etykietki danych** pojawi się okno dialogowe.  
  
2. Użyj okna dialogowego, aby znaleźć plik XML, który chcesz otworzyć, a następnie kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Instrukcje: Użyj okna dialogowego QuickWatch](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Tworzenie niestandardowych Wizualizatorów](../debugger/create-custom-visualizers-of-data.md)   
 [Instrukcje: Zmień Format numeryczny debuger Windows](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)

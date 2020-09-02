---
title: Wyświetlanie wartości danych w etykietkach danych w edytorze kodu | Microsoft Docs
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
ms.openlocfilehash: fd2c7bf67b5c2e7f25b4193462883b53cda8db87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700110"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Podgląd wartości danych w poradach dotyczących danych w edytorze kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Porady datapreview zapewniają wygodny sposób wyświetlania informacji o zmiennych w programie podczas debugowania. Etykietki danych działają tylko w trybie przerwania i są tylko w przypadku zmiennych, które znajdują się w bieżącym zakresie wykonywania.  
  
 W systemie [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] etykietki danych można przypinać do określonej lokalizacji w pliku źródłowym lub mogą być przepływane na wszystkich [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknach.  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Aby wyświetlić etykietki danych (tylko w trybie przerwania)  
  
1. W oknie źródła umieść wskaźnik myszy nad dowolną zmienną w bieżącym zakresie.  
  
    Zostanie wyświetlona etykietki danych.  
  
   > [!NOTE]
   > Porady dotyczące danych są zawsze oceniane w kontekście, w którym wykonywanie jest zawieszone, a nie miejsca, w którym kursor jest aktywowany. Po umieszczeniu wskaźnika myszy nad zmienną w innej funkcji o takiej samej nazwie jak zmienna, która znajduje się w bieżącym kontekście, wartość zmiennej w innej funkcji jest wyświetlana jako wartość zmiennej w bieżącym kontekście.  
  
2. Etykietki danych znika po usunięciu wskaźnika myszy. Aby przypiąć etykietki danych, tak aby pozostała otwarta, kliknij ikonę **Przypnij do źródła** lub  
  
   - Kliknij prawym przyciskiem myszy zmienną, a następnie kliknij pozycję **Przypnij do źródła**.  
  
     Przypięty etykietki danych jest zamykany po zakończeniu sesji debugowania.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Aby odpiąć etykietki danych i uczynić go swobodnym  
  
- W przypiętej etykietki danych kliknij ikonę **Odepnij ze źródła** .  
  
     Ikona pinezki zmieni się na przypiętą pozycję. Etykietki danych teraz przekracza wszystkie otwarte okna. Szybująca etykietki danych jest zamykana po zakończeniu sesji debugowania.  
  
### <a name="to-repin-a-floating-datatip"></a>Aby przypiąć zmiennoprzecinkową etykietki danych  
  
- W etykietki danych kliknij ikonę pinezki.  
  
     Ikona pinezki zmieni się na przypiętą pozycję. Jeśli etykietki danych znajduje się poza oknem źródłowym, ikona pinezki jest wyłączona, a etykietki danych nie może zostać przypięty.  
  
### <a name="to-close-a-datatip"></a>Aby zamknąć etykietki danych  
  
- Umieść wskaźnik myszy nad etykietki danych, a następnie kliknij ikonę **zamknięcia** .  
  
### <a name="to-close-all-datatips"></a>Aby zamknąć wszystkie etykietki danych  
  
- W menu **debugowanie** kliknij **Wyczyść wszystkie etykietki**danych.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Aby zamknąć wszystkie etykietki danych dla określonego pliku  
  
- W menu **debugowanie** kliknij **Wyczyść wszystkie etykietki danych przypięte do** *pliku*.  
  
## <a name="expanding-and-editing-information"></a>Rozwijanie i edytowanie informacji  
 Możesz użyć etykietek danych, aby rozwinąć tablicę, strukturę lub obiekt, aby wyświetlić jego elementy członkowskie. Możesz również edytować wartość zmiennej z etykietki danych.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Aby rozwinąć zmienną, aby zobaczyć jej elementy  
  
- W etykietki danych, umieść wskaźnik myszy nad **+** znakiem, który znajduje się przed nazwą zmiennej.  
  
     Zmienna rozwija się, aby pokazać jej elementy w formie drzewa.  
  
     Gdy zmienna jest rozwinięta, możesz użyć klawiszy strzałek na klawiaturze, aby przejść w górę i w dół. Alternatywnie możesz użyć myszy.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Aby edytować wartość zmiennej przy użyciu etykietki danych  
  
1. W etykietki danych kliknij wartość. Ta wartość jest wyłączona w przypadku wartości tylko do odczytu.  
  
2. Wpisz nową wartość i naciśnij klawisz ENTER.  
  
## <a name="making-a-datatip-transparent"></a>Etykietki danych przezroczysty  
 Jeśli chcesz zobaczyć kod, który znajduje się za etykietki danych, możesz sprawić, że etykietki danych jest tymczasowo przezroczysty. Nie ma to zastosowania do etykietek danych, które są przypięte lub przestawne.  
  
#### <a name="to-make-a-datatip-transparent"></a>Aby etykietki danych przezroczysty  
  
- W etykietki danych naciśnij klawisz CTRL.  
  
     Etykietki danych pozostanie przezroczyste, o ile przytrzymasz wciśnięty klawisz CTRL.  
  
## <a name="visualizing-complex-data-types"></a>Wizualizacja złożonych typów danych  
 Jeśli obok nazwy zmiennej w etykietki danych pojawia się ikona lupy, dla zmiennych tego typu danych są dostępne co najmniej jeden [niestandardowy wizualizator](../debugger/create-custom-visualizers-of-data.md) . Możesz użyć wizualizatora, aby wyświetlić informacje w bardziej zrozumiały, zwykle graficzny sposób.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Aby wyświetlić zawartość zmiennej przy użyciu wizualizatora  
  
- Kliknij ikonę lupy, aby wybrać domyślny wizualizator dla typu danych.  
  
     -lub-  
  
     Kliknij strzałkę podręczną obok wizualizatora, aby wybrać z listy odpowiednich wizualizatorów dla typu danych.  
  
     Wizualizator wyświetla informacje.  
  
## <a name="adding-information-to-a-watch-window"></a>Dodawanie informacji do okna czujki  
 Jeśli chcesz kontynuować obserwację zmiennej, możesz dodać zmienną do okna **czujki** z etykietki danych.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Aby dodać zmienną do okno wyrażeń kontrolnych  
  
- Kliknij prawym przyciskiem myszy etykietki danych, a następnie kliknij przycisk **Dodaj czujkę**.  
  
     Zmienna jest dodawana do okna **czujka** . Jeśli używasz wersji, która obsługuje wiele okien **czujki** , zmienna jest dodawana do **czujki 1.**  
  
## <a name="importing-and-exporting-datatips"></a>Importowanie i eksportowanie etykietek danych  
 Możesz eksportować etykietki danych do pliku XML, który może być współużytkowany przez współpracownika lub edytowany przy użyciu edytora tekstu.  
  
#### <a name="to-export-datatips"></a>Aby wyeksportować etykietki danych  
  
1. W menu Debugowanie kliknij polecenie **Eksportuj etykietki**danych.  
  
     Zostanie wyświetlone okno dialogowe **Eksportuj etykietki** danych.  
  
2. Użyj standardowych technik plików, aby przejść do lokalizacji, w której chcesz zapisać plik XML, wpisz nazwę pliku w polu **Nazwa pliku** , a następnie kliknij przycisk **OK**.  
  
#### <a name="to-import-datatips"></a>Aby zaimportować etykietki danych  
  
1. W menu Debugowanie kliknij polecenie **Importuj etykietki**danych.  
  
     Zostanie wyświetlone okno dialogowe **Importuj etykietki** danych.  
  
2. Użyj okna dialogowego, aby znaleźć plik XML, który chcesz otworzyć, a następnie kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Instrukcje: korzystanie z okna dialogowego QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Tworzenie wizualizacji niestandardowych](../debugger/create-custom-visualizers-of-data.md)   
 [Instrukcje: zmiana formatu liczbowego okien debugera](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)

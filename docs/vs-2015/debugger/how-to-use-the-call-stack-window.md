---
title: 'Instrukcje: Korzystanie z okna stosu wywołań | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 993c1380a37b0fedad07427e65fda0a6a80a73f2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756017"
---
# <a name="how-to-use-the-call-stack-window"></a>Instrukcje: Korzystanie z okna stosu wywołań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą **stos wywołań** okna, można wyświetlić wywołania funkcji lub procedur, które obecnie znajdują się w stosie.  
  
 **Stos wywołań** okna wyświetla nazwę każdej funkcji i języka programowania, który jest zapisywany w. Nazwy funkcji lub procedury mogą towarzyszyć informacje opcjonalne, takie jak nazwa modułu, numer wiersza oraz nazwy parametrów, typy i wartości. Wyświetlanie tych informacji opcjonalnych można włączyć lub wyłączyć.  
  
 Żółta strzałka identyfikuje ramkę stosu, w którym aktualnie znajduje się wskaźnik wykonania. Domyślnie jest to ramki, w której informacje pojawią się w źródle, **dezasemblacji**, **lokalne**, **Obejrzyj**, i **Autos** systemu windows. Jeśli chcesz zmienić kontekst do innej ramki na stosie, możesz to zrobić **stos wywołań** okna.  
  
 Jeżeli symbole debugowania nie są dostępne dla części stosu wywołań, **stos wywołań** okna może nie móc wyświetlić poprawnych informacji w tej części stosu wywołań. Pojawia się następujący zapis:  
  
 [Poniższe ramki mogą być niepoprawne i/lub brakujące, nie załadowano symboli dla name.dll]  
  
 W kodzie zarządzanym domyślnie. **stos wywołań** okna ukrywa informacje dla kodu innych użytkowników. Zamiast informacji ukrytych pojawia się następujący zapis:  
  
 **[\<External Code>]**  
  
 Kod niezwiązany z użytkownikiem jest każdy kod, który nie jest "Moim kodem" można wybrać, aby wyświetlić informacje stosu wywołań dla kodu niepochodzącego od użytkownika za pomocą menu skrótów.  
  
 Za pomocą menu skrótów, można wybrać, czy wyświetlane są wywołania między wątkami.  
  
> [!NOTE]
>  Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz pozycję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Aby wyświetlić okno stosu wywołań w trybie przerwania lub w trybie uruchamiania  
  
-   Na **debugowania** menu, wybierz opcję **Windows** a następnie kliknij przycisk **stos wywołań**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Aby zmienić wyświetlane informacje opcjonalne  
  
-   Kliknij prawym przyciskiem myszy **stos wywołań** okna i zestawu lub wyczyść **Pokaż \<**  _informacje, które mają_ **>**.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Aby wyświetlić ramki kodu niepochodzącego od użytkownika w oknie stosu wywołań  
  
-   Kliknij prawym przyciskiem myszy **stos wywołań** okna, a następnie wybierz pozycję **Pokaż kod zewnętrzny**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Aby przełączyć się do innej ramki stosu  
  
1.  W **stos wywołań** okna, kliknij prawym przyciskiem myszy ramkę, której kod i dane, które chcesz wyświetlić.  
  
2.  Wybierz **Przełącz do ramki**.  
  
     Zielona strzałka z zakręconym ogonkiem pojawia się obok wybranej przez użytkownika ramki. Wskaźnik wykonania pozostaje w pierwotnej ramce, która nadal jest oznaczona żółtą strzałką. Jeśli wybierzesz **kroku** lub **Kontynuuj** z **debugowania** menu, wykonywanie będzie kontynuowane w pierwotnej ramce, nie ramce wybranej.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>Aby wyświetlić wywołania do lub z innego wątku  
  
-   Kliknij prawym przyciskiem myszy **stos wywołań** okna, a następnie wybierz pozycję **obejmują wywołania do / z innych wątków**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Aby wyświetlić kod źródłowy dla funkcji na stosie wywołań  
  
-   W **stos wywołań** okna, kliknij prawym przyciskiem myszy funkcję, której kod źródłowy chcesz wyświetlić i wybierz **przejdź do kodu źródłowego**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Aby wizualnie śledzić stos wywołań  
  
1.  W **stos wywołań** okna, otwórz menu skrótów. Wybierz **Pokaż stos wywołań na mapie kodu**. (Klawiatura: **CTRL** + **SHIFT** + **`**)  
  
     Zobacz [metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Aby wyświetlić kod dezasemblacji dla funkcji na stosie wywołań  
  
-   W **stos wywołań** okna, kliknij prawym przyciskiem myszy funkcję, której kod demnotażu chcesz wyświetlić i wybierz **przejdź do demontażu**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Aby uruchomić określoną funkcję z okna stosu wywołań  
  
-  W **stos wywołań** okna, wybierz funkcję, kliknij prawym przyciskiem myszy i wybierz **Uruchom do kursora**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Aby ustawić punkt przerwania w punkcie Zakończ wywołania funkcji  
  
-   Zobacz [Ustaw punkt przerwania w funkcji stosu wywołań](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Aby załadować symbole dla modułu  
  
-   W **stos wywołań** okna, kliknij prawym przyciskiem myszy ramkę, która zawiera moduł, do którego symbole chcesz załadować ponownie i wybierz **załadować symbole**.  
  
## <a name="loading-symbols"></a>Ładowanie symboli  
 W **stos wywołań** okna, możesz załadować symbole debugowania dla kodu, który nie ma obecnie załadowanych symboli. Te symbole mogą być .NET Framework lub symbole systemu, które zostały pobrane z serwerów symboli publicznych firmy Microsoft lub symbolami w ścieżce symboli na komputerze, na którym wykonujesz debugowanie.  
  
 Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>Aby załadować symbole  
  
1.  W **stos wywołań** okna, kliknij prawym przyciskiem myszy ramkę, dla której symbole nie są ładowane. Ramki będą wyszarzone.  
  
2.  Wskaż **Załaduj symbole z** a następnie kliknij przycisk **serwery symboli firmy Microsoft** lub **ścieżki symboli**.  
  
#### <a name="to-set-the-symbol-path"></a>Aby ustawić ścieżkę symboli  
  
1.  W **stos wywołań** oknie Wybierz **ustawienia symboli** z menu skrótów.  
  
     **Opcje** zostanie otwarte okno dialogowe i **symbole** zostanie wyświetlona strona.  
  
2.  Kliknij przycisk **ustawienia symboli**.  
  
3.  W **opcje** okna dialogowego kliknij ikonę folderu.  
  
     W **symboli (.pdb) lokalizacji** polu, pojawi się kursor.  
  
4.  Wpisz nazwę ścieżki katalogu do lokalizacji symbolu na komputerze, na którym wykonujesz debugowanie. Dla debugowania lokalnego to jest komputer lokalny. W przypadku debugowania zdalnego jest komputer zdalny.  
  
5.  Kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Kod mieszany i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Instrukcje: Zmień Format numeryczny debuger Windows](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)

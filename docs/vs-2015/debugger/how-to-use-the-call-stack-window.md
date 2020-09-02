---
title: 'Instrukcje: korzystanie z okna stosu wywołań | Microsoft Docs'
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
ms.openlocfilehash: 84c0bfead1633da13b4284cad04ace674045b057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697476"
---
# <a name="how-to-use-the-call-stack-window"></a>Porady: korzystanie z okna stosu wywołań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą okna **stosu wywołań** można wyświetlić wywołania funkcji lub procedur, które są aktualnie na stosie.  
  
 W oknie **stos wywołań** zostanie wyświetlona nazwa każdej funkcji i języka programowania, w którym jest zapisywana. Nazwy funkcji lub procedury mogą towarzyszyć informacje opcjonalne, takie jak nazwa modułu, numer wiersza i nazwy parametrów, typy i wartości. Te informacje opcjonalne można włączać lub wyłączać.  
  
 Żółta strzałka określa ramkę stosu, w której znajduje się wskaźnik wykonania. Domyślnie jest to ramka, której informacje pojawiają się w oknach źródło, **demontaż**, **lokalne**, **czujka**i **Autowypełnianie** . Jeśli chcesz zmienić kontekst na inną ramkę na stosie, możesz to zrobić w oknie **stosu wywołań** .  
  
 Gdy symbole debugowania nie są dostępne dla części stosu wywołań, okno **stosu wywołań** może nie być w stanie wyświetlić poprawnych informacji dla tej części stosu wywołań. Zostanie wyświetlony następujący zapis:  
  
 [Poniższe ramki mogą być niepoprawne i/lub brakujące, nie załadowano symboli dla name.dll]  
  
 Domyślnie w kodzie zarządzanym. okno **stos wywołań** ukrywa informacje dotyczące kodu niezwiązanego z użytkownikiem. Zamiast ukrytych informacji pojawia się następujący zapis:  
  
 **[\<External Code>]**  
  
 Kod niebędący użytkownikiem to dowolny kod, który nie jest "My Code" można wybrać, aby wyświetlić informacje stosu wywołań dla kodu niepochodzącego od użytkownika przy użyciu menu skrótów.  
  
 Za pomocą menu skrótów, można wybrać, czy mają być wyświetlane wywołania między wątkami.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz pozycję **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Aby wyświetlić okno stosu wywołań w trybie przerwania lub w trybie uruchamiania  
  
- W menu **debugowanie** wybierz pozycję **Windows** , a następnie kliknij pozycję **stos wywołań**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Aby zmienić wyświetlane informacje opcjonalne  
  
- Kliknij prawym przyciskiem myszy okno **stos wywołań** i ustaw lub wyczyść opcję **Pokaż \<**_the information that you want_**> **.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Aby wyświetlić ramki kodu inne niż użytkownika w oknie stosu wywołań  
  
- Kliknij prawym przyciskiem myszy okno **stos wywołań** i wybierz polecenie **Pokaż kod zewnętrzny**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Aby przełączyć się do innej ramki stosu  
  
1. W oknie **stos wywołań** kliknij prawym przyciskiem myszy ramkę, której kod i dane chcesz wyświetlić.  
  
2. Wybierz pozycję **Przełącz do ramki**.  
  
     Zielona strzałka z ogonem klamrowym pojawia się obok zaznaczonej ramki. Wskaźnik wykonywania pozostaje w oryginalnej ramce, która nadal jest oznaczona żółtą strzałką. Jeśli wybierzesz pozycję **krok** lub **Kontynuuj** z menu **Debuguj** , wykonywanie będzie kontynuowane w pierwotnej ramce, a nie w wybranej ramce.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>Aby wyświetlić wywołania do lub z innego wątku  
  
- Kliknij prawym przyciskiem myszy okno **stos wywołań** i wybierz pozycję **Dołącz wywołania do/z innych wątków**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Aby wyświetlić kod źródłowy funkcji na stosie wywołań  
  
- W oknie **stos wywołań** kliknij prawym przyciskiem myszy funkcję, której kod źródłowy chcesz zobaczyć, i wybierz polecenie **Przejdź do kodu źródłowego**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Aby wizualnie śledzić stos wywołań  
  
1. W oknie **stos wywołań** Otwórz menu skrótów. Wybierz pozycję **Pokaż stos wywołań na mapie kodu**. (Klawiatura: **Ctrl**  +  **SHIFT**  +  **`** )  
  
     Zobacz [metody mapowania na stosie wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Aby wyświetlić kod demontażu dla funkcji na stosie wywołań  
  
- W oknie **stos wywołań** kliknij prawym przyciskiem myszy funkcję, której kod demontażu chcesz zobaczyć, i wybierz polecenie **Przejdź do demontażu**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Aby uruchomić konkretną funkcję z okna stosu wywołań  
  
- W oknie **stos wywołań** zaznacz funkcję, kliknij prawym przyciskiem myszy i wybierz polecenie **Uruchom do kursora**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Aby ustawić punkt przerwania w punkcie wyjścia wywołania funkcji  
  
- Zobacz [Ustawianie punktu przerwania w funkcji stosu wywołań](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Aby załadować symbole dla modułu  
  
- W oknie **stos wywołań** kliknij prawym przyciskiem myszy ramkę, która zawiera moduł, którego symbole chcesz załadować ponownie i wybierz pozycję **Załaduj symbole**.  
  
## <a name="loading-symbols"></a>Ładowanie symboli  
 W oknie **stos wywołań** można załadować symbole debugowania dla kodu, który nie ma obecnie załadowanych symboli. Te symbole mogą być .NET Framework lub symbole systemowe pobrane z publicznych serwerów symboli Microsoft lub symboli w ścieżce symboli na komputerze, który jest debugowany.  
  
 Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>Aby załadować symbole  
  
1. W oknie **stos wywołań** kliknij prawym przyciskiem myszy ramkę, dla której symbole nie są ładowane. Ramka będzie wyszarzona.  
  
2. Wskaż **Załaduj symbole z** , a następnie kliknij pozycję **serwery symboli Microsoft** lub **ścieżka symboli**.  
  
#### <a name="to-set-the-symbol-path"></a>Aby ustawić ścieżkę symbolu  
  
1. W oknie **stos wywołań** wybierz pozycję **Ustawienia symboli** z menu skrótów.  
  
     Zostanie otwarte okno dialogowe **Opcje** i zostanie wyświetlona strona **symbole** .  
  
2. Kliknij pozycję **Ustawienia symboli**.  
  
3. W oknie dialogowym **Opcje** kliknij ikonę folderu.  
  
     W polu **lokalizacje pliku symboli (. pdb)** pojawia się kursor.  
  
4. Wpisz nazwę ścieżki katalogu do lokalizacji symboli na komputerze, który jest debugowany. Na potrzeby debugowania lokalnego jest to komputer lokalny. Do zdalnego debugowania jest to komputer zdalny.  
  
5. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Opcje** .  
  
## <a name="see-also"></a>Zobacz też  
 [Kod mieszany i brakujące informacje w oknie stosu wywołań](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Instrukcje: zmiana formatu liczbowego okien debugera](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)

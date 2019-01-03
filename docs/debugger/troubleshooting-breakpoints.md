---
title: Rozwiązywanie problemów z punktów przerwania w debugerze | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2afbff14be944e17a26df09d041d9267ac5cb87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989912"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Rozwiązywanie problemów z punktów przerwania w debugerze programu Visual Studio

## <a name="breakpoint-warnings"></a>Ostrzeżenia punktu przerwania

Podczas debugowania, punkt przerwania ma dwa możliwe stany wizualne: stałe czerwone kółko i puste (biały wypełnione) koło. Debuger jest w stanie pomyślnie ustawiono punkt przerwania w procesie docelowym, pozostanie stałe czerwone kółko. Jeśli punkt przerwania jest pusty okrąg, punkt przerwania jest wyłączony lub ostrzeżenia podczas próby ustawienia punktu przerwania. Aby określić różnica, umieść kursor nad punkt przerwania i sprawdzić, czy jest ostrzeżenie.

Następujące dwie sekcje opisują widoczne ostrzeżenia i jak je rozwiązać. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Symboli nie zostały załadowane dla tego dokumentu" 

Przejdź do **modułów** okna (**debugowania** > **Windows** > **modułów**) i sprawdź, czy jest modułu załadowane.  
* Jeśli Twoje moduł jest załadowany, sprawdź **stan symboli** kolumny, aby zobaczyć, czy załadowano symbole. 
  * Jeśli nie załadowano symboli, sprawdź stan symboli do zdiagnozowania problemu. Z menu kontekstowego w module w **modułów** okna, kliknij przycisk **informacje o ładowaniu symboli...**  aby zobaczyć, gdzie debuger oglądałem się i spróbuj załadować symbole. Aby uzyskać więcej informacji na temat ładowania symboli, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Czy symbole są załadowane, PDB nie zawiera informacji o plikach źródłowych. Poniżej przedstawiono kilka możliwych przyczyn: 
    * Niedawno dodano plików źródłowych, upewnij się, że aktualna wersja modułu jest ładowany.  
    * Istnieje możliwość tworzenia PDB przy użyciu **/pdbstripped** — opcja konsolidatora. PDB nie zawierają informacji o pliku źródłowym. Upewnij się, że pracujesz z pełnego pliku PDB, a nie informacje PDB zostały usunięte.  
    * Plik PDB częściowo jest uszkodzony. Usuń ten plik i wykonać czystą kompilację modułu w celu rozwiązania problemu. 

* Jeśli modułu nie jest załadowany, sprawdź następujące polecenie, aby znaleźć przyczynę: 
  * Upewnij się, debugowany proces prawo. 
  * Sprawdź, czy debugujesz właściwego rodzaju kodu. Możesz dowiedzieć się jakiego typu kodu, Debuger jest skonfigurowany do debugowania w **procesy** okna (**debugowania** > **Windows**  >  **Procesy**). Na przykład, jeśli próbujesz debugowanie kodu C#, upewnij się, że debuger jest skonfigurowany dla odpowiedniego typu .NET Framework (na przykład zarządzane (v4\*) i zarządzane (v2\*/v3\*) i zarządzane (CoreCLR)). 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… Bieżący kod źródłowy różni się od wersji skompilowanej w..." 

Jeśli plik źródłowy został zmieniony i źródło nie jest już zgodny z kodu, który jest debugowany, debuger nie ustawi punktów przerwania w kodzie domyślnie. Zwykle ten problem ma to miejsce po zmodyfikowaniu pliku źródłowego, ale kod źródłowy nie został odbudowany. Aby rozwiązać ten problem, ponownie skompilować projekt. Jeśli system kompilacji podejrzewać, że projekt jest już aktualne, nawet jeśli nie jest, możesz wymusić system projektu, aby odbudować albo zapisując pliku źródłowego lub przez czyszczenie projektu dane wyjściowe przed kompilacją kompilacji. 

W rzadkich scenariuszach można debugować bez odpowiedniego kodu źródłowego. Debugowanie bez pasującego znaku kod źródłowy potencjalnego klienta do mylące debugowania środowiska, więc upewnić się, to sposób chcesz kontynuować.  

Aby wyłączyć te kontrole bezpieczeństwa, wykonaj jedną z następujących czynności: 
* Aby zmodyfikować pojedynczy punkt przerwania, wskaźnik myszy na ikonie punkt przerwania w edytorze, a następnie kliknij ikonę ustawienia (koło zębate). Okno podglądu jest dodawany do edytora. W górnej części okna podglądu jest hiperłącze, które wskazuje lokalizację punktu przerwania. Kliknij hiperlink do Zezwalaj na modyfikowanie lokalizacji punktu przerwania i sprawdź **Zezwalaj kod źródłowy różnił się od oryginału**.
* Aby zmodyfikować to ustawienie w przypadku wszystkich punktów przerwania, przejdź do **debugowania** > **opcje i ustawienia**. Na **debugowanie/ogólne** strony, wyczyść **wymaga plików źródłowych, które dokładnie dopasować oryginalną wersję** opcji. Upewnij się ponownie włączyć tę opcję, po zakończeniu debugowania. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Punkt przerwania została ustawiona pomyślnie (bez ostrzeżenia), ale nie został osiągnięty 

Ta sekcja zawiera informacje, aby rozwiązać problemy, gdy debuger nie są wyświetlane wszelkie ostrzeżenia — punkt przerwania jest stałe czerwone kółko podczas aktywnego debugowania, ale nie jest trafienia punktu przerwania. 

Oto kilka rzeczy, aby sprawdzić: 
1. Jeśli kod jest wykonywany w procesie więcej niż jeden lub więcej niż jednym komputerze, upewnij się, czy debugujesz prawo proces lub komputer.  
2. Upewnij się, że Twój kod jest uruchomiony. Aby sprawdzić, czy kod działa, dodaj wywołanie `System.Diagnostics.Debugger.Break` (C# /VB) lub `__debugbreak` (C++) do wiersza kodu, w której chcesz ustawić punkt przerwania, a następnie ponownego skompilowania projektu. 
3. Jeśli debugujesz zoptymalizowany kod, upewnij się, że funkcja, w którym ustawiono punkt przerwania nie jest wbudowana w innej funkcji. `Debugger.Break` Test opisany w poprzednim wyboru może pracować do przetestowania także ten problem. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Po usunięciu punktu przerwania, ale można kontynuować trafień je, gdy I ponownie Rozpocznij debugowanie 

Usunięcie punktu przerwania podczas debugowania może trafiony punkt przerwania ponownie przy następnym uruchomieniu debugowania. Aby zatrzymać, naciśnięcie tego punktu przerwania, sprawdź, czy wszystkie wystąpienia punktu przerwania są usuwane z **punktów przerwania** okna.  

---
title: Przy użyciu plików zrzutu w debugerze | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b392cf5eddaab877af56ee952074cff646e10a59
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693454"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Pliki zrzutu debugera programu Visual Studio

<a name="BKMK_What_is_a_dump_file_"></a> A *plik zrzutu* jest migawką, który przedstawia proces, który był wykonywany i modułów, które zostały załadowane dla aplikacji w punkcie w czasie. Zrzutu z informacjami o stercie także migawkę pamięci aplikacji w tym momencie.

Otwieranie pliku zrzutu ze stertą w programie Visual Studio jest podobny do zatrzymywanie w punkcie przerwania w trakcie sesji debugowania. Mimo że nie można kontynuować wykonywania, można sprawdzić stosy, wątki i wartości zmiennych aplikacji w momencie zrzutu.

Zrzuty są głównie używane do debugowania problemów z komputerów, które deweloperzy nie mają dostępu do. Można użyć pliku zrzutu z komputera klienta, gdy nie można odtworzyć awarii lub zawieszeniu na własnym komputerze. Testerom tworzyć również zrzuty, aby zapisać awarii lub zawieszeniu dane mają być używane do dalszego testowania.

Debuger programu Visual Studio może zapisywać pliki zrzutu dla kodu zarządzanego lub natywnego. Można go debugować pliki zrzutu utworzone przez program Visual Studio lub przez inne aplikacje, które zapisują pliki w *minizrzutu* formatu.

##  <a name="BKMK_Requirements_and_limitations"></a> Wymagania i ograniczenia

-   Aby debugować pliki zrzutu z komputerów 64-bitowych, Visual Studio musi działać na komputerze 64-bitowym.

-   Program Visual Studio umożliwia debugowanie plików zrzutu macierzystych aplikacji z urządzeń ARM. Mogą ponadto debugować zrzutów zarządzanych aplikacji z urządzeń ARM, ale tylko w macierzystym debugerze.

-   Aby debugować [trybu jądra](/windows-hardware/drivers/debugger/kernel-mode-dump-files) pliki zrzutu, lub użyj [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) Debugowanie rozszerzeń w programie Visual Studio, Pobierz narzędzia do debugowania dla Windows w [Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

-   Visual Studio nie może debugować plików zrzutu zapisanych w starszym formatem, [zrzut trybu użytkownika pełnego](/windows/desktop/wer/collecting-user-mode-dumps) formatu. Zrzut trybu użytkownika pełnego nie jest taka sama jak zrzut ze stertą.

-   Debugowanie plików zrzutu zoptymalizowanego kodu może być mylące. Na przykład Wbudowywanie funkcji przez kompilator może spowodować nieoczekiwane stosy wywołań, a inne optymalizacje mogą zmienić okres istnienia zmiennych.

##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Pliki zrzutu ze stertami lub bez

Pliki zrzutu może lub nie może mieć informacje o stercie.

-   **Pliki zrzutu ze stertami** zawierają migawkę pamięci aplikacji, w tym wartości zmiennych, w momencie zrzutu. Program Visual Studio zapisuje także pliki binarne załadowanych modułów macierzystych w pliku zrzutu ze stertą, co znacznie ułatwia debugowanie. Program Visual Studio załadować symbole z pliku zrzutu ze stertą, nawet wtedy, gdy nie można odnaleźć binarnych aplikacji.

-   **Zrzuć pliki bez stert** są znacznie mniejsze niż przy użyciu sterty, ale debuger musi załadować pliki binarne aplikacji, aby znaleźć informacje o symbolach. Załadowane dane binarne muszą dokładnie odpowiadać te działania podczas tworzenia zrzutu. Pliki zrzutu bez stert zapisać wartości tylko w zmiennych stosu.

##  <a name="BKMK_Create_a_dump_file"></a> Tworzenie pliku zrzutu

Podczas debugowania procesu w programie Visual Studio, można zapisać zrzutu po zatrzymaniu debugera w punkt przerwania lub wyjątku.

Za pomocą [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) włączone, można dołączyć debuger programu Visual Studio do awarii procesu poza programem Visual Studio i następnie zapisać plik zrzutu z debugera. Zobacz [dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Aby zapisać plik zrzutu:**

1. Po zatrzymaniu w błąd lub punkt przerwania podczas debugowania, wybierz **debugowania** > **Zapisz zrzut jako**.

1. W **Zapisz zrzut jako** dialogowego **Zapisz jako typ**, wybierz opcję **minizrzutu** lub **minizrzutu ze stertą** (ustawienie domyślne).

1. Przejdź do ścieżki i wybierz nazwę dla pliku zrzutu, a następnie wybierz **Zapisz**.

>[!NOTE]
>Można tworzyć pliki zrzutu za pomocą dowolnego programu, który obsługuje format minizrzutu Windows. Na przykład **Procdump** narzędzie wiersza polecenia z [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) można tworzyć pliki zrzutu awaryjnego procesów na podstawie wyzwalaczy lub na żądanie. Zobacz [wymagania i ograniczenia](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) uzyskać informacji na temat korzystania z innych narzędzi do tworzenia plików zrzutu.

##  <a name="BKMK_Open_a_dump_file"></a> Otwieranie pliku zrzutu

1. W programie Visual Studio, wybierz **pliku** > **Otwórz** > **pliku**.

1. W **Otwórz plik** okno dialogowe Znajdź i zaznacz plik zrzutu. Będzie zazwyczaj miał *.dmp* rozszerzenia. Wybierz **OK**.

   **Podsumowanie pliku minizrzutu** okno przedstawia podsumowanie i moduł informacje dotyczące pliku zrzutu i akcje można wykonać.

   ![Strona podsumowania minizrzutu](../debugger/media/dbg_dump_summarypage.png "minizrzutu strona podsumowania")

1. W obszarze **akcje**:
   - Aby ustawić lokalizacje ładowania symboli, wybierz **Ustaw ścieżki symboli**.
   - Aby rozpocząć debugowanie, wybierz **debugowanie zarządzane tylko za pomocą**, **Debuguj tylko kod natywny**, **debugowanie za pomocą mieszanego**, lub **debugowanie za pomocą pamięć zarządzaną**.

##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Znajdowanie .exe, .pdb i plików źródłowych

Aby użyć funkcji w pliku zrzutu do debugowania programu Visual Studio wymaga:

- *.Exe* zrzut został utworzony dla pliku, a pozostałe pliki binarne (biblioteki DLL itd.) używane w procesie zrzutu.
- Symbol (*.pdb*) pliki *.exe* i innych plików binarnych.
- *.Exe* i *.pdb* pliki, które dokładnie odpowiadać wersji i kompilacji plików podczas zrzutu tworzenia.
- Pliki źródłowe dla odpowiednich modułów. Możesz użyć deasemblacji modułów, jeśli nie możesz znaleźć plików źródłowych.

Jeśli zrzut zawiera dane sterty, Visual Studio może poradzić sobie z brakującymi plikami binarnymi dla niektórych modułów, ale musi on mieć pliki binarne dla wystarczającej liczby modułów generować prawidłowe stosy wywołań.

### <a name="search-paths-for-exe-files"></a>Przeszukuj ścieżki pod kątem plików .exe

Program Visual Studio automatycznie przeszukuje następujące lokalizacje *.exe* plików, które nie są uwzględnione w pliku zrzutu:

1. Folder, który zawiera plik zrzutu.
2. Ścieżka modułu określa plik zrzutu, który jest ścieżka modułu na komputerze, w którym zbierane zrzutu.
3. Ścieżki symboli określone w **narzędzia** (lub **debugowania**) > **opcje** > **debugowanie**  >  **Symbole**. Możesz również otworzyć **symbole** strony **akcje** okienku **Podsumowanie pliku zrzutu** okna. Na tej stronie możesz dodać więcej lokalizacji do przeszukania.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Korzystanie ze stron nie znaleziono pliku binarnego, Brak symboli lub nie znaleziono źródła

Jeśli program Visual Studio nie może znaleźć plików wymaganych do debugowania modułu w zrzucie, pokazuje **nie znaleziono pliku binarnego**, **nie znaleziono symboli**, lub **nie znaleziono źródła** strony. Strony te zawierają szczegółowe informacje o przyczynie problemu i zapewniają łącza akcji, które mogą pomóc Ci znaleźć pliki. Zobacz [określanie plików symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Zobacz także

- [Debugowanie Just In Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Określanie plików symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)
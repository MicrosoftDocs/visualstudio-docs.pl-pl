---
title: Używanie plików zrzutu w debugerze | Microsoft Docs
description: Plik zrzutu to migawka wykonywanej aplikacji i załadowanych modułów. Rozważ utworzenie pliku zrzutu w sytuacjach, gdy nie masz dostępu debugowania do aplikacji.
ms.custom: SEO-VS-2020, seodec18
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 993b5f61d8517d5638cb785fa2d79b47f80d1caf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940556"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Zrzuć pliki w debugerze programu Visual Studio

<a name="BKMK_What_is_a_dump_file_"></a>*Plik zrzutu* to migawka pokazująca wykonywany proces i moduły, które zostały załadowane dla aplikacji w danym momencie. Zrzut z informacjami o stercie zawiera również migawkę pamięci aplikacji w tym momencie.

Otwieranie pliku zrzutu ze stertą w programie Visual Studio jest czymś podobnym do zatrzymywania w punkcie przerwania w sesji debugowania. Chociaż nie możesz kontynuować wykonywania, możesz przeanalizować stosy, wątki i wartości zmiennych aplikacji w momencie zrzutu.

Zrzuty są najczęściej używane do debugowania problemów z maszyn, do których deweloperzy nie mają dostępu. Można użyć pliku zrzutu z komputera klienta, gdy nie można odtworzyć programu awaryjnego lub nieodpowiadającego na komputerze. Testerzy mogą również tworzyć zrzuty, aby zaoszczędzić dane dotyczące nieoczekiwanych lub nieodpowiadających programów do użycia w celu przeprowadzenia dalszych testów.

Debuger programu Visual Studio może zapisywać pliki zrzutu dla kodu zarządzanego lub natywnego. Może debugować pliki zrzutu utworzone przez program Visual Studio lub przez inne aplikacje, które zapisują pliki w formacie *minizrzutu* .

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Wymagania i ograniczenia

- Aby debugować pliki zrzutu z maszyn 64-bitowych, program Visual Studio musi działać na komputerze 64-bitowym.

- Program Visual Studio umożliwia debugowanie plików zrzutu macierzystych aplikacji z urządzeń ARM. Może również debugować zrzuty zarządzanych aplikacji z urządzeń ARM, ale tylko w debugerze natywnym.

- Aby debugować pliki zrzutu w [trybie jądra](/windows-hardware/drivers/debugger/kernel-mode-dump-files) lub użyć rozszerzenia debugowania [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) w programie Visual Studio, Pobierz narzędzia debugowania dla systemu Windows z [zestawu Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

- Program Visual Studio nie może debugować plików zrzutu zapisanych w starszym formacie [pełnego zrzutu trybu użytkownika](/windows/desktop/wer/collecting-user-mode-dumps) . Pełny zrzut trybu użytkownika nie jest taki sam jak zrzut ze stertą.

- Debugowanie plików zrzutu zoptymalizowanego kodu może być mylące. Na przykład kompilator wykreślania funkcji może spowodować nieoczekiwane stosy wywołań, a inne optymalizacje mogą zmienić okres istnienia zmiennych.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Zrzuć pliki ze stertami lub bez nich

Pliki zrzutu mogą lub nie mogą zawierać informacji o stercie.

- **Pliki zrzutu ze stertami** zawierają migawkę pamięci aplikacji, w tym wartości zmiennych, w momencie zrzutu. Program Visual Studio zapisuje także pliki binarne załadowanych modułów macierzystych w pliku zrzutu ze stertą, co może znacznie ułatwić debugowanie. Program Visual Studio może ładować symbole z pliku zrzutu ze stertą, nawet jeśli nie można znaleźć pliku binarnego aplikacji.

- **Pliki zrzutu bez sterty** są znacznie mniejsze niż zrzuty ze stertami, ale debuger musi załadować pliki binarne aplikacji, aby znaleźć informacje o symbolach. Ładowane pliki binarne muszą dokładnie pasować do tych, które są uruchomione podczas tworzenia zrzutu. Pliki zrzutu bez sterty zapisują tylko wartości zmiennych stosu.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Utwórz plik zrzutu

Podczas debugowania procesu w programie Visual Studio, można zapisać zrzut po zatrzymaniu debugera przy użyciu wyjątku lub punktu przerwania.

Dzięki włączeniu [debugowania just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) można dołączyć debuger programu Visual Studio do nieoczekiwanego procesu poza programem Visual Studio, a następnie zapisać plik zrzutu z debugera. Zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Aby zapisać plik zrzutu:**

1. Po zatrzymaniu z powodu błędu lub punktu przerwania podczas debugowania wybierz kolejno opcje **Debuguj**  >  **Zapisz zrzut jako**.

1. W oknie dialogowym **Zapisz zrzut jako** w obszarze **Zapisz jako typ** wybierz pozycję **minizrzutu** lub **minizrzutu ze stertą** (domyślnie).

1. Przejdź do ścieżki i wybierz nazwę pliku zrzutu, a następnie wybierz pozycję **Zapisz**.

>[!NOTE]
>Można tworzyć pliki zrzutu za pomocą dowolnego programu, który obsługuje format minizrzutu systemu Windows. Na przykład narzędzie wiersza polecenia **ProcDump** z [Windows Sysinternals](/sysinternals/) może tworzyć pliki zrzutu awaryjnego procesów na podstawie wyzwalaczy lub na żądanie. Zapoznaj się z [wymaganiami i ograniczeniami](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) dotyczącymi korzystania z innych narzędzi do tworzenia plików zrzutu.

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Otwórz plik zrzutu

1. W programie Visual Studio wybierz pozycję **plik**  >  **Otwórz**  >  **plik**.

1. W oknie dialogowym **Otwórz plik** zlokalizuj i wybierz plik zrzutu. Zazwyczaj ma rozszerzenie *. dmp* . Wybierz przycisk **OK**.

   Okno **podsumowania pliku minizrzutu** zawiera podsumowanie i informacje o module dla pliku zrzutu oraz akcje, które można wykonać.

   ![Strona podsumowania minizrzutu](../debugger/media/dbg_dump_summarypage.png "Strona podsumowania minizrzutu")

1. W obszarze **Akcje**:
   - Aby ustawić lokalizacje ładowania symboli, wybierz opcję **Ustaw ścieżki symboli**.
   - Aby rozpocząć debugowanie, wybierz opcję **Debuguj z opcją tylko zarządzane**, **Debuguj tylko natywny**, **Debuguj z mieszanym** lub **Debuguj z pamięcią zarządzaną**.

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Find. exe,. pdb i pliki źródłowe

Aby korzystać z funkcji pełnego debugowania w pliku zrzutu, program Visual Studio potrzebuje:

- Plik *. exe* , dla którego utworzono zrzut, i inne pliki binarne (biblioteki DLL itp.) używane przez proces zrzutu.
- Pliki symboli (*. pdb*) dla pliku *. exe* i innych plików binarnych.
- Pliki *. exe* i *. pdb* , które dokładnie pasują do wersji i kompilowania plików podczas tworzenia zrzutu.
- Pliki źródłowe odpowiednich modułów. Jeśli nie możesz znaleźć plików źródłowych, możesz użyć odzestawu modułów.

Jeśli zrzut zawiera dane sterty, program Visual Studio może poradzić sobie z brakującymi plikami binarnymi dla niektórych modułów, ale musi mieć pliki binarne dla wystarczającej liczby modułów, aby generować prawidłowe stosy wywołań.

### <a name="search-paths-for-exe-files"></a>Ścieżki wyszukiwania dla plików exe

Program Visual Studio automatycznie przeszukuje te lokalizacje plików *exe* , które nie znajdują się w pliku zrzutu:

1. Folder zawierający plik zrzutu.
2. Ścieżka modułu określa plik zrzutu, który jest ścieżką modułu na komputerze, na którym zebrano zrzut.
3. Ścieżki symboli określone w **Narzędzia** (lub **debugowanie**) > **Opcje**  >  **debugowania**  >  **symbole**. Możesz również otworzyć stronę **symbole** z okienka **Akcje** okna **Podsumowanie pliku zrzutu** . Na tej stronie można dodać więcej lokalizacji do wyszukania.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Nie znaleziono żadnych stron binarnych, bez symboli ani źródeł

Jeśli program Visual Studio nie może znaleźć plików potrzebnych do debugowania modułu w zrzucie, pokazuje **nie znaleziono pliku binarnego**, **nie znaleziono symboli** lub nie znaleziono **źródła** strony. Te strony zawierają szczegółowe informacje o przyczynie problemu i zawierają linki akcji, które mogą pomóc w znalezieniu plików. Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Zobacz też

- [Debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)
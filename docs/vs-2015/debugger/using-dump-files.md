---
title: Korzystanie z plików zrzutów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
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
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a2d6215887512f2e0c1410688b2bc924dc1fe3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387060"
---
# <a name="using-dump-files"></a>Używanie plików zrzutów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki zrzutu ze stertami lub bez nich; tworzenie pliku zrzutu; otwieranie pliku zrzutu; znajdowanie plików binarnych, PDB i pliku źródłowego pliku zrzutu. 
  
## <a name="contents"></a><a name="BKMK_Contents"></a> Contents  
 [Co to jest plik zrzutu?](#BKMK_What_is_a_dump_file_)  
  
 [Pliki zrzutu, z stertami lub bez nich](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Wymagania i ograniczenia](#BKMK_Requirements_and_limitations)  
  
 [Utwórz plik zrzutu](#BKMK_Create_a_dump_file)  
  
 [Otwórz plik zrzutu](#BKMK_Open_a_dump_file)  
  
 [Znajdowanie plików binarnych, pliki symboli (. pdb) i pliki źródłowe](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
## <a name="what-is-a-dump-file"></a><a name="BKMK_What_is_a_dump_file_"></a> Co to jest plik zrzutu?  
 *Plik zrzutu* jest migawką aplikacji w momencie trwania zrzutu. To pokazuje, jaki proces był wykonywany i które moduły zostały załadowane. Jeśli zrzut został zapisany z informacjami o stercie, plik zrzutu zawiera migawkę tego, co było w pamięci aplikacji w tamtym momencie. Otwieranie pliku zrzutu ze stertą w Visual Studio przypomina zatrzymywanie w punkcie przerwania sesji debugowania. Chociaż nie możesz kontynuować wykonywania, możesz przeanalizować stosy, wątki i wartości zmiennych aplikacji dla momentu zrzutu.  
  
 Zrzuty są wykorzystywane głównie do debugowania problemów występujących na komputerach, do których deweloper nie ma dostępu. Na przykład można użyć pliku zrzutu z komputera klienta, gdy nie można odtworzyć programu awarii lub nieodpowiadający na komputerze klienta. Zrzuty są również tworzone przez testerów w celu zapisania danych o awarii lub braku odpowiedzi, aby można było użyć maszyny testowej do większej liczby testów. Debuger programu Visual Studio może zapisywać pliki zrzutu dla kodu zarządzanego lub natywnego. Debuger może załadować pliki zrzutu utworzone przez program Visual Studio lub przez inne programy, które zapisują pliki w formacie *minizrzutu* .  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Pliki zrzutu, z stertami lub bez nich  
 Można tworzyć pliki zrzutu z informacjami o stercie lub bez nich.  
  
- **Pliki zrzutu ze stertami** zawierają migawkę pamięci aplikacji. Obejmuje to wartości zmiennych utworzonych w momencie zrzutu. Jeśli załadujesz plik zrzutu, który został zapisany ze stertą, program Visual Studio można załadować symbole, nawet jeśli nie można odnaleźć pliku binarnego aplikacji. Program Visual Studio zapisuje także pliki binarne załadowanych modułów macierzystych w pliku zrzutu, co znacznie ułatwia debugowanie.  
  
- **Pliki zrzutu bez sterty** są znacznie mniejsze niż zrzuty z informacjami o stercie. Jednak debuger musi załadować pliki binarne aplikacji, aby znaleźć informacje o symbolach. Pliki binarne muszą dokładnie odpowiadać plikom binarnym, które były używane podczas tworzenia zrzutu. Tylko wartości zmiennych stosu są zapisywane w plikach zrzutu bez danych sterty.  
  
  ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Wymagania i ograniczenia  
  
- Debugowanie plików zrzutu zoptymalizowanego kodu może być mylące. Na przykład wbudowywanie funkcji przez kompilator może spowodować nieoczekiwane stosy wywołań, a inne optymalizacje mogą zmienić okres istnienia zmiennych.  
  
- Pliki zrzutu z komputerów 64-bitowych muszą być debugowane na wystąpieniu programu Visual Studio, który jest uruchomiony na komputerze 64-bitowym.  
  
- W wersjach Visual Studio starszych niż VS 2013, zrzutów aplikacji 32-bitowych uruchamianych na komputerach 64-bitowych, które zostały zebrane przez kilka narzędzi (takich jak Menedżer zadań i WinDbg 64-bitowe), nie można otworzyć w programie Visual Studio. Ograniczenie to zostało usunięte w VS 2013.  
  
- Program Visual Studio umożliwia debugowanie plików zrzutu macierzystych aplikacji z urządzeń ARM. Program Visual Studio umożliwia również debugowanie plików zrzutu zarządzanych aplikacji z urządzeń ARM, ale tylko w macierzystym debugerze.  
  
- Aby debugować pliki zrzutu w [trybie jądra](https://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) w Visual Studio 2013, Pobierz [Windows 8.1 wersji narzędzi debugowania dla systemu Windows](https://msdn.microsoft.com/windows/hardware/gg463009). Zobacz [debugowanie jądra w programie Visual Studio](https://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Program Visual Studio nie może debugować plików zrzutu zapisanych w starszym formacie zrzutu znanego jako [pełny zrzut trybu użytkownika](/windows-hardware/drivers/debugger/user-mode-dump-files#full). Należy zauważyć, że pełny zrzut trybu użytkownika to nie to samo, co zrzut ze stertą.  
  
- Aby debugować przy użyciu [SOS.dll (rozszerzenie debugowania SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) w programie Visual Studio, należy zainstalować narzędzia debugowania dla systemu Windows, które jest częścią zestawu Windows Driver Kit (WDK). Zobacz [Windows 8.1 Preview: Pobierz zestawy, bity i narzędzia](https://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Utwórz plik zrzutu  
 Aby utworzyć plik zrzutu z programu Visual Studio:  
  
- Podczas debugowania procesu w Visual Studio, można zapisać plik zrzutu po zatrzymaniu debugera w sytuacji wyjątku lub w punkcie przerwania. Wybierz pozycję **Zapisz zrzut jako**, **Debuguj**. W oknie dialogowym **Zapisz zrzut jako** na liście **Zapisz jako typ** możesz wybrać **minizrzutu** lub **minizrzutu z stertą** (domyślnie).  
  
- Gdy [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) jest włączone, można dołączyć debuger do procesu, który działa poza debugerem, a następnie zapisać plik zrzutu. Zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  Można również tworzyć pliki zrzutu za pomocą dowolnego programu, który obsługuje format minizrzutu systemu Windows. Na przykład narzędzie wiersza polecenia **ProcDump** z programu [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) może tworzyć pliki zrzutu awaryjnego procesów na podstawie wyzwalaczy lub na żądanie. Zobacz [wymagania i ograniczenia](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) w tym temacie, aby uzyskać dodatkowe informacje dotyczące korzystania z innych narzędzi do tworzenia plików zrzutu.  
  
  ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Otwórz plik zrzutu  
  
1. W programie Visual Studio wybierz **plik**, **Otwórz**, **plik**.  
  
2. W oknie dialogowym **Otwórz plik** zlokalizuj i wybierz plik zrzutu. Będzie zazwyczaj miał rozszerzenie .dmp. Następnie wybierz przycisk **OK**.  
  
3. Zostanie wyświetlone okno **Podsumowanie pliku zrzutu** . W tym oknie można wyświetlać informacje podsumowujące debugowanie dla pliku zrzutu, ustawić ścieżkę symboli, rozpocząć debugowanie i skopiować informacje podsumowujące do Schowka.  
  
     ![Strona podsumowania minizrzutu](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4. Aby rozpocząć debugowanie, przejdź do sekcji **Akcje** , a następnie wybierz opcję **Debuguj tylko w trybie natywnym** lub **Debuguj z mieszaniem mieszanym**.  
  
## <a name="find-binaries-symbol-pdb-files-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Znajdowanie plików binarnych, pliki symboli (. pdb) i pliki źródłowe  
 Aby użyć wszystkich funkcji programu Visual Studio do debugowania pliku zrzutu, potrzebny jest dostęp do następujących elementów:  
  
- Plik .exe, dla którego zrobiono zrzut, i inne pliki binarne (biblioteki DLL itd.), które były używane w procesie zrzutu.  
  
   Jeśli debugujesz zrzut z danymi sterty, Visual Studio może poradzić sobie z brakującymi plikami binarnymi dla niektórych modułów, ale musi mieć pliki binarne dla wystarczającej liczby modułów, aby generować prawidłowe stosy wywołań. Program Visual Studio zawiera moduły macierzyste w pliku zrzutu ze stertą.  
  
- Pliki symboli (.pdb) dla pliku .exe i innych plików binarnych.  
  
- Pliki źródłowe dla modułów, które cię interesują.  
  
   Plik wykonywalny i pliki .pdb muszą dokładnie odpowiadać wersji i kompilacji plików używanych podczas tworzenia zrzutu.  
  
   Można debugować z użyciem deasemblacji modułów, jeżeli nie można znaleźć plików źródłowych,  
  
  **Domyślne ścieżki wyszukiwania dla plików wykonywalnych**  
  
  Program Visual Studio automatycznie przeszukuje następujące lokalizacje plików wykonywalnych, które nie są zawarte w pliku zrzutu:  
  
1. Katalog zawierający plik zrzutu.  
  
2. Ścieżka modułu, który jest określony w pliku zrzutu. Jest to ścieżka modułu na komputerze, na który pobrano zrzut.  
  
3. Ścieżki symboli określone na stronie **debugowanie**, **Opcje**, **symbole** okna dialogowego Visual Studio **Tools**, **Opcje** . Do wyszukiwania na tej stronie można dodać więcej lokalizacji.  
  
   **Korzystanie ze stron nie mających danych binarnych/symboli/źródeł**  
  
   Jeśli program Visual Studio nie może znaleźć plików potrzebnych do debugowania modułu w zrzucie, wyświetlana jest odpowiednia strona (**nie znaleziono pliku binarnego**, **nie znaleziono symboli**lub **nie znaleziono źródła**). Strony te zawierają szczegółowe informacje o przyczynie problemu i zawierają łącza do czynności, które mogą pomóc w określeniu poprawnej lokalizacji plików. Zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)

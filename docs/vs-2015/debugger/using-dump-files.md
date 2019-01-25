---
title: Przy użyciu plików zrzutu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 12f5c759e921ca1659e2821961e6295e096d19b7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783548"
---
# <a name="using-dump-files"></a>Przy użyciu plików zrzutu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki zrzutu ze stertami lub bez nich; tworzenie pliku zrzutu; otwieranie pliku zrzutu; znajdowanie plików binarnych, PDB i pliku źródłowego pliku zrzutu. 
  
##  <a name="BKMK_Contents"></a> Zawartość  
 [Co to jest plik zrzutu?](#BKMK_What_is_a_dump_file_)  
  
 [Naciśnięcie i przytrzymanie pliki zrzutu ze stertami lub bez](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Wymagania i ograniczenia](#BKMK_Requirements_and_limitations)  
  
 [Tworzenie pliku zrzutu](#BKMK_Create_a_dump_file)  
  
 [Otwieranie pliku zrzutu](#BKMK_Open_a_dump_file)  
  
 [Znajdowanie plików binarnych, plików symboli (.pdb) i plików źródłowych](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
##  <a name="BKMK_What_is_a_dump_file_"></a> Co to jest plik zrzutu?  
 A *plik zrzutu* jest migawką z aplikacji w punkcie w momencie dokonywana zrzutu. To pokazuje, jaki proces był wykonywany i które moduły zostały załadowane. Jeśli zrzut został zapisany z informacjami o stercie, plik zrzutu zawiera migawkę tego, co było w pamięci aplikacji w tamtym momencie. Otwieranie pliku zrzutu ze stertą w Visual Studio przypomina zatrzymywanie w punkcie przerwania sesji debugowania. Chociaż nie możesz kontynuować wykonywania, możesz przeanalizować stosy, wątki i wartości zmiennych aplikacji dla momentu zrzutu.  
  
 Zrzuty są wykorzystywane głównie do debugowania problemów występujących na komputerach, do których deweloper nie ma dostępu. Na przykład można użyć pliku zrzutu z komputera klienta, gdy nie można odtworzyć awarii lub zawieszenia u klienta na własnym komputerze. Zrzuty są również tworzone przez testerów w celu zapisania danych o awarii lub zawieszeniu, tak aby maszyna testowa mogła służyć do dalszego testowania. Debuger programu Visual Studio może zapisywać pliki zrzutu dla kodu zarządzanego lub natywnego. Debuger może załadować pliki zrzutu utworzone przez program Visual Studio lub przez inne programy, które zapisują pliki w *minizrzutu* formatu.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Dump_files__with_or_without_heaps"></a> Naciśnięcie i przytrzymanie pliki zrzutu ze stertami lub bez  
 Można tworzyć pliki zrzutu z informacjami o stercie lub bez nich.  
  
- **Pliki zrzutu ze stertami** zawierają migawkę pamięci aplikacji. Obejmuje to wartości zmiennych utworzonych w momencie zrzutu. Jeśli załadujesz plik zrzutu, który został zapisany ze stertą, program Visual Studio można załadować symbole, nawet jeśli nie można odnaleźć pliku binarnego aplikacji. Program Visual Studio zapisuje także pliki binarne załadowanych modułów macierzystych w pliku zrzutu, co znacznie ułatwia debugowanie.  
  
- **Zrzuć pliki bez stert** są znacznie mniejsze niż informacjami o stertach. Jednak debuger musi załadować pliki binarne aplikacji, aby znaleźć informacje o symbolach. Pliki binarne muszą dokładnie odpowiadać plikom binarnym, które były używane podczas tworzenia zrzutu. Tylko wartości zmiennych stosu są zapisywane w plikach zrzutu bez danych sterty.  
  
  ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Requirements_and_limitations"></a> Wymagania i ograniczenia  
  
- Debugowanie plików zrzutu zoptymalizowanego kodu może być mylące. Na przykład wbudowywanie funkcji przez kompilator może spowodować nieoczekiwane stosy wywołań, a inne optymalizacje mogą zmienić okres istnienia zmiennych.  
  
- Pliki zrzutu z komputerów 64-bitowych muszą być debugowane na wystąpieniu programu Visual Studio, który jest uruchomiony na komputerze 64-bitowym.  
  
- W wersjach Visual Studio starszych niż VS 2013, zrzutów aplikacji 32-bitowych uruchamianych na komputerach 64-bitowych, które zostały zebrane przez kilka narzędzi (takich jak Menedżer zadań i WinDbg 64-bitowe), nie można otworzyć w programie Visual Studio. Ograniczenie to zostało usunięte w VS 2013.  
  
- Program Visual Studio umożliwia debugowanie plików zrzutu macierzystych aplikacji z urządzeń ARM. Program Visual Studio umożliwia również debugowanie plików zrzutu zarządzanych aplikacji z urządzeń ARM, ale tylko w macierzystym debugerze.  
  
- Aby debugować [trybu jądra](http://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) plików zrzutu w programie Visual Studio 2013, Pobierz [Windows 8.1 w wersji dla debugowania narzędzi dla Windows](http://msdn.microsoft.com/windows/hardware/gg463009). Zobacz [debugowanie jądra w programie Visual Studio](http://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Visual Studio nie umożliwia debugowania plików zrzutu zapisanych w starszym formacie zrzutu znanym jako [zrzut trybu użytkownika pełnego](http://msdn.microsoft.com/library/windows/hardware/ff545506.aspx). Należy zauważyć, że pełny zrzut trybu użytkownika to nie to samo, co zrzut ze stertą.  
  
- Aby debugować z [SOS.dll (SOS Debugging Extension)](http://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) w programie Visual Studio, należy zainstalować debugowania narzędzi dla Windows będącego częścią Windows Driver Kit (WDK). Zobacz [Windows 8.1 (wersja zapoznawcza): Pobierz zestawy, bity i narzędzia](http://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Create_a_dump_file"></a> Tworzenie pliku zrzutu  
 Aby utworzyć plik zrzutu z programu Visual Studio:  
  
- Podczas debugowania procesu w Visual Studio, można zapisać plik zrzutu po zatrzymaniu debugera w sytuacji wyjątku lub w punkcie przerwania. Wybierz **Zapisz zrzut jako**, **debugowania**. W **Zapisz zrzut jako** dialogowym **Zapisz jako typ** listy, możesz wybrać **minizrzutu** lub **minizrzutu ze stertą** (ustawienie domyślne).  
  
- Za pomocą [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) włączone, można dołączyć debugera do awarii procesu, który działa poza debugera i następnie zapisać plik zrzutu. Zobacz [dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  Można również tworzyć pliki zrzutu za pomocą dowolnego programu, który obsługuje format minizrzutu systemu Windows. Na przykład **Procdump** narzędzie wiersza polecenia z [Windows Sysinternals](http://technet.microsoft.com/sysinternals/default) można tworzyć pliki zrzutu awaryjnego procesów na podstawie wyzwalaczy lub na żądanie. Zobacz [wymagania i ograniczenia](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) w tym temacie, aby uzyskać dodatkowe informacje na temat korzystania z innych narzędzi do tworzenia plików zrzutu.  
  
  ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Open_a_dump_file"></a> Otwieranie pliku zrzutu  
  
1.  W programie Visual Studio, wybierz **pliku**, **Otwórz**, **pliku**.  
  
2.  W **Otwórz plik** okno dialogowe Znajdź i zaznacz plik zrzutu. Będzie zazwyczaj miał rozszerzenie .dmp. Następnie wybierz **OK**.  
  
3.  **Podsumowanie pliku zrzutu** zostanie wyświetlone okno. W tym oknie można wyświetlać informacje podsumowujące debugowanie dla pliku zrzutu, ustawić ścieżkę symboli, rozpocząć debugowanie i skopiować informacje podsumowujące do Schowka.  
  
     ![Strona podsumowania minizrzutu](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4.  Aby rozpocząć debugowanie, przejdź do **akcje** sekcji, a następnie wybierz opcję **Debuguj tylko kod natywny** lub **debugowanie za pomocą mieszanego**.  
  
##  <a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Znajdowanie plików binarnych, plików symboli (.pdb) i plików źródłowych  
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
  
3. Ścieżki symboli określone w **debugowanie**, **opcje**, **symbole** stronie programu Visual Studio **narzędzia**, **opcje**  okno dialogowe. Do wyszukiwania na tej stronie można dodać więcej lokalizacji.  
  
   **Przy użyciu nie znaleziono pliku binarnego / symboli / źródła strony**  
  
   Jeśli program Visual Studio nie może znaleźć plików potrzebnych do debugowania modułu w zrzucie, wyświetlana jest odpowiednia strona (**nie znaleziono pliku binarnego**, **nie znaleziono symboli**, lub **nie znaleziono źródła**). Strony te zawierają szczegółowe informacje o przyczynie problemu i zawierają łącza do czynności, które mogą pomóc w określeniu poprawnej lokalizacji plików. Zobacz [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Just-In-Time Debugging](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Określ symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)

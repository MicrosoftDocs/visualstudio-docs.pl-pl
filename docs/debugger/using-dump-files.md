---
title: Używanie plików zrzutu w pliku | Microsoft Docs
description: Plik zrzutu to migawka wykonywanej aplikacji i załadowanych modułów. Rozważ utworzenie pliku zrzutu w sytuacjach, w których nie masz dostępu do debugowania aplikacji.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1496c50d6a4022083a5cd093a0682ef36c70bbaa
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389231"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Pliki zrzutu w Visual Studio debugowania

<a name="BKMK_What_is_a_dump_file_"></a> Plik *zrzutu* to migawka, która pokazuje wykonywany proces i moduły, które zostały załadowane dla aplikacji w punkcie w czasie. Zrzut z informacjami o stercie zawiera również migawkę pamięci aplikacji w tym momencie.

Otwieranie pliku zrzutu ze stertą w Visual Studio przypomina zatrzymywanie w punkcie przerwania w sesji debugowania. Mimo że nie można kontynuować wykonywania, można zbadać stosy, wątki i wartości zmiennych aplikacji w czasie zrzutu.

Zrzuty są najczęściej używane do debugowania problemów z maszynami, do których deweloperzy nie mają dostępu. Pliku zrzutu z komputera klienta można użyć, gdy nie można odtworzyć awarii lub nieosiągalnego programu na własnym komputerze. Testerzy tworzą również zrzuty, aby zapisać dane programu w przypadku awarii lub nieosiągalne do użycia w celu przeprowadzenia większej liczby testów.

Debuger programu Visual Studio może zapisywać pliki zrzutu dla kodu zarządzanego lub natywnego. Może debugować pliki zrzutu utworzone przez Visual Studio lub przez inne aplikacje, które zapisują pliki w *formacie minizrzuci.*

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Wymagania i ograniczenia

- Aby debugować pliki zrzutu z maszyn 64-bitowych, Visual Studio muszą być uruchomione na maszynie 64-bitowej.

::: moniker range=">= vs-2019"
- Visual Studio można debugować pliki zrzutu zarządzanych aplikacji z systemu operacyjnego Linux. 
::: moniker-end

- Program Visual Studio umożliwia debugowanie plików zrzutu macierzystych aplikacji z urządzeń ARM. Można również debugować zrzuty zarządzanych aplikacji z urządzeń ARM, ale tylko w natywnym debugerze.

- Aby [debugować pliki](/windows-hardware/drivers/debugger/kernel-mode-dump-files) zrzutu [](/dotnet/framework/tools/sos-dll-sos-debugging-extension) w trybie jądra lub użyć rozszerzenia debugowaniaSOS.dllw programie Visual Studio, pobierz narzędzia debugowania dla systemu Windows z witryny [Zestaw sterowników systemu Windows (WDK).](/windows-hardware/drivers/download-the-wdk)

- Visual Studio debugowania plików zrzutu zapisanych w starszym, pełnym formacie [zrzutu w trybie](/windows/desktop/wer/collecting-user-mode-dumps) użytkownika. Pełny zrzut trybu użytkownika nie jest taki sam jak zrzut ze stertą.

- Debugowanie plików zrzutu zoptymalizowanego kodu może być mylące. Na przykład wywłaszczanie funkcji przez kompilator może spowodować nieoczekiwane stosy wywołań, a inne optymalizacje mogą zmienić okres istnienia zmiennych.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Zrzucanie plików ze chyłkami lub bez

Pliki zrzutu mogą mieć informacje o stercie lub nie.

- **Pliki zrzutu ze** zrzutami zawierają migawkę pamięci aplikacji, w tym wartości zmiennych w czasie zrzutu. Visual Studio pliki binarne załadowanych modułów natywnych w pliku zrzutu ze stertą, co może znacznie ułatwić debugowanie. Visual Studio załadować symbole z pliku zrzutu ze stertą, nawet jeśli nie może odnaleźć pliku binarnego aplikacji.

- **Pliki zrzutu bez zrzutów są** znacznie mniejsze niż zrzuty ze swoimi hełmami, ale debuger musi załadować pliki binarne aplikacji, aby znaleźć informacje o symbolach. Załadowane pliki binarne muszą dokładnie odpowiadać plikom uruchomionym podczas tworzenia zrzutu. Pliki zrzutu bez sterty zapisują tylko wartości zmiennych stosu.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Tworzenie pliku zrzutu

Podczas debugowania procesu w programie Visual Studio można zapisać zrzut, gdy debuger zatrzymał się w punkcie przerwania lub wyjątku.

Po włączeniu debugowania [just in time](../debugger/just-in-time-debugging-in-visual-studio.md) można dołączyć debuger programu Visual Studio do procesu, który ulega awarii poza programem Visual Studio, a następnie zapisać plik zrzutu z debugera. Zobacz [Dołączanie do uruchomionych procesów.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Aby zapisać plik zrzutu:**

1. Po zatrzymaniu w momencie wystąpienia błędu lub punktu przerwania podczas debugowania wybierz pozycję  >  **Debuguj zapisz zrzut jako**.

1. W **oknie dialogowym Zapisywanie** zrzutu jako w obszarze Zapisz jako **typ** wybierz pozycję **Minizrzut** lub **Minidump ze** stertą (ustawienie domyślne).

1. Przejdź do ścieżki i wybierz nazwę pliku zrzutu, a następnie wybierz pozycję **Zapisz**.

>[!NOTE]
>Pliki zrzutu można tworzyć za pomocą dowolnego programu obsługującego format minizrzuca systemu Windows. Na przykład narzędzie wiersza polecenia **Procdump** z systemu [Windows Sysinternals](/sysinternals/) może tworzyć pliki zrzutu awaryjnego procesu na podstawie wyzwalaczy lub na żądanie. Zobacz [Wymagania i ograniczenia, aby](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) uzyskać informacje o używaniu innych narzędzi do tworzenia plików zrzutu.

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Otwieranie pliku zrzutu

1. W Visual Studio wybierz pozycję **Plik**  >  **Otwórz**  >  **plik.**

1. W **oknie dialogowym Otwieranie** pliku znajdź i wybierz plik zrzutu. Zazwyczaj ma rozszerzenie *dmp.* Wybierz przycisk **OK**.

   Okno **Podsumowanie minizrzuca** pliku zawiera podsumowanie i informacje o module dla pliku zrzutu oraz akcje, które można podjąć.

   ![Strona podsumowania minizmigonia](../debugger/media/dbg_dump_summarypage.png "Strona podsumowania minizmigonia")

1. W **obszarze Akcje:**
   - Aby ustawić lokalizacje ładowania symboli, wybierz **pozycję Ustaw ścieżki symboli**.
   - Aby rozpocząć debugowanie, wybierz pozycję Debuguj tylko **zarządzane,** **Debuguj** tylko natywnie, Debuguj za pomocą **mieszanych** lub **Debuguj za pomocą pamięci zarządzanej.**

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> Znajdowanie .exe, .pdb i plików źródłowych

Aby korzystać z funkcji pełnego debugowania w pliku zrzutu, Visual Studio potrzeby:

- Plik *.exe,* dla których utworzono zrzut, oraz inne pliki binarne (biblioteki DLL itp.), których używa proces zrzutu.
- Pliki symboli *(.pdb)* dla *.exe* i innych plików binarnych.
- Pliki *.exe* *i .pdb,* które dokładnie pasują do wersji i kompilacji plików podczas tworzenia zrzutu.
- Pliki źródłowe dla odpowiednich modułów. Jeśli nie możesz znaleźć plików źródłowych, możesz użyć desembemblii modułów.

Jeśli zrzut zawiera dane sterty, Visual Studio może poradzić sobie z brakującymi plikami binarnymi dla niektórych modułów, ale musi mieć pliki binarne wystarczające do wygenerowania prawidłowych stosów wywołań przez moduły.

### <a name="search-paths-for-exe-files"></a>Ścieżki wyszukiwania .exe plików

Visual Studio automatycznie wyszukuje pliki *.exe,* które nie znajdują się w pliku zrzutu, w tych lokalizacjach:

1. Folder zawierający plik zrzutu.
2. Ścieżka modułu określa plik zrzutu, czyli ścieżkę modułu na maszynie, na której zebrano zrzut.
3. Ścieżki symboli określone w **narzędziach** (lub **debugowaniu**) >   >    >  **debugowania symboli**. Możesz również otworzyć stronę **Symbole w** **okienku Akcje** okna Podsumowanie pliku **zrzutu.** Na tej stronie możesz dodać więcej lokalizacji do wyszukania.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Użyj stron Bez danych binarnych, Bez symboli lub Nie znaleziono źródła

Jeśli Visual Studio nie można znaleźć plików, których potrzebuje do debugowania modułu w zrzucie, zostanie pokazana strona Nie znaleziono pliku binarnego, Nie znaleziono symboli lub Nie znaleziono **źródła.**   Te strony zawierają szczegółowe informacje o przyczynach problemu i linki do akcji, które mogą pomóc w zlokalizowaniu plików. Zobacz [Temat Specify symbol (.pdb) and source files (Określanie plików symboli (.pdb) i plików źródłowych).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Zobacz też

- [Jak debugować zarządzany zrzut pamięci za pomocą analizatorów diagnostycznych .NET](../debugger/how-to-debug-managed-memory-dump.md)
- [Debugowanie just in time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)
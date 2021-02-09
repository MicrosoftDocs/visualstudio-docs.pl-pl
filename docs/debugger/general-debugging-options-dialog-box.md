---
title: Ogólne, debugowanie, Opcje — okno dialogowe | Microsoft Docs
description: Ustaw opcje debugera programu Visual Studio, aby spełniały Twoje potrzeby debugowania. Można skonfigurować zachowanie przerwania, poziomy debugowania, zachowanie wyświetlania i wiele innych.
ms.custom: SEO-VS-2020
ms.date: 06/04/2020
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 928499957ca90dda718f324827968f10cbb3a141
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870574"
---
# <a name="general-debugging-options"></a>Ogólne opcje debugowania

Aby ustawić opcje debugera programu Visual Studio, wybierz  >  **Opcje** narzędzia i w obszarze **debugowanie** zaznacz lub usuń zaznaczenie pól obok opcji **Ogólne** . Wszystkie ustawienia domyślne można przywrócić za pomocą **Narzędzia**  >  **Importuj i Eksportuj ustawienia**  >  **Zresetuj wszystkie ustawienia**. Aby zresetować podzbiór ustawień, Zapisz ustawienia za pomocą **Kreatora importowania i eksportowania ustawień** przed wprowadzeniem zmian, które chcesz przetestować, a następnie zaimportuj zapisane ustawienia później.

Można ustawić następujące opcje **Ogólne** :

**Zadawaj przed usunięciem wszystkich punktów przerwania**: wymaga potwierdzenia przed ukończeniem polecenia **Usuń wszystkie punkty przerwania** .

**Przerwij wszystkie procesy po przerwaniu jednego procesu**: równocześnie przerywa wszystkie procesy, do których jest dołączony debuger, gdy wystąpi przerwanie.

**Przerwij, gdy wyjątki przekraczają granice elementu AppDomain lub zarządzane/natywne**: w przypadku debugowania zarządzanego lub mieszanego środowisko uruchomieniowe języka wspólnego może przechwytywać wyjątki, które przekraczają granice domeny aplikacji lub granice zarządzane/natywne w przypadku spełnienia następujących warunków:

1. Gdy kod natywny wywołuje kod zarządzany za pomocą międzyoperacyjności modelu COM i kod zarządzany zgłasza wyjątek. Zobacz [wprowadzenie do międzyoperacyjności modelu COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Gdy kod zarządzany uruchomiony w domenie aplikacji 1 wywołuje kod zarządzany w domenie aplikacji 2, a kod w aplikacji domena 2 zgłasza wyjątek. Zobacz [programowanie z domenami aplikacji](/dotnet/articles/framework/app-domains/index).

3. Gdy kod wywołuje funkcję przy użyciu odbicia, a funkcja zgłasza wyjątek. Zobacz [odbicie](/dotnet/framework/reflection-and-codedom/reflection).

W warunkach 2 i 3 wyjątek jest czasami przechwytywany przez kod zarządzany w programie, `mscorlib` a nie przez środowisko uruchomieniowe języka wspólnego. Ta opcja nie wpływa na przerwanie w przypadku wyjątków przechwytywanych przez program `mscorlib` .

**Włącz debugowanie na poziomie adresu**: włącza zaawansowane funkcje debugowania na poziomie adresu (okno **demontażu** , okno **rejestrów** i punkty przerwania adresów).

- **Pokaż demontaż, jeśli źródło jest niedostępne**: automatycznie pokazuje okno **demontażu** podczas debugowania kodu, dla którego źródło jest niedostępne.

**Włącz filtry punktów przerwania**: umożliwia ustawienie filtrów dla punktów przerwania, aby miały wpływ tylko na określone procesy, wątki lub komputery.

**Użyj nowego pomocnika wyjątków**: włącza pomocnika wyjątków, który zastępuje asystenta wyjątków. (W programie Visual Studio 2017 jest obsługiwana pomocnik wyjątków)

> [!NOTE]
> Dla kodu zarządzanego ta opcja została wcześniej wywołana — **Włącz asystenta wyjątków** .

**Włącz tylko mój kod**: debuger wyświetla tylko kod użytkownika ("mój kod"), ignorując kod systemowy i inny kod, który jest zoptymalizowany lub który nie ma symboli debugowania.

- **Ostrzegaj w przypadku braku kodu użytkownika podczas uruchamiania (tylko kod zarządzany)**: gdy debugowanie rozpocznie się z tylko mój kod włączone, ta opcja ostrzega o tym, czy nie ma kodu użytkownika ("mój kod").

**Włącz wykonywanie kroków źródła .NET Framework**: umożliwia debugerowi przechodzenie do .NET Framework źródła. Włączenie tej opcji powoduje automatyczne wyłączenie Tylko mój kod. Symbole .NET Framework zostaną pobrane do lokalizacji pamięci podręcznej. Zmień lokalizację pamięci podręcznej za pomocą okna dialogowego **Opcje** , kategorii **debugowanie** i **symboli** .

Przekrocz **nad właściwościami i operatorami (tylko kod zarządzany)**: uniemożliwia debugerowi przechodzenie do właściwości i operatorów w kodzie zarządzanym.

**Włącz Obliczanie właściwości i inne niejawne wywołania funkcji**: włącza automatyczną ocenę właściwości i niejawne wywołania funkcji w oknach zmiennych i oknie dialogowym **QuickWatch** .

- **Wywołaj funkcję konwersji ciągów na obiektach w oknach zmiennych (tylko w języku C# i JavaScript)**: wykonuje wywołanie konwersji niejawnego ciągu podczas oceniania obiektów w oknach zmiennych. Wynik jest wyświetlany jako ciąg zamiast nazwy typu. Stosuje się tylko podczas debugowania w kodzie C#. To ustawienie może być zastąpione przez atrybut DebuggerDisplay (zobacz [using a DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md)).

**Włącz obsługę serwera źródłowego**: informuje debuger programu Visual Studio, aby pobierać pliki źródłowe z serwerów źródłowych, które implementują protokół srcsrv ( `srcsrv.dll` ). Team Foundation Server i narzędzia debugowania dla systemu Windows to dwa serwery źródłowe implementujące protokół. Więcej informacji na temat konfiguracji SrcSrv można znaleźć w dokumentacji [srcsrv](/windows-hardware/drivers/debugger/srcsrv) . Ponadto zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Ponieważ odczytywanie plików *. pdb* może wykonać dowolny kod w plikach, należy się upewnić, że ufasz serwerowi.

- **Drukuj komunikaty diagnostyczne serwera źródłowego w oknie danych wyjściowych**: po włączeniu obsługi serwera źródłowego to ustawienie włącza wyświetlanie danych diagnostycznych.

- **Zezwalaj na serwer źródłowy dla zestawów częściowego zaufania (tylko zarządzane)**: po włączeniu obsługi serwera źródłowego to ustawienie zastępuje domyślne zachowanie nie pobiera źródeł dla zestawów częściowej relacji zaufania.

- **Zawsze uruchamiaj niezaufane polecenia serwera źródłowego bez monitowania**: po włączeniu obsługi serwera źródłowego to ustawienie zastępuje domyślne zachowanie monitowania podczas uruchamiania polecenia niezaufanego.

**Włącz obsługę linku źródłowego**: informuje debuger programu Visual Studio, aby pobierał pliki źródłowe plików *. pdb* , które zawierają informacje o linku źródłowym. Aby uzyskać więcej informacji o łączu źródłowym, zobacz [specyfikację linku źródłowego](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Ponieważ link źródłowy pobierze pliki przy użyciu protokołu HTTP lub https, upewnij się, że ufasz plikowi *. pdb* .

- **Wróć do uwierzytelniania za pomocą programu Git Credential Manager dla wszystkich żądań linku źródłowego**: gdy włączona jest obsługa linku źródłowego, a żądanie linku źródłowego nie powiedzie się, program Visual Studio wywoła Menedżera poświadczeń git.

**Podświetl cały wiersz źródła dla punktów przerwania i bieżącej instrukcji (tylko C++)**: gdy debuger podświetla punkt przerwania lub bieżącą instrukcję, podświetla cały wiersz.

**Wymagaj, aby pliki źródłowe były dokładnie zgodne z oryginalną wersją**: instruuje debugera, aby upewnić się, że plik źródłowy jest zgodny z wersją kodu źródłowego użytego do skompilowania debugowanego pliku wykonywalnego. Gdy wersja nie jest zgodna, zostanie wyświetlony monit o znalezienie pasującego źródła. Jeśli nie znaleziono pasującego źródła, kod źródłowy nie będzie wyświetlany podczas debugowania.

**Przekieruj cały tekst okna danych wyjściowych do okna bezpośredniego**: wysyła wszystkie komunikaty debugera, które zwykle pojawiają się w oknie **danych wyjściowych** do okna **bezpośredniego** .

**Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych**: wyłącza wszystkie dostosowania widoku struktury obiektów. Aby uzyskać więcej informacji na temat dostosowywania widoku, zobacz [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-managed-objects.md).

**Pomiń optymalizację JIT podczas ładowania modułu (tylko kod zarządzany)**: wyłącza optymalizację JIT kodu zarządzanego, gdy moduł jest ładowany i jest kompilowany w trybie JIT podczas dołączania debugera. Wyłączenie optymalizacji może ułatwić debugowanie niektórych problemów, ale kosztem wydajności. Jeśli używasz Tylko mój kod, pominięcie optymalizacji JIT może spowodować, że kod niebędący użytkownikiem będzie wyświetlany jako kod użytkownika ("mój kod"). Aby uzyskać więcej informacji, zobacz [Optymalizacja i debugowanie JIT](../debugger/jit-optimization-and-debugging.md).

**Włącz debugowanie kodu JavaScript dla ASP.NET (Chrome, Microsoft Edge i IE)**: włącza debuger skryptów dla aplikacji ASP.NET. Przy pierwszym użyciu w programie Chrome może być konieczne zalogowanie się do przeglądarki w celu włączenia zainstalowanych rozszerzeń programu Chrome. Wyłącz tę opcję, aby przywrócić starsze zachowanie.

::: moniker range=">= vs-2019"
**Włącz używanie wieloskładnikowego debugera JavaScript do debugowania JavaScript w odpowiednich celach (wymaga ponownego uruchomienia debugowania)** Umożliwia jednoczesne łączenie się z przeglądarką i zapleczem, umożliwiając Debugowanie kodu działającego na kliencie i serwerze bezpośrednio z edytora.
::: moniker-end

**Załaduj biblioteki DLL (tylko natywne)**: ładuje tabele eksportu dll. Informacje o symbolach z tabel eksportu bibliotek DLL mogą być przydatne, jeśli pracujesz z komunikatami systemu Windows, procedurami systemu Windows (WindowProcs), obiektami COM lub kierowaniem lub dowolną biblioteką DLL, dla której nie masz symboli. Odczytywanie informacji o eksporcie z biblioteki DLL obejmuje pewne obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.

Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki DLL, użyj `dumpbin /exports` . Symbole są dostępne dla dowolnej 32-bitowej systemowej biblioteki DLL. Odczytując `dumpbin /exports` dane wyjściowe, można zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji z tabel eksportu bibliotek DLL mogą pojawić się w innym miejscu debugera. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [polecenia DUMPBIN/exports](/cpp/build/reference/dash-exports).

**Pokaż diagram stosów równoległych dołu**: określa kierunek wyświetlania stosów w oknie **stosów równoległych** .

**Ignoruj wyjątki dostępu do pamięci procesora GPU, jeśli zapisano dane nie zmieniły wartości**: ignoruje sytuacje wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie uległy zmianie. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md).

**Użyj zarządzanego trybu zgodności**: zastępuje domyślny aparat debugowania ze starszą wersją, aby umożliwić te scenariusze:

- Używasz języka .NET innego niż C#, Visual Basic lub F #, który oferuje własną ewaluatora wyrażeń (obejmuje to C++/CLI).

- Chcesz włączyć funkcję Edytuj i Kontynuuj dla projektów C++ podczas debugowania w trybie mieszanym.

> [!NOTE]
> Wybranie trybu zgodności zarządzanej powoduje wyłączenie niektórych funkcji, które są implementowane tylko w domyślnym aparacie debugowania. Starszy aparat debugowania został zastąpiony w programie Visual Studio 2012.

::: moniker range="vs-2017"
**Użyj starszych ocen w językach c# i VB**: debuger użyje ocen wyrażeń Visual Studio 2013 C# lub Visual Basic, a nie ocen wyrażeń opartych na Roslyn w programie Visual Studio 2015.
::: moniker-end

**Ostrzegaj w przypadku używania wizualizacji debugera niestandardowego z potencjalnie niebezpiecznymi procesami (tylko kod zarządzany)**: program Visual Studio ostrzega o tym, gdy korzystasz z niestandardowego wizualizatora debugera, który uruchamia kod w debugowanym procesie, ponieważ może to spowodować uruchomienie niebezpiecznego kodu.

**Włącz Alokator sterty debugowania systemu Windows (tylko kod natywny)**: włącza stertę debugowania systemu Windows w celu poprawienia diagnostyki sterty. Włączenie tej opcji będzie miało wpływ na wydajność debugowania.

**Włącz narzędzia debugowania interfejsu użytkownika dla języka XAML**: dynamiczne drzewo wizualne i właściwości na żywo Eksplorowanie systemu Windows zostaną wyświetlone po rozpoczęciu debugowania (**F5**) jako obsługiwanego typu projektu. Aby uzyskać więcej informacji, zobacz [Sprawdzanie właściwości XAML podczas debugowania](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Podgląd wybranych elementów w dynamicznym drzewie wizualnym**: element XAML, którego kontekst jest wybrany, również jest wybierany w **aktywnym oknie drzewa wizualnego** .

- **Pokaż narzędzia środowiska uruchomieniowego w aplikacji**: pokazuje **dynamiczne polecenia drzewa wizualnego** na pasku narzędzi w oknie głównym debugowanej aplikacji XAML. Ta opcja została wprowadzona w programie Visual Studio 2015 Update 2.

- **Włącz gorącą funkcję XAML**: umożliwia korzystanie z funkcji gorącego ładowania XAML w kodzie XAML, gdy aplikacja jest uruchomiona. (Ta funkcja była wcześniej nazywana "Edytuj i Kontynuuj" XAML ")

::: moniker range=">= vs-2019" 
- **Włącz opcję tylko mój kod XAML**: począwszy od programu Visual Studio 2019 w wersji 16,4, **dynamiczne drzewo wizualne** domyślnie pokazuje tylko kod XAML, który jest klasyfikowany do kodu użytkownika. Jeśli wyłączysz tę opcję, w narzędziu zostanie wyświetlony cały wygenerowany kod XAML.

- Wyłącz **tryb zaznaczania, gdy element jest zaznaczony** Począwszy od programu Visual Studio 2019 w wersji 16,4, przycisk selektora elementu paska narzędzi w aplikacji (**Włącz wybór**) wyłącza się, gdy element jest zaznaczony. Wyłączenie tej opcji spowoduje, że zaznaczenie elementu zostanie włączone do momentu ponownego kliknięcia przycisku paska narzędzi w aplikacji.

- **Zastosuj ładowanie kodu XAML przy zapisywaniu dokumentu** Począwszy od programu Visual Studio 2019 w wersji 16,6, podczas zapisywania dokumentu są stosowane gorące załadowanie XAML.

::: moniker-end

**Włącz narzędzia diagnostyczne podczas debugowania**: okno **Narzędzia diagnostyczne** pojawia się podczas debugowania.

**Pokaż czas, który upłynął element PerfTip dla podczas debugowania**: w oknie kodu jest wyświetlany czas, który upłynął podczas debugowania danego wywołania metody.

**Włącz opcję Edytuj i Kontynuuj**: Włącza funkcję Edytuj i Kontynuuj podczas debugowania.

- **Włącz natywne edytowanie i kontynuowanie**: możesz użyć funkcji Edytuj i Kontynuuj podczas debugowania natywnego kodu C++. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Zastosuj zmiany przy kontynuowaniu (tylko w trybie macierzystym)**: program Visual Studio automatycznie kompiluje i stosuje wszelkie zaległe zmiany kodu, które zostały wykonane podczas kontynuowania procesu ze stanu przerwania. Jeśli nie jest zaznaczone, można wybrać opcję zastosowania zmian za pomocą elementu **Zastosuj zmiany kodu** w menu **Debuguj** .

- **Ostrzegaj o nieodświeżonym kodzie (tylko kod natywny)**: uzyskuj ostrzeżenia dotyczące nieodświeżonego kodu.

**Pokaż przycisk uruchamiania do kliknięcia w edytorze podczas debugowania**: gdy ta opcja jest zaznaczona, przycisk [Uruchom do kliknięcia](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) będzie wyświetlany podczas debugowania.

**Automatycznie zamknij konsolę po zatrzymaniu debugowania**: informuje program Visual Studio, aby zamknąć konsolę na końcu sesji debugowania.

::: moniker range=">= vs-2019"
**Włącz funkcję szybkiego obliczania wyrażeń (tylko zarządzany)**: umożliwia debugerowi podejmowanie prób szybszej oceny przez symulowanie wykonywania prostych właściwości i metod.

**Załaduj symbole debugowania w procesie zewnętrznym (tylko kod natywny)** Włącza tę [optymalizację pamięci](https://devblogs.microsoft.com/cppblog/out-of-process-debugger-for-c-in-visual-studio-2019/) podczas debugowania.

**Przełączenie programu Visual Studio na pierwszy plan w przypadku przerwania w debugerze** Przełącza program Visual Studio na pierwszy plan po wstrzymaniu w debugerze.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opcje dostępne we wcześniejszych wersjach programu Visual Studio

Jeśli używasz starszej wersji programu Visual Studio, niektóre dodatkowe opcje mogą być obecne.

**Włącz narzędzia deweloperskie Edge dla aplikacji JavaScript platformy UWP (eksperymentalne)**: włącza narzędzia deweloperskie dla platformy UWP aplikacji JavaScript w przeglądarce Microsoft Edge.

**Włącz starszą wersję debugera języka JavaScript dla ASP.NET**: włącza starszy debuger skryptów języka JavaScript dla aplikacji ASP.NET. Przy pierwszym użyciu w programie Chrome może być konieczne zalogowanie się do przeglądarki w celu włączenia zainstalowanych rozszerzeń programu Chrome.

**Włącz asystenta wyjątków**: dla kodu zarządzanego, włącza asystenta wyjątków. Począwszy od programu Visual Studio 2017, pomocnik wyjątków zastąpił asystenta wyjątków.

**Odwinięcie stosu wywołań w przypadku nieobsługiwanych wyjątków**: powoduje, że okno **stos wywołań** wycofa stos wywołań do punktu przed wystąpieniem nieobsługiwanego wyjątku.

**Użyj eksperymentalnego sposobu uruchamiania debugowania kodu JavaScript w programie Chrome podczas uruchamiania programu Visual Studio jako administrator**: informuje program Visual Studio, aby wypróbować nowy sposób uruchamiania programu Chrome podczas debugowania JavaScript.

**Ostrzegaj, jeśli nie ma symboli podczas uruchamiania (tylko kod natywny)**: Wyświetla okno dialogowe ostrzeżenia podczas debugowania programu, dla którego debuger nie ma informacji o symbolach.

**Ostrzegaj, jeśli debugowanie skryptów jest wyłączone przy uruchomieniu**: Wyświetla okno dialogowe ostrzeżenia, gdy debuger jest uruchamiany z wyłączonym debugowaniem skryptów.

**Użyj natywnego trybu zgodności**: w przypadku wybrania tej opcji debuger używa programu Visual Studio 2010 Native Debugger zamiast nowego debugera natywnego.

- Użyj tej opcji, jeśli debugujesz kod .NET C++, ponieważ nowy aparat debugowania nie obsługuje oceniania wyrażeń .NET C++. Jednak włączenie macierzystego trybu zgodności wyłącza wiele funkcji, które są zależne od bieżącej implementacji debugera do działania. Na przykład starszy aparat nie ma wielu wizualizatorów dla wbudowanych typów, takich jak `std::string` w projektach programu Visual Studio 2015.   W takich przypadkach należy używać projektów Visual Studio 2013.

## <a name="see-also"></a>Zobacz też

- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)

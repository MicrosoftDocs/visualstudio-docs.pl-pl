---
title: Ogólne, debugowanie, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/09/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db4756107bb9f5e7e766634897013649db351faa
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211034"
---
# <a name="general-debugging-options"></a>Ogólne opcje debugowania

Aby ustawić opcje debugera programu Visual Studio, wybierz**Opcje** **Narzędzia** > i w obszarze **debugowanie** zaznacz lub usuń zaznaczenie pól obok opcji **Ogólne** . Wszystkie ustawienia domyślne można przywrócić za pomocą **Narzędzia** > **Importuj i Eksportuj ustawienia** > **Zresetuj wszystkie ustawienia**. Aby zresetować podzbiór ustawień, Zapisz ustawienia za pomocą **Kreatora importowania i eksportowania ustawień** przed wprowadzeniem zmian, które chcesz przetestować, a następnie zaimportuj zapisane ustawienia później.

Można ustawić następujące opcje **Ogólne** :

**Zadawaj przed usunięciem wszystkich punktów przerwania**: Wymaga potwierdzenia przed ukończeniem polecenia **Usuń wszystkie punkty przerwania** .

**Przerwij wszystkie procesy po przerwaniu jednego procesu**: Równocześnie przerywa wszystkie procesy, do których jest dołączony debuger, gdy występuje przerwy.

**Przerwij, gdy wyjątki przekraczają granice domeny lub zarządzane/natywne**: W przypadku debugowania w trybie zarządzanym lub mieszanym środowisko uruchomieniowe języka wspólnego może przechwytywać wyjątki, które przekraczają granice domeny aplikacji lub granice zarządzane/natywne w przypadku spełnienia następujących warunków:

1. Gdy kod natywny wywołuje kod zarządzany za pomocą międzyoperacyjności modelu COM i kod zarządzany zgłasza wyjątek. Zobacz [wprowadzenie do międzyoperacyjności modelu COM](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Gdy kod zarządzany uruchomiony w domenie aplikacji 1 wywołuje kod zarządzany w domenie aplikacji 2, a kod w aplikacji domena 2 zgłasza wyjątek. Zobacz [programowanie z domenami aplikacji](/dotnet/articles/framework/app-domains/index).

3. Gdy kod wywołuje funkcję przy użyciu odbicia, a funkcja zgłasza wyjątek. Zobacz [odbicie](/dotnet/framework/reflection-and-codedom/reflection).

W warunkach 2 i 3 wyjątek jest czasami przechwytywany przez kod zarządzany w programie `mscorlib` , a nie przez środowisko uruchomieniowe języka wspólnego. Ta opcja nie wpływa na przerwanie w przypadku wyjątków `mscorlib`przechwytywanych przez program.

**Włącz debugowanie na poziomie adresu**: Włącza zaawansowane funkcje debugowania na poziomie adresu (okno **demontażu** , okno **rejestrów** i punkty przerwania adresów).

- **Pokaż demontaż, jeśli źródło jest niedostępne**:   Automatycznie wyświetla okno **demontaż** , gdy debugujesz kod, dla którego źródło jest niedostępne.

**Włącz filtry punktów przerwania**: Umożliwia ustawienie filtrów dla punktów przerwania, aby miały wpływ tylko na określone procesy, wątki lub komputery.

**Użyj nowego pomocnika wyjątków**: Włącza pomocnika wyjątków, który zastępuje asystenta wyjątków. (W programie Visual Studio 2017 jest obsługiwana pomocnik wyjątków)

> [!NOTE]
> Dla kodu zarządzanego ta opcja została wcześniej wywołana — **Włącz asystenta wyjątków** .

**Włącz tylko mój kod**: Debuger wyświetla tylko kod użytkownika ("mój kod"), ignorując kod systemowy i inny kod, który jest zoptymalizowany lub nie ma symboli debugowania.

- **Ostrzegaj w przypadku braku kodu użytkownika podczas uruchamiania (tylko kod zarządzany)** :   Po rozpoczęciu debugowania z włączonym Tylko mój kod ta opcja ostrzega o braku kodu użytkownika ("mój kod").

**Włącz wykonywanie kroków źródła .NET Framework**: Zezwala debugerowi na wkroczenie do .NET Framework źródła. Włączenie tej opcji powoduje automatyczne wyłączenie Tylko mój kod. Symbole .NET Framework zostaną pobrane do lokalizacji pamięci podręcznej. Zmień lokalizację pamięci podręcznej za pomocą okna dialogowego **Opcje** , kategorii **debugowanie** i **symboli** .

Przekrocz **nad właściwościami i operatorami (tylko zarządzane)** : Uniemożliwia debugerowi przechodzenie do właściwości i operatorów w kodzie zarządzanym.

**Włącz Obliczanie właściwości i inne niejawne wywołania funkcji**: Włącza automatyczną ocenę właściwości i niejawne wywołania funkcji w oknach zmiennych i oknie dialogowym **QuickWatch** .

- **Wywołaj funkcję konwersji ciągów na obiektach w oknachC# zmiennych (tylko kod JavaScript)** : Wykonuje niejawne wywołanie konwersji ciągu podczas oceniania obiektów w oknach zmiennych. Wynik jest wyświetlany jako ciąg zamiast nazwy typu. Stosuje się tylko podczas debugowania C# w kodzie. To ustawienie może być zastąpione przez atrybut DebuggerDisplay (zobacz [using a DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md)).

**Włącz obsługę serwera źródłowego**: Poleca debugerowi programu Visual Studio pobieranie plików źródłowych z serwerów źródłowych, które implementują protokół`srcsrv.dll`srcsrv (). Team Foundation Server i narzędzia debugowania dla systemu Windows to dwa serwery źródłowe implementujące protokół. Więcej informacji na temat konfiguracji SrcSrv można znaleźć w dokumentacji [srcsrv](/windows-hardware/drivers/debugger/srcsrv) . Ponadto zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Ponieważ odczytywanie plików *. pdb* może wykonać dowolny kod w plikach, należy się upewnić, że ufasz serwerowi.

- **Drukuj komunikaty diagnostyczne serwera źródłowego w oknie danych wyjściowych**:   Po włączeniu obsługi serwera źródłowego to ustawienie włącza wyświetlanie danych diagnostycznych.

- **Zezwalaj na serwer źródłowy dla zestawów częściowego zaufania (tylko zarządzane)** :   Po włączeniu obsługi serwera źródłowego to ustawienie zastępuje domyślne zachowanie nie pobiera źródeł dla zestawów częściowej relacji zaufania.

- **Zawsze uruchamiaj niezaufane polecenia serwera źródłowego bez monitowania**:   Po włączeniu obsługi serwera źródłowego to ustawienie powoduje zastąpienie domyślnego zachowania monitowania podczas uruchamiania polecenia niezaufanego.

**Włącz obsługę linku źródłowego**: Informuje debuger programu Visual Studio, aby pobierał pliki źródłowe plików *. pdb* , które zawierają informacje o linku źródłowym. Aby uzyskać więcej informacji o łączu źródłowym, zobacz [specyfikację linku źródłowego](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Ponieważ link źródłowy pobierze pliki przy użyciu protokołu HTTP lub https, upewnij się, że ufasz plikowi *. pdb* .

- **Wróć do uwierzytelniania programu Git Credential Manager dla wszystkich żądań linku źródłowego**:   Gdy włączona jest obsługa linku źródłowego, a żądanie linku źródłowego nie powiedzie się, program Visual Studio wywoła Menedżer poświadczeń git.

**Wyróżnij cały wiersz dla punktów przerwania iC++ bieżącej instrukcji (tylko)** : Gdy debuger podświetla punkt przerwania lub bieżącą instrukcję, podświetli cały wiersz.

**Wymagaj, aby pliki źródłowe były dokładnie zgodne z oryginalną wersją**: Informuje debugera, aby upewnić się, że plik źródłowy jest zgodny z wersją kodu źródłowego użytego do skompilowania debugowanego pliku wykonywalnego. Gdy wersja nie jest zgodna, zostanie wyświetlony monit o znalezienie pasującego źródła. Jeśli nie znaleziono pasującego źródła, kod źródłowy nie będzie wyświetlany podczas debugowania.

**Przekieruj cały tekst okna danych wyjściowych do okna bezpośredniego**: Wysyła wszystkie komunikaty debugera, które zwykle pojawiają się w oknie **danych wyjściowych** do okna **bezpośredniego** .

**Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych**: Wyłącza wszystkie dostosowania widoku struktury obiektu. Aby uzyskać więcej informacji na temat dostosowań widoku, zobacz [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-dot-managed-objects.md).

**Pomiń optymalizację JIT podczas ładowania modułu (tylko w trybie zarządzanym)** : Wyłącza optymalizację JIT kodu zarządzanego, gdy moduł jest ładowany i kompilator JIT jest kompilowany podczas dołączania debugera. Wyłączenie optymalizacji może ułatwić debugowanie niektórych problemów, ale kosztem wydajności. Jeśli używasz Tylko mój kod, pominięcie optymalizacji JIT może spowodować, że kod niebędący użytkownikiem będzie wyświetlany jako kod użytkownika ("mój kod"). Aby uzyskać więcej informacji, zobacz [Optymalizacja i debugowanie JIT](../debugger/jit-optimization-and-debugging.md).

**Włącz debugowanie kodu JavaScript dla ASP.NET (Chrome, Edge i IE)** : Włącza debuger skryptów dla aplikacji ASP.NET. Przy pierwszym użyciu w programie Chrome może być konieczne zalogowanie się do przeglądarki w celu włączenia zainstalowanych rozszerzeń programu Chrome. Wyłącz tę opcję, aby przywrócić starsze zachowanie.

**Włącz narzędzia deweloperskie Edge dla aplikacji JavaScript platformy UWP (eksperymentalne)** : Włącza narzędzia deweloperskie do platformy UWP aplikacji JavaScript w przeglądarce Microsoft Edge.

**Włącz starszą wersję debugera języka JavaScript dla ASP.NET**: Włącza starszy debuger skryptów języka JavaScript dla aplikacji ASP.NET. Przy pierwszym użyciu w programie Chrome może być konieczne zalogowanie się do przeglądarki w celu włączenia zainstalowanych rozszerzeń programu Chrome.

**Użyj eksperymentalnego sposobu uruchamiania debugowania kodu JavaScript w programie Chrome podczas uruchamiania programu Visual Studio jako administrator**: Informuje program Visual Studio, aby wypróbować nowy sposób uruchamiania programu Chrome podczas debugowania JavaScript.

**Załaduj eksporty biblioteki DLL (tylko kod natywny)** : Ładuje tabele eksportu biblioteki DLL. Informacje o symbolach z tabel eksportu bibliotek DLL mogą być przydatne, jeśli pracujesz z komunikatami systemu Windows, procedurami systemu Windows (WindowProcs), obiektami COM lub kierowaniem lub dowolną biblioteką DLL, dla której nie masz symboli. Odczytywanie informacji o eksporcie z biblioteki DLL obejmuje pewne obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.

Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki DLL, użyj `dumpbin /exports`. Symbole są dostępne dla dowolnej 32-bitowej systemowej biblioteki DLL. Czytając `dumpbin /exports` danych wyjściowych, możesz zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji z tabel eksportu bibliotek DLL mogą pojawić się w innym miejscu debugera. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin/EXPORTS](/cpp/build/reference/dash-exports).

**Pokaż diagram stosów równoległych dołu**: Kontroluje kierunek wyświetlania stosów w oknie **stosów równoległych** .

**Ignoruj wyjątki dostępu do pamięci procesora GPU, jeśli zapisano dane nie zmieniły wartości**: Ignoruje sytuacje wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie uległy zmianie. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md).

**Użyj zarządzanego trybu zgodności**: Zastępuje domyślny aparat debugowania ze starszą wersją, aby umożliwić te scenariusze:

- Używasz języka .NET Framework innego niż C#, Visual Basic lub F# , który oferuje własną ewaluatora wyrażeń (obejmuje C++to/CLI).

- Chcesz włączyć funkcję Edytuj i Kontynuuj dla C++ projektów podczas debugowania w trybie mieszanym.

> [!NOTE]
> Wybranie trybu zgodności zarządzanej powoduje wyłączenie niektórych funkcji, które są implementowane tylko w domyślnym aparacie debugowania. Starszy aparat debugowania został zastąpiony w programie Visual Studio 2012.

**Użyj C# starszych i oceniających wyrażenia w języku VB**: Debuger użyje ocen wyrażeń Visual Studio 2013 C# lub Visual Basic zamiast ocen wyrażeń opartych na Roslyn programu Visual Studio 2015.

**Ostrzegaj w przypadku używania wizualizacji debugera niestandardowego z potencjalnie niebezpiecznymi procesami (tylko w programie zarządzanym)** : Program Visual Studio wyświetli ostrzeżenie, gdy korzystasz z niestandardowego wizualizatora debugera, który uruchamia kod w debugowanym procesie, ponieważ może to spowodować uruchomienie niebezpiecznego kodu.

**Włącz Alokator sterty debugowania systemu Windows (tylko kod natywny)** : Włącza stertę debugowania systemu Windows w celu poprawienia diagnostyki sterty. Włączenie tej opcji będzie miało wpływ na wydajność debugowania.

**Włącz narzędzia debugowania interfejsu użytkownika dla języka XAML**: Dynamiczne drzewo wizualne i właściwości na żywo zostaną wyświetlone po rozpoczęciu debugowania (**F5**) obsługiwanego typu projektu. Aby uzyskać więcej informacji, zobacz [Sprawdzanie właściwości XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md).

- **Podgląd wybranych elementów w dynamicznym drzewie wizualnym**:   Element XAML, którego kontekst jest wybrany, również jest wybierany w **aktywnym oknie drzewa wizualnego** .

- **Pokaż narzędzia środowiska uruchomieniowego w aplikacji**: Pokazuje **dynamiczne polecenia drzewa wizualnego** na pasku narzędzi w oknie głównym aplikacji XAML, która jest debugowana. Ta opcja została wprowadzona w programie Visual Studio 2015 Update 2.

- **Włącz Hot reload języka XAML**: Umożliwia korzystanie z funkcji Hot reload języka XAML z kodem XAML, gdy aplikacja jest uruchomiona. (Ta funkcja była wcześniej nazywana "Edytuj i Kontynuuj" XAML ")

**Włącz narzędzia diagnostyczne podczas debugowania**: Okno **Narzędzia diagnostyczne** pojawia się podczas debugowania.

**Pokaż czas, który upłynął element PerfTip dla podczas debugowania**: W oknie kod jest wyświetlany czas, który upłynął podczas debugowania danego wywołania metody.

**Włącz funkcję Edytuj i Kontynuuj**: Włącza funkcję Edytuj i Kontynuuj podczas debugowania.

- **Włącz natywną edycję i Kontynuuj**: Podczas debugowania kodu natywnego C++ można użyć funkcji Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Zastosuj zmiany przy kontynuowaniu (tylko kod natywny)** : Program Visual Studio automatycznie kompiluje i stosuje wszelkie zaległe zmiany kodu, które zostały wykonane podczas kontynuowania procesu ze stanu przerwania. Jeśli nie jest zaznaczone, można wybrać opcję zastosowania zmian za pomocą elementu **Zastosuj zmiany kodu** w menu **Debuguj** .

- **Ostrzegaj o nieodświeżonym kodzie (tylko kod natywny)** :   Otrzymuj ostrzeżenia dotyczące nieodświeżonego kodu.

**Pokaż przycisk Uruchom do kliknięcia w edytorze podczas debugowania**: Gdy ta opcja jest zaznaczona, podczas debugowania zostanie wyświetlony przycisk [Uruchom do kliknięcia](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) .

**Automatycznie zamknij konsolę po zatrzymaniu debugowania**: Informuje program Visual Studio, aby zamknąć konsolę na końcu sesji debugowania.

::: moniker range=">= vs-2019" 
**Włącz szybką ocenę wyrażeń (tylko zarządzane)** : Umożliwia debugerowi podejmowanie prób szybszej oceny przez symulowanie wykonywania prostych właściwości i metod.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opcje dostępne we wcześniejszych wersjach programu Visual Studio

Jeśli używasz starszej wersji programu Visual Studio, niektóre dodatkowe opcje mogą być obecne.

**Włącz asystenta wyjątków**: Dla kodu zarządzanego, włącza asystenta wyjątków. Począwszy od programu Visual Studio 2017, pomocnik wyjątków zastąpił asystenta wyjątków.

**Odwinięcie stosu wywołań w przypadku nieobsługiwanych wyjątków**: Powoduje, że okno **stos wywołań** wycofa stos wywołań do punktu przed wystąpieniem nieobsługiwanego wyjątku.

**Ostrzegaj, jeśli nie ma symboli podczas uruchamiania (tylko kod natywny)** : Wyświetla okno dialogowe ostrzeżenia podczas debugowania programu, dla którego debuger nie ma informacji o symbolach.

**Ostrzegaj, jeśli debugowanie skryptów jest wyłączone przy uruchomieniu**: Wyświetla okno dialogowe ostrzeżenia, gdy debuger jest uruchamiany z wyłączonym debugowaniem skryptów.

**Użyj natywnego trybu zgodności**: Po wybraniu tej opcji debuger używa programu Visual Studio 2010 Native Debugger zamiast nowego debugera natywnego.

- Użyj tej opcji, gdy debugujesz kod C++ .NET, ponieważ nowy aparat debugowania nie obsługuje oceniania wyrażeń programu .NET C++ . Jednak włączenie macierzystego trybu zgodności wyłącza wiele funkcji, które są zależne od bieżącej implementacji debugera do działania. Na przykład starszy aparat nie ma wielu wizualizatorów dla wbudowanych typów, takich jak `std::string` w projektach programu Visual Studio 2015.   W takich przypadkach należy używać projektów Visual Studio 2013.

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)

---
title: Ogólne, debugowanie, okno dialogowe Opcje | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 29b730bacd589e7b42b9f87086eda91d9e199622
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59504422"
---
# <a name="general-debugging-options"></a>Ogólne opcje debugowania

Aby ustawić opcje debugera programu Visual Studio, wybierz **narzędzia** > **opcje**, a następnie w obszarze **debugowanie** zaznacz lub usuń zaznaczenie pola wyboru obok pozycji  **Ogólne** opcje. Można przywrócić wszystkie ustawienia domyślne przy użyciu **narzędzia** > **Import i eksport ustawień** > **Resetuj wszystkie ustawienia**. Aby zresetować podzbioru ustawień, należy zapisać ustawienia za pomocą **Kreatora importowania i eksportowania ustawień** przed wprowadzeniem zmian, które mają zostać przetestowane, następnie zaimportuj zapisane ustawienia później.

Można ustawić następujące **ogólne** opcje:

**Pytaj przed usunięciem wszystkich punktów przerwania**: Wymaga potwierdzenia przed ukończeniem **Usuń wszystkie punkty przerwania** polecenia.

**Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu**: Jednocześnie przerywa wszystkie procesy, w których jest dołączony debuger, gdy występuje przerwa.

**Przerwij, gdy wyjątki przekroczą granice AppDomain lub granice zarządzane/macierzyste**: Podczas debugowania zarządzanego lub mieszanym, środowisko uruchomieniowe języka wspólnego może przechwytywać wyjątki, które przecinają granice domen aplikacji lub granice zarządzane/macierzyste, gdy są spełnione następujące warunki:

1. Kiedy kod macierzysty wywołuje kod zarządzany za pomocą COM Interop a zarządzany kod zgłasza wyjątek. Zobacz [wprowadzenie do COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Gdy kodu zarządzanego uruchomionego w domenie aplikacji 1 wywołuje kod zarządzany w domenie aplikacji, 2, a kodw aplikacji Domena 2 zgłasza wyjątek. Zobacz [programowanie z domenami aplikacji](/dotnet/articles/framework/app-domains/index).

3. Gdy kod wywołuje funkcję przy użyciu odbicia, i zgłasza wyjątek, tej funkcji. Zobacz [odbicia](/dotnet/framework/reflection-and-codedom/reflection).

W warunkach, 2 i 3, wyjątek jest czasami zgłoszony przez kod zarządzany w `mscorlib` , a nie za środowiska uruchomieniowego języka wspólnego. Ta opcja nie wpływa na przerwanie w wyjątkach przechwyconych przez `mscorlib`.

**Włącz debugowanie na poziomie adresów**: Włącza zaawansowane funkcje debugowania na poziomie adresów ( **dezasemblacji** oknie **rejestruje** okna, a punkty przerwania adresów).

- **Pokaż dezasemblację, jeśli źródło jest niedostępne**:   Jest automatycznie wyświetlana **dezasemblacji** okna podczas debugowania kodu, dla którego źródło jest niedostępne.

**Włącz filtry punktów przerwania**: Umożliwia ustawiania filtrów punktów przerwania, tak że wpływają one tylko określone procesy, wątki lub komputery.

**Użyj nowego pomocnika wyjątków**: Umożliwia pomocnika wyjątków, która zastępuje Asystenta wyjątków. (Pomocnika wyjątków jest obsługiwana w programie Visual Studio 2017)

> [!NOTE]
> Dla kodu zarządzanego, ta opcja był wcześniej nazywany programem **Włącz Asystenta wyjątków** .

**Włącz opcję tylko mój kod**: Debuger wyświetla i kroki kod użytkownika ("Mój kod"), ignorując kod systemowy i inny kod, który zoptymalizowano lub w którym nie ma symboli debugowania.

- **Ostrzegaj w przypadku braku kodu użytkownika przy uruchomieniu (tylko kod zarządzany)**:   Gdy debugowanie się rozpocznie się za pomocą włączono opcję tylko mój kod, opcja ta ostrzega, jeśli brak kodu użytkownika ("Mój kod").

**Włączyć program .NET Framework krokowe wykonywanie źródła**: Pozwala debugerowi na wkroczenie do źródła .NET Framework. Włączenie tej opcji spowoduje automatyczne wyłączenie tylko mój kod. Symbole środowiska .NET framework będą pobierane do lokalizacji pamięci podręcznej. Zmienić lokalizację pamięci podręcznej za pomocą **opcje** okno dialogowe **debugowanie** kategorii **symbole** strony.

**Przekrocz nad właściwościami i operatorami (tylko kod zarządzany)**: Sprawia, że debuger wchodzi we właściwości i operatory w kodzie zarządzanym.

**Włącz obliczanie właściwości i inne niejawne wywołania funkcji**: Włącza funkcję automatycznej oceny właściwości i niejawne funkcja wywołuje w oknach zmiennych i **QuickWatch** okno dialogowe.

- **Wywołaj funkcję konwersji ciągu na obiektach w oknach zmiennych (C# i tylko kod JavaScript)**: Wykonuje wywołanie niejawnej konwersji ciągu podczas szacowania wartości obiektów w oknach zmiennych. Wynik jest wyświetlany jako ciąg, nie nazwę typu. Dotyczy to tylko podczas debugowania kodu C#. To ustawienie może być zastąpiona przez atrybut DebuggerDisplay (zobacz [korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Włącz obsługę serwera źródłowego**: Nakazuje debugerowi programu Visual Studio pobranie plików źródłowych z serwerów źródłowych, które implementują SrcSrv (`srcsrv.dll`) protokołu. Team Foundation Server i Debugging Tools for Windows to dwa serwery źródłowe implementujące ten protokół. Aby uzyskać więcej informacji o konfiguracji SrcSrv, zobacz [SrcSrv](/windows-hardware/drivers/debugger/srcsrv) dokumentacji. Ponadto zobacz [określanie plików symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Ponieważ czytania *.pdb* plików może wykonywać dowolny kod w plikach, upewnij się, że masz zaufanie do serwera.

- **Drukowanie komunikatów diagnostycznych serwera źródłowego w oknie danych wyjściowych**:   Po włączeniu obsługi serwera źródłowego, to ustawienie powoduje włączenie ekranu diagnostycznego.

- **Zezwalaj serwerowi źródłowemu na częściowo zaufane zestawy (tylko kod zarządzany)**:   Po włączeniu obsługi serwera źródłowego, ustawienie to zastępuje domyślne zachowanie niepobierania źródeł dla zestawów częściowej relacji zaufania.

- **Zawsze uruchamiaj niezaufane polecenia serwera źródłowego bez monitowania użytkownika o**:   Po włączeniu obsługi serwera źródłowego, ustawienie to zastępuje domyślne zachowanie monitowania użytkownika podczas uruchamiania polecenia niezaufanych.

**Włącz obsługę Source Link**: Informuje debuger programu Visual Studio w celu pobrania plików źródłowych dla *.pdb* pliki, które zawierają informacje o Linku źródłowego. Aby uzyskać więcej informacji dotyczących Linku źródłowego, zobacz [określenie linku źródłowego](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
>  Ponieważ Link źródłowy zostanie pobrany plików przy użyciu protokołu http lub https, upewnij się, że ufasz *.pdb* pliku.

- **Należą do uwierzytelniania usługi Git Credential Manager dla wszystkich żądań dotyczących Linku źródłowego**:   Obsługa Linku źródłowego jest włączona, gdy żądanie Linku źródłowego niepowodzenia uwierzytelniania, Visual Studio wywołuje program Git Credential Manager.

**Zaznaczanie całego wiersza dla punktów przerwania i bieżącej instrukcji (tylko C++)**: Gdy debuger wyróżnia punkt przerwania lub bieżącą instrukcję, wyróżnia cały wiersz.

**Wymagaj plików źródłowych Aby dokładnie dopasować oryginalną wersję**: Nakazuje debugerowi sprawdzenie, czy plik źródłowy jest zgodny z wersją kodu źródłowego użytego do utworzenia pliku wykonywalnego, który debugujesz. Jeśli wersja nie jest zgodna, wyświetlany jest monit o znalezienie pasującego źródła. Jeśli zgodne źródło nie zostanie znaleziony, nie można wyświetlić kodu źródłowego podczas debugowania.

**Przekieruj wszystkie dane wyjściowe okna tekstowego do okna bezpośredniego**: Wysyła wszystkie komunikaty debugera, które normalnie pojawiają się w **dane wyjściowe** okna **bezpośrednie** okna zamiast tego.

**Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych**: Wyłącza wszystkie dostosowania widoku struktury obiektu. Aby uzyskać więcej informacji na temat dostosowania widoków, zobacz [Tworzenie niestandardowych widoków obiektów .managed](../debugger/create-custom-views-of-dot-managed-objects.md).

**Pomijanie optymalizacji JIT przy ładowaniu modułu (tylko kod zarządzany)**: Wyłącza optymalizację JIT kodu zarządzanego, gdy moduł jest załadowany a JIT kompilowana w czasie, gdy jest dołączony debuger. Wyłączenie optymalizacji może ułatwić debugowanie pewnych problemów, ale kosztem wydajności. Jeśli używasz tylko mój kod, pomijanie JIT optymalizacji może spowodować niebędący kodem użytkownika do wyświetlania jako kod użytkownika ("Mój kod"). Aby uzyskać więcej informacji, zobacz [JIT Optymalizacja i debugowanie](../debugger/jit-optimization-and-debugging.md).

**Włącz debugowanie kodu JavaScript dla platformy ASP.NET (przeglądarki Chrome, krawędzi i programu Internet Explorer)**: Włącza debugera skryptów w przypadku aplikacji ASP.NET. Przy pierwszym użyciu w przeglądarce Chrome może być konieczne Zaloguj się do przeglądarki, aby włączyć rozszerzenia dla programu Chrome, które zostały zainstalowane. Wyłącz tę opcję, aby przywrócić starsze zachowanie.

**Włącz narzędzia deweloperskie przeglądarki Edge dla aplikacji JavaScript platformy uniwersalnej systemu Windows (wersja eksperymentalna)**: Umożliwia developer tools dla aplikacji JavaScript platformy uniwersalnej systemu Windows w programie Edge.

**Włącz starsze debugera języka JavaScript w przeglądarce Chrome dla platformy ASP.NET**: Włącza starsze debugera skryptów JavaScript w przeglądarce Chrome dla aplikacji ASP.NET. Przy pierwszym użyciu w przeglądarce Chrome może być konieczne Zaloguj się do przeglądarki, aby włączyć rozszerzenia dla programu Chrome, które zostały zainstalowane.

**Użyj eksperymentalne sposób, aby uruchomić debugowanie kodu JavaScript w przeglądarce Chrome, podczas uruchamiania programu Visual Studio jako Administrator**: Zawiera informacje dla programu Visual Studio, aby spróbować nowy sposób uruchamiania dla programu Chrome podczas debugowania kodu JavaScript.

**Ładuj eksporty dll (tylko natywne)**: Ładuje tabele eksportu bibliotek dll. Informacje o symbolach tabel eksportu biblioteki dll może być przydatne, jeśli pracujesz z Windows wiadomości, procedur Windows (WindowProcs), obiektami COM, lub organizowanie lub dowolną biblioteką dll, dla której nie masz symboli. Odczytywanie pliku dll informacji o eksportowaniu pewne nadmiarowe obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.

Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki dll, użyj `dumpbin /exports`. Symbole są dostępne dla każdej biblioteki dll systemu 32-bitowego. Czytając `dumpbin /exports` danych wyjściowych, możesz zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji tabel eksportu biblioteki dll, może pojawić się obcięte gdzie indziej w debugerze. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin/EXPORTS](/cpp/build/reference/dash-exports).

**Pokaż równoległych stosów od dołu do góry diagram**: Kontroluje kierunek, w którym stosy są wyświetlane w **stosów równoległych** okna.

**Ignoruj wyjątki dostępu do pamięci procesora GPU, jeśli zapisane dane nie zmieniły wartości**: Ignoruje Sytuacje wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie zmieniły. Aby uzyskać więcej informacji, zobacz [debugowania kodu GPU](../debugger/debugging-gpu-code.md).

**Użyj trybu zgodności zarządzanej**: Zastępuje domyślny aparat starszą wersją, aby włączyć te scenariusze debugowania:

- Używasz języka .NET Framework innego niż C#, Visual Basic lub F# zapewniający własny Ewaluator wyrażeń (dotyczy to również C++sposób niezamierzony).

- Chcesz włączyć Edytuj i Kontynuuj dla projektów C++ podczas debugowania w trybie mieszanym.

> [!NOTE]
> Trybu, wybierając zgodności zarządzanej wyłącza niektóre funkcje, które są zaimplementowane tylko w domyślnym aparacie debugowania. Starego aparatu debugowania zostało zastąpione w programie Visual Studio 2012.

**Użyj starszego C# i ewaluatory wyrażeń VB**: Debuger użyje programu Visual Studio 2013 C# lub ewaluatory wyrażeń języka Visual Basic zamiast ewaluatory wyrażeń opartych na programie Visual Studio 2015 Roslyn.

**Ostrzegaj, gdy niestandardowe wizualizatory debugera względem potencjalnie niebezpiecznych procesów (tylko kod zarządzany)**: Program Visual Studio ostrzega o tym, kiedy używasz wizualizatora niestandardowego debugera działający kod w debugowanym procesie, ponieważ może być uruchomiony niebezpieczny kod.

**Włącz alokatora sterty debugowania Windows (tylko natywne)**: Włącza na stercie systemu windows, lepszą diagnostykę sterty. Włączenie tej opcji będzie mieć wpływ na wydajność debugowania.

**Włączanie debugowania interfejsu użytkownika narzędzia dla XAML**: Dynamiczne drzewo wizualne i windows Live Eksplorowanie właściwość pojawi się po rozpoczęciu debugowania (**F5**) typu obsługiwanych projektu. Aby uzyskać więcej informacji, zobacz [właściwości sprawdzić XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md).

- **Wyświetl podgląd wybranych elementów w dynamicznym drzewie wizualnym**:   Element XAML, którego kontekst jest zaznaczona, jest również wybrany w **dynamiczne drzewo wizualne** okna.

- **Pokaż narzędzia środowiska uruchomieniowego w aplikacji**: Pokazuje **dynamiczne drzewo wizualne** polecenia na pasku narzędzi w oknie głównym aplikacji XAML, która jest debugowana. Ta opcja została wprowadzona w Visual Studio 2015 Update 2.

- **Włącz XAML Edytuj i Kontynuuj**:   Umożliwia używanie funkcji Edytuj i Kontynuuj funkcji przy użyciu kodu XAML.

**Włącz narzędzia diagnostyczne podczas debugowania**: **Narzędzia diagnostyczne** zostanie wyświetlone okno podczas debugowania.

**Podczas debugowania Pokaż element perftip dla czasu upłynęło**: W oknie Kod wyświetla czas wywołania danej metody podczas debugowania.

**Włącz funkcję Edytuj i Kontynuuj**: Włącza funkcję Edytuj i Kontynuuj podczas debugowania.

- **Włącz natywną funkcję Edytuj i Kontynuuj**: Możesz użyć edycji i kontynuowania funkcji podczas debugowania kodu natywnego języka C++. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Zastosuj zmiany przy kontynuowaniu (tylko natywne)**: Program Visual Studio kompiluje i automatycznie stosuje żadnych zmian w kodzie oczekujących, wprowadzone podczas kontynuując proces w stanie przerwania. Jeśli nie jest zaznaczone, możesz zastosować zmiany, przy użyciu **zastosowanie zmian kodu** w obszarze **debugowania** menu.

- **Ostrzeżenie o nieodświeżonym kodzie (tylko natywne)**:   Pobierz ostrzeżenia o nieodświeżonym kodzie.

**Pokaż Uruchom do kliknięcia przycisku w edytorze podczas debugowania**: Gdy ta opcja jest zaznaczona, [uruchamianie do kliknięcia](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) przycisk będzie wyświetlany podczas debugowania.

**Automatycznie Zamknij konsolę, po zatrzymaniu debugowania**: Zawiera informacje dla programu Visual Studio, aby zamknąć konsolę na końcu sesji debugowania.

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opcje dostępne w starszych wersjach programu Visual Studio

Jeśli używasz starszej wersji programu Visual Studio może istnieć pewne dodatkowe opcje.

**Włącz Asystenta wyjątków**: Dla kodu zarządzanego umożliwia Asystenta wyjątków. Począwszy od programu Visual Studio 2017 pomocnika wyjątków zastąpione Asystenta wyjątków.

**Operacja unwind na stosie wywołań dotycząca nieobsłużonych wyjątków**: Powoduje, że **stos wywołań** okna, aby wycofać stos wywołań do punktu przed wystąpieniem nieobsługiwanego wyjątku.

**Ostrzegaj, jeśli brak symboli podczas uruchamiania (tylko natywne)**: Wyświetla okno dialogowe ostrzeżenia podczas debugowania programu, dla którego debuger nie ma żadnych informacji o symbolach.

**Ostrzegaj, jeśli debugowanie skryptów jest wyłączone w momencie uruchomienia**: Wyświetla okno dialogowe ostrzeżenia, gdy debuger jest uruchamiany z wyłączonym debugowaniem skryptów.

**Użyj trybu zgodności natywnych**: Gdy ta opcja jest zaznaczona, debuger używa macierzystym debugerze programu Visual Studio 2010 zamiast nowej debuger natywny.

- Użyj tej opcji podczas debugowania kodu w języku C++ platformy .NET, ponieważ nowy aparat debugowania nie obsługuje oceny wyrażeń języka C++ platformy .NET. Włączanie natywnego trybu zgodności wyłącza jednak wiele funkcji, które są zależne od bieżącej implementacji debugera do działania. Na przykład starszego aparatu nie posiada wiele wizualizatorów, dla wbudowanych typów, takich jak `std::string` w projektach programu Visual Studio 2015.   Projekty programu Visual Studio 2013 na użytek optymalne środowisko debugowania w tych przypadkach.

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
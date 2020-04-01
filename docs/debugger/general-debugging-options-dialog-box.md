---
title: Ogólne, debugowanie, okno dialogowe Opcje | Dokumenty firmy Microsoft
ms.date: 11/12/2019
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
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472694"
---
# <a name="general-debugging-options"></a>Ogólne opcje debugowania

Aby ustawić opcje debugera programu Visual Studio, wybierz pozycję**Opcje** **narzędzi** > , a następnie w obszarze **Debugowanie** zaznacz lub usuń zaznaczenie pól obok opcji **ogólne.** Wszystkie ustawienia domyślne można przywrócić za pomocą ustawień**importu i eksportu** >  **Narzędzia** > **Resetuj wszystkie ustawienia**. Aby zresetować podzbiór ustawień, zapisz ustawienia za pomocą **Kreatora importu i eksportu** przed wprowadzeniem zmian, które chcesz przetestować, a następnie zaimportuj zapisane ustawienia.

Można ustawić następujące opcje **ogólne:**

**Zapytaj przed usunięciem wszystkich punktów przerwania:** Wymaga potwierdzenia przed wykonaniem polecenia **Usuń wszystkie punkty przerwania.**

**Przerywanie wszystkich procesów, gdy jeden proces zostanie przerwany:** Jednocześnie przerywa wszystkie procesy, do których jest dołączony debuger, gdy wystąpi przerwa.

**Przerwij, gdy wyjątki przekraczają appdomain lub granice zarządzane/macierzyste:** W debugowaniu w trybie zarządzanym lub mieszanym środowisko wykonawcze języka wspólnego może przechwytywać wyjątki, które przekraczają granice domeny aplikacji lub granice zarządzane/macierzyste, gdy spełnione są następujące warunki:

1. Gdy kod macierzysty wywołuje kod zarządzany przy użyciu com interop i kod zarządzany zgłasza wyjątek. Zobacz [Wprowadzenie do COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Gdy kod zarządzany uruchomiony w domenie aplikacji 1 wywołuje kod zarządzany w domenie aplikacji 2, a kod w domenie aplikacji 2 zgłasza wyjątek. Zobacz [Programowanie z domenami aplikacji](/dotnet/articles/framework/app-domains/index).

3. Gdy kod wywołuje funkcję przy użyciu odbicia, a ta funkcja zgłasza wyjątek. Zobacz [Odbicie](/dotnet/framework/reflection-and-codedom/reflection).

W warunkach 2 i 3 wyjątek jest `mscorlib` czasami przechwytyny przez kod zarządzany w, a nie przez środowisko uruchomieniowe języka wspólnego. Ta opcja nie ma wpływu na `mscorlib`łamanie wyjątków przechwyconych przez .

**Włącz debugowanie**na poziomie adresu: Włącza zaawansowane funkcje debugowania na poziomie adresu (okno **Demontaż,** okna **Rejestry** i punkty przerwania adresu).

- **Pokaż demontaż, jeśli źródło nie jest dostępne:** Automatycznie pokazuje okno **Demontaż** podczas debugowania kodu, dla którego źródło jest niedostępne.

**Włącz filtry punktów przerwania:** Umożliwia ustawienie filtrów w punktach przerwania, tak aby miały one wpływ tylko na określone procesy, wątki lub komputery.

**Użyj nowego Pomocnika wyjątków:** Włącza Pomocnika wyjątku, który zastępuje asystenta wyjątków. (Pomocnik wyjątków jest obsługiwany począwszy od programu Visual Studio 2017)

> [!NOTE]
> W przypadku kodu zarządzanego ta opcja była wcześniej nazywana **Włączanie asystenta wyjątków** .

**Włącz tylko mój kod:** Debuger wyświetla i kroki do kodu użytkownika ("Mój kod") tylko, ignorując kod systemu i inny kod, który jest zoptymalizowany lub który nie ma symboli debugowania.

- **Ostrzegaj, jeśli żaden kod użytkownika podczas uruchamiania (tylko zarządzany)**: Gdy debugowanie zaczyna się z włączoną opcją Tylko mój kod, ta opcja ostrzega, jeśli nie ma kodu użytkownika ("Mój kod").

**Włącz stepping źródła programu .NET Framework:** Umożliwia debugerowi krok do źródła .NET Framework. Włączenie tej opcji automatycznie wyłącza tylko mój kod. Symbole programu .NET Framework zostaną pobrane do lokalizacji pamięci podręcznej. Zmienianie lokalizacji pamięci podręcznej za pomocą okna dialogowego **Opcje,** **Debugowanie,** strona **Symbole.**

**Krok nad właściwości i operatorów (tylko zarządzane)**: Zapobiega debugera z przechodzenia do właściwości i operatorów w kodzie zarządzanym.

**Włącz ocenę właściwości i inne wywołania funkcji niejawnych:** Włącza automatyczną ocenę właściwości i wywołania funkcji niejawnych w oknach zmiennych i oknie dialogowym **QuickWatch.**

- **Funkcja konwersji ciągu wywołania na obiektach w oknach zmiennych (tylko C# i JavaScript)**: Wykonuje niejawne wywołanie konwersji ciągu podczas oceny obiektów w oknach zmiennych. Wynik jest wyświetlany jako ciąg zamiast nazwy typu. Dotyczy tylko podczas debugowania w kodzie języka C#. To ustawienie może zostać zastąpione przez atrybut DebuggerDisplay (zobacz [Użycie atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Włącz obsługę serwera źródłowego:** Informuje debuger programu Visual Studio, aby uzyskać`srcsrv.dll`pliki źródłowe z serwerów źródłowych, które implementują protokół SrcSrv ( ). Team Foundation Server i Narzędzia debugowania dla systemu Windows to dwa serwery źródłowe, które implementują protokół. Aby uzyskać więcej informacji na temat konfiguracji SrcSrv, zobacz dokumentację [SrcSrv.](/windows-hardware/drivers/debugger/srcsrv) Ponadto zobacz [Określanie symbolu (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Ponieważ odczyt plików *pdb* może wykonywać dowolny kod w plikach, upewnij się, że ufasz serwerowi.

- **Komunikaty diagnostyczne serwera źródła wydruku do okna Dane wyjściowe**: Gdy obsługa serwera źródłowego jest włączona, to ustawienie włącza wyświetlanie diagnostyczne.

- **Zezwalaj na serwer źródłowy dla zespołów częściowego zaufania (tylko zarządzane)**: Gdy obsługa serwera źródłowego jest włączona, to ustawienie zastępuje domyślne zachowanie nie pobieranie źródeł dla zespołów częściowego zaufania.

- **Zawsze uruchamiaj niezaufane polecenia serwera źródłowego bez monitowania:** Gdy obsługa serwera źródłowego jest włączona, to ustawienie zastępuje domyślne zachowanie monitowania podczas uruchamiania niezaufanego polecenia.

**Włącz obsługę łącza źródłowego:** Nakazuje debugerowi programu Visual Studio, aby pobrać pliki źródłowe dla plików *pdb* zawierających informacje o łączu źródłowym. Aby uzyskać więcej informacji na temat łącza źródłowego, zobacz [specyfikację łącza źródłowego](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Ponieważ source link będzie pobierać pliki przy użyciu protokołu http lub https, upewnij się, że ufasz plikowi *pdb.*

- **Powrót do uwierzytelniania Menedżera poświadczeń Git dla wszystkich żądań łącza źródłowego:** gdy obsługa łącza źródłowego jest włączona, a żądanie łącza źródłowego nie powiedzie się uwierzytelnieniu, program Visual Studio wywołuje Menedżera poświadczeń Git.

**Wyróżnij cały wiersz dla punktów przerwania i bieżącej instrukcji (tylko C++)**: Gdy debuger podświetla punkt przerwania lub bieżącą instrukcję, wyróżnia cały wiersz.

**Wymagaj plików źródłowych, aby dokładnie dopasować oryginalną wersję:** Informuje debugera, aby sprawdzić, czy plik źródłowy pasuje do wersji kodu źródłowego używanego do tworzenia pliku wykonywalnego, który debugujesz. Gdy wersja nie jest zgodna, zostanie wyświetlony monit o znalezienie pasującego źródła. Jeśli pasujące źródło nie zostanie znalezione, kod źródłowy nie będzie wyświetlany podczas debugowania.

**Przekieruj cały tekst okna dane wyjściowe do okna Natychmiastowe:** Wysyła wszystkie komunikaty debugera, które zwykle pojawiają się w oknie **Dane wyjściowe** do okna **Natychmiastowe.**

**Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych:** Wyłącza wszystkie dostosowania widoku struktury obiektów. Aby uzyskać więcej informacji na temat dostosowań widoku, zobacz [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-managed-objects.md).

**Pomijanie optymalizacji JIT przy obciążeniu modułu (tylko zarządzane)**: Wyłącza optymalizację JIT kodu zarządzanego, gdy moduł jest ładowany, a JIT jest kompilowany, gdy debuger jest dołączony. Wyłączenie optymalizacji może ułatwić debugowanie niektórych problemów, chociaż kosztem wydajności. Jeśli używasz tylko mój kod, pomijanie optymalizacji JIT może spowodować, że kod niebędący użytkownikiem pojawi się jako kod użytkownika ("Mój kod"). Aby uzyskać więcej informacji, zobacz [Optymalizacja JIT i debugowanie](../debugger/jit-optimization-and-debugging.md).

**Włącz debugowanie javascript dla ASP.NET (Chrome, Microsoft Edge i IE)**: Włącza debuger skryptów dla ASP.NET aplikacji. Przy pierwszym użyciu w Chrome może być konieczne zalogowanie się do przeglądarki, aby włączyć zainstalowane rozszerzenia Chrome. Wyłącz tę opcję, aby powrócić do starszego zachowania.

**Włącz narzędzia programistyczne edge dla aplikacji Platformy Uniwersalnej Platformy Uniwersalnej Systemu Windows (Experimental)**: Umożliwia tworzenie narzędzi programowych dla aplikacji Platformy Uniwersalnej Platformy Uniwersalnej w programie Microsoft Edge.

**Włącz starszy debuger Chrome JavaScript dla ASP.NET:** Włącza starszy debuger skryptów Chrome JavaScript dla ASP.NET aplikacji. Przy pierwszym użyciu w Chrome może być konieczne zalogowanie się do przeglądarki, aby włączyć zainstalowane rozszerzenia Chrome.

**Użyj eksperymentalnego sposobu uruchamiania debugowania JavaScript w Chrome podczas uruchamiania programu Visual Studio jako administrator:** nakazuje programowi Visual Studio wypróbowanie nowego sposobu uruchamiania Chrome podczas debugowania JavaScript.

**Eksport dll obciążenia (tylko macierzysty)**: Ładuje tabele eksportu biblioteki DLL. Informacje o symbolach z tabel eksportu biblioteki DLL mogą być przydatne, jeśli pracujesz z wiadomościami systemu Windows, procedurami systemu Windows (WindowProcs), obiektami COM lub organizowaniem lub dowolną biblioteką DLL, dla której nie masz symboli. Odczytywanie informacji eksportu dll obejmuje pewne obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.

Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki DLL, użyj programu `dumpbin /exports`. Symbole są dostępne dla dowolnej 32-bitowej biblioteki dll systemu. Odczytając `dumpbin /exports` dane wyjściowe, można zobaczyć dokładną nazwę funkcji, w tym znaki niealnumericzne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji z tabel eksportu bibliotek dll mogą być obcięty w innym miejscu debugera. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin /exports](/cpp/build/reference/dash-exports).

**Pokaż diagram stosów równoległych oddolnie**: Określa kierunek, w którym stosy są wyświetlane w oknie **Stosy równoległe.**

**Ignoruj wyjątki dostępu do pamięci GPU, jeśli zapisane dane nie zmieniły wartości:** Ignoruje warunki wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie zostały zmienić. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md).

**Użyj trybu zgodności zarządzanej:** Zastępuje domyślny aparat debugowania starszą wersją, aby włączyć następujące scenariusze:

- Używasz języka .NET innego niż C#, Visual Basic lub F#, który zapewnia własny program oceniający wyrażenie (w tym C++/CLI).

- Chcesz włączyć edycji i kontynuuj dla projektów C++ podczas debugowania w trybie mieszanym.

> [!NOTE]
> Wybranie trybu zgodności zarządzanej powoduje wyłączenie niektórych funkcji, które są implementowane tylko w domyślnym silniku debugowania. Starszy aparat debugowania został zastąpiony w programie Visual Studio 2012.

**Użyj starszych oceniających wyrażenie C# i VB:** Debuger użyje visual studio 2013 C# lub Visual Basic oceniających wyrażenie, a nie visual studio 2015 roslyn oceniających wyrażenie.

**Ostrzegaj podczas korzystania z niestandardowych wizualizatorów debugera przed potencjalnie niebezpiecznymi procesami (tylko zarządzane)**: Visual Studio ostrzega, gdy używasz niestandardowego wizualizatora debugera, który jest uruchomiony kod w procesie debugowania, ponieważ może być uruchomiony niebezpieczny kod.

**Włącz alokator sterty debugowania systemu Windows (tylko natywny)**: Włącza sterty debugowania systemu Windows, aby poprawić diagnostykę sterty. Włączenie tej opcji wpłynie na wydajność debugowania.

**Włącz narzędzia debugowania interfejsu użytkownika dla XAML:** Aktywne drzewo wizualne i okna Eksploruj właściwości na żywo pojawią się po uruchomieniu debugowania **(F5)** obsługiwanego typu projektu. Aby uzyskać więcej informacji, zobacz [Inspekcja właściwości XAML podczas debugowania](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Podgląd wybranych elementów w aktywnej wersji wizualnej:** Element XAML, którego kontekst jest zaznaczony, jest również zaznaczony w oknie **Aktywne drzewo wizualne.**

- **Pokaż narzędzia środowiska uruchomieniowego w aplikacji:** Pokazuje polecenia **aktywne drzewo wizualne** na pasku narzędzi w oknie głównym aplikacji XAML, która jest debugowana. Ta opcja została wprowadzona w programie Visual Studio 2015 Update 2.

- **Włącz ponowne ładowanie gorąca XAML:** Umożliwia korzystanie z funkcji XAML Hot Reload z kodem XAML, gdy aplikacja jest uruchomiona. (Ta funkcja była wcześniej nazywana "Edycją XAML i Kontynuuj")

::: moniker range=">= vs-2019" 
- **Włącz tylko mój kod XAML:** Począwszy od programu Visual Studio 2019 w wersji 16.4, **aktywne drzewo wizualne** domyślnie pokazuje tylko XAML, który jest klasyfikowany jako kod użytkownika. Jeśli ta opcja zostanie wyłączona, w narzędziu pojawi się cały wygenerowany kod XAML.

- **Wyłączanie trybu zaznaczenia po wybraniu elementu** Począwszy od programu Visual Studio 2019 w wersji 16.4 przycisk selektora elementu paska narzędzi w aplikacji (**Włącz zaznaczenie**) wyłącza się po wybraniu elementu. Jeśli ta opcja zostanie wyłączyna, zaznaczenie elementu pozostanie włączone do momentu ponownego kliknięcia przycisku paska narzędzi w aplikacji.
::: moniker-end

**Włącz narzędzia diagnostyczne podczas debugowania:** Podczas debugowania pojawia się okno **Narzędzia diagnostyczne.**

**Pokaż upomnienie czasu podczas debugowania:** Okno kodu wyświetla czas, jaki upłynął od danego wywołania metody podczas debugowania.

**Włącz edycję i kontynuuj:** Włącza funkcję Edycji i Kontynuuj podczas debugowania.

- **Włącz edycję natywną i kontynuuj:** Można użyć funkcji Edytuj i Kontynuuj podczas debugowania natywnego kodu C++. Aby uzyskać więcej informacji, zobacz [Edytowanie i kontynuowanie (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Zastosuj zmiany na kontynuować (tylko macierzyste)**: Visual Studio automatycznie kompiluje i stosuje wszelkie zmiany kodu zaległe, które zostały wprowadzone podczas kontynuowania procesu ze stanu przerwania. Jeśli nie jest zaznaczona, można zastosować zmiany za pomocą elementu **Zastosuj zmiany kodu** w menu **Debugowanie.**

- **Ostrzegaj o nieaktualnym kodzie (tylko natywny)**: Uzyskaj ostrzeżenia dotyczące przestarzałego kodu.

**Pokaż przycisk Uruchom, aby kliknąć w edytorze podczas debugowania:** Po wybraniu tej opcji przycisk [Uruchom, aby kliknąć,](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) zostanie wyświetlony podczas debugowania.

**Automatyczne zamykanie konsoli po zatrzymaniu debugowania:** Informuje program Visual Studio, aby zamknąć konsolę na końcu sesji debugowania.

::: moniker range=">= vs-2019"
**Włącz szybką ocenę wyrażeń (tylko zarządzane)**: Umożliwia debugerowi szybszą ocenę poprzez symulowanie wykonywania prostych właściwości i metod.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opcje dostępne w starszych wersjach programu Visual Studio

Jeśli używasz starszej wersji programu Visual Studio, niektóre dodatkowe opcje mogą być obecne.

**Włącz asystenta wyjątków:** Dla kodu zarządzanego włącza asystenta wyjątków. Począwszy od programu Visual Studio 2017 Pomocnik wyjątków zastąpił asystenta wyjątków.

**Odwiń stos wywołań na nieobsłużonych wyjątków:** Powoduje, że okno **stos wywołań,** aby wycofać stos wywołań do punktu przed nieobsługiwać wyjątek.

**Ostrzegaj, jeśli podczas uruchamiania nie ma symboli (tylko natywne):** Wyświetla okno dialogowe z ostrzeżeniem podczas debugowania programu, dla którego debuger nie zawiera żadnych informacji o symbolu.

**Ostrzegaj, jeśli debugowanie skryptu jest wyłączone podczas uruchamiania:** Wyświetla okno dialogowe z ostrzeżeniem, gdy debuger jest uruchamiany z wyłączonym debugowaniem skryptów.

**Użyj trybu zgodności natywnej:** Gdy ta opcja jest zaznaczona, debuger używa natywnego debugera programu Visual Studio 2010 zamiast nowego natywnego debugera.

- Użyj tej opcji podczas debugowania kodu .NET C++, ponieważ nowy aparat debugowania nie obsługuje oceny wyrażeń .NET C++. Jednak włączenie trybu zgodności natywnej wyłącza wiele funkcji, które zależą od bieżącej implementacji debugera do działania. Na przykład starszego aparatu brakuje wiele wizualizatorów `std::string` dla wbudowanych typów, takich jak w projektach programu Visual Studio 2015.   Użyj projektów programu Visual Studio 2013 dla optymalnego środowiska debugowania w tych przypadkach.

## <a name="see-also"></a>Zobacz też

- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)

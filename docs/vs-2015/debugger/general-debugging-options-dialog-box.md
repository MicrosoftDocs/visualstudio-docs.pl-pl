---
title: Ogólne, debugowanie, okno dialogowe Opcje | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2dd7d3f41790fac7a37fc3a98d728757f5bad967
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704677"
---
# <a name="general-debugging-options-dialog-box"></a>Ogólne, debugowanie, okno dialogowe Opcje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Narzędzia / Opcje / Debugowanie / ogólne** strona pozwala ustawić następujące opcje:  
  
 **Pytaj przed usunięciem wszystkich punktów przerwania**  
 Wymaga potwierdzenia przed ukończeniem **Usuń wszystkie punkty przerwania** polecenia.  
  
 **Przerwij wszystkie procesy, gdy jeden proces ulegnie przerwaniu**  
 Jednocześnie przerywa wszystkie procesy, w których jest dołączony debuger, gdy występuje przerwa.  
  
 **Przerwij, gdy wyjątki przekroczą granice AppDomain lub granice zarządzane/macierzyste**  
 Podczas debugowania zarządzanego lub mieszanym, środowisko uruchomieniowe języka wspólnego może przechwytywać wyjątki, które przecinają granice domen aplikacji lub granice zarządzane/macierzyste, gdy są spełnione następujące warunki:  
  
 1\) kiedy kod macierzysty wywołuje kod zarządzany za pomocą COM Interop, i zgłasza wyjątek, kod zarządzany. Zobacz [wprowadzenie do COM Interop](https://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2\) gdy kodu zarządzanego uruchomionego w domenie aplikacji 1 wywołuje kod zarządzany w domenie aplikacji, 2, a kodw aplikacji Domena 2 zgłasza wyjątek. Zobacz [programowanie z domenami aplikacji](https://msdn.microsoft.com/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) gdy kod wywołuje funkcję przy użyciu odbicia, a funkcja zgłasza wyjątek. Zobacz [odbicia](https://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 W 2) i 3), jest czasami wyjątek przez kod zarządzany w `mscorlib` zamiast środowiska uruchomieniowego języka wspólnego. Ta opcja nie wpływa na przerwanie w wyjątkach przechwyconych przez `mscorlib`.  
  
 **Włącz debugowanie na poziomie adresów**  
 Włącza zaawansowane funkcje debugowania na poziomie adresów ( **dezasemblacji** oknie **rejestruje** okna, a punkty przerwania adresów).  
  
 **Pokaż dezasemblację, jeśli źródło jest niedostępne**  
 Jest automatycznie wyświetlana **dezasemblacji** okna podczas próby debugowania kodu, dla którego źródło jest niedostępne.  
  
 **Włącz filtry punktów przerwania**  
 Umożliwia ustawiania filtrów punktów przerwania, tak że wpływają one tylko określone procesy, wątki lub komputery.  
  
 **Włącz Asystenta wyjątków**  
 Tylko dla kodu zarządzanego. Zarządzane wyjątki, Otwórz okno dialogowe Asystenta wyjątków.  Zobacz [Asystenta wyjątków](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Operacja unwind na stosie wywołań dotycząca nieobsłużonych wyjątków**  
 Powoduje, że **stos wywołań** okna, aby wycofać stos wywołań do punktu przed wystąpieniem nieobsługiwanego wyjątku.  
  
 **Włącz opcję tylko mój kod**  
 Debuger wyświetla i kroki kod użytkownika ("Mój kod"), ignorując kod systemowy i inny kod, który zoptymalizowano lub w którym nie ma symboli debugowania.  
  
 **Wyświetlanie wszystkich elementów członkowskich dla obiektów niebędących użytkownikami w oknach zmiennych (tylko Visual Basic)**  
 Włącza wyświetlanie elementów członkowskich niepublicznych w obiektach, które znajdują się w niebędący kodem użytkownika (nie "Mój kod").  
  
 **Ostrzegaj w przypadku braku kodu użytkownika przy uruchomieniu**  
 Gdy debugowanie się rozpocznie się za pomocą włączono opcję tylko mój kod, opcja ta ostrzega, jeśli brak kodu użytkownika ("Mój kod").  
  
 **Włączyć program .NET Framework krokowe wykonywanie źródła**  
 Pozwala debugerowi na wkroczenie do źródła .NET Framework. Włączenie tej opcji spowoduje automatyczne wyłączenie tylko mój kod .NET Framework symbole będą pobierane do lokalizacji pamięci podręcznej. Możesz zmienić lokalizację pamięci podręcznej w **opcje** okno dialogowe **debugowanie** kategorii **symbole** strony.  
  
 **Przekrocz nad właściwościami i operatorami (tylko zarządzany)**  
 Sprawia, że debuger wchodzi we właściwości i operatory w kodzie zarządzanym.  
  
 **Włącz obliczanie właściwości i inne niejawne wywołania funkcji**  
 Włącza funkcję automatycznej oceny właściwości i niejawne funkcja wywołuje w oknach zmiennych i **QuickWatch** okno dialogowe.  
  
 **Wywołaj funkcję konwersji ciągu na obiektach w oknach zmiennych (C# i JavaScript tylko)**  
 Wykonuje wywołanie niejawnej konwersji ciągu podczas szacowania wartości obiektów w oknach zmiennych. W związku z tym że wynik jest wyświetlany jako ciąg, nie nazwę typu. Dotyczy to tylko podczas debugowania kodu C#. To ustawienie może być zastąpiona przez atrybut DebuggerDisplay (zobacz [korzystanie z atrybutu DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Włącz obsługę serwera źródłowego**  
 Nakazuje debugerowi programu Visual Studio pobranie plików źródłowych z serwerów źródłowych, które implementują SrcSrv (`srcsrv.dll`) protokołu. Team Foundation Server i Debugging Tools for Windows to dwa serwery źródłowe implementujące ten protokół. Aby uzyskać więcej informacji o konfiguracji SrcSrv zobacz dokumentację Debugging Tools for Windows. Ponadto zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Ponieważ odczyt plików .pdb może wykonywać dowolny kod w plikach, upewnij się, że masz zaufanie do serwera.  
  
 **Drukowanie komunikatów diagnostycznych serwera źródłowego w oknie danych wyjściowych**  
 Po włączeniu obsługi serwera źródłowego, to ustawienie powoduje włączenie ekranu diagnostycznego.  
  
 **Zezwalaj serwerowi źródłowemu na częściowo zaufane zestawy (tylko kod zarządzany)**  
 Po włączeniu obsługi serwera źródłowego, ustawienie to zastępuje domyślne zachowanie niepobierania źródeł dla zestawów częściowej relacji zaufania.  
  
 **Zaznaczanie całego wiersza dla punktów przerwania i bieżącej instrukcji**  
 Gdy debuger wyróżnia punkt przerwania lub bieżącą instrukcję, wyróżnia cały wiersz.  
  
 **Wymaga plików źródłowych, aby dokładnie dopasować oryginalną wersję**  
 Nakazuje debugerowi sprawdzenie, czy plik źródłowy jest zgodny z wersją kodu źródłowego użytego do utworzenia pliku wykonywalnego, który debugujesz. Jeśli wersja nie jest zgodny, będzie się monit o znalezienie pasującego źródła. Jeśli zgodne źródło nie zostanie znaleziony, nie można wyświetlić kodu źródłowego podczas debugowania.  
  
 **Przekieruj wszystkie dane wyjściowe okna tekstowego do okna bezpośredniego**  
 Wysyła wszystkie komunikaty debugera, które normalnie pojawiają się w **dane wyjściowe** okna **bezpośrednie** okna zamiast tego.  
  
 **Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych**  
 Wyłącza wszystkie dostosowania widoku struktury obiektu. Aby uzyskać więcej informacji na temat dostosowania widoków, zobacz [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Pomijanie optymalizacji JIT przy ładowaniu modułu (tylko zarządzany)**  
 Wyłącza optymalizację JIT kodu zarządzanego, gdy moduł jest załadowany a JIT kompilowana w czasie, gdy jest dołączony debuger. Wyłączenie optymalizacji może ułatwić debugowanie pewnych problemów, ale kosztem wydajności. Jeśli używasz tylko mój kod, pomijanie JIT optymalizacji może spowodować niebędący kodem użytkownika do wyświetlania jako kod użytkownika ("Mój kod").  
  
 **Ostrzegaj, jeśli brak symboli podczas uruchamiania (tylko natywne)**  
 Wyświetla okno dialogowe ostrzeżenia podczas próby debugowania programu, dla którego debuger nie ma żadnych informacji o symbolach.  
  
 **Ostrzegaj, jeśli debugowanie skryptów jest wyłączone przy uruchomieniu**  
 Wyświetla okno dialogowe ostrzeżenia, gdy debuger jest uruchamiany z wyłączonym debugowaniem skryptów.  
  
 **Ładuj eksporty dll**  
 Ładuje tabele eksportu bibliotek dll. Informacje o symbolach tabel eksportu biblioteki dll może być przydatne, jeśli pracujesz z Windows wiadomości, procedur Windows (WindowProcs), obiektami COM, lub organizowanie lub dowolną biblioteką dll, dla której nie masz symboli. Odczytywanie pliku dll informacji o eksportowaniu pewne nadmiarowe obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.  
  
 Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki dll, użyj `dumpbin /exports`. Symbole są dostępne dla każdej biblioteki dll systemu 32-bitowego. Czytając `dumpbin /exports` danych wyjściowych, możesz zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji tabel eksportu biblioteki dll, może pojawić się obcięte gdzie indziej w debugerze. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin/EXPORTS](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Pokaż diagram równoległych stosów od dołu do góry**  
 Kontroluje kierunek, w którym stosy są wyświetlane w **stosów równoległych** okna.  
  
 **Ignoruj wyjątki dostępu do pamięci procesora GPU, jeśli zapisane dane nie zmieniły wartości**  
 Ignoruje Sytuacje wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie zmieniły. Aby uzyskać więcej informacji, zobacz [debugowania kodu GPU](../debugger/debugging-gpu-code.md).  
  
 **Użyj zarządzanego trybu zgodności**  
 Zastępuje domyślny aparat starszą wersją, aby włączyć te scenariusze debugowania:  
  
- Używasz języka .NET Framework innego niż C#, VB, lub F# zapewniający własny Ewaluator wyrażeń (dotyczy to również C++sposób niezamierzony).  
  
- Chcesz włączyć Edytuj i Kontynuuj dla projektów C++ podczas debugowania w trybie mieszanym.  
  
  Należy pamiętać, że wybranie zgodności zarządzanej tryb wyłącza niektóre funkcje, które są zaimplementowane tylko w domyślnym aparacie debugowania.  
  
  **Użyj trybu zgodności natywne**  
  Gdy ta opcja jest zaznaczona, debuger używa macierzystym debugerze programu Visual Studio 2010 zamiast nowej debuger natywny.  
  
  Należy używać tej opcji podczas debugowania kodu w języku C++ platformy .NET, ponieważ nowy aparat debugowania nie obsługuje oceny wyrażeń języka C++ platformy .NET. Włączanie natywnego trybu zgodności wyłącza jednak wiele funkcji, które są zależne od bieżącej implementacji debugera do działania. Na przykład starszego aparatu nie posiada wiele wizualizatorów, dla wbudowanych typów, takich jak `std::string` w projektach programu Visual Studio 2015.   Użyj projektów programu Visual Studio 2013 dla zapewnienia optymalnego działania debugowania w tych przypadkach.  
  
  **Użyj starszych ewaluatory wyrażeń języka C# i VB**  
  Debuger użyje ewaluatory wyrażeń Visual Studio 2013 w języku C# /VB zamiast ewaluatory wyrażeń opartych na programie Visual Studio 2015 Roslyn.  
  
  **Ostrzegaj, gdy niestandardowe wizualizatory debugera względem potencjalnie niebezpiecznych procesów (tylko kod zarządzany)**  
  Program Visual Studio ostrzeże Cię, gdy używasz wizualizatora niestandardowego debugera działającego kodu w procesie debugowanego obiektu, ponieważ może być uruchomiony niebezpieczny kod.  
  
  **Włącz alokatora sterty debugowania Windows (tylko natywne)**  
  Włącza na stercie systemu windows, lepszą diagnostykę sterty. Włączenie tej opcji będzie mieć wpływ na wydajność debugowania.  
  
  **Włączanie debugowania interfejsu użytkownika narzędzia dla XAML**  
  Dynamiczne drzewo wizualne i na żywo właściwość zapoznaj się z systemu windows pojawi się po rozpoczęciu debugowania (F5) typu obsługiwanych projektu. Aby uzyskać więcej informacji, zobacz [właściwości sprawdzić XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Wyświetl podgląd wybranych elementów w dynamicznym drzewie wizualnym**  
  Element XAML, którego kontekst jest zaznaczona, jest również wybrany w **dynamiczne drzewo wizualne** okna.  
  
  **Pokaż narzędzia środowiska uruchomieniowego w aplikacji**  
  Pokazuje **dynamiczne drzewo wizualne** polecenia na pasku narzędzi w oknie głównym aplikacji XAML, która jest debugowana. Ta opcja została wprowadzona w Visual Studio 2015 Update 2.  
  
  **Włącz narzędzia diagnostyczne podczas debugowania**  
  **Narzędzia diagnostyczne** zostanie wyświetlone okno podczas debugowania. Aby uzyskać więcej informacji, zobacz [zintegrowane z debugerem profilowania](https://msdn.microsoft.com/library/a1f40370-7b61-42c2-afc4-0e13eba98859).  
  
  **Podczas debugowania Pokaż element perftip dla czasu upłynęło**  
  W oknie Kod wyświetla czas wywołania danej metody podczas debugowania.  
  
  **Włącz funkcję Edytuj i Kontynuuj**  
  Możesz użyć edycji i kontynuowania funkcji podczas debugowania.  
  
  **Włącz natywną funkcję Edytuj i Kontynuuj**  
  Możesz użyć edycji i kontynuowania funkcji podczas debugowania kodu natywnego języka C++. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Zastosuj zmiany przy kontynuowaniu (tylko natywne)**  
  Program Visual Studio kompiluje i automatycznie stosuje żadnych zmian w kodzie oczekujących, wprowadzone podczas kontynuując proces w stanie przerwania. Jeśli nie jest zaznaczone, można zastosować zmian przy użyciu elementu "Zastosowanie zmian kodu" w menu Debugowanie.  
  
  **Ostrzeżenie o nieodświeżonym kodzie (tylko natywne)**  
  Pobierz ostrzeżenia o nieodświeżonym kodzie.  
  
  **Zezwalaj na prekompilowanie (tylko natywne)**  
  Prekompilowanie jest dozwolone.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)

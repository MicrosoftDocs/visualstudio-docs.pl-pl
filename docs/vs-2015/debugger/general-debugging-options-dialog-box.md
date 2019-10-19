---
title: Ogólne, debugowanie, Opcje — okno dialogowe | Microsoft Docs
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
ms.openlocfilehash: 6c53af4a8e0f42708ab94d7206a9c0cc54819798
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573550"
---
# <a name="general-debugging-options-dialog-box"></a>Ogólne, debugowanie, okno dialogowe Opcje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na stronie**Narzędzia/Opcje/debugowanie/ogólne** można ustawić następujące opcje:  
  
 **Monituj przed usunięciem wszystkich punktów przerwania**  
 Wymaga potwierdzenia przed ukończeniem polecenia **Usuń wszystkie punkty przerwania** .  
  
 **Przerwij wszystkie procesy w przypadku przerwania jednego procesu**  
 Równocześnie przerywa wszystkie procesy, do których jest dołączony debuger, gdy występuje przerwy.  
  
 **Przerwij, gdy wyjątki przekraczają granice domeny lub zarządzane/natywne**  
 W przypadku debugowania w trybie zarządzanym lub mieszanym środowisko uruchomieniowe języka wspólnego może przechwytywać wyjątki, które przekraczają granice domeny aplikacji lub granice zarządzane/natywne w przypadku spełnienia następujących warunków:  
  
 1 \), gdy kod natywny wywołuje kod zarządzany za pomocą międzyoperacyjności modelu COM, a kod zarządzany zgłasza wyjątek. Zobacz [wprowadzenie do międzyoperacyjności modelu COM](https://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2 \), gdy kod zarządzany uruchomiony w domenie aplikacji 1 wywołuje kod zarządzany w domenie aplikacji 2, a kod w aplikacji domena 2 zgłasza wyjątek. Zobacz [programowanie z domenami aplikacji](https://msdn.microsoft.com/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3 \), gdy kod wywołuje funkcję przy użyciu odbicia, a funkcja zgłasza wyjątek. Zobacz [odbicie](https://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 W 2) i 3) wyjątek jest czasami przechwytywany przez kod zarządzany w `mscorlib` zamiast środowiska uruchomieniowego języka wspólnego. Ta opcja nie ma wpływu na przerwanie w przypadku wyjątków przechwytywanych przez `mscorlib`.  
  
 **Włącz debugowanie na poziomie adresu**  
 Włącza zaawansowane funkcje debugowania na poziomie adresu (okno **demontażu** , okno **rejestrów** i punkty przerwania adresów).  
  
 **Pokaż demontaż, jeśli źródło jest niedostępne**  
 Automatycznie wyświetla okno **demontaż** podczas próby debugowania kodu, dla którego źródło jest niedostępne.  
  
 **Włącz filtry punktów przerwania**  
 Umożliwia ustawienie filtrów dla punktów przerwania, aby miały wpływ tylko na określone procesy, wątki lub komputery.  
  
 **Włącz asystenta wyjątków**  
 Tylko dla kodu zarządzanego. Zarządzane wyjątki otwiera okno dialogowe Asystent wyjątków.  Zobacz [Asystent wyjątków](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Odwinięcie stosu wywołań w przypadku nieobsługiwanych wyjątków**  
 Powoduje, że okno **stos wywołań** wycofa stos wywołań do punktu przed wystąpieniem nieobsługiwanego wyjątku.  
  
 **Włącz Tylko mój kod**  
 Debuger wyświetla tylko kod użytkownika ("mój kod"), ignorując kod systemowy i inny kod, który jest zoptymalizowany lub nie ma symboli debugowania.  
  
 **Pokaż wszystkie elementy członkowskie dla obiektów niebędących użytkownikami w oknach zmiennych (tylko Visual Basic)**  
 Włącza wyświetlanie niepublicznych członków w obiektach, które znajdują się w kodzie nienależącym do użytkownika (nie "mój kod").  
  
 **Ostrzegaj w przypadku braku kodu użytkownika podczas uruchamiania**  
 Po rozpoczęciu debugowania z włączonym Tylko mój kod ta opcja ostrzega o braku kodu użytkownika ("mój kod").  
  
 **Włącz przechodzenie do .NET Framework źródła**  
 Zezwala debugerowi na wkroczenie do .NET Framework źródła. Włączenie tej opcji powoduje automatyczne wyłączenie Tylko mój kod .NET Framework symbole zostaną pobrane do lokalizacji pamięci podręcznej. Można zmienić lokalizację pamięci podręcznej w oknie dialogowym **Opcje** , kategorii **debugowanie** , stronie **symbole** .  
  
 **Przekrocz nad właściwościami i operatorami (tylko zarządzane)**  
 Uniemożliwia debugerowi przechodzenie do właściwości i operatorów w kodzie zarządzanym.  
  
 **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji**  
 Włącza automatyczną ocenę właściwości i niejawne wywołania funkcji w oknach zmiennych i oknie dialogowym **QuickWatch** .  
  
 **Wywołaj funkcję konwersji ciągów na obiektach w oknachC# zmiennych (tylko kod JavaScript)**  
 Wykonuje niejawne wywołanie konwersji ciągu podczas oceniania obiektów w oknach zmiennych. W związku z tym, ten wynik jest wyświetlany jako ciąg zamiast nazwy typu. Stosuje się tylko podczas debugowania C# w kodzie. To ustawienie może być zastąpione przez atrybut DebuggerDisplay (zobacz [using a DebuggerDisplay Attribute](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Włącz obsługę serwera źródłowego**  
 Poleca debugerowi programu Visual Studio pobieranie plików źródłowych z serwerów źródłowych, które implementują protokół SrcSrv (`srcsrv.dll`). Team Foundation Server i narzędzia debugowania dla systemu Windows to dwa serwery źródłowe implementujące protokół. Więcej informacji o instalatorze SrcSrv można znaleźć w dokumentacji narzędzi debugowania dla systemu Windows. Ponadto zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Ponieważ odczytywanie plików. pdb może wykonać dowolny kod w plikach, należy się upewnić, że ufasz serwerowi.  
  
 **Drukuj komunikaty diagnostyczne serwera źródłowego w oknie danych wyjściowych**  
 Po włączeniu obsługi serwera źródłowego to ustawienie włącza wyświetlanie danych diagnostycznych.  
  
 **Zezwalaj na serwer źródłowy dla zestawów częściowego zaufania (tylko zarządzane)**  
 Po włączeniu obsługi serwera źródłowego to ustawienie zastępuje domyślne zachowanie nie pobiera źródeł dla zestawów częściowej relacji zaufania.  
  
 **Wyróżnij cały wiersz dla punktów przerwania i bieżącej instrukcji**  
 Gdy debuger podświetla punkt przerwania lub bieżącą instrukcję, podświetli cały wiersz.  
  
 **Wymagaj, aby pliki źródłowe były dokładnie zgodne z wersją oryginalną**  
 Informuje debugera, aby upewnić się, że plik źródłowy jest zgodny z wersją kodu źródłowego użytego do skompilowania debugowanego pliku wykonywalnego. Jeśli wersja nie jest zgodna, zostanie wyświetlony monit o znalezienie pasującego źródła. Jeśli nie znaleziono pasującego źródła, kod źródłowy nie będzie wyświetlany podczas debugowania.  
  
 **Przekieruj cały tekst okna danych wyjściowych do okna bezpośredniego**  
 Wysyła wszystkie komunikaty debugera, które zwykle pojawiają się w oknie **danych wyjściowych** do okna **bezpośredniego** .  
  
 **Pokaż nieprzetworzoną strukturę obiektów w oknach zmiennych**  
 Wyłącza wszystkie dostosowania widoku struktury obiektu. Aby uzyskać więcej informacji na temat dostosowywania widoku, zobacz [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-managed-objects.md).  
  
 **Pomiń optymalizację JIT podczas ładowania modułu (tylko zarządzane)**  
 Wyłącza optymalizację JIT kodu zarządzanego, gdy moduł jest ładowany i kompilator JIT jest kompilowany podczas dołączania debugera. Wyłączenie optymalizacji może ułatwić debugowanie niektórych problemów, ale kosztem wydajności. Jeśli używasz Tylko mój kod, pominięcie optymalizacji JIT może spowodować, że kod niebędący użytkownikiem będzie wyświetlany jako kod użytkownika ("mój kod").  
  
 **Ostrzegaj, jeśli nie ma symboli podczas uruchamiania (tylko kod natywny)**  
 Wyświetla okno dialogowe ostrzeżenia podczas próby debugowania programu, dla którego debuger nie ma informacji o symbolach.  
  
 **Ostrzegaj, jeśli debugowanie skryptów jest wyłączone przy uruchomieniu**  
 Wyświetla okno dialogowe ostrzeżenia, gdy debuger jest uruchamiany z wyłączonym debugowaniem skryptów.  
  
 **Załaduj eksporty biblioteki DLL**  
 Ładuje tabele eksportu biblioteki DLL. Informacje o symbolach z tabel eksportu bibliotek DLL mogą być przydatne, jeśli pracujesz z komunikatami systemu Windows, procedurami systemu Windows (WindowProcs), obiektami COM lub kierowaniem lub dowolną biblioteką DLL, dla której nie masz symboli. Odczytywanie informacji o eksporcie z biblioteki DLL obejmuje pewne obciążenie. Dlatego ta funkcja jest domyślnie wyłączona.  
  
 Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki DLL, użyj `dumpbin /exports`. Symbole są dostępne dla dowolnej 32-bitowej systemowej biblioteki DLL. Odczytując dane wyjściowe `dumpbin /exports`, można zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji z tabel eksportu bibliotek DLL mogą pojawić się w innym miejscu debugera. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [Zrzuć bin/exports](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Pokaż diagram stosów równoległych od dołu do góry**  
 Kontroluje kierunek wyświetlania stosów w oknie **stosów równoległych** .  
  
 **Ignoruj wyjątki dostępu do pamięci procesora GPU, jeśli zapisano dane nie zmieniły wartości**  
 Ignoruje sytuacje wyścigu, które zostały wykryte podczas debugowania, jeśli dane nie uległy zmianie. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md).  
  
 **Użyj zarządzanego trybu zgodności**  
 Zastępuje domyślny aparat debugowania ze starszą wersją, aby umożliwić te scenariusze:  
  
- Używasz języka .NET Framework innego niż C#, VB lub F# , który oferuje własną ewaluatora wyrażeń (obejmuje C++to/CLI).  
  
- Chcesz włączyć funkcję Edytuj i Kontynuuj dla C++ projektów podczas debugowania w trybie mieszanym.  
  
  Należy pamiętać, że wybranie trybu zgodności zarządzanej powoduje wyłączenie niektórych funkcji, które są implementowane tylko w domyślnym aparacie debugowania.  
  
  **Użyj natywnego trybu zgodności**  
  Po wybraniu tej opcji debuger używa programu Visual Studio 2010 Native Debugger zamiast nowego debugera natywnego.  
  
  Tej opcji należy użyć w przypadku debugowania kodu .NET C++ , ponieważ nowy aparat debugowania nie obsługuje oceniania wyrażeń platformy .NET. C++ Jednak włączenie macierzystego trybu zgodności wyłącza wiele funkcji, które są zależne od bieżącej implementacji debugera do działania. Na przykład starszy aparat nie ma wielu wizualizatorów dla wbudowanych typów, takich jak `std::string` w projektach programu Visual Studio 2015.  W takich przypadkach należy używać projektów Visual Studio 2013.  
  
  **Używanie starszych C# i oceniających wyrażenia w języku VB**  
  Debuger będzie używać Visual Studio 2013 C#ocen wyrażeń/VB zamiast ocen wyrażeń opartych na programie Visual Studio 2015 Roslyn.  
  
  **Ostrzegaj w przypadku używania wizualizacji debugera niestandardowego z potencjalnie niebezpiecznymi procesami (tylko zarządzany)**  
  Program Visual Studio wyświetli ostrzeżenie, gdy korzystasz z niestandardowego wizualizatora debugera, który uruchamia kod w procesie debugowanego obiektu, ponieważ może to spowodować uruchomienie niebezpiecznego kodu.  
  
  **Włącz Alokator sterty debugowania systemu Windows (tylko kod natywny)**  
  Włącza stertę debugowania systemu Windows w celu poprawienia diagnostyki sterty. Włączenie tej opcji będzie miało wpływ na wydajność debugowania.  
  
  **Włącz narzędzia debugowania interfejsu użytkownika dla języka XAML**  
  Dynamiczne drzewo wizualne i właściwości na żywo zostaną wyświetlone po rozpoczęciu debugowania (F5) obsługiwanego typu projektu. Aby uzyskać więcej informacji, zobacz [Sprawdzanie właściwości XAML podczas debugowania](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Podgląd wybranych elementów w dynamicznym drzewie wizualnym**  
  Element XAML, którego kontekst jest wybrany, również jest wybierany w **aktywnym oknie drzewa wizualnego** .  
  
  **Pokaż narzędzia środowiska uruchomieniowego w aplikacji**  
  Pokazuje **dynamiczne polecenia drzewa wizualnego** na pasku narzędzi w oknie głównym aplikacji XAML, która jest debugowana. Ta opcja została wprowadzona w programie Visual Studio 2015 Update 2.  
  
  **Włącz narzędzia diagnostyczne podczas debugowania**  
  Okno **Narzędzia diagnostyczne** pojawia się podczas debugowania. Aby uzyskać więcej informacji, zobacz [profilowanie zintegrowane z debugerem](/visualstudio/profiling/running-profiling-tools-with-or-without-the-debugger).  
  
  **Pokaż czas, który upłynął element PerfTip dla podczas debugowania**  
  W oknie kod jest wyświetlany czas, który upłynął podczas debugowania danego wywołania metody.  
  
  **Włącz funkcję Edytuj i Kontynuuj**  
  Podczas debugowania można użyć funkcji Edytuj i Kontynuuj.  
  
  **Włącz natywną edycję i Kontynuuj**  
  Podczas debugowania kodu natywnego C++ można użyć funkcji Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [Edytuj i Kontynuuj ( C++wizualizacja)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Zastosuj zmiany przy kontynuowaniu (tylko kod natywny)**  
  Program Visual Studio automatycznie kompiluje i stosuje wszelkie zaległe zmiany kodu, które zostały wykonane podczas kontynuowania procesu ze stanu przerwania. Jeśli nie jest zaznaczone, możesz zastosować zmiany przy użyciu elementu "Zastosuj zmiany kodu" w menu Debuguj.  
  
  **Ostrzegaj o nieodświeżonym kodzie (tylko kod natywny)**  
  Otrzymuj ostrzeżenia dotyczące nieodświeżonego kodu.  
  
  **Zezwalaj na prekompilowanie (tylko kod natywny)**  
  Prekompilowanie jest dozwolone.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)

---
title: Intellisense dla programu Visual C++ | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2754a8ea663d888bb8ba2e2ff0276911976ff0af
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696557"
---
# <a name="visual-c-intellisense"></a>Visual C++ Intellisense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio 2015 IntelliSense dostępnej dla pojedynczego kodu pliki także jak w przypadku plików w projektach. W projektach dla wielu platform niektóre funkcje IntelliSense są dostępne w plikach CPP i .c w projekcie współdzielonym kodem nawet wtedy, gdy jesteś w kontekście systemu Android lub iOS.  
  
## <a name="intellisense-features-in-c"></a>Funkcje IntelliSense w języku C++  
 Funkcja IntelliSense jest nazwą nadaną zestaw funkcji, które kodowania bardziej wygodne. Ponieważ różne osoby mają różne pomysłów dotyczących co to jest wygodne, praktycznie wszystkie funkcje IntelliSense może być włączone lub wyłączone w **Edytor tekstu, C/C++, zaawansowane** stronę właściwości.  
  
 ![Tools, Options, Text Editor, C&#47;C&#43;&#43;, Advanced](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")  
  
 Elementy menu i skróty klawiaturowe, które pokazano na poniższej ilustracji umożliwia dostęp do funkcji IntelliSense.  
  
 ![Visual C&#43;&#43; IntelliSense Menu](../ide/media/vs2015-cpp-intellisense-menu.png "vs2015_cpp_intellisense_menu")  
  
### <a name="statement-completion-and-member-list"></a>Listy uzupełniania i elementów członkowskich — instrukcja  
 Po uruchomieniu, wpisując słowo kluczowe, typ, funkcji, nazwa zmiennej lub inny element program, który kompilator rozpoznaje, Edytor umożliwia Dokończ wyraz dla Ciebie  
  
 Aby uzyskać listę ikon i ich znaczenie, zobacz [widoku klas i przeglądarka obiektów ― ikony](../ide/class-view-and-object-browser-icons.md).  
  
 ![Program Visual C&#43; &#43; okna Dokończ wyraz](../ide/media/vs2015-cpp-complete-word.png "vs2015_cpp_complete_word")  
  
 Lista elementów członkowskich jest wywoływana po raz pierwszy pokazywane są tylko elementy członkowskie, które są dostępne dla bieżącego kontekstu. Jeśli używasz **Ctrl + J** po tym pokazuje wszystkie elementy członkowskie, niezależnie od tego, w ułatwienia dostępu. Jeśli wywołujesz ją raz trzeci, wyświetlany jest jeszcze większą listę elementów programu. Można wyłączyć uzupełnianie instrukcji w **opcji C/C++ General** strony.  
  
 ![Visual C&#43;&#43; Member List](../ide/media/vs2015-cpp-list-members.png "vs2015_cpp_list_members")  
  
### <a name="parameter-help"></a>Parametr pomocy  
 Po wpisaniu nawiasu otwierającego wywołania funkcji lub nawiasu ostrego w deklaracji zmiennej szablonu klasy Edytor pokazuje niewielki przedział z typami parametrów dla każdego przeciążenia funkcji ani konstruktora. "Bieżący" parametr--na podstawie lokalizacji kursora — jest pogrubioną czcionką. Można wyłączyć uzupełnianie instrukcji w **opcji C/C++ General** strony.  
  
 ![Visual C&#43;&#43; Parameter Help](../ide/media/vs-2015-cpp-param-help.png "vs_2015_cpp_param_help")  
  
### <a name="quick-info"></a>Szybkie informacje  
 Po umieszczeniu kursora myszy nad zmienną wbudowane, który zawiera informacje o typie i nagłówek, w którym zdefiniowano typ zostanie wyświetlone okno małe. Umieść kursor nad wywołanie funkcji, aby zobaczyć podpisu funkcji. Można wyłączyć szybkie informacje w **Edytor tekstu, C/C++, zaawansowane** strony.  
  
 ![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015-cpp-quickinfo.png "vs2015_cpp_quickInfo")  
  
## <a name="error-squiggles"></a>Zygzaki sygnalizujące błędy  
 Faliste linie w elemencie programu, (zmienna, słowo kluczowe, nawias klamrowy, wpisz nazwę i tak dalej) Wywołaj zwrócić uwagę na komunikat o błędzie lub potencjalnych błędów w kodzie. Zielony fala pojawi się podczas pisania deklaracją do przodu, aby przypomnieć, że nadal należy napisać implementację. Purpurowa wężyk w projekcie udostępnionym jest wyświetlany błąd w kodzie, który nie jest obecnie aktywny, na przykład podczas pracy w kontekście Windows, ale wprowadzenie tekstu, która byłaby błędu w kontekście systemu Android. Czerwona fala wskazuje błąd kompilatora lub ostrzeżenie w aktywnej kod, który należy do czynienia z.  
  
 ![Program Visual C&#43; &#43; zygzaki sygnalizujące błędy](../ide/media/vs2015-cpp-error-quiggles.png "vs2015_cpp_error_quiggles")  
  
## <a name="code-colorization-and-fonts"></a>Czcionki i kolorowanie kodu  
 Domyślne kolory i czcionki można zmienić za pomocą **środowiska, czcionki i kolory** stronę właściwości. Możesz zmienić czcionki dla wielu interfejsu użytkownika systemu windows, w tym miejscu nie tylko edytora. Ustawienia, które są specyficzne dla języka C++ zaczynają się od "C++"; inne ustawienia dotyczą wszystkich języków.  
  
## <a name="cross-platform-intellisense"></a>Funkcja IntelliSense dla wielu Platform  
 W projekcie współdzielonym kodem niektóre funkcje IntelliSense, takie jak zygzaki są dostępne nawet wtedy, gdy użytkownik pracuje w kontekście systemu Android. Jeśli piszesz kodu, które mogłyby spowodować błąd w projekcie jest nieaktywny, funkcja IntelliSense wyświetla nadal faliste linie, ale znajdują się w innym kolorze niż zygzaki błędy w bieżącym kontekście.  
  
 W tym miejscu to aplikacja OpenGLES, która jest skonfigurowana dla kompilacji dla systemów Android i iOS. Na ilustracji przedstawiono kod udostępniony edytowany. Na pierwszym obrazie systemu Android jest aktywnym projektem:  
  
 ![Projekt systemu Android jest aktywnym projektem. ](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")  
  
 Zapamiętaj poniższe:  
  
- #Else gałęzi w wierszu 8 jest wygaszone, aby wskazać region nieaktywne, ponieważ `__ANDROID__` jest zdefiniowany dla projektu dla systemu Android.  
  
- Zmienna powitanie, w wierszu 11 jest inicjowana z identyfikatorem Witaj, mającej wężyk purpurowy. Jest to spowodowane nie identyfikatora HELLO jest zdefiniowane w projekcie obecnie nieaktywne dla systemu iOS. Gdy w systemie Android będzie skompilować projekt w wierszu 11, nie będzie w systemie iOS. Ponieważ jest to kod udostępniony, który nie jest możesz zmienić, nawet jeśli skompilowany w aktualnie aktywnej konfiguracji.  
  
- W wierszu 12 ma czerwona fala na identyfikator BYE; Ten identyfikator nie jest zdefiniowany w aktualnie zaznaczonego aktywnego projektu.  
  
  Teraz Zmień aktywnego projektu na iOS.StaticLibrary i zwróć uwagę, jak zmienić faliste linie.  
  
  ![dla systemu iOS jest wybrany jako aktywnego projektu. ](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")  
  
  Zapamiętaj poniższe:  
  
- Gałąź #ifdef w wierszu 6 jest wygaszone, aby wskazać region nieaktywne, ponieważ *_ANDROID\\*  \_ nie jest zdefiniowany dla projektu systemu iOS.  
  
- Zmienna powitanie, w wierszu 11 jest inicjowana z identyfikatorem Witaj, który ma teraz czerwona fala. Jest to spowodowane nie identyfikatora HELLO jest zdefiniowane w projekcie aktualnie aktywne dla systemu iOS.  
  
- Wiersz 12 ma purpurowy wężyk na identyfikatorze BYE; Ten identyfikator nie jest zdefiniowany w obecnie nieaktywne Android.NativeActivity projektu.  
  
## <a name="single-file-intellisense"></a>Pojedynczy plik IntelliSense  
 Po otwarciu pojedynczy plik poza jakiegokolwiek projektu, będzie nadal się pojawiać IntelliSense. Można włączyć lub wyłączyć określonych funkcji, przechodząc do **Edytor tekstu, C/C++, zaawansowane** można włączyć lub wyłączyć funkcje IntelliSense. Aby skonfigurować ustawienia funkcji IntelliSense dla pojedynczych plików, które nie są częścią projektu, należy wyszukać **IntelliSense i przeglądania plików poza projektami** w **zaawansowane** sekcji. Zobacz [Przewodnik po Visual C++](https://msdn.microsoft.com/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).  
  
 ![Visual C&#43;&#43; single file intellisense](../ide/media/vs2015-cpp-single-file-intellisense.png "vs2015_cpp_single_file_intellisense")  
  
 Domyślnie pojedynczy plik IntelliSense używane tylko standardowe obejmują katalogi w celu znalezienia plików nagłówkowych. Aby dodać dodatkowe katalogi, otwórz menu skrótów węzła rozwiązania i Dodaj katalog na **debugować kod źródłowy** listy, jak pokazano na następującym rysunku:  
  
 ![Dodanie ścieżki do pliku nagłówka. ](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)

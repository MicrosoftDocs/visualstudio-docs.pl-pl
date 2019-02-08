---
title: IntelliSense dla C++
ms.date: 10/08/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6f92a1c9e39013c9c9cc0a320169f12e0c075b5a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942274"
---
# <a name="visual-c-intellisense-features"></a>Funkcje programu Visual C++ IntelliSense

Funkcja IntelliSense jest nazwą nadaną zestaw funkcji, które kodowania bardziej wygodne. IntelliSense dla języka C++ jest dostępna dla autonomicznych plików oraz jak w przypadku plików, które są częścią projektu w języku C++. W projektach dla wielu platform, niektóre funkcje IntelliSense są dostępne w *.cpp* i *.c* pliki w projekcie współdzielonym kodem, nawet wtedy, gdy jesteś w kontekście systemu Android lub iOS.

Ten artykuł zawiera omówienie funkcji C++ IntelliSense funkcji. Aby uzyskać informacje na temat konfigurowania projektu dla technologii IntelliSense i rozwiązywania problemów, zobacz [skonfigurować projekt języka C++ dla technologii IntelliSense](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>Funkcje IntelliSense w języku C++

Funkcja IntelliSense jest nazwą nadaną zestaw funkcji, które kodowania bardziej wygodne. Ponieważ różne osoby mają różne pomysłów dotyczących co to jest wygodne, praktycznie wszystkie funkcje IntelliSense może być włączone lub wyłączone w **opcje** dialogowego **edytora tekstów**  >  **C/C++** > **zaawansowane**. **Opcje** okno dialogowe jest dostępne z **narzędzia** menu na pasku menu.

![Okno dialogowe opcji narzędzi](../ide/media/sintellisensecpptoolsoptions.PNG)

Elementy menu i skróty klawiaturowe, które pokazano na poniższej ilustracji umożliwia dostęp do funkcji IntelliSense.

![Menu funkcji IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Listy uzupełniania i elementów członkowskich — instrukcja

Po uruchomieniu, wpisując słowo kluczowe, typ, funkcji, nazwa zmiennej lub inny element program, który kompilator rozpoznaje, edytor oferuje Dokończ wyraz dla Ciebie.

Aby uzyskać listę ikon i ich znaczenie, zobacz [ikony w widoku klas i przeglądarki obiektów](../ide/class-view-and-object-browser-icons.md).

![Program Visual C&#43; &#43; okna Dokończ wyraz](../ide/media/vs2015_cpp_complete_word.png)

Przy pierwszym wywołaniu listy członków pokazywane są tylko elementy członkowskie, które są dostępne dla bieżącego kontekstu. Jeśli użytkownik naciśnie klawisz **Ctrl**+**"j"** po tym pokazuje wszystkie elementy członkowskie, niezależnie od tego, w ułatwienia dostępu. Jeśli wywołujesz ją raz trzeci, wyświetlany jest jeszcze większą listę elementów programu. Można wyłączyć listy członków w **opcje** dialogowego **edytora tekstów** > **C/C++** > **ogólne**  >  **Automatyczna lista członków**.

![Visual C&#43;&#43; Member List](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Parametr pomocy

Po wpisaniu nawiasu otwierającego wywołania funkcji lub nawiasu ostrego w deklaracji zmiennej szablonu klasy Edytor pokazuje niewielki przedział z typami parametrów dla każdego przeciążenia funkcji ani konstruktora. Parametr "bieżący"&mdash;na podstawie lokalizacji kursora&mdash;jest pogrubioną czcionką. Można wyłączyć, informacje o parametrach w **opcje** dialogowego **edytora tekstów** > **C/C++** > **ogólne**  >  **Informacje o parametrach**.

![Program Visual C&#43; &#43; parametr pomocy](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Szybkie informacje

Po umieszczeniu kursora myszy nad zmienną wbudowane, który zawiera informacje o typie i nagłówek, w którym zdefiniowano typ zostanie wyświetlone okno małe. Umieść kursor nad wywołanie funkcji, aby zobaczyć podpisu funkcji. Można wyłączyć szybkie informacje w **opcje** dialogowego **edytora tekstów** > **C/C++** > **zaawansowane**  >  **Auto Quick Info**.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Zygzaki sygnalizujące błędy

Faliste linie w elemencie programu, (zmienna, słowo kluczowe, nawias klamrowy, wpisz nazwę i tak dalej) Wywołaj zwrócić uwagę na komunikat o błędzie lub potencjalnych błędów w kodzie. Zielony fala pojawi się podczas pisania deklaracją do przodu, aby przypomnieć, że nadal należy napisać implementację. Purpurowa wężyk w projekcie udostępnionym jest wyświetlany błąd w kodzie, który nie jest obecnie aktywny, na przykład podczas pracy w kontekście Windows, ale wprowadzenie tekstu, która byłaby błędu w kontekście systemu Android. Czerwona fala wskazuje błąd kompilatora lub ostrzeżenie w aktywnej kod, który należy do czynienia z.

![Visual C&#43;&#43; error squiggles](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Czcionki i kolorowanie kodu

Można zmienić domyślne kolory i czcionki w programie **opcje** dialogowego **środowiska** > **czcionki i kolory**. Możesz zmienić czcionki dla wielu interfejsu użytkownika systemu windows, w tym miejscu nie tylko edytora. Ustawienia, które są specyficzne dla języka C++ zaczynają się od "C++"; inne ustawienia dotyczą wszystkich języków.

## <a name="cross-platform-intellisense"></a>Funkcja IntelliSense dla wielu platform

W projekcie współdzielonym kodem niektóre funkcje IntelliSense, takie jak zygzaki są dostępne nawet wtedy, gdy użytkownik pracuje w kontekście systemu Android. Jeśli piszesz kodu, które mogłyby spowodować błąd w projekcie jest nieaktywny, funkcja IntelliSense wyświetla nadal faliste linie, ale znajdują się w innym kolorze niż zygzaki błędy w bieżącym kontekście.

Należy wziąć pod uwagę aplikacja OpenGLES, który został skonfigurowany do kompilacji dla systemów Android i iOS. Na ilustracji przedstawiono kod udostępniony edytowany. Na tej ilustracji jest aktywny projekt **iOS.StaticLibrary**:

![dla systemu iOS jest wybrany jako aktywnego projektu.](../ide/media/intellisensecppcrossplatform2.png)

Zapamiętaj poniższe:

- `#ifdef` Gałęzi w wierszu 6 jest wygaszone, aby wskazać region nieaktywne, ponieważ `__ANDROID__` nie jest zdefiniowany dla projektu systemu iOS.

- Zmienna powitanie, w wierszu 11 jest inicjowana z identyfikatorem `HELLO`, dla której istnieje czerwona fala. Jest to spowodowane nie identyfikatora `HELLO` jest zdefiniowana w projekcie aktualnie aktywne dla systemu iOS.

- Wierszu 12 ma purpurowy wężyk na identyfikator `BYE` ponieważ ten identyfikator nie jest zdefiniowany w (obecnie) nieaktywne **Android.NativeActivity** projektu. Mimo że ten wiersz kompiluje, gdy dla systemu iOS jest aktywnym projektem, nie będzie kompilacji, gdy systemu Android jest aktywnym projektem. Ponieważ jest to kod udostępniony, powinien Popraw kod, nawet jeśli skompilowany w aktualnie aktywnej konfiguracji.

Jeśli zmienisz aktywny projekt systemu Android, zmień zygzaki:

- `#else` Gałęzi w wierszu 8 jest wygaszone, aby wskazać region nieaktywne, ponieważ `__ANDROID__` jest zdefiniowany dla projektu dla systemu Android.

- Zmienna powitanie, w wierszu 11 jest inicjowana z identyfikatorem `HELLO`, mającym wężyk purpurowy. Jest to spowodowane nie identyfikatora `HELLO` jest zdefiniowana w projekcie obecnie nieaktywne dla systemu iOS.

- Wiersz 12 ma czerwona fala na identyfikatorze `BYE` ponieważ ten identyfikator nie jest zdefiniowana w aktywnym projekcie.

## <a name="intellisense-for-stand-alone-files"></a>Funkcja IntelliSense dla plików autonomicznych

Po otwarciu pojedynczy plik poza jakiegokolwiek projektu, będzie nadal się pojawiać IntelliSense. Można włączyć lub wyłączyć określonych funkcji IntelliSense w **opcje** dialogowego **edytora tekstów** > **C/C++**  >  **Zaawansowane**. Aby skonfigurować ustawienia funkcji IntelliSense dla pojedynczych plików, które nie są częścią projektu, należy wyszukać **IntelliSense i przeglądanie dla plików nienależących do projektu** sekcji.

![Program Visual C&#43; &#43; intellisense pojedynczego pliku](../ide/media/vs2015_cpp_single_file_intellisense.png)

Domyślnie pojedynczy plik IntelliSense używane tylko standardowe obejmują katalogi w celu znalezienia plików nagłówkowych. Aby dodać dodatkowe katalogi, otwórz menu skrótów na **rozwiązania** węzeł i Dodaj katalog na **debugować kod źródłowy** listy, jak pokazano na następującym rysunku:

![Dodanie ścieżki do pliku nagłówka.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Włącz lub wyłącz funkcje

Ponieważ różne osoby mają różne pomysłów dotyczących co to jest wygodne, praktycznie wszystkie funkcje IntelliSense może być włączone lub wyłączone w **opcje** dialogowego **edytora tekstów**  >  **C/C++** > **zaawansowane**. **Opcje** okno dialogowe jest dostępne z **narzędzia** menu na pasku menu.

![Okno dialogowe opcji narzędzi](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Zobacz także

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Konfigurowanie projektu w języku C++ dla funkcji IntelliSense](visual-cpp-intellisense-configuration.md)

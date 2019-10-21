---
title: Visual C++ IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 173020a95977bdae2ad3006ce23dea376fb9d22e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608823"
---
# <a name="visual-c-intellisense"></a>Visual C++ IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio 2015 technologia IntelliSense jest dostępna dla plików o pojedynczym kodzie oraz dla plików w projektach. W projektach międzyplatformowych niektóre funkcje IntelliSense są dostępne w plikach CPP i c w projekcie kodu udostępnionego nawet w kontekście systemu Android lub iOS.

## <a name="intellisense-features-in-c"></a>Funkcje IntelliSense wC++
 IntelliSense to nazwa nadana zestawowi funkcji, które sprawiają, że kodowanie jest wygodniejsze. Ponieważ różne osoby mają różne pomysły dotyczące tego, co jest wygodne, praktycznie wszystkie funkcje IntelliSense można włączyć lub wyłączyć w **edytorze tekstu, C/C++, zaawansowana** Strona właściwości.

 ![Narzędzia, opcje, Edytor tekstu, c&#47;c&#43;&#43;, zaawansowane](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")

 Można użyć elementów menu i skrótów klawiaturowych przedstawionych na poniższym obrazie, aby uzyskać dostęp do funkcji IntelliSense.

 ![Menu IntelliSense&#43; &#43; języka Visual C](../ide/media/vs2015-cpp-intellisense-menu.png "vs2015_cpp_intellisense_menu")

### <a name="statement-completion-and-member-list"></a>Uzupełnianie instrukcji i lista elementów członkowskich
 Po rozpoczęciu wpisywania słowa kluczowego, typu, funkcji, nazwy zmiennej lub innego programu, który jest rozpoznawany przez kompilator, Edytor proponuje ukończenie tego słowa

 Aby zapoznać się z listą ikon i ich znaczenia, zobacz [Widok klasy i Przeglądarka obiektów ikon](../ide/class-view-and-object-browser-icons.md).

 ![Okno uzupełniające słowo języka Visual C&#43; &#43;](../ide/media/vs2015-cpp-complete-word.png "vs2015_cpp_complete_word")

 Pierwsza lista elementów członkowskich jest wywoływana, aby wyświetlić tylko elementy członkowskie, które są dostępne dla bieżącego kontekstu. Jeśli używasz **kombinacji klawiszy Ctrl + J** , zobaczysz wszystkie elementy członkowskie niezależnie od ułatwień dostępu. Jeśli wywołajesz go w trzecim czasie, zostanie wyświetlona jeszcze szerszej listy elementów programu. Można wyłączyć uzupełnianie instrukcji na stronie **opcji C/C++ ogólne** .

 ![Lista elementów&#43; &#43; członkowskich Visual C](../ide/media/vs2015-cpp-list-members.png "vs2015_cpp_list_members")

### <a name="parameter-help"></a>Pomoc dotycząca parametrów
 Po wpisaniu otwierającego nawiasu klamrowego wywołania funkcji lub nawiasu kątowego w deklaracji zmiennej szablonu klasy, Edytor pokazuje małe okno z typami parametrów dla każdego przeciążenia funkcji lub konstruktora. Parametr "Current" — w oparciu o lokalizację kursora — jest pogrubiony. Można wyłączyć uzupełnianie instrukcji na stronie **opcji C/C++ ogólne** .

 ![Pomoc parametru&#43; &#43; języka Visual C](../ide/media/vs-2015-cpp-param-help.png "vs_2015_cpp_param_help")

### <a name="quick-info"></a>Szybkie informacje
 Po umieszczeniu wskaźnika myszy nad zmienną wyświetlane jest małe okno, w którym są wyświetlane informacje o typie i nagłówku, w którym jest zdefiniowany typ. Umieść kursor nad wywołaniem funkcji, aby zobaczyć podpis funkcji. Szybkie informacje można wyłączyć w **edytorze tekstu,C++na stronie zaawansowanej** .

 ![Visual C&#43; &#43; sekcji szybkich informacji](../ide/media/vs2015-cpp-quickinfo.png "vs2015_cpp_quickInfo")

## <a name="error-squiggles"></a>Zygzaki błędów
 Zygzaky w elemencie programu (zmienna, słowo kluczowe, nawiasy, nazwa typu itd.) wywołują uwagi do błędu lub potencjalnego błędu w kodzie. Zielony zygzak pojawia się podczas pisania deklaracji do przodu, aby przypominać, że nadal trzeba napisać implementację. Purpurowy zygzak pojawia się w projekcie udostępnionym, gdy występuje błąd w kodzie, który nie jest obecnie aktywny, na przykład podczas pracy w kontekście systemu Windows, ale wprowadź coś, co może być błędem w kontekście systemu Android. Czerwona zygzak wskazuje błąd kompilatora lub ostrzeżenie w aktywnym kodzie, z którym należy się zająć.

 ![Wizualny&#43; &#43; błąd Visual C](../ide/media/vs2015-cpp-error-quiggles.png "vs2015_cpp_error_quiggles")

## <a name="code-colorization-and-fonts"></a>Kolorowanie i czcionki kodu
 Domyślne kolory i czcionki można zmienić przy użyciu strony właściwości **środowisko, czcionki i kolory** . Czcionki dla wielu okien interfejsu użytkownika można zmienić w tym miejscu, a nie tylko w edytorze. Ustawienia specyficzne dla C++ rozpoczynające się od "C++"; Pozostałe ustawienia dotyczą wszystkich języków.

## <a name="cross-platform-intellisense"></a>Technologia IntelliSense dla wielu platform
 W projekcie udostępnionego kodu niektóre funkcje IntelliSense, takie jak zygzaki, są dostępne nawet podczas pracy w kontekście systemu Android. Jeśli piszesz jakiś kod, który mógłby spowodować błąd w nieaktywnym projekcie, funkcja IntelliSense nadal będzie wyświetlać zygzaki, ale są one w innym kolorze niż zygzaky dla błędów w bieżącym kontekście.

 Oto aplikacje OpenGL, które są skonfigurowane do kompilowania dla systemów Android i iOS. Ilustracja przedstawia kod współużytkowany, który jest edytowany. W pierwszym obrazie jest aktywny projekt systemu Android:

 ![Projekt systemu Android jest aktywnym projektem.](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")

 Zwróć uwagę na następujące kwestie:

- Gałąź #else w wierszu 8 jest wyszarzona w celu wskazania nieaktywnego regionu, ponieważ `__ANDROID__` jest zdefiniowany dla projektu systemu Android.

- Zmienna Greeting w wierszu 11 jest inicjowana z identyfikatorem HELLO, który ma purpurowy zygzak. Wynika to z faktu, że w aktualnie nieaktywnym projekcie systemu iOS nie jest zdefiniowany identyfikator HELLO. W wierszu projektu systemu Android 11 kompilacja nie będzie w systemie iOS. Ponieważ jest to kod współużytkowany, to coś należy zmienić, nawet jeśli kompiluje się w aktualnie aktywnej konfiguracji.

- Wiersz 12 ma czerwony Zygzak na identyfikatorze BYE; Ten identyfikator nie jest zdefiniowany w aktualnie wybranym aktywnym projekcie.

  Teraz zmień aktywny projekt na iOS. StaticLibrary i zwróć uwagę na to, w jaki sposób zmiany są zmieniane.

  ![System iOS jest wybrany jako aktywny projekt.](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")

  Zwróć uwagę na następujące kwestie:

- Gałąź #ifdef w wierszu 6 jest wyszarzona, aby wskazać nieaktywny region, ponieważ *_ANDROID \\* \_ nie jest zdefiniowany dla projektu systemu iOS.

- Zmienna Greeting w wierszu 11 została zainicjowana z identyfikatorem HELLO, który ma teraz czerwony zygzak. Wynika to z faktu, że w obecnie aktywnym projekcie systemu iOS nie jest zdefiniowany Witaj.

- Wiersz 12 ma purpurowy Zygzak na identyfikatorze BYE; Ten identyfikator nie jest zdefiniowany w aktualnie nieaktywnym projekcie systemu Android. Native.

## <a name="single-file-intellisense"></a>Funkcja IntelliSense pojedynczego pliku
 Po otwarciu pojedynczego pliku poza projektem nadal uzyskasz funkcję IntelliSense. Poszczególne funkcje można włączać lub wyłączać, przechodząc do **edytora tekstuC++, C/, zaawansowane** , aby włączyć lub wyłączyć funkcje IntelliSense. Aby skonfigurować funkcję IntelliSense dla pojedynczych plików, które nie są częścią projektu, należy poszukać funkcji **IntelliSense i przeglądać dla plików nienależących do projektu** w sekcji **Zaawansowane** . Zobacz [Przewodnik C++ po wizualizacji](https://msdn.microsoft.com/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).

 ![Funkcja IntelliSense&#43; &#43; pojedynczego pliku języka Visual C](../ide/media/vs2015-cpp-single-file-intellisense.png "vs2015_cpp_single_file_intellisense")

 Domyślnie funkcja IntelliSense z pojedynczym plikiem używa tylko standardowych katalogów include do znajdowania plików nagłówkowych. Aby dodać dodatkowe katalogi, otwórz menu skrótów w węźle rozwiązanie i Dodaj katalog do listy **kod źródłowy debugowania** , jak pokazano na poniższej ilustracji:

 ![Dodawanie ścieżki do pliku nagłówkowego.](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")

## <a name="see-also"></a>Zobacz też
 [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)

---
title: Funkcja IntelliSense języka C++
description: Dowiedz się więcej na temat funkcji IntelliSense, których można użyć podczas kodowania projektu języka C++.
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 49d555b2e509237e34375e1b85a35c57a6db4f3b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478890"
---
# <a name="visual-c-intellisense-features"></a>Visual C++ funkcje IntelliSense

IntelliSense to nazwa nadana zestawowi funkcji, które sprawiają, że kodowanie jest wygodniejsze. Funkcja IntelliSense dla języka C++ jest dostępna dla autonomicznych plików, a także dla plików, które są częścią projektu języka C++. W projektach międzyplatformowych niektóre funkcje IntelliSense są dostępne w plikach *CPP* i *c* w projekcie kodu udostępnionego, nawet gdy jesteś w kontekście systemu Android lub iOS.

Ten artykuł zawiera omówienie funkcji IntelliSense języka C++. Aby uzyskać informacje na temat sposobu konfigurowania projektu dla funkcji IntelliSense i rozwiązywania problemów, zobacz [Konfigurowanie projektu C++ dla IntelliSense](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>Funkcje IntelliSense w języku C++

IntelliSense to nazwa nadana zestawowi funkcji, które sprawiają, że kodowanie jest wygodniejsze. Ponieważ różne osoby mają różne pomysły dotyczące tego, co jest wygodne, praktycznie wszystkie funkcje IntelliSense można włączyć lub wyłączyć w oknie dialogowym **Opcje** , w obszarze **Edytor tekstu**  >  **C/C++**  >  **Advanced**. Okno dialogowe **Opcje** jest dostępne w menu **Narzędzia** na pasku menu.

![Opcje narzędzia — okno dialogowe](../ide/media/sintellisensecpptoolsoptions.PNG)

Można użyć elementów menu i skrótów klawiaturowych przedstawionych na poniższym obrazie, aby uzyskać dostęp do funkcji IntelliSense.

![Menu IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Uzupełnianie instrukcji i lista elementów członkowskich

Po rozpoczęciu wpisywania słowa kluczowego, typu, funkcji, nazwy zmiennej lub innego elementu programu, który jest rozpoznawany przez kompilator, Edytor oferuje ukończenie tego słowa.

Aby zapoznać się z listą ikon i ich znaczenia, zobacz [Widok klasy i Przeglądarka obiektów ikon](../ide/class-view-and-object-browser-icons.md).

![Visual C&#43;&#43; Ukończ okno programu Word](../ide/media/vs2015_cpp_complete_word.png)

Przy pierwszym wywołaniu listy elementów członkowskich wyświetlane są tylko te elementy, które są dostępne dla bieżącego kontekstu. Po naciśnięciu klawisza **Ctrl** + **J** po tym wyświetli wszystkie elementy członkowskie, niezależnie od dostępności. Jeśli wywołajesz go w trzecim czasie, zostanie wyświetlona jeszcze szerszej listy elementów programu. Listę elementów członkowskich można wyłączyć w oknie dialogowym **Opcje** , w obszarze **Edytor tekstu**  >  **C/C++**  >  **Ogólne**  >  **elementy członkowskie listy rozwijanej**.

![Lista elementów członkowskich&#43;&#43; Visual C](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Pomoc dotycząca parametrów

Po wpisaniu otwierającego nawiasu klamrowego wywołania funkcji lub nawiasu kątowego w deklaracji zmiennej szablonu klasy, Edytor pokazuje małe okno z typami parametrów dla każdego przeciążenia funkcji lub konstruktora. Parametr "Current" &mdash; oparty na lokalizacji kursora &mdash; jest pogrubiony. Informacje o parametrach można wyłączyć w oknie dialogowym **Opcje** , w obszarze **Edytor tekstu**  >  **C/C++**  >  **Ogólne**  >  **Informacje o parametrach**.

![Pomoc parametru&#43;&#43; języka Visual C](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Szybkie informacje

Po umieszczeniu wskaźnika myszy nad zmienną wyświetlane jest małe okno, w którym są wyświetlane informacje o typie i nagłówku, w którym jest zdefiniowany typ. Umieść kursor nad wywołaniem funkcji, aby zobaczyć podpis funkcji. Szybkie informacje można wyłączyć w oknie dialogowym **Opcje** , w obszarze **Edytor tekstu**  >  **C/C++**  >  **Zaawansowane**  >  **Informacje o szybkim** użyciu.

![Visual C&#43;&#43; sekcji szybkich informacji](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Zygzaki błędów

Zygzaky w elemencie programu (zmienna, słowo kluczowe, nawiasy, nazwa typu itd.) wywołują uwagi do błędu lub potencjalnego błędu w kodzie. Zielony zygzak pojawia się podczas pisania deklaracji do przodu, aby przypominać, że nadal trzeba napisać implementację. Purpurowy zygzak pojawia się w projekcie udostępnionym, gdy występuje błąd w kodzie, który nie jest obecnie aktywny, na przykład podczas pracy w kontekście systemu Windows, ale wprowadź coś, co może być błędem w kontekście systemu Android. Czerwona zygzak wskazuje błąd kompilatora lub ostrzeżenie w aktywnym kodzie, z którym należy się zająć.

![Wizualizacja błędów&#43;&#43; Visual C](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Kolorowanie i czcionki kodu

Domyślne kolory i czcionki można zmienić w oknie dialogowym **Opcje** , w obszarze **Environment**  >  **czcionki i kolory** środowiska. Czcionki dla wielu okien interfejsu użytkownika można zmienić w tym miejscu, a nie tylko w edytorze. Ustawienia specyficzne dla języka C++ zaczynają się od "C++"; Pozostałe ustawienia dotyczą wszystkich języków.

## <a name="cross-platform-intellisense"></a>Technologia IntelliSense dla wielu platform

W projekcie udostępnionego kodu niektóre funkcje IntelliSense, takie jak zygzaki, są dostępne nawet podczas pracy w kontekście systemu Android. Jeśli piszesz jakiś kod, który mógłby spowodować błąd w nieaktywnym projekcie, funkcja IntelliSense nadal będzie wyświetlać zygzaki, ale są one w innym kolorze niż zygzaky dla błędów w bieżącym kontekście.

Weź pod uwagę aplikację OpenGL, która jest skonfigurowana do kompilowania dla systemów Android i iOS. Ilustracja przedstawia kod współużytkowany, który jest edytowany. Na tym obrazie aktywnym projektem jest **iOS. StaticLibrary**:

![System iOS jest wybrany jako aktywny projekt.](../ide/media/intellisensecppcrossplatform2.png)

Zapamiętaj poniższe:

- `#ifdef`Gałąź w wierszu 6 jest wyszarzona, aby wskazać nieaktywny region, ponieważ `__ANDROID__` nie jest zdefiniowana dla projektu systemu iOS.

- Zmienna Greeting w wierszu 11 jest inicjowana z identyfikatorem `HELLO` , który ma teraz czerwony zygzak. Wynika to z faktu, że żaden identyfikator nie `HELLO` jest zdefiniowany w obecnie aktywnym projekcie systemu iOS.

- Wiersz 12 ma purpurowy Zygzak na identyfikatorze, `BYE` ponieważ ten identyfikator nie jest zdefiniowany w bieżącym projekcie **systemu Android. Native** . Mimo że ten wiersz jest kompilowany, gdy system iOS jest aktywnym projektem, nie będzie kompilować, gdy system Android jest aktywnym projektem. Ponieważ jest to kod współużytkowany, należy poprawić kod, mimo że kompiluje się w aktualnie aktywnej konfiguracji.

W przypadku zmiany aktywnego projektu na system Android zmiany są zmieniane:

- `#else`Gałąź w wierszu 8 jest wyszarzona, aby wskazać nieaktywny region, ponieważ `__ANDROID__` jest zdefiniowana dla projektu systemu Android.

- Zmienna Greeting w wierszu 11 jest inicjowana z identyfikatorem `HELLO` , który ma purpurowy zygzak. Wynika to z faktu, że żaden identyfikator nie `HELLO` jest zdefiniowany w aktualnie nieaktywnym projekcie systemu iOS.

- Wiersz 12 ma czerwony zygzak o identyfikatorze, `BYE` ponieważ ten identyfikator nie jest zdefiniowany w aktywnym projekcie.

## <a name="intellisense-for-stand-alone-files"></a>Funkcja IntelliSense dla plików autonomicznych

Po otwarciu pojedynczego pliku poza projektem nadal uzyskasz funkcję IntelliSense. W oknie dialogowym **Opcje** można włączać lub wyłączać określone funkcje IntelliSense, w obszarze **Edytor tekstu**  >  **C/C++**  >  **Advanced**. Aby skonfigurować funkcję IntelliSense dla pojedynczych plików, które nie są częścią projektu, zapoznaj się z sekcją **IntelliSense i przeglądanie dla plików nienależących do projektu** .

![Visual C&#43;&#43; funkcja IntelliSense dla jednego pliku](../ide/media/vs2015_cpp_single_file_intellisense.png)

Domyślnie funkcja IntelliSense z pojedynczym plikiem używa tylko standardowych katalogów include do znajdowania plików nagłówkowych. Aby dodać dodatkowe katalogi, otwórz menu skrótów w węźle **rozwiązanie** i Dodaj katalog do listy **kod źródłowy debugowania** , jak pokazano na poniższej ilustracji:

![Dodawanie ścieżki do pliku nagłówkowego.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Włączanie lub wyłączanie funkcji

Ponieważ różne osoby mają różne pomysły dotyczące tego, co jest wygodne, praktycznie wszystkie funkcje IntelliSense można włączyć lub wyłączyć w oknie dialogowym **Opcje** , w obszarze **Edytor tekstu**  >  **C/C++**  >  **Advanced**. Okno dialogowe **Opcje** jest dostępne w menu **Narzędzia** na pasku menu.

![Opcje narzędzia — okno dialogowe](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Zobacz też

- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Konfigurowanie projektu w języku C++ pod kątem funkcji IntelliSense](visual-cpp-intellisense-configuration.md)

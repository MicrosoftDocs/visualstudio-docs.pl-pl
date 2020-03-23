---
title: C++ IntelliSense
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: c0d1be12f733a858bf223fb1dce6a091c0dc6c50
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594217"
---
# <a name="visual-c-intellisense-features"></a>Funkcje visual c++ IntelliSense

IntelliSense to nazwa nadana zestawowi funkcji, które sprawiają, że kodowanie jest wygodniejsze. IntelliSense dla języka C++ jest dostępny dla plików autonomicznych, a także dla plików, które są częścią projektu C++. W projektach wieloplatformowych niektóre funkcje IntelliSense są dostępne w plikach *.cpp* i *.c* w projekcie udostępnionego kodu, nawet jeśli znajdujesz się w kontekście systemu Android lub iOS.

Ten artykuł zawiera omówienie funkcji programu IntelliSense języka C++. Aby uzyskać informacje na temat konfigurowania projektu dla programu IntelliSense i rozwiązywania problemów, zobacz [Konfigurowanie projektu języka C++ dla programu IntelliSense](visual-cpp-intellisense-configuration.md).

## <a name="intellisense-features-in-c"></a>Funkcje IntelliSense w języku C++

IntelliSense to nazwa nadana zestawowi funkcji, które sprawiają, że kodowanie jest wygodniejsze. Ponieważ różni ludzie mają różne pomysły na to, co jest wygodne, praktycznie wszystkie funkcje IntelliSense można włączyć lub wyłączyć w oknie dialogowym **Opcje,** w obszarze **Edytor** > tekstu**C / C ++** > **Zaawansowane**. Okno dialogowe **Opcje** jest dostępne w menu **Narzędzia** na pasku menu.

![Okno dialogowe Opcje narzędzia](../ide/media/sintellisensecpptoolsoptions.PNG)

Aby uzyskać dostęp do programu IntelliSense, można użyć elementów menu i skrótów klawiaturowych pokazanych na poniższej ilustracji.

![Menu IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Uzupełnianie wyciągu i lista członków

Po rozpoczęciu wpisywania słowa kluczowego, typu, funkcji, nazwy zmiennej lub innego elementu programu, który kompilator rozpoznaje, edytor oferuje dopełnienie wyrazu dla Ciebie.

Aby uzyskać listę ikon i ich znaczeń, zobacz [Ikony widoku klasy i przeglądarki obiektów](../ide/class-view-and-object-browser-icons.md).

![Okno Programu Visual C&#43;&#43; Complete Word](../ide/media/vs2015_cpp_complete_word.png)

Przy pierwszym wywołaniu listy elementów członkowskich, pokazuje tylko elementy członkowskie, które są dostępne dla bieżącego kontekstu. Jeśli naciśniesz **klawisz Ctrl**+**J** po tym, pokazuje wszystkich członków, niezależnie od dostępności. Jeśli wywołasz go po raz trzeci, zostanie wyświetlona jeszcze szersza lista elementów programu. Listę członków można wyłączyć w oknie dialogowym **Opcje** w obszarze **Edytor** > tekstu**C/C++** > **Ogólne** > **elementy listy auto członków**.

![Visual C&#43;&#43; lista elementów członkowskich](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Pomoc dotycząca parametrów

Po wpisaniu nawiasu otwierającego wywołania funkcji lub nawiasu kątowego w deklaracji zmiennej szablonu klasy edytor pokazuje małe okno z typami parametrów dla każdego przeciążenia funkcji lub konstruktora. Parametr "bieżący"&mdash;oparty na lokalizacji&mdash;kursora jest pogrubiony. Informacje o parametrach można wyłączyć w oknie dialogowym **Opcje** w obszarze **Edytor** > tekstu**C/C++** > **Informacje o parametrach****ogólnych** > .

![Pomoc parametru&#43;&#43; języka Visual C](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Szybkie informacje

Po najechaniu kursorem myszy na zmienną zostanie wyświetlene małe okno z informacjami o typie i nagłówkiem, w którym zdefiniowano typ. Umieść wskaźnik myszy na wywołaniu funkcji, aby wyświetlić podpis funkcji. Szybkie informacje można wyłączyć w oknie dialogowym **Opcje** w obszarze **Edytor** > tekstu**C/C++** > **Zaawansowane** > **automatyczne szybkie informacje**.

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Błąd squiggles

Squiggles pod element programu (zmienna, słowo kluczowe, nawias klamrowy, nazwa typu i tak dalej) zwrócić uwagę na błąd lub potencjalny błąd w kodzie. Zielona squiggle pojawia się podczas pisania deklaracji do przodu, aby przypomnieć, że nadal trzeba napisać implementację. Purpurowy squiggle pojawia się w projekcie udostępnionym, gdy występuje błąd w kodzie, który nie jest obecnie aktywny, na przykład podczas pracy w kontekście systemu Windows, ale wprowadź coś, co byłoby błędem w kontekście systemu Android. Czerwony squiggle wskazuje błąd kompilatora lub ostrzeżenie w aktywnym kodzie, który należy wykonać.

![Wizualne&#43;&#43; błąd C squiggles](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Kolorowanie kodu i czcionki

Domyślne kolory i czcionki można zmieniać w oknie dialogowym **Opcje** w obszarze**Czcionki i kolory** **środowiska** > . W tym miejscu można zmienić czcionki dla wielu okien interfejsu użytkownika, a nie tylko edytora. Ustawienia, które są specyficzne dla języka C++ zaczynają się od "C++"; pozostałe ustawienia są dla wszystkich języków.

## <a name="cross-platform-intellisense"></a>Wieloplatformowy IntelliSense

W projekcie udostępnionego kodu niektóre funkcje IntelliSense, takie jak squiggles są dostępne nawet podczas pracy w kontekście systemu Android. Jeśli piszesz jakiś kod, który spowodowałoby błąd w nieaktywnym projekcie, IntelliSense nadal pokazuje squiggles, ale są one w innym kolorze niż squiggles dla błędów w bieżącym kontekście.

Należy wziąć pod uwagę aplikację OpenGLES, która jest skonfigurowana do tworzenia dla systemu Android i iOS. Na ilustracji przedstawiono edytowany kod udostępniony. Na tym obrazie aktywnym projektem jest **iOS.StaticLibrary**:

![IOS jest wybierany jako aktywny projekt.](../ide/media/intellisensecppcrossplatform2.png)

Zapamiętaj poniższe:

- Gałąź `#ifdef` w wierszu 6 jest wyszarzony, `__ANDROID__` aby wskazać nieaktywny region, ponieważ nie jest zdefiniowany dla projektu systemu iOS.

- Zmienna powitania w wierszu 11 jest `HELLO`inicjowana za pomocą identyfikatora , który ma teraz czerwoną falisk. Dzieje się tak, `HELLO` ponieważ żaden identyfikator nie jest zdefiniowany w aktualnie aktywnym projekcie systemu iOS.

- Linia 12 ma purpurową falistkę na identyfikatorze, `BYE` ponieważ ten identyfikator nie jest zdefiniowany w (obecnie) nieaktywnym projekcie **Android.NativeActivity.** Mimo że ten wiersz kompiluje, gdy system iOS jest aktywnym projektem, nie będzie kompilowany, gdy android jest aktywnym projektem. Ponieważ jest to kod udostępniony, należy poprawić kod, nawet jeśli kompiluje w aktualnie aktywnej konfiguracji.

Jeśli zmienisz aktywny projekt na Androida, squiggles zmienić:

- Gałąź `#else` w wierszu 8 jest wyszarzony, `__ANDROID__` aby wskazać nieaktywny region, ponieważ jest zdefiniowany dla projektu systemu Android.

- Zmienna powitania w wierszu 11 `HELLO`jest inicjowana za pomocą identyfikatora , który ma fioletowy squiggle. Dzieje się tak, `HELLO` ponieważ żaden identyfikator nie jest zdefiniowany w aktualnie nieaktywnym projekcie systemu iOS.

- Wiersz 12 ma czerwony squiggle `BYE` na identyfikatorze, ponieważ ten identyfikator nie jest zdefiniowany w aktywnym projekcie.

## <a name="intellisense-for-stand-alone-files"></a>IntelliSense dla plików autonomicznych

Po otwarciu jednego pliku poza dowolnym projektem nadal otrzymasz IntelliSense. W oknie dialogowym **Opcje** w obszarze **Edytor** > tekstu**C/C++** > **Advanced**można włączyć lub wyłączyć określone funkcje programu IntelliSense. Aby skonfigurować intellisense dla pojedynczych plików, które nie są częścią projektu, poszukaj **IntelliSense i przeglądania plików innych niż projekt.**

![Visual C&#43;&#43; pojedynczy plik intellisense](../ide/media/vs2015_cpp_single_file_intellisense.png)

Domyślnie pojedynczy plik IntelliSense używa tylko standardowych katalogów dołączanych do znajdowania plików nagłówkowych. Aby dodać dodatkowe katalogi, otwórz menu skrótów w węźle **Rozwiązanie** i dodaj katalog do listy **Kod źródłowy debugowania,** jak pokazano na poniższej ilustracji:

![Dodawanie ścieżki do pliku nagłówka.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Włączanie lub wyłączanie funkcji

Ponieważ różni ludzie mają różne pomysły na to, co jest wygodne, praktycznie wszystkie funkcje IntelliSense można włączyć lub wyłączyć w oknie dialogowym **Opcje,** w obszarze **Edytor** > tekstu**C / C ++** > **Zaawansowane**. Okno dialogowe **Opcje** jest dostępne w menu **Narzędzia** na pasku menu.

![Okno dialogowe Opcje narzędzia](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Zobacz też

- [Korzystanie z IntelliSense](../ide/using-intellisense.md)
- [Konfigurowanie projektu w języku C++ pod kątem funkcji IntelliSense](visual-cpp-intellisense-configuration.md)

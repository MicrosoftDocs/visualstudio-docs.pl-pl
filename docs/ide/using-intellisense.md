---
title: Informacje o parametrach, członkowie listy i szybkie informacje
ms.date: 05/25/2018
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34e038256d46909e135f8285cb1b3edc45d0ba3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565347"
---
# <a name="intellisense-in-visual-studio"></a>IntelliSense w programie Visual Studio

IntelliSense to pomoc w wypełnianiu kodu, która zawiera wiele funkcji: Lista członków, Informacje o parametrach, Szybkie informacje i Pełne słowo. Te funkcje pomagają dowiedzieć się więcej o kodzie, którego używasz, śledzić parametry, które piszesz, i dodawać wywołania do właściwości i metod za pomocą tylko kilku naciśnięć klawiszy.

Wiele aspektów IntelliSense jest specyficzne dla języków. Aby uzyskać więcej informacji na temat intellisense dla różnych języków, zobacz tematy wymienione w [sekcji Zobacz też.](#see-also)

## <a name="list-members"></a>Lista składników

Lista prawidłowych elementów członkowskich z typu (lub obszaru nazw) pojawia się po`.`wpisaniu znaku `::` wyzwalacza (na przykład kropki ( ) w kodzie zarządzanym lub w języku C++). Jeśli nadal wpisujesz znaki, lista zostanie odfiltrowana tak, aby zawierała tylko elementy członkowskie, które zaczynają się od tych znaków lub gdy początek *dowolnego* wyrazu w nazwie zaczyna się od tych znaków. IntelliSense wykonuje również dopasowanie "przypadku wielbłąda", dzięki czemu możesz po prostu wpisać pierwszą literę każdego słowa w przypadku wielbłąda w nazwie członka, aby zobaczyć dopasowania.

Po wybraniu elementu można go wstawić do kodu, naciskając klawisz **Tab** lub wpisując spację. Jeśli wybierzesz element i wpiszesz kropkę, element pojawia się, a po nim kropka, co wywołuje kolejną listę elementów członkowskich. Po wybraniu elementu, ale przed jego wstawieniem, otrzymasz szybkie informacje na jego temat.

Na liście składowych ikona po lewej stronie reprezentuje typ składowej, taki jak przestrzeń nazw, klasa, funkcja lub zmienna. Aby uzyskać listę ikon, zobacz [Ikony widoku klasy i przeglądarki obiektów](../ide/class-view-and-object-browser-icons.md). Lista może być dość długa, więc możesz nacisnąć **PgUp** i **PgDn,** aby przejść w górę lub w dół na liście.

![Lista członków programu Visual Studio](../ide/media/vs2015_intellisense.png)

Funkcję **Członków listy** można wywołać ręcznie, wpisując klawisz **Ctrl**+**J**, wybierając **pozycję Edytuj** > **elementy członkowskie listy****IntelliSense** > lub wybierając przycisk **Lista członków** na pasku narzędzi edytora. Gdy jest wywoływana w pustym wierszu lub poza rozpoznawalnym zasięgiem, na liście wyświetlane są symbole w globalnej przestrzeni nazw.

Aby domyślnie wyłączyć listę członków (tak, aby nie pojawiała się, chyba że jest to wyraźnie wywoływane), przejdź do **opcji Narzędzia** > **Wszystkie** > **języki** i usuń zaznaczenie **autoustawników listy**. Jeśli chcesz wyłączyć listę członków tylko dla określonego języka, przejdź do ustawień **ogólnych** dla tego języka.

Można również przejść do trybu sugestii, w którym tylko wpisany tekst jest umieszczony w kodzie. Na przykład, jeśli wprowadzisz identyfikator, którego nie ma na liście, i nacisnąc **tabulatora**, w trybie uzupełniania wpisy wpisz zastąpi wpisany identyfikator. Aby przełączyć tryb ukończenia i tryb sugestii, naciśnij **klawisze Ctrl**+**Alt**+**Space**lub wybierz polecenie **Edytuj** > tryb ukończenia**przełącznika****IntelliSense** > .

## <a name="parameter-info"></a>Informacje o parametrach

Informacje o parametrach zawierają informacje na temat liczby, nazw i typów parametrów wymaganych przez metodę, parametr typu ogólnego atrybutu (w języku C#) lub szablon (w języku C++).

Parametr pogrubiony wskazuje następny parametr, który jest wymagany podczas wprowadzania funkcji. W przypadku funkcji przeciążonych można użyć klawiszy strzałek **w górę** i **w dół,** aby wyświetlić alternatywne informacje o parametrach przeciążeń funkcji.

![Informacje o parametrach](../ide/media/vs2015_param_info.png)

Gdy opisujesz funkcje i parametry za pomocą komentarzy dokumentacji XML, komentarze będą wyświetlane jako informacje o parametrach. Aby uzyskać więcej informacji, zobacz [Dostarczanie komentarzy do kodu XML](reference/generate-xml-documentation-comments.md).

Informacje o parametrach można wywołać ręcznie, wybierając pozycję **Edytuj** > **informacje o parametrach****IntelliSense,** > naciskając klawisz **Ctrl**+**Shift**+**Space**lub wybierając przycisk Informacje **o parametrach** na pasku narzędzi edytora.

## <a name="quick-info"></a>Szybkie informacje

Szybkie informacje wyświetlają pełną deklarację dla każdego identyfikatora w kodzie.

![Szybkie informacje w programie Visual Studio](../ide/media/vs2015_quick_info.png)

Po wybraniu członka z pola **Lista członków** pojawi się również szybkie informacje.

![Informacje o parametrach w pliku kodu&#35; C](../ide/media/vs2015_paraminfo.png)

Szybkie informacje można wywołać ręcznie, wybierając **pozycję Edytuj** > **szybkie informacje****intellisense,** > naciskając klawisz **Ctrl**+**I**lub wybierając przycisk **Szybkie informacje** na pasku narzędzi edytora.

Jeżeli funkcja jest przeciążona, mechanizm IntelliSense może nie wyświetlać informacji dla wszystkich postaci przeciążenia.

Szybkie informacje można wyłączyć dla kodu języka C++, przechodząc do**Options** > **edytora** >  **tekstu Opcje narzędzi** >  `false`**C/C++** > **Advanced**i ustawiając przycisk Auto Szybkie **informacje** na .

## <a name="complete-word"></a>Dokończ wyraz

Program Complete Word uzupełnia pozostałą część zmiennej, polecenia lub nazwy funkcji po wprowadzeniu wystarczającej liczby znaków, aby odróżnić ten termin. Program Complete Word można wywołać, wybierając pozycję **Edytuj** > polecenie**IntelliSense** > **Complete Word**, naciskając klawisz **Ctrl**+**Spacja**lub wybierając przycisk **Zakończ program Word** na pasku narzędzi edytora.

## <a name="intellisense-options"></a>Opcje IntelliSense

Opcje IntelliSense są domyślnie włączone. Aby je wyłączyć, wybierz pozycję**Edytor tekstu** **Opcje** >  **narzędzi** > i usuń **zaznaczenie informacji o parametrach** lub **Automatyczne wyświetlanie członków listy,** jeśli nie chcesz, aby funkcja Członkowie listy była ów charakterystyczna.

## <a name="intellisense-icons"></a>Ikony IntelliSense
Ikony w IntelliSense mogą przekazać dodatkowe znaczenie za pomocą modyfikatorów ikon. Są to gwiazdy, serca i zamki warstwowe na ikonie obiektu, które przekazują odpowiednio chronione, wewnętrzne lub prywatne.

|    Ikona    |    Ułatwienia dostępu    |    Opis    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Modyfikator ikon publicznych](../ide/media/intellisensePublicNoModifier.png)       |    Klasa publiczna    |    Dostęp nie jest ograniczony.   |
| ![Modyfikator chronionych ikon](../ide/media/intellisenseProtectedModifier.png)       |    Klasa chroniona    |    Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących z klasy zawierającej.    |
| ![Chroniony modyfikator ikon wewnętrznych](../ide/media/intellisenseProtectedInternalModifier.png)       |    Chroniona klasa wewnętrzna    |    Dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących z klasy zawierającej.    |
| ![Wewnętrzny modyfikator ikon](../ide/media/intellisenseInternalModifier.png)       |    Klasa wewnętrzna    |    Dostęp jest ograniczony do bieżącego zestawu.    |
|![Modyfikator ikon prywatnych](../ide/media/intellisensePrivateModifier.png)        |    Klasa prywatna    |    Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących z klasy zawierającej w bieżącym zestawie. (Dostępne od C# 7.2.)    |

## <a name="troubleshoot-intellisense"></a>Rozwiązywanie problemów z intellisense

W niektórych przypadkach opcje IntelliSense mogą nie działać zgodnie z oczekiwaniami.

**Kursor znajduje się poniżej błędu kodu.** Korzystanie z programu IntelliSense może być nie możliwe, jeśli w kodzie nad kursorem występuje funkcja niekompletna lub inny błąd, ponieważ intellisense może nie być w stanie przeanalizować elementów kodu. Można naprawić ten problem, zakomentowując odpowiedni kod.

**Kursor znajduje się w komentarzu do kodu.** Nie można użyć intellisense, jeśli kursor znajduje się w komentarzu w pliku źródłowym.

**Kursor znajduje się w literału ciągu.** Nie można użyć IntelliSense, jeśli kursor znajduje się w cudzysłowie wokół literału ciągu, jak w poniższym przykładzie:

```cpp
MessageBox( hWnd, "String literal|")
```

**Opcje automatyczne są wyłączone.** Domyślnie IntelliSense działa automatycznie, ale można go wyłączyć. Nawet jeśli automatyczne uzupełnianie instrukcji jest wyłączone, można wywołać funkcję mechanizmu IntelliSense.

## <a name="see-also"></a>Zobacz też

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Kod zapisu i refaktoryzacji (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Dostarczanie komentarzy do kodu XML](reference/generate-xml-documentation-comments.md)

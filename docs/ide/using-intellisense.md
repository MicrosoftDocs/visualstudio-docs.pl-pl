---
title: Informacje o parametrach, Lista członków i szybkie informacje
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75565347"
---
# <a name="intellisense-in-visual-studio"></a>Technologia IntelliSense w programie Visual Studio

IntelliSense to pomoc dla uzupełniania kodu, która obejmuje wiele funkcji: członków listy, informacji o parametrach, szybkich informacji i kompletnego wyrazu. Te funkcje pozwalają dowiedzieć się więcej o kodzie, którego używasz, śledzić parametry, które wpisujesz, i dodawać wywołania do właściwości i metod za pomocą tylko kilku naciśnięć klawiszy.

Wiele aspektów IntelliSense jest specyficzne dla języków. Aby uzyskać więcej informacji na temat technologii IntelliSense dla różnych języków, zobacz tematy wymienione w sekcji [Zobacz też](#see-also) .

## <a name="list-members"></a>Lista składników

Lista prawidłowych członków z typu (lub przestrzeni nazw) pojawia się po wpisaniu znaku wyzwalacza (na przykład kropki ( `.` ) w kodzie zarządzanym lub `::` w języku C++). Jeśli będziesz kontynuować wpisywanie znaków, lista jest filtrowana w celu uwzględnienia tylko elementów członkowskich, które zaczynają się od tych znaków lub gdzie początek *dowolnego* wyrazu w nazwie zaczyna się od tych znaków. Technologia IntelliSense wykonuje również dopasowanie "notacji CamelCase Case", więc można po prostu wpisać pierwszą literę każdego wyrazu notacji CamelCase w nazwie elementu członkowskiego, aby zobaczyć dopasowania.

Po wybraniu elementu można wstawić go do kodu, naciskając klawisz **Tab** lub wpisując spację. Jeśli wybierzesz element i wpiszesz kropkę, element pojawia się, a po nim kropka, co wywołuje kolejną listę elementów członkowskich. Po wybraniu elementu, ale przed jego wstawieniem, otrzymasz szybkie informacje na jego temat.

Na liście składowych ikona po lewej stronie reprezentuje typ składowej, taki jak przestrzeń nazw, klasa, funkcja lub zmienna. Aby zapoznać się z listą ikon, zobacz [Widok klasy i Przeglądarka obiektów ikon](../ide/class-view-and-object-browser-icons.md). Lista może być dość długa, więc można nacisnąć klawisze **PgUp** i **PgDn** , aby przejść w górę lub w dół na liście.

![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015_intellisense.png)

Można wywołać funkcję **listy członków** ręcznie, wpisując **Ctrl** + **J**, wybierając **Edytuj**  >  **IntelliSense**  >  **członków listy**IntelliSense lub wybierając przycisk **listy członków** na pasku narzędzi edytora. Gdy jest wywoływana w pustym wierszu lub poza rozpoznawalnym zasięgiem, na liście wyświetlane są symbole w globalnej przestrzeni nazw.

Aby wyłączyć członków listy domyślnie (tak, aby nie były wyświetlane, chyba że jest to określone), przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **wszystkie języki** i usuń zaznaczenie pozycji **autolista członków**. Jeśli chcesz wyłączyć członków listy tylko dla określonego języka, przejdź do ustawień **ogólnych** dla tego języka.

Można również przejść do trybu sugestii, w którym tylko wpisany tekst jest umieszczony w kodzie. Na przykład, jeśli wprowadzisz identyfikator, który nie znajduje się na liście, i naciśniesz klawisz **Tab**, w trybie uzupełniania wpis zastąpi wpisanego identyfikatora. Aby przełączać się między trybem ukończenia i trybem sugestii, naciśnij klawisz **Ctrl** + **Alt** + **spacja**lub wybierz opcję **Edytuj**  >  **IntelliSense**  >  **Tryb uzupełniania**funkcji IntelliSense.

## <a name="parameter-info"></a>Informacje o parametrach

Informacje o parametrach zawierają informacje na temat liczby, nazw i typów parametrów wymaganych przez metodę, parametr typu ogólnego atrybutu (w języku C#) lub szablon (w języku C++).

Parametr pogrubiony wskazuje następny parametr, który jest wymagany podczas wprowadzania funkcji. W przypadku przeciążonych funkcji można użyć klawiszy strzałek w **górę** i **w dół** , aby wyświetlić alternatywne informacje o parametrach przeciążeń funkcji.

![Informacje o parametrach](../ide/media/vs2015_param_info.png)

Gdy opisujesz funkcje i parametry za pomocą komentarzy dokumentacji XML, komentarze będą wyświetlane jako informacje o parametrach. Aby uzyskać więcej informacji, zobacz [dostarczanie komentarzy do kodu XML](reference/generate-xml-documentation-comments.md).

Można ręcznie wywołać informacje o parametrach poprzez wybranie opcji **Edytuj**  >  **IntelliSense**  >  **Informacje o parametrach**IntelliSense, naciskając klawisz **Ctrl** + **SHIFT** + **Space**lub wybierając przycisk **Informacje o parametrach** na pasku narzędzi edytora.

## <a name="quick-info"></a>Szybkie informacje

Szybkie informacje wyświetlają pełną deklarację dla każdego identyfikatora w kodzie.

![Szybkie informacje programu Visual Studio](../ide/media/vs2015_quick_info.png)

Po wybraniu elementu członkowskiego z pola **członków listy** pojawiają się również szybkie informacje.

![Informacje o parametrach w pliku kodu języka C&#35;](../ide/media/vs2015_paraminfo.png)

Szybkie informacje można wywołać ręcznie, wybierając pozycję **Edytuj**  >  **IntelliSense**  >  **szybkie informacje**IntelliSense, naciskając klawisz **Ctrl** + **i**lub wybierając przycisk **szybkie informacje** na pasku narzędzi edytora.

Jeżeli funkcja jest przeciążona, mechanizm IntelliSense może nie wyświetlać informacji dla wszystkich postaci przeciążenia.

Szybkie informacje można wyłączyć dla kodu C++, przechodząc do opcji **Narzędzia**  >  **Options**  >  **Edytor tekstu**  >  **C/c++**  >  **Zaawansowane**i ustawiając opcję **autoszybkie informacje** na `false` .

## <a name="complete-word"></a>Dokończ wyraz

Po wprowadzeniu wystarczającej liczby znaków, aby odróżnić ten wyraz, kończy się pozostałą częścią zmiennej, polecenia lub nazwy funkcji. Możesz wywołać kompletny wyraz, wybierając opcję **Edytuj**  >  **IntelliSense**  >  **kompletny wyraz**IntelliSense, naciskając klawisz **Ctrl** + **Space**lub wybierając przycisk **Ukończ słowo** na pasku narzędzi edytora.

## <a name="intellisense-options"></a>Opcje IntelliSense

Opcje IntelliSense są domyślnie włączone. Aby je wyłączyć, wybierz opcje **Narzędzia**  >  **Options**  >  **Edytor tekstu** i usuń zaznaczenie opcji **Informacje o parametrach** lub **Lista członków listy** , jeśli nie chcesz, aby lista członków była dostępna.

## <a name="intellisense-icons"></a>Ikony IntelliSense
Ikony w IntelliSense mogą przekazać dodatkowe znaczenie za pomocą modyfikatorów ikon. Są to gwiazdki, kiery i blokady warstwowe na ikonie obiektu, która odpowiednio przekazuje ochronę, wewnętrzną lub prywatną.

|    Ikona    |    Ułatwienia dostępu    |    Opis    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Public Icon — modyfikator](../ide/media/intellisensePublicNoModifier.png)       |    Klasa publiczna    |    Dostęp nie jest ograniczony.   |
| ![Modyfikator ikony chronionej](../ide/media/intellisenseProtectedModifier.png)       |    Klasa chroniona    |    Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej.    |
| ![Modyfikator chronionej ikony wewnętrznej](../ide/media/intellisenseProtectedInternalModifier.png)       |    Chroniona Klasa wewnętrzna    |    Dostęp jest ograniczony do bieżącego zestawu lub typów pochodzących od klasy zawierającej.    |
| ![Wewnętrzny modyfikator ikon](../ide/media/intellisenseInternalModifier.png)       |    Wewnętrzna klasa    |    Dostęp jest ograniczony do bieżącego zestawu.    |
|![Prywatny modyfikator ikon](../ide/media/intellisensePrivateModifier.png)        |    Klasa prywatna    |    Dostęp jest ograniczony do zawierającej klasy lub typów pochodzących od klasy zawierającej w bieżącym zestawie. (Dostępne od języka C# 7,2).    |

## <a name="troubleshoot-intellisense"></a>Rozwiązywanie problemów z funkcją IntelliSense

W niektórych przypadkach opcje IntelliSense mogą nie działać zgodnie z oczekiwaniami.

**Kursor znajduje się poniżej błędu kodu.** Korzystanie z technologii IntelliSense może być niemożliwe, jeśli w kodzie powyżej kursora występuje niepełna funkcja lub inny błąd, ponieważ technologia IntelliSense może nie być w stanie przeanalizować elementów kodu. Można naprawić ten problem, zakomentowując odpowiedni kod.

**Kursor znajduje się w komentarzu do kodu.** Nie można użyć funkcji IntelliSense, jeśli kursor znajduje się w komentarzu w pliku źródłowym.

**Kursor znajduje się w literale ciągu.** Nie można użyć funkcji IntelliSense, jeśli kursor znajduje się w cudzysłowie wokół literału ciągu, jak w poniższym przykładzie:

```cpp
MessageBox( hWnd, "String literal|")
```

**Opcje automatyczne są wyłączone.** Domyślnie technologia IntelliSense działa automatycznie, ale można ją wyłączyć. Nawet jeśli automatyczne uzupełnianie instrukcji jest wyłączone, można wywołać funkcję mechanizmu IntelliSense.

## <a name="see-also"></a>Zobacz też

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Zapis i kod refaktoryzacji (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Dostarczanie komentarzy do kodu XML](reference/generate-xml-documentation-comments.md)

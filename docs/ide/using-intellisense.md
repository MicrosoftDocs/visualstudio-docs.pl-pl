---
title: Informacje o parametrach, listę elementów członkowskich i szybkie informacje
ms.date: 05/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e28c3a09197fd3fe0b45d40a3402f484ab867d7
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684905"
---
# <a name="intellisense-in-visual-studio"></a>Funkcja IntelliSense w programie Visual Studio

Funkcja IntelliSense jest pomoc uzupełniania kodu, która obejmuje pewną liczbę funkcji: Wyświetl listę członków, informacje o parametrach, szybkie informacje i Dokończ wyraz. Te funkcje pozwalają dowiedzieć się więcej o kodzie, którego używasz, śledzić parametry wpisywania i dodawać wywołania do właściwości i metod za pomocą tylko kilku naciśnięć klawiszy.

Wiele aspektów IntelliSense jest specyficzne dla języków. Aby uzyskać więcej informacji na temat technologii IntelliSense dla różnych języków, zobacz tematy wymienione w [Zobacz też](#see-also) sekcji.

## <a name="list-members"></a>Lista składników

Lista prawidłowych elementów członkowskich z typu (lub przestrzeni nazw) pojawia się po wpisaniu znaku wyzwalacza (na przykład kropki (`.`) w kodzie zarządzanym lub `::` w języku C++). Jeśli będziesz kontynuować wpisywanie znaków, lista jest filtrowana w celu uwzględnienia tylko do elementów członkowskich, które zaczynają się od tych znaków, gdy początku *wszelkie* programu word w ramach nazwa zaczyna się od tych znaków. Funkcja IntelliSense wykonuje również "format camel case" dopasowanie, więc nazwę elementu członkowskiego, aby wyświetlić dopasowania można po prostu wpisz pierwszą literę każdego wyrazu formacie camelcase.

Po wybraniu elementu, Wstaw go w kodzie, naciskając klawisz **kartę** lub wciśnięcia spacji. Jeśli wybierzesz element i wpiszesz kropkę, element pojawia się, a po nim kropka, co wywołuje kolejną listę elementów członkowskich. Po wybraniu elementu, ale przed jego wstawieniem, otrzymasz szybkie informacje na jego temat.

Na liście składowych ikona po lewej stronie reprezentuje typ składowej, taki jak przestrzeń nazw, klasa, funkcja lub zmienna. Aby uzyskać listę ikon, zobacz [ikony w widoku klas i przeglądarki obiektów](../ide/class-view-and-object-browser-icons.md). Lista może być dość długa, więc możesz nacisnąć przycisk **PgUp** i **PgDn** można przenieść w górę lub w dół na liście.

![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015_intellisense.png)

Możesz wywołać **List Members** funkcję ręcznie, wpisując **Ctrl**+**"j"**, wybierając **Edytuj**  >  **IntelliSense** > **List Members**, lub wybierając **List Members** na listwie narzędziowej edytora. Gdy jest wywoływana w pustym wierszu lub poza rozpoznawalnym zasięgiem, na liście wyświetlane są symbole w globalnej przestrzeni nazw.

Aby wyłączyć członków listy domyślnie (tak że nie są wyświetlane, chyba że specjalnego wywołania), przejdź do **narzędzia** > **opcje** > **wszystkie języki**i usuń zaznaczenie opcji **automatyczna lista członków**. Jeśli chcesz wyłączyć członków listy tylko dla określonego języka, przejdź do strony **ogólne** ustawień dla tego języka.

Można również przejść do trybu sugestii, w którym tylko wpisany tekst jest umieszczony w kodzie. Na przykład, jeśli wpiszesz identyfikator, który nie jest na liście i naciśnij klawisz **kartę**, uzupełniania tryb wpis zastąpi wpisany identyfikator. Aby przełączyć między trybem uzupełniania a trybem sugestii, naciśnij klawisz **Ctrl**+**Alt**+**miejsca**, lub wybierz **Edytuj**  >  **IntelliSense** > **Przełącz tryb uzupełniania**.

## <a name="parameter-info"></a>Informacje o parametrach

Informacje o parametrach zawierają informacje na temat liczby, nazw i typów parametrów wymaganych przez metodę, parametr typu ogólnego atrybutu (w języku C#) lub szablon (w języku C++).

Parametr pogrubiony wskazuje następny parametr, który jest wymagany podczas wprowadzania funkcji. Dla przeciążonych funkcji, można użyć **się** i **dół** klawiszy strzałek, aby wyświetlić informacje alternatywnych parametrach przeciążeń funkcji.

![Informacje o parametrach](../ide/media/vs2015_param_info.png)

Gdy opisujesz funkcje i parametry za pomocą komentarzy dokumentacji XML, komentarze będą wyświetlane jako informacje o parametrach. Aby uzyskać więcej informacji, zobacz [komentarzy kodu XML, podaj](reference/generate-xml-documentation-comments.md).

Można ręcznie wywołać Parameter Info, wybierając **Edytuj** > **IntelliSense** > **Parameter Info**, naciskając klawisz **Ctrl**  + **Shift**+**miejsca**, lub wybierając **Parameter Info** na listwie narzędziowej edytora.

## <a name="quick-info"></a>Szybkie informacje

Szybkie informacje wyświetlają pełną deklarację dla każdego identyfikatora w kodzie.

![Szybkie informacje w programie Visual Studio](../ide/media/vs2015_quick_info.png)

Po zaznaczeniu elementu członkowskiego w **List Members** polu pojawiają się również szybkie informacje.

![Informacje o parametrach w C&#35; plik kodu](../ide/media/vs2015_paraminfo.png)

Można ręcznie wywołać Quick Info, wybierając **Edytuj** > **IntelliSense** > **Quick Info**, naciskając klawisz **Ctrl** + **I**, lub wybierając **Quick Info** na listwie narzędziowej edytora.

Jeżeli funkcja jest przeciążona, mechanizm IntelliSense może nie wyświetlać informacji dla wszystkich postaci przeciążenia.

Można wyłączyć szybkie informacje dla kodu C++, przechodząc do **narzędzia** > **opcje** > **edytora tekstów** > **C / C++** > **zaawansowane**i ustawienie **Auto Quick Info** do `false`.

## <a name="complete-word"></a>Dokończ wyraz

Dokończ wyraz uzupełnia reszty zmiennej, polecenia lub nazwą funkcji, po wprowadzeniu dostatecznej liczby znaków, aby odróżnić termin. Można wywołać Dokończ wyraz, wybierając **Edytuj** > **IntelliSense** > **Dokończ wyraz**, naciskając klawisz **Ctrl** + **Miejsca**, lub wybierając **Dokończ wyraz** na listwie narzędziowej edytora.

## <a name="intellisense-options"></a>Opcje IntelliSense

Opcje IntelliSense są domyślnie włączone. Aby je wyłączyć, wybierz opcję **narzędzia** > **opcje** > **edytora tekstów** i usuń zaznaczenie opcji **informacje o parametrach**lub **automatyczna lista członków** Jeśli nie chcesz, aby funkcja listy członków.

## <a name="troubleshoot-intellisense"></a>Rozwiązywanie problemów IntelliSense

W niektórych przypadkach opcje IntelliSense mogą nie działać zgodnie z oczekiwaniami.

**Kursor znajduje się poniżej błędu w kodzie.** Nie można używać funkcji IntelliSense, jeśli występuje niedokończona funkcja lub inny błąd występuje w kodzie powyżej kursora, ponieważ IntelliSense może nie być w stanie przeanalizować elementów kodu. Można naprawić ten problem, zakomentowując odpowiedni kod.

**Kursor znajduje się w komentarzu do kodu.** Nie można użyć funkcji IntelliSense, jeśli kursor znajduje się w komentarzu w pliku źródłowym.

**Kursor znajduje się w literale ciągu.** Nie można używać funkcji IntelliSense, jeśli kursor znajduje się w znaki cudzysłowu wokół literału ciągu, jak w poniższym przykładzie:

```cpp
MessageBox( hWnd, "String literal|")
```

**Opcje automatyczne są wyłączone.** Domyślnie technologia IntelliSense działa automatycznie, ale można je wyłączyć. Nawet jeśli automatyczne uzupełnianie instrukcji jest wyłączone, można wywołać funkcję mechanizmu IntelliSense.

## <a name="see-also"></a>Zobacz także

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [Funkcja IntelliSense dla języka JavaScript](../ide/javascript-intellisense.md)
- [Pisanie i Refaktoryzacja kodu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Podaj komentarzy kodu XML](reference/generate-xml-documentation-comments.md)
---
title: Korzystanie z technologii IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- IntelliSense, Complete Word
- IntelliSense, completion mode
- parameter information
- IntelliSense, List Members
- Quick Info
- Parameter Info
- IntelliSense [Visual Studio]
- IntelliSense, suggestion mode
- IntelliSense, Parameter Info
- IntelliSense, customizing
- Complete Word
- IntelliSense
- List Members
ms.assetid: 9fdb489b-8b46-4b92-9ccc-c8f8cc184081
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 735f93b2f900b8681a1e9fee490de8e4b697f9e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656444"
---
# <a name="using-intellisense"></a>Korzystanie z IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Technologia IntelliSense jest ogólnym terminem dla wielu funkcji: elementów członkowskich listy, informacji o parametrach, szybkich informacji i uzupełniania słów. Te funkcje pozwalają dowiedzieć się więcej o kodzie, którego używasz, śledzić wpisywane parametry i dodawać wywołania do właściwości i metod za pomocą zaledwie kilku naciśnięć klawiszy.

 Wiele aspektów IntelliSense jest specyficzne dla języków. Aby uzyskać więcej informacji na temat technologii IntelliSense dla różnych języków, zobacz tematy wymienione w sekcji Zobacz też.

## <a name="list-members"></a>Lista składników
 Lista prawidłowych członków z typu (lub przestrzeni nazw) pojawia się po wpisaniu znaku wyzwalacza (na przykład kropki (`.`) w kodzie zarządzanym lub `::` w programie C++). Jeśli będziesz kontynuować wpisywanie znaków, lista jest filtrowana w celu uwzględnienia tylko elementów członkowskich, które zaczynają się od tych znaków.

 Po wybraniu elementu, wstaw go do kodu za pomocą klawisza TAB lub wciśnięcia spacji. Jeśli wybierzesz element i wpiszesz kropkę, element pojawia się, a po nim kropka, co wywołuje kolejną listę elementów członkowskich. Po wybraniu elementu, ale przed jego wstawieniem, otrzymasz szybkie informacje na jego temat.

 Na liście składowych ikona po lewej stronie reprezentuje typ składowej, taki jak przestrzeń nazw, klasa, funkcja lub zmienna. Aby zapoznać się z listą ikon, zobacz [Widok klasy i Przeglądarka obiektów ikon](../ide/class-view-and-object-browser-icons.md). Lista może być dość długa, więc można nacisnąć klawisz PAGE UP lub PAGE DOWN, aby przejść w górę lub w dół na liście.

 ![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

 Można wywołać funkcję **listy członków** ręcznie, wpisując Ctrl + J, klikając polecenie **Edytuj/IntelliSense/Wyświetl listę członków**lub klikając przycisk **listy członków** na pasku narzędzi edytora. Gdy jest wywoływana w pustym wierszu lub poza rozpoznawalnym zasięgiem, na liście wyświetlane są symbole w globalnej przestrzeni nazw.

 Aby wyłączyć członków listy domyślnie (tak, aby nie były wyświetlane, chyba że jest to określone), przejdź do pozycji **Narzędzia/Opcje/wszystkie języki** i usuń zaznaczenie pozycji **autolista członków**. Jeśli chcesz wyłączyć członków listy tylko dla określonego języka, przejdź do ustawień **ogólnych** dla tego języka.

 Można również przejść do trybu sugestii, w którym tylko wpisany tekst jest umieszczony w kodzie. Na przykład, jeśli wpiszesz identyfikator, który nie jest na liście, i naciśniesz klawisz TAB, w trybie uzupełniania wpis zastąpi wpisany identyfikator. Aby przełączyć się między trybem ukończenia i trybem sugestii, naciśnij kombinację klawiszy CTRL + ALT + SPACJa lub kliknij pozycję **Edytuj/IntelliSense/Przełącz tryb uzupełniania**.

## <a name="parameter-info"></a>Informacje o parametrach
 Informacje o parametrach zawierają informacje na temat liczby, nazw i typów parametrów wymaganych przez metodę, parametr typu ogólnego atrybutu (w języku C#) lub szablon (w języku C++).

 Parametr pogrubiony wskazuje następny parametr, który jest wymagany podczas wprowadzania funkcji. Dla przeciążonych funkcji klawisze strzałek w górę i w dół umożliwiają wyświetlenie informacji o alternatywnych parametrach przeciążeń funkcji.

 ![Informacje o parametrach](../ide/media/vs2015-param-info.png "VS2015_param_Info")

 Gdy opisujesz funkcje i parametry za pomocą komentarzy dokumentacji XML, komentarze będą wyświetlane jako informacje o parametrach. Aby uzyskać więcej informacji, zobacz [dostarczanie komentarzy do kodu XML](../ide/supplying-xml-code-comments.md).

 Możesz ręcznie wywołać informacje o parametrach, klikając **Edytuj informacje IntelliSense/parametry**, wpisując CTRL + SHIFT + Space lub klikając przycisk **Informacje o parametrach** na pasku narzędzi edytora.

## <a name="quick-info"></a>Szybkie informacje
 Szybkie informacje wyświetlają pełną deklarację dla każdego identyfikatora w kodzie.

 ![Szybkie informacje programu Visual Studio](../ide/media/vs2015-quick-info.png "VS2015_Quick_info")

 Po wybraniu elementu członkowskiego z pola **członków listy** pojawiają się również szybkie informacje.

 ![Informacje o parametrach w&#35; pliku kodu języka C](../ide/media/vs2015-paraminfo.png "VS2015_ParamInfo")

 Szybkie informacje można wywołać ręcznie, klikając **Edytuj/IntelliSense/Quick info**, wpisując CTRL + I lub klikając przycisk **szybkie informacje** na pasku narzędzi edytora.

 Jeżeli funkcja jest przeciążona, mechanizm IntelliSense może nie wyświetlać informacji dla wszystkich postaci przeciążenia.

 Szybkie informacje można wyłączyć w obszarze C++ ustawienia **Narzędzia/Opcje/Edytor tekstu/C/C++/Advanced/Auto szybkie informacje** do `false`.

## <a name="complete-word"></a>Dokończ wyraz
 Dokończ wyraz uzupełnia pozostałą część zmiennej, polecenia lub nazwy funkcji, po wprowadzeniu dostatecznej liczby znaków, aby odróżnić termin. Możesz wywołać kompletny wyraz, klikając **Edytuj/IntelliSense/Ukończ wyraz**, wpisując Ctrl + Space lub klikając przycisk **Ukończ słowo** na pasku narzędzi edytora.

## <a name="intellisense-options"></a>Opcje IntelliSense
 Opcje IntelliSense są domyślnie włączone. Aby je wyłączyć, kliknij przycisk **Narzędzia/Opcje/Edytor tekstu** i usuń zaznaczenie **informacji o parametrach** lub **członków listy autolist** , jeśli nie chcesz, aby lista członków nie była dostępna.

## <a name="troubleshooting-intellisense"></a>Rozwiązywanie problemów z technologią IntelliSense
 W niektórych przypadkach opcje IntelliSense mogą nie działać zgodnie z oczekiwaniami.

 **Kursor znajduje się poniżej błędu kodu.** Korzystanie z technologii IntelliSense może być niemożliwe, jeśli w kodzie powyżej kursora występuje niepełna funkcja lub inny błąd, ponieważ technologia IntelliSense może nie być w stanie przeanalizować elementów kodu. Można naprawić ten problem, zakomentowując odpowiedni kod.

 **Kursor znajduje się w komentarzu do kodu.** Nie można użyć funkcji IntelliSense, jeśli kursor znajduje się w komentarzu w pliku źródłowym.

 **Kursor znajduje się w literale ciągu.** Nie można użyć funkcji IntelliSense, jeśli kursor znajduje się w cudzysłowie wokół literału ciągu, jak w poniższym przykładzie:

```
MessageBox( hWnd, "String literal|") )
```

 **Opcje automatyczne są wyłączone.** Domyślnie technologia IntelliSense działa automatycznie, ale można ją wyłączyć. Nawet jeśli automatyczne uzupełnianie instrukcji jest wyłączone, można wywołać funkcję mechanizmu IntelliSense.

## <a name="see-also"></a>Zobacz też
 Funkcja IntelliSense [ C# Visual](../ide/visual-csharp-intellisense.md) IntelliSense [JavaScript](../ide/javascript-intellisense.md) [](../ide/supplying-xml-code-comments.md) z technologią [Visual Basic](../ide/visual-basic-specific-intellisense.md)

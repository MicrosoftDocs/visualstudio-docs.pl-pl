---
title: Za pomocą funkcji IntelliSense | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bb859fe5e66dbfcc1f43dfff3c0744c84066054b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158315"
---
# <a name="using-intellisense"></a>Korzystanie z IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja IntelliSense jest ogólnym terminem dla wielu funkcji: Wyświetl listę członków, informacje o parametrach, szybkie informacje i Dokończ wyraz. Te funkcje pozwalają dowiedzieć się więcej o kodzie, którego używasz, śledzić wpisywane parametry i dodawać wywołania do właściwości i metod za pomocą zaledwie kilku naciśnięć klawiszy.  
  
 Wiele aspektów IntelliSense jest specyficzne dla języków. Aby uzyskać więcej informacji na temat technologii IntelliSense dla różnych języków, zobacz tematy wymienione w sekcji Zobacz też.  
  
## <a name="list-members"></a>Lista składników  
 Lista prawidłowych elementów członkowskich z typu (lub przestrzeni nazw) pojawia się po wpisaniu znaku wyzwalacza (na przykład kropki (`.`) w kodzie zarządzanym lub `::` w języku C++). Jeśli będziesz kontynuować wpisywanie znaków, lista jest filtrowana w celu uwzględnienia tylko elementów członkowskich, które zaczynają się od tych znaków.  
  
 Po wybraniu elementu, wstaw go do kodu za pomocą klawisza TAB lub wciśnięcia spacji. Jeśli wybierzesz element i wpiszesz kropkę, element pojawia się, a po nim kropka, co wywołuje kolejną listę elementów członkowskich. Po wybraniu elementu, ale przed jego wstawieniem, otrzymasz szybkie informacje na jego temat.  
  
 Na liście składowych ikona po lewej stronie reprezentuje typ składowej, taki jak przestrzeń nazw, klasa, funkcja lub zmienna. Aby uzyskać listę ikon, zobacz [widoku klas i przeglądarka obiektów ― ikony](../ide/class-view-and-object-browser-icons.md). Lista może być dość długa, więc można nacisnąć klawisz PAGE UP lub PAGE DOWN, aby przejść w górę lub w dół na liście.  
  
 ![Lista elementów członkowskich programu Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")  
  
 Możesz wywołać **listę elementów członkowskich** funkcję ręcznie, wpisując CTRL + J, klikając **Edit/Intelisense/List Members**, lub klikając **List Members** przycisku w edytorze pasek narzędzi. Gdy jest wywoływana w pustym wierszu lub poza rozpoznawalnym zasięgiem, na liście wyświetlane są symbole w globalnej przestrzeni nazw.  
  
 Aby wyłączyć członków listy domyślnie (tak że nie są wyświetlane, chyba że specjalnego wywołania), przejdź do **narzędzia/Opcje/wszystkie języki** i usuń zaznaczenie opcji **automatyczna lista członków**. Jeśli chcesz wyłączyć członków listy tylko dla określonego języka, przejdź do strony **ogólne** ustawień dla tego języka.  
  
 Można również przejść do trybu sugestii, w którym tylko wpisany tekst jest umieszczony w kodzie. Na przykład, jeśli wpiszesz identyfikator, który nie jest na liście, i naciśniesz klawisz TAB, w trybie uzupełniania wpis zastąpi wpisany identyfikator. Aby przełączyć między trybem uzupełniania a trybem sugestii, naciśnij klawisze CTRL + ALT + SPACJA lub kliknij przycisk **Edytuj/IntelliSense/Przełącz tryb uzupełniania**.  
  
## <a name="parameter-info"></a>Informacje o parametrach  
 Informacje o parametrach zawierają informacje na temat liczby, nazw i typów parametrów wymaganych przez metodę, parametr typu ogólnego atrybutu (w języku C#) lub szablon (w języku C++).  
  
 Parametr pogrubiony wskazuje następny parametr, który jest wymagany podczas wprowadzania funkcji. Dla przeciążonych funkcji klawisze strzałek w górę i w dół umożliwiają wyświetlenie informacji o alternatywnych parametrach przeciążeń funkcji.  
  
 ![Informacje o parametrach](../ide/media/vs2015-param-info.png "VS2015_param_Info")  
  
 Gdy opisujesz funkcje i parametry za pomocą komentarzy dokumentacji XML, komentarze będą wyświetlane jako informacje o parametrach. Aby uzyskać więcej informacji, zobacz [podawania komentarzy kodu XML](../ide/supplying-xml-code-comments.md).  
  
 Można ręcznie wywołać Parameter Info, klikając **Edytuj IntelliSense/Parameter Info**, wpisując CTRL + SHIFT + SPACE lub klikając **Parameter Info** na listwie narzędziowej edytora.  
  
## <a name="quick-info"></a>Szybkie informacje  
 Szybkie informacje wyświetlają pełną deklarację dla każdego identyfikatora w kodzie.  
  
 ![Visual Studio Quick Info](../ide/media/vs2015-quick-info.png "VS2015_Quick_info")  
  
 Po zaznaczeniu elementu członkowskiego w **List Members** polu pojawiają się również szybkie informacje.  
  
 ![Informacje o parametrach w C&#35; pliku z kodem](../ide/media/vs2015-paraminfo.png "VS2015_ParamInfo")  
  
 Można ręcznie wywołać Quick Info, klikając **Edycja/IntelliSense/Quick Info**, wpisując CTRL + I lub klikając **Quick Info** na listwie narzędziowej edytora.  
  
 Jeżeli funkcja jest przeciążona, mechanizm IntelliSense może nie wyświetlać informacji dla wszystkich postaci przeciążenia.  
  
 Można wyłączyć szybkie informacje C++ , ustawiając **narzędzia / Opcje / Edytor tekstu/C/C++zaawansowane/Auto Quick Info** do `false`.  
  
## <a name="complete-word"></a>Dokończ wyraz  
 Dokończ wyraz uzupełnia pozostałą część zmiennej, polecenia lub nazwy funkcji, po wprowadzeniu dostatecznej liczby znaków, aby odróżnić termin. Można wywołać Complete Word klikając **Edycja/IntelliSense/Dokończ wyraz**, wpisując CTRL + SPACE lub klikając **Dokończ wyraz** na listwie narzędziowej edytora.  
  
## <a name="intellisense-options"></a>Opcje IntelliSense  
 Opcje IntelliSense są domyślnie włączone. Aby je wyłączyć, kliknij przycisk **narzędzia/Opcje/Edytor tekstu** i usuń zaznaczenie opcji **informacje o parametrach** lub **automatyczna lista członków** Jeśli nie chcesz, aby funkcja listy członków.  
  
## <a name="troubleshooting-intellisense"></a>Rozwiązywanie problemów z technologią IntelliSense  
 W niektórych przypadkach opcje IntelliSense mogą nie działać zgodnie z oczekiwaniami.  
  
 **Kursor znajduje się poniżej błędu w kodzie.** Nie można używać funkcji IntelliSense, jeśli występuje niedokończona funkcja lub inny błąd występuje w kodzie powyżej kursora, ponieważ IntelliSense może nie być w stanie przeanalizować elementów kodu. Można naprawić ten problem, zakomentowując odpowiedni kod.  
  
 **Kursor znajduje się w komentarzu do kodu.** Nie można użyć funkcji IntelliSense, jeśli kursor znajduje się w komentarzu w pliku źródłowym.  
  
 **Kursor znajduje się w literale ciągu.** Nie można używać funkcji IntelliSense, jeśli kursor znajduje się w znaki cudzysłowu wokół literału ciągu, jak w poniższym przykładzie:  
  
```  
MessageBox( hWnd, "String literal|") )  
```  
  
 **Opcje automatyczne są wyłączone.** Domyślnie technologia IntelliSense działa automatycznie, ale można je wyłączyć. Nawet jeśli automatyczne uzupełnianie instrukcji jest wyłączone, można wywołać funkcję mechanizmu IntelliSense.  
  
## <a name="see-also"></a>Zobacz też  
 [IntelliSense specyficzne dla języka Visual Basic](../ide/visual-basic-specific-intellisense.md)   
 [Funkcja IntelliSense programu Visual C#](../ide/visual-csharp-intellisense.md)   
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Stosowanie komentarzy kodu XML](../ide/supplying-xml-code-comments.md)

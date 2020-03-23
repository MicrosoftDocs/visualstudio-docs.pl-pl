---
title: Debugowanie za pomocą platformy Xamarin
description: Debugowanie jest wspólną i konieczną częścią programowania. Jako dojrzały IDE visual studio dla komputerów Mac zawiera cały zestaw funkcji, aby debugowanie łatwe. Od bezpiecznego debugowania do wizualizacji danych, w tym artykule wyjaśniono, jak używać pełnego potencjału debugowania w programie Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: f62ebe21dcc5eb60927c0bc14617051aba3363e8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985014"
---
# <a name="debugging-with-xamarin"></a>Debugowanie za pomocą platformy Xamarin

Visual Studio dla komputerów Mac ma natywnego debugera umożliwiającego obsługę debugowania dla aplikacji Xamarin.iOS, Xamarin.Mac i Xamarin.Android.

Visual Studio dla komputerów Mac używa [*debugera mono soft*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), który jest zaimplementowany w czasie wykonywania Mono, dzięki czemu visual studio dla komputerów Mac do debugowania kodu zarządzanego na wszystkich platformach.

## <a name="the-debugger"></a>Debuger

Visual Studio dla komputerów Mac używa debugera mono soft do debugowania zarządzanego kodu (C# lub F#) we wszystkich aplikacjach platformy Xamarin. Debuger mono soft różni się od zwykłych debugerów, ponieważ jest to debuger kooperacyjny, który jest wbudowany w środowisko wykonawcze Mono; wygenerowany kod i mono środowiska wykonawczego współpracować z IDE, aby zapewnić środowisko debugowania. Środowisko wykonawcze Mono udostępnia funkcje debugowania za pośrednictwem protokołu przewodowego, o którym można przeczytać więcej [w dokumentacji Mono](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Debugery twarde, takie jak [LLDB](https://lldb.llvm.org/index.html) lub [GDB,](https://www.gnu.org/software/gdb/)kontrolują program bez wiedzy lub współpracy z debugowanego programu, ale nadal mogą być przydatne podczas debugowania aplikacji platformy Xamarin w przypadku konieczności debugowania natywnego kodu systemu iOS lub Android.

## <a name="using-the-debugger"></a>Korzystanie z debugera

Aby rozpocząć debugowanie dowolnej aplikacji, zawsze upewnij się, że konfiguracja jest ustawiona na **Debugowanie**. Konfiguracja debugowania zapewnia pomocny zestaw narzędzi do obsługi debugowania, takich jak punkty przerwania, przy użyciu wizualizatorów danych i wyświetlania stosu wywołań:

![Konfiguracja debugowania](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Ustawianie punktu przerwania

Aby ustawić punkt przerwania w ide, kliknij na marginesie edytora, obok numeru wiersza kodu, w którym chcesz złamać:

![Ustawianie punktu przerwania na marginesie](media/debugging-image0.png)

Można wyświetlić wszystkie punkty przerwania, które zostały ustawione w kodzie, przechodząc do **punktu przerwania:**

![Lista punktów przerwania](media/debugging-image0a.png)

## <a name="start-debugging"></a>Rozpocznij debugowanie

Aby rozpocząć debugowanie, wybierz urządzenie docelowe lub podobny/emulator w ide:

![Wybierz urządzenie docelowe](media/debugging-image1.png)

Następnie wdrożyć aplikację, naciskając przycisk **Play,** lub **Cmd + return**. Po trafieniu punktu przerwania kod zostanie wyróżniony na żółto:

![Wyróżnienie pokazujące punkt przerwania zostało trafione](media/debugging-image2.png)

Narzędzia debugowania, takie jak ten używany do sprawdzania wartości obiektów, mogą być używane w tym momencie, aby uzyskać więcej informacji na temat tego, co dzieje się w kodzie:

![Wizualizacje debugowania](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Warunkowe punkty przerwania

Można również ustawić reguły dyktujące okoliczności, w których powinien wystąpić punkt przerwania, jest to nazywane dodawaniem *warunkowego punktu przerwania*. Aby ustawić warunkowy punkt przerwania, należy uzyskać dostęp do **okna Właściwości punktu przerwania,** które można wykonać na dwa sposoby:

* Aby dodać nowy warunkowy punkt przerwania, kliknij prawym przyciskiem myszy margines edytora, po lewej stronie numeru wiersza dla kodu, na którym chcesz ustawić punkt przerwania, i wybierz pozycję Nowy punkt przerwania:

 ![Menu kontekstowe punktu przerwania](media/debugging-image4.png)

* Aby dodać warunek do istniejącego punktu przerwania, kliknij prawym przyciskiem myszy punkt przerwania i wybierz polecenie **Właściwości punktu przerwania**lub w **panelu Breakpoints Pad**wybierz przycisk Edytuj punkt przerwania zilustrowany poniżej:

 ![Edytowanie istniejącego punktu przerwania w programie Breakpoints Pad](media/debugging-image5.png)

Następnie można wprowadzić warunek, w którym ma wystąpić punkt przerwania:

 ![Edytowanie warunków punktu przerwania](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Przechodzenie przez kod

Po osiągnięciu punktu przerwania narzędzia debugowania umożliwiają uzyskanie kontroli nad wykonaniem programu. Visual Studio dla komputerów Mac wyświetli cztery przyciski, co pozwala na uruchamianie i krok po kroku przez kod. W programie Visual Studio dla komputerów Mac będą wyglądać następująco:

 ![Przyciski do przechodzenia przez kod](media/debugging-image7.png)

Oto cztery przyciski:

* **Odtwórz** — rozpocznie się wykonywanie kodu, aż do następnego punktu przerwania.
* **Krok —** spowoduje to wykonanie następnego wiersza kodu. Jeśli następny wiersz jest wywołanie funkcji, Step Over wykona funkcję i zatrzyma się w następnym wierszu kodu *po* funkcji.
* **Krok do** — spowoduje to również wykonanie następnego wiersza kodu. Jeśli następny wiersz jest wywołaniem funkcji, Step Into zatrzyma się w pierwszym wierszu funkcji, co pozwala kontynuować debugowanie wiersza po wierszu funkcji. Jeśli następny wiersz nie jest funkcją, będzie zachowywać się tak samo jak Step Over.
* **Wyjdź** — spowoduje to powrót do wiersza, w którym została wywołana bieżąca funkcja.

## <a name="debugging-monos-class-libraries"></a>Debugowanie bibliotek klas Mono

Produkty platformy Xamarin dostarczane z kodem źródłowym bibliotek klasy Mono i można użyć tego do pojedynczego kroku z debugera, aby sprawdzić, jak rzeczy działają pod maską.

Ponieważ ta funkcja zużywa więcej pamięci podczas debugowania, jest domyślnie wyłączona.

Aby włączyć tę funkcję, przejdź do **programu Visual Studio for Mac > Preferencje > debugera** i upewnij się, że tylko kod projektu**debugowania; nie wchodź do kodu framework.**" opcja jest **niezaznaczona,** jak pokazano poniżej:

![Nie wchodź do opcji kodu framework](media/debugging-image8.png)

## <a name="see-also"></a>Zobacz też

- [Debugowanie w programie Visual Studio (w systemie Windows)](/visualstudio/debugger/)

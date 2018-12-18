---
title: Debugowanie za pomocą platformy Xamarin
description: Debugowanie jest typowe i jest to konieczne, część programowania. Jako dojrzała środowiska IDE programu Visual Studio dla komputerów Mac zawiera całego zestawu funkcji Łatwe debugowanie. Z bezpiecznego debugowania, Wizualizacja danych, w tym artykule wyjaśniono, jak użyć pełnego potencjału debugowania w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: e17a423e9db6826c8cc693e1c75c75bb067a19e8
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295296"
---
# <a name="debugging-with-xamarin"></a>Debugowanie za pomocą platformy Xamarin

Visual Studio dla komputerów Mac ma debuger natywny umożliwiająca obsługę debugowania dla aplikacji platformy Xamarin.iOS, Xamarin.Mac i projektami interfejsu Xamarin.Android.

Program Visual Studio for Mac używa [ *nietrwałego debugera Mono*](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), którego jest stosowana do środowiska uruchomieniowego Mono, co program Visual Studio for Mac można debugować kodu zarządzanego na wszystkich platformach.

## <a name="the-debugger"></a>Debuger

Program Visual Studio dla komputerów Mac używa nietrwałego debugera Mono do debugowania zarządzanego (C# lub F#) kodu we wszystkich aplikacjach platformy Xamarin. Debugera Mono nietrwałego różni się od zwykłych debugery, jest debugera współpracy, która jest wbudowana w środowiska uruchomieniowego Mono; wygenerowany kod i środowiska uruchomieniowego Mono współpracować ze środowiskiem IDE, aby zapewnić środowisko debugowania. Środowisko uruchomieniowe Mono uwidacznia funkcje debugowania przy użyciu protokołu o komunikacji sieciowej, której możesz przeczytać więcej na temat [w dokumentacji platformy Mono](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Twarde debugery, takich jak [LLDB]( http://lldb.llvm.org/index.html) lub [GDB]( https://www.gnu.org/software/gdb/), sterowania programem bez wiedzy lub współpracy z debugowanym programem, ale nadal może być przydatne podczas debugowania aplikacji platformy Xamarin w zdarzeniu, trzeba debugowania natywnych dla systemów iOS, lub kodu dla systemu Android.

## <a name="using-the-debugger"></a>Za pomocą debugera

Aby rozpocząć debugowanie aplikacji, zawsze upewnij się, że konfiguracja jest ustawiona na **debugowania**. Konfiguracja debugowania udostępnia przydatne zestaw narzędzi do obsługi debugowania, takie jak punkty przerwania, przy użyciu wizualizatorów danych i wyświetlanie stosu wywołań:

![Konfiguracja debugowania](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Ustawienie punktu przerwania

Aby ustawić punkt przerwania w środowisku IDE, kliknij obszar margines edytora obok numer wiersza kodu, w którym chcesz przerwać:

![Ustawianie punktu przerwania na marginesie](media/debugging-image0.png)

Możesz wyświetlić wszystkie punkty przerwania, które zostały ustawione w kodzie, przechodząc do **Konsola punktów przerwania**:

![Lista punktów przerwania](media/debugging-image0a.png)

## <a name="start-debugging"></a>Rozpocznij debugowanie

Aby rozpocząć debugowanie, wybierz urządzenie docelowe lub podobne/emulatora w środowisku IDE:

![Wybierz urządzenie docelowe](media/debugging-image1.png)

Następnie Wdróż aplikację, naciskając klawisz **Odtwórz** przycisku lub **Cmd + return**. Po osiągnięciu punktu przerwania kod będzie wyróżniony żółtym:

![Został trafiony punkt przerwania przedstawiający wyróżnienia](media/debugging-image2.png)

Debugowanie z narzędziami, takimi jak użytym do sprawdzenia wartości obiektów, można w tym momencie Aby uzyskać więcej informacji o tym, co się dzieje w kodzie:

![Debugowanie wizualizacji](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Warunkowe punkty przerwania

Można również ustawić zasady dyktowanie okoliczności, w których powinny być wykonywane punkt przerwania, jest to nazywane Dodawanie *warunkowego punktu przerwania*. Aby ustawić warunkowego punktu przerwania, dostęp do **okna Właściwości punktu przerwania**, które można zrobić na dwa sposoby:

* Aby dodać nowe warunkowego punktu przerwania, kliknij prawym przyciskiem myszy na marginesu edytora, numer wiersza dla kodu, który chcesz ustawić punkt przerwania, po lewej stronie, a następnie wybierz nowy punkt przerwania:

 ![Menu kontekstowe punktu przerwania](media/debugging-image4.png)

* Aby dodać warunek istniejącym punkcie przerwania, kliknij prawym przyciskiem myszy punkt przerwania, a następnie wybierz pozycję **właściwości punktu przerwania**, lub w **Konsola punktów przerwania**, wybierz przycisk Edytuj punkt przerwania, przedstawiono poniżej:

 ![Edytuj istniejący punkt przerwania w konsoli punktów przerwania](media/debugging-image5.png)

Następnie możesz wprowadzić warunek, pod którym ma punkt przerwania, wystąpienia:

 ![Edytuj warunki punktu przerwania](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Krokowe wykonywanie kodu

Po osiągnięciu punktu przerwania narzędzi debugowania pozwalają uzyskać kontrolę nad wykonywania programu. Program Visual Studio for Mac wyświetli cztery przyciski, co pozwala na uruchamianie i przejść przez kod. W programie Visual Studio dla komputerów Mac będzie wyglądać następująco:

 ![Przyciski, aby przejść przez kod](media/debugging-image7.png)

Poniżej przedstawiono cztery przyciski:

*   **Odtwórz** — spowoduje to rozpoczęcie wykonywania kodu, aż do następnego punktu przerwania.
*   **Step Over** — spowoduje to wykonanie następnego wiersza kodu. Jeśli następny wiersz jest wywołanie funkcji, Step Over spowoduje wykonanie funkcji, a zostanie zatrzymane w następnym wierszu kodu *po* funkcji.
*   **Step Into** — spowoduje to również wykonanie następnego wiersza kodu. Jeśli następny wiersz jest wywołanie funkcji, Step Into przestanie w pierwszym wierszu funkcji, co pozwala na dalsze wiersz po wierszu debugowanie funkcji. Jeśli następny wiersz nie jest funkcją, będzie ona działać taka sama jak Step Over.
*   **Step Out** — spowoduje to zwrócenie do wiersza gdy wywołana została funkcja bieżąca.

## <a name="debugging-monos-class-libraries"></a>Debugowanie biblioteki klas platformy Mono firmy

Produkty platformy Xamarin są dostarczane z kodu źródłowego dla bibliotek klas firmy Mono i służy to do pojedynczego kroku z debugera, aby sprawdzić, jak wszystko działa pod maską.

Ponieważ ta funkcja zużywa więcej pamięci podczas debugowania, jego jest domyślnie wyłączona.

Aby włączyć tę funkcję, przejdź do **programu Visual Studio dla komputerów Mac > Preferencje > debuger** i upewnij się, że "**Debuguj tylko kod projektu nie wkraczaj do kodu struktury.** " opcja jest **niezaznaczone**, jak pokazano poniżej:

![Nie wkraczaj do framework kod — opcja](media/debugging-image8.png)

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio (w Windows)](/visualstudio/debugger/)
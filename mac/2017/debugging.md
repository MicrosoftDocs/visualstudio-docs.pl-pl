---
title: Debugowanie za pomocą platformy Xamarin
description: Debugowanie jest powszechną i niezbędną częścią programowania. Jako dojrzały IDE Visual Studio dla komputerów Mac zawiera cały zestaw funkcji, które ułatwiają debugowanie. Z bezpiecznego debugowania do wizualizacji danych w tym artykule wyjaśniono, jak używać pełnego potencjału debugowania w Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: f62ebe21dcc5eb60927c0bc14617051aba3363e8
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74985014"
---
# <a name="debugging-with-xamarin"></a>Debugowanie za pomocą platformy Xamarin

Visual Studio dla komputerów Mac ma natywny debuger umożliwiający obsługę debugowania dla aplikacji Xamarin. iOS, Xamarin. Mac i Xamarin. Android.

Visual Studio dla komputerów Mac używa [*debugera miękkiego mono*](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), który jest implementowany w środowisku uruchomieniowym mono, umożliwiając Visual Studio dla komputerów Mac Debugowanie kodu zarządzanego na wszystkich platformach.

## <a name="the-debugger"></a>Debuger

Visual Studio dla komputerów Mac używa debugera miękkiego mono do debugowania zarządzanego koduC# ( F#lub) we wszystkich aplikacjach platformy Xamarin. Program mono Soft Debugger różni się od zwykłych debugerów, ponieważ jest to współpracujący debuger, który jest wbudowany w środowisko uruchomieniowe mono. wygenerowany kod i środowisko uruchomieniowe mono współdziałają z IDE w celu zapewnienia środowiska debugowania. Środowisko uruchomieniowe mono udostępnia funkcje debugowania za pomocą protokołu przewodowego, który można dowiedzieć [się więcej na temat dokumentacji programu mono](https://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Mocne debugery, takie jak [LLDB](https://lldb.llvm.org/index.html) lub [GDB](https://www.gnu.org/software/gdb/), kontrolują program bez wiedzy ani współpracy z debugowanego programu, ale nadal mogą być przydatne podczas debugowania aplikacji platformy Xamarin w przypadku, gdy wymagane jest debugowanie natywnego kodu dla systemu iOS lub Android.

## <a name="using-the-debugger"></a>Korzystanie z debugera

Aby rozpocząć debugowanie aplikacji, zawsze upewnij się, że konfiguracja jest ustawiona na **Debuguj**. Konfiguracja debugowania oferuje przydatny zestaw narzędzi do obsługi debugowania, takich jak punkty przerwania, używanie wizualizatorów danych i wyświetlanie stosu wywołań:

![Konfiguracja debugowania](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Ustawienie punktu przerwania

Aby ustawić punkt przerwania w środowisku IDE, kliknij obszar marginesu w edytorze obok numeru wiersza kodu, w którym chcesz przerwać:

![Ustawianie punktu przerwania na marginesie](media/debugging-image0.png)

Wszystkie punkty przerwania, które zostały ustawione w kodzie, można wyświetlić, przechodząc do **konsoli punkty przerwania**:

![Lista punktów przerwania](media/debugging-image0a.png)

## <a name="start-debugging"></a>Rozpocznij debugowanie

Aby rozpocząć debugowanie, wybierz urządzenie docelowe lub podobną/emulator w środowisku IDE:

![Wybierz urządzenie docelowe](media/debugging-image1.png)

Następnie wdróż aplikację, naciskając przycisk **Odtwórz** lub **polecenie cmd + Return**. Po trafieniu punktu przerwania kod zostanie wyróżniony żółty:

![Wyróżnij wyświetlany punkt przerwania został trafiony](media/debugging-image2.png)

Aby uzyskać więcej informacji na temat tego, co dzieje się w kodzie, można użyć narzędzi debugowania, takich jak używany do sprawdzania wartości obiektów.

![Debugowanie wizualizacji](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Warunkowe punkty przerwania

Można również ustawić reguły określające sytuacje, w których powinien wystąpić punkt przerwania, tak jak w przypadku dodawania *warunkowego punktu przerwania*. Aby ustawić warunkowy punkt przerwania, uzyskaj dostęp do **okno właściwości punktu przerwania**, który można wykonać na dwa sposoby:

* Aby dodać nowy warunkowy punkt przerwania, kliknij prawym przyciskiem myszy na marginesie edytora, po lewej stronie numeru wiersza dla kodu, dla którego chcesz ustawić punkt przerwania, a następnie wybierz polecenie Nowy punkt przerwania:

 ![Menu kontekstowe punktu przerwania](media/debugging-image4.png)

* Aby dodać warunek do istniejącego punktu przerwania, kliknij prawym przyciskiem myszy punkt przerwania i wybierz polecenie **właściwości punktu przerwania**, lub w **konsoli punkty przerwania**wybierz przycisk Edytuj punkt przerwania przedstawiony poniżej:

 ![Edytuj istniejący punkt przerwania w konsoli punkty przerwania](media/debugging-image5.png)

Następnie możesz wprowadzić warunek, pod którym ma nastąpić punkt przerwania:

 ![Edytuj warunki punktu przerwania](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Krokowe przechodzenie przez kod

Po osiągnięciu punktu przerwania narzędzia debugowania umożliwiają uzyskanie kontroli nad wykonywaniem programu. W Visual Studio dla komputerów Mac zostaną wyświetlone cztery przyciski, które umożliwiają wykonywanie kroków i przechodzenie przez kod. W Visual Studio dla komputerów Mac będą wyglądać następująco:

 ![Przyciski umożliwiające przechodzenie przez kod](media/debugging-image7.png)

Poniżej przedstawiono cztery przyciski:

* **Odtwórz** — spowoduje to rozpoczęcie wykonywania kodu aż do następnego punktu przerwania.
* **Przekroczenie** — spowoduje to wykonanie następnego wiersza kodu. Jeśli następnym wierszem jest wywołanie funkcji, krok powyżej wykona funkcję i zatrzyma się w następnym wierszu kodu *po* funkcji.
* **Wkrocz do** -spowoduje to również wykonanie następnego wiersza kodu. Jeśli następnym wierszem jest wywołanie funkcji, krok do zostanie zatrzymany w pierwszym wierszu funkcji, co pozwoli na kontynuowanie debugowania między wierszami funkcji. Jeśli następny wiersz nie jest funkcją, będzie działać tak samo jak krok powyżej.
* **Wyjdź** — spowoduje to powrót do wiersza, w którym wywołano bieżącą funkcję.

## <a name="debugging-monos-class-libraries"></a>Debugowanie bibliotek klas mono

Produkty platformy Xamarin są dostarczane z kodem źródłowym dla bibliotek klas mono i można ich użyć do pojedynczego kroku z debugera, aby sprawdzić, jak działają elementy na wyciągu.

Ponieważ ta funkcja zużywa więcej pamięci podczas debugowania, jest domyślnie wyłączona.

Aby włączyć tę funkcję, przejdź do **Visual Studio dla komputerów Mac > preferencji > debugerze** i upewnij się, że "**Debugowanie kodu projektu; nie wkraczaj do kodu struktury ".** opcja jest **niezaznaczona**, jak pokazano poniżej:

![Nie wkraczaj do kodu struktury — opcja](media/debugging-image8.png)

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio (w systemie Windows)](/visualstudio/debugger/)

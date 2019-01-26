---
title: Debugowanie lub wyłączanie kodu projektu w projektancie XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 972ca9b7d2041284435f4ed7dacadddd7bb5027a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966572"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>Debugowanie lub wyłączanie kodu projektu w projektancie XAML

W wielu przypadkach nieobsłużonych wyjątków z **XAML** designer może być spowodowany przez kod projektu, próby uzyskania dostępu do właściwości lub metody, które zwracać różne wartości, i pracować w inny sposób, gdy aplikacja działa w projektancie. Rozwiązania tych wyjątków dzięki możliwości debugowania kodu projektu w innym wystąpieniu programu Visual Studio lub czasowo uniemożliwić wyjątki po wyłączeniu kodu projektu w projektancie.

Zawiera kod projektu:

-   Kontrolki niestandardowe i kontrolki użytkownika

-   Biblioteki klas

-   Konwertery wartości

-   Powiązania względem danych czasu projektowania wygenerowane z kodu projektu

Po wyłączeniu kodu projektu programu Visual Studio zawiera symbole zastępcze. Na przykład programu Visual Studio zawiera nazwę właściwości do powiązania, gdzie dane są już dostępne lub symbol zastępczy dla formantu, który nie jest już uruchomiony.

![Nieobsługiwany wyjątek w oknie dialogowym](../designers/media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Aby określić, jeśli kod projektu powoduje wyjątek

1.  W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby załadować ponownie projektanta** łącza.

2.  Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie** Aby skompilować i uruchomić aplikację.

     Jeśli aplikacja zostanie skompilowana i zostanie wykonane pomyślnie, wyjątek czasu projektowania może być spowodowane przez działanie kodu projektu w projektancie.

## <a name="to-debug-project-code-running-in-the-designer"></a>Aby debugować kod projektu w Projektancie

1.  W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i załadować ponownie projektanta** łącza.

2.  W Menedżerze zadań Windows, wybierz **Zakończ zadanie** przycisk, aby zamknąć wszystkie wystąpienia projektanta XAML programu Visual Studio, które są aktualnie uruchomione.

     ![Wystąpienia projektanta XAML w Menedżer zadań](../designers/media/xaml_taskmanager.png)

3.  W programie Visual Studio Otwórz stronę XAML, który zawiera kod lub formant, który chcesz debugować.

4.  Otwórz nowe wystąpienie programu Visual Studio, a następnie otwórz drugie wystąpienie projektu.

5.  Ustaw punkt przerwania w kodzie projektu.

6.  W wystąpieniu programu Visual Studio, na pasku menu wybierz **debugowania** > **dołączyć do procesu**.

7.  W **dołączyć do procesu** okna dialogowego w **dostępne procesy** , wybierz **XDesProc.exe**, a następnie wybierz **Dołącz** przycisku.

     ![Proces projektanta XAML](../designers/media/xaml_attach.png)

     Jest to proces projektanta XAML w pierwszym wystąpieniu programu Visual Studio.

8.  W pierwszej kolejności programu Visual Studio, na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.

     Możesz teraz wejść w kodzie, w którym jest uruchomiony w projektancie.

## <a name="to-disable-project-code-in-the-designer"></a>Aby wyłączyć kodu projektu w Projektancie

-   W oknie dialogowym nieobsługiwany wyjątek, wybierz **kliknij tutaj, aby wyłączyć uruchamianie kodu projektu i załadować ponownie projektanta** łącza.

-   Możesz również na pasku narzędzi w **projektanta XAML**, wybierz **Wyłącz kod projektu** przycisku.

     ![Przycisk Wyłącz kod projektu](../designers/media/xaml_disablecode.png)

     Można przełączać się przycisk ponownie, aby ponownie włączyć kod projektu.

    > [!NOTE]
    > Dla projektów przeznaczonych dla ARM lub X64 procesorów, Visual Studio nie można uruchomić kod projektu w projektancie, więc **Wyłącz kod projektu** przycisk jest niedostępny w projektancie.

-   Jedną z opcji powoduje, że projektanta aby załadować ponownie, a następnie wyłącz cały kod dla skojarzonego projektu.

    > [!NOTE]
    > Wyłączanie kodu projektu może prowadzić do utraty danych w czasie projektowania. Alternatywą jest, aby debugować kod uruchomiony w projektancie.

## <a name="control-display-options"></a>Opcje wyświetlania kontrolki

> [!NOTE]
> **Kontrolowanie opcji wyświetlania** jest dostępna tylko dla aplikacji Universal Windows Platform, których platformą docelową Windows 10 Fall Creators Update (kompilacja 16299) lub nowszej. **Opcje wyświetlania kontrolki** funkcja jest dostępna w programie Visual Studio 2017 w wersji 15.9 lub nowszej. 

W Projektancie XAML możesz zmienić opcje wyświetlania kontrolki, aby wyświetlić tylko kontrolek platformy z zestawu Windows SDK. Może to zwiększyć niezawodność projektanta XAML.

Aby zmienić opcje wyświetlania kontrolki, kliknij ikonę w lewej dolnej części okna projektanta, a następnie wybierz opcję w obszarze **opcje wyświetlania kontrolki**:

![Opcje wyświetlania kontrolki](../designers/media/control_display_options.png)

Po wybraniu **tylko formanty wyświetlania platformy**, formanty użytkownika klienta wszystkie kontrolki niestandardowe pochodzące z zestawów SDK, i uzyskać więcej informacji, nie będą renderować całości. Zamiast tego są zastępowane przez rezerwowy formanty, aby zademonstrować, rozmiar i położenie formantu.

## <a name="see-also"></a>Zobacz także

- [Projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md)

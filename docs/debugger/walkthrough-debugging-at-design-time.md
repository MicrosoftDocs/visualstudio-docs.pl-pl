---
title: Debugowanie w czasie projektowania | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf4a781bee0d0ccb1acd7d9c6b035acac603aea3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696704"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Debugowanie w czasie projektowania w programie Visual Studio (C#, C++, Visual Basic F#)

Debugowanie kodu w czasie projektowania, a nie podczas aplikacja jest uruchomiona, można użyć **bezpośrednie** okna.

Aby debugować kod XAML związany z aplikacji przy użyciu projektanta XAML, takich jak kod powiązania danych, można użyć **debugowania** > **dołączyć do procesu**.

## <a name="use-the-immediate-window"></a>Użyj okna bezpośredniego

Możesz użyć programu Visual Studio **bezpośrednie** okna do wykonania funkcji lub podprocedury bez uruchamiania aplikacji. Jeśli funkcja lub podprocedura zawiera punkt przerwania, program Visual Studio spowoduje przerwanie w punkcie przerwania. Można następnie użyć okien debugera do sprawdzenia stanu programu. Ta funkcja jest nazywana *debugowanie w czasie projektowania*.

Poniższy przykład jest w języku Visual Basic. Można również użyć **bezpośrednie** okna w czasie projektowania w C#, F#oraz aplikacje w języku C++.

1. Wklej następujący kod do pustej aplikacji konsoli języka Visual Basic:

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. Ustaw punkt przerwania w wierszu **funkcja kończąca**.

1. Otwórz **bezpośrednie** okna, wybierając **debugowania** > **Windows** > **bezpośrednie**. Typ `?MyFunction` okna, a następnie naciśnij klawisz **Enter**.

   Punkt przerwania jest trafień i wartość **MyFunction** w **lokalne** okno jest **1**. Stos wywołań i innych oknach debugowania można sprawdzić, gdy aplikacja działa w trybie przerwania.

1. Wybierz **Kontynuuj** na pasku narzędzi programu Visual Studio. Aplikacja zostaje zakończona, i **1** jest zwracany w **bezpośrednie** okna. Upewnij się, że jesteś nadal w trybie projektowania.

1. Typ `?MyFunction` w **bezpośrednie** ponownie okno, a następnie naciśnij klawisz **Enter**. Punkt przerwania jest trafień i wartość **MyFunction** w **lokalne** okno jest **2**.

1. Bez zaznaczania **Kontynuuj**, typ `?MySub()` w **bezpośrednie** okna, a następnie naciśnij klawisz **Enter**. Punkt przerwania jest trafień i wartość **MyFunction** w **lokalne** okno jest **3**. Można sprawdzić stan aplikacji, gdy aplikacja działa w trybie przerwania.

1. Wybierz **nadal**. Punkt przerwania jest ponownie trafień i wartość **MyFunction** w **lokalne** okno jest teraz **2**. **Bezpośrednie** zwraca okna **wyrażenie zostało ocenione i nie ma wartości**.

1. Wybierz **Kontynuuj** ponownie. Aplikacja zostaje zakończona, i **2** jest zwracany w **bezpośrednie** okna. Upewnij się, że jesteś nadal w trybie projektowania.

1. Aby wyczyścić zawartość **bezpośrednie** okna, kliknij prawym przyciskiem myszy w oknie i wybierz **Wyczyść wszystko**.

## <a name="attach-to-an-app-from-the-xaml-designer"></a>Dołącz do aplikacji przy użyciu projektanta XAML

W niektórych scenariuszach powiązania dane deklaratywne może pomóc debugowania kodzie w Projektancie XAML.

1. W projekcie programu Visual Studio Dodaj nową stronę XAML, takich jak *temp.xaml*. Nowa strona XAML należy pozostawić pusty.

1. Skompiluj rozwiązanie.

1. Otwórz *temp.xaml*, który ładuje projektanta XAML *XDesProc.exe*, lub *UwpSurface.exe* w aplikacji platformy uniwersalnej systemu Windows.

1. Otwórz nowe wystąpienie programu Visual Studio. W nowym wystąpieniu wybierz **debugowania** > **dołączyć do procesu**.

1. W **dołączyć do procesu** okno dialogowe, wybierz opcję projektanta proces z **dostępne procesy** listy.

   Dla platformy UWP projekty przeznaczone dla Windows kompilacji 16299 lub nowszego, proces projektanta *UwpSurface.exe*. WPF lub platforma UWP wersji wcześniejszych niż 16299, proces projektanta jest *XDesProc.exe*.

1. Upewnij się, że **dołączyć do** pole jest ustawione na wpisz poprawny kod dla używanej wersji platformy .NET, takich jak **kodu zarządzanego (CoreCLR)**.

1. Wybierz **dołączyć**.

1. Gdy dołączony do procesu, przełącz się do innego wystąpienia programu Visual Studio, a następnie ustawić punkty przerwania, w którym chcesz debugować kod związany z Twojej aplikacji.

   Na przykład można ustawić punkt przerwania w kodzie konwerter typu dla następujących XAML, który wiąże TextBlock w czasie projektowania.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Po załadowaniu strony zostanie osiągnięty punkt przerwania.

## <a name="see-also"></a>Zobacz także
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
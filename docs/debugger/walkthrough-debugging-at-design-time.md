---
title: Debugowanie w czasie projektowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/10/2019
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
ms.openlocfilehash: beb16ae52f880e31bd19a185d47b13c02026752f
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916141"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Debugowanie w czasie projektowania w programie Visual StudioC#( C++,/CLI, Visual Basic F#,)

Debugowanie kodu w czasie projektowania, a nie podczas aplikacja jest uruchomiona, można użyć **bezpośrednie** okna.

Aby debugować kod XAML za aplikacją z projektanta XAML, takich jak scenariusze powiązań danych deklaratywnych, można użyć > **debugowania** **dołączania do procesu**.

## <a name="use-the-immediate-window"></a>Użyj okna bezpośredniego

Możesz użyć programu Visual Studio **bezpośrednie** okna do wykonania funkcji lub podprocedury bez uruchamiania aplikacji. Jeśli funkcja lub podprocedura zawiera punkt przerwania, program Visual Studio spowoduje przerwanie w punkcie przerwania. Można następnie użyć okien debugera do sprawdzenia stanu programu. Ta funkcja jest nazywana *debugowanie w czasie projektowania*.

Poniższy przykład jest w języku Visual Basic. Możesz również użyć okna **bezpośredniego** w czasie projektowania w C#aplikacjach, F#i C++/CLI.

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

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Debuguj niestandardową kontrolkę XAML w czasie projektowania przez dołączenie do projektanta XAML

1. Otwórz rozwiązanie lub projekt w programie Visual Studio.

1. Kompiluj rozwiązanie/projekt.

1. Otwórz stronę XAML zawierającą kontrolkę niestandardową, którą chcesz debugować.

   W przypadku projektów platformy UWP przeznaczonych dla kompilacji systemu Windows 16299 lub nowszego ten krok spowoduje uruchomienie procesu *UwpSurface. exe* . W przypadku wersji WPF lub platformy UWP starszych niż kompilacja systemu Windows 16299 w tym kroku zostanie uruchomiony proces *XDesProc. exe* .

1. Otwórz drugie wystąpienie programu Visual Studio. Nie otwieraj rozwiązania lub projektu w drugim wystąpieniu.

1. W drugim wystąpieniu programu Visual Studio Otwórz menu **Debuguj** i wybierz polecenie **Dołącz do procesu...** .

1. W zależności od typu projektu (zobacz poprzednie kroki) wybierz z listy dostępnych procesów pozycję *UwpSurface. exe* lub proces *XDesProc. exe* .

1. W polu **Dołącz do** w oknie dialogowym **Dołącz do procesu** wybierz odpowiedni typ kodu dla kontrolki niestandardowej, która ma być debugowana.

   Jeśli kontrolka niestandardowa została zapisywana w języku .NET, wybierz odpowiedni typ kodu platformy .NET, taki jak **Managed (CoreCLR)** . Jeśli kontrolka niestandardowa została zapisywana C++, wybierz opcję **natywny**.

1. Dołącz drugie wystąpienie programu Visual Studio, klikając przycisk **Dołącz** .

1. W drugim wystąpieniu programu Visual Studio Otwórz pliki kodu skojarzone z kontrolką niestandardową, którą chcesz debugować. Pamiętaj, aby po prostu otworzyć pliki, a nie całe rozwiązanie lub projekt.

1. Umieść niezbędne punkty przerwania w poprzednio otwartych plikach.

1. W pierwszym wystąpieniu programu Visual Studio Zamknij stronę XAML zawierającą kontrolkę niestandardową, którą chcesz debugować (ta sama strona została otwarta w poprzednich krokach).

1. W pierwszym wystąpieniu programu Visual Studio Otwórz stronę XAML zamkniętą w poprzednim kroku. Spowoduje to zatrzymanie debugera z pierwszego punktu przerwania ustawionego w drugim wystąpieniu programu Visual Studio.

1. Debuguj kod w drugim wystąpieniu programu Visual Studio.

## <a name="see-also"></a>Zobacz także
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
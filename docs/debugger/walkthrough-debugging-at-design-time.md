---
title: Debugowanie w czasie projektowania | Microsoft Docs
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
ms.openlocfilehash: 8bc5d08e8b0ae71acb846e1e863e24e8b8def0ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183564"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Debugowanie w czasie projektowania w programie Visual Studio (C#, C++/CLI, Visual Basic, F #)

Aby debugować kod w czasie projektowania, a nie w czasie, gdy aplikacja jest uruchomiona, można użyć okna **bezpośredniego** .

Aby debugować kod XAML za aplikacją z projektanta XAML, takich jak scenariusze powiązań danych deklaratywnych, można użyć **Debug**  >  **dołączania debugowania do procesu**.

## <a name="use-the-immediate-window"></a>Korzystanie z okna bezpośredniego

Możesz użyć **bezpośredniego** okna programu Visual Studio, aby wykonać funkcję lub procedurę podprocedury bez uruchamiania aplikacji. Jeśli funkcja lub podprocedura zawiera punkt przerwania, program Visual Studio przerwie się w punkcie przerwania. Można następnie użyć okien debugera do sprawdzenia stanu programu. Ta funkcja jest nazywana *debugowaniem w czasie projektowania*.

Poniższy przykład znajduje się w Visual Basic. Możesz również użyć okna **bezpośredniego** w czasie projektowania w aplikacjach C#, F # i C++/CLI.

1. Wklej następujący kod do pustej aplikacji konsolowej Visual Basic:

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

1. Ustaw punkt przerwania w **funkcji końca**wiersza.

1. Otwórz okno **bezpośrednie** , wybierając pozycję **Debuguj**  >  **Windows**  >  **natychmiast**Windows. Wpisz `?MyFunction` w oknie, a następnie naciśnij klawisz **Enter**.

   Punkt przerwania został trafiony, a wartość **funkcji** w oknie **zmiennych lokalnych** to **1**. Możesz przeanalizować stos wywołań i inne okna debugowania, gdy aplikacja jest w trybie przerwania.

1. Wybierz pozycję **Kontynuuj** na pasku narzędzi programu Visual Studio. Aplikacja zostanie zakończona, a w oknie **bezpośrednim** zostanie zwrócona wartość **1** . Upewnij się, że nadal Pracujesz w trybie projektowania.

1. Wpisz `?MyFunction` ponownie okno **bezpośrednie** , a następnie naciśnij klawisz **Enter**. Punkt przerwania został trafiony, a wartość **funkcji** w oknie **zmiennych lokalnych** wynosi **2**.

1. Bez wybierania opcji **Kontynuuj**, wpisz `?MySub()` w oknie **bezpośrednim** , a następnie naciśnij klawisz **Enter**. Punkt przerwania został trafiony, a wartość **funkcji** w oknie **zmiennych lokalnych** to **3**. Stan aplikacji można przeanalizować, gdy aplikacja jest w trybie przerwania.

1. Wybierz pozycję **Continue** (Kontynuuj). Punkt przerwania zostanie ponownie trafiony, a wartość **funkcji** w oknie **zmiennych lokalnych** wynosi teraz **2**. **Bezpośrednie** okno zwraca **wyrażenie zostało ocenione i nie ma wartości**.

1. Wybierz pozycję **Kontynuuj** ponownie. Aplikacja zostanie zakończona, a w oknie **bezpośrednim** zostanie zwrócona wartość **2** . Upewnij się, że nadal Pracujesz w trybie projektowania.

1. Aby wyczyścić zawartość okna **bezpośredniego** , kliknij prawym przyciskiem myszy w oknie i wybierz polecenie **Wyczyść wszystko**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Debuguj niestandardową kontrolkę XAML w czasie projektowania przez dołączenie do projektanta XAML

1. Otwórz rozwiązanie lub projekt w programie Visual Studio.

1. Kompiluj rozwiązanie/projekt.

1. Otwórz stronę XAML zawierającą kontrolkę niestandardową, którą chcesz debugować.

   W przypadku projektów platformy UWP przeznaczonych dla kompilacji systemu Windows 16299 lub nowszego ten krok uruchomi proces *UwpSurface.exe* . W przypadku projektów WPF przeznaczonych dla systemu Windows Build 16299 lub nowszego ten krok uruchomi proces *WpfSurface.exe* . W przypadku wersji WPF lub platformy UWP starszych niż kompilacja systemu Windows 16299 ten krok uruchomi proces *XDesProc.exe* . 

1. Otwórz drugie wystąpienie programu Visual Studio. Nie otwieraj rozwiązania lub projektu w drugim wystąpieniu.

1. W drugim wystąpieniu programu Visual Studio Otwórz menu **Debuguj** i wybierz polecenie **Dołącz do procesu...**.

1. W zależności od typu projektu (zobacz poprzednie kroki) wybierz z listy dostępnych procesów *UwpSurface.exe*, *WpfSurface.exe*lub proces *XDesProc.exe* .

1. W polu **Dołącz do** w oknie dialogowym **Dołącz do procesu** wybierz odpowiedni typ kodu dla kontrolki niestandardowej, która ma być debugowana.

   Jeśli kontrolka niestandardowa została zapisywana w języku .NET, wybierz odpowiedni typ kodu platformy .NET, taki jak **Managed (CoreCLR)**. Jeśli kontrolka niestandardowa została zapisywana w języku C++, wybierz opcję **natywny**.

1. Dołącz drugie wystąpienie programu Visual Studio, klikając przycisk **Dołącz** .

1. W drugim wystąpieniu programu Visual Studio Otwórz pliki kodu skojarzone z kontrolką niestandardową, którą chcesz debugować. Pamiętaj, aby po prostu otworzyć pliki, a nie całe rozwiązanie lub projekt.

1. Umieść niezbędne punkty przerwania w poprzednio otwartych plikach.

1. W pierwszym wystąpieniu programu Visual Studio Zamknij stronę XAML zawierającą kontrolkę niestandardową, którą chcesz debugować (ta sama strona została otwarta w poprzednich krokach).

1. W pierwszym wystąpieniu programu Visual Studio Otwórz stronę XAML zamkniętą w poprzednim kroku. Spowoduje to zatrzymanie debugera z pierwszego punktu przerwania ustawionego w drugim wystąpieniu programu Visual Studio.

1. Debuguj kod w drugim wystąpieniu programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
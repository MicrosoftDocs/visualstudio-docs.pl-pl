---
title: Napisz wizualizator w Visual Basic | Microsoft Docs
ms.custom: seodec18
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25720f31c721cae44ed5425631a86b3a41bf475e
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180548"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Wskazówki: pisanie wizualizatora w Visual Basic

W tym instruktażu przedstawiono sposób pisania prostego wizualizatora przy użyciu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Wizualizator, który utworzysz w tym instruktażu, wyświetla zawartość ciągu przy użyciu okna komunikatu Windows Forms. Ten prosty wizualizator ciągów to podstawowy przykład pokazujący, jak tworzyć Wizualizatory dla innych typów danych, które są bardziej odpowiednie dla projektów.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, przejdź do menu **Narzędzia** i wybierz polecenie **Importuj i Eksportuj** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Kod wizualizatora musi być umieszczony w pliku DLL, który będzie odczytywany przez debuger. Pierwszym krokiem jest utworzenie projektu biblioteki klas dla biblioteki DLL.

## <a name="create-and-prepare-a-class-library-project"></a>Utwórz i przygotuj projekt biblioteki klas

### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas

1. Utwórz nowy projekt biblioteki klas.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, **wpisz Visual Basic**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Utwórz nową bibliotekę klas (.NET Framework)**. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual Basic**wybierz pozycję **.NET Standard**, a następnie w środkowym okienku wybierz pozycję **Biblioteka klas (.NET standard)**.
    ::: moniker-end

2. Wpisz odpowiednią nazwę biblioteki klas, np `MyFirstVisualizer` ., a następnie kliknij przycisk **Utwórz** lub **OK**.

   Po utworzeniu biblioteki klas należy dodać odwołanie do pliku Microsoft. VisualStudio. DebuggerVisualizers. DLL, aby można było użyć zdefiniowanych tam klas. Najpierw jednak Nadaj projektowi zrozumiałą nazwę.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę Class1. vb i dodać Microsoft. VisualStudio. DebuggerVisualizers

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **Class1. vb**, a następnie w menu skrótów kliknij polecenie **Zmień nazwę**.

2. Zmień nazwę z Class1. vb na coś znaczącego, na przykład DebuggerSide. vb.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automatycznie zmienia deklarację klasy w DebuggerSide. vb w celu dopasowania jej do nazwy nowego pliku.

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **mój pierwszy wizualizator**, a następnie w menu skrótów kliknij pozycję **Dodaj odwołanie**.

4. W oknie dialogowym **Dodaj odwołanie** na karcie **Przeglądaj** wybierz pozycję **Przeglądaj** i Znajdź plik Microsoft. VisualStudio. DebuggerVisualizers. dll.

    Bibliotekę DLL można znaleźć w podkatalogu * \<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* w katalogu instalacyjnym programu Visual Studio.

5. Kliknij przycisk **OK**.

6. W DebuggerSide. vb Dodaj następującą instrukcję do `Imports` instrukcji:

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Dodawanie kodu po stronie debugera
 Teraz możesz przystąpić do tworzenia kodu po stronie debugera. Jest to kod, który działa w debugerze, aby wyświetlić informacje, które chcesz wizualizować. Najpierw należy zmienić deklarację `DebuggerSide` obiektu, aby dziedziczyć z klasy bazowej `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Aby dziedziczyć z DialogDebuggerVisualizer

1. W DebuggerSide. vb przejdź do następującego wiersza kodu:

   ```vb
   Public Class DebuggerSide
   ```

2. Edytuj kod w taki sposób, aby wyglądał następująco:

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer`ma jedną metodę abstrakcyjną, `Show` która musi zostać przesłonięta.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby zastąpić metodę DialogDebuggerVisualizer. show

- W programie `public class DebuggerSide` Dodaj następującą metodę:

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  `Show`Metoda zawiera kod, który tworzy wizualizatorer okno dialogowe lub inny interfejs użytkownika i wyświetla informacje, które zostały przesłane do wizualizatora z debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym instruktażu należy to zrobić przy użyciu okna komunikatu Windows Forms. Najpierw należy dodać odwołanie i `Imports` instrukcję dla <xref:System.Windows.Forms> .

### <a name="to-add-systemwindowsforms"></a>Aby dodać system. Windows. Forms

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie w menu skrótów kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodaj odwołanie** na karcie **Przeglądaj** wybierz pozycję **Przeglądaj**, a następnie znajdź polecenie System. Windows. Forms. dll.

    Bibliotekę DLL można znaleźć w *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3. Kliknij przycisk **OK**.

4. W DebuggerSide.cs Dodaj następującą instrukcję do `Imports` instrukcji:

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Tworzenie interfejsu użytkownika wizualizatora
 Teraz dodasz kod do tworzenia i wyświetlania interfejsu użytkownika wizualizatora. Ponieważ jest to Twój pierwszy wizualizator, będziesz utrzymywać prosty interfejs użytkownika i korzystać z okna komunikatu.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym

1. W metodzie `Show` dodaj następujący wiersz kodu:

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     Ten przykładowy kod nie zawiera obsługi błędów. Należy uwzględnić obsługę błędów w rzeczywistym wizualizatorze lub dowolnym innym rodzaju aplikacji.

2. W menu **kompilacja** kliknij pozycję **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

## <a name="add-the-necessary-attribute"></a>Dodaj wymagany atrybut
 To jest koniec kodu po stronie debugera. Istnieje jeszcze jeden krok, jednak: atrybut, który instruuje debugowanego obiektu, która kolekcja klas składa się wizualizatora.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Aby dodać typ do wizualizacji kodu po stronie debugowanego obiektu

W kodzie po stronie debugera należy określić typ do wizualizacji (źródło obiektu) dla debugowanego obiektu przy użyciu <xref:System.Diagnostics.DebuggerVisualizerAttribute> atrybutu. `Target`Właściwość ustawia typ do wizualizacji.

1. Dodaj następujący kod atrybutu do DebuggerSide. vb po `Imports` instrukcjach, ale przed `namespace MyFirstVisualizer` :

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. W menu **kompilacja** kliknij pozycję **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

## <a name="create-a-test-harness"></a>Tworzenie zespołu testowego
 W tym momencie pierwszy wizualizator zostanie zakończony. Jeśli wykonano kroki prawidłowo, można skompilować wizualizator i zainstalować go w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Przed zainstalowaniem wizualizatora w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] należy go przetestować, aby upewnić się, że działa poprawnie. Teraz utworzysz zespół testów do uruchamiania wizualizatora bez instalowania go w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową w celu wyświetlenia wizualizatora

1. Dodaj następującą metodę do klasy `public DebuggerSide` :

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. W menu **kompilacja** kliknij pozycję **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

   Następnie należy utworzyć projekt wykonywalny do wywoływania biblioteki DLL wizualizatora. Dla uproszczenia Użyj projektu aplikacji konsolowej.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsolowej do rozwiązania

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.

    ::: moniker range=">=vs-2019"
    W polu wyszukiwania wpisz **Visual Basic**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Utwórz nową aplikację konsolową (.NET Framework)**. W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** w obszarze **Visual Basic**wybierz pozycję **Windows Desktop**, a następnie w środkowym okienku wybierz pozycję **aplikacja konsoli (.NET Framework)**.
    ::: moniker-end

2. Wpisz odpowiednią nazwę biblioteki klas, np `MyTestConsole` ., a następnie kliknij przycisk **Utwórz** lub **OK**.

   Teraz musisz dodać niezbędne odwołania, aby MyTestConsole mógł wywołać MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do MyTestConsole

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MyTestConsole**, a następnie w menu skrótów kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodaj odwołanie** na karcie **Przeglądaj** kliknij pozycję Microsoft. VisualStudio. DebuggerVisualizers.

3. Kliknij przycisk **OK**.

4. Kliknij prawym przyciskiem myszy pozycję **MyTestConsole**, a następnie ponownie kliknij pozycję **Dodaj odwołanie** .

5. W oknie dialogowym **Dodaj odwołanie** kliknij kartę **projekty** , a następnie wybierz pozycję MyFirstVisualizer.

6. Kliknij przycisk **OK**.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Zakończ pracę zespołu testowego i przetestuj wizualizator
 Teraz dodasz kod do zakończenia zespołu testowego.

### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do MyTestConsole

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **program Visual. vb**, a następnie w menu skrótów kliknij polecenie **Zmień nazwę**.

2. Edytuj nazwę z Module1. vb do odpowiedniego elementu, takiego jak **TestConsole. vb**.

    Należy zauważyć, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Automatyczna zmiana deklaracji klasy w TestConsole. vb w celu dopasowania do nazwy nowego pliku.

3. W TestConsole. VB, Dodaj następującą `Imports` instrukcję:

   ```vb
   Imports MyFirstVisualizer
   ```

4. W metodzie `Main` Dodaj następujący kod:

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Teraz można przystąpić do testowania pierwszego wizualizatora.

### <a name="to-test-the-visualizer"></a>Aby przetestować wizualizator

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MyTestConsole**, a następnie w menu skrótów kliknij pozycję **Ustaw jako projekt startowy**.

2. W menu **debugowanie** kliknij przycisk **Uruchom**.

    Zostanie uruchomiona aplikacja konsolowa. Wizualizator zostanie wyświetlony i zostanie wyświetlony ciąg "Hello, World".

   Gratulacje. Właśnie został skompilowany i przetestowany pierwszy wizualizator.

   Jeśli chcesz użyć wizualizatora [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zamiast tylko wywołać go z zespołu testowego, musisz go zainstalować. Aby uzyskać więcej informacji, zobacz [How to: Install the wizualizator](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>Zobacz także

- [Architektura wizualizatora](../debugger/visualizer-architecture.md)
- [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
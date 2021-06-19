---
title: Pisanie wizualizatora w Visual Basic | Microsoft Docs
description: Skorzystaj z przewodnika, aby utworzyć prosty wizualizator w Visual Basic. Utworzysz również uprząż testową do testowania wizualizatora.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b1a4fc7d6f33d1bdfd469ec352674b08dd2495e6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385009"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Wskazówki: pisanie wizualizatora w Visual Basic

W tym przewodniku pokazano, jak napisać prosty wizualizator przy użyciu narzędzia [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Wizualizator, który utworzysz w tym przewodniku, wyświetla zawartość ciągu przy użyciu Windows Forms komunikatu. Ten prosty wizualizator ciągów to podstawowy przykład, który pokazuje, jak można tworzyć wizualizatory dla innych typów danych bardziej odpowiednich dla projektów.

> [!NOTE]
> Wyświetlane okna dialogowe i polecenia menu mogą różnić się od tych opisanych w Pomocy, w zależności od aktywnych ustawień lub wersji. Aby zmienić ustawienia, przejdź do menu **Narzędzia** i wybierz pozycję **Importuj i Eksportuj.** Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Kod wizualizatora musi być umieszczony w bibliotece DLL, która będzie odczytywana przez debuger. Pierwszym krokiem jest utworzenie projektu biblioteki klas dla biblioteki DLL.

## <a name="create-and-prepare-a-class-library-project"></a>Tworzenie i przygotowywanie projektu biblioteki klas

### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas

1. Utwórz nowy projekt biblioteki klas.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno uruchamiania. Naciśnij **klawisze Ctrl +Q,** aby otworzyć pole wyszukiwania, wpisz **visual basic,** wybierz pozycję **Szablony,** a następnie wybierz pozycję Utwórz **nową bibliotekę klas (.NET Framework).** W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku  okna dialogowego Nowy projekt w obszarze **Visual Basic** wybierz pozycję **.NET Standard**, a następnie w środkowym okienku wybierz pozycję Biblioteka klas **(.NET Standard).**
    ::: moniker-end

2. Wpisz odpowiednią nazwę biblioteki klas, taką jak `MyFirstVisualizer` , a następnie kliknij przycisk Utwórz **lub** **OK.**

   Po utworzeniu biblioteki klas należy dodać odwołanie do biblioteki Microsoft.VisualStudio.DebuggerVisualizers.DLL, aby można było używać zdefiniowanych w tym miejscu klas. Najpierw jednak nadaj projektowi znaczącą nazwę.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę pliku Class1.vb i dodać elementy Microsoft.VisualStudio.DebuggerVisualizers

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję Class1.vb,** a następnie w menu skrótów kliknij polecenie Zmień **nazwę**.

2. Zmień nazwę z Class1.vb na coś znaczącego, na przykład DebuggerSide.vb.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmienia deklarację klasy w debuggerSide.vb, aby dopasować nową nazwę pliku.

3. W **Eksplorator rozwiązań** prawym przyciskiem myszy pozycję My First Visualizer (Mój **pierwszy wizualizator),** a następnie w menu skrótów kliknij polecenie **Add Reference (Dodaj odwołanie).**

4. W **oknie dialogowym** Dodawanie odwołania na karcie **Przeglądaj** wybierz pozycję **Przeglądaj** i znajdź Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Bibliotekę DLL można znaleźć w podkatalogu *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* Visual Studio katalogu instalacyjnego programu .

5. Kliknij przycisk **OK**.

6. W debuggerSide.vb dodaj następującą instrukcje do `Imports` instrukcji :

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Dodawanie kodu po stronie debugera
 Teraz możesz utworzyć kod po stronie debugera. Jest to kod uruchamiany w debugerze w celu wyświetlenia informacji, które chcesz zwizualizować. Najpierw należy zmienić deklarację obiektu tak, aby `DebuggerSide` dziedziczył z klasy bazowej `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dziedziczenie z właściwości DialogDebuggerVisualizer

1. W debuggerSide.vb przejdź do następującego wiersza kodu:

   ```vb
   Public Class DebuggerSide
   ```

2. Zedytowuj kod w taki sposób, aby wyglądał następująco:

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` ma jedną metodę `Show` abstrakcyjną, , która musi zostać przesłoniła.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby zastąpić metodę DialogDebuggerVisualizer.Show

- W `public class DebuggerSide` metodzie dodaj następującą metodę:

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  Metoda zawiera kod, który faktycznie tworzy okno dialogowe wizualizatora lub inny interfejs użytkownika, i wyświetla informacje przekazane do wizualizatora z `Show` debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym przewodniku zrobisz to przy użyciu Windows Forms komunikatu. Najpierw należy dodać odwołanie i `Imports` instrukcje dla <xref:System.Windows.Forms> .

### <a name="to-add-systemwindowsforms"></a>Aby dodać system.Windows.Forms

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Odwołania**, a następnie w menu skrótów kliknij polecenie **Dodaj odwołanie**.

2. W **oknie dialogowym** Dodawanie odwołania na karcie **Przeglądaj** wybierz pozycję **Przeglądaj** i znajdź System.Windows.Forms.DLL.

    Bibliotekę DLL można znaleźć w folderze *C:\Windows\Microsoft.NET\Framework\v4.0.30319.*

3. Kliknij przycisk **OK**.

4. W instrukcje DebuggerSide.cs dodaj następującą `Imports` instrukcje:

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Tworzenie aplikacji wizualizator Interfejs użytkownika a
 Teraz dodasz kod, aby utworzyć i wyświetlić interfejs użytkownika wizualizatora. Ponieważ jest to Twój pierwszy wizualizator, interfejs użytkownika będzie prosty i będzie używać okna komunikatów.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym

1. W metodzie `Show` dodaj następujący wiersz kodu:

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     Ten przykładowy kod nie obejmuje obsługi błędów. Należy uwzględnić obsługę błędów w rzeczywistym wizualizatorze lub dowolnym innym rodzaju aplikacji.

2. W menu **Kompilacja** kliknij pozycję **Build MyFirstVisualizer (Kompilacja myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Przed kontynuowaniem popraw wszystkie błędy kompilacji.

## <a name="add-the-necessary-attribute"></a>Dodawanie niezbędnego atrybutu
 Jest to koniec kodu po stronie debugera. Istnieje jednak jeszcze jeden krok: atrybut, który informuje stronę debugera, która kolekcja klas składa się z wizualizatora.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Aby dodać typ wizualizacji dla kodu po stronie debugera

W kodzie po stronie debugera należy określić typ wizualizacji (źródło obiektu) dla debugera przy użyciu <xref:System.Diagnostics.DebuggerVisualizerAttribute> atrybutu . Właściwość `Target` ustawia typ do wizualizacji.

1. Dodaj następujący kod atrybutu do debuggerSide.vb po instrukcjach , `Imports` ale przed `namespace MyFirstVisualizer` :

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2. W menu **Kompilacja** kliknij pozycję **Build MyFirstVisualizer (Kompilacja myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Przed kontynuowaniem popraw wszystkie błędy kompilacji.

## <a name="create-a-test-harness"></a>Tworzenie uprzęży testów
 Na tym etapie pierwszy wizualizator jest gotowy. Jeśli kroki zostały wykonane prawidłowo, możesz skompilować wizualizator i zainstalować go w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jednak przed zainstalowaniem wizualizatora w programie należy go przetestować, aby upewnić się, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] że działa prawidłowo. Teraz utworzysz uprząż testową, aby uruchomić wizualizator bez instalowania go w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową w celu pokazania wizualizatora

1. Dodaj następującą metodę do klasy `public DebuggerSide` :

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. W menu **Kompilacja** kliknij pozycję **Build MyFirstVisualizer (Kompilacja myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Przed kontynuowaniem popraw wszystkie błędy kompilacji.

   Następnie należy utworzyć projekt wykonywalny w celu wywołania biblioteki DLL wizualizatora. Dla uproszczenia użyj projektu aplikacji konsolowej.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsolowej do rozwiązania

1. W Eksplorator rozwiązań kliknij rozwiązanie prawym przyciskiem myszy, wybierz polecenie **Dodaj,** a następnie kliknij **pozycję Nowy projekt.**

    ::: moniker range=">=vs-2019"
    W polu Wyszukaj wpisz **visual basic,** wybierz **pozycję Szablony,** a następnie wybierz pozycję **Utwórz nową aplikację konsoli (.NET Framework).** W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku  okna dialogowego Nowy projekt w obszarze Visual Basic wybierz pozycję **Windows Desktop,** **a** następnie w środkowym okienku wybierz pozycję Aplikacja konsoli **(.NET Framework).**
    ::: moniker-end

2. Wpisz odpowiednią nazwę biblioteki klas, taką jak `MyTestConsole` , a następnie kliknij przycisk Utwórz **lub** **OK.**

   Teraz musisz dodać niezbędne odwołania, aby mojakonsole Testowa może wywołać myFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do myTestConsole

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **MyTestConsole,** a następnie w menu skrótów kliknij polecenie **Dodaj odwołanie**.

2. W **oknie dialogowym** Dodawanie odwołania na karcie **Przeglądaj** kliknij pozycję Microsoft.VisualStudio.DebuggerVisualizers.

3. Kliknij przycisk **OK**.

4. Kliknij prawym przyciskiem myszy **pozycję MyTestConsole**, a następnie ponownie kliknij **pozycję Dodaj** odwołanie.

5. W **oknie dialogowym** Dodawanie odwołania kliknij **kartę Projekty,** a następnie wybierz pozycję MyFirstVisualizer.

6. Kliknij przycisk **OK**.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Kończ testowy uprząż i przetestuj wizualizator
 Teraz dodasz kod, aby zakończyć testowy uprząż.

### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do aplikacji MyTestConsole

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **plik Program.vb,** a następnie w menu skrótów kliknij polecenie **Zmień nazwę**.

2. Zmień nazwę pliku Module1.vb na odpowiednią, na przykład **TestConsole.vb.**

    Zwróć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uwagę, że deklaracja klasy w pliku TestConsole.vb jest automatycznie zmieniana tak, aby dopasować ją do nowej nazwy pliku.

3. W testconsole. vb, dodaj następującą `Imports` instrukcje:

   ```vb
   Imports MyFirstVisualizer
   ```

4. W metodzie `Main` dodaj następujący kod:

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Teraz możesz przetestować pierwszy wizualizator.

### <a name="to-test-the-visualizer"></a>Aby przetestować wizualizator

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **MyTestConsole,** a następnie w menu skrótów kliknij pozycję **Ustaw jako projekt startowy.**

2. W menu **Debug (Debugowanie)** kliknij pozycję Start **(Uruchom).**

    Zostanie uruchomina aplikacja konsolowa. Zostanie wyświetlony wizualizator z wyświetlonym ciągiem "Hello, World".

   Gratulacje. Twój pierwszy wizualizator został właśnie sbudowaną i przetestowaną.

   Jeśli chcesz użyć wizualizatora w programie , a nie tylko wywołania go z uprzęży [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] testowej, musisz go zainstalować. Aby uzyskać więcej informacji, [zobacz Jak zainstalować wizualizator](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>Zobacz też

- [Architektura wizualizatora](../debugger/visualizer-architecture.md)
- [How to: Install a Visualizer](../debugger/how-to-install-a-visualizer.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
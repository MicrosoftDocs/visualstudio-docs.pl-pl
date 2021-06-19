---
title: Pisanie wizualizatora w języku C# | Microsoft Docs
description: Skorzystaj z przewodnika, aby utworzyć prosty wizualizator w języku C#. Przedstawiono w nim kroki wymagane zarówno z szablonem elementu Visualizer, jak i bez niego.
ms.custom: SEO-VS-2020
ms.date: 05/27/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 86123ece79f7bbde4f4f91fac657dcc235056c0b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384998"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Przewodnik: pisanie wizualizatora w języku C\#

W tym przewodniku pokazano, jak napisać prosty wizualizator przy użyciu języka C#. Wizualizator, który utworzysz w tym przewodniku, wyświetla zawartość ciągu przy użyciu okna komunikatu formularzy systemu Windows. Ten prosty wizualizator ciągów sam w sobie nie jest szczególnie przydatny, ale pokazuje podstawowe kroki, które należy wykonać, aby utworzyć bardziej przydatne wizualizatory dla innych typów danych.

> [!NOTE]
> Wyświetlane okna dialogowe i polecenia menu mogą różnić się od tych opisanych w Pomocy, w zależności od aktywnych ustawień lub wersji. Aby zmienić ustawienia, przejdź do menu **Narzędzia** i wybierz pozycję **Importuj i eksportuj ustawienia.** Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Kod wizualizatora musi być umieszczony w bibliotece DLL, która będzie odczytywana przez debuger. W związku z tym pierwszym krokiem jest utworzenie projektu biblioteki klas dla biblioteki DLL.

## <a name="create-a-visualizer-manually"></a>Ręczne tworzenie wizualizatora

Wykonaj poniższe zadania, aby utworzyć wizualizator.

### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas

1. Utwórz nowy projekt biblioteki klas.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno uruchamiania. Naciśnij **klawisze Ctrl +Q,** aby otworzyć pole wyszukiwania, wpisz bibliotekę **klas,** wybierz pozycję **Szablony,** a następnie wybierz pozycję Utwórz **nową bibliotekę klas (.NET Framework).** W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku  okna dialogowego Nowy projekt w obszarze **Visual C#** wybierz pozycję .NET Framework , **a** następnie w środkowym okienku wybierz pozycję Biblioteka klas **(.NET Framework).**
    ::: moniker-end

2. Wpisz odpowiednią nazwę biblioteki klas, taką jak `MyFirstVisualizer` , a następnie kliknij przycisk Utwórz **lub** **OK.**

   Po utworzeniu biblioteki klas należy dodać odwołanie do biblioteki Microsoft.VisualStudio.DebuggerVisualizers.DLL, aby można było używać zdefiniowanych w tej bibliotece klas. Przed dodaniu odwołania należy jednak zmienić nazwy niektórych klas tak, aby ich nazwy były znaczące.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę pliku Class1.cs i dodać bibliotekę Microsoft.VisualStudio.DebuggerVisualizers

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik Class1.cs i wybierz polecenie **Zmień nazwę** w menu skrótów.

2. Zmień nazwę z Class1.cs na coś znaczącego, na przykład DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmienia deklarację klasy w pliku DebuggerSide.cs w celu dopasowania jej do nowej nazwy pliku.

3. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Odwołania** i wybierz polecenie **Dodaj** odwołanie w menu skrótów.

4. W **oknie dialogowym** Dodawanie odwołania na karcie **Przeglądaj** wybierz pozycję **Przeglądaj** i znajdź Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Bibliotekę DLL można znaleźć w podkatalogu *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* Visual Studio katalogu instalacyjnego programu .

5. Kliknij przycisk **OK**.

6. W debuggerSide.cs dodaj następujące elementy do `using` dyrektyw :

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Teraz możesz utworzyć kod po stronie debugera. Jest to kod uruchamiany w debugerze w celu wyświetlenia informacji, które chcesz zwizualizować. Najpierw należy zmienić deklarację obiektu tak, aby dziedziczyła `DebuggerSide` z klasy bazowej `DialogDebuggerVisualizer` .

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dziedziczenie z właściwości DialogDebuggerVisualizer

1. W debuggerSide.cs przejdź do następującego wiersza kodu:

   ```csharp
   public class DebuggerSide
   ```

2. Zmień kod na:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` ma jedną metodę abstrakcyjną ( `Show` ), która musi zostać przesłoniła.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby zastąpić metodę DialogDebuggerVisualizer.Show

- W `public class DebuggerSide` metodzie dodaj następującą **metodę:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  Metoda zawiera kod, który faktycznie tworzy okno dialogowe wizualizatora lub inny interfejs użytkownika i wyświetla informacje przekazane do wizualizatora `Show` z debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym przewodniku zrobisz to przy użyciu okna komunikatu formularzy systemu Windows. Najpierw należy dodać odwołanie i dyrektywę `using` dla system.Windows.Forms.

### <a name="to-add-systemwindowsforms"></a>Aby dodać system.Windows.Forms

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Odwołania** i wybierz polecenie **Dodaj** odwołanie w menu skrótów.

2. W **oknie dialogowym** Dodawanie odwołania na karcie **Przeglądaj** wybierz pozycję **Przeglądaj** i znajdź System.Windows.Forms.DLL.

    Bibliotekę DLL można znaleźć w folderze *C:\Windows\Microsoft.NET\Framework\v4.0.30319.*

3. Kliknij przycisk **OK**.

4. W debuggerSide.cs dodaj następujące elementy do `using` dyrektyw :

   ```csharp
   using System.Windows.Forms;
   ```

   Teraz dodasz kod, aby utworzyć i wyświetlić interfejs użytkownika wizualizatora. Ponieważ jest to Twój pierwszy wizualizator, interfejs użytkownika będzie prosty i użyjemy okna komunikatów.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym

1. W metodzie `Show` dodaj następujący wiersz kodu:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Ten przykładowy kod nie obejmuje obsługi błędów. Obsługa błędów powinna być uwzględniana w rzeczywistym wizualizatorze lub dowolnym innym rodzaju aplikacji.

2. W menu **Kompilacja** wybierz pozycję **Build MyFirstVisualizer (Kompilowanie myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Przed kontynuowaniem popraw wszystkie błędy kompilacji.

   Jest to koniec kodu po stronie debugera. Istnieje jednak jeszcze jeden krok: atrybut, który informuje stronę debugera, która kolekcja klas składa się z wizualizatora.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Aby dodać typ wizualizacji dla kodu po stronie debugera

W kodzie po stronie debugera należy określić typ wizualizacji (źródło obiektu) dla debugera przy użyciu <xref:System.Diagnostics.DebuggerVisualizerAttribute> atrybutu . Właściwość `Target` ustawia typ do wizualizacji.

1. Dodaj następujący kod atrybutu do pliku DebuggerSide.cs po dyrektywach , `using` ale przed `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. W menu **Kompilacja** wybierz pozycję **Build MyFirstVisualizer (Kompilowanie myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Przed kontynuowaniem popraw wszystkie błędy kompilacji.

   Na tym etapie pierwszy wizualizator jest gotowy. Jeśli kroki zostały wykonane prawidłowo, możesz skompilować wizualizator i zainstalować go w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jednak przed zainstalowaniem wizualizatora w programie należy go przetestować, aby upewnić się, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] że działa prawidłowo. Teraz utworzysz uprząż testową, aby uruchomić wizualizator bez instalowania go w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową w celu pokazania wizualizatora

1. Dodaj następującą metodę do klasy `public DebuggerSide` :

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. W menu **Kompilacja** wybierz pozycję **Build MyFirstVisualizer (Kompilowanie myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Przed kontynuowaniem popraw wszystkie błędy kompilacji.

   Następnie należy utworzyć projekt wykonywalny w celu wywołania biblioteki DLL wizualizatora. Dla uproszczenia użyjemy projektu Aplikacja konsolowa.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsolowej do rozwiązania

1. W Eksplorator rozwiązań kliknij rozwiązanie prawym przyciskiem myszy, wybierz polecenie **Dodaj,** a następnie kliknij **pozycję Nowy projekt.**

    ::: moniker range=">=vs-2019"
    W polu Wyszukaj wpisz nazwę **aplikacji konsolowej,** wybierz pozycję **Szablony,** a następnie wybierz pozycję Utwórz nową aplikację konsoli **(.NET Framework).** W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku  okna dialogowego Nowy projekt w obszarze **Visual C#** wybierz pozycję **Windows Desktop,** a następnie w środkowym okienku wybierz pozycję Aplikacja konsoli **(.NET Framework).**
    ::: moniker-end

2. Wpisz odpowiednią nazwę biblioteki klas, taką jak `MyTestConsole` , a następnie kliknij przycisk Utwórz **lub** **OK.**

   Teraz musisz dodać niezbędne odwołania, aby mojakonsole Testowa może wywołać myFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do myTestConsole

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **MyTestConsole** i wybierz polecenie **Dodaj** odwołanie w menu skrótów.

2. W **oknie dialogowym** Dodawanie odwołania na **karcie Przeglądaj** wybierz pozycję Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Kliknij przycisk **OK**.

4. Kliknij prawym przyciskiem myszy **pozycję MyTestConsole** i ponownie wybierz **pozycję Dodaj odwołanie.**

5. W **oknie dialogowym** Dodawanie odwołania kliknij **kartę Projekty,** a następnie kliknij pozycję MyFirstVisualizer.

6. Kliknij przycisk **OK**.

   Teraz dodasz kod, aby zakończyć testowy uprząż.

### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do myTestConsole

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik Program.cs i wybierz polecenie **Zmień nazwę** w menu skrótów.

2. Zmień nazwę pliku Program.cs na bardziej zrozumiałą, na przykład TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmienia deklarację klasy w pliku TestConsole.cs, aby dopasować ją do nowej nazwy pliku.

3. W edycie TestConsole.cs dodaj następujący kod do `using` dyrektyw :

   ```csharp
   using MyFirstVisualizer;
   ```

4. W metodzie `Main` dodaj następujący kod:

   ```csharp
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Teraz możesz przetestować pierwszy wizualizator.

### <a name="to-test-the-visualizer"></a>Aby przetestować wizualizator

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **MyTestConsole** i wybierz polecenie **Ustaw jako** projekt startowy w menu skrótów.

2. W menu **Debugowanie** wybierz pozycję **Uruchom.**

    Aplikacja konsolowa zostanie uruchamiana, a zostanie wyświetlony wizualizator z wyświetlonym ciągiem "Hello, World".

   Gratulacje. Twój pierwszy wizualizator został właśnie sbudowaną i przetestowaną.

   Jeśli chcesz użyć wizualizatora w programie , a nie tylko wywołania go z uprzęży [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] testowej, musisz go zainstalować. Aby uzyskać więcej informacji, [zobacz Jak zainstalować wizualizator](../debugger/how-to-install-a-visualizer.md).

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Tworzenie wizualizatora przy użyciu szablonu elementu wizualizatora

Do tej pory w tym przewodniku pokazano, jak ręcznie utworzyć wizualizator. Zostało to zrobione jako ćwiczenie szkoleniowe. Teraz, gdy wiesz już, jak działa prosty wizualizator, istnieje łatwiejszy sposób jego utworzenia: użycie szablonu elementu wizualizatora.

Najpierw należy utworzyć nowy projekt biblioteki klas.

### <a name="to-create-a-new-class-library"></a>Aby utworzyć nową bibliotekę klas

1. W menu **File (Plik)** wybierz **pozycję New > Project (Nowy projekt).**

2. W **oknie dialogowym Nowy** projekt w obszarze **Visual C#** **wybierz pozycję .NET Framework**.

3. W środkowym okienku wybierz pozycję **Biblioteka klas**.

4. W polu **Nazwa** wpisz odpowiednią nazwę dla biblioteki klas, taką jak MySecondVisualizer.

5. Kliknij przycisk **OK**.

   Teraz możesz dodać do niego element wizualizatora:

### <a name="to-add-a-visualizer-item"></a>Aby dodać element wizualizatora

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję MySecondVisualizer.

2. W menu skrótów wybierz pozycję **Dodaj,** a następnie kliknij **pozycję Nowy element**.

3. W **oknie dialogowym Dodawanie nowego** elementu w obszarze **Elementy Visual C#** wybierz **pozycję Debuger Visualizer**.

4. W polu **Nazwa** wpisz odpowiednią nazwę, na przykład SecondVisualizer.cs.

5. Kliknij pozycję **Dodaj**.

   To wszystko. Spójrz na plik SecondVisualizer.cs i wyświetl kod dodany przez szablon. Poeksperymentuj z kodem. Teraz, gdy znasz już podstawy, możesz tworzyć bardziej złożone i przydatne wizualizatory samodzielnie.
::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Architektura wizualizatora](../debugger/visualizer-architecture.md)
- [How to: Install a Visualizer](../debugger/how-to-install-a-visualizer.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)

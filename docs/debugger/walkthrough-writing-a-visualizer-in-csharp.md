---
title: Pisanie wizualizatora w języku C# | Microsoft Docs
description: Postępuj zgodnie ze wskazówkim, aby utworzyć prosty wizualizator w języku C#. Przedstawiono w nim kroki wymagane zarówno z szablonem elementu Visualizer, jak i bez niego.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
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
ms.openlocfilehash: 47c7fa8eaa5a735f05b338101a1aefe0601e9915
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298294"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Przewodnik: pisanie wizualizatora w języku C\#

W tym przewodniku pokazano, jak napisać prosty wizualizator przy użyciu języka C#. Wizualizator, który utworzysz w tym przewodniku, wyświetla zawartość ciągu przy użyciu Windows formularza. Ten prosty wizualizator ciągów sam w sobie nie jest szczególnie przydatny, ale pokazuje podstawowe kroki, które należy wykonać, aby utworzyć bardziej przydatne wizualizatory dla innych typów danych.

> [!NOTE]
> Wyświetlane okna dialogowe i polecenia menu mogą różnić się od tych opisanych w Pomocy, w zależności od aktywnych ustawień lub wersji. Aby zmienić ustawienia, przejdź do menu **Narzędzia** i wybierz pozycję Importuj i **eksportuj Ustawienia.** Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Kod wizualizatora musi być umieszczony w bibliotece DLL, która będzie odczytywana przez debuger. W związku z tym pierwszym krokiem jest utworzenie projektu biblioteki klas dla biblioteki DLL.

## <a name="create-a-visualizer-manually"></a>Ręczne tworzenie wizualizatora

Wykonaj poniższe zadania, aby utworzyć wizualizator.

### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas

* Utwórz nowy projekt biblioteki klas.

    ::: moniker range=">=vs-2019"
    Wybierz **pozycję Plik**  >  **Nowy**  >  **Project**. Z listy rozwijanej języka wybierz pozycję **C#.** W polu wyszukiwania wpisz biblioteka **klas**, a następnie wybierz pozycję **Biblioteka klas (.NET Framework).** Kliknij przycisk **Dalej**. W wyświetlonym oknie dialogowym wpisz nazwę `MyFirstVisualizer` , a następnie kliknij przycisk **Utwórz**.

    W przypadku projektu wizualizatora upewnij się, że wybierasz .NET Framework klas, a nie platformę .NET. Mimo że wizualizator musi być .NET Framework, wywołującą aplikacją może być .NET Core.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Nowy** plik  >    >  **Project.** W lewym okienku  okna dialogowego Nowy projekt w obszarze **Visual C#** wybierz pozycję .NET Framework , **a następnie** w środkowym okienku wybierz pozycję Biblioteka klas **(.NET Framework).**

    Wpisz odpowiednią nazwę biblioteki klas, taką jak `MyFirstVisualizer` , a następnie kliknij przycisk Utwórz **lub** **OK.**
    ::: moniker-end

   Po utworzeniu biblioteki klas należy dodać odwołanie do Microsoft.VisualStudio.DebuggerVisualizers.DLL, aby można było używać zdefiniowanych tam klas. Jednak przed dodaniu odwołania należy zmienić nazwy niektórych klas tak, aby mieć znaczące nazwy.

### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę pliku Class1.cs i dodać microsoft.VisualStudio.DebuggerVisualizers

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik Class1.cs i wybierz polecenie **Zmień nazwę** w menu skrótów.

2. Zmień nazwę z Class1.cs na coś znaczącego, na przykład DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmienia deklarację klasy w pliku DebuggerSide.cs w celu dopasowania jej do nowej nazwy pliku.

3. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Odwołania** i wybierz polecenie **Dodaj** odwołanie w menu skrótów.

4. W **oknie dialogowym** Dodawanie odwołania na karcie **Przeglądaj** wybierz pozycję **Przeglądaj** i znajdź Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Bibliotekę DLL można znaleźć w podkatalogu *\<Visual Studio Install Directory> \Common7\IDE\PublicAssemblies* Visual Studio katalogu instalacyjnego programu .

5. Kliknij przycisk **OK**.

6. W debuggerSide.cs dodaj następujące do `using` dyrektyw:

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

   `DialogDebuggerVisualizer` Ma jedną metodę abstrakcyjną ( `Show` ), która musi zostać przesłonięcie.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby zastąpić metodę DialogDebuggerVisualizer.Show

- W `public class DebuggerSide` programie dodaj następującą **metodę:**

  ```csharp
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  Metoda zawiera kod, który faktycznie tworzy okno dialogowe wizualizatora lub inny interfejs użytkownika i wyświetla informacje przekazane do wizualizatora `Show` z debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym przewodniku zrobisz to przy użyciu pola komunikatu Windows Forms. Najpierw należy dodać odwołanie i dyrektywę `using` dla system.Windows. Formularzy.

### <a name="to-add-systemwindowsforms"></a>Aby dodać system. Windows. Formularzy

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Odwołania** i wybierz polecenie **Dodaj** odwołanie w menu skrótów.

2. W **oknie dialogowym** Dodawanie odwołania na karcie **Przeglądaj** wybierz pozycję **Przeglądaj** i znajdź System.Windows.Forms.DLL.

    Bibliotekę DLL można znaleźć w folderze *C:\Windows\Microsoft.NET\Framework\v4.0.30319.*

3. Kliknij przycisk **OK**.

4. W debuggerSide.cs dodaj następujące do `using` dyrektyw:

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

2. W menu **Kompilacja** wybierz pozycję **Build MyFirstVisualizer (Kompilowanie myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

   To jest koniec kodu po stronie debugera. Istnieje jednak jeszcze jeden krok: atrybut, który informuje stronę debugera, która kolekcja klas składa się z wizualizatora.

### <a name="to-add-the-type-to-visualize-for-the-debuggee-side-code"></a>Aby dodać typ wizualizacji dla kodu po stronie debugera

W kodzie po stronie debugera należy określić typ wizualizacji (źródło obiektu) debugera przy użyciu <xref:System.Diagnostics.DebuggerVisualizerAttribute> atrybutu . Właściwość `Target` ustawia typ do wizualizacji.

1. Dodaj następujący kod atrybutu do pliku DebuggerSide.cs po dyrektywach , `using` ale przed `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target = typeof(System.String),
   Description = "My First Visualizer")]
   ```

2. W menu **Kompilacja** wybierz pozycję **Build MyFirstVisualizer (Kompilowanie myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

   W tym momencie pierwszy wizualizator jest gotowy. Jeśli kroki zostały wykonane prawidłowo, możesz skompilować wizualizator i zainstalować go w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Jednak przed zainstalowaniem wizualizatora w programie należy go przetestować, aby upewnić się, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] że działa prawidłowo. Teraz utworzysz testowy uprząż, aby uruchomić wizualizator bez instalowania go w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową w celu pokazania wizualizatora

1. Dodaj następującą metodę do klasy `public DebuggerSide` :

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. W menu **Kompilacja** wybierz pozycję **Build MyFirstVisualizer (Kompilowanie myFirstVisualizer).** Projekt powinien zostać pomyślnie skompilowany. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

   Następnie należy utworzyć projekt wykonywalny w celu wywołania biblioteki DLL wizualizatora. Dla uproszczenia użyj projektu Aplikacja konsolowa.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsolowej do rozwiązania

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz pozycję **Dodaj,** a następnie kliknij pozycję **Nowy Project.**

    ::: moniker range=">=vs-2019"

    Wybierz **pozycję Plik**  >  **Nowy**  >  **Project**. Z listy rozwijanej języka wybierz pozycję **C#.** W polu wyszukiwania wpisz **nazwę aplikacja konsoli**, a następnie wybierz pozycję Aplikacja konsolowa **(.NET Framework)** lub **Aplikacja konsolowa** dla programu .NET. Kliknij przycisk **Dalej**. W wyświetlonym oknie dialogowym wpisz nazwę `MyTestConsole` , a następnie kliknij przycisk **Utwórz**.

    > [!NOTE]
    > Jeśli chcesz łatwo przetestować wizualizator przy użyciu uprzęży testowej, utwórz .NET Framework konsoli. Zamiast tego możesz utworzyć aplikację konsolową .NET, ale opisany w dalszej części testów nie jest jeszcze obsługiwany dla programu .NET, dlatego w celu przetestowania go należy zainstalować wizualizator. W tym scenariuszu najpierw utwórz aplikację konsolową w tym miejscu, a następnie wykonaj kroki opisane w części Dodawanie obiektu danych [po stronie debugera](#add-a-debuggee-side-data-object).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Nowy** plik  >    >  **Project.** W lewym okienku  okna dialogowego Nowy projekt w obszarze **Visual C#** wybierz pozycję **Windows Desktop, a** następnie w środkowym okienku wybierz pozycję Aplikacja konsolowa **(.NET Framework).**

    Wpisz odpowiednią nazwę biblioteki klas, taką jak `MyTestConsole` , a następnie kliknij przycisk **OK.**
    ::: moniker-end

   Teraz musisz dodać niezbędne odwołania, aby mojakonsole MyTestConsole może wywołać myFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do myTestConsole

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy **pozycję MyTestConsole** i wybierz polecenie **Dodaj odwołanie** w menu skrótów.

2. W **oknie dialogowym Dodawanie** odwołania na **karcie Przeglądaj** wybierz pozycję Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Kliknij przycisk **OK**.

4. Kliknij prawym przyciskiem myszy **pozycję MyTestConsole** i ponownie wybierz **polecenie Dodaj odwołanie.**

5. W **oknie dialogowym** Dodawanie odwołania kliknij **kartę Projekty,** a następnie kliknij pozycję MyFirstVisualizer.

6. Kliknij przycisk **OK**.

   Teraz dodasz kod, aby zakończyć testowy uprząż.

### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do myTestConsole

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik Program.cs i wybierz polecenie **Zmień nazwę** w menu skrótów.

2. Zmień nazwę pliku Program.cs na bardziej zrozumiałą, na przykład TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmienia deklarację klasy w pliku TestConsole.cs, aby dopasować ją do nowej nazwy pliku.

3. W kodzie TestConsole.cs dodaj następujący kod do `using` dyrektyw :

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

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **MyTestConsole** i wybierz polecenie Ustaw jako Project **uruchamiania** w menu skrótów.

2. W menu **Debugowanie** wybierz pozycję **Uruchom.**

    Aplikacja konsolowa zostanie uruchamiana, a zostanie wyświetlony wizualizator z wyświetlonym ciągiem "Hello, World".

   Gratulacje. Twój pierwszy wizualizator został właśnie sbudowaną i przetestowaną!

   Jeśli chcesz użyć wizualizatora w programie , a nie tylko wywołania go z uprzęży [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] testowej, musisz go zainstalować. Aby uzyskać więcej informacji, [zobacz Jak zainstalować wizualizator](../debugger/how-to-install-a-visualizer.md).

::: moniker range=">=vs-2019"
## <a name="add-a-debuggee-side-data-object"></a>Dodawanie obiektu danych po stronie debugera

W tej sekcji przełączysz się z obiektu `System.String` danych na niestandardowy obiekt danych.  

1. Wybierz **pozycję Plik**  >  **Nowy**  >  **Project**. Z listy rozwijanej języka wybierz pozycję **C#.** W polu wyszukiwania wpisz biblioteka **klas**, a następnie wybierz bibliotekę klas **(.NET Framework)** lub Bibliotekę **klas** dla .NET Standard.

   >[!NOTE]
   >Jeśli używasz testowej .NET Framework konsoli, upewnij się, że .NET Framework projektu biblioteki klas.

1. Kliknij przycisk **Dalej**. W wyświetlonym oknie dialogowym wpisz nazwę `MyDataObject` , a następnie kliknij przycisk **Utwórz**.

1. (.NET Standard biblioteki klas) W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Edytuj Project plik .** Zmień `<TargetFramework>` wartość na `netstandard2.0` .

1. W przestrzeni `MyDataObject` nazw zastąp kod domyślny następującym kodem.

   ```csharp
   [Serializable] 
   public class CustomDataObject
   {
      public CustomDataObject()
      {
         this.MyData = "MyTestData";
      }
      public string MyData { get; set; }
   }
   ```

   W przypadku wizualizatora tylko do odczytu, takiego jak w tym przykładzie, nie jest konieczne implementowanie metod [visualizerObjectSource](/dotnet/api/microsoft.visualstudio.debuggervisualizers.visualizerobjectsource).

   Następnie zaktualizuj projekt MyFirstVisualizer, aby użyć nowego obiektu danych.

1. W Eksplorator rozwiązań projektu MyFirstVisualizer kliknij prawym przyciskiem myszy węzeł **Odwołania** i wybierz polecenie **Dodaj odwołanie**.

1. W **obszarze** Projekty wybierz **projekt MyDataObject.**

1. W kodzie atrybutu pliku DebuggerSide.cs zaktualizuj wartość Target, zmieniając wartość `System.String` na `MyDataObject.CustomDataObject` .

   ```csharp
   Target = typeof(MyDataObject.CustomDataObject),
   ```

1. W projekcie MyFirstVisualizer zastąp kod `Show` metody następującym kodem.

   ```csharp
   var data = objectProvider.GetObject() as MyDataObject.CustomDataObject;

   // You can replace displayForm with your own custom Form or Control.  
   Form displayForm = new Form();
   displayForm.Text = data.MyData;
   windowService.ShowDialog(displayForm);
   ```

   Powyższy kod używa właściwości obiektu danych do pokazania w tytule formularza.

   Następnie zaktualizuj aplikację konsoli, aby używać niestandardowego obiektu danych.

1. W Eksplorator rozwiązań w projekcie MyTestConsole kliknij prawym przyciskiem  myszy węzeł **Odwołania** lub Zależności, a następnie dodaj odwołanie do projektu do . `MyDataObject`

1. W programie Program.cs zastąp kod w `Main` metodzie następującym kodem.

   ```csharp
   // String myString = "Hello, World";
   CustomDataObject customDataObject = new CustomDataObject();

   DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   ```

1. (Aplikacja konsolowa .NET) Ujmij wywołanie `TestShowVisualizer` metody w instrukcji try-catch, ponieważ wykorzystanie testów nie jest obsługiwane.

   ```csharp
   try
   {
         DebuggerSide.TestShowVisualizer(customDataObject.MyData);
   }
   catch (Exception) {
   }
   ```

   Debuger wymaga odwołania do wizualizatora. Jednym ze sposobów zachowania odwołania jest zachowanie poprzedniego kodu na miejscu.

1. W przypadku .NET Framework konsoli możesz uruchomić testowy uprząż **(naciśnij klawisz F5)** lub wykonać instrukcje w teście How to: Install a Visualizer (Instrukcje: instalowanie [wizualizatora).](../debugger/how-to-install-a-visualizer.md)

   Jeśli uruchamiasz aplikację przy użyciu uprzęży testów, zostanie ona Windows formularzu.

1. W przypadku aplikacji konsolowej .NET skopiuj wartości i do folderów opisanych w tece `MyFirstVisualizer.dll` `MyDataObject.dll` How [to: Install a Visualizer (Instaluj wizualizator).](../debugger/how-to-install-a-visualizer.md)

1. Po zainstalowaniu wizualizatora ustaw punkt przerwania, uruchom aplikację konsolową i umieść kursor `customDataObject` na . Jeśli wszystko jest poprawnie skonfigurowane, powinna zostać wyświetlony ikona ![lupy VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ikona wizualizatora").

   :::image type="content" source="../debugger/media/vs-2019/visualizer-csharp-data-object.png" alt-text="Ikona lupy wizualizatora.":::

   Po wybraniu **opcji MyFirstVisualizer** z lupy zostanie wyświetlony formularz z tekstem obiektu danych w tytule.

   ![Wizualizator przedstawiający formularz Windows formularza](../debugger/media/vs-2019/visualizer-csharp-windows-form.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Tworzenie wizualizatora przy użyciu szablonu elementu wizualizatora

Do tej pory w tym przewodniku pokazano, jak ręcznie utworzyć wizualizator. Zostało to zrobione jako ćwiczenie szkoleniowe. Teraz, gdy wiesz, jak działa prosty wizualizator, istnieje łatwiejszy sposób jego utworzenia: użycie szablonu elementu wizualizatora.

Najpierw należy utworzyć nowy projekt biblioteki klas.

### <a name="to-create-a-new-class-library"></a>Aby utworzyć nową bibliotekę klas

1. W menu **Plik** wybierz pozycję **Nowy > Project.**

2. W **oknie dialogowym Project** w obszarze **Visual C#** wybierz **pozycję .NET Framework**.

3. W środkowym okienku wybierz pozycję **Biblioteka klas**.

4. W **polu Nazwa** wpisz odpowiednią nazwę biblioteki klas, taką jak MySecondVisualizer.

5. Kliknij przycisk **OK**.

   Teraz możesz dodać do niego element wizualizatora:

### <a name="to-add-a-visualizer-item"></a>Aby dodać element wizualizatora

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję MySecondVisualizer.

2. W menu skrótów wybierz pozycję **Dodaj,** a następnie kliknij **pozycję Nowy element.**

3. W **oknie dialogowym Dodawanie nowego** elementu w obszarze **Elementy Visual C#** wybierz **pozycję Debuger Visualizer**.

4. W **polu Nazwa** wpisz odpowiednią nazwę, taką jak SecondVisualizer.cs.

5. Kliknij pozycję **Dodaj**.

   To wszystko. Przyjrzyj się plikowi SecondVisualizer.cs i wyświetl kod dodany przez szablon. Poeksperymentuj z kodem. Teraz, gdy znasz już podstawy, możesz tworzyć bardziej złożone i przydatne wizualizatory samodzielnie.
::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Architektura wizualizatora](../debugger/visualizer-architecture.md)
- [How to: Install a Visualizer](../debugger/how-to-install-a-visualizer.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)

---
title: 'Przewodnik: pisanie wizualizatora w języku C# | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b95ac29f3084bf8899249039ffbaa7da8c2294f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67890468"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Przewodnik: pisanie wizualizatora w języku C\#

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób pisania prostego wizualizatora przy użyciu języka C#. Wizualizator, który zostanie utworzony w tym instruktażu, wyświetla zawartość ciągu przy użyciu okna komunikatu formularzy systemu Windows. Ten prosty wizualizator ciągu nie jest szczególnie przydatny w sobie, ale zawiera podstawowe kroki, które należy wykonać, aby utworzyć bardziej przydatne Wizualizatory dla innych typów danych.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, przejdź do menu **Narzędzia** i wybierz polecenie **Importuj i Eksportuj ustawienia**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

Kod wizualizatora musi być umieszczony w pliku DLL, który zostanie odczytany przez debuger. W związku z tym pierwszym krokiem jest utworzenie projektu biblioteki klas dla biblioteki DLL.

#### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas

1. W menu **plik** wybierz polecenie **Nowy** , a następnie kliknij pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** w obszarze **Project Type**s wybierz pozycję **Visual C#**.

3. W polu **Szablony** wybierz pozycję **Biblioteka klas**.

4. W polu **Nazwa** wpisz odpowiednią nazwę biblioteki klas, taką jak MyFirstVisualizer.

5. Kliknij przycisk **OK**.

   Po utworzeniu biblioteki klas należy dodać odwołanie do Microsoft.VisualStudio.DebuggerVisualizers.DLL tak, aby można było używać klas zdefiniowanych w tym miejscu. Przed dodaniem odwołania należy jednak zmienić nazwy niektórych klas, aby miały one znaczące nazwy.

#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę Class1.cs i dodać Microsoft. VisualStudio. DebuggerVisualizers

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję Class1.cs i wybierz polecenie **Zmień nazwę** w menu skrótów.

2. Zmień nazwę z Class1.cs na coś znaczącego, na przykład DebuggerSide.cs.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmienia deklarację klasy w DebuggerSide.cs, aby odpowiadała nowej nazwie pliku.

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania** i wybierz polecenie **Dodaj odwołanie** w menu skrótów.

4. W oknie dialogowym **Dodaj odwołanie** na karcie **.net** wybierz pozycję Microsoft.VisualStudio.DebuggerVisualizers.DLL.

5. Kliknij przycisk **OK**.

6. W DebuggerSide.cs Dodaj następującą instrukcję do `using` instrukcji:

   ```csharp
   using Microsoft.VisualStudio.DebuggerVisualizers;
   ```

   Teraz możesz przystąpić do tworzenia kodu po stronie debugera. Jest to kod, który działa w debugerze, aby wyświetlić informacje, które chcesz wizualizować. Najpierw należy zmienić deklarację `DebuggerSide` obiektu, aby dziedziczyć z klasy bazowej `DialogDebuggerVisualizer` .

#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Aby dziedziczyć z DialogDebuggerVisualizer

1. W DebuggerSide.cs, przejdź do następującego wiersza kodu:

   ```csharp
   public class DebuggerSide
   ```

2. Zmień kod na:

   ```csharp
   public class DebuggerSide : DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` ma jedną metodę abstrakcyjną ( `Show` ), która musi zostać przesłonięta.

#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby zastąpić metodę DialogDebuggerVisualizer. show

- W programie `public class DebuggerSide` Dodaj następującą **metodę:**

  ```csharp
  override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)
  {
  }
  ```

  `Show`Metoda zawiera kod, który tworzy wizualizator okna dialogowego lub inny interfejs użytkownika i wyświetla informacje, które zostały przesłane do wizualizatora z debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym instruktażu należy to zrobić przy użyciu okna komunikatu formularzy systemu Windows. Najpierw należy dodać odwołanie i `using` instrukcję dla elementu System. Windows. Forms.

#### <a name="to-add-systemwindowsforms"></a>Aby dodać system. Windows. Forms

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania** i wybierz polecenie **Dodaj odwołanie** w menu skrótów.

2. W oknie dialogowym **Dodaj odwołanie** na karcie **.net** wybierz pozycję System.Windows.Forms.DLL.

3. Kliknij przycisk **OK**.

4. W DebuggerSide.cs Dodaj następującą instrukcję do `using` instrukcji:

   ```csharp
   using System.Windows.Forms;
   ```

   Teraz dodasz kod służący do tworzenia i wyświetlania interfejsu użytkownika wizualizatora. Ponieważ jest to Twój pierwszy wizualizator, zachowamy interfejs użytkownika, a następnie użyjemy okna komunikatu.

#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym

1. W metodzie `Show` dodaj następujący wiersz kodu:

   ```csharp
   MessageBox.Show(objectProvider.GetObject().ToString());
   ```

    Ten przykładowy kod nie zawiera obsługi błędów. Należy uwzględnić obsługę błędów w rzeczywistym wizualizatorze lub dowolnym innym rodzaju aplikacji.

2. W menu **kompilacja** wybierz polecenie **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

   To jest koniec kodu po stronie debugera. Istnieje jednak jeden krok; atrybut, który instruuje debugowanego obiektu, która kolekcja klas składa wizualizatora.

#### <a name="to-add-the-debuggee-side-code"></a>Aby dodać kod po stronie debugowanego obiektu

1. Dodaj następujący kod atrybutu do DebuggerSide.cs, po `using` instrukcjach, ale przed `namespace MyFirstVisualizer` :

   ```csharp
   [assembly:System.Diagnostics.DebuggerVisualizer(
   typeof(MyFirstVisualizer.DebuggerSide),
   typeof(VisualizerObjectSource),
   Target  = typeof(System.String),
   Description  = "My First Visualizer")]
   ```

2. W menu **kompilacja** wybierz polecenie **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

   W tym momencie pierwszy wizualizator zostanie zakończony. Jeśli wykonano kroki prawidłowo, można skompilować wizualizator i zainstalować go w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Przed zainstalowaniem wizualizatora w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] należy go przetestować, aby upewnić się, że działa poprawnie. Teraz utworzysz zespół testów do uruchamiania wizualizatora bez instalowania go w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową w celu wyświetlenia wizualizatora

1. Dodaj następującą metodę do klasy `public DebuggerSide` :

   ```csharp
   public static void TestShowVisualizer(object objectToVisualize)
   {
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
      visualizerHost.ShowVisualizer();
   }
   ```

2. W menu **kompilacja** wybierz polecenie **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.

   Następnie należy utworzyć projekt wykonywalny do wywoływania biblioteki DLL wizualizatora. Dla uproszczenia będziemy używać projektu aplikacji konsolowej.

#### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsolowej do rozwiązania

1. W menu **plik** wybierz polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt**.

2. W oknie dialogowym **Dodaj nowy projekt** w polu **Szablony** wybierz pozycję **Aplikacja konsolowa**.

3. W polu **Nazwa** wpisz nazwę zrozumiałą dla aplikacji konsolowej, na przykład `MyTestConsole` .

4. Kliknij przycisk **OK**.

   Teraz musisz dodać niezbędne odwołania, aby MyTestConsole mógł wywołać MyFirstVisualizer.

#### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do MyTestConsole

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MyTestConsole** i wybierz polecenie **Dodaj odwołanie** w menu skrótów.

2. W oknie dialogowym **Dodaj odwołanie** na karcie **.net** wybierz pozycję Microsoft.VisualStudio.DebuggerVisualizers.DLL.

3. Kliknij przycisk **OK**.

4. Kliknij prawym przyciskiem myszy pozycję **MyTestConsole** , a następnie ponownie wybierz pozycję **Dodaj odwołanie** .

5. W oknie dialogowym **Dodaj odwołanie** kliknij kartę **projekty** , a następnie kliknij pozycję MyFirstVisualizer.

6. Kliknij przycisk **OK**.

   Teraz dodasz kod do zakończenia zespołu testowego.

#### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do MyTestConsole

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję program.cs i wybierz polecenie **Zmień nazwę** w menu skrótów.

2. Zmień nazwę z Program.cs na bardziej zrozumiałą, taką jak TestConsole.cs.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmienia deklarację klasy w TestConsole.cs, aby odpowiadała nowej nazwie pliku.

3. W TestConsole.cs Dodaj następujący kod do `using` instrukcji:

   ```csharp
   using MyFirstVisualizer;
   ```

4. W metodzie `Main` Dodaj następujący kod:

   ```
   String myString = "Hello, World";
   DebuggerSide.TestShowVisualizer(myString);
   ```

   Teraz wszystko jest gotowe do przetestowania pierwszego wizualizatora.

#### <a name="to-test-the-visualizer"></a>Aby przetestować wizualizator

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MyTestConsole** i wybierz pozycję **Ustaw jako projekt startowy** w menu skrótów.

2. W menu **debugowanie** wybierz polecenie **Uruchom**.

    Aplikacja konsolowa uruchamia się, a wizualizator pojawia się i wyświetla ciąg "Hello, World".

   Gratulacje. Właśnie został skompilowany i przetestowany pierwszy wizualizator.

   Jeśli chcesz użyć wizualizatora [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zamiast tylko wywołać go z zespołu testowego, musisz go zainstalować. Aby uzyskać więcej informacji, zobacz [How to: Install the wizualizator](../debugger/how-to-install-a-visualizer.md).

## <a name="using-the-visualizer-item-template"></a>Używanie szablonu elementu wizualizatora
 Do tej pory w tym instruktażu pokazano, jak utworzyć wizualizator ręcznie. Zostało to zrobione w ramach ćwiczenia szkoleniowego. Teraz, gdy wiesz już, jak działa prosty wizualizator, istnieje łatwiejszy sposób, aby go utworzyć: przy użyciu szablonu elementu wizualizatora.

 Najpierw należy utworzyć nowy projekt biblioteki klas.

#### <a name="to-create-a-new-class-library"></a>Aby utworzyć nową bibliotekę klas

1. W menu **plik** wybierz polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt**.

2. W oknie dialogowym **Dodaj nowy projekt** w obszarze **Project Type**s wybierz pozycję **Visual C#**.

3. W polu **Szablony** wybierz pozycję **Biblioteka klas**.

4. W polu **Nazwa** wpisz odpowiednią nazwę biblioteki klas, taką jak MySecondVisualizer.

5. Kliknij przycisk **OK**.

   Teraz można dodać do niego element wizualizatora:

#### <a name="to-add-a-visualizer-item"></a>Aby dodać element wizualizatora

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję MySecondVisualizer.

2. W menu skrótów wybierz polecenie **Dodaj** , a następnie kliknij pozycję **nowy element**.

3. W oknie dialogowym **Dodaj nowy element** w obszarze **Szablony**, **zainstalowane szablony programu Visual Studio**wybierz **wizualizator debugera**.

4. W polu **Nazwa** wpisz odpowiednią nazwę, na przykład SecondVisualizer.cs.

5. Kliknij pozycję **Dodaj**.

   To wszystko. Spójrz na plik SecondVisualizer.cs i Wyświetl kod, który został dodany przez szablon. Przejdź dalej i poeksperymentuj z kodem. Teraz, gdy znasz już podstawowe elementy, jesteś w trakcie tworzenia bardziej złożonych i przydatnych wizualizatorów.

## <a name="see-also"></a>Zobacz też

- [Architektura wizualizatora](../debugger/visualizer-architecture.md)
- [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)

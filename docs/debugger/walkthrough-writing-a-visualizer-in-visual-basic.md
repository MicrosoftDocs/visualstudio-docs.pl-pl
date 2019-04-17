---
title: Pisanie wizualizatora w języku Visual Basic | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 04/12/2019
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
ms.openlocfilehash: d30e789d0ae3fa3e717be9739b94439a7d6a31a2
ms.sourcegitcommit: 847d192013eb8225776243045c9b5a53d1ba4a59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2019
ms.locfileid: "59584548"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Przewodnik: Pisanie wizualizatora w języku Visual Basic
W tym przewodniku pokazano, jak pisanie prostego wizualizatora przy użyciu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Wizualizator, która zostanie utworzona w tym przewodniku Wyświetla zawartość ciągu przy użyciu Windows Forms okno komunikatu. Ten Wizualizator prostego ciągu jest prosty przykład, aby pokazać, jak utworzyć wizualizatorów dla innych typów danych bardziej odpowiednie do swoich projektów.

> [!NOTE]
> Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, przejdź do **narzędzia** menu i wybrać **importowanie i eksportowanie** . Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

Wizualizator kodu muszą być umieszczone w pliku DLL, który będzie odczytywany przez debuger. Pierwszym krokiem jest, aby utworzyć projekt biblioteki klas dla biblioteki DLL.

## <a name="create-and-prepare-a-class-library-project"></a>Tworzenie i przygotowywanie projektu biblioteki klas

### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas

1. Utwórz nowy projekt biblioteki klas.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **Esc** aby zamknąć okno rozpoczęcia. Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **języka visual basic**, wybierz **szablony**, następnie wybierz **Utwórz nową bibliotekę klas (.NET Standard)**. W oknie dialogowym wybierz **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okno dialogowe, w obszarze **języka Visual Basic**, wybierz **.NET Standard**, a następnie w środkowym okienku wybierz **biblioteki klas (platforma .NET Warstwa standardowa)**.
    ::: moniker-end

2. Wpisz odpowiednią nazwę biblioteki klas, taką jak `MyFirstVisualizer`, a następnie kliknij przycisk **Utwórz** lub **OK**.

   Po utworzeniu biblioteki klas należy dodać odwołanie do Microsoft.VisualStudio.DebuggerVisualizers.DLL, tak, aby można było używać klas zdefiniowanych istnieje. Najpierw jednak należy nadaj projektowi nazwę opisową.

### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę Class1.vb i dodać Microsoft.VisualStudio.DebuggerVisualizers

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Class1.vb**, a następnie w menu skrótów kliknij **Zmień nazwę**.

2. Zmień nazwę z Class1.vb na bardziej opisową nazwę, takich jak DebuggerSide.vb.

   > [!NOTE]
   >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmienia deklaracji klasy w DebuggerSide.vb, aby dopasować nazwę nowego pliku.

3. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Mój pierwszy Wizualizator**, a następnie w menu skrótów kliknij **Dodaj odwołanie**.

4. W **Dodaj odwołanie** dialogowym **Przeglądaj** zaznacz **Przeglądaj** i Znajdź Microsoft.VisualStudio.DebuggerVisualizers.DLL.

    Można znaleźć biblioteki DLL w  *\<Visual Studio katalog instalacji > \Common7\IDE\PublicAssemblies* podkatalogu katalogu instalacyjnego programu Visual Studio.

5. Kliknij przycisk **OK**.

6. W DebuggerSide.vb, dodaj następującą instrukcję, aby `Imports` instrukcji:

   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers
   ```

## <a name="add-the-debugger-side-code"></a>Dodaj kod po stronie debugera
 Teraz można przystąpić do pisania kodu po stronie debugera. Jest to kod, który jest uruchamiany w ramach debugera, aby wyświetlić informacje, które mają być wyświetlane. Najpierw należy zmienić deklarację `DebuggerSide` obiekt dziedziczy z klasy bazowej `DialogDebuggerVisualizer`.

### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dziedziczenie z DialogDebuggerVisualizer

1. W DebuggerSide.vb przejdź do następującego kodu:

   ```vb
   Public Class DebuggerSide
   ```

2. Edytowanie kodu, tak że wygląda następująco:

   ```vb
   Public Class DebuggerSide
   Inherits DialogDebuggerVisualizer
   ```

   `DialogDebuggerVisualizer` zawiera jedną metodę abstrakcyjną, `Show`, który należy zastąpić.

### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby przesłonić metodę DialogDebuggerVisualizer.Show

- W `public class DebuggerSide`, dodaj następującą metodę:

  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)

      End Sub
  ```

  `Show` Metoda zawiera kod, który faktycznie tworzy okno dialogowe Wizualizator lub innego interfejsu użytkownika i wyświetla informacje, który został przekazany do wizualizatora z debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym instruktażu będziesz to robić przy użyciu Windows Forms okno komunikatu. Najpierw musisz dodać odwołanie i `Imports` poufności informacji dotyczące <xref:System.Windows.Forms>.

### <a name="to-add-systemwindowsforms"></a>Aby dodać przestrzeń nazw System.Windows.Forms

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie w menu skrótów kliknij **Dodaj odwołanie**.

2. W **Dodaj odwołanie** dialogowym **Przeglądaj** zaznacz **Przeglądaj**i Znajdź System.Windows.Forms.DLL.

    Można znaleźć biblioteki DLL w *C:\Windows\Microsoft.NET\Framework\v4.0.30319*.

3.  Kliknij przycisk **OK**.

4.  W DebuggerSide.cs, dodaj następującą instrukcję, aby `Imports` instrukcji:

    ```vb
    Imports System.Windows.Forms
    ```

## <a name="create-your-visualizers-user-interface"></a>Tworzenie interfejsu użytkownika usługi wizualizatora
 Teraz dodasz działał kod służący do tworzenia i wyświetlać interfejsu użytkownika dla usługi wizualizatora. Ponieważ jest to Twoje pierwsze wizualizatora, będzie proste interfejsu użytkownika i użyć okno komunikatu.

### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym

1.  W `Show` metody, Dodaj następujący wiersz kodu:

    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())
    ```

     Ten przykładowy kod nie ma obsługi błędów. Powinien zawierać obsługę błędów w rzeczywistych Wizualizator lub dowolny inny rodzaj aplikacji.

2.  Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.

## <a name="add-the-necessary-attribute"></a>Dodaj atrybut niezbędne
 To już koniec kodu po stronie debugera. Istnieje jeszcze jeden krok, jednak: atrybut, który informuje po stronie debugowanego obiektu, która kolekcja klas składa się z wizualizatora.

### <a name="to-add-the-debugee-side-code"></a>Aby dodać kod po stronie debugee

1.  Dodaj następujący kod atrybutu do DebuggerSide.vb, po `Imports` instrukcji lecz przed `namespace MyFirstVisualizer`:

    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>
    ```

2.  Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.

## <a name="create-a-test-harness"></a>Utwórz kontroler testu
 W tym momencie Twojego pierwszego Wizualizator jest zakończony. Jeśli kroki zostały wykonane poprawnie, można utworzyć wizualizatora i zainstalować go do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Przed zainstalowaniem wizualizatora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], jednak należy go przetestować, aby upewnić się, że działa poprawnie. Teraz możesz utworzyć kontroler testów do uruchomienia wizualizatora bez konieczności instalowania go do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową, aby wyświetlić wizualizatora

1. Dodaj następującą metodę do klasy `public DebuggerSide`:

   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))
   visualizerHost.ShowVisualizer()
   End Sub
   ```

2. Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.

   Następnie należy utworzyć projekt wykonywalny do wywołania usługi Wizualizator biblioteki DLL. Dla uproszczenia należy użyć projektu aplikacji konsolowej.

### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsoli w rozwiązaniu

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj**, a następnie kliknij przycisk **nowy projekt**.

    ::: moniker range=">=vs-2019"
    W polu wyszukiwania wpisz **języka visual basic**, wybierz **szablony**, następnie wybierz **Utwórz nową aplikację konsoli (.NET Framework)**. W oknie dialogowym wybierz **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okno dialogowe, w obszarze **języka Visual Basic**, wybierz **pulpitu Windows**, a następnie w środkowym okienku wybierz **Aplikacja konsoli (.NET Framework)**.
    ::: moniker-end

2. Wpisz odpowiednią nazwę biblioteki klas, taką jak `MyTestConsole`, a następnie kliknij przycisk **Utwórz** lub **OK**.

   Teraz musisz dodać niezbędne odwołania tak MyTestConsole może wywołać MyFirstVisualizer.

### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do MyTestConsole

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole**, a następnie w menu skrótów kliknij **Dodaj odwołanie**.

2.  W **Dodaj odwołanie** dialogowym **Przeglądaj** Microsoft.VisualStudio.DebuggerVisualizers kliknij pozycję.

3.  Kliknij przycisk **OK**.

4.  Kliknij prawym przyciskiem myszy **MyTestConsole**, a następnie kliknij przycisk **Dodaj odwołanie** ponownie.

5.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **projektów** , a następnie wybierz pozycję MyFirstVisualizer.

6.  Kliknij przycisk **OK**.

## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Zakończenie swoje kontroler testów i przetestowanie usługi wizualizatora
 Teraz dodasz kod, aby zakończyć kontroler testów.

### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do MyTestConsole

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.vb**, a następnie w menu skrótów kliknij **Zmień nazwę**.

2. Edytuj nazwę z Module1.vb, aby pasowały, takich jak **TestConsole.vb**.

    Należy zauważyć, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie zmieni deklaracji klasy w TestConsole.vb, aby dopasować nazwę nowego pliku.

3. W TestConsole. VB, Dodaj następujący kod `Imports` instrukcji:

   ```vb
   Imports MyFirstVisualizer
   ```

4. W metodzie `Main`, Dodaj następujący kod:

   ```vb
   Dim myString As String = "Hello, World"
   DebuggerSide.TestShowVisualizer(myString)
   ```

   Teraz można przystąpić do testowania Twojego pierwszego wizualizatora.

### <a name="to-test-the-visualizer"></a>Aby przetestować Wizualizator

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole**, a następnie w menu skrótów kliknij **Ustaw jako projekt startowy**.

2. Na **debugowania** menu, kliknij przycisk **Start**.

    Uruchamia aplikację konsolową. Wizualizator pojawi się i wyświetli ciąg "Hello, World."

   Gratulacje. Mieć po prostu tworzone i testowane na Twoje pierwsze wizualizatora.

   Aby korzystanie z wizualizatora w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zamiast po prostu wywoływanie z kontroler testów, należy go zainstalować. Aby uzyskać więcej informacji, zobacz [jak: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md).

## <a name="see-also"></a>Zobacz także

- [Architektura wizualizatora](../debugger/visualizer-architecture.md)
- [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)
- [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)
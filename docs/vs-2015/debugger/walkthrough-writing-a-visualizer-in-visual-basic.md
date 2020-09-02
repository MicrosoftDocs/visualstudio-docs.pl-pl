---
title: 'Przewodnik: pisanie wizualizatora w Visual Basic | Microsoft Docs'
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
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 954bd976317f5b5ad577b1236c9d7421c2d50315
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688210"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Wskazówki: pisanie wizualizatora w Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób pisania prostego wizualizatora przy użyciu [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . Wizualizator, który utworzysz w tym instruktażu, wyświetla zawartość ciągu przy użyciu okna komunikatu Windows Forms. Ten prosty wizualizator ciągów to podstawowy przykład pokazujący, jak tworzyć Wizualizatory dla innych typów danych, które są bardziej odpowiednie dla projektów.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, przejdź do menu **Narzędzia** i wybierz polecenie **Importuj i Eksportuj** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Kod wizualizatora musi być umieszczony w pliku DLL, który będzie odczytywany przez debuger. Pierwszym krokiem jest utworzenie projektu biblioteki klas dla biblioteki DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Utwórz i przygotuj projekt biblioteki klas  
  
#### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas  
  
1. W menu **plik** wybierz polecenie **Nowy** , a następnie kliknij pozycję **Nowy projekt**.  
  
2. W oknie dialogowym **Nowy projekt** w obszarze **Project Type**s kliknij **Visual Basic**.  
  
3. W polu **Szablony** kliknij pozycję **Biblioteka klas**.  
  
4. W polu **Nazwa** wpisz odpowiednią nazwę biblioteki klas, taką jak **MyFirstVisualizer**.  
  
5. Kliknij przycisk **OK**.  
  
   Po utworzeniu biblioteki klas należy dodać odwołanie do Microsoft.VisualStudio.DebuggerVisualizers.DLL, tak aby można było używać klas zdefiniowanych w tym miejscu. Najpierw jednak Nadaj projektowi zrozumiałą nazwę.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę Class1. vb i dodać Microsoft. VisualStudio. DebuggerVisualizers  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **Class1. vb**, a następnie w menu skrótów kliknij polecenie **Zmień nazwę**.  
  
2. Zmień nazwę z Class1. vb na coś znaczącego, na przykład DebuggerSide. vb.  
  
    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmienia deklarację klasy w DebuggerSide. vb w celu dopasowania jej do nazwy nowego pliku.  
  
3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **mój pierwszy wizualizator**, a następnie w menu skrótów kliknij pozycję **Dodaj odwołanie**.  
  
4. W oknie dialogowym **Dodaj odwołanie** na karcie **.net** kliknij przycisk Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5. Kliknij przycisk **OK**.  
  
6. W DebuggerSide. vb Dodaj następującą instrukcję do `Imports` instrukcji:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Dodawanie kodu po stronie debugera  
 Teraz możesz przystąpić do tworzenia kodu po stronie debugera. Jest to kod, który działa w debugerze, aby wyświetlić informacje, które chcesz wizualizować. Najpierw należy zmienić deklarację `DebuggerSide` obiektu, aby dziedziczyć z klasy bazowej `DialogDebuggerVisualizer` .  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Aby dziedziczyć z DialogDebuggerVisualizer  
  
1. W DebuggerSide. vb przejdź do następującego wiersza kodu:  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. Edytuj kod w taki sposób, aby wyglądał następująco:  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` ma jedną metodę abstrakcyjną, `Show` która musi zostać przesłonięta.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby zastąpić metodę DialogDebuggerVisualizer. show  
  
- W programie `public class DebuggerSide` Dodaj następującą metodę:  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  `Show`Metoda zawiera kod, który tworzy wizualizatorer okno dialogowe lub inny interfejs użytkownika i wyświetla informacje, które zostały przesłane do wizualizatora z debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym instruktażu należy to zrobić przy użyciu okna komunikatu Windows Forms. Najpierw należy dodać odwołanie i `Imports` instrukcję dla <xref:System.Windows.Forms> .  
  
#### <a name="to-add-systemwindowsforms"></a>Aby dodać system. Windows. Forms  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania**, a następnie w menu skrótów kliknij pozycję **Dodaj odwołanie**.  
  
2. W oknie dialogowym **Dodawanie odwołania** na karcie **.NET** kliknij pozycję **System. Windows. Forms**.  
  
3. Kliknij przycisk **OK**.  
  
4. W DebuggerSide.cs Dodaj następującą instrukcję do `Imports` instrukcji:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Tworzenie interfejsu użytkownika wizualizatora  
 Teraz dodasz kod do tworzenia i wyświetlania interfejsu użytkownika wizualizatora. Ponieważ jest to Twój pierwszy wizualizator, będziesz utrzymywać prosty interfejs użytkownika i korzystać z okna komunikatu.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym  
  
1. W metodzie `Show` dodaj następujący wiersz kodu:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Ten przykładowy kod nie zawiera obsługi błędów. Należy uwzględnić obsługę błędów w rzeczywistym wizualizatorze lub dowolnym innym rodzaju aplikacji.  
  
2. W menu **kompilacja** kliknij pozycję **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.  
  
## <a name="add-the-necessary-attribute"></a>Dodaj wymagany atrybut  
 To jest koniec kodu po stronie debugera. Istnieje jeszcze jeden krok, jednak: atrybut, który instruuje debugowanego obiektu, która kolekcja klas składa się wizualizatora.  
  
#### <a name="to-add-the-debugee-side-code"></a>Aby dodać kod po stronie debugee  
  
1. Dodaj następujący kod atrybutu do DebuggerSide. vb po `Imports` instrukcjach, ale przed `namespace MyFirstVisualizer` :  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2. W menu **kompilacja** kliknij pozycję **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.  
  
## <a name="create-a-test-harness"></a>Tworzenie zespołu testowego  
 W tym momencie pierwszy wizualizator zostanie zakończony. Jeśli wykonano kroki prawidłowo, można skompilować wizualizator i zainstalować go w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Przed zainstalowaniem wizualizatora w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] należy go przetestować, aby upewnić się, że działa poprawnie. Teraz utworzysz zespół testów do uruchamiania wizualizatora bez instalowania go w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową w celu wyświetlenia wizualizatora  
  
1. Dodaj następującą metodę do klasy `public DebuggerSide` :  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. W menu **kompilacja** kliknij pozycję **Kompiluj MyFirstVisualizer**. Projekt powinien zostać skompilowany pomyślnie. Popraw wszystkie błędy kompilacji przed kontynuowaniem.  
  
   Następnie należy utworzyć projekt wykonywalny do wywoływania biblioteki DLL wizualizatora. Dla uproszczenia Użyj projektu aplikacji konsolowej.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsolowej do rozwiązania  
  
1. W menu **plik** kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.  
  
2. W oknie dialogowym **Dodaj nowy projekt** w polu **Szablony** kliknij pozycję **Aplikacja konsolowa**.  
  
3. W polu **Nazwa** wpisz nazwę zrozumiałą dla aplikacji konsolowej, na przykład **MyTestConsole**.  
  
4. Kliknij przycisk **OK**.  
  
   Teraz musisz dodać niezbędne odwołania, aby MyTestConsole mógł wywołać MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do MyTestConsole  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MyTestConsole**, a następnie w menu skrótów kliknij pozycję **Dodaj odwołanie**.  
  
2. W oknie dialogowym **Dodawanie odwołania** na karcie **.NET** kliknij pozycję Microsoft. VisualStudio. DebuggerVisualizers.  
  
3. Kliknij przycisk **OK**.  
  
4. Kliknij prawym przyciskiem myszy pozycję **MyTestConsole**, a następnie ponownie kliknij pozycję **Dodaj odwołanie** .  
  
5. W oknie dialogowym **Dodaj odwołanie** kliknij kartę **projekty** , a następnie wybierz pozycję MyFirstVisualizer.  
  
6. Kliknij przycisk **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Zakończ pracę zespołu testowego i przetestuj wizualizator  
 Teraz dodasz kod do zakończenia zespołu testowego.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do MyTestConsole  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **program Visual. vb**, a następnie w menu skrótów kliknij polecenie **Zmień nazwę**.  
  
2. Edytuj nazwę z Module1. vb do odpowiedniego elementu, takiego jak **TestConsole. vb**.  
  
    Należy zauważyć, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Automatyczna zmiana deklaracji klasy w TestConsole. vb w celu dopasowania do nazwy nowego pliku.  
  
3. W TestConsole. VB, Dodaj następującą `Imports` instrukcję:  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. W metodzie `Main` Dodaj następujący kod:  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   Teraz można przystąpić do testowania pierwszego wizualizatora.  
  
#### <a name="to-test-the-visualizer"></a>Aby przetestować wizualizator  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **MyTestConsole**, a następnie w menu skrótów kliknij pozycję **Ustaw jako projekt startowy**.  
  
2. W menu **debugowanie** kliknij przycisk **Uruchom**.  
  
    Zostanie uruchomiona aplikacja konsolowa. Wizualizator zostanie wyświetlony i zostanie wyświetlony ciąg "Hello, World".  
  
   Gratulacje. Właśnie został skompilowany i przetestowany pierwszy wizualizator.  
  
   Jeśli chcesz użyć wizualizatora [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zamiast tylko wywołać go z zespołu testowego, musisz go zainstalować. Aby uzyskać więcej informacji, zobacz [How to: Install the wizualizator](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura wizualizatora](../debugger/visualizer-architecture.md)   
 [Instrukcje: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)   
 [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)

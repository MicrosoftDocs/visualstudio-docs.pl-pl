---
title: 'Wskazówki: Pisanie wizualizatora w języku Visual Basic | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 549e1ce240808a3947b2780f5c96485439e44ecc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794903"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Wskazówki: pisanie wizualizatora w Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku pokazano, jak pisanie prostego wizualizatora przy użyciu [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Wizualizator, która zostanie utworzona w tym przewodniku Wyświetla zawartość ciągu przy użyciu Windows Forms okno komunikatu. Ten Wizualizator prostego ciągu jest prosty przykład, aby pokazać, jak utworzyć wizualizatorów dla innych typów danych bardziej odpowiednie do swoich projektów.  
  
> [!NOTE]
>  Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, przejdź do **narzędzia** menu i wybrać **importowanie i eksportowanie** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Wizualizator kodu muszą być umieszczone w pliku DLL, który będzie odczytywany przez debuger. Pierwszym krokiem jest, aby utworzyć projekt biblioteki klas dla biblioteki DLL.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Tworzenie i przygotowywanie projektu biblioteki klas  
  
#### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas  
  
1. Na **pliku** menu, wybierz **New** i kliknij przycisk **nowy projekt**.  
  
2. W **nowy projekt** dialogowego **typu projektu**s, kliknij przycisk **języka Visual Basic**.  
  
3. W **szablony** kliknij **biblioteki klas**.  
  
4. W **nazwa** wpisz odpowiednią nazwę biblioteki klas, takie jak **MyFirstVisualizer**.  
  
5. Kliknij przycisk **OK**.  
  
   Po utworzeniu biblioteki klas należy dodać odwołanie do Microsoft.VisualStudio.DebuggerVisualizers.DLL, tak, aby można było używać klas zdefiniowanych istnieje. Najpierw jednak należy nadaj projektowi nazwę opisową.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Aby zmienić nazwę Class1.vb i dodać Microsoft.VisualStudio.DebuggerVisualizers  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Class1.vb**, a następnie w menu skrótów kliknij **Zmień nazwę**.  
  
2.  Zmień nazwę z Class1.vb na bardziej opisową nazwę, takich jak DebuggerSide.vb.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmienia deklaracji klasy w DebuggerSide.vb, aby dopasować nazwę nowego pliku.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Mój pierwszy Wizualizator**, a następnie w menu skrótów kliknij **Dodaj odwołanie**.  
  
4.  W **Dodaj odwołanie** dialogowym **.NET** Microsoft.VisualStudio.DebuggerVisualizers.DLL kliknij pozycję.  
  
5.  Kliknij przycisk **OK**.  
  
6.  W DebuggerSide.vb, dodaj następującą instrukcję, aby `Imports` instrukcji:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>Dodaj kod po stronie debugera  
 Teraz można przystąpić do pisania kodu po stronie debugera. Jest to kod, który jest uruchamiany w ramach debugera, aby wyświetlić informacje, które mają być wyświetlane. Najpierw należy zmienić deklarację `DebuggerSide` obiekt dziedziczy z klasy bazowej `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dziedziczenie z DialogDebuggerVisualizer  
  
1. W DebuggerSide.vb przejdź do następującego kodu:  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. Edytowanie kodu, tak że wygląda następująco:  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` zawiera jedną metodę abstrakcyjną, `Show`, który należy zastąpić.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby przesłonić metodę DialogDebuggerVisualizer.Show  
  
- W `public class DebuggerSide`, dodaj następującą metodę:  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  `Show` Metoda zawiera kod, który faktycznie tworzy okno dialogowe Wizualizator lub innego interfejsu użytkownika i wyświetla informacje, który został przekazany do wizualizatora z debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym instruktażu będziesz to robić przy użyciu Windows Forms okno komunikatu. Najpierw musisz dodać odwołanie i `Imports` poufności informacji dotyczące <xref:System.Windows.Forms>.  
  
#### <a name="to-add-systemwindowsforms"></a>Aby dodać przestrzeń nazw System.Windows.Forms  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania**, a następnie w menu skrótów kliknij **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** dialogowym **.NET** kliknij pozycję **System.Windows.Forms**.  
  
3.  Kliknij przycisk **OK**.  
  
4.  W DebuggerSide.cs, dodaj następującą instrukcję, aby `Imports` instrukcji:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Tworzenie interfejsu użytkownika usługi wizualizatora  
 Teraz dodasz działał kod służący do tworzenia i wyświetlać interfejsu użytkownika dla usługi wizualizatora. Ponieważ jest to Twoje pierwsze wizualizatora, będzie proste interfejsu użytkownika i użyć okno komunikatu.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym  
  
1.  W `Show` metody, Dodaj następujący wiersz kodu:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Ten przykładowy kod nie ma obsługi błędów. Powinien zawierać obsługę błędów w rzeczywistych Wizualizator lub dowolny inny rodzaj aplikacji.  
  
2.  Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.  
  
## <a name="add-the-necessary-attribute"></a>Dodaj atrybut niezbędne  
 To już koniec kodu po stronie debugera. Istnieje jeszcze jeden krok, jednak: atrybut, który informuje po stronie debugowanego obiektu, która kolekcja klas składa się z wizualizatora.  
  
#### <a name="to-add-the-debugee-side-code"></a>Aby dodać kod po stronie debugee  
  
1.  Dodaj następujący kod atrybutu do DebuggerSide.vb, po `Imports` instrukcji lecz przed `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.  
  
## <a name="create-a-test-harness"></a>Utwórz kontroler testu  
 W tym momencie Twojego pierwszego Wizualizator jest zakończony. Jeśli kroki zostały wykonane poprawnie, można utworzyć wizualizatora i zainstalować go do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Przed zainstalowaniem wizualizatora do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], jednak należy go przetestować, aby upewnić się, że działa poprawnie. Teraz możesz utworzyć kontroler testów do uruchomienia wizualizatora bez konieczności instalowania go do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową, aby wyświetlić wizualizatora  
  
1. Dodaj następującą metodę do klasy `public DebuggerSide`:  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. Na **kompilacji** menu, kliknij przycisk **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.  
  
   Następnie należy utworzyć projekt wykonywalny do wywołania usługi Wizualizator biblioteki DLL. Dla uproszczenia należy użyć projektu aplikacji konsolowej.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsoli w rozwiązaniu  
  
1. Na **pliku** menu, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.  
  
2. W **Dodaj nowy projekt** dialogowym **szablony** kliknij **aplikację Konsolową**.  
  
3. W **nazwa** wpisz nazwę opisową dla aplikacji konsoli, takie jak **MyTestConsole**.  
  
4. Kliknij przycisk **OK**.  
  
   Teraz musisz dodać niezbędne odwołania tak MyTestConsole może wywołać MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do MyTestConsole  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole**, a następnie w menu skrótów kliknij **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** dialogowym **.NET** Microsoft.VisualStudio.DebuggerVisualizers kliknij pozycję.  
  
3.  Kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **MyTestConsole**, a następnie kliknij przycisk **Dodaj odwołanie** ponownie.  
  
5.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **projektów** , a następnie wybierz pozycję MyFirstVisualizer.  
  
6.  Kliknij przycisk **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Zakończenie swoje kontroler testów i przetestowanie usługi wizualizatora  
 Teraz dodasz kod, aby zakończyć kontroler testów.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do MyTestConsole  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.vb**, a następnie w menu skrótów kliknij **Zmień nazwę**.  
  
2. Edytuj nazwę z Module1.vb, aby pasowały, takich jak **TestConsole.vb**.  
  
    Należy zauważyć, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmieni deklaracji klasy w TestConsole.vb, aby dopasować nazwę nowego pliku.  
  
3. W TestConsole. VB, Dodaj następujący kod `Imports` instrukcji:  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. W metodzie `Main`, Dodaj następujący kod:  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   Teraz można przystąpić do testowania Twojego pierwszego wizualizatora.  
  
#### <a name="to-test-the-visualizer"></a>Aby przetestować Wizualizator  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole**, a następnie w menu skrótów kliknij **Ustaw jako projekt startowy**.  
  
2. Na **debugowania** menu, kliknij przycisk **Start**.  
  
    Uruchamia aplikację konsolową. Wizualizator pojawi się i wyświetli ciąg "Hello, World."  
  
   Gratulacje. Mieć po prostu tworzone i testowane na Twoje pierwsze wizualizatora.  
  
   Aby korzystanie z wizualizatora w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zamiast po prostu wywoływanie z kontroler testów, należy go zainstalować. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura wizualizatora](../debugger/visualizer-architecture.md)   
 [Porady: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)   
 [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)




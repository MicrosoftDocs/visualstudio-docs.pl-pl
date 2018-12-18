---
title: 'Wskazówki: Pisanie wizualizatora w języku C# | Dokumentacja firmy Microsoft'
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
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e265810e30423064e27b1650f57fb054743341ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817337"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Wskazówki: Pisanie wizualizatora w C# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak pisanie prostego wizualizatora przy użyciu języka C#. Wizualizator, która zostanie utworzona w tym przewodniku Wyświetla zawartość ciągu przy użyciu okna komunikatu Windows forms. Ten Wizualizator prostego ciągu nie jest szczególnie przydatne w sobie, ale pokazuje podstawowe kroki, które należy wykonać, aby utworzyć bardziej użyteczny, wizualizatorów dla innych typów danych.  
  
> [!NOTE]
>  Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, przejdź do **narzędzia** menu i wybrać **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Wizualizator kodu muszą być umieszczone w bibliotece DLL, który będzie odczytywany przez debuger. W związku z tym pierwszym krokiem jest utworzenie projektu biblioteki klas dla biblioteki DLL.  
  
#### <a name="to-create-a-class-library-project"></a>Aby utworzyć projekt biblioteki klas  
  
1. Na **pliku** menu, wybierz **New** a następnie kliknij przycisk **nowy projekt**.  
  
2. W **nowy projekt** dialogowego **typu projektu**s, wybierz opcję **Visual C#**.  
  
3. W **szablony** wybierz **biblioteki klas**.  
  
4. W **nazwa** wpisz odpowiednią nazwę biblioteki klas, takie jak MyFirstVisualizer.  
  
5. Kliknij przycisk **OK**.  
  
   Po utworzeniu biblioteki klas, należy dodać odwołanie do Microsoft.VisualStudio.DebuggerVisualizers.DLL tak, aby można było używać klas zdefiniowanych istnieje. Przed dodaniem odwołania, jednak należy zmienić niektóre klasy tak, że mają one nadawać opisowe nazwy.  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Zmień nazwę Class1.cs, a następnie dodać Microsoft.VisualStudio.DebuggerVisualizers  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy Class1.cs i wybierz polecenie **Zmień nazwę** w menu skrótów.  
  
2. Nazwę można zmienić poziomu Class1.cs, wpisując tekst opisowy, takich jak DebuggerSide.cs.  
  
   > [!NOTE]
   >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmienia deklaracji klasy w DebuggerSide.cs, aby dopasować nazwę nowego pliku.  
  
3. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie** w menu skrótów.  
  
4. W **Dodaj odwołanie** dialogowym **.NET** kartę, wybrać Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5. Kliknij przycisk **OK**.  
  
6. W DebuggerSide.cs, dodaj następującą instrukcję, aby `using` instrukcji:  
  
   ```  
   using Microsoft.VisualStudio.DebuggerVisualizers;  
   ```  
  
   Teraz można przystąpić do pisania kodu po stronie debugera. Jest to kod, który jest uruchamiany w ramach debugera, aby wyświetlić informacje, które mają być wyświetlane. Najpierw należy zmienić deklarację `DebuggerSide` obiekt, który dziedziczy z klasy bazowej `DialogDebuggerVisualizer`.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>Dziedziczenie z DialogDebuggerVisualizer  
  
1. W DebuggerSide.cs przejdź do następującego kodu:  
  
   ```  
   public class DebuggerSide  
   ```  
  
2. Zmień kod, aby:  
  
   ```  
   public class DebuggerSide : DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` zawiera jedną metodę abstrakcyjną (`Show`), konieczne jest przesłonięcie.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>Aby przesłonić metodę DialogDebuggerVisualizer.Show  
  
- W `public class DebuggerSide`, Dodaj następujący kod **metody:**  
  
  ```  
  override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
  {  
  }  
  ```  
  
  `Show` Metoda zawiera kod, który faktycznie tworzy okno dialogowe Wizualizator lub innego interfejsu użytkownika i wyświetla informacje, który został przekazany do wizualizatora z debugera. Należy dodać kod, który tworzy okno dialogowe i wyświetla informacje. W tym instruktażu będziesz to robić przy użyciu okna komunikatu Windows forms. Najpierw musisz dodać odwołanie i `using` poufności informacji dotyczące przestrzeń nazw System.Windows.Forms.  
  
#### <a name="to-add-systemwindowsforms"></a>Aby dodać przestrzeń nazw System.Windows.Forms  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie** w menu skrótów.  
  
2. W **Dodaj odwołanie** dialogowym **.NET** karty, wybierz pozycję System.Windows.Forms.DLL.  
  
3. Kliknij przycisk **OK**.  
  
4. W DebuggerSide.cs, dodaj następującą instrukcję, aby `using` instrukcji:  
  
   ```  
   using System.Windows.Forms;  
   ```  
  
   Teraz dodasz działał kod służący do tworzenia i wyświetlać interfejsu użytkownika dla usługi wizualizatora. Ponieważ jest to Twoje pierwsze wizualizatora, jesteśmy będzie proste interfejsu użytkownika i okno komunikatu.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>Aby wyświetlić dane wyjściowe wizualizatora w oknie dialogowym  
  
1. W `Show` metody, Dodaj następujący wiersz kodu:  
  
   ```  
   MessageBox.Show(objectProvider.GetObject().ToString());  
   ```  
  
    Ten przykładowy kod nie ma obsługi błędów. Powinien zawierać obsługę błędów w rzeczywistych Wizualizator lub dowolny inny rodzaj aplikacji.  
  
2. Na **kompilacji** menu, wybierz **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.  
  
   To już koniec kodu po stronie debugera. Istnieje jeszcze jeden krok, jednak; atrybut, który informuje po stronie debugowanego obiektu, która kolekcja klas, obejmuje wizualizatora.  
  
#### <a name="to-add-the-debuggee-side-code"></a>Aby dodać kod po stronie debugowanego obiektu  
  
1. Dodaj następujący kod atrybutu do DebuggerSide.cs, po `using` instrukcji lecz przed `namespace MyFirstVisualizer`:  
  
   ```  
   [assembly:System.Diagnostics.DebuggerVisualizer(  
   typeof(MyFirstVisualizer.DebuggerSide),  
   typeof(VisualizerObjectSource),  
   Target  = typeof(System.String),  
   Description  = "My First Visualizer")]  
   ```  
  
2. Na **kompilacji** menu, wybierz **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.  
  
   W tym momencie Twojego pierwszego Wizualizator jest zakończony. Jeśli kroki zostały wykonane poprawnie, można utworzyć wizualizatora i zainstalować go do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Przed zainstalowaniem wizualizatora do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], jednak należy go przetestować, aby upewnić się, że działa poprawnie. Teraz możesz utworzyć kontroler testów do uruchomienia wizualizatora bez konieczności instalowania go do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>Aby dodać metodę testową, aby wyświetlić wizualizatora  
  
1. Dodaj następującą metodę do klasy `public DebuggerSide`:  
  
   ```  
   public static void TestShowVisualizer(object objectToVisualize)  
   {  
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
      visualizerHost.ShowVisualizer();  
   }  
   ```  
  
2. Na **kompilacji** menu, wybierz **kompilacji MyFirstVisualizer**. Projekt powinien być kompilowany pomyślnie. Usuń wszelkie błędy kompilacji, aby kontynuować.  
  
   Następnie należy utworzyć projekt wykonywalny do wywołania usługi Wizualizator biblioteki DLL. Dla uproszczenia używamy projekt aplikacji konsoli.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>Aby dodać projekt aplikacji konsoli w rozwiązaniu  
  
1. Na **pliku** menu, wybierz **Dodaj** a następnie kliknij przycisk **nowy projekt**.  
  
2. W **Dodaj nowy projekt** dialogowym **szablony** wybierz **aplikację Konsolową**.  
  
3. W **nazwa** wpisz nazwę opisową dla aplikacji konsoli, takie jak `MyTestConsole`.  
  
4. Kliknij przycisk **OK**.  
  
   Teraz musisz dodać niezbędne odwołania tak MyTestConsole może wywołać MyFirstVisualizer.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>Aby dodać niezbędne odwołania do MyTestConsole  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole** i wybierz polecenie **Dodaj odwołanie** w menu skrótów.  
  
2. W **Dodaj odwołanie** okno dialogowe **.NET** kartę, wybrać Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
3. Kliknij przycisk **OK**.  
  
4. Kliknij prawym przyciskiem myszy **MyTestConsole** i wybierz polecenie **Dodaj odwołanie** ponownie.  
  
5. W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **projektów** kartę, a następnie kliknij przycisk MyFirstVisualizer.  
  
6. Kliknij przycisk **OK**.  
  
   Teraz dodasz kod, aby zakończyć kontroler testów.  
  
#### <a name="to-add-code-to-mytestconsole"></a>Aby dodać kod do MyTestConsole  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik Program.cs i wybierz polecenie **Zmień nazwę** w menu skrótów.  
  
2. Edytuj nazwę z pliku Program.cs na bardziej opisową, takich jak TestConsole.cs.  
  
    **Uwaga** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmieni deklaracji klasy w TestConsole.cs, aby dopasować nazwę nowego pliku.  
  
3. W TestConsole.cs, Dodaj następujący kod do `using` instrukcji:  
  
   ```  
   using MyFirstVisualizer;  
   ```  
  
4. W metodzie `Main`, Dodaj następujący kod:  
  
   ```  
   String myString = "Hello, World";  
   DebuggerSide.TestShowVisualizer(myString);  
   ```  
  
   Teraz można przystąpić do testowania Twojego pierwszego wizualizatora.  
  
#### <a name="to-test-the-visualizer"></a>Aby przetestować Wizualizator  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyTestConsole** i wybierz polecenie **Ustaw jako projekt startowy** w menu skrótów.  
  
2. Na **debugowania** menu, wybierz **Start**.  
  
    Uruchamia aplikację konsolową i wizualizatora pojawi się i wyświetli ciąg "Hello, World".  
  
   Gratulacje. Mieć po prostu tworzone i testowane na Twoje pierwsze wizualizatora.  
  
   Aby korzystanie z wizualizatora w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zamiast po prostu wywoływanie z kontroler testów, należy go zainstalować. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="using-the-visualizer-item-template"></a>Za pomocą szablonu elementu wizualizatora  
 Do tej pory w tym przewodniku wykazało, należy jak ręcznie utworzyć wizualizatora. Zostało to zrobione ćwiczenia uczenia. Teraz, gdy wiesz, sposobu działania proste wizualizatora, jest łatwiejszy sposób, aby go utworzyć: za pomocą szablonu elementu wizualizatora.  
  
 Najpierw należy utworzyć nowy projekt biblioteki klas.  
  
#### <a name="to-create-a-new-class-library"></a>Aby utworzyć nową bibliotekę klas  
  
1. Na **pliku** menu, wybierz **Dodaj** a następnie kliknij przycisk **nowy projekt**.  
  
2. W **Dodaj nowy projekt** dialogowego **typu projektu**s, wybierz opcję **Visual C#**.  
  
3. W **szablony** wybierz **biblioteki klas**.  
  
4. W **nazwa** wpisz odpowiednią nazwę biblioteki klas, takie jak MySecondVisualizer.  
  
5. Kliknij przycisk **OK**.  
  
   Teraz można dodać elementu visualizer do niego:  
  
#### <a name="to-add-a-visualizer-item"></a>Aby dodać element wizualizatora  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy MySecondVisualizer.  
  
2. W menu skrótów wybierz **Dodaj** a następnie kliknij przycisk **nowy element**.  
  
3. W **Dodaj nowy element** dialogowego **szablony**, **zainstalowane szablony programu Visual Studio**, wybierz opcję **uproszczony Wizualizator debugowania**.  
  
4. W **nazwa** wpisz odpowiednią nazwę, takich jak SecondVisualizer.cs.  
  
5. Kliknij przycisk **Dodaj**.  
  
   To wszystko jest do niego. Przejrzyj plik SecondVisualizer.cs i przeglądać kod, który dodawane szablonu. Przejdź dalej i eksperymentować z kodem. Skoro znasz już podstawy, jesteś na dobrej drodze do utworzenia bardziej złożonych i przydatne wizualizatorów własne.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura wizualizatora](../debugger/visualizer-architecture.md)   
 [Porady: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)   
 [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md)




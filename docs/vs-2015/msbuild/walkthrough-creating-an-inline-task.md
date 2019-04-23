---
title: 'Przewodnik: Tworzenie zadania wbudowanego | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77f57eeda2f193170f4cd4f8b09d92989962e7fd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061596"
---
# <a name="walkthrough-creating-an-inline-task"></a>Przewodnik: Tworzenie zadania wbudowanego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadania programu MSBuild są zwykle tworzone przez skompilowanie klasy, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejsu. Począwszy od programu .NET Framework w wersji 4, można utworzyć zadania wbudowane w pliku projektu. Nie trzeba utworzyć osobny zestaw do obsługi zadań. Aby uzyskać więcej informacji, zobacz [zadania wbudowane](../msbuild/msbuild-inline-tasks.md).  
  
 W tym instruktażu pokazano, jak utworzyć i uruchomić te zadania wbudowane:  
  
- Zadanie, które nie ma danych wejściowych lub wyjściowych parametrów.  
  
- Zadanie, które ma jeden parametr wejściowy i bez parametrów wyjściowych.  
  
- Zadanie, które ma dwa parametry wejściowe i parametr jedno wyjście, który zwraca wartość właściwości programu MSBuild.  
  
- Zadanie, które ma dwa parametry wejściowe i parametr jedno wyjście, która zwraca elementu MSBuild.  
  
  Aby utworzyć i uruchomić zadania, należy użyć programu Visual Studio i **okno wiersza polecenia w usłudze Visual Studio**, wykonując następujące czynności:  
  
- Tworzenie pliku projektu programu MSBuild w programie Visual Studio.  
  
- Zmodyfikuj plik projektu w programie Visual Studio do tworzenie zadania wbudowanego.  
  
- Użyj **okna wiersza polecenia** do skompilowania projektu i sprawdź wyniki.  
  
## <a name="creating-and-modifying-an-msbuild-project"></a>Tworzenie i modyfikowanie projektu programu MSBuild  
 System projektu programu Visual Studio zależy od programu MSBuild. W związku z tym można utworzyć plik projektu kompilacji za pomocą programu Visual Studio. W tej sekcji utworzysz plik projektu języka Visual C#. (Możesz utworzyć plik projektu w języku Visual Basic. W kontekście tego samouczka różnica między plikami dwóch projektów jest niewielki.)  
  
#### <a name="to-create-and-modify-a-project-file"></a>Do tworzenia i modyfikowania pliku projektu  
  
1. W programie Visual Studio na **pliku** menu, kliknij przycisk **New** a następnie kliknij przycisk **projektu**.  
  
2. W **nowy projekt** okno dialogowe, wybierz opcję języka Visual C# typ projektu, a następnie wybierz **aplikacja interfejsu Windows Forms** szablonu. W **nazwa** wpisz `InlineTasks`. Wpisz **lokalizacji** dla rozwiązania, na przykład `D:\`. Upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone, **Dodaj do kontroli źródła** jest wyczyszczone, a **Nazwa rozwiązania** jest `InlineTasks`.  
  
     Kliknij przycisk **OK** do tworzenia pliku projektu.  
  
3. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu InlineTasks, a następnie kliknij przycisk **Zwolnij projekt**.  
  
4. Ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij przycisk **Edytuj InlineTasks.csproj**.  
  
     Plik projektu zostanie wyświetlony w edytorze kodu.  
  
## <a name="adding-a-basic-hello-task"></a>Dodawanie zadania podstawowe Hello  
 Teraz Dodaj do pliku projektu podstawowe zadania, która wyświetla komunikat "Hello, world!" Również dodać domyślny adres docelowy TestBuild do wywołania zadania.  
  
#### <a name="to-add-a-basic-hello-task"></a>Aby dodać zadanie hello podstawowe  
  
1. W katalogu głównym `Project` węzła, zmiana `DefaultTargets` atrybutu `TestBuild`. Wartość wynikowa `Project` węzła powinna przypominać przedstawioną w tym przykładzie:  
  
    `<Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">`  
  
2. Dodaj następujące zadania wbudowanego i obiektu docelowego do pliku projektu bezpośrednio przed elementem `</Project>` tagu.  
  
   ```  
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup />  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         Log.LogMessage("Hello, world!", MessageImportance.High);  
       </Code>  
     </Task>  
   </UsingTask>  
   <Target Name="TestBuild">  
     <Hello />  
   </Target>  
   ```  
  
3. Zapisz plik projektu.  
  
   Ten kod tworzy zadania wbudowanego nosi nazwę Witaj, która nie ma parametrów, odwołań, lub `Using` instrukcji. Zadanie Hello zawiera tylko jeden wiersz kodu, który wyświetla komunikat Witaj na urządzeniu rejestrowania domyślny, zazwyczaj w oknie konsoli.  
  
### <a name="running-the-hello-task"></a>Uruchamianie zadania Hello  
 Uruchom program MSBuild, używając **okna wiersza polecenia** do utworzenia zadania Hello i przetwarzania docelowy TestBuild, który ją wywołuje.  
  
##### <a name="to-run-the-hello-task"></a>Aby uruchomić zadanie Hello  
  
1. Kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, a następnie zlokalizuj **Visual Studio Tools** folder i kliknij przycisk **Visual Studio Command Prompt**.  
  
2. W **okna wiersza polecenia**, Znajdź folder, który zawiera plik projektu w tym przypadku D:\InlineTasks\InlineTasks\\.  
  
3. Typ **msbuild** bez przełączników polecenia, a następnie naciśnij klawisz ENTER. Domyślnie to tworzy plik InlineTasks.csproj i przetwarza domyślny element docelowy TestBuild, która wywołuje zadanie Hello.  
  
4. Sprawdź dane wyjściowe w **okna wiersza polecenia**. Powinien zostać wyświetlony ten wiersz:  
  
    `Hello, world!`  
  
   > [!NOTE]
   >  Jeśli nie widzisz wiadomości powitania, spróbuj ponownie zapisać w pliku projektu, a następnie uruchom zadanie Hello.  
  
   Przez przełączanie między Edytorem kodu a **okna wiersza polecenia**, można zmienić w pliku projektu i szybko wyświetlić wyniki.  
  
## <a name="defining-the-echo-task"></a>Definiowanie zadań Echo  
 Tworzenie zadania wbudowanego, który przyjmuje parametr ciąg i wyświetla ciąg w domyślnym, rejestrowania urządzenia.  
  
#### <a name="to-define-the-echo-task"></a>Aby zdefiniować zadania Echo  
  
1. W edytorze kodu Zastąp Hello zadań i TestBuild docelowych przy użyciu następującego kodu.  
  
   ```  
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <Text Required="true" />  
     </ParameterGroup>  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         Log.LogMessage(Text, MessageImportance.High);  
       </Code>  
     </Task>  
   </UsingTask>  
   <Target Name="TestBuild">  
     <Echo Text="Greetings!" />  
   </Target>  
   ```  
  
2. W **okna wiersza polecenia**, typ **msbuild** bez przełączników polecenia, a następnie naciśnij klawisz ENTER. Domyślnie to przetwarza domyślny element docelowy TestBuild, która wywołuje zadanie Echo.  
  
3. Sprawdź dane wyjściowe w **okna wiersza polecenia**. Powinien zostać wyświetlony ten wiersz:  
  
    `Greetings!`  
  
   Ten kod definiuje zadania wbudowanego nosi nazwę Echo, która ma tylko jeden parametr wejściowy wymagany tekst. Domyślnie parametry są typu System.String. Wartość parametru tekstu jest ustawiona podczas docelowy TestBuild wywołuje zadanie Echo.  
  
## <a name="defining-the-adder-task"></a>Definiowanie zadań Moduł dodający  
 Tworzenie zadania wbudowanego dodaje dwa parametry liczby całkowitej, który emituje ich suma jako właściwość narzędzia MSBuild.  
  
#### <a name="to-define-the-adder-task"></a>Aby zdefiniować Moduł dodający zadania  
  
1. W edytorze kodu Zastąp Echo zadań i TestBuild docelowych przy użyciu następującego kodu.  
  
   ```  
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <A ParameterType="System.Int32" Required="true" />  
       <B ParameterType="System.Int32" Required="true" />  
       <C ParameterType="System.Int32" Output="true" />  
     </ParameterGroup>  
     <Task>  
       <Code Type="Fragment" Language="cs">  
         C = A + B;  
       </Code>  
     </Task>  
   </UsingTask>    
   <Target Name="TestBuild">  
     <Adder A="4" B="5">  
       <Output PropertyName="Sum" TaskParameter="C" />  
     </Adder>  
     <Message Text="The sum is $(Sum)" Importance="High" />  
   </Target>  
   ```  
  
2. W **okna wiersza polecenia**, typ **msbuild** bez przełączników polecenia, a następnie naciśnij klawisz ENTER. Domyślnie to przetwarza domyślny element docelowy TestBuild, która wywołuje zadanie Echo.  
  
3. Sprawdź dane wyjściowe w **okna wiersza polecenia**. Powinien zostać wyświetlony ten wiersz:  
  
    `The sum is 9`  
  
   Ten kod definiuje zadania wbudowanego, który nosi nazwę Moduł dodający, ma dwa wymagane parametry wejściowe liczba całkowita, A i B, i jeden argument dane wyjściowe parametru-C. Zadanie Moduł dodający dodaje dwa parametry wejściowe i zwraca sumę w parametr wyjściowy. Suma jest emitowany jako właściwość MSBuild `Sum`. Wartości parametrów wejściowych są ustawione, gdy docelowy TestBuild wywołuje zadanie Moduł dodający.  
  
## <a name="defining-the-regx-task"></a>Definiowanie zadań RegX  
 Tworzenie zadania wbudowanego, który akceptuje grupy elementów, jak i wyrażenia regularnego i zwraca listę wszystkich elementów, które mają zawartość, która odpowiada wyrażeniu.  
  
#### <a name="to-define-the-regx-task"></a>Aby zdefiniować zadania RegX  
  
1. W edytorze kodu Zastąp Moduł dodający zadań i TestBuild docelowych przy użyciu następującego kodu.  
  
   ```  
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
     <ParameterGroup>  
       <Expression Required="true" />  
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />  
     </ParameterGroup>  
     <Task>  
       <Using Namespace="System.Text.RegularExpressions"/>  
       <Code Type="Fragment" Language="cs">  
   <![CDATA[  
         if (Files.Length > 0)  
         {  
           Result = new TaskItem[Files.Length];  
           for (int i = 0; i < Files.Length; i++)  
           {  
             ITaskItem item = Files[i];  
             string path = item.GetMetadata("FullPath");  
             using(StreamReader rdr = File.OpenText(path))  
             {  
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)  
               {  
                 Result[i] = new TaskItem(item.ItemSpec);  
               }  
             }  
           }  
         }  
   ]]>  
       </Code>  
     </Task>  
   </UsingTask>    
   <Target Name="TestBuild">  
     <RegX Expression="public|protected" Files="@(Compile)">  
       <Output ItemName="MatchedFiles" TaskParameter="Result" />  
     </RegX>  
     <Message Text="Input files: @(Compile)" Importance="High" />  
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />  
   </Target>  
   ```  
  
2. W **okna wiersza polecenia**, typ **msbuild** bez przełączników polecenia, a następnie naciśnij klawisz ENTER. Domyślnie to przetwarza domyślny element docelowy TestBuild, która wywołuje zadanie RegX.  
  
3. Sprawdź dane wyjściowe w **okna wiersza polecenia**. Powinny zostać wyświetlone następujące wiersze:  
  
    `Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs`  
  
    `Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs`  
  
   Ten kod definiuje zadania wbudowanego nosi nazwę RegX, która ma trzy następujące parametry:  
  
- `Expression` jest wymagany ciąg. parametr wejściowy, którego wartość jest wyrażenia regularnego do dopasowania. W tym przykładzie wyrażenie dopasowuje słowa "public" lub "protected".  
  
- `Files` jest wymagany element listy parametr wejściowy, który ma wartość, która znajduje się lista plików, które mają być wyszukiwane dopasowanie. W tym przykładzie `Files` ustawiono `Compile` elementu, który zawiera pliki źródłowe projektu.  
  
- `Result` to parametr wyjściowy, który ma wartość, która znajduje się lista plików, które mają zawartość, która odpowiada wyrażeniu regularnemu.  
  
  Wartości parametrów wejściowych są ustawione, gdy element docelowy TestBuild wywołuje zadanie RegX. Zadanie RegX odczytuje każdy plik i zwraca listę wszystkich plików, które odpowiada wyrażeniu regularnemu. Ta lista jest zwracana jako `Result` parametr wyjściowy, który jest emitowany jako element MSBuild `MatchedFiles`.  
  
### <a name="handling-reserved-characters"></a>Obsługa zastrzeżone znaki  
 Analizator MSBuild przetwarza zadania wbudowane jako XML. Znaki, które mają zastrzeżone znaczenie w formacie XML, na przykład "\<" i ">", są wykrywane oraz obsługiwane tak, jakby były one XML, a nie kod źródłowy platformy .NET. W poszukiwaniu zastrzeżonych znaków w wyrażeniach kodu, takich jak `Files.Length > 0`, zapis `Code` element, aby jej zawartość są zawarte w wyrażeniu CDATA w następujący sposób:  
  
 `<Code Type="Fragment" Language="cs">`  
  
 `<![CDATA[`  
  
 `// Your code goes here.`  
  
 `]]>`  
  
 `</Code>`  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Docelowe elementy](../msbuild/msbuild-targets.md)

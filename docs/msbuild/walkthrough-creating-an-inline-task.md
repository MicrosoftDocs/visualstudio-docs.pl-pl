---
title: 'Instruktaż: Tworzenie zadania wbudowanego | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70ce19a6dcd9c61b0e14d0d88c52072f59f87fb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631162"
---
# <a name="walkthrough-create-an-inline-task"></a>Instruktaż: Tworzenie zadania wbudowanego

Zadania MSBuild są zazwyczaj tworzone przez kompilowanie <xref:Microsoft.Build.Framework.ITask> klasy, która implementuje interfejs. Począwszy od programu .NET Framework w wersji 4, można tworzyć zadania wkolejce pliku projektu. Nie trzeba tworzyć oddzielny zestaw do obsługi zadania. Aby uzyskać więcej informacji, zobacz [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md).

 W tym przewodniku pokazano, jak utworzyć i uruchomić te zadania wbudowane:

- Zadanie, które nie ma parametrów wejściowych lub wyjściowych.

- Zadanie, które ma jeden parametr wejściowy i nie ma parametrów wyjściowych.

- Zadanie, które ma dwa parametry wejściowe i jeden parametr wyjściowy, który zwraca właściwość MSBuild.

- Zadanie, które ma dwa parametry wejściowe i jeden parametr wyjściowy, który zwraca element MSBuild.

Aby utworzyć i uruchomić zadania, użyj programu Visual Studio i **okna wiersza polecenia programu Visual Studio**w następujący sposób:

1. Utwórz plik projektu MSBuild przy użyciu programu Visual Studio.

2. Zmodyfikuj plik projektu w programie Visual Studio, aby utworzyć zadanie wbudowane.

3. Użyj **okna wiersza polecenia,** aby utworzyć projekt i sprawdzić wyniki.

## <a name="create-and-modify-an-msbuild-project"></a>Tworzenie i modyfikowanie projektu MSBuild

 System projektu programu Visual Studio jest oparty na msbuild. W związku z tym można utworzyć plik projektu kompilacji przy użyciu programu Visual Studio. W tej sekcji należy utworzyć plik projektu języka Visual C#. (Zamiast tego można utworzyć plik projektu języka Visual Basic. W kontekście tego samouczka różnica między dwoma plikami projektu jest niewielka.)

#### <a name="to-create-and-modify-a-project-file"></a>Aby utworzyć i zmodyfikować plik projektu

1. W programie Visual Studio utwórz nowy projekt przy użyciu szablonu **aplikacji formularzy windows** w języku C#. W polu **Nazwa** wpisz `InlineTasks`. Wpisz **lokalizację** dla rozwiązania, na przykład *D:\\*. Upewnij się, że wybrano opcję **Utwórz katalog dla rozwiązania,** opcja **Dodaj do źródła jest** wyczyszczona, a nazwa **rozwiązania** to **Zadania wbudowane**.

3. Kliknij **przycisk OK,** aby utworzyć plik projektu.

3. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **InlineTasks,** a następnie kliknij polecenie **Zwolnij projekt**.

4. Kliknij prawym przyciskiem myszy węzeł projektu ponownie, a następnie kliknij polecenie **Edytuj inlinetasks.csproj**.

     Plik projektu pojawi się w edytorze kodu.

## <a name="add-a-basic-hello-task"></a>Dodawanie podstawowego zadania Hello

 Teraz dodaj do pliku projektu podstawowe zadanie, które wyświetla komunikat "Hello, world!" Również dodać domyślny testbuild docelowe do wywołania zadania.

#### <a name="to-add-a-basic-hello-task"></a>Aby dodać podstawowe zadanie Hello

1. W węźle `Project` głównym `DefaultTargets` zmień `TestBuild`atrybut na . Wynikowy `Project` węzeł powinien przypominać ten przykład:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Dodaj następujące zadanie wbudowane i obiekt docelowy `</Project>` do pliku projektu tuż przed tagiem.

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. Zapisz plik projektu.

   Ten kod tworzy wbudowane zadanie o nazwie Hello i nie `Using` ma parametrów, odwołań ani dyrektyw. Hello zadanie zawiera tylko jeden wiersz kodu, który wyświetla komunikat powitania na domyślnym urządzeniu rejestrującym, zazwyczaj w oknie konsoli.

### <a name="run-the-hello-task"></a>Uruchamianie zadania Hello

 Uruchom MSBuild za pomocą **okna wiersza polecenia** do konstruowania Hello zadanie i do przetwarzania TestBuild miejsce docelowe, który wywołuje go.

##### <a name="to-run-the-hello-task"></a>Aby uruchomić zadanie Hello

1. Kliknij **przycisk Start**, kliknij pozycję Wszystkie **programy**, a następnie znajdź folder Narzędzia programu **Visual Studio** i kliknij pozycję Wiersz polecenia programu Visual **Studio**.

2. W **oknie wiersza polecenia**znajdź folder zawierający plik projektu, w tym przypadku *\\D:\InlineTasks\InlineTasks*.

3. Wpisz **msbuild** bez przełączników poleceń, a następnie naciśnij **klawisz Enter**. Domyślnie ten tworzy plik *InlineTasks.csproj* i przetwarza domyślny docelowy TestBuild, który wywołuje hello zadanie.

4. Sprawdź dane wyjściowe w **oknie wiersza polecenia**. Powinieneś zobaczyć ten wiersz:

    `Hello, world!`

   > [!NOTE]
   > Jeśli nie widzisz komunikatu powitania, spróbuj ponownie zapisać plik projektu, a następnie uruchom zadanie Hello.

   Zmieniając edytor kodu i okno **wiersza polecenia,** można zmienić plik projektu i szybko wyświetlić wyniki.

## <a name="define-the-echo-task"></a>Zdefiniuj zadanie Echo

 Utwórz zadanie wbudowane, które akceptuje parametr ciągu i wyświetla ciąg na domyślnym urządzeniu rejestrującym.

#### <a name="to-define-the-echo-task"></a>Aby zdefiniować zadanie Echo

1. W edytorze kodu zastąp Hello task i TestBuild target przy użyciu następującego kodu.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. W **oknie wiersza polecenia**wpisz **msbuild** bez przełączników poleceń, a następnie naciśnij klawisz **Enter**. Domyślnie powoduje to procesy domyślnego docelowego TestBuild, który wywołuje zadanie Echo.

3. Sprawdź dane wyjściowe w **oknie wiersza polecenia**. Powinieneś zobaczyć ten wiersz:

    `Greetings!`

   Ten kod definiuje wbudowane zadanie o nazwie Echo i ma tylko jeden wymagany parametr wejściowy Text. Domyślnie parametry są typu System.String. Wartość Text parametr jest ustawiany, gdy TestBuild cel wywołuje echo zadania.

## <a name="define-the-adder-task"></a>Definiowanie zadania Adder

 Utwórz zadanie wbudowane, które dodaje dwa parametry całkowite i emituje ich sumę jako właściwość MSBuild.

#### <a name="to-define-the-adder-task"></a>Aby zdefiniować zadanie Adder

1. W edytorze kodu zastąp zadanie Echo i TestBuild target przy użyciu następującego kodu.

   ```xml
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

2. W **oknie wiersza polecenia**wpisz **msbuild** bez przełączników poleceń, a następnie naciśnij klawisz **Enter**. Domyślnie powoduje to procesy domyślnego docelowego TestBuild, który wywołuje zadanie Echo.

3. Sprawdź dane wyjściowe w **oknie wiersza polecenia**. Powinieneś zobaczyć ten wiersz:

    `The sum is 9`

   Ten kod definiuje zadanie wbudowane o nazwie Adder i ma dwa wymagane parametry wejściowe liczby całkowitej, A i B oraz jeden parametr wyjściowy liczby całkowitej, C. Zadanie Adder dodaje dwa parametry wejściowe i zwraca sumę w parametrze wyjściowym. Suma jest emitowana jako właściwość `Sum`MSBuild . Wartości parametrów wejściowych są ustawiane, gdy testbuild cel wywołuje zadanie Adder.

## <a name="define-the-regx-task"></a>Definiowanie zadania RegX

 Utwórz zadanie wbudowane, które akceptuje grupę elementów i wyrażenie regularne, i zwraca listę wszystkich elementów, które mają zawartość pliku, która pasuje do wyrażenia.

#### <a name="to-define-the-regx-task"></a>Aby zdefiniować zadanie RegX

1. W edytorze kodu zastąp zadanie Adder i TestBuild miejsce docelowe przy użyciu następującego kodu.

   ```xml
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

2. W **oknie wiersza polecenia**wpisz **msbuild** bez przełączników poleceń, a następnie naciśnij klawisz **Enter**. Domyślnie powoduje to procesy domyślnego docelowego TestBuild, który wywołuje zadanie RegX.

3. Sprawdź dane wyjściowe w **oknie wiersza polecenia**. Powinny być widoczne następujące wiersze:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Ten kod definiuje zadanie wbudowane o nazwie RegX i ma te trzy parametry:

- `Expression`jest wymaganym parametrem wejściowym ciągu, który ma wartość, która jest wyrażeniem regularnym, które ma być dopasowane. W tym przykładzie wyrażenie pasuje do słów "public" lub "protected".

- `Files`jest wymaganym parametrem wejściowym listy elementów, który ma wartość, która jest listą plików, które mają być wyszukiwane dla dopasowania. W tym `Files` przykładzie jest `Compile` ustawiona na element, który zawiera listę plików źródłowych projektu.

- `Result`jest parametrem wyjściowym, który ma wartość, która jest lista plików, które mają zawartość, która pasuje do wyrażenia regularnego.

  Wartość parametrów wejściowych są ustawiane, gdy TestBuild cel wywołuje zadanie RegX. Zadanie RegX odczytuje każdy plik i zwraca listę plików, które pasują do wyrażenia regularnego. Ta lista jest `Result` zwracana jako parametr wyjściowy, który jest `MatchedFiles`emitowany jako element MSBuild .

### <a name="handle-reserved-characters"></a>Obsługa znaków zastrzeżonych

 Analizator analizatora MSBuild przetwarza zadania wbudowane jako XML. Znaki, które mają zarezerwowane znaczenie w\<XML, na przykład " " i ">", są wykrywane i obsługiwane tak, jakby były XML, a nie kod źródłowy .NET. Aby uwzględnić znaki zastrzeżone w `Files.Length > 0`wyrażeniach `Code` kodu, takich jak , napisz element, tak aby jego zawartość była zawarta w wyrażeniu CDATA, w następujący sposób:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  // Your code goes here.

  ]]>
</Code>
```

## <a name="see-also"></a>Zobacz też

- [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Cele](../msbuild/msbuild-targets.md)

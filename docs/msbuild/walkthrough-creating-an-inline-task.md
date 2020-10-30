---
title: 'Przewodnik: Tworzenie zadania wbudowanego | Microsoft Docs'
description: Zapoznaj się z tematem Tworzenie zadania programu MSBuild w pliku projektu, bez konieczności tworzenia oddzielnego zestawu do hostowania zadania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d2d72745aebedb5dad5efc86d33804a51e36b762
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046634"
---
# <a name="walkthrough-create-an-inline-task"></a>Przewodnik: Tworzenie zadania wbudowanego

Zadania programu MSBuild są zwykle tworzone przez skompilowanie klasy, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs. Począwszy od .NET Framework w wersji 4, można tworzyć zadania w tekście w pliku projektu. Nie trzeba tworzyć oddzielnego zestawu, aby hostować zadanie. Aby uzyskać więcej informacji, zobacz [zadania wbudowane](../msbuild/msbuild-inline-tasks.md).

 W tym instruktażu pokazano, jak tworzyć i uruchamiać te zadania wbudowane:

- Zadanie, które nie ma parametrów wejściowych lub wyjściowych.

- Zadanie, które ma jeden parametr wejściowy i bez parametrów wyjściowych.

- Zadanie, które ma dwa parametry wejściowe i jeden parametr wyjściowy, który zwraca właściwość programu MSBuild.

- Zadanie, które ma dwa parametry wejściowe i jeden parametr wyjściowy, który zwraca element MSBuild.

Aby utworzyć i uruchomić zadania, użyj programu Visual Studio i **okna wiersza polecenia programu Visual Studio** w następujący sposób:

1. Utwórz plik projektu MSBuild przy użyciu programu Visual Studio.

2. Zmodyfikuj plik projektu w programie Visual Studio, aby utworzyć zadanie wbudowane.

3. Użyj **okna wiersza polecenia** , aby skompilować projekt i przeanalizować wyniki.

## <a name="create-and-modify-an-msbuild-project"></a>Tworzenie i modyfikowanie projektu MSBuild

 System projektu programu Visual Studio jest oparty na programie MSBuild. W związku z tym można utworzyć plik projektu kompilacji przy użyciu programu Visual Studio. W tej sekcji utworzysz plik projektu Visual C#. (Zamiast tego można utworzyć plik projektu Visual Basic. W kontekście tego samouczka różnica między dwoma plikami projektu jest niewielka.)

#### <a name="to-create-and-modify-a-project-file"></a>Aby utworzyć i zmodyfikować plik projektu

1. W programie Visual Studio Utwórz nowy projekt za pomocą szablonu **aplikacji Windows Forms** C#. W polu **Nazwa** wpisz `InlineTasks`. Wpisz **lokalizację** rozwiązania, na przykład *D: \\* . Upewnij się, że wybrano opcję **Utwórz katalog dla rozwiązania** , pole wyboru **Dodaj do kontroli źródła** jest wyczyszczone, a **Nazwa rozwiązania** to **InlineTasks** .

3. Kliknij przycisk **OK** , aby utworzyć plik projektu.

3. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu **InlineTasks** , a następnie kliknij pozycję **Zwolnij projekt** .

4. Ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij polecenie **Edytuj InlineTasks. csproj** .

     Plik projektu pojawi się w edytorze kodu.

## <a name="add-a-basic-hello-task"></a>Dodaj podstawowe zadanie powitania

 Teraz Dodaj do pliku projektu podstawowe zadanie, które wyświetla komunikat "Hello, World!" Dodaj również domyślny obiekt docelowy TestBuild, aby wywołać zadanie.

#### <a name="to-add-a-basic-hello-task"></a>Aby dodać podstawowe zadanie powitania

1. W węźle głównym `Project` Zmień `DefaultTargets` atrybut na `TestBuild` . Węzeł w efekcie `Project` powinien wyglądać podobnie do tego przykładu:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Dodaj następujące zadanie wbudowane i element docelowy do pliku projektu tuż przed `</Project>` tagiem.

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

   Ten kod tworzy zadanie wbudowane o nazwie Hello i nie ma parametrów, odwołań ani `Using` dyrektyw. Zadanie Hello zawiera tylko jeden wiersz kodu, który wyświetla komunikat powitalny na domyślnym urządzeniu rejestrowania, zazwyczaj okno konsoli.

### <a name="run-the-hello-task"></a>Uruchamianie zadania powitania

 Uruchom program MSBuild przy użyciu **okna wiersza polecenia** , aby skonstruować zadanie powitania i przetworzyć obiekt docelowy TestBuild, który go wywołuje.

##### <a name="to-run-the-hello-task"></a>Aby uruchomić zadanie powitania

1. Kliknij przycisk **Start** , kliknij pozycję **Wszystkie programy** , a następnie znajdź folder **Visual Studio Tools** i kliknij pozycję **wiersz polecenia programu Visual Studio** .

2. W **oknie wiersza polecenia** Znajdź folder zawierający plik projektu, w tym przypadku *\\ D:\InlineTasks\InlineTasks* .

3. Wpisz **MSBuild** bez przełączników polecenia, a następnie naciśnij klawisz **Enter** . Domyślnie program tworzy plik *InlineTasks. csproj* i przetwarza domyślny element docelowy TestBuild, który wywołuje zadanie powitania.

4. Sprawdzanie danych wyjściowych w **oknie wiersza polecenia** . Powinien zostać wyświetlony następujący wiersz:

    `Hello, world!`

   > [!NOTE]
   > Jeśli komunikat powitania nie jest widoczny, spróbuj ponownie zapisać plik projektu, a następnie uruchom zadanie powitania.

   Przez przemienne między edytorem kodu a **oknem wiersza polecenia** można zmienić plik projektu i szybko zobaczyć wyniki.

## <a name="define-the-echo-task"></a>Definiowanie zadania echo

 Utwórz zadanie wbudowane, które przyjmuje parametr String i wyświetla ciąg na domyślnym urządzeniu rejestrowania.

#### <a name="to-define-the-echo-task"></a>Aby zdefiniować zadanie echo

1. W edytorze kodu Zastąp zadanie Hello i element docelowy TestBuild przy użyciu następującego kodu.

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

2. W **oknie wiersza polecenia** wpisz **MSBuild** bez przełączników polecenia, a następnie naciśnij klawisz **Enter** . Domyślnie powoduje to przetwarzanie domyślnego TestBuild docelowego, który wywołuje zadanie echo.

3. Sprawdzanie danych wyjściowych w **oknie wiersza polecenia** . Powinien zostać wyświetlony następujący wiersz:

    `Greetings!`

   Ten kod definiuje zadanie wbudowane o nazwie echo i ma tylko jeden wymagany tekst parametru wejściowego. Domyślnie parametry są typu System. String. Wartość parametru tekstowego jest ustawiana, gdy obiekt docelowy TestBuild wywołuje zadanie echo.

## <a name="define-the-adder-task"></a>Definiowanie zadania dodającego

 Utwórz zadanie wbudowane, które dodaje dwa parametry całkowite i emituje ich sumę jako właściwość programu MSBuild.

#### <a name="to-define-the-adder-task"></a>Aby zdefiniować zadanie dodające

1. W edytorze kodu Zastąp zadanie echo i element docelowy TestBuild przy użyciu następującego kodu.

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

2. W **oknie wiersza polecenia** wpisz **MSBuild** bez przełączników polecenia, a następnie naciśnij klawisz **Enter** . Domyślnie powoduje to przetwarzanie domyślnego TestBuild docelowego, który wywołuje zadanie echo.

3. Sprawdzanie danych wyjściowych w **oknie wiersza polecenia** . Powinien zostać wyświetlony następujący wiersz:

    `The sum is 9`

   Ten kod definiuje zadanie wbudowane o nazwie dodające i ma dwa wymagane parametry wejściowe Integer, a i B oraz jeden parametr wyjściowy Integer, C. Zadanie dodające dodaje dwa parametry wejściowe i zwraca sumę w parametrze danych wyjściowych. Suma jest emitowana jako właściwość programu MSBuild `Sum` . Wartości parametrów wejściowych są ustawiane, gdy obiekt docelowy TestBuild wywołuje zadanie dodające.

## <a name="define-the-regx-task"></a>Definiowanie zadania RegX

 Utwórz zadanie wbudowane, które akceptuje grupę elementów i wyrażenie regularne i zwraca listę wszystkich elementów, które mają zawartość pliku zgodną z wyrażeniem.

#### <a name="to-define-the-regx-task"></a>Aby zdefiniować zadanie RegX

1. W edytorze kodu Zastąp zadanie dodającego i element docelowy TestBuild przy użyciu następującego kodu.

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

2. W **oknie wiersza polecenia** wpisz **MSBuild** bez przełączników polecenia, a następnie naciśnij klawisz **Enter** . Domyślnie powoduje to przetwarzanie domyślnego TestBuild docelowego, który wywołuje zadanie RegX.

3. Sprawdzanie danych wyjściowych w **oknie wiersza polecenia** . Powinny zostać wyświetlone następujące wiersze:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Ten kod definiuje zadanie wbudowane o nazwie RegX i ma trzy parametry:

- `Expression` jest wymaganym parametrem wejściowym ciągu, który ma wartość, która jest wyrażeniem regularnym do dopasowania. W tym przykładzie wyrażenie pasuje do wyrazów "Public" lub "Protected".

- `Files` jest parametrem wejściowym listy wymaganych elementów, który ma wartość, która jest listą plików, które mają być wyszukiwane dla dopasowania. W tym przykładzie `Files` jest ustawiony na `Compile` element, który zawiera listę źródłowych plików projektu.

- `Result` jest parametrem wyjściowym, który ma wartość, która jest listą plików, które pasują do wyrażenia regularnego.

  Wartość parametrów wejściowych ustawia się, gdy obiekt docelowy TestBuild wywołuje zadanie RegX. Zadanie RegX odczytuje każdy plik i zwraca listę plików, które pasują do wyrażenia regularnego. Ta lista jest zwracana jako `Result` parametr wyjściowy, który jest emitowany jako element MSBuild `MatchedFiles` .

### <a name="handle-reserved-characters"></a>Obsługa znaków zarezerwowanych

 Analizator MSBuild przetwarza zadania wbudowane jako XML. Znaki, które mają zarezerwowane znaczenie w formacie XML, na przykład " \<" and "> ", są wykrywane i obsługiwane tak, jakby były XML, a nie kodem źródłowym platformy .NET. Aby uwzględnić zastrzeżone znaki w wyrażeniach kodu, takich jak `Files.Length > 0` , napisz `Code` element tak, aby jego zawartość znajdowała się w wyrażeniu CDATA, w następujący sposób:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  if (Files.Length > 0)
  {
      // Your code goes here.
  }
  ]]>
</Code>
```

## <a name="see-also"></a>Zobacz też

- [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)

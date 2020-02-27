---
title: Zadania wbudowane programu MSBuild z RoslynCodeTaskFactory | Microsoft Docs
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ead738042b15c955aadb458c527253f3759b934e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633229"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Zadania wbudowane programu MSBuild z RoslynCodeTaskFactory

Podobnie jak w przypadku [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory używa międzyplatformowych kompilatorów Roslyn do generowania zestawów zadań w pamięci do użycia jako zadania wbudowane.  .NET Standard obiektów docelowych zadań RoslynCodeTaskFactory i może współdziałać z .NET Framework i środowiska uruchomieniowe platformy .NET Core, a także z innymi platformami, takimi jak Linux i Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory jest dostępna tylko w programie MSBuild 15,8 i nowszych.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Struktura zadania śródwierszowego z RoslynCodeTaskFactory

 RoslynCodeTaskFactory wbudowane zadania są deklarowane w taki sam sposób jak [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), jedyną różnicą jest to, że docelowe .NET Standard.  Zadanie śródwierszowe i element `UsingTask`, który go zawiera, są zwykle zawarte w pliku *. targets* i importowane do innych plików projektu zgodnie z wymaganiami. Oto podstawowe zadanie wbudowane. Należy zauważyć, że nic nie robi.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 Element `UsingTask` w przykładzie ma trzy atrybuty opisujące zadanie i wbudowaną fabrykę zadań, która kompiluje go.

- `TaskName` atrybutu nazywa zadanie, w tym przypadku `DoNothing`.

- Atrybut `TaskFactory` nazywa klasę implementującą wewnętrzną fabrykę zadań.

- Atrybut `AssemblyFile` zawiera lokalizację wewnętrznej fabryki zadań. Alternatywnie, można użyć atrybutu `AssemblyName`, aby określić w pełni kwalifikowaną nazwę wbudowanej klasy fabryki zadań, która zwykle znajduje się w globalnej pamięci podręcznej zestawów (GAC).

Pozostałe elementy zadania `DoNothing` są puste i są dostarczane w celu zilustrowania kolejności i struktury zadania wbudowanego. Bardziej niezawodny przykład został przedstawiony w dalszej części tego tematu.

- Element `ParameterGroup` jest opcjonalny. Gdy jest określony, deklaruje parametry zadania. Aby uzyskać więcej informacji na temat parametrów wejściowych i wyjściowych, zobacz [Parametry wejściowe i wyjściowe](#input-and-output-parameters) w dalszej części tego tematu.

- Element `Task` opisuje i zawiera kod źródłowy zadania.

- Element `Reference` określa odwołania do zestawów .NET, które są używane w kodzie. Jest to równoznaczne z dodaniem odwołania do projektu w programie Visual Studio. Atrybut `Include` określa ścieżkę do przywoływanego zestawu.

- Element `Using` wyświetla listę przestrzeni nazw, do których chcesz uzyskać dostęp. Jest to podobne do instrukcji `Using` w wizualizacji C#. Atrybut `Namespace` określa przestrzeń nazw do uwzględnienia.

elementy `Reference` i `Using` to Language-niezależny od. Zadania wbudowane można napisać w jednym z obsługiwanych języków języka .NET CodeDom, na przykład Visual Basic lub wizualizacji C#.

> [!NOTE]
> Elementy zawarte w elemencie `Task` są specyficzne dla fabryki zadań, w tym przypadku w fabryce zadań Code.

### <a name="code-element"></a>Element Code

Ostatni element podrzędny, który ma być wyświetlany w elemencie `Task`, to `Code` elementu. Element `Code` zawiera lub lokalizuje kod, który chcesz skompilować do zadania. Elementy `Code` są zależne od tego, jak chcesz napisać zadanie.

Atrybut `Language` określa język, w którym napisano kod. Dopuszczalne wartości to `cs` dla C#`vb` Visual Basic.

Atrybut `Type` określa typ kodu, który znajduje się w elemencie `Code`.

- Jeśli wartość `Type` jest `Class`, element `Code` zawiera kod dla klasy, która pochodzi od interfejsu <xref:Microsoft.Build.Framework.ITask>.

- Jeśli wartość `Type` jest `Method`, kod definiuje przesłonięcie metody `Execute` interfejsu <xref:Microsoft.Build.Framework.ITask>.

- Jeśli wartość `Type` jest `Fragment`, kod definiuje zawartość metody `Execute`, ale nie sygnaturę lub `return` instrukcji.

Sam kod jest zwykle wyświetlany między znacznikiem `<![CDATA[` i znacznikiem `]]>`. Ponieważ kod znajduje się w sekcji CDATA, nie trzeba martwić się o znak ucieczki, na przykład "\<" lub ">".

Alternatywnie, można użyć atrybutu `Source` elementu `Code`, aby określić lokalizację pliku zawierającego kod zadania. Kod w pliku źródłowym musi być typu, który jest określony przez atrybut `Type`. Jeśli atrybut `Source` jest obecny, wartość domyślna `Type` jest `Class`. Jeśli `Source` nie istnieje, wartość domyślna to `Fragment`.

> [!NOTE]
> Podczas definiowania klasy zadań w pliku źródłowym, nazwa klasy musi zgadzać się z atrybutem `TaskName` odpowiadającego elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) .

## <a name="hello-world"></a>Witaj, świecie

 Oto bardziej niezawodne zadanie wbudowane z RoslynCodeTaskFactory. Zadanie HelloWorld wyświetla "Hello, World!" na domyślnym urządzeniu rejestrowania błędów, które jest zazwyczaj konsolą systemową lub oknem **danych wyjściowych** programu Visual Studio. Element `Reference` w przykładzie jest uwzględniany tylko w przypadku ilustracji.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

Zadanie HelloWorld można zapisać w pliku o nazwie *HelloWorld. targets*, a następnie wywołać go z projektu w następujący sposób.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Parametry wejściowe i wyjściowe

 Wbudowane parametry zadania są elementami podrzędnymi elementu `ParameterGroup`. Każdy parametr przyjmuje nazwę elementu, który go definiuje. Poniższy kod definiuje `Text`parametru.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametry mogą mieć jeden lub więcej z następujących atrybutów:

- `Required` jest opcjonalnym atrybutem, który jest `false` domyślnie. Jeśli `true`, to parametr jest wymagany i musi mieć określoną wartość przed wywołaniem zadania.

- `ParameterType` jest opcjonalnym atrybutem, który jest `System.String` domyślnie. Może być ustawiony na dowolny w pełni kwalifikowany typ, który jest elementem lub wartością, którą można przekonwertować na i z ciągu przy użyciu System. Convert. ChangeType. (Innymi słowy każdy typ, który może być przekazywać do i z zewnętrznego zadania).

- `Output` jest opcjonalnym atrybutem, który jest `false` domyślnie. Jeśli `true`, wówczas parametr musi mieć wartość przed powrotem z metody Execute.

Na przykład:

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

definiuje te trzy parametry:

- `Expression` jest wymaganym parametrem wejściowym typu System. String.

- `Files` jest parametrem wejściowym listy wymaganych elementów.

- `Tally` jest parametrem wyjściowym typu System. Int32.

Jeśli element `Code` ma atrybut `Type` `Fragment` lub `Method`, wówczas właściwości są tworzone automatycznie dla każdego parametru. W przeciwnym razie właściwości muszą być jawnie zadeklarowane w kodzie źródłowym zadania i muszą dokładnie pasować do ich definicji parametrów.

## <a name="example"></a>Przykład

 Następujące zadanie wbudowane rejestruje niektóre komunikaty i zwraca ciąg.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

Te zadania wbudowane mogą łączyć ścieżki i uzyskać nazwę pliku.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Przewodnik: Tworzenie zadania wbudowanego](../msbuild/walkthrough-creating-an-inline-task.md)

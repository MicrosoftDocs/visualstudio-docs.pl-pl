---
title: Zadania wbudowane MSBuild z RoslynCodeTaskFactory | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 658302de187d6bbeab67dedaaa816709f00436ed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865378"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Zadania wbudowane MSBuild z RoslynCodeTaskFactory

Podobnie jak [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory używa kompilatorów Roslyn między platformami do generowania zestawów zadań w pamięci do użycia jako zadania wbudowane.  Zadania RoslynCodeTaskFactory są przeznaczone dla platformy .NET Standard i mogą pracować w środowiskach uruchomieniowych platformy .NET Framework i .NET Core, a także w innych platformach, takich jak Linux i Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory jest dostępny tylko w standardzie MSBuild 15.8 i powyżej. Wersje MSBuild są zgodne z wersjami programu Visual Studio, więc RoslynCodeTaskFactory jest dostępny w programie Visual Studio 15.8 lub nowszym.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Struktura zadania wbudowanego z RoslynCodeTaskFactory

 RoslynCodeTaskFactory wbudowane zadania są deklarowane w identyczny sposób jako [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), jedyną różnicą jest to, że są one ukierunkowane .NET Standard.  Zadanie wbudowane i `UsingTask` element, który go zawiera, są zazwyczaj zawarte w pliku *.targets* i importowane do innych plików projektu zgodnie z wymaganiami. Oto podstawowe zadanie wbudowane. Zauważ, że nic nie robi.

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

 Element `UsingTask` w przykładzie ma trzy atrybuty, które opisują zadanie i wbudowanej fabryki zadań, która kompiluje go.

- Atrybut `TaskName` nazywa zadanie, w tym `DoNothing`przypadku .

- Atrybut `TaskFactory` nazywa klasę, która implementuje wbudowaną fabrykę zadań.

- Atrybut `AssemblyFile` podaje lokalizację wbudowanej fabryki zadań. Alternatywnie można użyć `AssemblyName` atrybutu, aby określić w pełni kwalifikowaną nazwę wbudowanej klasy fabryki zadań, która zazwyczaj znajduje się w globalnej pamięci podręcznej zestawów (GAC).

Pozostałe elementy `DoNothing` zadania są puste i są dostarczane w celu zilustrowania kolejności i struktury zadania wbudowanego. Bardziej niezawodny przykład przedstawiono w dalszej części tego tematu.

- Element `ParameterGroup` jest opcjonalny. Po określeniu deklaruje parametry dla zadania. Aby uzyskać więcej informacji na temat parametrów wejściowych i wyjściowych, zobacz [parametry wejściowe i wyjściowe](#input-and-output-parameters) w dalszej części tego tematu.

- Element `Task` opisuje i zawiera kod źródłowy zadania.

- Element `Reference` określa odwołania do zestawów .NET, które są używane w kodzie. Jest to równoważne dodanie odwołania do projektu w programie Visual Studio. Atrybut `Include` określa ścieżkę zestawu, do którego istnieje odwołanie.

- Element `Using` zawiera listę obszarów nazw, do których chcesz uzyskać dostęp. Przypomina to `Using` instrukcję w języku Visual C#. Atrybut `Namespace` określa obszar nazw do uwzględnienia.

`Reference`i `Using` elementy są niezależne od języka. Zadania wbudowane mogą być zapisywane w dowolnym z obsługiwanych języków .NET CodeDom, na przykład Visual Basic lub Visual C#.

> [!NOTE]
> Elementy zawarte w `Task` elemencie są specyficzne dla fabryki zadań, w tym przypadku fabryki zadań kodu.

### <a name="code-element"></a>Element Code

Ostatni element podrzędny, `Task` który ma `Code` pojawić się w elemencie jest elementem. Element `Code` zawiera lub lokalizuje kod, który ma zostać skompilowany do zadania. To, co `Code` umieścisz w elemencie, zależy od tego, jak chcesz napisać zadanie.

Atrybut `Language` określa język, w którym kod jest zapisywany. Dopuszczalne `cs` wartości są `vb` dla języka C#, dla języka Visual Basic.

Atrybut `Type` określa typ kodu, który znajduje się `Code` w elemencie.

- Jeśli wartość `Type` jest `Class`, `Code` a następnie element zawiera kod dla <xref:Microsoft.Build.Framework.ITask> klasy, która pochodzi z interfejsu.

- Jeśli wartość `Type` jest `Method`, a następnie kod definiuje zastąpienie `Execute` metody <xref:Microsoft.Build.Framework.ITask> interfejsu.

- Jeśli wartość `Type` jest `Fragment`, a następnie kod definiuje `Execute` zawartość metody, ale `return` nie podpis lub instrukcji.

Sam kod zazwyczaj pojawia `<![CDATA[` się między `]]>` znacznikiem a znacznikiem. Ponieważ kod znajduje się w sekcji CDATA, nie musisz się martwić o\<ucieczkę zastrzeżonych znaków, na przykład " " lub ">".

Alternatywnie można użyć `Source` atrybutu `Code` elementu, aby określić lokalizację pliku, który zawiera kod dla zadania. Kod w pliku źródłowym musi być typu określonego `Type` przez atrybut. Jeśli `Source` atrybut jest obecny, domyślną `Type` `Class`wartością jest . Jeśli `Source` nie ma, wartością `Fragment`domyślną jest .

> [!NOTE]
> Podczas definiowania klasy zadań w pliku źródłowym, nazwa `TaskName` klasy musi zgadzać się z atrybutem odpowiedniego [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu.

## <a name="hello-world"></a>Witaj, świecie

 Oto bardziej niezawodne zadanie wbudowane z RoslynCodeTaskFactory. W zadaniu HelloWorld jest wyświetlane "Hello, world!" na domyślnym urządzeniu rejestrującym błędy, które jest zazwyczaj konsolą systemową lub oknem **dane wyjściowe** programu Visual Studio. Element `Reference` w przykładzie jest dołączony tylko do ilustracji.

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

Zadanie HelloWorld można zapisać w pliku o nazwie *HelloWorld.targets,* a następnie wywołać je z projektu w następujący sposób.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Parametry wejściowe i wyjściowe

 Parametry zadania wbudowanego są `ParameterGroup` elementami podrzędnymi elementu. Każdy parametr przyjmuje nazwę elementu, który go definiuje. Poniższy kod definiuje `Text`parametr .

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametry mogą mieć jeden lub więcej z tych atrybutów:

- `Required`jest atrybutem opcjonalnym, który jest `false` domyślnie. Jeśli `true`parametr jest wymagany i musi otrzymać wartość przed wywołaniem zadania.

- `ParameterType`jest atrybutem opcjonalnym, który jest `System.String` domyślnie. Można go ustawić na dowolny w pełni kwalifikowany typ, który jest elementem lub wartością, którą można przekonwertować na i z ciągu przy użyciu pliku System.Convert.ChangeType. (Innymi słowy, każdy typ, który może być przekazywany do i z zadania zewnętrznego.)

- `Output`jest atrybutem opcjonalnym, który jest `false` domyślnie. Jeśli `true`, a następnie parametr musi mieć wartość przed zwróceniem z Execute metody.

Na przykład:

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

określa te trzy parametry:

- `Expression`jest wymaganym parametrem wejściowym typu System.String.

- `Files`jest wymaganym parametrem wejściowym listy elementów.

- `Tally`jest parametrem wyjściowym typu System.Int32.

Jeśli `Code` element ma `Type` atrybut `Fragment` lub `Method`, a następnie właściwości są tworzone automatycznie dla każdego parametru.  W RoslynCodeTaskFactory, `Code` jeśli element `Type` ma `Class`atrybut , to nie trzeba `ParameterGroup`określić , ponieważ jest wywnioskowane `CodeTaskFactory`z kodu źródłowego (jest to różnica od ). W przeciwnym razie właściwości muszą być jawnie zadeklarowane w kodzie źródłowym zadania i muszą dokładnie odpowiadać ich definicjom parametrów.

## <a name="example"></a>Przykład

 Następujące wbudowane zadanie rejestruje niektóre komunikaty i zwraca ciąg.

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
- [Instruktaż: Tworzenie zadania wbudowanego](../msbuild/walkthrough-creating-an-inline-task.md)

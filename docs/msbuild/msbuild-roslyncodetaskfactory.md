---
title: Zadania wbudowane programu MSBuild, za pomocą RoslynCodeTaskFactory | Dokumentacja firmy Microsoft
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a3d9de68392bbb7f8e4f9c1ecd43211725f61d8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052016"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Zadania wbudowane programu MSBuild z RoslynCodeTaskFactory
Podobnie jak [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory używa kompilatory Roslyn dla wielu platform, aby wygenerować zestawy zadań w pamięci do użycia jako zadań w tekście.  Zadania RoslynCodeTaskFactory docelowych .NET Standard i może pracować nad środowiska uruchomieniowe platformy .NET Framework i .NET Core, a także innych platformach, takich jak Linux i Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory jest tylko dostępne w MSBuild 15.8 i powyżej.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Struktura z RoslynCodeTaskFactory zadania wbudowanego
 Zadania wbudowane RoslynCodeTaskFactory są deklarowane w identyczny sposób jak [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), jedyną różnicą, że ich celem .NET Standard.  Zadania wbudowane i `UsingTask` zawierający go najczęściej przygotowywanych do uwzględnienia w *.targets* pliku i zaimportować do innych plików projektów, zgodnie z potrzebami. Poniżej przedstawiono podstawowe wbudowane zadania. Należy zauważyć, że nic nie robi.

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

 `UsingTask` Element w przykładzie ma trzy atrybuty, które opisują zadania i wbudowane fabryki zadań, który kompiluje go.

- `TaskName` Nazwy atrybutów, zadania, w tym przypadku `DoNothing`.

- `TaskFactory` Atrybutu nazwy klasy, która implementuje fabryki zadań w tekście.

- `AssemblyFile` Atrybutu zapewnia lokalizacji fabryki zadań w tekście. Alternatywnie, można użyć `AssemblyName` atrybutu, aby określić w pełni kwalifikowana nazwa klasy fabryki wbudowanych zadań, która znajduje się w globalnej pamięci podręcznej zestawów (GAC).

Pozostałe elementy `DoNothing` zadania są puste, znajdują się w celu zilustrowania kolejności i struktura zadania wbudowanego. Bardziej niezawodna przykład został przedstawiony w dalszej części tego tematu.

- `ParameterGroup` Element jest opcjonalne. Jeśli zostanie określony, deklaruje parametrów zadania. Aby uzyskać więcej informacji na temat parametrów wejściowych i wyjściowych, zobacz [dane wejściowe i parametry wyjściowe](#input-and-output-parameters) w dalszej części tego tematu.

- `Task` Element opisuje i zawiera kod źródłowy zadania.

- `Reference` Element określa odwołania do zestawów .NET, które są używane w kodzie. Jest to równoważne do dodawania odwołania do projektu w programie Visual Studio. `Include` Atrybut ścieżka przywoływanego zestawu.

- `Using` Element zawiera przestrzenie nazw, które chcesz uzyskać dostęp. Przypomina to `Using` instrukcji w języku Visual C#. `Namespace` Atrybut określa przestrzeń nazw do uwzględnienia.

`Reference` i `Using` elementy są one niezależne od języka. Zadania wbudowane można pisać w jednym z obsługiwanych języków .NET CodeDom, na przykład Visual Basic lub Visual C#.

> [!NOTE]
>  Elementy zawarte w `Task` elementu są specyficzne dla fabryki zadań, w tym przypadku fabryki zadań kodu.

### <a name="code-element"></a>Element Code
Ostatni element podrzędny, które mają być wyświetlane w `Task` element jest `Code` elementu. `Code` Element zawiera lub lokalizuje kod, który ma być skompilowane w ramach zadania. Umieść w `Code` element zależy od tego, jak chcesz napisać zadanie.

`Language` Atrybut określa język, w którym napisano kod. Dopuszczalne wartości to `cs` dla języka C# `vb` dla języka Visual Basic.

`Type` Atrybut określa typ kodu, który można znaleźć w `Code` elementu.

- Jeśli wartość `Type` jest `Class`, a następnie `Code` element zawiera kod dla klasy, która pochodzi od klasy <xref:Microsoft.Build.Framework.ITask> interfejsu.

- Jeśli wartość `Type` jest `Method`, ten kod definiuje nadpisanie `Execute` metody <xref:Microsoft.Build.Framework.ITask> interfejsu.

- Jeśli wartość `Type` jest `Fragment`, ten kod definiuje zawartość `Execute` metody, ale nie podpisu lub `return` instrukcji.

Sam kod zwykle pojawia się między `<![CDATA[` znaczników i `]]>` znacznika. Ponieważ kod znajduje się w sekcji CDATA, nie masz już martwić się o zmianę znaczenia znaków zastrzeżonych, na przykład "\<" lub ">".

Alternatywnie, można użyć `Source` atrybutu `Code` element, aby określić lokalizację pliku, który zawiera kod dla zadania. Kod w pliku źródłowym musi być typu, który jest określony przez `Type` atrybutu. Jeśli `Source` atrybut był obecny, wartość domyślna `Type` jest `Class`. Jeśli `Source` jest nieobecna, wartość domyślna to `Fragment`.

> [!NOTE]
>  Podczas definiowania klasy zadań w pliku źródłowym, nazwa klasy należy uzgodnić z `TaskName` atrybut odpowiadającego [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu.

## <a name="hello-world"></a>Witaj Świecie
 Poniżej przedstawiono bardziej niezawodne zadania wbudowanego z RoslynCodeTaskFactory. Wyświetla zadania HelloWorld "Hello, world!" na domyślne urządzenie rejestrowania błędów, który jest zazwyczaj konsoli systemowej lub Visual Studio **dane wyjściowe** okna. `Reference` Elementu w przykładzie jest dołączony tylko do celów ilustracyjnych.

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

Zadanie HelloWorld można zapisać w pliku o nazwie *HelloWorld.targets*, a następnie wywołaj ją z projektu w następujący sposób.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Parametry wejściowe i wyjściowe
 Parametry zadania wbudowane są elementami podrzędnymi `ParameterGroup` elementu. Każdy parametr przyjmuje nazwę elementu, który go definiuje. Poniższy kod definiuje parametru `Text`.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametry może mieć co najmniej jeden z tych atrybutów:

- `Required` jest opcjonalny atrybut, który jest `false` domyślnie. Jeśli `true`, a następnie parametr jest wymagany i musi być danej wartości przed wywołaniem zadania.

- `ParameterType` jest opcjonalny atrybut, który jest `System.String` domyślnie. Mogą posłużyć do w pełni kwalifikowaną typu, elementu lub wartości, który może zostać przekonwertowany do i z ciągu za pomocą System.Convert.ChangeType. (Innymi słowy, dowolnej typ, który mogą być przekazywane do i z zadania zewnętrznego.)

- `Output` jest opcjonalny atrybut, który jest `false` domyślnie. Jeśli `true`, a następnie parametru musi być danej wartości przed powrotem z metody Execute.

Na przykład

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

definiuje trzy następujące parametry:

- `Expression` jest wymagany parametr wejściowy typu System.String.

- `Files` jest wymagany element parametr wejściowy listy.

- `Tally` jest parametrem wyjściowym typu System.Int32.

Jeśli `Code` element ma `Type` atrybutu `Fragment` lub `Method`, a następnie właściwości są tworzone automatycznie dla każdego parametru. W przeciwnym razie właściwości musi być jawnie zadeklarowana w kodzie źródłowym zadań i muszą dokładnie odpowiadać ich definicji parametru.

## <a name="example"></a>Przykład
 Następujące zadania wbudowanego rejestruje komunikaty z żądaniem i zwraca wartość typu ciąg.

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

Te zadania wbudowane można łączyć ścieżek i pobrać nazwy pliku.

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

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Przewodnik: Tworzenie zadania wbudowanego](../msbuild/walkthrough-creating-an-inline-task.md)

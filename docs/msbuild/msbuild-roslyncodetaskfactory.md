---
title: Zadania wbudowane programu MSBuild z RoslynCodeTaskFactory | Microsoft Docs
description: Dowiedz się więcej o programie MSBuild RoslynCodeTaskFactory, który używa międzyplatformowych kompilatorów Roslyn do generowania zestawów zadań w pamięci do użycia jako zadania wbudowane.
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c033c4d0ee36b9cb01618dd3ac3183e8782c70d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878425"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Zadania wbudowane programu MSBuild przy użyciu fabryki RoslynCodeTaskFactory

Podobnie jak w przypadku [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), RoslynCodeTaskFactory używa międzyplatformowych kompilatorów Roslyn do generowania zestawów zadań w pamięci do użycia jako zadania wbudowane.  .NET Standard obiektów docelowych zadań RoslynCodeTaskFactory i może współdziałać z .NET Framework i środowiska uruchomieniowe platformy .NET Core, a także z innymi platformami, takimi jak Linux i Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory jest dostępna tylko w programie MSBuild 15,8 i nowszych. Wersje MSBuild są zgodne z wersjami programu Visual Studio, więc RoslynCodeTaskFactory jest dostępna w programie Visual Studio 2017 w wersji 15,8 lub nowszej.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Struktura zadania śródwierszowego z RoslynCodeTaskFactory

 RoslynCodeTaskFactory wbudowane zadania są deklarowane w taki sam sposób jak [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), jedyną różnicą jest to, że docelowe .NET Standard.  Zadanie śródwierszowe i `UsingTask` element, który go zawiera, są zwykle zawarte w pliku *. targets* i importowane do innych plików projektu zgodnie z wymaganiami. Oto podstawowe zadanie wbudowane. Należy zauważyć, że nic nie robi.

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

 `UsingTask`Element w przykładzie ma trzy atrybuty opisujące zadanie i wbudowaną fabrykę zadań, która kompiluje go.

- `TaskName`Atrybut Nazwa zadania, w tym przypadku `DoNothing` .

- `TaskFactory`Atrybut określa nazwę klasy, która implementuje wbudowaną fabrykę zadań.

- Ten `AssemblyFile` atrybut zawiera lokalizację wewnętrznej fabryki zadań. Alternatywnie można użyć `AssemblyName` atrybutu, aby określić w pełni kwalifikowaną nazwę wbudowanej klasy fabryki zadań, która zwykle znajduje się w globalnej pamięci podręcznej zestawów (GAC).

Pozostałe elementy `DoNothing` zadania są puste i są dostarczane w celu zilustrowania kolejności i struktury zadania wbudowanego. Bardziej niezawodny przykład został przedstawiony w dalszej części tego tematu.

- `ParameterGroup`Element jest opcjonalny. Gdy jest określony, deklaruje parametry zadania. Aby uzyskać więcej informacji na temat parametrów wejściowych i wyjściowych, zobacz [Parametry wejściowe i wyjściowe](#input-and-output-parameters) w dalszej części tego tematu.

- `Task`Element opisuje i zawiera kod źródłowy zadania.

- `Reference`Element określa odwołania do zestawów .NET, które są używane w kodzie. Jest to równoznaczne z dodaniem odwołania do projektu w programie Visual Studio. Ten `Include` atrybut określa ścieżkę do przywoływanego zestawu.

- `Using`Element zawiera listę przestrzeni nazw, do których chcesz uzyskać dostęp. Jest to podobne do `Using` instrukcji w Visual C#. `Namespace`Atrybut określa przestrzeń nazw do uwzględnienia.

`Reference` i `Using` są elementami języka niezależny od. Zadania wbudowane można napisać w jednym z obsługiwanych języków języka .NET CodeDom, na przykład Visual Basic lub Visual C#.

> [!NOTE]
> Elementy zawarte w `Task` elemencie są specyficzne dla fabryki zadań, w tym przypadku fabryki zadań Code.

### <a name="code-element"></a>Element Code

Ostatni element podrzędny, który ma być wyświetlany w `Task` elemencie, jest `Code` elementem. `Code`Element zawiera lub lokalizuje kod, który chcesz skompilować do zadania. Elementy, które umieszczasz w `Code` elemencie, zależą od tego, jak chcesz napisać zadanie.

Ten `Language` atrybut określa język, w którym napisano kod. Akceptowalne wartości `cs` dla Visual Basic są dla języka C# `vb` .

Ten `Type` atrybut określa typ kodu, który znajduje się w `Code` elemencie.

- Jeśli wartość `Type` to `Class` , `Code` element zawiera kod dla klasy, która dziedziczy z <xref:Microsoft.Build.Framework.ITask> interfejsu.

- Jeśli wartość `Type` jest `Method` , wówczas kod definiuje przesłonięcie `Execute` metody <xref:Microsoft.Build.Framework.ITask> interfejsu.

- Jeśli wartość `Type` jest `Fragment` , wówczas kod definiuje zawartość `Execute` metody, ale nie sygnaturę lub `return` instrukcję.

Sam kod jest zwykle wyświetlany między `<![CDATA[` znacznikiem a `]]>` znacznikiem. Ponieważ kod znajduje się w sekcji CDATA, nie trzeba martwić się o znak ucieczki, na przykład " \<" or "> ".

Alternatywnie, można użyć `Source` atrybutu `Code` elementu, aby określić lokalizację pliku, który zawiera kod zadania. Kod w pliku źródłowym musi być typu, który jest określony przez `Type` atrybut. Jeśli `Source` atrybut jest obecny, wartość domyślna `Type` to `Class` . Jeśli `Source` nie istnieje, wartość domyślna to `Fragment` .

> [!NOTE]
> Podczas definiowania klasy zadań w pliku źródłowym, nazwa klasy musi zgadzać się z `TaskName` atrybutem odpowiadającego elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) .

## <a name="hello-world"></a>Witaj, świecie

 Oto bardziej niezawodne zadanie wbudowane z RoslynCodeTaskFactory. Zadanie HelloWorld wyświetla "Hello, World!" na domyślnym urządzeniu rejestrowania błędów, które jest zazwyczaj konsolą systemową lub oknem **danych wyjściowych** programu Visual Studio. `Reference`Element w przykładzie jest dołączony tylko do ilustracji.

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

 Wbudowane parametry zadań są elementami podrzędnymi `ParameterGroup` elementu. Każdy parametr przyjmuje nazwę elementu, który go definiuje. Poniższy kod definiuje parametr `Text` .

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

Parametry mogą mieć jeden lub więcej z następujących atrybutów:

- `Required` jest opcjonalnym atrybutem, który jest `false` domyślnie. Jeśli `true` parametr jest wymagany i musi mieć określoną wartość przed wywołaniem zadania.

- `ParameterType` jest opcjonalnym atrybutem, który jest `System.String` domyślnie. Może być ustawiony na dowolny w pełni kwalifikowany typ, który jest elementem lub wartością, którą można przekonwertować na i z ciągu przy użyciu System. Convert. ChangeType. (Innymi słowy każdy typ, który może być przekazywać do i z zewnętrznego zadania).

- `Output` jest opcjonalnym atrybutem, który jest `false` domyślnie. Jeśli `true` , wówczas parametr musi mieć wartość przed powrotem z metody Execute.

Na przykład

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

Jeśli `Code` element ma `Type` atrybut `Fragment` lub `Method` , wówczas właściwości są tworzone automatycznie dla każdego parametru.  W RoslynCodeTaskFactory, jeśli `Code` element ma `Type` atrybut `Class` , nie trzeba określać `ParameterGroup` , ponieważ jest wywnioskowany na podstawie kodu źródłowego (jest to różnica od `CodeTaskFactory` ). W przeciwnym razie właściwości muszą być jawnie zadeklarowane w kodzie źródłowym zadania i muszą dokładnie pasować do ich definicji parametrów.

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

## <a name="provide-backward-compatibility"></a>Zapewnianie zgodności z poprzednimi wersjami

`RoslynCodeTaskFactory` Pierwsza stała się dostępna w programie MSBuild w wersji 15,8. Załóżmy, że masz sytuacje, w których chcesz obsługiwać poprzednie wersje programu Visual Studio i MSBuild, gdy `RoslynCodeTaskFactory` była niedostępna, ale jeśli `CodeTaskFactory` chcesz użyć tego samego skryptu kompilacji. Można użyć konstrukcji korzystającej z `Choose` właściwości, `$(MSBuildVersion)` aby decydować w czasie kompilacji, czy użyć `RoslynCodeTaskFactory` lub wrócić do `CodeTaskFactory` , jak w poniższym przykładzie:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Choose>
    <When Condition=" '$(MSBuildVersion.Substring(0,2))' >= 16 Or
    ('$(MSBuildVersion.Substring(0,2))' == 15 And '$(MSBuildVersion.Substring(3,1))' >= 8)">
      <PropertyGroup>
        <TaskFactory>RoslynCodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </When>
    <Otherwise>
      <PropertyGroup>
        <TaskFactory>CodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </Otherwise>
  </Choose>
  
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="$(TaskFactory)"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup />
    <Task>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
        <![CDATA[
         Log.LogError("Using RoslynCodeTaskFactory");
      ]]>
      </Code>
    </Task>
  </UsingTask>

  <Target Name="RunTask" AfterTargets="Build">
    <Message Text="MSBuildVersion: $(MSBuildVersion)"/>
    <Message Text="TaskFactory: $(TaskFactory)"/>
    <HelloWorld />
  </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Przewodnik: Tworzenie zadania wbudowanego](../msbuild/walkthrough-creating-an-inline-task.md)

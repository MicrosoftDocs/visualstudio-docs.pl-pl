---
title: Zadania wbudowane programu MSBuild | Microsoft Docs
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
ms.openlocfilehash: e68f2bdf0559dc2bea6bd349dbf5f9bedca3671e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633320"
---
# <a name="msbuild-inline-tasks"></a>Zadania wbudowane programu MSBuild

Zadania programu MSBuild są zwykle tworzone przez skompilowanie klasy implementującej interfejs <xref:Microsoft.Build.Framework.ITask>. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

 Począwszy od .NET Framework w wersji 4, można tworzyć zadania wbudowane w pliku projektu. Nie trzeba tworzyć oddzielnego zestawu, aby hostować zadanie. Ułatwia to śledzenie kodu źródłowego i ułatwia wdrażanie zadania. Kod źródłowy jest zintegrowany ze skryptem.

 W programie MSBuild 15,8 został dodany [RoslynCodeTaskFactory](../msbuild/msbuild-roslyncodetaskfactory.md) , który może tworzyć .NET Standard zadania wbudowane na wiele platform.  Jeśli musisz używać wbudowanych zadań w programie .NET Core, musisz użyć RoslynCodeTaskFactory.
## <a name="the-structure-of-an-inline-task"></a>Struktura zadania wbudowanego

 Zadanie śródwierszowe jest zawarte w elemencie [UsingTask](../msbuild/usingtask-element-msbuild.md) . Zadanie śródwierszowe i element `UsingTask`, który go zawiera, są zwykle zawarte w pliku *. targets* i importowane do innych plików projektu zgodnie z wymaganiami. Oto podstawowe zadanie wbudowane. Należy zauważyć, że nic nie robi.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="CodeTaskFactory"
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

## <a name="helloworld"></a>HelloWorld

 Oto bardziej niezawodne zadanie wbudowane. Zadanie HelloWorld wyświetla "Hello, World!" na domyślnym urządzeniu rejestrowania błędów, które jest zazwyczaj konsolą systemową lub oknem **danych wyjściowych** programu Visual Studio. Element `Reference` w przykładzie jest uwzględniany tylko w przypadku ilustracji.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="CodeTaskFactory"
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

 Następujące zadanie wbudowane zastępuje każde wystąpienie tokenu w danym pliku podaną wartością.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup>
      <Path ParameterType="System.String" Required="true" />
      <Token ParameterType="System.String" Required="true" />
      <Replacement ParameterType="System.String" Required="true" />
    </ParameterGroup>
    <Task>
      <Code Type="Fragment" Language="cs"><![CDATA[
string content = File.ReadAllText(Path);
content = content.Replace(Token, Replacement);
File.WriteAllText(Path, content);

]]></Code>
    </Task>
  </UsingTask>

  <Target Name='Demo' >
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Przewodnik: Tworzenie zadania wbudowanego](../msbuild/walkthrough-creating-an-inline-task.md)

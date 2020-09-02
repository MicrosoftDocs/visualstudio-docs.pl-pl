---
title: Zadania wbudowane programu MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cea0d72488bbd18972b2a2f6d87f21dfb32481d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64826812"
---
# <a name="msbuild-inline-tasks"></a>Zadania wbudowane programu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadania programu MSBuild są zwykle tworzone przez skompilowanie klasy, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
 Począwszy od .NET Framework w wersji 4, można tworzyć zadania wbudowane w pliku projektu. Nie trzeba tworzyć oddzielnego zestawu, aby hostować zadanie. Ułatwia to śledzenie kodu źródłowego i ułatwia wdrażanie zadania. Kod źródłowy jest zintegrowany ze skryptem.  
  
## <a name="the-structure-of-an-inline-task"></a>Struktura zadania wbudowanego  
 Zadanie śródwierszowe jest zawarte w elemencie [UsingTask](../msbuild/usingtask-element-msbuild.md) . Zadanie śródwierszowe i `UsingTask` element, który go zawiera, są zwykle zawarte w pliku. targets i importowane do innych plików projektu zgodnie z wymaganiami. Oto podstawowe zadanie wbudowane. Należy zauważyć, że nic nie robi.  
  
```  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task does nothing. -->  
  <UsingTask  
    TaskName="DoNothing"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll" >  
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
  
- `ParameterGroup`Element jest opcjonalny. Gdy jest określony, deklaruje parametry zadania. Aby uzyskać więcej informacji na temat parametrów wejściowych i wyjściowych, zobacz "parametry wejściowe i wyjściowe" w dalszej części tego tematu.  
  
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
 Oto bardziej niezawodne zadanie wbudowane. Zadanie HelloWorld wyświetla "Hello, World!" na domyślnym urządzeniu rejestrowania błędów, które jest zazwyczaj konsolą systemową lub oknem **danych wyjściowych** programu Visual Studio. `Reference`Element w przykładzie jest dołączony tylko do ilustracji.  
  
```  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task displays "Hello, world!" -->  
  <UsingTask  
    TaskName="HelloWorld"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
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
  
 Zadanie HelloWorld można zapisać w pliku o nazwie HelloWorld. targets, a następnie wywołać go z projektu w następujący sposób.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## <a name="input-and-output-parameters"></a>Parametry wejściowe i wyjściowe  
 Wbudowane parametry zadań są elementami podrzędnymi `ParameterGroup` elementu. Każdy parametr przyjmuje nazwę elementu, który go definiuje. Poniższy kod definiuje parametr `Text` .  
  
```  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  
  
 Parametry mogą mieć jeden lub więcej z następujących atrybutów:  
  
- `Required` jest opcjonalnym atrybutem, który jest `false` domyślnie. Jeśli `true` parametr jest wymagany i musi mieć określoną wartość przed wywołaniem zadania.  
  
- `ParameterType` jest opcjonalnym atrybutem, który jest `System.String` domyślnie. Może być ustawiony na dowolny w pełni kwalifikowany typ, który jest elementem lub wartością, którą można przekonwertować na i z ciągu przy użyciu System. Convert. ChangeType. (Innymi słowy każdy typ, który może być przekazywać do i z zewnętrznego zadania).  
  
- `Output` jest opcjonalnym atrybutem, który jest `false` domyślnie. Jeśli `true` , wówczas parametr musi mieć wartość przed powrotem z metody Execute.  
  
  Przykład:  
  
```  
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
  
  Jeśli `Code` element ma `Type` atrybut `Fragment` lub `Method` , wówczas właściwości są tworzone automatycznie dla każdego parametru. W przeciwnym razie właściwości muszą być jawnie zadeklarowane w kodzie źródłowym zadania i muszą dokładnie pasować do ich definicji parametrów.  
  
## <a name="example"></a>Przykład  
 Następujące zadanie wbudowane zastępuje każde wystąpienie tokenu w danym pliku podaną wartością.  
  
```  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="12.0">  
  
  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll">  
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
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Przewodnik: Tworzenie zadania wbudowanego](../msbuild/walkthrough-creating-an-inline-task.md)

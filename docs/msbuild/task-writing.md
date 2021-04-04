---
title: Pisanie zadania | Microsoft Docs
description: Dowiedz się, jak tworzyć własne zadania w celu zapewnienia kodu, który jest uruchamiany podczas procesu kompilacji MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0db9504404142e5bfdd17a66471820ddad790130
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214554"
---
# <a name="task-writing"></a>Pisanie zadań

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Zadania są zawarte w obiektach docelowych. Biblioteka typowych zadań jest dołączona do programu MSBuild i można również tworzyć własne zadania. Aby uzyskać więcej informacji na temat biblioteki zadań, które są dołączone do programu MSBuild, zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Zadania

 Przykłady zadań obejmują [kopię](../msbuild/copy-task.md), która kopiuje jeden lub więcej plików, [MakeDir](../msbuild/makedir-task.md), który tworzy katalog i [CSC](../msbuild/csc-task.md), który kompiluje pliki kodu źródłowego C#. Każde zadanie jest implementowane jako Klasa platformy .NET, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w zestawie *Microsoft.Build.Framework.dll* .

 Istnieją dwie metody, których można użyć podczas implementowania zadania:

- Zaimplementuj <xref:Microsoft.Build.Framework.ITask> interfejs bezpośrednio.

- Utwórz klasę z klasy pomocnika, <xref:Microsoft.Build.Utilities.Task> która jest zdefiniowana w zestawie *Microsoft.Build.Utilities.dll* . Zadanie implementuje ITask i udostępnia domyślne implementacje niektórych elementów członkowskich ITask. Ponadto rejestrowanie jest łatwiejsze.

W obu przypadkach należy dodać do klasy metodę o nazwie `Execute` , która jest wywoływana, gdy zadanie zostanie uruchomione. Ta metoda nie przyjmuje parametrów i zwraca `Boolean` wartość: `true` Jeśli zadanie zakończyło się pomyślnie lub `false` zakończyło się niepowodzeniem. Poniższy przykład pokazuje zadanie, które nie wykonuje akcji i zwraca wartość `true` .

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }
    }
}
```

 Następujący plik projektu uruchamia to zadanie:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Po uruchomieniu zadania mogą także odbierać dane wejściowe z pliku projektu, jeśli tworzysz właściwości platformy .NET dla klasy Task. MSBuild ustawia te właściwości bezpośrednio przed wywołaniem metody zadania `Execute` . Aby utworzyć właściwość String, użyj kodu zadania, takiego jak:

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }

        public string MyProperty { get; set; }
    }
}
```

 Następujący plik projektu uruchamia to zadanie i ustawia `MyProperty` daną wartość:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Rejestrowanie zadań

 Jeśli projekt będzie uruchamiał zadanie, MSBuild musi wiedzieć, jak zlokalizować zestaw, który zawiera klasę zadania. Zadania są rejestrowane przy użyciu [elementu UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Plik MSBuild *Microsoft. Common. Tasks* to plik projektu, który zawiera listę `UsingTask` elementów, które rejestrują wszystkie zadania dostarczone z programem MSBuild. Ten plik jest automatycznie dołączany podczas kompilowania każdego projektu. Jeśli zadanie zarejestrowane w *programie Microsoft. Common. Tasks* jest również zarejestrowane w pliku bieżącego projektu, ma pierwszeństwo bieżący plik projektu. oznacza to, że można zastąpić zadanie domyślne przy użyciu własnego zadania o tej samej nazwie.

> [!TIP]
> Listę zadań, które są dostarczane z programem MSBuild, można zobaczyć, wyświetlając zawartość elementu *Microsoft. Common. Tasks*.

## <a name="raise-events-from-a-task"></a>Wywoływanie zdarzeń z zadania

 Jeśli zadanie pochodzi od <xref:Microsoft.Build.Utilities.Task> klasy pomocnika, można użyć dowolnej z następujących metod pomocnika w <xref:Microsoft.Build.Utilities.Task> klasie, aby zgłosić zdarzenia, które będą przechwytywane i wyświetlane przez wszystkie zarejestrowane rejestratory:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Jeśli zadanie zostanie zaimplementowane <xref:Microsoft.Build.Framework.ITask> bezpośrednio, można nadal zgłosić takie zdarzenia, ale należy użyć interfejsu IBuildEngine. Poniższy przykład pokazuje zadanie implementujące ITask i wywołuje zdarzenie niestandardowe:

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

    public override bool Execute()
    {
        TaskEventArgs taskEvent =
            new TaskEventArgs(BuildEventCategory.Custom,
            BuildEventImportance.High, "Important Message",
           "SimpleTask");
        BuildEngine.LogBuildEvent(taskEvent);
        return true;
    }
}
```

## <a name="require-task-parameters-to-be-set"></a>Wymagaj ustawiania parametrów zadania

 Niektóre właściwości zadania można oznaczyć jako "wymagane", aby każdy plik projektu, który uruchomił zadanie, musiał ustawić wartości tych właściwości lub kompilacja kończy się niepowodzeniem. Zastosuj `[Required]` atrybut do właściwości .NET w zadaniu w następujący sposób:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 `[Required]`Atrybut jest definiowany przez <xref:Microsoft.Build.Framework.RequiredAttribute> w <xref:Microsoft.Build.Framework> przestrzeni nazw.

## <a name="how-msbuild-invokes-a-task"></a>Jak program MSBuild wywołuje zadanie

Podczas wywoływania zadania program MSBuild najpierw tworzy wystąpienie klasy Task, a następnie wywołuje metody ustawiające właściwości tego obiektu dla parametrów zadań ustawionych w elemencie Task w pliku projektu. Jeśli element Task nie określa parametru lub jeśli wyrażenie określone w elemencie Szacuje pusty ciąg, Metoda ustawiająca właściwość nie jest wywoływana.

Na przykład w projekcie

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

tylko Metoda ustawiająca dla `Input3` jest wywoływana.

Zadanie nie powinno zależeć od żadnej względnej kolejności wywołania metody ustawiającej właściwości parametru.

### <a name="task-parameter-types"></a>Typy parametrów zadań

Program MSBuild natywnie obsługuje właściwości typu `string` , `bool` , `ITaskItem` i `ITaskItem[]` . Jeśli zadanie akceptuje parametr innego typu, program MSBuild wywołuje <xref:System.Convert.ChangeType%2A> konwersję z `string` (ze wszystkimi rozwiniętymi właściwościami i elementami) na typ docelowy. Jeśli konwersja nie powiedzie się dla żadnego parametru wejściowego, MSBuild emituje błąd i nie wywołuje metody zadania `Execute()` .

## <a name="example-1"></a>Przykład 1

### <a name="description"></a>Opis

W poniższej klasie języka C# przedstawiono zadanie pochodne od <xref:Microsoft.Build.Utilities.Task> klasy pomocnika. To zadanie zwraca `true` , wskazując, że zakończyło się pomyślnie.

### <a name="code"></a>Kod

```csharp
using System;
using Microsoft.Build.Utilities;

namespace SimpleTask1
{
    public class SimpleTask1: Task
    {
        public override bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-2"></a>Przykład 2

### <a name="description"></a>Opis

W poniższej klasie języka C# przedstawiono zadanie implementujące <xref:Microsoft.Build.Framework.ITask> interfejs. To zadanie zwraca `true` , wskazując, że zakończyło się pomyślnie.

### <a name="code"></a>Kod

```csharp
using System;
using Microsoft.Build.Framework;

namespace SimpleTask2
{
    public class SimpleTask2: ITask
    {
        //When implementing the ITask interface, it is necessary to
        //implement a BuildEngine property of type
        //Microsoft.Build.Framework.IBuildEngine. This is done for
        //you if you derive from the Task class.
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-3"></a>Przykład 3

### <a name="description"></a>Opis

Ta klasa języka C# pokazuje zadanie, które pochodzi od <xref:Microsoft.Build.Utilities.Task> klasy pomocnika. Ma ona wymaganą właściwość String i wywołuje zdarzenie, które jest wyświetlane przez wszystkie zarejestrowane rejestratory.

### <a name="code"></a>Kod

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs" id="Snippet1":::

## <a name="example-4"></a>Przykład 4

### <a name="description"></a>Opis

W poniższym przykładzie przedstawiono plik projektu wywołujący poprzednie przykładowe zadanie, SimpleTask3.

### <a name="code"></a>Kod

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

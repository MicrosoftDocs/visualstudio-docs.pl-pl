---
title: Pisanie zadania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cf7f82d628c0c093e0d807920b379263c20ff0b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238194"
---
# <a name="task-writing"></a>Pisanie zadania
Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Zadania są zawarte w obiektach docelowych. Biblioteka typowych zadań jest dołączona do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]programu i można także utworzyć własne zadania. Aby uzyskać więcej informacji na temat biblioteki zadań, które są dołączone [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]do programu, zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Zadania
 Przykłady zadań obejmują [kopię](../msbuild/copy-task.md), która kopiuje jeden lub więcej plików, [MakeDir](../msbuild/makedir-task.md), który tworzy katalog i [CSC](../msbuild/csc-task.md), który kompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pliki kodu źródłowego. Każde zadanie jest implementowane jako Klasa platformy .NET, która <xref:Microsoft.Build.Framework.ITask> implementuje interfejs, który jest zdefiniowany w zestawie *Microsoft. Build. Framework. dll* .

 Istnieją dwie metody, których można użyć podczas implementowania zadania:

- Zaimplementuj <xref:Microsoft.Build.Framework.ITask> interfejs bezpośrednio.

- Utwórz klasę z klasy pomocnik, <xref:Microsoft.Build.Utilities.Task>która jest zdefiniowana w zestawie *Microsoft. Build. Utilities. dll* . Zadanie implementuje ITask i udostępnia domyślne implementacje niektórych elementów członkowskich ITask. Ponadto rejestrowanie jest łatwiejsze.

W obu przypadkach należy dodać do klasy metodę o nazwie `Execute`, która jest wywoływana, gdy zadanie zostanie uruchomione. Ta metoda nie przyjmuje parametrów i zwraca `Boolean` wartość: `true` Jeśli zadanie zakończyło się pomyślnie `false` lub zakończyło się niepowodzeniem. Poniższy przykład pokazuje zadanie, które nie wykonuje akcji i zwraca wartość `true`.

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

 Po uruchomieniu zadania mogą także odbierać dane wejściowe z pliku projektu, jeśli tworzysz właściwości platformy .NET dla klasy Task. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]Ustawia te właściwości bezpośrednio przed wywołaniem `Execute` metody zadania. Aby utworzyć właściwość String, użyj kodu zadania, takiego jak:

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
 Jeśli projekt będzie uruchamiał zadanie, należy wiedzieć, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jak zlokalizować zestaw, który zawiera klasę zadania. Zadania są rejestrowane przy użyciu [elementu UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Plik Microsoft *. Common. Tasks* to plik projektu, który `UsingTask` zawiera listę elementów, które rejestrują wszystkie zadania, które są dostarczane z. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Ten plik jest automatycznie dołączany podczas kompilowania każdego projektu. Jeśli zadanie zarejestrowane w *programie Microsoft. Common. Tasks* jest również zarejestrowane w pliku bieżącego projektu, ma pierwszeństwo bieżący plik projektu. oznacza to, że można zastąpić zadanie domyślne przy użyciu własnego zadania o tej samej nazwie.

> [!TIP]
> Można wyświetlić listę zadań, które są dostarczane z programem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] , wyświetlając zawartość elementu *Microsoft. Common. Tasks*.

## <a name="raise-events-from-a-task"></a>Wywoływanie zdarzeń z zadania
 Jeśli zadanie pochodzi od <xref:Microsoft.Build.Utilities.Task> klasy pomocnika, można użyć dowolnej z następujących metod pomocnika <xref:Microsoft.Build.Utilities.Task> w klasie, aby zgłosić zdarzenia, które będą przechwytywane i wyświetlane przez wszystkie zarejestrowane rejestratory:

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
 Niektóre właściwości zadania można oznaczyć jako "wymagane", aby każdy plik projektu, który uruchomił zadanie, musiał ustawić wartości tych właściwości lub kompilacja kończy się niepowodzeniem. `[Required]` Zastosuj atrybut do właściwości .NET w zadaniu w następujący sposób:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 Atrybut jest definiowany przez <xref:Microsoft.Build.Framework.RequiredAttribute> w <xref:Microsoft.Build.Framework> przestrzeni nazw. `[Required]`

## <a name="how-includevstecmsbuildextensibilityinternalsincludesvstecmsbuild_mdmd-invokes-a-task"></a>Jak [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wywołuje zadanie

Podczas wywoływania zadania, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] najpierw tworzy wystąpienie klasy Task, a następnie wywołuje metody ustawiające właściwości tego obiektu dla parametrów zadań ustawionych w elemencie Task w pliku projektu. Jeśli element Task nie określa parametru lub jeśli wyrażenie określone w elemencie Szacuje pusty ciąg, Metoda ustawiająca właściwość nie jest wywoływana.

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

tylko Metoda ustawiająca `Input3` dla jest wywoływana.

Zadanie nie powinno zależeć od żadnej względnej kolejności wywołania metody ustawiającej właściwości parametru.

### <a name="task-parameter-types"></a>Typy parametrów zadań

`string` `bool` `ITaskItem` Natywnie obsługuje właściwości typu,, i`ITaskItem[]`. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Jeśli zadanie akceptuje parametr innego typu, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wywoła <xref:System.Convert.ChangeType%2A> do konwersji z `string` (ze wszystkimi rozwiniętymi właściwościami i elementami) na typ docelowy. Jeśli konwersja nie powiedzie się dla żadnego parametru [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wejściowego, emituje błąd i nie wywołuje `Execute()` metody zadania.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższej [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasie przedstawiono zadanie pochodne <xref:Microsoft.Build.Utilities.Task> od klasy pomocnika. To zadanie zwraca `true`, wskazując, że zakończyło się pomyślnie.

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

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższej [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] klasie przedstawiono zadanie <xref:Microsoft.Build.Framework.ITask> implementujące interfejs. To zadanie zwraca `true`, wskazując, że zakończyło się pomyślnie.

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

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Ta [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Klasa pokazuje zadanie, które pochodzi <xref:Microsoft.Build.Utilities.Task> od klasy pomocnika. Ma ona wymaganą właściwość String i wywołuje zdarzenie, które jest wyświetlane przez wszystkie zarejestrowane rejestratory.

### <a name="code"></a>Kod

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a>Przykład

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

## <a name="see-also"></a>Zobacz także

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

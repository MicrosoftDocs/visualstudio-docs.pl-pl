---
title: Pisanie zadania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 369584a815f671c8b7b4f8a99a5280626b493104
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594997"
---
# <a name="task-writing"></a>Pisanie zadania
Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Zadania są zawarte w obiektach docelowych. Biblioteka typowych zadań jest dołączona do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]i można także utworzyć własne zadania. Aby uzyskać więcej informacji na temat biblioteki zadań, które są dołączone do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Zadania
 Przykłady zadań obejmują [kopię](../msbuild/copy-task.md), która kopiuje jeden lub więcej plików, [MakeDir](../msbuild/makedir-task.md), który tworzy katalog i [Csc](../msbuild/csc-task.md), który kompiluje [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pliki kodu źródłowego. Każde zadanie jest implementowane jako Klasa .NET implementująca interfejs <xref:Microsoft.Build.Framework.ITask>, który jest zdefiniowany w zestawie *Microsoft. Build. Framework. dll* .

 Istnieją dwie metody, których można użyć podczas implementowania zadania:

- Zaimplementuj interfejs <xref:Microsoft.Build.Framework.ITask> bezpośrednio.

- Utwórz klasę z klasy pomocnika, <xref:Microsoft.Build.Utilities.Task>, która jest zdefiniowana w zestawie *Microsoft. Build. Utilities. dll* . Zadanie implementuje ITask i udostępnia domyślne implementacje niektórych elementów członkowskich ITask. Ponadto rejestrowanie jest łatwiejsze.

W obu przypadkach należy dodać do klasy metodę o nazwie `Execute`, która jest wywoływana, gdy zadanie zostanie uruchomione. Ta metoda nie przyjmuje parametrów i zwraca wartość `Boolean`: `true`, jeśli zadanie zakończyło się pomyślnie lub `false`, jeśli zakończyło się niepowodzeniem. Poniższy przykład pokazuje zadanie, które nie wykonuje żadnej akcji i zwraca `true`.

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

 Po uruchomieniu zadania mogą także odbierać dane wejściowe z pliku projektu, jeśli tworzysz właściwości platformy .NET dla klasy Task. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ustawia te właściwości bezpośrednio przed wywołaniem metody `Execute` zadania. Aby utworzyć właściwość String, użyj kodu zadania, takiego jak:

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

 Następujący plik projektu uruchamia to zadanie i ustawia `MyProperty` na daną wartość:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Rejestrowanie zadań
 Jeśli projekt będzie uruchamiał zadanie, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] musi wiedzieć, jak zlokalizować zestaw, który zawiera klasę zadania. Zadania są rejestrowane przy użyciu [elementu UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Plik [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] *Microsoft. Common. Tasks* to plik projektu, który zawiera listę elementów `UsingTask`, które rejestrują wszystkie zadania dostarczone z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Ten plik jest automatycznie dołączany podczas kompilowania każdego projektu. Jeśli zadanie zarejestrowane w *programie Microsoft. Common. Tasks* jest również zarejestrowane w pliku bieżącego projektu, ma pierwszeństwo bieżący plik projektu. oznacza to, że można zastąpić zadanie domyślne przy użyciu własnego zadania o tej samej nazwie.

> [!TIP]
> Listę zadań, które są dostarczane z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], można wyświetlić, wyświetlając zawartość elementu *Microsoft. Common. Tasks*.

## <a name="raise-events-from-a-task"></a>Wywoływanie zdarzeń z zadania
 Jeśli zadanie pochodzi od klasy pomocnika <xref:Microsoft.Build.Utilities.Task>, można użyć dowolnej z następujących metod pomocnika na klasie <xref:Microsoft.Build.Utilities.Task>, aby zgłosić zdarzenia, które będą przechwytywane i wyświetlane przez wszystkie zarejestrowane rejestratory:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Jeśli zadanie implementuje <xref:Microsoft.Build.Framework.ITask> bezpośrednio, można nadal zgłosić takie zdarzenia, ale należy użyć interfejsu IBuildEngine. Poniższy przykład pokazuje zadanie implementujące ITask i wywołuje zdarzenie niestandardowe:

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
 Niektóre właściwości zadania można oznaczyć jako "wymagane", aby każdy plik projektu, który uruchomił zadanie, musiał ustawić wartości tych właściwości lub kompilacja kończy się niepowodzeniem. Zastosuj atrybut `[Required]` do właściwości .NET w zadaniu w następujący sposób:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 Atrybut `[Required]` jest definiowany przez <xref:Microsoft.Build.Framework.RequiredAttribute> w przestrzeni nazw <xref:Microsoft.Build.Framework>.

## <a name="how-includevstecmsbuildextensibilityinternalsincludesvstecmsbuild_mdmd-invokes-a-task"></a>Jak [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wywołuje zadanie

Podczas wywoływania zadania [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pierwsze wystąpienie klasy zadania, a następnie wywołuje metody ustawiające właściwości tego obiektu dla parametrów zadań ustawionych w elemencie Task w pliku projektu. Jeśli element Task nie określa parametru lub jeśli wyrażenie określone w elemencie Szacuje pusty ciąg, Metoda ustawiająca właściwość nie jest wywoływana.

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

wywoływana jest tylko Metoda ustawiająca dla `Input3`.

Zadanie nie powinno zależeć od żadnej względnej kolejności wywołania metody ustawiającej właściwości parametru.

### <a name="task-parameter-types"></a>Typy parametrów zadań

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] natywnie obsługuje właściwości typu `string`, `bool`, `ITaskItem` i `ITaskItem[]`. Jeśli zadanie akceptuje parametr innego typu, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wywoła <xref:System.Convert.ChangeType%2A> do konwersji z `string` (wszystkie odwołania właściwości i elementów rozwinięte) do typu docelowego. Jeśli konwersja nie powiedzie się dla żadnego parametru wejściowego, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] emituje błąd i nie wywoła metody `Execute()` zadania.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższej klasie [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] przedstawiono zadanie pochodne z klasy pomocnika <xref:Microsoft.Build.Utilities.Task>. To zadanie zwraca `true`, wskazując, że zakończyło się pomyślnie.

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

W poniższej klasie [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] przedstawiono zadanie implementujące interfejs <xref:Microsoft.Build.Framework.ITask>. To zadanie zwraca `true`, wskazując, że zakończyło się pomyślnie.

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

Ta klasa [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ilustruje zadanie pochodzące z klasy pomocnika <xref:Microsoft.Build.Utilities.Task>. Ma ona wymaganą właściwość String i wywołuje zdarzenie, które jest wyświetlane przez wszystkie zarejestrowane rejestratory.

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

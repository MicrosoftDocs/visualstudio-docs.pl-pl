---
title: Pisanie zadań | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 8cbcf47ec83e1b900ba94ab3842c2cfa63fdcc5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631841"
---
# <a name="task-writing"></a>Pisanie zadań

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Zadania są zawarte w obiekty docelowe. Biblioteka typowych zadań jest dołączona do MSBuild i można również tworzyć własne zadania. Aby uzyskać więcej informacji na temat biblioteki zadań dołączonych do programu MSBuild, zobacz [Odwołanie do zadania](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Zadania

 Przykłady zadań obejmują [Kopiuj](../msbuild/copy-task.md), który kopiuje jeden lub więcej plików, [MakeDir](../msbuild/makedir-task.md), który tworzy katalog, i [Csc](../msbuild/csc-task.md), który kompiluje pliki kodu źródłowego języka C#. Każde zadanie jest implementowane jako klasa .NET, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w zestawie *Microsoft.Build.Framework.dll.*

 Istnieją dwa podejścia, których można użyć podczas implementowania zadania:

- Implementuj <xref:Microsoft.Build.Framework.ITask> interfejs bezpośrednio.

- Wywodź swoją klasę z <xref:Microsoft.Build.Utilities.Task>klasy pomocnika, która jest zdefiniowana w zestawie *Microsoft.Build.Utilities.dll.* Zadanie implementuje ITask i zapewnia domyślne implementacje niektórych członków ITask. Ponadto rejestrowanie jest łatwiejsze.

W obu przypadkach należy dodać do klasy `Execute`metodę o nazwie , która jest metodą, która jest wywoływana po uruchomieniu zadania. Ta metoda nie przyjmuje `Boolean` żadnych `true` parametrów i zwraca `false` wartość: jeśli zadanie zakończyło się pomyślnie lub jeśli nie powiodło się. W poniższym przykładzie przedstawiono zadanie, `true`które nie wykonuje żadnej akcji i zwraca .

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

 Następujące zadanie uruchamia plik projektu:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Po uruchomieniu zadań mogą również odbierać dane wejściowe z pliku projektu, jeśli utworzysz właściwości platformy .NET w klasie zadań. MSBuild ustawia te właściwości bezpośrednio przed `Execute` wywołaniem metody zadania. Aby utworzyć właściwość ciągu, należy użyć kodu zadania, takiego jak:

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

 Następujący plik projektu uruchamia to `MyProperty` zadanie i ustawia pod uwagę wartość:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Rejestrowanie zadań

 Jeśli projekt ma zamiar uruchomić zadanie, MSBuild musi wiedzieć, jak zlokalizować zestaw, który zawiera klasę zadań. Zadania są rejestrowane przy użyciu [UsingTask element (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Plik MSBuild *Microsoft.Common.Tasks* jest plikiem projektu, `UsingTask` który zawiera listę elementów, które rejestrują wszystkie zadania dostarczane z MSBuild. Ten plik jest automatycznie uwzględniany podczas tworzenia każdego projektu. Jeśli zadanie zarejestrowane w programie *Microsoft.Common.Tasks* jest również zarejestrowane w bieżącym pliku projektu, pierwszeństwo ma bieżący plik projektu; oznacza to, że można zastąpić zadanie domyślne własnym zadaniem, które ma taką samą nazwę.

> [!TIP]
> Listę zadań dostarczanych z programem MSBuild można wyświetlić, wyświetlając zawartość programu *Microsoft.Common.Tasks*.

## <a name="raise-events-from-a-task"></a>Podwyższaj zdarzenia z zadania

 Jeśli zadanie pochodzi od <xref:Microsoft.Build.Utilities.Task> klasy pomocnika, można użyć dowolnej z następujących <xref:Microsoft.Build.Utilities.Task> metod pomocnika w klasie do podnoszenia zdarzeń, które zostaną przechwycone i wyświetlane przez zarejestrowane rejestratory:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Jeśli zadanie implementuje <xref:Microsoft.Build.Framework.ITask> bezpośrednio, nadal można podnieść takie zdarzenia, ale należy użyć interfejsu IBuildEngine. W poniższym przykładzie pokazano zadanie, które implementuje ITask i wywołuje zdarzenie niestandardowe:

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

 Można oznaczyć niektóre właściwości zadania jako "wymagane", tak aby każdy plik projektu, który uruchamia zadanie musi ustawić wartości dla tych właściwości lub kompilacji nie powiedzie się. Zastosuj `[Required]` atrybut do właściwości .NET w zadaniu w następujący sposób:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 Atrybut `[Required]` jest zdefiniowany <xref:Microsoft.Build.Framework.RequiredAttribute> przez <xref:Microsoft.Build.Framework> w obszarze nazw.

## <a name="how-msbuild-invokes-a-task"></a>Jak MSBuild wywołuje zadanie

Podczas wywoływania zadania MSBuild najpierw wywołuje utworzenie wystąpienia klasy zadań, a następnie wywołuje ustawiacze właściwości tego obiektu dla parametrów zadań, które są ustawione w elemencie zadania w pliku projektu. Jeśli element zadania nie określa parametru lub jeśli wyrażenie określone w elemencie ma wartość pustego ciągu, ustawiacz właściwości nie jest wywoływany.

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

nazywa `Input3` się tylko ustawiacz.

Zadanie nie powinno zależeć od względnej kolejności wywołania settera właściwości parametru.

### <a name="task-parameter-types"></a>Typy parametrów zadania

MSBuild natywnie obsługuje właściwości `string` `bool`typu `ITaskItem` `ITaskItem[]`, i . Jeśli zadanie akceptuje parametr innego typu, MSBuild <xref:System.Convert.ChangeType%2A> wywołuje do `string` konwersji z (z wszystkich właściwości i elementów odwołania rozwinięte) do typu docelowego. Jeśli konwersja nie powiedzie się dla dowolnego parametru wejściowego, MSBuild emituje błąd i nie wywoła `Execute()` metody zadania.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Ta następująca klasa Języka C# pokazuje <xref:Microsoft.Build.Utilities.Task> zadanie wynikające z klasy pomocnika. To zadanie `true`zwraca , wskazując, że powiodło się.

### <a name="code"></a>Code

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

Ta następująca klasa języka C# <xref:Microsoft.Build.Framework.ITask> pokazuje zadanie implementujące interfejs. To zadanie `true`zwraca , wskazując, że powiodło się.

### <a name="code"></a>Code

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

Ta klasa Języka C# pokazuje zadanie, <xref:Microsoft.Build.Utilities.Task> które pochodzi od klasy pomocnika. Ma wymaganą właściwość ciągu i wywołuje zdarzenie, które jest wyświetlane przez wszystkie zarejestrowane rejestratory.

### <a name="code"></a>Code

[!code-csharp[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie pokazano plik projektu wywołujący poprzednie przykładowe zadanie, SimpleTask3.

### <a name="code"></a>Code

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

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

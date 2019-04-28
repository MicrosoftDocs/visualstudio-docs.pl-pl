---
title: Zadanie zapisywania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaf927b1049709a04d8a883615d1997e9316599e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445389"
---
# <a name="task-writing"></a>Wpisywanie zadania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadania zapewniają kod, który jest uruchamiany w procesie kompilacji. Zadania są zawarte w elementów docelowych. Bibliotekę typowych zadań jest dołączana [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], możesz również tworzyć własnych zadań. Aby uzyskać więcej informacji na temat biblioteki zadań, które są dołączone [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], zobacz [odwołanie do zadania](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Zadania  
 Przykłady zadań [kopiowania](../msbuild/copy-task.md), który kopiuje jeden lub więcej plików [MakeDir](../msbuild/makedir-task.md), co powoduje utworzenie katalogu, i [Csc](../msbuild/csc-task.md), który kompiluje [!INCLUDE[csprcs](../includes/csprcs-md.md)] pliki kodów źródłowych. Każde zadanie podrzędne jest implementowany jako klasa .NET, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w zestawie Microsoft.Build.Framework.dll.  
  
 Istnieją dwie metody, których można użyć podczas wykonywania zadania:  
  
- Implementowanie <xref:Microsoft.Build.Framework.ITask> interfejs bezpośrednio.  
  
- Pochodną klasy z klasy Pomocnika <xref:Microsoft.Build.Utilities.Task>, który jest zdefiniowany w zestawie Microsoft.Build.Utilities.dll. Zadanie implementuje ITask i zawiera domyślne implementacje niektórych członków ITask. Ponadto rejestrowanie jest łatwiejsze.  
  
  W obu przypadkach należy dodać do swojej klasy metodę o nazwie `Execute`, czyli metody, która jest wywoływana, gdy zadanie jest uruchamiane. Ta metoda nie przyjmuje żadnych parametrów i zwraca `Boolean` wartość: `true` Jeśli zadanie zakończyło się pomyślnie lub `false` Jeśli go nie powiodła się. Poniższy przykład przedstawia zadanie, które nie wykonuje żadnych działań i zwraca `true`.  
  
```  
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
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Po uruchomieniu zadania można również otrzyma dane wejściowe z pliku projektu tworzenia właściwości platformy .NET dla klasy zadania. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Ustawia właściwości bezpośrednio przed wywołaniem zadania podrzędnego `Execute` metody. Aby utworzyć właściwość ciągu, użyj kodu zadania, takie jak:  
  
```  
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
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Następujące projektu pliku uruchomienia tego zadania i zestawy `MyProperty` podanej wartości:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Rejestrowanie zadania  
 Jeśli projekt zostanie uruchomione zadanie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] musi wiedzieć, jak zlokalizować zestaw, który zawiera klasę zadania. Zadania są rejestrowane przy użyciu [usingtask — Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Plik Microsoft.Common.Tasks znajduje się plik projektu, który zawiera listę `UsingTask` elementy, które rejestrują wszystkie zadania, które są dostarczane z [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Ten plik jest automatycznie dołączane podczas tworzenia każdego projektu. Jeśli zadanie, który jest zarejestrowany w Microsoft.Common.Tasks również jest zarejestrowany w bieżącym pliku projektu, bieżący plik projektu ma pierwszeństwo przed; oznacza to, że można zastąpić domyślnego zadania przy użyciu własnych zadań, który ma taką samą nazwę.  
  
> [!TIP]
> Można wyświetlić listę zadań, które są dostarczane z [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , wyświetlając zawartość Microsoft.Common.Tasks.  
  
## <a name="raising-events-from-a-task"></a>Wywoływanie zdarzeń z zadania  
 Jeśli zadanie jest pochodną <xref:Microsoft.Build.Utilities.Task> klasy pomocnika, umożliwia dowolny z następujących metod pomocnika na <xref:Microsoft.Build.Utilities.Task> klasy, aby wywołać zdarzenia, które będą przechwytywane i wyświetlane przez dowolnego rejestratorów zarejestrowanych:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Jeśli zadanie implementuje <xref:Microsoft.Build.Framework.ITask> bezpośrednio, możesz nadal umieszczać takie zdarzenia, ale należy użyć interfejsu IBuildEngine. Poniższy przykład przedstawia zadanie, które implementuje ITask i zgłasza zdarzenie niestandardowe:  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
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
  
## <a name="requiring-task-parameters-to-be-set"></a>Parametry zadania należy ustawić wymaganie  
 Tak, aby ustawić wartości tych właściwości każdego pliku projektu, który uruchamia zadanie lub kompilacja nie powiedzie się, można oznaczyć niektórych właściwości zadania jako "required". Zastosuj `[Required]` atrybutu do właściwości platformy .NET w zadaniu w następujący sposób:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` Atrybutu jest definiowana przez <xref:Microsoft.Build.Framework.RequiredAttribute> w <xref:Microsoft.Build.Framework> przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższej [!INCLUDE[csprcs](../includes/csprcs-md.md)] klasa przedstawia zadanie pochodząca od <xref:Microsoft.Build.Utilities.Task> Klasa pomocy. To zadanie zwraca `true`, co oznacza, że udało mu się.  
  
### <a name="code"></a>Kod  
  
```  
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
 Poniższej [!INCLUDE[csprcs](../includes/csprcs-md.md)] klasy pokazano Implementowanie zadań <xref:Microsoft.Build.Framework.ITask> interfejsu. To zadanie zwraca `true`, co oznacza, że udało mu się.  
  
### <a name="code"></a>Kod  
  
```  
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
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
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
 To [!INCLUDE[csprcs](../includes/csprcs-md.md)] klasa przedstawia zadania, która pochodzi od klasy <xref:Microsoft.Build.Utilities.Task> Klasa pomocy. Ma właściwość wymagane parametry i wywołuje zdarzenie, które jest wyświetlane przez wszystkich rejestratorów zarejestrowanych.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleTask3#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs#1)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia wywoływanie poprzednie zadanie przykład SimpleTask3 pliku projektu.  
  
### <a name="code"></a>Kod  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

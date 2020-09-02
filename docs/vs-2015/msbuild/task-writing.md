---
title: Pisanie zadania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802798"
---
# <a name="task-writing"></a>Wpisywanie zadania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadania zapewniają kod, który jest uruchamiany podczas procesu kompilacji. Zadania są zawarte w obiektach docelowych. Biblioteka typowych zadań jest dołączona do programu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] i można także utworzyć własne zadania. Aby uzyskać więcej informacji na temat biblioteki zadań, które są dołączone do programu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Zadania  
 Przykłady zadań obejmują [kopię](../msbuild/copy-task.md), która kopiuje jeden lub więcej plików, [MakeDir](../msbuild/makedir-task.md), który tworzy katalog i [CSC](../msbuild/csc-task.md), który kompiluje [!INCLUDE[csprcs](../includes/csprcs-md.md)] pliki kodu źródłowego. Każde zadanie jest implementowane jako Klasa platformy .NET, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejs, który jest zdefiniowany w zestawie Microsoft.Build.Framework.dll.  
  
 Istnieją dwie metody, których można użyć podczas implementowania zadania:  
  
- Zaimplementuj <xref:Microsoft.Build.Framework.ITask> interfejs bezpośrednio.  
  
- Utwórz klasę z klasy pomocnika, <xref:Microsoft.Build.Utilities.Task> która jest zdefiniowana w zestawie Microsoft.Build.Utilities.dll. Zadanie implementuje ITask i udostępnia domyślne implementacje niektórych elementów członkowskich ITask. Ponadto rejestrowanie jest łatwiejsze.  
  
  W obu przypadkach należy dodać do klasy metodę o nazwie `Execute` , która jest wywoływana, gdy zadanie zostanie uruchomione. Ta metoda nie przyjmuje parametrów i zwraca `Boolean` wartość: `true` Jeśli zadanie zakończyło się pomyślnie lub `false` zakończyło się niepowodzeniem. Poniższy przykład pokazuje zadanie, które nie wykonuje akcji i zwraca wartość `true` .  
  
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
  
 Po uruchomieniu zadania mogą także odbierać dane wejściowe z pliku projektu, jeśli tworzysz właściwości platformy .NET dla klasy Task. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Ustawia te właściwości bezpośrednio przed wywołaniem metody zadania `Execute` . Aby utworzyć właściwość String, użyj kodu zadania, takiego jak:  
  
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
  
 Następujący plik projektu uruchamia to zadanie i ustawia `MyProperty` daną wartość:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Rejestrowanie zadań  
 Jeśli projekt będzie uruchamiał zadanie, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] należy wiedzieć, jak zlokalizować zestaw, który zawiera klasę zadania. Zadania są rejestrowane przy użyciu [elementu UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Plik Microsoft. Common. Tasks to plik projektu, który zawiera listę `UsingTask` elementów, które rejestrują wszystkie zadania, które są dostarczane z [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Ten plik jest automatycznie dołączany podczas kompilowania każdego projektu. Jeśli zadanie zarejestrowane w programie Microsoft. Common. Tasks jest również zarejestrowane w pliku bieżącego projektu, ma pierwszeństwo bieżący plik projektu. oznacza to, że można zastąpić zadanie domyślne przy użyciu własnego zadania o tej samej nazwie.  
  
> [!TIP]
> Można wyświetlić listę zadań, które są dostarczane z programem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , wyświetlając zawartość elementu Microsoft. Common. Tasks.  
  
## <a name="raising-events-from-a-task"></a>Wywoływanie zdarzeń z zadania  
 Jeśli zadanie pochodzi od <xref:Microsoft.Build.Utilities.Task> klasy pomocnika, można użyć dowolnej z następujących metod pomocnika w <xref:Microsoft.Build.Utilities.Task> klasie, aby zgłosić zdarzenia, które będą przechwytywane i wyświetlane przez wszystkie zarejestrowane rejestratory:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Jeśli zadanie zostanie zaimplementowane <xref:Microsoft.Build.Framework.ITask> bezpośrednio, można nadal zgłosić takie zdarzenia, ale należy użyć interfejsu IBuildEngine. Poniższy przykład pokazuje zadanie implementujące ITask i wywołuje zdarzenie niestandardowe:  
  
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
  
## <a name="requiring-task-parameters-to-be-set"></a>Wymaganie ustawiania parametrów zadania  
 Niektóre właściwości zadania można oznaczyć jako "wymagane", aby każdy plik projektu, który uruchomił zadanie, musiał ustawić wartości tych właściwości lub kompilacja kończy się niepowodzeniem. Zastosuj `[Required]` atrybut do właściwości .NET w zadaniu w następujący sposób:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]`Atrybut jest definiowany przez <xref:Microsoft.Build.Framework.RequiredAttribute> w <xref:Microsoft.Build.Framework> przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższej [!INCLUDE[csprcs](../includes/csprcs-md.md)] klasie przedstawiono zadanie pochodne od <xref:Microsoft.Build.Utilities.Task> klasy pomocnika. To zadanie zwraca `true` , wskazując, że zakończyło się pomyślnie.  
  
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
 W poniższej [!INCLUDE[csprcs](../includes/csprcs-md.md)] klasie przedstawiono zadanie implementujące <xref:Microsoft.Build.Framework.ITask> interfejs. To zadanie zwraca `true` , wskazując, że zakończyło się pomyślnie.  
  
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
 Ta [!INCLUDE[csprcs](../includes/csprcs-md.md)] Klasa pokazuje zadanie, które pochodzi od <xref:Microsoft.Build.Utilities.Task> klasy pomocnika. Ma ona wymaganą właściwość String i wywołuje zdarzenie, które jest wyświetlane przez wszystkie zarejestrowane rejestratory.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleTask3#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs#1)]  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono plik projektu wywołujący poprzednie przykładowe zadanie, SimpleTask3.  
  
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

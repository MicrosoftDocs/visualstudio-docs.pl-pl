---
title: 'Instrukcje: Konfigurowanie obiektów docelowych i zadań | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8ef52638858160822fcc271a53513b130afc3f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64806042"
---
# <a name="how-to-configure-targets-and-tasks"></a>Porady: konfigurowanie obiektów docelowych i zadań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wybrane zadania programu MSBuild można ustawić tak, aby były uruchamiane w środowisku, w którym są docelowe, niezależnie od środowiska komputera deweloperskiego. Na przykład w przypadku używania komputera 64-bitowego do kompilowania aplikacji, która jest przeznaczona dla architektury 32-bitowej, wybrane zadania są uruchamiane w procesie 32-bitowym.  
  
> [!NOTE]
> Jeśli zadanie kompilacji jest zapisywana w języku .NET, takim jak Visual C# lub Visual Basic, i nie korzysta z natywnych zasobów lub narzędzi, zostanie uruchomione w dowolnym kontekście docelowym bez dostosowania.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask atrybutów i parametrów zadań  
 Następujące `UsingTask` atrybuty mają wpływ na wszystkie operacje zadania w określonym procesie kompilacji:  
  
- `Runtime`Atrybut, jeśli jest obecny, ustawia wersję środowiska uruchomieniowego języka wspólnego (CLR) i może przyjmować jedną z następujących wartości: `CLR2` , `CLR4` , `CurrentRuntime` lub `*` (dowolnego środowiska uruchomieniowego).  
  
- `Architecture`Atrybut, jeśli jest obecny, ustawia platformę i bitową i może przyjmować jedną z następujących wartości: `x86` , `x64` , `CurrentArchitecture` lub `*` (dowolna architektura).  
  
- `TaskFactory`Atrybut, jeśli jest obecny, ustawia fabrykę zadań, która tworzy i uruchamia wystąpienie zadania i pobiera tylko wartość `TaskHostFactory` . Aby uzyskać więcej informacji, zobacz sekcję fabryki zadań w dalszej części tego dokumentu.  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Można również użyć `MSBuildRuntime` parametrów i, `MSBuildArchitecture` Aby ustawić kontekst docelowy pojedynczego zadania.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Przed uruchomieniem zadania przez program MSBuild szuka pasującego `UsingTask` kontekstu, który ma ten sam kontekst docelowy.  Parametry, które są określone w, `UsingTask` ale nie w odpowiadającym mu zadaniu, są uznawane za dopasowane.  Parametry określone w zadaniu, ale nie w odpowiedniej, `UsingTask` są również uznawane za dopasowane. Jeśli wartości parametrów nie są określone w `UsingTask` ani zadania, wartości domyślne to `*` (dowolny parametr).  
  
> [!WARNING]
> Jeśli istnieje więcej niż jeden `UsingTask` i wszystkie mają pasujące `TaskName` atrybuty, `Runtime` , i `Architecture` , ostatni z nich do obliczenia zastępuje pozostałe.  
  
 Jeśli w zadaniu są ustawione parametry, MSBuild próbuje znaleźć `UsingTask` , który pasuje do tych parametrów lub, co najmniej, nie jest w konflikcie z nimi.  Więcej niż jeden `UsingTask` może określać kontekst docelowy tego samego zadania.  Na przykład zadanie, które ma inne pliki wykonywalne dla różnych środowisk docelowych może wyglądać następująco:  
  
```  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>Fabryki zadań  
 Przed uruchomieniem zadania program MSBuild sprawdza, czy jest on przeznaczony do uruchomienia w bieżącym kontekście oprogramowania.  Jeśli zadanie jest oznaczone, MSBuild przekazuje go do AssemblyTaskFactory, który uruchamia go w bieżącym procesie; w przeciwnym razie MSBuild przekazuje zadanie do TaskHostFactory, które uruchamia zadanie w procesie, który jest zgodny z kontekstem docelowym. Nawet jeśli bieżący kontekst i dopasowanie kontekstu docelowego, można wymusić uruchamianie pozaprocesowe zadania (na potrzeby izolacji, zabezpieczeń lub innych powodów) przez ustawienie wartości `TaskFactory` `TaskHostFactory` .  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Fantom — parametry zadania  
 Podobnie jak w przypadku innych parametrów zadania `MSBuildRuntime` i `MSBuildArchitecture` można je ustawić na podstawie właściwości kompilacji.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 W przeciwieństwie do innych parametrów zadania `MSBuildRuntime` i `MSBuildArchitecture` nie są widoczne dla samego zadania.  Aby napisać zadanie, które jest świadome kontekstu, w którym działa, należy przetestować kontekst przez wywołanie .NET Framework lub użyć właściwości kompilacji, aby przekazać informacje kontekstowe za pomocą innych parametrów zadań.  
  
> [!NOTE]
> `UsingTask` atrybuty można ustawić na podstawie właściwości zestawu narzędzi i środowiska.  
  
 `MSBuildRuntime`Parametry i `MSBuildArchitecture` zapewniają największą elastyczność sposobu ustawiania kontekstu docelowego, ale również z największą ograniczoną zakresem.  Z jednej strony, ponieważ są one ustawiane w wystąpieniu zadania i nie są oceniane do momentu uruchomienia zadania, mogą uzyskać wartość z pełnego zakresu właściwości dostępnych zarówno w czasie oceny, jak i w czasie kompilacji.  Z drugiej strony te parametry dotyczą tylko określonego wystąpienia zadania w konkretnym miejscu docelowym.  
  
> [!NOTE]
> Parametry zadań są oceniane w kontekście węzła nadrzędnego, a nie w kontekście hosta zadania. Zmienne środowiskowe, które są zależne od architektury (takie jak lokalizacja plików programu), będą oceniane do wartości zgodnej z węzłem nadrzędnym.  Jeśli jednak ta sama zmienna środowiskowa jest odczytywana bezpośrednio przez zadanie, zostanie ona prawidłowo oceniona w kontekście hosta zadania.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie obiektów docelowych i zadań](../msbuild/configuring-targets-and-tasks.md)

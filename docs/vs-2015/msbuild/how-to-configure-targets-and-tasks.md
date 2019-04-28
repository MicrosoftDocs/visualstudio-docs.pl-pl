---
title: 'Instrukcje: Konfigurowanie obiektów docelowych i zadań | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440050"
---
# <a name="how-to-configure-targets-and-tasks"></a>Instrukcje: Konfigurowanie obiektów docelowych i zadań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można ustawić wybranych zadań programu MSBuild do uruchamiania w środowisku, docelowych, niezależnie od środowiska na komputerze deweloperskim. Na przykład gdy używasz 64-bitowy komputer do tworzenia aplikacji w danej architekturze celów 32-bitowa wybranych zadań są uruchamiane w procesie 32-bitowym.  
  
> [!NOTE]
> Jeśli zadanie kompilacji są zapisywane w języku .NET, takich jak Visual C# lub Visual Basic, a nie korzysta z zasobów natywnych ani narzędzia, a następnie uruchomi się w dowolnym kontekście docelowej bez dostosowania.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask atrybuty i parametry zadania  
 Następujące `UsingTask` atrybuty mają wpływ na wszystkie operacje zadań w procesie konkretnej kompilacji:  
  
- `Runtime` Atrybutu, jeśli jest obecny, ustawia typowe wersję środowiska uruchomieniowego języka (wspólnego CLR) i można wykonać dowolną z następujących wartości: `CLR2`, `CLR4`, `CurrentRuntime`, lub `*` (wszystkie środowiska wykonawczego).  
  
- `Architecture` Atrybutu, jeśli jest obecny, ustawia platformy i liczbę bitów i może mieć jedną z następujących wartości: `x86`, `x64`, `CurrentArchitecture`, lub `*` (dowolnej architekturze).  
  
- `TaskFactory` Atrybut, jeśli jest obecny, ustawia fabryki zadań, które tworzy i uruchamia wystąpienie zadania i przyjmuje tylko wartość `TaskHostFactory`. Aby uzyskać więcej informacji zobacz sekcję fabryki zadań w dalszej części tego dokumentu.  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Można również użyć `MSBuildRuntime` i `MSBuildArchitecture` parametry, aby ustawić kontekst docelowy pojedynczego zadania.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Zanim program MSBuild uruchamia zadanie, szuka pasujący obiekt typu `UsingTask` ma ten sam kontekst docelowego.  Parametry, które są określone w `UsingTask` , ale w odpowiedniego zadania nie są traktowane jako do dopasowania.  Parametry, które są określone w zadaniu, ale nie znajduje się w odpowiednich `UsingTask` również pełnią funkcję do dopasowania. Jeśli nie określono wartości parametrów albo `UsingTask` lub zadania, wartości domyślne, aby `*` (żadnych parametrów).  
  
> [!WARNING]
> Jeśli istnieje więcej niż jedna `UsingTask` istnieje i wszystkie dopasowania `TaskName`, `Runtime`, i `Architecture` atrybutów, ostatni z nich ma zostać obliczone zastępuje inne.  
  
 Jeśli parametry są skonfigurowane na zadanie, program MSBuild próbuje znaleźć `UsingTask` , który pasuje do tych parametrów lub, co najmniej jest nie konflikcie z nich.  Więcej niż jeden `UsingTask` można określić kontekstu docelowych tego samego zadania.  Na przykład zadanie, które ma różne pliki wykonywalne w środowiskach inny element docelowy może wyglądać to:  
  
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
 Przed uruchomieniem zadania, program MSBuild sprawdza, czy jest wyznaczone do uruchamiania w bieżącym kontekście oprogramowania.  Jeśli wyznaczona zadanie MSBuild przekazuje go do AssemblyTaskFactory, który uruchamia go w bieżącym procesie; w przeciwnym razie program MSBuild przekazuje TaskHostFactory, który uruchamia zadanie w procesie, który pasuje do kontekstu docelowego zadania. Nawet wtedy, gdy bieżący kontekst i kontekst docelowej są zgodne, możesz wymusić uruchomienie zadania poza procesem (w przypadku izolacji, zabezpieczeń lub innych powodów), ustawiając `TaskFactory` do `TaskHostFactory`.  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Parametry zadania fantomu  
 Wszystkie inne parametry zadania, takie jak `MSBuildRuntime` i `MSBuildArchitecture` można ustawić właściwości kompilacji.  
  
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
  
 W przeciwieństwie do innych parametrów zadania `MSBuildRuntime` i `MSBuildArchitecture` nie są widoczne dla samo zadanie.  Aby napisać zadanie, które ma informacje o kontekście, w której jest uruchamiany, musisz przetestować kontekst przez wywołanie metody .NET Framework lub przekazać informacje o kontekście za pośrednictwem innych parametrów zadania przy użyciu właściwości kompilacji.  
  
> [!NOTE]
> `UsingTask` atrybuty mogą zostać ustawione przy użyciu właściwości zestawu narzędzi i środowiska.  
  
 `MSBuildRuntime` i `MSBuildArchitecture` parametry zawierają najbardziej elastyczny sposób, aby ustawić kontekst target, ale także najbardziej ograniczone w zakresie.  Z jednej strony ponieważ są ustawione na samego wystąpienia zadania i nie są sprawdzane, dopóki zadanie zostanie uruchomiony, można uzyskać wartości z pełnego zakresu właściwości dostępne w czasie kompilacji i czas oceny.  Z drugiej strony parametry te dotyczą tylko konkretne wystąpienie zadania w określonej lokalizacji docelowej.  
  
> [!NOTE]
> Parametry zadania są oceniane w kontekście węzła nadrzędnego, a nie w kontekście hosta zadań. Zmienne środowiskowe, które są zależne środowiska uruchomieniowego lub architektura, które (takie jak lokalizacja plików programu) będzie zwrócić wartość, która pasuje do węzła nadrzędnego.  Jednak jeśli ten sam zmienna środowiskowa jest odczytywana bezpośrednio przez zadanie, zostanie prawidłowo ono ocenione w ramach hosta zadań.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie obiektów docelowych i zadań](../msbuild/configuring-targets-and-tasks.md)

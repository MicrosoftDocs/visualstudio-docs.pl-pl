---
title: 'Jak: Konfigurowanie obiektów docelowych i zadań | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe2955feb50a28e5ba631cdeddd169973a42ed25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633892"
---
# <a name="how-to-configure-targets-and-tasks"></a>Jak: Konfigurowanie obiektów docelowych i zadań

Wybrane zadania MSBuild można ustawić do uruchamiania w środowisku, które są kierowane, niezależnie od środowiska komputera deweloperskiego. Na przykład podczas tworzenia aplikacji przeznaczonej dla architektury 32-bitowej za pomocą komputera 64-bitowego wybrane zadania są uruchamiane w procesie 32-bitowym.
Wybrane zadania MSBuild można ustawić do uruchamiania w środowisku, które są kierowane, niezależnie od środowiska komputera deweloperskiego. Na przykład podczas tworzenia aplikacji przeznaczonej dla architektury 32-bitowej za pomocą komputera 64-bitowego wybrane zadania są uruchamiane w procesie 32-bitowym.

> [!NOTE]
> Jeśli zadanie kompilacji jest napisane w języku .NET, takich jak Visual C# lub Visual Basic i nie używa zasobów natywnych lub narzędzi, a następnie będzie działać w dowolnym kontekście docelowym bez adaptacji.

## <a name="usingtask-attributes-and-task-parameters"></a>Używanie atrybutów i parametrów zadania

Następujące `UsingTask` atrybuty wpływają na wszystkie operacje zadania w określonym procesie kompilacji:

- `Runtime` Atrybut, jeśli jest obecny, ustawia wersję środowiska wykonawczego języka wspólnego (CLR) i `CLR2` `CLR4`może `CurrentRuntime`przyjmować dowolną z następujących wartości: , , , lub `*` (dowolne środowisko wykonawcze).

- Atrybut, `Architecture` jeśli jest obecny, ustawia platformę i bitness i może `x86` `x64`przyjąć `CurrentArchitecture`jedną `*` z tych wartości: , , , lub (dowolna architektura).

- Atrybut, `TaskFactory` jeśli jest obecny, ustawia fabrykę zadań, która tworzy i `TaskHostFactory`uruchamia wystąpienie zadania, i przyjmuje tylko wartość . Aby uzyskać więcej informacji, zobacz [Fabryki zadań](#task-factories) w dalszej części tego dokumentu.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

Można również użyć `MSBuildRuntime` `MSBuildArchitecture` parametrów i, aby ustawić docelowy kontekst pojedynczego zadania.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

Przed MSBuild uruchamia zadanie, szuka `UsingTask` dopasowania, który ma ten sam kontekst docelowy. Parametry, które są `UsingTask` określone w, ale nie w odpowiednim zadaniu są uważane za dopasowane. Parametry, które określono w zadaniu, ale nie w odpowiednim `UsingTask` są również uważane za dopasowane. Jeśli wartości parametrów nie są `UsingTask` określone w zadaniu `*` lub zadaniu, wartości domyślnie (dowolny parametr).

> [!WARNING]
> Jeśli istnieje `UsingTask` więcej niż jeden `TaskName`i `Runtime`wszystkie `Architecture` mają pasujące , i atrybuty, ostatni do oceny zastępuje pozostałe.

 Jeśli parametry są ustawione na zadanie, MSBuild próbuje `UsingTask` znaleźć, który pasuje do tych parametrów lub, przynajmniej, nie jest w konflikcie z nimi. Więcej niż `UsingTask` jeden można określić kontekst docelowy tego samego zadania. Na przykład zadanie, które ma różne pliki wykonywalne dla różnych środowisk docelowych może przypominać to zadanie:

```xml
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

Przed uruchomieniem zadania, MSBuild sprawdza, czy jest wyznaczony do uruchomienia w bieżącym kontekście oprogramowania. Jeśli zadanie jest tak wyznaczone, MSBuild przekazuje go do AssemblyTaskFactory, który uruchamia go w bieżącym procesie; w przeciwnym razie MSBuild przekazuje zadanie do TaskHostFactory, który uruchamia zadanie w procesie, który pasuje do kontekstu docelowego. Nawet jeśli bieżący kontekst i kontekst docelowy są zgodne, można wymusić zadanie, aby uruchomić poza `TaskFactory` procesem `TaskHostFactory`(dla izolacji, zabezpieczeń lub innych powodów), ustawiając na .

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>Parametry zadania fantomu

Podobnie jak inne `MSBuildRuntime` parametry `MSBuildArchitecture` zadania i można ustawić z właściwości kompilacji.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <FrameworkVersion>3.0</FrameworkVersion>
    </PropertyGroup>
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

W przeciwieństwie do `MSBuildRuntime` `MSBuildArchitecture` innych parametrów zadania i nie są widoczne dla samego zadania. Aby napisać zadanie, które jest świadomy kontekstu, w którym jest uruchamiany, należy przetestować kontekst, wywołując .NET Framework lub użyć właściwości kompilacji, aby przekazać informacje kontekstu za pośrednictwem innych parametrów zadania.

> [!NOTE]
> `UsingTask`atrybuty można ustawić z zestawu narzędzi i właściwości środowiska.

Parametry `MSBuildRuntime` `MSBuildArchitecture` i zapewniają najbardziej elastyczny sposób ustawiania kontekstu docelowego, ale także najbardziej ograniczony zakres. Z jednej strony, ponieważ są one ustawione na wystąpienie zadania, które się i nie są oceniane, dopóki zadanie ma się uruchomić, mogą czerpać swoją wartość z pełnego zakresu właściwości dostępnych zarówno w czasie oceny, jak i w czasie kompilacji. Z drugiej strony te parametry dotyczą tylko określonego wystąpienia zadania w określonym celu.

> [!NOTE]
> Parametry zadania są oceniane w kontekście węzła nadrzędnego, a nie w kontekście hosta zadań. Zmienne środowiskowe zależne od środowiska wykonawczego lub architektury (takie jak lokalizacja *Pliki programu)* będą oceniać wartość odpowiadającą węzłowi nadrzędnemu. Jeśli jednak ta sama zmienna środowiskowa jest odczytywana bezpośrednio przez zadanie, zostanie poprawnie oceniona w kontekście hosta zadań.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie obiektów docelowych i zadań](../msbuild/configuring-targets-and-tasks.md)

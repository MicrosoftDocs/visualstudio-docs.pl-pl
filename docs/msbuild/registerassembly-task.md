---
title: RegisterAssembly — — zadanie | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c95606a00e86ffd187162e444f2c710c5cc3a0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632891"
---
# <a name="registerassembly-task"></a>RegisterAssembly — zadanie

Odczytuje metadane w określonym zestawie i dodaje niezbędne wpisy do rejestru, co umożliwia klientom COM tworzenie klas .NET Framework przezroczystie. Zachowanie tego zadania jest podobne, ale nie identyczne, z [Regasm.exe (Narzędzie rejestracji zestawów)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool).

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `RegisterAssembly` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Assemblies`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa zestawy, które mają być zarejestrowane w modelu COM.|
|`AssemblyListFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Zawiera informacje o stanie między `RegisterAssembly` zadaniem a zadaniem [UnregisterAssembly —](../msbuild/unregisterassembly-task.md) . Te informacje uniemożliwiają `UnregisterAssembly` podjęcie próby wyrejestrowania zestawu, którego nie udało się zarejestrować w `RegisterAssembly` zadaniu.|
|`CreateCodeBase`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , program tworzy wpis codebase w rejestrze, który określa ścieżkę pliku dla zestawu, który nie jest zainstalowany w globalnej pamięci podręcznej zestawów. Nie należy określać tej opcji, jeśli później instalowany będzie zestaw, który jest rejestrowany w globalnej pamięci podręcznej zestawów.|
|`TypeLibFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa bibliotekę typów do wygenerowania na podstawie określonego zestawu. Wygenerowana biblioteka typów zawiera definicje dostępnych typów zdefiniowanych w ramach zestawu. Biblioteka typów jest generowana tylko wtedy, gdy spełniony jest jeden z następujących warunków:<br /><br /> -Biblioteka typów o tej nazwie nie istnieje w tej lokalizacji.<br />-Istnieje biblioteka typów, ale jest ona starsza niż przekazanie zestawu.<br /><br /> Jeśli biblioteka typów jest nowsza niż przekazanie zestawu, nowy element nie zostanie utworzony, ale zestaw nadal będzie zarejestrowany.<br /><br /> Jeśli ten parametr jest określony, musi mieć taką samą liczbę elementów jak `Assemblies` parametr lub zadanie zakończy się niepowodzeniem. Jeśli żadne dane wejściowe nie są określone, zadanie zostanie domyślnie przyłączone do nazwy zestawu i zmienione rozszerzenie elementu na *. tlb*.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 W poniższym przykładzie za pomocą `RegisterAssembly` zadania zarejestrowano zestaw określony przez `MyAssemblies` kolekcję elementów.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyAssemblies Include="MyAssembly.dll" />
    <ItemGroup>

    <Target Name="RegisterAssemblies">
        <RegisterAssembly
            Assemblies="@(MyAssemblies)" >
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

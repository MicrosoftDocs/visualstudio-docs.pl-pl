---
title: Zadanie rejestracji | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632891"
---
# <a name="registerassembly-task"></a>RegisterAssembly — zadanie

Odczytuje metadane w określonym zestawie i dodaje niezbędne wpisy do rejestru, co umożliwia klientom COM tworzenie klas .NET Framework w sposób przejrzysty. Zachowanie tego zadania jest podobne, ale nie identyczne z [zachowaniem programu Regasm.exe (narzędzie Rejestracja zestawu).](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)

## <a name="parameters"></a>Parametry

 W poniższej tabeli `RegisterAssembly` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Assemblies`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa zestawy, które mają być zarejestrowane w COM.|
|`AssemblyListFile`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Zawiera informacje o stanie `RegisterAssembly` między zadaniem a zadaniem [Wyrejestrowania.](../msbuild/unregisterassembly-task.md) Te informacje uniemożliwiają `UnregisterAssembly` zadanie wyrejestrowania zestawu, którego nie `RegisterAssembly` można zarejestrować w zadaniu.|
|`CreateCodeBase`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program , tworzy wpis bazy kodu w rejestrze, który określa ścieżkę pliku dla zestawu, który nie jest zainstalowany w globalnej pamięci podręcznej zestawów. Nie należy określać tej opcji, jeśli później instalowany będzie zestaw, który jest rejestrowany w globalnej pamięci podręcznej zestawów.|
|`TypeLibFiles`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Określa bibliotekę typów do wygenerowania z określonego złożenia. Wygenerowana biblioteka typów zawiera definicje dostępnych typów zdefiniowanych w zestawie. Biblioteka typów jest generowana tylko wtedy, gdy spełniony jest jeden z następujących warunków:<br /><br /> - Biblioteka typów o tej nazwie nie istnieje w tej lokalizacji.<br />- Istnieje biblioteka typów, ale jest starsza niż zespół przekazywany.<br /><br /> Jeśli biblioteka typów jest nowsza niż zestaw przekazywany, nowy nie zostanie utworzony, ale zestaw będzie nadal zarejestrowany.<br /><br /> Jeśli ten parametr jest określony, musi mieć taką `Assemblies` samą liczbę elementów jak parametr lub zadanie zakończy się niepowodzeniem. Jeśli nie określono żadnych danych wejściowych, zadanie domyślnie będzie nazywać się zestawem i zmieni rozszerzenie elementu na *.tlb*.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 W poniższym przykładzie `RegisterAssembly` użyto zadania do `MyAssemblies` zarejestrowania zestawu określonego przez kolekcję towarów.

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

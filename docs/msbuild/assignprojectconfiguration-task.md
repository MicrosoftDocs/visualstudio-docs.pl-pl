---
title: AssignProjectConfiguration, zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bc9fb3ab600c106d762d5f4ec55b6bc7117e101
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635491"
---
# <a name="assignprojectconfiguration-task"></a>Assignprojectconfiguration — zadanie
To zadanie akceptuje ciągi konfiguracji listy i przypisuje je do określonych projektów.

## <a name="task-parameters"></a>Parametry zadania
 W poniższej tabeli opisano parametry `AssignProjectConfiguration` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`SolutionConfigurationContents`|Opcjonalnie `string` parametr wyjściowy.<br /><br /> Zawiera ciąg znaków XML zawierający konfigurację projektu dla każdego projektu. Konfiguracje są przypisywane do nazwanych projektów.|
|`DefaultToVcxPlatformMapping`|Opcjonalnie `string` parametr wyjściowy.<br /><br /> Zawiera rozdzieloną średnikami listę mapowań od nazw używanych przez większość typów do tych używanych przez platform *.vcxproj* plików.<br /><br /> Na przykład:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Optional<br /><br /> `string` Parametr wyjściowy.<br /><br /> Zawiera rozdzieloną średnikami listę mapowań z *.vcxproj* nazw platform do nazw platform użycia przez większość typów.<br /><br /> Na przykład:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Opcjonalnie `string` parametr wyjściowy.<br /><br /> Zawiera konfigurację dla bieżącego projektu.|
|`CurrentProjectPlatform`|Opcjonalnie `string` parametr wyjściowy.<br /><br /> Zawiera platformę dla bieżącego projektu.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Opcjonalnie `bool` parametr wyjściowy.<br /><br /> Zawiera flagę wskazującą, czy odwołania powinny być tworzone, nawet jeśli zostały wyłączone w konfiguracji projektu.|
|`ShouldUnsetParentConfigurationAndPlatform`|Opcjonalnie `bool` parametr wyjściowy.<br /><br /> Zawiera flagę wskazującą, jeśli konfiguracja nadrzędna i platforma powinny być nieustalone.|
|`OutputType`|Opcjonalnie `string` parametr wyjściowy.<br /><br /> Zawiera typ danych wyjściowych dla projektu.|
|`ResolveConfigurationPlatformUsingMappings`|Opcjonalnie `bool` parametr wyjściowy.<br /><br /> Zawiera flagę wskazującą, jeśli kompilacja powinna używać domyślnego mapowania do rozpoznawania konfiguracji i platformy przekazanych w odwołaniach projektu.|
|`AssignedProjects`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę ścieżek rozpoznanych odwołań.|
|`UnassignedProjects`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera listę elementów odniesienia projektu, których nie można rozpoznać przy użyciu wstępnie rozpoznanej listy wyników.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
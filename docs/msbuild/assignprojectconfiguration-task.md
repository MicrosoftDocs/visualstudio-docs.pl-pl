---
title: Zadanie konfiguracji assignproject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5159b73058c73c925cae644c2e3ddd2bc84ac41
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634555"
---
# <a name="assignprojectconfiguration-task"></a>Zadanie konfiguracji assignproject

To zadanie akceptuje ciągi konfiguracji listy i przypisuje je do określonych projektów.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli `AssignProjectConfiguration` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`SolutionConfigurationContents`|Opcjonalny parametr wyjściowy. `string`<br /><br /> Zawiera ciąg XML zawierający konfigurację projektu dla każdego projektu. Konfiguracje są przypisane do nazwanych projektów.|
|`DefaultToVcxPlatformMapping`|Opcjonalny parametr wyjściowy. `string`<br /><br /> Zawiera listę mapowań rozdzielanych średnikami z nazw platform używanych przez większość typów do tych używanych przez pliki *.vcxproj.*<br /><br /> Przykład:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Optional (Opcjonalność)<br /><br /> `string`parametru wyjściowego.<br /><br /> Zawiera listę mapowań rozdzielanych średnikami z nazw platform *.vcxproj* do nazw platform używanych przez większość typów.<br /><br /> Przykład:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Opcjonalny parametr wyjściowy. `string`<br /><br /> Zawiera konfigurację dla bieżącego projektu.|
|`CurrentProjectPlatform`|Opcjonalny parametr wyjściowy. `string`<br /><br /> Zawiera platformę dla bieżącego projektu.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Opcjonalny parametr wyjściowy. `bool`<br /><br /> Zawiera flagę wskazującą, że odwołania powinny być tworzone, nawet jeśli zostały wyłączone w konfiguracji projektu.|
|`ShouldUnsetParentConfigurationAndPlatform`|Opcjonalny parametr wyjściowy. `bool`<br /><br /> Zawiera flagę wskazującą, czy konfiguracja nadrzędna i platforma powinna zostać unset.|
|`OutputType`|Opcjonalny parametr wyjściowy. `string`<br /><br /> Zawiera typ danych wyjściowych dla projektu.|
|`ResolveConfigurationPlatformUsingMappings`|Opcjonalny parametr wyjściowy. `bool`<br /><br /> Zawiera flagę wskazującą, czy kompilacja powinna używać mapowań domyślnych w celu rozwiązania konfiguracji i platformy przekazanych w odwołaniach do projektu.|
|`AssignedProjects`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera listę rozwiązanych ścieżek referencyjnych.|
|`UnassignedProjects`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem> `[]`<br /><br /> Zawiera listę elementów odwołania do projektu, których nie można rozpoznać przy użyciu wstępnie rozpoznanej listy wyjść.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

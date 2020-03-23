---
title: Generowanie zadaniaTrustInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e84007c9a10618c6d757a36debe58c272302fa3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634035"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo — zadanie

Generuje zaufanie aplikacji z manifestu podstawowego `TargetZone` `ExcludedPermissions` oraz z i parametrów.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `GenerateTrustInfo` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationDependencies`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa zestawy zależne.|
|`BaseManifest`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa manifest podstawowy do generowania zaufania aplikacji.|
|`ExcludedPermissions`|Parametr `String` opcjonalny.<br /><br /> Określa jedną lub więcej wartości tożsamości uprawnień oddzielonych średnikami, które mają zostać wykluczone z domyślnego zestawu uprawnień strefy.|
|`TargetZone`|Parametr `String` opcjonalny.<br /><br /> Określa domyślny zestaw uprawnień strefy, który jest uzyskiwany z zasad komputera.|
|`TrustInfoFile`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa plik zawierający informacje o zaufaniu zabezpieczeń aplikacji.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
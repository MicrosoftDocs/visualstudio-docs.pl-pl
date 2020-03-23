---
title: UpdateManifest Zadanie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25e410ba3122e0065f92186195ee5a82d6a55c2f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631345"
---
# <a name="updatemanifest-task"></a>UpdateManifest — zadanie

Aktualizuje wybrane właściwości w manifeście i rezygnuje.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `UpdateManifest` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationManifest`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa manifest aplikacji.|
|`ApplicationPath`|Wymagany parametr interfejsu `String`.<br /><br /> Określa ścieżkę manifestu aplikacji.|
|`InputManifest`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa manifest do aktualizacji.|
|`OutputManifest`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Określa manifest zawierający zaktualizowane właściwości.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Utilities.Task> zadanie dziedziczy parametry z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [Klasa podstawowa zadania](../msbuild/task-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
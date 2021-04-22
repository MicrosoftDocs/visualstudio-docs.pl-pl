---
title: Dostosowywanie plików projektu utworzonych za pomocą interfejsu VSTU | Microsoft Docs
description: Dowiedz się, jak dostosować pliki projektu utworzone przez Visual Studio Tools for Unity (VSTU). Zapoznaj się z przykładem kodu w języku C#.
ms.custom: ''
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a4a5973863877db2d071f9be8d4689928b21a689
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879320"
---
# <a name="customize-project-files-created-by-vstu"></a>Dostosowywanie plików projektu utworzonych przez vstu
Unity udostępnia wywołania zwrotne podczas generowania pliku projektu. Zaim implementuj metody i przy użyciu metody , aby modyfikować projekt lub `OnGeneratedSlnSolution` plik rozwiązania przy każdym jego `OnGeneratedCSProject` [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) wygenerowaniu.

## <a name="demonstrates"></a>Demonstracje
Dostosowywanie plików Visual Studio generowanych przez Visual Studio Tools for Unity.

## <a name="example"></a>Przykład

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```

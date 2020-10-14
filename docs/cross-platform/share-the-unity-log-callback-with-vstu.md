---
title: Udostępnianie wywołania zwrotnego dziennika aparatu Unity za pomocą rozszerzenia VSTU | Microsoft Docs
description: Udostępnij swoje wywołanie zwrotne dziennika aparatu Unity z tą, która jest zarejestrowana w Visual Studio Tools for Unity (rozszerzenia VSTU) w celu przesyłania strumieniowego swojej konsoli do programu Visual Studio.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 88abc27ad757487ae8f65b8bbb66d4dfee9791cc
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039875"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika aparatu Unity z rozszerzenia VSTU
Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika za pomocą aparatu Unity, aby móc przesyłać strumieniowo swoją konsolę do programu Visual Studio. Jeśli skrypty edytora rejestrują także wywołanie zwrotne dziennika za pomocą aparatu Unity, wywołanie zwrotne rozszerzenia VSTU może zakłócać wywołanie zwrotne. Aby zapobiec tej możliwości, użyj `VisualStudioIntegration.LogCallback` zdarzenia do współpracy z rozszerzenia VSTU.

## <a name="demonstrates"></a>Demonstracje
 Jak udostępnić wywołanie zwrotne dziennika aparatu Unity utworzone przez Visual Studio Tools for Unity.

## <a name="example"></a>Przykład

```csharp
#if ENABLE_VSTU
using System;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class LogCallbackHook
{
    static LogCallbackHook()
    {
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>
        {
            // place code that implements your log callback here
        };
    }
}
#endif
```

## <a name="see-also"></a>Zobacz także
 [Przykład: generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md)

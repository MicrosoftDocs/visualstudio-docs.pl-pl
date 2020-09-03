---
title: Udostępnianie wywołania zwrotnego dziennika aparatu Unity za pomocą rozszerzenia VSTU | Microsoft Docs
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
ms.openlocfilehash: dc54c51f078e5b800a9cc9f2de687db7b1fa0387
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815047"
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

## <a name="see-also"></a>Zobacz też
 [Przykład: generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md)

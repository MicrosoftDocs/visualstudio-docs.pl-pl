---
title: Udostępnianie wywołania zwrotnego dziennika unity za pomocą usługi VSTU | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: aa8a4a229102a6a9439ffb36582cd03e322a086b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62815668"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika Unity za pomocą usługi VSTU
Narzędzia programu Visual Studio dla unity rejestruje wywołania zwrotnego dziennika z Unity, aby móc przesyłać strumieniowo jego konsoli do programu Visual Studio. Jeśli skrypty edytora również zarejestrować wywołania zwrotnego dziennika z Unity, wywołania zwrotnego VSTU może zakłócać wywołanie zwrotne. Aby zapobiec tej możliwości, `VisualStudioIntegration.LogCallback` należy użyć zdarzenia do współpracy z VSTU.

## <a name="demonstrates"></a>Demonstracje
 Jak udostępnić wywołanie zwrotne dziennika unity utworzone przez narzędzia programu Visual Studio dla unity.

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
 [Przykład: Generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md)

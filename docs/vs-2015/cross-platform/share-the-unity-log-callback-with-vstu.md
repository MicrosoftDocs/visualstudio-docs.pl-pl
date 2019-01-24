---
title: Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 5e4fcfdc35e9329429421fd03a941e611e6b5b8f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54789172"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika środowiska Unity za pomocą rozszerzenia VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika przy użyciu aparatu Unity, aby móc przesyłać strumieniowo jego konsoli w programie Visual Studio. Edytor skryptów również zarejestrować wywołanie zwrotne dziennika przy użyciu aparatu Unity, wywołanie zwrotne w narzędziach VSTU może zakłócać wywołanie zwrotne. Aby zapobiec tej możliwości, użyj `VisualStudioIntegration.LogCallback` zdarzenie, aby współpracować za pomocą rozszerzenia VSTU.  
  
## <a name="demonstrates"></a>Demonstracje  
 Jak udostępnić wywołania zwrotnego dziennika środowiska Unity, które zostały utworzone przez program Visual Studio Tools for Unity.  
  
## <a name="example"></a>Przykład  
  
```csharp  
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
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykład: Generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md)

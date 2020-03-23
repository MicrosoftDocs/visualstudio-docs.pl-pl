---
title: Dostosowywanie plików projektu utworzonych przez VSTU | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: ad52e9f97dfbb9a5d0b3d65085c6c2627ccb2232
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62819532"
---
# <a name="customize-project-files-created-by-vstu"></a>Dostosowywanie plików projektu utworzonych przez usługę VSTU
Visual Studio Tools for Unity zapewnia wywołania zwrotnego w stylu Unity podczas generowania pliku projektu. Zarejestruj się `VisualStudioIntegration.ProjectFileGeneration` w zdarzeniu, aby zmodyfikować plik projektu za każdym razem, gdy jest generowany ponownie.

## <a name="demonstrates"></a>Demonstracje
 Jak dostosować pliki projektu programu Visual Studio generowane przez narzędzia programu Visual Studio dla unity.

## <a name="example"></a>Przykład

```csharp
#if ENABLE_VSTU
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
#endif
```

## <a name="see-also"></a>Zobacz też
 [Przykład: wywołanie zwrotne dziennika](../cross-platform/share-the-unity-log-callback-with-vstu.md)

---
title: Dostosowywanie plików projektu utworzonych za pomocą rozszerzenia VSTU | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62819532"
---
# <a name="customize-project-files-created-by-vstu"></a>Dostosowywanie plików projektu utworzonych za pomocą rozszerzenia VSTU
Visual Studio Tools for Unity zapewnia wywołanie zwrotne stylu aparatu Unity w trakcie Generowanie pliku projektu. Zarejestrowanie `VisualStudioIntegration.ProjectFileGeneration` zdarzenia w celu zmodyfikowania pliku projektu, zawsze wtedy, gdy zostanie ponownie wygenerowany.

## <a name="demonstrates"></a>Demonstracje
 Jak dostosowywanie plików projektu programu Visual Studio, które są generowane przez program Visual Studio Tools for Unity.

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

## <a name="see-also"></a>Zobacz także
 [Przykład: Wywołanie zwrotne dziennika](../cross-platform/share-the-unity-log-callback-with-vstu.md)

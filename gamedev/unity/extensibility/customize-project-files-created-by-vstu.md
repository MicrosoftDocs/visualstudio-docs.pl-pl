---
title: Dostosowywanie plików projektu utworzonych przez rozszerzenia VSTU | Microsoft Docs
description: Dowiedz się, jak dostosować pliki projektu utworzone przez Visual Studio Tools for Unity (rozszerzenia VSTU). Zapoznaj się z przykładem kodu w języku C#.
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 071dc7a9f12dcfeb5fff9e59bbbf34dc64f61cf5
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341873"
---
# <a name="customize-project-files-created-by-vstu"></a>Dostosowywanie plików projektu utworzonych przez rozszerzenia VSTU
Visual Studio Tools for Unity zapewnia wywołanie zwrotne w stylu aparatu Unity podczas generowania pliku projektu. Zarejestruj się w `VisualStudioIntegration.ProjectFileGeneration` zdarzeniu, aby zmodyfikować plik projektu za każdym razem, gdy zostanie on ponownie wygenerowany.

## <a name="demonstrates"></a>Demonstracje
 Jak dostosować pliki projektu programu Visual Studio wygenerowane przez Visual Studio Tools for Unity.

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
 [Przykład: wywołanie zwrotne dziennika](/cross-platform/share-the-unity-log-callback-with-vstu.md)

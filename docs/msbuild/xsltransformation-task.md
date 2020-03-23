---
title: Zadanie XslTransformation | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d23799e5ce5bf391915ac459c69c27b990211f0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094543"
---
# <a name="xsltransformation-task"></a>XslTransformation — zadanie

Przekształca dane wejściowe XML przy użyciu XSLT lub skompilowanego XSLT i wyprowadza do urządzenia wyjściowego lub pliku.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `XslTransformation` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`OutputPaths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki wyjściowe transformacji XML.|
|`Parameters`|Parametr `String` opcjonalny.<br /><br /> Określa parametry dokumentu wejścia XSLT.  Podaj nieprzetworzony `<Parameter Name="" Value="" Namespace="" />`kod XML, który przechowuje każdy parametr jako .|
|`XmlContent`|Parametr `String` opcjonalny.<br /><br /> Określa dane wejściowe XML jako ciąg.|
|`XmlInputPaths`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.<br /><br /> Określa pliki wejściowe XML.|
|`XslCompiledDllPath`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa skompilowany XSLT.|
|`XslContent`|Parametr `String` opcjonalny.<br /><br /> Określa dane wejściowe XSLT jako ciąg.|
|`XslInputPath`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny.<br /><br /> Określa plik wejściowy XSLT.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to <xref:Microsoft.Build.Tasks.TaskExtension> zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy, która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie do modyfikowania pliku `$(XmlInputFileName)`xml jest używany plik transformowania XSL.xslt . *transform.xslt* Przekształcony kod XML `$(IntermediateOutputPath)output.xml`jest zapisywany w pliku . Transformacja XSL `$(Parameter1)` przyjmuje jako parametr wejściowy.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Zobacz też

- [Parametry XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

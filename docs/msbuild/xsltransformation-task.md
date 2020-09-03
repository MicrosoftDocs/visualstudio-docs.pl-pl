---
title: XslTransformation — — zadanie | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094543"
---
# <a name="xsltransformation-task"></a>XslTransformation — zadanie

Przekształca dane wejściowe XML przy użyciu XSLT lub skompilowanego XSLT i wyjść do urządzenia wyjściowego lub pliku.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `XslTransformation` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`OutputPaths`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Określa pliki wyjściowe transformacji XML.|
|`Parameters`|Opcjonalny `String` parametr.<br /><br /> Określa parametry dokumentu wejściowego XSLT.  Podaj nieprzetworzony kod XML, który przechowuje każdy parametr jako `<Parameter Name="" Value="" Namespace="" />` .|
|`XmlContent`|Opcjonalny `String` parametr.<br /><br /> Określa dane wejściowe w formacie XML jako ciąg.|
|`XmlInputPaths`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa pliki wejściowe XML.|
|`XslCompiledDllPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa skompilowane XSLT.|
|`XslContent`|Opcjonalny `String` parametr.<br /><br /> Określa dane wejściowe XSLT jako ciąg.|
|`XslInputPath`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa plik wejściowy XSLT.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie plik przekształcenia XSL *Transform. XSLT* służy do modyfikowania pliku XML `$(XmlInputFileName)` . Przekształcony plik XML jest zapisywana w `$(IntermediateOutputPath)output.xml` . Transformacja XSL przyjmuje `$(Parameter1)` jako parametr wejściowy.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Zobacz też

- [Parametry XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

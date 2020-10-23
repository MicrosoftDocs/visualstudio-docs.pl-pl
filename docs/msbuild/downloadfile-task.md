---
title: DownloadFile — zadanie | Microsoft Docs
description: Dowiedz się więcej na temat parametrów zadania DownloadFile programu MSBuild, które pobiera określone pliki przy użyciu protokołu HTTP.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fda3edcd1c8bf173e1b70d8bf2d76d58f6e10d8d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436657"
---
# <a name="downloadfile-task"></a>DownloadFile, zadanie

Pobiera określone pliki przy użyciu protokołu HTTP (Hyper-Text Transfer Protocol).

>[!NOTE]
>Zadanie DownloadFile jest dostępne tylko w programie MSBuild 15,8 i nowszych wersjach.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `DownloadFile` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFileName`|<xref:Microsoft.Build.Framework.ITaskItem>Parametr opcjonalny<br /><br /> Nazwa do użycia dla pobranego pliku.  Domyślnie nazwa pliku jest wyprowadzana z `SourceUrl` lub z serwera zdalnego.|
|`DestinationFolder`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa folder docelowy, do którego ma zostać pobrany plik.  Jeśli folder zostanie utworzony, jeśli nie istnieje.|
|`DownloadedFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa plik, który został pobrany.|
|`Retries`|Opcjonalny `Int32` parametr.<br /><br /> Określa, ile razy należy próbować pobrać, jeśli wszystkie poprzednie próby zakończyły się niepowodzeniem. Domyślnie przyjmuje wartość zero.|
|`RetryDelayMilliseconds`|Opcjonalny `Int32` parametr.<br /><br /> Określa opóźnienie (w milisekundach) między dowolnymi niezbędnymi ponownymi próbami. Wartość domyślna to 5000.|
|`SkipUnchangedFiles`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , pomija pobieranie niezmienionych plików. Wartość domyślna to `true` . `DownloadFile`Zadanie traktuje pliki, które mają być bez zmian, jeśli mają taki sam rozmiar i ten sam czas ostatniej modyfikacji, zgodnie z serwerem zdalnym. <br /><br />**Uwaga:**  Nie wszystkie serwery HTTP wskazują, że data ostatniej modyfikacji plików spowoduje ponowne pobranie pliku.|
|`SourceUrl`|Wymagany parametr interfejsu `String`.<br /><br /> Określa adres URL do pobrania.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pobiera plik i dołącza go do `Content` elementów przed skompilowaniem projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

---
title: DownloadFile — zadanie | Microsoft Docs
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
ms.openlocfilehash: 06171f3a1543f6fa827c1b6fd477b992d099fff6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590478"
---
# <a name="downloadfile-task"></a>DownloadFile, zadanie
Pobiera określone pliki przy użyciu protokołu HTTP (Hyper-Text Transfer Protocol).

>[!NOTE]
>Zadanie DownloadFile jest dostępne tylko w programie MSBuild 15,8 i nowszych wersjach.

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry zadania `DownloadFile`.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFileName`|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Nazwa do użycia dla pobranego pliku.  Domyślnie nazwa pliku pochodzi od `SourceUrl` lub serwera zdalnego.|
|`DestinationFolder`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa folder docelowy, do którego ma zostać pobrany plik.  Jeśli folder zostanie utworzony, jeśli nie istnieje.|
|`DownloadedFile`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa plik, który został pobrany.|
|`Retries`|Opcjonalny parametr `Int32`.<br /><br /> Określa, ile razy należy próbować pobrać, jeśli wszystkie poprzednie próby zakończyły się niepowodzeniem. Domyślnie przyjmuje wartość zero.|
|`RetryDelayMilliseconds`|Opcjonalny parametr `Int32`.<br /><br /> Określa opóźnienie (w milisekundach) między dowolnymi niezbędnymi ponownymi próbami. Wartość domyślna to 5000.|
|`SkipUnchangedFiles`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, pomija pobieranie niezmienionych plików. Wartość domyślna to `true`. Zadanie `DownloadFile` uznaje, że pliki mają być bez zmian, jeśli mają taki sam rozmiar i ten sam czas ostatniej modyfikacji, zgodnie z serwerem zdalnym. <br /><br />**Uwaga:**  Nie wszystkie serwery HTTP wskazują, że data ostatniej modyfikacji plików spowoduje ponowne pobranie pliku.|
|`SourceUrl`|Wymagany `String` parametr.<br /><br /> Określa adres URL do pobrania.|

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

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

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

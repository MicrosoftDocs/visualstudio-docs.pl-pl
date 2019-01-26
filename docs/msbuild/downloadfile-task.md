---
title: Zadanie DownloadFile | Dokumentacja firmy Microsoft
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
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f22d335cb9f0c9bde5d9a5adc11c32e2d165fd97
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978155"
---
# <a name="downloadfile-task"></a>Zadanie DownloadFile
Pobiera określone pliki przy użyciu Hyper tekstu Transfer Protocol (HTTP).

>[!NOTE]
>Zadanie DownloadFile jest tylko dostępne w MSBuild 15.8 i powyżej.
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `DownloadFile` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DestinationFileName`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru<br /><br /> Nazwa do użycia dla pobranego pliku.  Domyślnie, nazwa pliku jest tworzony na podstawie `SourceUrl` lub serwerze zdalnym.|
|`DestinationFolder`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa folder docelowy, aby pobrać plik do.  Jeśli folder jest tworzony, jeśli nie istnieje.|
|`DownloadedFile`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa plik, który został pobrany.|
|`Retries`|Opcjonalnie `Int32` parametru.<br /><br /> Określa, ile razy, aby spróbować pobrać, jeśli wszystkie poprzednie próby się nie powiodły. Domyślnie przyjmuje wartość zero.|  
|`RetryDelayMilliseconds`|Opcjonalnie `Int32` parametru.<br /><br /> Określa opóźnienie (w milisekundach) między kolejnymi niezbędnymi ponownymi próbami. Wartość domyślna to 5000.|  
|`SkipUnchangedFiles`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, pomija pobieranie plików, które nie uległy zmianie. Wartość domyślna to `true`. `DownloadFile` Zadań uzna, że pliki za niezmienione, jeśli mają taki sam rozmiar i taki sam Data ostatniej modyfikacji zgodnie z serwera zdalnego. <br /><br />**Uwaga:**  Nie wszystkie serwery HTTP wskazują, Data ostatniej modyfikacji plików spowoduje, że plik Aby ponownie pobrana.|
|`SourceUrl`|Wymagane `String` parametru.<br /><br /> Określa adres URL do pobrania.|
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera plik i dołączenia go w `Content` elementy przed utworzeniem projektu.
  
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
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

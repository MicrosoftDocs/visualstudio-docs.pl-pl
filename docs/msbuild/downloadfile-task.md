---
title: DownloadFile Zadanie | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 81a9c3b1c22277261276ced1940f1f2e83d11882
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634256"
---
# <a name="downloadfile-task"></a>Zadanie DownloadFile

Pobiera określone pliki przy użyciu protokołu HTTP (Hyper-Text Transfer Protocol).

>[!NOTE]
>Zadanie DownloadFile jest dostępne tylko w udziale MSBuild 15.8 i powyżej.

## <a name="parameters"></a>Parametry

W poniższej tabeli `DownloadFile` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`DestinationFileName`|Parametr <xref:Microsoft.Build.Framework.ITaskItem> opcjonalny<br /><br /> Nazwa używana dla pobranego pliku.  Domyślnie nazwa pliku pochodzi od `SourceUrl` serwera zdalnego lub zdalnego.|
|`DestinationFolder`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa folder docelowy, do który ma być pobrany plik.  Jeśli folder jest tworzony, jeśli nie istnieje.|
|`DownloadedFile`|Opcjonalny parametr wyjściowy. <xref:Microsoft.Build.Framework.ITaskItem><br /><br /> Określa pobrany plik.|
|`Retries`|Parametr `Int32` opcjonalny.<br /><br /> Określa, ile razy należy próbować pobrać, jeśli wszystkie poprzednie próby nie powiodły się. Domyślnie przyjmuje wartość zero.|
|`RetryDelayMilliseconds`|Parametr `Int32` opcjonalny.<br /><br /> Określa opóźnienie w milisekundach między wszelkimi niezbędnymi próbami. Wartość domyślna to 5000.|
|`SkipUnchangedFiles`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`program ,pomija pobieranie plików, które pozostają niezmienione. Wartość domyślna to `true`. Zadanie `DownloadFile` uznaje pliki za niezmienione, jeśli mają ten sam rozmiar i ten sam czas ostatniej modyfikacji zgodnie z serwerem zdalnym. <br /><br />**Uwaga:**  Nie wszystkie serwery HTTP wskazują, że data ostatniej modyfikacji plików spowoduje ponowne pobranie pliku.|
|`SourceUrl`|Wymagany parametr interfejsu `String`.<br /><br /> Określa adres URL do pobrania.|

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pobiera plik i zawiera `Content` go w elementach przed tworzeniem projektu.

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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

---
title: GetOutputFileName — zadanie | Microsoft Docs
description: Za pomocą zadania pomocnika programu MSBuild GetOutputFileName można określić opcje nazwy pliku wyjściowego dla cl.exe i innych narzędzi.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436790"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName, zadanie

Zadanie pomocnika, aby uzyskać nazwę pliku wyjściowego dla CL i innych narzędzi, które umożliwiają określenie tylko katalogu wyjściowego lub pełną nazwę pliku lub Nothing.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **GetOutputFileName** .

|Parametr|Opis|
|---------------|-----------------|
|**OutputExtension**|Wymagany parametr **ciągu** .|
|**Plik_wyjściowy**|Opcjonalny parametr wyjściowy **ciągu** .|
|**OutputPath**|Opcjonalny parametr **ciągu** .|
|**SourceFile**|Wymagany parametr **ciągu** .|

## <a name="see-also"></a>Zobacz też

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

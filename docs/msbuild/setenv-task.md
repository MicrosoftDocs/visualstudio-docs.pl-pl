---
title: SetEnv — zadanie | Microsoft Docs
ms.date: 11/05/2018
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59523e3f6b12eb5921235efcf15d7937a14e7247
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595101"
---
# <a name="setenv-task"></a>SetEnv, zadanie
Ustawia lub usuwa wartość określonej zmiennej środowiskowej.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania **setenv** .

|Parametr|Opis|
|---------------|-----------------|
|**Nazwa**|Wymagany parametr **ciągu** .<br /><br /> Nazwa zmiennej środowiskowej.|
|**OutputEnvironmentVariable**|Opcjonalny parametr wyjściowy **ciągu** .<br /><br /> Zawiera wartość, która jest przypisana do zmiennej środowiskowej, która jest określona przez parametr **name** .|
|**Prefiks**|Obowiązkowy parametr `Boolean`.<br /><br /> Jeśli `true`, łączy wartość parametru **Value** przed wartością zmiennej środowiskowej, która jest określona przez parametr **name** , a następnie przypisuje wynik do zmiennej środowiskowej. Jeśli `false`, przypisuje tylko wartość parametru **Value** do zmiennej środowiskowej.|
|**Cel**|Opcjonalny parametr **ciągu** .<br /><br /> Określa lokalizację, w której jest przechowywana zmienna środowiskowa. Określ "User" lub "Machine".<br /><br /> Aby uzyskać więcej informacji, zobacz [EnvironmentVariableTarget Enumeration](xref:System.EnvironmentVariableTarget).|
|**Wartość**|Opcjonalny parametr **ciągu** .<br /><br /> Wartość przypisana do zmiennej środowiskowej, która jest określona przez parametr **name** . Jeśli **wartość** jest pusta, a zmienna istnieje, zmienna jest usuwana. Jeśli zmienna nie istnieje, żaden błąd nie występuje, mimo że nie można wykonać operacji.<br /><br /> Aby uzyskać więcej informacji, zobacz [Metoda Environment:: SetEnvironmentVariable nie zawiera](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

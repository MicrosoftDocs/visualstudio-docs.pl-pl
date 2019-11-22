---
title: SetEnv — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7dc9b15efb8fca12382fae94912d22c39b96bd4c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295969"
---
# <a name="setenv-task"></a>SetEnv — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawia lub usuwa wartość określonej zmiennej środowiskowej.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry zadania **setenv** .  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**Nazwa**|Wymagany parametr **ciągu** .<br /><br /> Nazwa zmiennej środowiskowej.|  
|**OutputEnvironmentVariable**|Opcjonalny parametr wyjściowy **ciągu** .<br /><br /> Zawiera wartość, która jest przypisana do zmiennej środowiskowej, która jest określona przez parametr **name** .|  
|**Prefiks**|Obowiązkowy parametr `Boolean`.<br /><br /> Jeśli `true`, łączy wartość parametru **Value** przed wartością zmiennej środowiskowej, która jest określona przez parametr **name** , a następnie przypisuje wynik do zmiennej środowiskowej. Jeśli `false`, przypisuje tylko wartość parametru **Value** do zmiennej środowiskowej.|  
|**Obiektów**|Opcjonalny parametr **ciągu** .<br /><br /> Określa lokalizację, w której jest przechowywana zmienna środowiskowa. Określ wartość "`User`" lub "`Machine`".<br /><br /> Aby uzyskać więcej informacji, zobacz "Wyliczenie EnvironmentVariableTarget" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
|**Wartość**|Opcjonalny parametr **ciągu** .<br /><br /> Wartość przypisana do zmiennej środowiskowej, która jest określona przez parametr **name** . Jeśli **wartość** jest pusta, a zmienna istnieje, zmienna jest usuwana. Jeśli zmienna nie istnieje, żaden błąd nie występuje, mimo że nie można wykonać operacji.<br /><br /> Aby uzyskać więcej informacji, zobacz "Environment:: SetEnvironmentVariable nie zawiera Method" w witrynie [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) w sieci Web.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

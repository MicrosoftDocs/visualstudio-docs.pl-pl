---
title: SETENV — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/05/2018
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3024a0477193647a6949eeaa4d8d40d4d965f940
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220409"
---
# <a name="setenv-task"></a>SETENV — zadanie
Ustawia lub usuwa wartość określonej zmiennej środowiskowej.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **SetEnv** zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**Nazwa**|Wymagane **ciąg** parametru.<br /><br /> Nazwa zmiennej środowiskowej.|  
|**OutputEnvironmentVariable**|Opcjonalnie **ciąg** parametr wyjściowy.<br /><br /> Zawiera wartość, która jest przypisana do zmiennej środowiskowej, który jest określony przez **nazwa** parametru.|  
|**Prefiks**|Obowiązkowe `Boolean` parametru.<br /><br /> Jeśli `true`, łączy wartości **wartość** parametru przed wartością zmiennej środowiskowej, który jest określony przez **nazwa** parametru, a następnie przypisuje wynik do środowiska Zmienna. Jeśli `false`, przypisuje wartość elementu **wartość** parametr do zmiennej środowiskowej.|  
|**Docelowy**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa lokalizację przechowywania dla zmiennej środowiskowej. Określ "User" lub "Machine".<br /><br /> Aby uzyskać więcej informacji, zobacz [wyliczenie EnvironmentVariableTarget](xref:System.EnvironmentVariableTarget).|  
|**Wartość**|Opcjonalnie **ciąg** parametru.<br /><br /> Wartość przypisana do zmiennej środowiskowej, który jest określony przez **nazwa** parametru. Jeśli **wartość** jest pusta i zmienna istnieje, zmienna zostanie usunięty. Jeśli zmienna nie istnieje, nie występuje błąd, mimo że nie można wykonać operacji.<br /><br /> Aby uzyskać więcej informacji, zobacz [metoda Environment::SetEnvironmentVariable](xref:System.Environment.SetEnvironmentVariable%2A).|  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
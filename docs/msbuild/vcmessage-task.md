---
title: Vcmessage — zadanie | Dokumentacja firmy Microsoft
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5543627332e7c70fa40df5be4091bca7fab7bcfd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004860"
---
# <a name="vcmessage-task"></a>VCMessage — Zadanie
Dzienniki, ostrzeżenia i komunikaty o błędach podczas kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 To zadanie ułatwia Implementowanie MSBuild dla języka Visual C++ i nie jest przeznaczona do wywoływania przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry **vcmessage —** zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|**Argumenty**|Opcjonalnie **ciąg** parametru.<br /><br /> Rozdzielana średnikami lista wiadomości do wyświetlenia.|  
|**Kod**|Wymagane **ciąg** parametru.<br /><br /> Numer błędu, który kwalifikuje wiadomości.|  
|**Typ**|Opcjonalnie **ciąg** parametru.<br /><br /> Określa rodzaj komunikatów do emitowania. Określ "Ostrzeżenie", aby emitować komunikat ostrzegawczy lub "Error", aby emitować komunikat o błędzie.|  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
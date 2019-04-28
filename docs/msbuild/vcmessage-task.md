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
ms.openlocfilehash: d025fd1f71b67acbcd532232b36b55fd35e1f530
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970760"
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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
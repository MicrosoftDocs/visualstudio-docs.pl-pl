---
title: VCMessage — — zadanie | Microsoft Docs
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
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66b1bf1eb222d70c18bfb94c65dddd2903864c68
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591115"
---
# <a name="vcmessage-task"></a>VCMessage — Zadanie
Rejestruje ostrzeżenia i komunikaty o błędach podczas kompilacji.

## <a name="remarks"></a>Uwagi
 To zadanie ułatwia zaimplementowanie C++ programu MSBuild dla projektów i nie jest przeznaczone do wywoływania przez użytkownika. Aby uzyskać więcej informacji, zobacz temat <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania **VCMessage —** .

|Parametr|Opis|
|---------------|-----------------|
|**Argumenty**|Opcjonalny parametr **ciągu** .<br /><br /> Rozdzielana średnikami lista komunikatów do wyświetlenia.|
|**Kod**|Wymagany parametr **ciągu** .<br /><br /> Numer błędu, który uprawnia do wiadomości.|
|**Typ**|Opcjonalny parametr **ciągu** .<br /><br /> Określa rodzaj komunikatu do emisji. Określ "ostrzeżenie", aby emitować komunikat ostrzegawczy, lub "błąd", aby wyemitować komunikat o błędzie.|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

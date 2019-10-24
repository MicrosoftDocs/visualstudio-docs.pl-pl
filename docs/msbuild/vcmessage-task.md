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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be4f963a5944882f14118be54e498fd4712c2e46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747183"
---
# <a name="vcmessage-task"></a>VCMessage — Zadanie
Rejestruje ostrzeżenia i komunikaty o błędach podczas kompilacji.

## <a name="remarks"></a>Uwagi
 To zadanie ułatwia zaimplementowanie C++ programu MSBuild dla projektów i nie jest przeznaczone do wywoływania przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania **VCMessage —** .

|Parametr|Opis|
|---------------|-----------------|
|**Argumenty**|Opcjonalny parametr **ciągu** .<br /><br /> Rozdzielana średnikami lista komunikatów do wyświetlenia.|
|**Kod**|Wymagany parametr **ciągu** .<br /><br /> Numer błędu, który uprawnia do wiadomości.|
|**Wprowadź**|Opcjonalny parametr **ciągu** .<br /><br /> Określa rodzaj komunikatu do emisji. Określ "ostrzeżenie", aby emitować komunikat ostrzegawczy, lub "błąd", aby wyemitować komunikat o błędzie.|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
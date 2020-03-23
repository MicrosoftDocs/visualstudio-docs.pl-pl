---
title: Zadanie VCMessage | Dokumenty firmy Microsoft
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
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631214"
---
# <a name="vcmessage-task"></a>VCMessage — Zadanie

Rejestruje komunikaty ostrzegawcze i komunikaty o błędach podczas kompilacji.

## <a name="remarks"></a>Uwagi

 To zadanie pomaga zaimplementować MSBuild dla projektów Języka C++ i nie jest przeznaczony do wywoływania przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **VCMessage.**

|Parametr|Opis|
|---------------|-----------------|
|**Argumenty**|Opcjonalny parametr **String.**<br /><br /> Lista wiadomości rozdzielanych średnikami do wyświetlenia.|
|**Code**|Wymagany parametr **String.**<br /><br /> Numer błędu, który kwalifikuje wiadomość.|
|**Typ**|Opcjonalny parametr **String.**<br /><br /> Określa rodzaj wiadomości do emisji. Określ "Ostrzeżenie", aby emitować komunikat ostrzegawczy lub "Błąd", aby emitować komunikat o błędzie.|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

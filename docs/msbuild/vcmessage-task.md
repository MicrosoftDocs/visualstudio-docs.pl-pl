---
title: VCMessage — — zadanie | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania VCMessage — do rejestrowania ostrzeżeń i komunikatów o błędach podczas kompilacji dla projektów języka C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c01c86a5374c14ac27de1535020c5deed29a89f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046750"
---
# <a name="vcmessage-task"></a>VCMessage — Zadanie

Rejestruje ostrzeżenia i komunikaty o błędach podczas kompilacji.

## <a name="remarks"></a>Uwagi

 To zadanie ułatwia implementację programu MSBuild dla projektów języka C++ i nie jest przeznaczone do wywoływania przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **VCMessage —** .

|Parametr|Opis|
|---------------|-----------------|
|**Argumenty**|Opcjonalny parametr **ciągu** .<br /><br /> Rozdzielana średnikami lista komunikatów do wyświetlenia.|
|**Kod**|Wymagany parametr **ciągu** .<br /><br /> Numer błędu, który uprawnia do wiadomości.|
|**Typ**|Opcjonalny parametr **ciągu** .<br /><br /> Określa rodzaj komunikatu do emisji. Określ "ostrzeżenie", aby emitować komunikat ostrzegawczy, lub "błąd", aby wyemitować komunikat o błędzie.|

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)

---
title: SETENV — zadanie | Dokumentacja firmy Microsoft
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
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16a73ac066ff0b61570f0ed918308cf8874121d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996516"
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
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
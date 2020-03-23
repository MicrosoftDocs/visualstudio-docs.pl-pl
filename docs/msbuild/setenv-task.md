---
title: Zadanie SetEnv | Dokumenty firmy Microsoft
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
ms.openlocfilehash: c5df538e7eb86a20dfc06e6e6558bded577ba3d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632384"
---
# <a name="setenv-task"></a>Zadanie SetEnv

Ustawia lub usuwa wartość określonej zmiennej środowiskowej.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **SetEnv.**

|Parametr|Opis|
|---------------|-----------------|
|**Nazwa**|Wymagany parametr **String.**<br /><br /> Nazwa zmiennej środowiskowej.|
|**Dane wyjścioweWarienne**|Opcjonalny parametr wyjścia **ciągu.**<br /><br /> Zawiera wartość przypisaną do zmiennej środowiskowej określonej przez parametr **Name.**|
|**Prefiks**|Parametr `Boolean` obowiązkowy.<br /><br /> Jeśli `true`, łączy wartość **Value** parametr przed wartością zmiennej środowiskowej, która jest określona przez **Name** parametr, a następnie przypisuje wynik do zmiennej środowiskowej. Jeśli `false`, przypisuje tylko wartość **parametru Wartość** do zmiennej środowiskowej.|
|**Obiekt docelowy**|Opcjonalny parametr **String.**<br /><br /> Określa lokalizację, w której przechowywana jest zmienna środowiskowa. Określ "Użytkownik" lub "Maszyna".<br /><br /> Aby uzyskać więcej informacji, zobacz [EnvironmentVariableTarget Wyliczanie](xref:System.EnvironmentVariableTarget).|
|**Wartość**|Opcjonalny parametr **String.**<br /><br /> Wartość przypisana do zmiennej środowiskowej, która jest określona przez **name** parametru. Jeśli **wartość** jest pusta i zmienna istnieje, zmienna jest usuwana. Jeśli zmienna nie istnieje, nie występuje żaden błąd, mimo że nie można wykonać operacji.<br /><br /> Aby uzyskać więcej informacji, zobacz [Środowisko::SetEnvironmentVariable Method](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

---
title: Resolvekeysource — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 123c45ed23743335a1c4db2000dd241cb92ce291
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810639"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource — zadanie
Określa źródło klucza silnej nazwy.

## <a name="task-parameters"></a>Parametry zadania
 W poniższej tabeli opisano parametry `ResolveKeySource` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Opcjonalnie `Int32` parametru.<br /><br /> Pobiera lub ustawia czas, w ciągu kilku sekund, aby wyświetlić liczbę w dół wiadomości.|
|`AutoClosePasswordPromptTimeout`|Opcjonalnie `Int32` parametru.<br /><br /> Pobiera lub ustawia czas, w ciągu kilku sekund oczekiwania przed zamknięciem okna dialogowego monitu hasła.|
|`CertificateFile`|Opcjonalnie `String` parametru.<br /><br /> Pobiera lub ustawia ścieżkę do pliku certyfikatu.|
|`CertificateThumbprint`|Opcjonalnie `String` parametru.<br /><br /> Pobiera lub ustawia odcisk palca certyfikatu.|
|`KeyFile`|Opcjonalnie `String` parametru.<br /><br /> Pobiera lub ustawia ścieżkę pliku klucza.|
|`ResolvedKeyContainer`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia rozwiązane kontener kluczy.|
|`ResolvedKeyFile`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia rozpoznać pliku klucza.|
|`ResolvedThumbprint`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia odcisk palca certyfikatu rozwiązane.|
|`ShowImportDialogDespitePreviousFailures`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, Pokaż Importuj okno dialogowe, niezależnie od wcześniejszych niepowodzeń.|
|`SuppressAutoClosePasswordPrompt`|Opcjonalnie `Boolean` parametru.<br /><br /> Pobiera lub ustawia wartość logiczną, która określa, czy okno dialogowe monitu hasła powinna nie automatycznego zamykania.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
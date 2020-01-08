---
title: ResolveKeySource — — zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 09b3917e1c67014a780d11e2ae9a944844e63e25
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595192"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource — zadanie
Określa źródło klucza o silnej nazwie.

## <a name="task-parameters"></a>Parametry zadania
 W poniższej tabeli opisano parametry zadania `ResolveKeySource`.

|Parametr|Opis|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Opcjonalny parametr `Int32`.<br /><br /> Pobiera lub ustawia czas (w sekundach) wyświetlania komunikatu o pomniejszeniu.|
|`AutoClosePasswordPromptTimeout`|Opcjonalny parametr `Int32`.<br /><br /> Pobiera lub ustawia czas (w sekundach) oczekiwania przed zamknięciem okna dialogowego monitu o hasło.|
|`CertificateFile`|Opcjonalny parametr `String`.<br /><br /> Pobiera lub ustawia ścieżkę pliku certyfikatu.|
|`CertificateThumbprint`|Opcjonalny parametr `String`.<br /><br /> Pobiera lub ustawia odcisk palca certyfikatu.|
|`KeyFile`|Opcjonalny parametr `String`.<br /><br /> Pobiera lub ustawia ścieżkę pliku klucza.|
|`ResolvedKeyContainer`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia rozpoznany kontener kluczy.|
|`ResolvedKeyFile`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia rozpoznany plik klucza.|
|`ResolvedThumbprint`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Pobiera lub ustawia odcisk palca rozpoznanego certyfikatu.|
|`ShowImportDialogDespitePreviousFailures`|Opcjonalny parametr `Boolean`.<br /><br /> Jeśli `true`, Pokaż okno dialogowe importowania pomimo poprzednich błędów.|
|`SuppressAutoClosePasswordPrompt`|Opcjonalny parametr `Boolean`.<br /><br /> Pobiera lub ustawia wartość logiczną określającą, czy okno dialogowe monitu o hasło nie powinno być autozamykane.|

## <a name="remarks"></a>Uwagi
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz także
- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

---
title: Zadanie ResolveKeySource | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 3aa4e2454a0216e697ed12404091eb0ef16416cb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632709"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource — zadanie

Określa źródło klucza silnej nazwy.

## <a name="task-parameters"></a>Parametry zadania

 W poniższej tabeli `ResolveKeySource` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Parametr `Int32` opcjonalny.<br /><br /> Pobiera lub ustawia ilość czasu w sekundach, aby wyświetlić komunikat odliczania.|
|`AutoClosePasswordPromptTimeout`|Parametr `Int32` opcjonalny.<br /><br /> Pobiera lub ustawia czas, w sekundach, aby odczekać przed zamknięciem okna dialogowego monitu hasła.|
|`CertificateFile`|Parametr `String` opcjonalny.<br /><br /> Pobiera lub ustawia ścieżkę pliku certyfikatu.|
|`CertificateThumbprint`|Parametr `String` opcjonalny.<br /><br /> Pobiera lub ustawia odcisk palca certyfikatu.|
|`KeyFile`|Parametr `String` opcjonalny.<br /><br /> Pobiera lub ustawia ścieżkę pliku klucza.|
|`ResolvedKeyContainer`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Pobiera lub ustawia kontener rozwiązany klucz.|
|`ResolvedKeyFile`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Pobiera lub ustawia rozwiązany plik klucza.|
|`ResolvedThumbprint`|Opcjonalny parametr wyjściowy. `String`<br /><br /> Pobiera lub ustawia odcisk palca certyfikatu rozwiązany.|
|`ShowImportDialogDespitePreviousFailures`|Parametr `Boolean` opcjonalny.<br /><br /> Jeśli `true`, pokaż okno dialogowe importu pomimo wcześniejszych błędów.|
|`SuppressAutoClosePasswordPrompt`|Parametr `Boolean` opcjonalny.<br /><br /> Pobiera lub ustawia wartość logiczną, która określa, czy okno dialogowe monitu hasła nie należy automatycznie zamykać.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)

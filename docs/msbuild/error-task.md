---
title: Zadanie błędu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5dd3214c9575a34e9265c33061b024648a221c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634230"
---
# <a name="error-task"></a>Error — Zadanie

Zatrzymuje kompilacji i rejestruje błąd na podstawie ocenione instrukcji warunkowej.

## <a name="parameters"></a>Parametry

W poniższej tabeli `Error` opisano parametry zadania.

| Parametr | Opis |
|---------------| - |
| `Code` | Parametr `String` opcjonalny.<br /><br /> Kod błędu do skojarzenia z błędem. |
| `File` | Parametr `String` opcjonalny.<br /><br /> Nazwa pliku zawierającego błąd. Jeśli nie podano nazwy pliku, zostanie użyty plik zawierający zadanie Error. |
| `HelpKeyword` | Parametr `String` opcjonalny.<br /><br /> Słowo kluczowe Pomoc, aby skojarzyć z błędem. |
| `Text` | Parametr `String` opcjonalny.<br /><br /> Tekst błędu, który MSBuild `Condition` rejestruje, jeśli `true`parametr jest oceniany na . |

## <a name="remarks"></a>Uwagi

Zadanie `Error` umożliwia msbuild projektów do wystawiania tekstu błędu do rejestratorów i zatrzymać wykonanie kompilacji.

Jeśli `Condition` parametr ocenia `true`, kompilacja jest zatrzymana i rejestrowany jest błąd. Jeśli `Condition` parametr nie istnieje, błąd jest rejestrowany i zatrzymuje wykonywanie kompilacji. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu sprawdza, czy wszystkie wymagane właściwości są ustawione. Jeśli nie są ustawione, projekt wywołuje zdarzenie błędu i rejestruje `Text` wartość parametru `Error` zadania.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Error
            Text=" The 0 property must be set on the command line."
            Condition="'$(0)' == ''" />
        <Error
            Text="The FREEBUILD property must be set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

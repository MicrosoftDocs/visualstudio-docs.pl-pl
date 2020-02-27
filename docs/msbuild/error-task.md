---
title: Błąd — zadanie | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634230"
---
# <a name="error-task"></a>Error — Zadanie

Kończy kompilację i rejestruje błąd na podstawie ocenianej instrukcji warunkowej.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania `Error`.

| Parametr | Opis |
|---------------| - |
| `Code` | Opcjonalny parametr `String`.<br /><br /> Kod błędu, który ma zostać skojarzony z błędem. |
| `File` | Opcjonalny parametr `String`.<br /><br /> Nazwa pliku, który zawiera błąd. Jeśli nie podano nazwy pliku, zostanie użyty plik zawierający zadanie błędu. |
| `HelpKeyword` | Opcjonalny parametr `String`.<br /><br /> Słowo kluczowe pomocy do skojarzenia z błędem. |
| `Text` | Opcjonalny parametr `String`.<br /><br /> Tekst błędu, który program MSBuild rejestruje, jeśli `Condition` parametr oblicza `true`. |

## <a name="remarks"></a>Uwagi

Zadanie `Error` umożliwia projektom MSBuild wygenerowanie tekstu błędów w celu rejestrowania i zatrzymanie wykonywania kompilacji.

Jeśli `Condition` parametr oblicza `true`, kompilacja zostanie zatrzymana i zostanie zarejestrowany błąd. Jeśli parametr `Condition` nie istnieje, zostanie zarejestrowany błąd i zostanie zatrzymane wykonywanie kompilacji. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu sprawdza, czy są ustawione wszystkie wymagane właściwości. Jeśli nie są ustawione, projekt zgłasza zdarzenie błędu i rejestruje wartość parametru `Text` zadania `Error`.

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

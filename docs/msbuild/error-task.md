---
title: Błąd — zadanie | Microsoft Docs
description: Użyj zadania błędu MSBuild, aby zatrzymać kompilację i zarejestrować błąd na podstawie obliczanej instrukcji warunkowej.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e4e1a91bc018bdf77671b13994ce57e4e10e694
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877203"
---
# <a name="error-task"></a>Error — Zadanie

Kończy kompilację i rejestruje błąd na podstawie ocenianej instrukcji warunkowej.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry `Error` zadania.

| Parametr | Opis |
|---------------| - |
| `Code` | Opcjonalny `String` parametr.<br /><br /> Kod błędu, który ma zostać skojarzony z błędem. |
| `File` | Opcjonalny `String` parametr.<br /><br /> Nazwa pliku, który zawiera błąd. Jeśli nie podano nazwy pliku, zostanie użyty plik zawierający zadanie błędu. |
| `HelpKeyword` | Opcjonalny `String` parametr.<br /><br /> Słowo kluczowe pomocy do skojarzenia z błędem. |
| `Text` | Opcjonalny `String` parametr.<br /><br /> Tekst błędu, który program MSBuild rejestruje, jeśli `Condition` parametr ma wartość `true` . |

## <a name="remarks"></a>Uwagi

`Error`Zadanie pozwala projektom MSBuild na wystawianie tekstu błędów w rejestratory i zatrzymanie wykonywania kompilacji.

Jeśli `Condition` parametr ma wartość `true` , kompilacja zostaje zatrzymana i zostanie zarejestrowany błąd. Jeśli `Condition` parametr nie istnieje, ten błąd jest rejestrowany i wykonywanie kompilacji zostanie zatrzymane. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład kodu sprawdza, czy są ustawione wszystkie wymagane właściwości. Jeśli nie są ustawione, projekt zgłasza zdarzenie błędu i rejestruje wartość `Text` parametru `Error` zadania.

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

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

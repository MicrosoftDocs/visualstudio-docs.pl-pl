---
title: Error — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc603d11a087fb413896b9ae897ee730e18aae1b
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853381"
---
# <a name="error-task"></a>Error — Zadanie
Zatrzymuje kompilację i rejestruje błąd oparte na ocenianą instrukcji warunkowej.

## <a name="parameters"></a>Parametry
W poniższej tabeli opisano parametry `Error` zadania.

| Parametr | Opis |
|---------------| - |
| `Code` | Opcjonalnie `String` parametru.<br /><br /> Kod błędu do skojarzenia z powodu błędu. |
| `File` | Opcjonalnie `String` parametru.<br /><br /> Nazwa pliku który zawiera błąd. Jeśli nazwa pliku nie zostanie podany, plik zawierający błąd zadania będą używane. |
| `HelpKeyword` | Opcjonalnie `String` parametru.<br /><br /> Słowo kluczowe pomocy do skojarzenia z powodu błędu. |
| `Text` | Opcjonalnie `String` parametru.<br /><br /> Tekst błędu, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rejestruje Jeśli `Condition` daje w wyniku parametru `true`. |

## <a name="remarks"></a>Uwagi
`Error` Zadanie pozwala [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów, aby wystawić rejestratorów tekst błędu i Zatrzymaj tworzenie wykonywania.

Jeśli `Condition` daje w wyniku parametru `true`, kompilacja zostanie zatrzymana i zostanie zarejestrowany błąd. Jeśli `Condition` parametr nie istnieje, błąd jest rejestrowane i zatrzymuje wykonywanie kompilacji. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [dzienniki kompilacji uzyskiwanie](../msbuild/obtaining-build-logs-with-msbuild.md).

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
Poniższy przykład kodu sprawdza, czy wszystkie wymagane właściwości są ustawione. Jeśli nie są ustawione, projekt zgłasza zdarzenie błędu i rejestruje wartość `Text` parametru `Error` zadania.

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

## <a name="see-also"></a>Zobacz także
[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)  
[Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

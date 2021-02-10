---
title: Zadanie ostrzegawcze | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania ostrzegawczego do rejestrowania ostrzeżenia podczas kompilacji opartej na obliczanej instrukcji warunkowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f31ad26b6efffa540ecae6a61f0f7ff12115cef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933807"
---
# <a name="warning-task"></a>Warning — Zadanie

Rejestruje ostrzeżenie podczas kompilacji oparte na obliczanej instrukcji warunkowej.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `Warning` zadania.

| Parametr | Opis |
|---------------| - |
| `Code` | Opcjonalny `String` parametr.<br /><br /> Kod ostrzeżenia do skojarzenia z ostrzeżeniem. |
| `File` | Opcjonalny `String` parametr.<br /><br /> Określa odpowiedni plik, jeśli istnieje. Jeśli plik nie zostanie podany, zostanie użyty plik zawierający zadanie ostrzegawcze. |
| `HelpKeyword` | Opcjonalny `String` parametr.<br /><br /> Słowo kluczowe pomocy do skojarzenia z ostrzeżeniem. |
| `Text` | Opcjonalny `String` parametr.<br /><br /> Tekst ostrzegawczy, który program MSBuild rejestruje, jeśli `Condition` parametr ma wartość `true` . |

## <a name="remarks"></a>Uwagi

 `Warning`Zadanie pozwala projektom MSBuild sprawdzić obecność wymaganej konfiguracji lub właściwości przed przejściem do kolejnego kroku kompilacji.

 Jeśli `Condition` parametr `Warning` zadania jest obliczany `true` , wartość `Text` parametru jest rejestrowany, a kompilacja kontynuuje wykonywanie. Jeśli `Condition` parametr nie istnieje, jest rejestrowany tekst ostrzegawczy. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [pobieranie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład kodu sprawdza właściwości, które są ustawiane w wierszu polecenia. Jeśli nie ma ustawionych właściwości, projekt zgłasza zdarzenie ostrzeżenia i rejestruje wartość `Text` parametru `Warning` zadania.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Warning
            Text=" The 0 property was not set on the command line."
            Condition="'$(0)' == ''" />
        <Warning
            Text=" The FREEBUILD property was not set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

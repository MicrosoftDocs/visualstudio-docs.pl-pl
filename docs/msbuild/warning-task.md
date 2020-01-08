---
title: Zadanie ostrzegawcze | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84b9f9d9d92815d1719f8ba43f4014ef9598e0c4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567141"
---
# <a name="warning-task"></a>Warning — Zadanie
Rejestruje ostrzeżenie podczas kompilacji oparte na obliczanej instrukcji warunkowej.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `Warning`.

| Parametr | Opis |
|---------------| - |
| `Code` | Opcjonalny parametr `String`.<br /><br /> Kod ostrzeżenia do skojarzenia z ostrzeżeniem. |
| `File` | Opcjonalny parametr `String`.<br /><br /> Określa odpowiedni plik, jeśli istnieje. Jeśli plik nie zostanie podany, zostanie użyty plik zawierający zadanie ostrzegawcze. |
| `HelpKeyword` | Opcjonalny parametr `String`.<br /><br /> Słowo kluczowe pomocy do skojarzenia z ostrzeżeniem. |
| `Text` | Opcjonalny parametr `String`.<br /><br /> Tekst ostrzegawczy, który [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dzienniki, jeśli parametr `Condition` zostanie oszacowany jako `true`. |

## <a name="remarks"></a>Uwagi
 Zadanie `Warning` pozwala [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty sprawdzają obecność wymaganej konfiguracji lub właściwości przed przejściem do kolejnego kroku kompilacji.

 Jeśli parametr `Condition` zadania `Warning` zostanie oszacowany `true`, wartość parametru `Text` jest rejestrowana i kompilacja będzie nadal wykonywana. Jeśli parametr `Condition` nie istnieje, jest rejestrowany tekst ostrzegawczy. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [pobieranie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
 Poniższy przykład kodu sprawdza właściwości, które są ustawiane w wierszu polecenia. Jeśli nie ma ustawionych właściwości, projekt zgłasza zdarzenie ostrzeżenia i rejestruje wartość parametru `Text` zadania `Warning`.

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

## <a name="see-also"></a>Zobacz także
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

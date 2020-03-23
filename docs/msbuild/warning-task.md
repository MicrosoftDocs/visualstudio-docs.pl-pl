---
title: Zadanie ostrzegawcze | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 2e95b59b4ccc0bd2df89e45512a5bdd05c027556
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631097"
---
# <a name="warning-task"></a>Warning — Zadanie

Rejestruje ostrzeżenie podczas kompilacji na podstawie ocenianej instrukcji warunkowej.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `Warning` opisano parametry zadania.

| Parametr | Opis |
|---------------| - |
| `Code` | Parametr `String` opcjonalny.<br /><br /> Kod ostrzeżenia do skojarzenia z ostrzeżeniem. |
| `File` | Parametr `String` opcjonalny.<br /><br /> Określa odpowiedni plik, jeśli istnieje. Jeśli nie podano pliku, używany jest plik zawierający zadanie Ostrzeżenie. |
| `HelpKeyword` | Parametr `String` opcjonalny.<br /><br /> Słowo kluczowe Pomoc, aby skojarzyć z ostrzeżeniem. |
| `Text` | Parametr `String` opcjonalny.<br /><br /> Tekst ostrzeżenia, który MSBuild `Condition` rejestruje, jeśli `true`parametr jest oceniany na . |

## <a name="remarks"></a>Uwagi

 Zadanie `Warning` umożliwia msbuild projektów, aby sprawdzić obecność wymaganej konfiguracji lub właściwości przed przystąpieniem do następnego kroku kompilacji.

 Jeśli `Condition` parametr `Warning` zadania jest oceniany na `true`, `Text` wartość parametru jest rejestrowana, a kompilacja jest kontynuowana. Jeśli `Condition` parametr nie istnieje, tekst ostrzeżenia jest rejestrowany. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład kodu sprawdza właściwości, które są ustawione w wierszu polecenia. Jeśli nie ma żadnych właściwości ustawionego, projekt wywołuje zdarzenie ostrzegawcze i `Text` rejestruje `Warning` wartość parametru zadania.

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

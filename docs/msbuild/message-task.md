---
title: Zadanie komunikatu | Microsoft Docs
description: Poznaj parametry i ustawienia zadania programu MSBuild, które rejestruje komunikaty podczas kompilacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eb2a1837210a5f36577d3bf677a4152033914f49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918245"
---
# <a name="message-task"></a>Komunikat — Zadanie

Rejestruje komunikat w trakcie kompilacji.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry `Message` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Importance`|Opcjonalny `String` parametr.<br /><br /> Określa ważność komunikatu. Ten parametr może mieć wartość `high` `normal` lub `low` . Wartość domyślna to `normal`.|
|`Text`|Opcjonalny `String` parametr.<br /><br /> Tekst błędu do zarejestrowania.|

## <a name="remarks"></a>Uwagi

 `Message`Zadanie pozwala projektom MSBuild wystawiać komunikaty do rejestratorów w różnych krokach procesu kompilacji.

 Jeśli `Condition` parametr daje w to `true` , wartość `Text` parametru zostanie zarejestrowana, a kompilacja będzie kontynuowana. Jeśli `Condition` parametr nie istnieje, tekst komunikatu jest rejestrowany. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [pobieranie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

 Domyślnie komunikat jest wysyłany do wszystkich zarejestrowanych rejestratorów. Rejestrator interpretuje `Importance` parametr. Zwykle komunikat `high` jest wysyłany, gdy poziom szczegółowości rejestratora jest ustawiony na <xref:Microsoft.Build.Framework.LoggerVerbosity> .`Minimal` lub wyższy. Wiadomość ustawiona na `low` jest wysyłana, gdy poziom szczegółowości rejestratora jest ustawiony na <xref:Microsoft.Build.Framework.LoggerVerbosity> . `Detailed`

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład kodu rejestruje komunikaty do wszystkich zarejestrowanych rejestratorów.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

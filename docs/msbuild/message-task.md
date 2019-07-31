---
title: Zadanie komunikatu | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5efcc41a82cab32172aa395b488535f2777b9e13
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681154"
---
# <a name="message-task"></a>Komunikat — Zadanie
Rejestruje komunikat w trakcie kompilacji.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry `Message` zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Importance`|Opcjonalny `String` parametr.<br /><br /> Określa ważność komunikatu. Ten parametr może mieć wartość `high` `normal` lub `low`. Wartość domyślna to `normal`.|
|`Text`|Opcjonalny `String` parametr.<br /><br /> Tekst błędu do zarejestrowania.|

## <a name="remarks"></a>Uwagi
 `Message` Zadanie pozwala[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] na wydawanie komunikatów przez projekty w różnych krokach procesu kompilacji.

 Jeśli parametr daje `true`w to `Text` , wartość parametru zostanie zarejestrowana, a kompilacja będzie kontynuowana. `Condition` `Condition` Jeśli parametr nie istnieje, tekst komunikatu jest rejestrowany. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [pobieranie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

 Domyślnie komunikat jest wysyłany do rejestratora konsoli programu MSBuild. Można to zmienić, ustawiając <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> parametr. Rejestrator interpretuje `Importance` parametr. Zazwyczaj komunikat `high` jest wysyłany, gdy poziom szczegółowości rejestratora jest ustawiony na <xref:Microsoft.Build.Framework.LoggerVerbosity> `Minimal` lub wyższy. Wiadomość `low` jest wysyłana po <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`ustawieniu szczegółowości rejestratora.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> z klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
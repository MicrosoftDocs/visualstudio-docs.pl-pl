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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a2e2a1adb810a8468d318298747eec226846df
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592181"
---
# <a name="message-task"></a>Komunikat — Zadanie
Rejestruje komunikat w trakcie kompilacji.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania `Message`.

|Parametr|Opis|
|---------------|-----------------|
|`Importance`|Opcjonalny parametr `String`.<br /><br /> Określa ważność komunikatu. Ten parametr może mieć wartość `high`, `normal` lub `low`. Wartość domyślna to `normal`.|
|`Text`|Opcjonalny parametr `String`.<br /><br /> Tekst błędu do zarejestrowania.|

## <a name="remarks"></a>Uwagi
 Zadanie `Message` umożliwia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty do wystawiania komunikatów do rejestratorów w różnych krokach procesu kompilacji.

 Jeśli parametr `Condition` zostanie oszacowany na `true`, wartość parametru `Text` zostanie zarejestrowana, a kompilacja będzie nadal wykonywana. Jeśli parametr `Condition` nie istnieje, tekst komunikatu jest rejestrowany. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [pobieranie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

 Domyślnie komunikat jest wysyłany do rejestratora konsoli programu MSBuild. Można to zmienić, ustawiając parametr <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. Rejestrator interpretuje parametr `Importance`. Zwykle komunikat ustawiany na `high` jest wysyłany, gdy poziom szczegółowości rejestratora jest ustawiony na <xref:Microsoft.Build.Framework.LoggerVerbosity>`Minimal` lub wyższy. Wiadomość ustawiona na `low` jest wysyłana, gdy poziom szczegółowości rejestrowania jest ustawiony na <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

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

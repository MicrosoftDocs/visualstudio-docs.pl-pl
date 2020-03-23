---
title: Zadanie wiadomości | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 264ff3a5e64b756020648e888f7817e12702659f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865365"
---
# <a name="message-task"></a>Komunikat — Zadanie

Rejestruje komunikat podczas kompilacji.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `Message` opisano parametry zadania.

|Parametr|Opis|
|---------------|-----------------|
|`Importance`|Parametr `String` opcjonalny.<br /><br /> Określa znaczenie wiadomości. Ten parametr może mieć `high` `normal` wartość `low`, lub . Wartością domyślną jest `normal`.|
|`Text`|Parametr `String` opcjonalny.<br /><br /> Tekst błędu do zalogowania.|

## <a name="remarks"></a>Uwagi

 Zadanie `Message` umożliwia msbuild projektów do wystawiania komunikatów do rejestratorów na różnych etapach procesu kompilacji.

 Jeśli `Condition` parametr zostanie `true`obliczony na `Text` , wartość parametru zostanie zarejestrowana, a kompilacja będzie nadal wykonywana. Jeśli `Condition` parametr nie istnieje, tekst wiadomości jest rejestrowany. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

 Domyślnie wiadomość jest wysyłana do wszystkich zarejestrowanych rejestratorów. Rejestrator interpretuje `Importance` parametr. Zazwyczaj komunikat ustawiony jest `high` wysyłany, gdy szczegółowość rejestratora <xref:Microsoft.Build.Framework.LoggerVerbosity>jest ustawiona na .`Minimal` lub wyższe. Komunikat ustawiony `low` na jest wysyłany, gdy szczegółowość <xref:Microsoft.Build.Framework.LoggerVerbosity>rejestratora jest ustawiona na . `Detailed`.

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

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

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

---
title: Komunikat zadania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 254602005966a9d9f95ff6b76f8ad42360e4a57d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770792"
---
# <a name="message-task"></a>Komunikat — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Rejestruje komunikat podczas kompilacji.  
  
## <a name="parameters"></a>Parametry  
 W następujących tabeli przedstawiono parametry `Message` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Importance`|Opcjonalnie `String` parametru.<br /><br /> Określa ważność wiadomości. Ten parametr może mieć wartość `high`, `normal` lub `low`. Wartość domyślna to `normal`.|  
|`Text`|Opcjonalnie `String` parametru.<br /><br /> Tekst błędu logowania.|  
  
## <a name="remarks"></a>Uwagi  
 `Message` Zadanie pozwala [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projekty do problemu komunikatów rejestratorów w innych czynności w procesie kompilacji.  
  
 Jeśli `Condition` daje w wyniku parametr `true`, wartość `Text` parametru będą rejestrowane i kompilacja będą w dalszym ciągu wykonują. Jeśli `Condition` parametr nie istnieje, tekst komunikatu jest rejestrowane. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Domyślnie komunikat jest wysyłany do rejestratora konsoli do programu MSBuild. Można to zmienić, ustawiając <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> parametru. Rejestrator interpretuje `Importance` parametru.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu rejestruje komunikaty wszystkich rejestratorów zarejestrowanych.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

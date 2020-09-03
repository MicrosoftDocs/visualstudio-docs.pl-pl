---
title: Zadanie komunikatu | Microsoft Docs
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
ms.openlocfilehash: 48e867cd0993106247f7105c1102f4e1407a4fed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190895"
---
# <a name="message-task"></a>Komunikat — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rejestruje komunikat w trakcie kompilacji.  
  
## <a name="parameters"></a>Parametry  
 W tabeli następujące kwestie opisano parametry `Message` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Importance`|Opcjonalny `String` parametr.<br /><br /> Określa ważność komunikatu. Ten parametr może mieć wartość `high` `normal` lub `low` . Wartość domyślna to `normal`.|  
|`Text`|Opcjonalny `String` parametr.<br /><br /> Tekst błędu do zarejestrowania.|  
  
## <a name="remarks"></a>Uwagi  
 `Message`Zadanie pozwala na [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wydawanie komunikatów przez projekty w różnych krokach procesu kompilacji.  
  
 Jeśli `Condition` parametr daje w to `true` , wartość `Text` parametru zostanie zarejestrowana, a kompilacja będzie kontynuowana. Jeśli `Condition` parametr nie istnieje, tekst komunikatu jest rejestrowany. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Domyślnie komunikat jest wysyłany do rejestratora konsoli programu MSBuild. Można to zmienić, ustawiając <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> parametr. Rejestrator interpretuje `Importance` parametr.  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu rejestruje komunikaty do wszystkich zarejestrowanych rejestratorów.  
  
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

---
title: Error — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71c257dae17f6846e3e6a4490178b49f28c6dad3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767490"
---
# <a name="error-task"></a>Error — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zatrzymuje kompilację i rejestruje błąd oparte na ocenianą instrukcji warunkowej.  
  
## <a name="parameters"></a>Parametry  
 W następujących tabeli przedstawiono parametry `Error` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Code`|Opcjonalnie `String` parametru.<br /><br /> Kod błędu do skojarzenia z powodu błędu.|  
|`File`|Opcjonalnie `String` parametru.<br /><br /> Nazwa pliku który zawiera błąd. Jeśli nazwa pliku nie zostanie podany, plik zawierający błąd zadania będą używane.|  
|`HelpKeyword`|Opcjonalnie `String` parametru.<br /><br /> Słowo kluczowe pomocy do skojarzenia z powodu błędu.|  
|`Text`|Opcjonalnie `String` parametru.<br /><br /> Tekst błędu, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rejestruje Jeśli `Condition` daje w wyniku parametru `true`.|  
  
## <a name="remarks"></a>Uwagi  
 `Error` Zadanie pozwala [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektów wystawiać rejestratorów tekst błędu i zatrzymać wykonywanie kompilacji.  
  
 Jeśli `Condition` daje w wyniku parametru `true`, kompilacja zostanie zatrzymana i zostanie zarejestrowany błąd. Jeśli `Condition` parametr nie istnieje, błąd jest rejestrowane i zatrzymuje wykonywanie kompilacji. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu sprawdza, czy wszystkie wymagane właściwości są ustawione. Jeśli nie są ustawione, projekt zgłasza zdarzenie błędu i rejestruje wartość `Text` parametru `Error` zadania.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)

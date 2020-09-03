---
title: Błąd — zadanie | Microsoft Docs
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
ms.openlocfilehash: b220d12b872a81cba5f46bd14fdebafaa58cf4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201812"
---
# <a name="error-task"></a>Error — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kończy kompilację i rejestruje błąd na podstawie ocenianej instrukcji warunkowej.  
  
## <a name="parameters"></a>Parametry  
 W tabeli następujące kwestie opisano parametry `Error` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Code`|Opcjonalny `String` parametr.<br /><br /> Kod błędu, który ma zostać skojarzony z błędem.|  
|`File`|Opcjonalny `String` parametr.<br /><br /> Nazwa pliku, który zawiera błąd. Jeśli nie podano nazwy pliku, zostanie użyty plik zawierający zadanie błędu.|  
|`HelpKeyword`|Opcjonalny `String` parametr.<br /><br /> Słowo kluczowe pomocy do skojarzenia z błędem.|  
|`Text`|Opcjonalny `String` parametr.<br /><br /> Tekst błędu, który jest [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zarejestrowana, jeśli `Condition` parametr ma wartość `true` .|  
  
## <a name="remarks"></a>Uwagi  
 `Error`Zadanie umożliwia [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektom wystawianie tekstu błędów w celu rejestrowania i zatrzymania wykonywania kompilacji.  
  
 Jeśli `Condition` parametr ma wartość `true` , kompilacja zostaje zatrzymana i zostanie zarejestrowany błąd. Jeśli `Condition` parametr nie istnieje, ten błąd jest rejestrowany i wykonywanie kompilacji zostanie zatrzymane. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu sprawdza, czy są ustawione wszystkie wymagane właściwości. Jeśli nie są ustawione, projekt zgłasza zdarzenie błędu i rejestruje wartość `Text` parametru `Error` zadania.  
  
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

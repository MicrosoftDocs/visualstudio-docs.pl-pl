---
title: Zadanie ostrzegawcze | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adbddc2fb36e5036e535dfc1049945187fe14ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62558492"
---
# <a name="warning-task"></a>Warning — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rejestruje ostrzeżenie podczas kompilacji oparte na obliczanej instrukcji warunkowej.  
  
## <a name="parameters"></a>Parametry  
 W tabeli następujące kwestie opisano parametry `Warning` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`Code`|Opcjonalny `String` parametr.<br /><br /> Kod ostrzeżenia do skojarzenia z ostrzeżeniem.|  
|`File`|Opcjonalny `String` parametr.<br /><br /> Określa odpowiedni plik, jeśli istnieje. Jeśli plik nie zostanie podany, zostanie użyty plik zawierający zadanie ostrzegawcze.|  
|`HelpKeyword`|Opcjonalny `String` parametr.<br /><br /> Słowo kluczowe pomocy do skojarzenia z ostrzeżeniem.|  
|`Text`|Opcjonalny `String` parametr.<br /><br /> Tekst ostrzegawczy, który zostanie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zarejestrowana w przypadku, gdy `Condition` parametr ma wartość `true` .|  
  
## <a name="remarks"></a>Uwagi  
 `Warning`Zadanie umożliwia [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektom sprawdzenie obecności wymaganej konfiguracji lub właściwości przed przejściem do kolejnego kroku kompilacji.  
  
 Jeśli `Condition` parametr `Warning` zadania jest obliczany `true` , wartość `Text` parametru jest rejestrowany, a kompilacja kontynuuje wykonywanie. Jeśli parametr nie jest `Condition` exisit, tekst ostrzegawczy jest rejestrowany. Aby uzyskać więcej informacji na temat rejestrowania, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu sprawdza właściwości, które są ustawiane w wierszu polecenia. Jeśli nie ma ustawionych właściwości, projekt zgłasza zdarzenie ostrzeżenia i rejestruje wartość `Text` parametru `Warning` zadania.  
  
```  
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
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)

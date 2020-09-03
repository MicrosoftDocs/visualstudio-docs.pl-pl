---
title: Klasa bazowa TaskExtension | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c8e4823ae9a997feae15836962d0c5b8a1f2aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182338"
---
# <a name="taskextension-base-class"></a>TaskExtension — Klasa podstawowa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wiele zadań dziedziczy z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzą z nich. Te parametry są wymienione w tym dokumencie.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry klas bazowych.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby zezwolić na wywoływanie zadań z powrotem.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine2> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby zezwolić na wywoływanie zadań z powrotem.<br /><br /> Jest to wygodna właściwość, dzięki czemu autorzy zadań dziedziczą z tej klasy nie muszą rzutować wartości z `IBuildEngine` na `IBuildEngine2` .|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Opcjonalny <xref:Microsoft.Build.Framework.IBuildEngine3> parametr.<br /><br /> Określa interfejs aparatu kompilacji dostarczony przez hosta.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Opcjonalny <xref:Microsoft.Build.Framework.ITaskHost> parametr.<br /><br /> Określa wystąpienie obiektu hosta (może mieć wartość null). Aparat kompilacji ustawia tę właściwość, jeśli IDE hosta skojarzył obiekt hosta z tym konkretnym zadaniem.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Opcjonalny <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr tylko do odczytu.<br /><br /> Pobiera `TaskLoggingHelperExtension` obiekt, który zawiera metody rejestrowania zadań.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)

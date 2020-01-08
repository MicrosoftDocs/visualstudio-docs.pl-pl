---
title: Klasa bazowa TaskExtension | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58410d1a2dbb2fc477915ac78e30a67b525e59f0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594958"
---
# <a name="taskextension-base-class"></a>Klasa bazowa TaskExtension
Wiele zadań dziedziczy z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Ten łańcuch dziedziczenia dodaje kilka parametrów do zadań, które pochodzą z nich. Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry klas bazowych.

|Parametr|Opis|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Opcjonalny parametr <xref:Microsoft.Build.Framework.IBuildEngine>.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby zezwolić na wywoływanie zadań z powrotem.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Opcjonalny parametr <xref:Microsoft.Build.Framework.IBuildEngine2>.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby zezwolić na wywoływanie zadań z powrotem.<br /><br /> Jest to wygodna właściwość, dzięki czemu autorzy zadań dziedziczą z tej klasy nie muszą rzutować wartości z `IBuildEngine` na `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Opcjonalny parametr <xref:Microsoft.Build.Framework.IBuildEngine3>.<br /><br /> Określa interfejs aparatu kompilacji dostarczony przez hosta.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Opcjonalny parametr <xref:Microsoft.Build.Framework.ITaskHost>.<br /><br /> Określa wystąpienie obiektu hosta (może mieć wartość null). Aparat kompilacji ustawia tę właściwość, jeśli IDE hosta skojarzył obiekt hosta z tym konkretnym zadaniem.|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Opcjonalny <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr tylko do odczytu.<br /><br /> Pobiera obiekt `TaskLoggingHelperExtension`, który zawiera metody rejestrowania zadań.|

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

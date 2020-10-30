---
title: Klasa bazowa TaskExtension | Microsoft Docs
description: Dowiedz się więcej na temat parametrów, które Klasa bazowa Microsoft. Build. Tasks. TaskExtension dodaje do zadań, które dziedziczą z tego elementu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 33808468653cf969719b6da5380da96cc53e490a
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047859"
---
# <a name="taskextension-base-class"></a>TaskExtension, klasa podstawowa

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

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

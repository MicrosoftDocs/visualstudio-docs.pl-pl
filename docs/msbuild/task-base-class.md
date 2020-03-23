---
title: Klasa podstawowa zadania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7d6e0870f809a30bc3feb7ecb7a7302b7729124
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631955"
---
# <a name="task-base-class"></a>Klasa podstawowa zadania

Wiele zadań ostatecznie <xref:Microsoft.Build.Utilities.Task> dziedziczyć z klasy. Ta klasa dodaje kilka parametrów do zadań, które pochodzą z nich. Te parametry są wymienione w tym dokumencie.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry tej klasy podstawowej.

|Parametr|Opis|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parametr <xref:Microsoft.Build.Framework.IBuildEngine> opcjonalny.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby umożliwić zadania do wywołania z powrotem do niego.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parametr <xref:Microsoft.Build.Framework.IBuildEngine2> opcjonalny.<br /><br /> Określa interfejs aparatu kompilacji dostępny dla zadań. Aparat kompilacji automatycznie ustawia ten parametr, aby umożliwić zadania do wywołania z powrotem do niego.<br /><br /> Jest to właściwość wygody, dzięki czemu autorzy zadań dziedziczący z tej klasy nie muszą przerzucać wartości z `IBuildEngine` do `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parametr <xref:Microsoft.Build.Framework.IBuildEngine3> opcjonalny.<br /><br /> Określa interfejs aparatu kompilacji dostarczony przez hosta.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parametr <xref:Microsoft.Build.Framework.ITaskHost> opcjonalny.<br /><br /> Określa wystąpienie obiektu hosta (może mieć wartość null). Aparat kompilacji ustawia tę właściwość, jeśli ide hosta skojarzył obiekt hosta z tym konkretnym zadaniem.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Opcjonalny <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parametr tylko do odczytu.<br /><br /> Obiekt pomocnika rejestrowania..|

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)

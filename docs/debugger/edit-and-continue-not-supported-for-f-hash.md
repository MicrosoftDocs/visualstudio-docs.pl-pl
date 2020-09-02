---
title: 'Edytuj i Kontynuuj nie są obsługiwane w języku F # | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ceb0ca767b1ac6364e103925fb86ed639c3d321d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62851160"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Opcje edytuj i kontynuuj nie są obsługiwane w F# #
Polecenie Edytuj i Kontynuuj nie jest obsługiwane podczas debugowania kodu F #. Podczas sesji debugowania można edytować kod języka F #, ale należy go unikać. Zmiany kodu nie są stosowane podczas sesji debugowania. W związku z tym wszystkie zmiany w kodzie języka F # podczas debugowania spowodują kod źródłowy, który nie pasuje do debugowanego kodu.

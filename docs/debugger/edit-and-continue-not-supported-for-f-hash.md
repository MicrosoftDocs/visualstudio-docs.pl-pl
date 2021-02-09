---
title: 'Edytuj i Kontynuuj nie są obsługiwane w języku F # | Microsoft Docs'
description: 'Edytowanie i kontynuowanie nie jest obsługiwane w przypadku debugowania języka F #. Zmiany w kodzie podczas debugowania nie są stosowane do źródła, więc debugowany kod nie jest zgodny ze źródłem.'
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a686cf91a515d2b7b59d87d7b3ca8e92d4e54c59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871991"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Opcje edytuj i kontynuuj nie są obsługiwane w F# #
Polecenie Edytuj i Kontynuuj nie jest obsługiwane podczas debugowania kodu F #. Podczas sesji debugowania można edytować kod języka F #, ale należy go unikać. Zmiany kodu nie są stosowane podczas sesji debugowania. W związku z tym wszystkie zmiany w kodzie języka F # podczas debugowania spowodują kod źródłowy, który nie pasuje do debugowanego kodu.

---
title: Gdzie można sprawdzić kody błędów Win32? | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8e3dda1b728cd631efe8a84913af3d5c475138d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72728033"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Gdzie można sprawdzić kody błędów Win32?
WINERROR. H w katalogu dołączania domyślnej instalacji systemu zawiera definicje kodu błędów dla funkcji Win32 API.

 Kod błędu można wyszukać, wpisując kod w oknie **czujka** lub oknie dialogowym **QuickWatch** . Na przykład:

`0x80000004,hr`

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego — Często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
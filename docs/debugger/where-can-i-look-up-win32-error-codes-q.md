---
title: Gdzie można sprawdzić kody błędów Win32? | Microsoft Docs
description: Aby wyszukać kod błędu Win32, wprowadź go w Watch lub QuickWatch. Na przykład "0x80000004, HR". Definicje kodu błędu znajdują się w INCLUDE\WINERROR.H.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4eb61a6eda5848277a1da95f9282b396b413ad5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883834"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Gdzie można sprawdzić kody błędów Win32?
WINERROR. H w katalogu dołączania domyślnej instalacji systemu zawiera definicje kodu błędów dla funkcji Win32 API.

 Kod błędu można wyszukać, wpisując kod w oknie **czujka** lub oknie dialogowym **QuickWatch** . Na przykład:

`0x80000004,hr`

## <a name="see-also"></a>Zobacz też
- [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44a006be3b6ecad3ef723c00154354cb35df0049
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149290"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Gdzie można sprawdzić kody błędów Win32?
WINERROR. H w katalogu dołączania domyślnej instalacji systemu zawiera definicje kodu błędów dla funkcji Win32 API.

 Kod błędu można wyszukać, wpisując kod w oknie **czujka** lub oknie dialogowym **QuickWatch** . Na przykład:

`0x80000004,hr`

## <a name="see-also"></a>Zobacz także
- [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
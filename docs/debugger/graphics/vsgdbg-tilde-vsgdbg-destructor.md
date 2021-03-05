---
description: Niszczy wystąpienie klasy VsgDbg.
title: 'VsgDbg:: ~ VsgDbg (destruktor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d90664723695756ebd8acdc7c56bec1fcbd08a31
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155229"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruktor)
Niszczy wystąpienie `VsgDbg` klasy. Jeśli informacje o grafice są aktywnie rejestrowane, plik dziennika grafiki zostanie sfinalizowany i zamknięty, a zasoby, które były używane podczas aktywnie przechwytywania informacji graficznych, są uwalniane.

## <a name="syntax"></a>Składnia

```C++
~VsgDbg();
```

## <a name="see-also"></a>Zobacz też
- [VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)

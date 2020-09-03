---
title: 'VsgDbg:: ~ VsgDbg (destruktor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734795"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruktor)
Niszczy wystąpienie `VsgDbg` klasy. Jeśli informacje o grafice są aktywnie rejestrowane, plik dziennika grafiki zostanie sfinalizowany i zamknięty, a zasoby, które były używane podczas aktywnie przechwytywania informacji graficznych, są uwalniane.

## <a name="syntax"></a>Składnia

```C++
~VsgDbg();
```

## <a name="see-also"></a>Zobacz też
- [VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)
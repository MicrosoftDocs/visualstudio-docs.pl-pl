---
description: Niszczy wystąpienie klasy VsgDbg.
title: VsgDbg::~VsgDbg (destruktor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ddc942d2ef3a33f1f8d843ff5657f76bb58104c4
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232391"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruktor)
Niszczy wystąpienie `VsgDbg` klasy . Jeśli informacje graficzne są aktywnie rejestrowane, plik dziennika grafiki jest finalizowany i zamykany, a zasoby, które były używane podczas aktywnego przechwytywania informacji graficznych, są zwalniane.

## <a name="syntax"></a>Składnia

```C++
~VsgDbg();
```

## <a name="see-also"></a>Zobacz też
- [VsgDbg::VsgDbg (Konstruktor)](vsgdbg-vsgdbg-constructor.md)

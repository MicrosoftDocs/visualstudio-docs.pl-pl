---
description: Konstruuje wystąpienie klasy VsgDbg z przygotowaniem składnika diagnostyki grafiki w aplikacji lub bez niego do aktywnego przechwytywania i nagrywania informacji graficznych na podstawie określonego parametru logicznych.
title: VsgDbg::VsgDbg (konstruktor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3693301aef27e01f2d12fa954f94fcc55fb8dea
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232430"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
Konstruuje wystąpienie klasy z lub bez przygotowania składnika w aplikacji diagnostyki grafiki do aktywnego przechwytywania i nagrywania informacji graficznych domyślnie na podstawie określonego parametru `VsgDbg` logicznych.

## <a name="syntax"></a>Składnia

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametry
 `bDefaultInit`aby określić, że składnik diagnostyki grafiki w aplikacji ma być przygotowany do aktywnego `true` przechwytywania i nagrywania informacji graficznych; `false` w celu określenia, że aplikacja nie powinna być przygotowana do aktywnego przechwytywania i nagrywania informacji graficznych w tej chwili.

## <a name="remarks"></a>Uwagi
 Gdy konstruktor jest wywoływany z ustawionym na , nazwa pliku dziennika grafiki jest określana przez sposób, w jaki symbole `bDefaultInit` preprocesora i są zdefiniowane przed dodaniem ich do `true` `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` `vsgcapture.h` aplikacji.

 Gdy konstruktor jest wywoływany z ustawionym na , składnik diagnostyki grafiki w aplikacji może być przygotowany do aktywnego przechwytywania i nagrywania informacji graficznych w późniejszym czasie przez wywołanie `bDefaultInit` `false` funkcji `Init` .

## <a name="see-also"></a>Zobacz też
- [VsgDbg::~VsgDbg (Destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)

---
title: 'VsgDbg:: VsgDbg (Konstruktor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae94a7cb9572a0975dc1c3717275c384c2e45978
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734759"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
Konstruuje wystąpienie klasy `VsgDbg` z lub bez przygotowania składnika w aplikacji diagnostyki grafiki, aby aktywnie przechwytywać i rejestrować informacje graficzne na podstawie określonego parametru logicznego.

## <a name="syntax"></a>Składnia

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametry
 `bDefaultInit` `true`, aby określić, że składnik w aplikacji diagnostyki grafiki ma być przygotowany do aktywnego przechwytywania i rejestrowania informacji graficznych. `false`, aby określić, że aplikacja nie powinna być przygotowana do aktywnego przechwytywania i rejestrowania informacji graficznych.

## <a name="remarks"></a>Uwagi
 Gdy Konstruktor jest wywoływany z `bDefaultInit` ustawionym na `true`, nazwa pliku dziennika grafiki jest określana na podstawie sposobu definiowania symboli preprocesora `DONT_SAVE_VSGLOG_TO_TEMP` i `VSG_DEFAULT_RUN_FILENAME`, zanim `vsgcapture.h` zostanie uwzględniony w aplikacji.

 Gdy Konstruktor jest wywoływany z `bDefaultInit` ustawionym na `false`, składnik w aplikacji diagnostyki grafiki może być przygotowany do aktywnego przechwytywania i rejestrowania informacji graficznych w późniejszym czasie, wywołując funkcję `Init`.

## <a name="see-also"></a>Zobacz także
- [VsgDbg::~VsgDbg (Destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
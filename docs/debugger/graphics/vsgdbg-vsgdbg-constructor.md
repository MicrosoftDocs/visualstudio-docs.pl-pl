---
title: VsgDbg::VsgDbg (Konstruktor) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db51226c4d980359fd36ee5196e48d7fa4577a37
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723204"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Konstruktor)
Tworzy wystąpienie klasy `VsgDbg` klasy z lub bez przygotowania diagnostyki grafiki aktywnie przechwytywanie i rejestrowanie informacji graficznych domyślnie w oparciu o określony parametr logiczny składnik w aplikacji.

## <a name="syntax"></a>Składnia

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametry
 `bDefaultInit` `true` do określenia, to należy przygotować aktywnie przechwytywanie i rejestrowanie informacji graficznych; składnik w aplikacji Narzędzie Diagnostyka grafiki `false` do określenia, że aplikacja nie powinna być przygotowana do aktywnego przechwytywanie i rejestrowanie informacji graficznych w tej chwili.

## <a name="remarks"></a>Uwagi
 Gdy Konstruktor jest wywoływana z `bDefaultInit` równa `true`, nazwę pliku w pliku dziennika grafiki określają sposób, w jaki `DONT_SAVE_VSGLOG_TO_TEMP` i `VSG_DEFAULT_RUN_FILENAME` symboli preprocesora są zdefiniowane przed `vsgcapture.h` znajduje się w aplikacji.

 Gdy Konstruktor jest wywoływana z `bDefaultInit` równa `false`, składnik w aplikacji Narzędzie Diagnostyka grafiki można przygotować aktywnie przechwytywanie i rejestrowanie informacji graficznych w późniejszym czasie przez wywołanie metody `Init` funkcji.

## <a name="see-also"></a>Zobacz też
- [VsgDbg::~VsgDbg (Destruktor)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
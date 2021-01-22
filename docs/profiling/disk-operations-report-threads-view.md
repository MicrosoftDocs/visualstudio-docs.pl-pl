---
title: Raport operacji dyskowych (Widok wątków) | Microsoft Docs
description: Raport operacje na dyskach przedstawia operacje we/wy dysku w kanałach dyskowych. Sprawdź, jakie informacje są raportowane dla każdego dostępu do dysku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44975999c71b1c331d90aa10f709071cef466cb1
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686535"
---
# <a name="disk-operations-report-threads-view"></a>Raport dotyczący operacji na dysku (Widok wątków)
Raport operacje na dyskach przedstawia operacje we/wy dysku w kanałach dyskowych.

 Dla każdego dostępu do dysku, który występuje w imieniu procesu, który jest profilowany w aktualnie widocznym przedziale czasu, te informacje są raportowane:

- Nazwa i Identyfikator PID procesu, który przeprowadził dostęp do dysku

- Identyfikator wątku, który uzyskał dostęp do dysku

- Nazwa pliku, do którego uzyskano dostęp

- Liczba odczytów dla pliku

- Liczba odczytanych bajtów

- Opóźnienie odczytu (w milisekundach)

- Liczba zapisów

- Liczba zapisanych bajtów

- Opóźnienie zapisu w milisekundach

## <a name="see-also"></a>Zobacz też
- [Widok wątków](../profiling/threads-view-parallel-performance.md)
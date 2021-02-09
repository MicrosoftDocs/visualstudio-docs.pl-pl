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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6b0e15257d67e1d7ff1aaef14c2ebfff3775d6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923730"
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
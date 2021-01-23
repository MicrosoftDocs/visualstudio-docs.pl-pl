---
title: Znaczniki komunikatów | Microsoft Docs
description: Dowiedz się, w jaki sposób można eksportować komunikaty do pliku tekstowego w celu użycia z innymi narzędziami i zawiesić wskaźnik na komunikacie w narzędziu Concurrency Visualizer, aby wyświetlić ciąg komunikatów.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d8e4d493173cb50f62510a9b776701a0b199f47
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720569"
---
# <a name="message-markers"></a>Znaczniki komunikatów
Znacznik komunikatu reprezentuje dane wyjściowe dziennika. Komunikat jest ciągiem, który jest wystawiony przez określony wątek w określonym czasie. Komunikaty można eksportować do pliku tekstowego, który ma być używany z innymi narzędziami. Możesz ustawić wskaźnik na wiadomości w wizualizatorze współbieżności, aby wyświetlić ciąg komunikatu. W [raporcie znaczniki](../profiling/markers-report.md)można wyświetlić wszystkie znaczniki komunikatów.  Na poniższej ilustracji przedstawiono znacznik komunikatu.

## <a name="message-aggregation-markers"></a>Znaczniki agregacji komunikatów
 Czasami wiele komunikatów występuje blisko siebie w wizualizatorze współbieżności, które nie mogą być narysowane pojedynczo. W takim przypadku zostanie wyświetlony *znacznik agregacji komunikatów* reprezentujący bazowe komunikaty. Po umieszczeniu wskaźnika na jednej z tych ikon, w etykietce narzędzia zostanie wyświetlona liczba przedstawionych podstawowych komunikatów. Aby wyświetlić komunikaty, Powiększ.  W przypadku powiększania wszystkich sposobów i nadal uzyskiwania znacznika agregacji w [raporcie znaczniki](../profiling/markers-report.md)można wyświetlić podstawowe komunikaty.

## <a name="see-also"></a>Zobacz także
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)
- [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)
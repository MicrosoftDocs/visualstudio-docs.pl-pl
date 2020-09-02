---
title: Znaczniki komunikatów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c7a173bf0b7f5b3dc2187c0c8574819b2317a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176908"
---
# <a name="message-markers"></a>Znaczniki komunikatu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znacznik komunikatu reprezentuje dane wyjściowe dziennika. Komunikat jest ciągiem, który jest wystawiony przez określony wątek w określonym czasie. Komunikaty można eksportować do pliku tekstowego, który ma być używany z innymi narzędziami. Możesz ustawić wskaźnik na wiadomości w wizualizatorze współbieżności, aby wyświetlić ciąg komunikatu. W [raporcie znaczniki](../profiling/markers-report.md)można wyświetlić wszystkie znaczniki komunikatów.  Na poniższej ilustracji przedstawiono znacznik komunikatu.  
  
## <a name="message-aggregation-markers"></a>Znaczniki agregacji komunikatów  
 Czasami wiele komunikatów występuje blisko siebie w wizualizatorze współbieżności, które nie mogą być narysowane pojedynczo. W takim przypadku zostanie wyświetlony *znacznik agregacji komunikatów* reprezentujący bazowe komunikaty. Po umieszczeniu wskaźnika na jednej z tych ikon, w etykietce narzędzia zostanie wyświetlona liczba przedstawionych podstawowych komunikatów. Aby wyświetlić komunikaty, Powiększ.  W przypadku powiększania wszystkich sposobów i nadal uzyskiwania znacznika agregacji w [raporcie znaczniki](../profiling/markers-report.md)można wyświetlić podstawowe komunikaty.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)   
 [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)

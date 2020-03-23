---
title: Znaczniki wiadomości | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 0b668f0331345e6a1022ef79105614f4a22e91d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62830081"
---
# <a name="message-markers"></a>Znaczniki wiadomości
Znacznik komunikatu reprezentuje dane wyjściowe dziennika. Komunikat jest ciągiem, który jest wystawiany przez określony wątek w określonym czasie. Wiadomości można eksportować do pliku tekstowego do użytku z innymi narzędziami. Można opowiedzieć wskaźnik na komunikat w współbieżności wizualizatora, aby wyświetlić ciąg wiadomości. I można wyświetlić wszystkie znaczniki wiadomości w [raporcie Znaczniki](../profiling/markers-report.md).  Na poniższej ilustracji przedstawiono znacznik wiadomości.

## <a name="message-aggregation-markers"></a>Znaczniki agregacji wiadomości
 Czasami wiele komunikatów występuje tak blisko siebie w wizualizatora współbieżności, że nie można ich narysować indywidualnie. W takim przypadku wyświetlany jest *znacznik agregacji wiadomości* reprezentujący podstawowe komunikaty. Po umieszczeniu wskaźnika na jednej z tych ikon, etykietka narzędzia wyświetla liczbę podstawowych wiadomości, które są reprezentowane. Aby wyświetlić wiadomości, powiększ.  Jeśli powiększysz cały sposób i nadal otrzymujesz znacznik agregacji, możesz wyświetlić podstawowe wiadomości w [raporcie znaczników](../profiling/markers-report.md).

## <a name="see-also"></a>Zobacz też
- [Znaczniki wizualizatora współbieżności](../profiling/concurrency-visualizer-markers.md)
- [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)
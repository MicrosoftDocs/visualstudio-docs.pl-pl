---
title: Widok caller-callee | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bab816a0b71adef190a7d919b5ada7138a6a0e7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779717"
---
# <a name="callercallee-view"></a>Widok wywołujący/wywoływany
W widoku Wywołujący/Wywoływany są wyświetlane informacje profilowania wybranej funkcji oraz jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki:

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i pokazuje informacje profilowania dla wybranej funkcji. Wartości obejmują wszystkie wywołania funkcji, które zostały zebrane w przebiegu profilowania.

 **Funkcje, które wywołały bieżącą funkcję,** są wyświetlane w górnej siatce i pokazują liczbę wartości wybranej (bieżącej) funkcji, które zostały wygenerowane przez wywołania z funkcji wywołującego (nadrzędnego).

 **Funkcje, które zostały wywołane przez bieżącą funkcję** jest wyświetlany w dolnej siatce i pokazuje informacje profilowania dla wywoływane (podrzędne) funkcje wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

 Kolumny, które są dostępne w widoku wywołującego/wywoływania zależą od metody profilowania (próbkowania lub instrumentacji), która została użyta do zbierania danych i czy dane pamięci .NET zostały zebrane w przebiegu profilowania.

 Można wybrać inną funkcję jako bieżącą funkcję w środkowej części widoku Raport, klikając dwukrotnie jedną z funkcji wymienionych w pozostałych dwóch częściach widoku. Widok Raport jest aktualizowany automatycznie w celu odzwierciedlenia zmian.

 Dane można sortować, klikając nazwy kolumn. Dodatkowe kolumny można dodać do widoku wywołującego/wywoływania. Aby uzyskać więcej informacji, zobacz [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).

## <a name="see-also"></a>Zobacz też
- [Widok wywołujący/wywoływany — dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
- [Widok rozmówcy/wywoływania — dane oprzyrządowania](../profiling/caller-callee-view-instrumentation-data.md)
- [Widok wywołujący/wywoływany — dane instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Widok wywołujący/wywoływany — dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Widok wywołujący/wywoływany — dane rywalizacji](../profiling/caller-callee-view-contention-data.md)

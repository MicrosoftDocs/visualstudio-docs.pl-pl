---
description: Widok wywołujący/wywoływany wyświetla informacje profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych.
title: Widok Caller-Callee | Microsoft Docs
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 375c0f366fb32fcbe8187c2c4b5d1d3d632f7260
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223709"
---
# <a name="callercallee-view"></a>Widok wywołujący/wywoływany
Widok wywołujący/wywoływany wyświetla informacje profilowania dla wybranej funkcji i jej funkcji nadrzędnych i podrzędnych. Widok wywołujący/wywoływany zawiera trzy siatki:

 **Bieżąca funkcja** jest wyświetlana w środkowej siatce i zawiera informacje profilowania dla wybranej funkcji. Wartości obejmują wszystkie wywołania funkcji, które zostały zebrane w ramach uruchomienia profilowania.

 **Funkcje, które wywołały bieżącą funkcję** , są wyświetlane w górnej siatce i pokazują liczbę wartości wybranej funkcji (bieżącej), która została wygenerowana przez wywołania z funkcji wywołującej (nadrzędnej).

 **Funkcje, które zostały wywołane przez bieżącą funkcję** , są wyświetlane w dolnej siatce i pokazują informacje profilowania dla funkcji wywoływanych (podrzędnych) wybranej funkcji, gdy funkcja podrzędna została wywołana przez bieżącą funkcję.

 Kolumny, które są dostępne w widoku wywołującego/wywoływanego, zależą od metody profilowania (próbkowania lub Instrumentacji), która została użyta do zebrania danych oraz od tego, czy dane pamięci platformy .NET zostały zebrane w ramach uruchomienia profilowania.

 Możesz wybrać inną funkcję jako bieżącą funkcję w środkowej części widoku Raport, klikając dwukrotnie jedną z funkcji, które są wymienione w pozostałych dwóch częściach widoku. Widok raportu jest automatycznie aktualizowany w celu odzwierciedlenia zmian.

 Dane można sortować, klikając pozycję nazwy kolumn. Dodatkowe kolumny można dodać do widoku wywołującego/wywoływanego. Aby uzyskać więcej informacji, zobacz [How to: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).

## <a name="see-also"></a>Zobacz też
- [Widok wywołujący/wywoływany-Dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
- [Widok wywołujący/wywoływany-Dane instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)
- [Widok elementu wywołującego/wywoływanego — dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Widok wywołujący/wywoływany — Dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Widok wywołujący/wywoływany-dane rywalizacji](../profiling/caller-callee-view-contention-data.md)

---
title: Widok wywołującego/wywoływanego — dane próbkowania pamięci platformy .NET | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Caller/Callee view
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f3e07510f38c18f7d8e4a52d788935400b5a9388
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627249"
---
# <a name="callercallee-view---net-memory-sampling-data"></a>Widok wywołujący/wywoływany - dane próbkowania pamięci platformy .NET
Widok wywołujący/wywoływany wyświetla dane dla wybranej funkcji i jej funkcji nadrzędne i podrzędne profilowania pamięci .NET. Widok wywołujący/wywoływany zawiera trzy siatki.

 **Bieżąca funkcja** są wyświetlane w siatce Środkowej i zawiera informacje na temat wybranej funkcji profilowania pamięci. Wartości obejmują wszystkie próbki wywołania funkcji.

 **Funkcje, które wywołały bieżącą funkcję** są wyświetlane w siatce górnym i przedstawia ilość wartość wybranej funkcji (bieżącego), który został wygenerowany przez wywołania funkcji wywołującego (nadrzędnego).

 **Funkcje, które zostały wywołane przez bieżącą funkcję** są wyświetlane w siatce dolnej i pokazuje dane dla funkcji elementu wywoływanego (podrzędne) wybranej funkcji profilowania, gdy funkcja podrzędnych została wywołana przez bieżącą funkcję pamięci.

 Kliknij dwukrotnie wywołujący lub wywoływany funkcja wiersz się wiersz bieżącą funkcję.

|Kolumna|Opis|
|------------|-----------------|
|**Identyfikator procesu**|Identyfikator procesu (PID) uruchomienia profilowania.|
|**Nazwa procesu**|Nazwa procesu.|
|**Nazwa modułu**|Nazwa modułu, która zawiera funkcję.|
|**Ścieżka modułu**|Ścieżka modułu, która zawiera funkcję.|
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji.|
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|
|**Adres funkcji**|Adres funkcji.|
|**Typ**|Kontekst funkcji:<br /><br /> **0** -bieżącej funkcji<br /><br /> **1** — funkcji wywołującej bieżącą funkcję<br /><br /> **2** — funkcja, która jest wywoływana przez bieżącą funkcję<br /><br /> Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|
|**Poziom**|Głębokość funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|
|**Przydziały włączne**|-Aby uzyskać bieżącą funkcję liczby obiektów przydzielonych za pomocą funkcji podczas uruchomienia profilowania. Liczba ta obejmuje obiekty, które zostały utworzone w funkcjach / / wywoływany.<br />— W przypadku funkcji wywołującego liczba przydziałów włącznych bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji.<br />— W przypadku funkcji / / wywoływany liczbę obiektów, które zostały przydzielone przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Liczba uwzględnia alokacji dokonanych przez funkcje, które zostały wywołane przez funkcję / / wywoływany.|
|**% Przydziałów włącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów włącznych tej funkcji.|
|**Przydziały wyłączne**|— W przypadku funkcji bieżącej liczby obiektów, które zostały utworzone podczas wykonywania funkcji kodu w treści funkcji (oznacza to, kiedy funkcja znajdowała się w górnej części stosu wywołań). Liczba nie obejmuje obiekty, które zostały utworzone w funkcjach, które zostały wywołane przez funkcję.<br />— W przypadku funkcji wywołującego liczba przydziałów wyłącznych bieżącej funkcji, które zostały wygenerowane przez wywołania z tej funkcji.<br />— W przypadku funkcji / / wywoływany liczbę obiektów, które zostały utworzone przez wystąpienia tej funkcji, które zostały wywołane przez bieżącą funkcję. Liczba nie obejmuje obiekty, które zostały utworzone przez funkcje, które zostały wywołane przez funkcję / / wywoływany.|
|**% Przydziałów wyłącznych**|Procent wszystkich obiektów, które zostały utworzone w profilowania, były przydziałów włącznych tej funkcji.|
|**Bajty włączne**|-Aby uzyskać bieżącą funkcję liczbę bajtów pamięci przydzielonych za pomocą funkcji podczas uruchomienia profilowania. Liczba uwzględnia pamięci, która została przydzielona w funkcjach, które zostały wywołane przez tę funkcję.<br />— Aby wywołujący funkcję liczba bajtów włącznych bieżącej funkcji, które zostały wygenerowane z wywołań przez funkcję obiekt wywołujący.<br />— W przypadku funkcji / / wywoływany liczba bajtów przydzielonych przez wystąpienia tej funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba uwzględnia bajtów przydzielonych przez funkcje, które zostały wywołane przez funkcję / / wywoływany.|
|**% Bajtów włącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były przydziałów włącznych tej funkcji.|
|**Bajty wyłączne**|-Aby uzyskać bieżącą funkcję liczbę bajtów pamięci przydzielonych za pomocą funkcji podczas uruchomienia profilowania. Ta liczba nie obejmuje pamięci, która została przydzielona przez funkcje, które zostały wywołane przez bieżącą funkcję.<br />— Aby wywołujący funkcję liczbę bajtów wyłącznych bieżącej funkcji, które zostały wygenerowane przez wywołuje funkcję obiekt wywołujący.<br />— W przypadku funkcji / / wywoływany liczba bajtów przydzielonych przez wystąpień funkcji, które zostały wygenerowane przez wywołania z bieżącej funkcji. Liczba nie obejmuje bajtów przydzielonych przez funkcje, które zostały wywołane przez funkcję / / wywoływany.|
|**% Bajtów wyłącznych**|Procent wszystkich bajtów pamięci przydzielonych w uruchomienia profilowania były przydziałów wyłącznych tej funkcji.|

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)
- [Widok wywołujący/wywoływany - dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Widok wywołujący/wywoływany - dane próbkowania](../profiling/caller-callee-view-sampling-data.md)
- [Widok wywołujący/wywoływany - dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)
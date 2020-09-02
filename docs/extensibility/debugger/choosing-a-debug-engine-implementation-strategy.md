---
title: Wybór strategii implementacji aparatu debugowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739129"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Wybierz strategię implementacji aparatu debugowania
Użyj architektury czasu wykonywania, aby określić strategię implementacji aparatu debugowania (DE). Aparat debugowania można utworzyć w procesie dla debugowanego programu. Utwórz aparat debugowania w procesie do Menedżera debugowania sesji programu Visual Studio (SDM). Można też utworzyć poza procesem aparat debugowania do obu tych elementów. Poniższe wskazówki powinny pomóc w wyborze spośród tych trzech strategii.

## <a name="guidelines"></a>Wytyczne
 Chociaż istnieje możliwość, że stan "poza procesem" jest używany zarówno przez model SDM, jak i debugowany program, zazwyczaj nie jest to konieczne. Wywołania między granicami procesu są stosunkowo wolne.

 Aparaty debugowania są już udostępniane dla natywnego środowiska uruchomieniowego Win32 i dla środowiska uruchomieniowego języka wspólnego. Jeśli konieczne jest zamienienie elementu DE dla każdego środowiska, należy utworzyć w trakcie procesu w modelu SDM.

 W przeciwnym razie można utworzyć w procesie proces w języku SDM lub w trybie w procesie, który jest debugowany. Należy rozważyć, czy ewaluatora wyrażeń dla elementu DE wymaga częstego dostępu do magazynu symboli programu. Lub, jeśli magazyn symboli można załadować do pamięci, aby uzyskać szybki dostęp. Należy również wziąć pod uwagę następujące podejścia:

- Jeśli nie ma wielu wywołań między ewaluatora wyrażeń i magazynem symboli, lub jeśli magazyn symboli można odczytać w przestrzeni pamięci modelu SDM, Utwórz w procesie proces do modelu SDM. Po dołączeniu do programu należy zwrócić identyfikator CLSID aparatu debugowania do modelu SDM. Model SDM używa tego identyfikatora CLSID do tworzenia wystąpienia w procesie dla DE.

- Jeśli DE musi wywoływać program w celu uzyskania dostępu do magazynu symboli, należy utworzyć w trakcie procesu w programie. W takim przypadku program tworzy wystąpienie elementu DE.

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

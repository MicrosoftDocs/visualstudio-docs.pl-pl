---
title: Wybór strategii implementacji aparatu debugowania | Microsoft Docs
description: Dowiedz się, jak architektura czasu wykonywania ułatwia wybór spośród kilku strategii dla implementacji aparatu debugowania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2b87d61586fb4acc360b5f5202b1219199c6a24b
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914299"
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

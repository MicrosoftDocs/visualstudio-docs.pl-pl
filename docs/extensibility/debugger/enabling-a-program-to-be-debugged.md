---
title: Włączanie debugowania programu | Microsoft Docs
description: Dowiedz się, jak uruchomić aparat debugowania lub dołączyć aparat debugowania do istniejącego programu w celu debugowania programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac9a43a0ec539dd978710c23c9b44f27eac81799
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915261"
---
# <a name="enable-a-program-to-be-debugged"></a>Włącz debugowanie programu
Zanim aparat debugowania (DE) będzie mógł debugować program, należy najpierw uruchomić go lub dołączyć do istniejącego programu.

## <a name="in-this-section"></a>W tej sekcji
 [Pobierz port](../../extensibility/debugger/getting-a-port.md) W tym artykule omówiono, jak uzyskać port jako pierwszy krok w celu umożliwienia debugowania programu.

 [Rejestrowanie programu](../../extensibility/debugger/registering-the-program.md) Wyjaśnia następny krok w celu włączenia debugowania programu: zarejestrowanie go z portem. Po zarejestrowaniu program może być debugowany przez proces dołączania lub debugowania just-in-Time (JIT).

 [Dołącz do programu](../../extensibility/debugger/attaching-to-the-program.md) Wyjaśnia następny krok: dołączanie debugera do programu.

 [Dołączanie na podstawie uruchamiania](../../extensibility/debugger/launch-based-attachment.md) Opisuje załącznik na podstawie uruchamiania do programu, który jest automatycznie uruchamiany przez model SDM.

 [Wyślij wymagane zdarzenia](../../extensibility/debugger/sending-the-required-events.md) Przeprowadzi Cię przez wymagane zdarzenia podczas tworzenia aparatu debugowania (DE) i dołączenia go do programu.

## <a name="related-sections"></a>Sekcje pokrewne
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definiuje aparat debugowania (DE) i opisuje usługi zaimplementowane za pomocą DE Interfaces oraz jak mogą spowodować przejście debugera między różnymi trybami operacyjnymi.

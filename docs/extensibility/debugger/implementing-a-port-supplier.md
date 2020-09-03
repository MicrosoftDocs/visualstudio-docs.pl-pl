---
title: Implementowanie dostawcy portów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738558"
---
# <a name="implement-a-port-supplier"></a>Implementowanie dostawcy portu
Dostawca portu dostarcza porty na żądanie do Menedżera debugowania sesji (SDM). Dostawca portu musi być zaimplementowany podczas debugowania na komputerze nienależącym do modelu DCOM lub w przypadku, gdy nowe urządzenie wymaga obsługi. Na przykład w celu zapewnienia debugowania na telefonie komórkowym można skonfigurować dostawcę portu, który udostępnia porty, które nawiązują połączenie z telefonem komórkowym (prawdopodobnie przez połączenie IR lub z komórką) i wylicza procesy i programy uruchomione na telefonie.

 W przypadku debugowania programów na maszynach z systemem Windows (w tym debugowanie zdalne) program Visual Studio udostępnia dostawcy portów dla procesów natywnego i środowiska uruchomieniowego języka wspólnego (CLR), więc nie ma potrzeby konfigurowania własnego dostawcy portów w takich przypadkach.

## <a name="in-this-section"></a>W tej sekcji
 [Implementowanie i rejestrowanie dostawcy portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) Omawia, w jaki sposób model SDM współdziała z dostawcą portów i jego portami.

 [Wymagane interfejsy dostawcy portów](../../extensibility/debugger/required-port-supplier-interfaces.md) Dokumentuje interfejsy, które należy zaimplementować w celu uzyskania dostawcy portów.

## <a name="related-sections"></a>Sekcje pokrewne
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md) Opisuje główne koncepcje dotyczące architektury debugowania.

## <a name="see-also"></a>Zobacz też
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

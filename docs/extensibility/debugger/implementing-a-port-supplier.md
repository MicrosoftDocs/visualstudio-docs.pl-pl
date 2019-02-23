---
title: Implementowanie dostawcy portu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d6875baf72d94494a1abaea9260e344b236f83c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685927"
---
# <a name="implement-a-port-supplier"></a>Implementowanie dostawcy portu
Dostawcy portu dostarcza portów na żądanie Menedżer debugowania sesji (SDM). Podczas debugowania na maszynie bez modelu DCOM, lub gdy nowe urządzenie wymaga obsługi, należy zaimplementować dostawcy portu. Na przykład aby umożliwić debugowanie na telefon komórkowy, może być skonfigurowaniu dostawcy portu, który udostępnia porty, które połączenia na telefon komórkowy (prawdopodobnie przez środowisko IR lub połączenia komórki) i wylicza procesów i programy uruchomione na telefonie.

 Debugowanie programów na komputerach z systemem Windows (w tym zdalnego debugowania) Visual Studio udostępnia dostawcy portów dla natywnych i procesów środowiska uruchomieniowego języka wspólnego (CLR), więc nie musisz konfigurować własnego dostawcy portu w tych przypadkach.

## <a name="in-this-section"></a>W tej sekcji
 [Implementowanie i rejestrowanie dostawcy portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) w tym artykule omówiono, jak SDM współdziała z portu dostawcy i jego portów.

 [Wymagane interfejsy dostawcy portów](../../extensibility/debugger/required-port-supplier-interfaces.md) dokumenty interfejsów musi implementować, aby pobrać dostawcy portu.

## <a name="related-sections"></a>Sekcje pokrewne
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md) opisano główne pojęcia dotyczące architektury debugowania.

## <a name="see-also"></a>Zobacz także
 [Rozszerzeń debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
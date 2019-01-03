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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cd068f9c669b898ac3d29dadccffb6edd1e0c783
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985527"
---
# <a name="implement-a-port-supplier"></a>Implementowanie dostawcy portu
Dostawcy portu dostarcza portów na żądanie Menedżer debugowania sesji (SDM). Podczas debugowania na maszynie bez modelu DCOM, lub gdy nowe urządzenie wymaga obsługi, należy zaimplementować dostawcy portu. Na przykład aby umożliwić debugowanie na telefon komórkowy, może być skonfigurowaniu dostawcy portu, który udostępnia porty, które połączenia na telefon komórkowy (prawdopodobnie przez środowisko IR lub połączenia komórki) i wylicza procesów i programy uruchomione na telefonie.  
  
 Debugowanie programów na komputerach z systemem Windows (w tym zdalnego debugowania) Visual Studio udostępnia dostawcy portów dla natywnych i procesów środowiska uruchomieniowego języka wspólnego (CLR), więc nie musisz konfigurować własnego dostawcy portu w tych przypadkach.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie i rejestrowanie dostawcy portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 W tym artykule omówiono, jak SDM współdziała z portu dostawcy i jego portów.  
  
 [Wymagane interfejsy dostawcy portów](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Dokumenty interfejsów, którą musi implementować, aby uzyskać dostawcy portu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 W tym artykule opisano główne pojęcia dotyczące architektury debugowania.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzeń debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
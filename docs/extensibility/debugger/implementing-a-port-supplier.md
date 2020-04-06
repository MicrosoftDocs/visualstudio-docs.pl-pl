---
title: Wdrożenie dostawcy portu | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738558"
---
# <a name="implement-a-port-supplier"></a>Wdrażanie dostawcy portu
Dostawca portu dostarcza porty na żądanie do menedżera debugowania sesji (SDM). Dostawca portu musi być zaimplementowany podczas debugowania do komputera innego niż DCOM lub gdy nowe urządzenie wymaga pomocy technicznej. Na przykład, aby zapewnić debugowanie do telefonu komórkowego, można skonfigurować dostawcę portu, który udostępnia porty, które łączą się z telefonem komórkowym (być może za pomocą podczerwenia lub połączenia komórkowego) i wylicza procesy i programy uruchomione w telefonie.

 W przypadku programów debugowania na komputerach z systemem Windows (w tym zdalnego debugowania) program Visual Studio udostępnia dostawców portów dla procesów clr (Native i Common Language Runtime), więc nie ma potrzeby konfigurowania własnego dostawcy portu w tych przypadkach.

## <a name="in-this-section"></a>W tej sekcji
 [Wdrażanie i rejestrowanie dostawcy portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) W tym artykule omówiono sposób interakcji sdm z dostawcą portu i jego portów.

 [Wymagane interfejsy dostawców portów](../../extensibility/debugger/required-port-supplier-interfaces.md) Dokumenty interfejsy, które należy zaimplementować, aby uzyskać dostawcę portu.

## <a name="related-sections"></a>Powiązane sekcje
 [Pojęcia debugera](../../extensibility/debugger/debugger-concepts.md) W tym artykule opisano główne debugowanie koncepcji architektury.

## <a name="see-also"></a>Zobacz też
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

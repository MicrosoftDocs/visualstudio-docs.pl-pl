---
title: Implementowanie dostawcy portu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0596809ceccd3d528e3276f2ed310a4835c836eb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738759"
---
# <a name="implementing-a-port-supplier"></a>Implementowanie dostawcy portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dostawcy portu dostarcza portów na żądanie Menedżer debugowania sesji (SDM). Dostawcy portu musi być implementowane podczas debugowania na maszynie bez modelu DCOM, lub gdy nowe urządzenie musi być obsługiwane. Na przykład aby umożliwić debugowanie na telefon komórkowy, można wdrożyć dostawcy portu, który udostępnia porty, które łączą na telefon komórkowy (być może za pomocą środowiska IR lub połączenia komórki) i wylicza procesów i programy uruchomione na telefonie.  
  
 Debugowanie programów na komputerach z systemem Windows (w tym zdalnego debugowania) program Visual Studio udostępnia dostawcy portów dla natywnych i procesów środowiska uruchomieniowego języka wspólnego (CLR), więc nie ma potrzeby implementowanie dostawcy portu w przypadkach.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie i rejestrowanie dostawcy portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 W tym artykule omówiono, jak SDM współdziała z portu dostawcy i jego portów.  
  
 [Wymagane interfejsy dostawcy portów](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Dokumenty, interfejsy, które muszą zostać zaimplementowane w celu uzyskania dostawcy portu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 W tym artykule opisano główne pojęcia dotyczące architektury debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)


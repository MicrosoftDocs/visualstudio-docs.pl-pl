---
title: Implementowanie dostawcy portu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54755602"
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

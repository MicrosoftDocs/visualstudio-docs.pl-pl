---
title: Implementowanie dostawcy portów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152678"
---
# <a name="implementing-a-port-supplier"></a>Implementowanie dostawcy portu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dostawca portu dostarcza porty na żądanie do Menedżera debugowania sesji (SDM). Dostawca portu musi być zaimplementowany podczas debugowania na komputerze nienależącym do modelu DCOM lub w przypadku, gdy nowe urządzenie musi być obsługiwane. Na przykład w celu zapewnienia debugowania na telefonie komórkowym można zaimplementować dostawcę portu, który dostarcza porty łączące się z telefonem komórkowym (np. za pomocą połączenia IR lub z komórką) i wylicza procesy i programy uruchomione na telefonie.  
  
 W przypadku debugowania programów na maszynach z systemem Windows (w tym debugowanie zdalne) program Visual Studio udostępnia dostawcy portów dla procesów natywnego i środowiska uruchomieniowego języka wspólnego (CLR), dzięki czemu w takich przypadkach nie ma potrzeby implementowania własnego dostawcy portów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Implementowanie i rejestrowanie dostawcy portu](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Omawia, w jaki sposób model SDM współdziała z dostawcą portów i jego portami.  
  
 [Wymagane interfejsy dostawcy portów](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Dokumentuje interfejsy, które muszą zostać wdrożone w celu uzyskania dostawcy portów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)  
 Opisuje główne koncepcje dotyczące architektury debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

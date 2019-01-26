---
title: Za pomocą Menedżera tekstu do monitorowania ustawień globalnych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29f054a5b584f7cf5471e783d28e857994c1a5a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989370"
---
# <a name="use-the-text-manager-to-monitor-global-settings"></a>Ustawienia globalne monitorowanie za pomocą Menedżera tekstu
W przypadku zastosowania edytorze podstawowych, należy monitorować zmiany wprowadzone do ustawień globalnych, ponieważ te zmiany mogą wpłynąć na wystąpienie edytora. Możesz śledzić zmiany przez nasłuchiwanie zdarzeń zgłaszanych przez Menedżer tekstu. Na przykład po określeniu globalne preferencje wygląd i zachowanie składnika w edytorze podstawowych, takich jak jego obiekt danych dokumentów, Menedżer tekstu przechowuje te informacje i przesyła je do wszystkich klientów, których to dotyczy.  
  
## <a name="text-manager-functions"></a>Funkcje Menedżera tekstowe  
 Menedżer tekstu wywołuje zdarzenia, dla liczby ustawienia, takie jak następujące:  
  
- Czy bufor jest pod kontrolą kodu źródłowego  
  
- Jak zarejestrować dla powiadomień o zmianie pliku  
  
- Sposób śledzić widoków, które są skojarzone z niektórych buforów  
  
- Preferencje Kolorowanie tekstu  
  
- Karty w stosunku do miejsca preferencje  
  
  Preferencje, które są unikatowe dla danego języka nie są zarządzane przez Menedżera tekstu. Te ustawienia muszą być zarządzane przez poszczególne usługi języka.  
  
  Powiadomienie o zdarzeniu Menedżera tekstu jest świadczona przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfejsu. Implementuje ten interfejs na komputerze klienckim obiektu do obsługi zdarzeń zgłoszone przez Menedżera tekstu. Zarejestruj te zdarzenia za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfejsu na Menedżer tekstu.  
  
## <a name="see-also"></a>Zobacz także  
 [W edytorze podstawowych](../extensibility/inside-the-core-editor.md)   
 [Funkcje edytora](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
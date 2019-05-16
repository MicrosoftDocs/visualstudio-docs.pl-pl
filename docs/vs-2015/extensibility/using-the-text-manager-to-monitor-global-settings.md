---
title: Za pomocą Menedżera tekstu do monitorowania ustawień globalnych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695465"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Za pomocą Menedżera tekstu do monitorowania ustawień globalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku zastosowania edytorze podstawowych, należy monitorować zmiany wprowadzone do ustawień globalnych, ponieważ te zmiany mogą wpłynąć na wystąpienie edytora. Możesz śledzić zmiany przez nasłuchiwanie zdarzeń zgłaszanych przez Menedżer tekstu. Na przykład po określeniu globalne preferencje wygląd i zachowanie składnika w edytorze podstawowych, takich jak jego obiekt danych dokumentów, Menedżer tekstu przechowuje te informacje i przesyła je do wszystkich klientów, których to dotyczy.  
  
## <a name="text-manager-functions"></a>Funkcje Menedżera tekstu  
 Menedżer tekstu wywołuje zdarzenia, dla liczby ustawienia, takie jak następujące:  
  
- Czy bufor jest pod kontrolą kodu źródłowego  
  
- Jak zarejestrować dla powiadomień o zmianie pliku  
  
- Sposób śledzić widoków, które są skojarzone z niektórych buforów  
  
- Preferencje Kolorowanie tekstu  
  
- Karty w stosunku do miejsca preferencje  
  
  Preferencje, które są unikatowe dla danego języka nie są zarządzane przez Menedżera tekstu. Te ustawienia muszą być zarządzane przez poszczególne usługi języka.  
  
  Powiadomienie o zdarzeniu Menedżera tekstu jest świadczona przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfejsu. Implementuje ten interfejs na komputerze klienckim obiektu do obsługi zdarzeń zgłoszone przez Menedżera tekstu. Zarejestruj te zdarzenia za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfejsu na Menedżer tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [W edytorze podstawowych](../extensibility/inside-the-core-editor.md)   
 [Funkcje edytora](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)

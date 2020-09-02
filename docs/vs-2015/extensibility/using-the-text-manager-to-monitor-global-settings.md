---
title: Używanie Menedżera tekstów do monitorowania ustawień globalnych | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695465"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Używanie menedżera tekstu do monitorowania ustawień globalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku zaimplementowania edytora podstawowego należy monitorować zmiany wprowadzone w ustawieniach globalnych, ponieważ te zmiany mogą wpływać na wystąpienie edytora. Można śledzić zmiany, nasłuchiwanie zdarzeń zgłaszanych przez Menedżera tekstu. Na przykład po określeniu preferencji globalnych dla wyglądu lub zachowania składnika w edytorze podstawowym, takiego jak obiekt danych dokumentu, Menedżer tekstu przechowuje te informacje i komunikuje go wszystkim klientom, których dotyczy problem.  
  
## <a name="text-manager-functions"></a>Funkcje Menedżera tekstu  
 Menedżer tekstów zgłasza zdarzenia dla wielu ustawień, w tym następujące:  
  
- Czy bufor znajduje się pod kontrolą kodu źródłowego  
  
- Jak zarejestrować się w celu otrzymywania powiadomień o zmianach plików  
  
- Jak śledzić, które widoki są skojarzone z określonymi buforami  
  
- Preferencje kolorowania tekstu  
  
- Preferencje tabulacji i miejsca  
  
  Preferencje, które są unikatowe dla danego języka, nie są zarządzane przez Menedżera tekstu. Te ustawienia muszą być zarządzane przez poszczególne usługi językowe.  
  
  Powiadomienie o zdarzeniu dla Menedżera tekstów jest dostarczane przez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interfejs. Zaimplementuj ten interfejs w obiekcie klienta, aby obsługiwać zdarzenia zgłoszone przez Menedżera tekstu. Możesz zarejestrować się w celu uzyskania tych zdarzeń za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfejsu w Menedżerze tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wewnątrz edytora podstawowego](../extensibility/inside-the-core-editor.md)   
 [Funkcje edytora](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)

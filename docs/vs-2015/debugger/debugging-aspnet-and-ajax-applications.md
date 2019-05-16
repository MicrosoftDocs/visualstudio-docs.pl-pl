---
title: Debugowanie aplikacji ASP.NET i AJAX | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- debugging ASP.NET Web applications
- debugging [ASP.NET], about ASP.NET debugging
- WCF, debugging
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0645cd28e6124e31e19b03489661c6828799cf4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686740"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Debugowanie aplikacji ASP.NET i AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web jest podobne do debugowania formularza Windows lub innej aplikacji Windows, ponieważ oba rodzaje aplikacji obejmują formantów i zdarzeń. Istnieją jednak również podstawowe różnice między dwoma rodzajami aplikacji:  
  
- Rejestrowanie informacji o stanie jest bardziej złożone w aplikacji sieci Web.  
  
- W aplikacji Windows można debugować kodu jest przede wszystkim w jednej lokalizacji. w aplikacji sieci Web kod może być na kliencie i na serwerze. Gdy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod to wszystko na serwerze, mogą istnieć JavaScript lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kodu na komputerze klienckim.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przygotowywanie do debugowania ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 W tym artykule opisano kroki, które są wymagane, aby włączyć debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji.  
  
 [Debugowanie aplikacji internetowych](../debugger/debugging-web-applications.md)  
 W tym artykule omówiono sposób debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji, w tym aplikacji skryptu z włączoną obsługą technologii AJAX.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)  
 Wyjaśnia, dlaczego tylko mój kod, należy włączyć debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] wyjątków.  
  
 [Debugowanie i śledzenie Ajax aplikacje — Przegląd](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 W tym artykule omówiono niektóre techniki i narzędzia, które mogą pomóc w debugowaniu kodu AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Debugowanie kodu szybciej przy użyciu funkcji IntelliTrace można rejestrować i przeglądać historię stanu aplikacji bez konieczności ponownego uruchamiania aplikacji, jak często. Można wyświetlić informacje o zdarzenia i wywołania, które występują podczas uruchamiania aplikacji, a następnie rozpocząć debugowanie w tych punktach w czasie. Wymaga programu Visual Studio Ultimate.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)

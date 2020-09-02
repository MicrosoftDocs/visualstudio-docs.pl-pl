---
title: Debugowanie aplikacji ASP.NET i AJAX | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686740"
---
# <a name="debugging-aspnet-and-ajax-applications"></a>Debugowanie aplikacji ASP.NET i AJAX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web jest podobne do debugowania formularza systemu Windows lub dowolnej innej aplikacji systemu Windows, ponieważ oba rodzaje aplikacji obejmują kontrolki i zdarzenia. Istnieją jednak również podstawowe różnice między dwoma rodzajami aplikacji:  
  
- Śledzenie stanu jest bardziej skomplikowane w aplikacji sieci Web.  
  
- W aplikacji systemu Windows kod, który ma być debugowany, znajduje się głównie w jednej lokalizacji. w aplikacji sieci Web kod może być na kliencie i na serwerze. Chociaż [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kod jest na serwerze, na kliencie może być również język JavaScript lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kod.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przygotowywanie do debugowania ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Zawiera opis czynności, które są wymagane do włączenia debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji.  
  
 [Debugowanie aplikacji internetowych](../debugger/debugging-web-applications.md)  
 Omawia sposób debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji, w tym aplikacji skryptów obsługujących technologię AJAX.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)  
 Wyjaśnia, dlaczego Tylko mój kod muszą być włączone na potrzeby debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] wyjątków.  
  
 [Debugowanie i śledzenie aplikacji Ajax — Omówienie](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)  
 Omawia kilka technik i narzędzi, które mogą ułatwić Debugowanie kodu AJAX.  
  
 [IntelliTrace](../debugger/intellitrace.md)  
 Szybciej Debuguj kod przy użyciu IntelliTrace, aby rejestrować i przeglądać historię stanu aplikacji bez konieczności ponownego uruchamiania aplikacji. Możesz wyświetlić informacje o zdarzeniach i wywołaniach, które wystąpiły podczas uruchamiania aplikacji, i rozpocząć debugowanie od tych punktów w czasie. Wymaga Visual Studio Ultimate.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md)   
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)

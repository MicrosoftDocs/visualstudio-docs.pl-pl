---
title: Debugowanie just in Time, okno dialogowe Opcje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b3bd6c6ee32145a94dbc4b751834ecc003f2bdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201107"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-in-time, debugowanie, opcje ― Okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać dostęp do strony **just-in-Time** , przejdź do menu **Narzędzia** , a następnie kliknij przycisk **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **debugowanie** i wybierz opcję **just in Time**. Na tej stronie można włączyć debugowanie just in Time dla kodu zarządzanego, kodu natywnego i skryptu. Aby uzyskać więcej informacji, zobacz [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Debugowanie just in Time dla tych typów programów można włączyć:  
  
- Zarządzany  
  
- Natywna  
  
- Skrypt  
  
  Debugowanie just in Time to technika debugowania programu, który jest uruchamiany poza programem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Można uruchomić program utworzony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowiskiem. Jeśli włączono debugowanie just-in-Time, w przypadku awarii zostanie wyświetlone okno dialogowe z pytaniem, czy chcesz debugować.  
  
## <a name="associated-warnings"></a>Skojarzone ostrzeżenia  
 Po odwiedzeniu tej strony okna dialogowego **Opcje** może zostać wyświetlony komunikat ostrzegawczy podobny do tego:  
  
 **Inny debuger zarejestrował się jako debuger just in Time. Aby naprawić, Włącz debugowanie just in Time lub Uruchom naprawę programu Visual Studio.**  
  
 Ten komunikat występuje, jeśli masz inny debuger, prawdopodobnie starszą wersję [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugera, ustawioną jako debuger just in Time.  
  
 Może się pojawić kolejny komunikat:  
  
 **Wykryto błędy rejestracji debugowania just in Time. Aby naprawić, Włącz debugowanie just in Time lub Uruchom naprawę programu Visual Studio.**  
  
 Jeśli zobaczysz jedno z tych ostrzeżeń, debugowanie just in Time w programie [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] wymaga uprawnień administratora, dopóki problem nie zostanie rozwiązany. Jeśli spróbujesz włączyć opcję "tylko jako administrator" w tych warunkach, zobaczysz następujący komunikat o błędzie:  
  
 **Odmowa dostępu. Mieć uprawnienia administratora Włącz debugowanie just in Time lub Napraw instalację programu Visual Studio.**  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, Opcje — okno dialogowe](../debugger/debugging-options-dialog-box.md)   
 [Instrukcje: określanie ustawień debugera](../debugger/how-to-specify-debugger-settings.md)

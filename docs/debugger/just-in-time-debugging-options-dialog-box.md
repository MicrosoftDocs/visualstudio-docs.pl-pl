---
title: Debugowanie just in Time, okno dialogowe Opcje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c27ec66c8165995c6877b9a9e65802813140c7f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731609"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-in-time, debugowanie, opcje ― Okno dialogowe
Aby uzyskać dostęp do strony **just-in-Time** , przejdź do menu **Narzędzia** , a następnie kliknij przycisk **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **debugowanie** i wybierz opcję **just in Time**. Na tej stronie można włączyć debugowanie just in Time dla kodu zarządzanego, kodu natywnego i skryptu. Aby uzyskać więcej informacji, zobacz [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md).

 Debugowanie just in Time dla tych typów programów można włączyć:

- Zarządzany

- Natywna

- Skrypt

  Debugowanie just in Time to technika debugowania programu, który jest uruchamiany poza programem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Można uruchomić program utworzony [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiskiem. Jeśli włączono debugowanie just-in-Time, w przypadku awarii zostanie wyświetlone okno dialogowe z pytaniem, czy chcesz debugować.

## <a name="associated-warnings"></a>Skojarzone ostrzeżenia
 Po odwiedzeniu tej strony okna dialogowego **Opcje** może zostać wyświetlony komunikat ostrzegawczy podobny do tego:

 **Inny debuger zarejestrował się jako debuger just in Time. Aby naprawić, Włącz debugowanie just in Time lub Uruchom naprawę programu Visual Studio.**

 Ten komunikat występuje, jeśli masz inny debuger, prawdopodobnie starszą wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugera, ustawioną jako debuger just in Time.

 Może się pojawić kolejny komunikat:

 **Wykryto błędy rejestracji debugowania just in Time. Aby naprawić, Włącz debugowanie just in Time lub Uruchom naprawę programu Visual Studio.**

 Jeśli zobaczysz jedno z tych ostrzeżeń, debugowanie just in Time w programie [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] wymaga uprawnień administratora, dopóki problem nie zostanie rozwiązany. Jeśli spróbujesz włączyć opcję "tylko jako administrator" w tych warunkach, zobaczysz następujący komunikat o błędzie:

 **Odmowa dostępu. Mieć uprawnienia administratora Włącz debugowanie just in Time lub Napraw instalację programu Visual Studio.**

## <a name="see-also"></a>Zobacz też
- [Debugowanie, opcje ― Okno dialogowe](../debugger/debugging-options-dialog-box.md)
- [Instrukcje: określanie ustawień debugera](../debugger/how-to-specify-debugger-settings.md)
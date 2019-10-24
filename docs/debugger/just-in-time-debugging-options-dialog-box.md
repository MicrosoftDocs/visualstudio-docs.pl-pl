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
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731609"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-in-time, debugowanie, opcje ― Okno dialogowe
Aby uzyskać dostęp do strony **just-in-Time** , przejdź do menu **Narzędzia** , a następnie kliknij przycisk **Opcje**. W oknie dialogowym **Opcje** rozwiń węzeł **debugowanie** i wybierz opcję **just in Time**. Na tej stronie można włączyć debugowanie just in Time dla kodu zarządzanego, kodu natywnego i skryptu. Aby uzyskać więcej informacji, zobacz [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md).

 Debugowanie just in Time dla tych typów programów można włączyć:

- zarządzanych

- Natywne

- napisy

  Debugowanie just in Time to technika debugowania programu, który jest uruchamiany poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można uruchomić program utworzony w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poza środowiskiem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jeśli włączono debugowanie just-in-Time, w przypadku awarii zostanie wyświetlone okno dialogowe z pytaniem, czy chcesz debugować.

## <a name="associated-warnings"></a>Skojarzone ostrzeżenia
 Po odwiedzeniu tej strony okna dialogowego **Opcje** może zostać wyświetlony komunikat ostrzegawczy podobny do tego:

 **Inny debuger zarejestrował się jako debuger just in Time. Aby naprawić, Włącz debugowanie just in Time lub Uruchom naprawę programu Visual Studio.**

 Ten komunikat występuje, jeśli masz inny debuger, prawdopodobnie starszą wersję debugera [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ustawioną jako debuger just in Time.

 Może się pojawić kolejny komunikat:

 **Wykryto błędy rejestracji debugowania just in Time. Aby naprawić, Włącz debugowanie just in Time lub Uruchom naprawę programu Visual Studio.**

 Jeśli zobaczysz jedno z tych ostrzeżeń, debugowanie just in Time z [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] wymaga uprawnień administratora, dopóki problem nie zostanie rozwiązany. Jeśli spróbujesz włączyć opcję "tylko jako administrator" w tych warunkach, zobaczysz następujący komunikat o błędzie:

 **Odmowa dostępu. Mieć uprawnienia administratora Włącz debugowanie just in Time lub Napraw instalację programu Visual Studio.**

## <a name="see-also"></a>Zobacz także
- [Debugowanie, Opcje, okno dialogowe](../debugger/debugging-options-dialog-box.md)
- [Instrukcje: określanie ustawień debugera](../debugger/how-to-specify-debugger-settings.md)
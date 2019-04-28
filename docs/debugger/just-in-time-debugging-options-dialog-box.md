---
title: Just-In-Time, debugowanie, okno dialogowe Opcje | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 23a285cf0ce017130a5fe76171c50082362e4856
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905938"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Just-in-time, debugowanie, opcje ― Okno dialogowe
Aby uzyskać dostęp do **Just-In-Time** strony, przejdź do **narzędzia** menu i kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **debugowanie** a następnie wybierz węzeł **Just-In-Time**. Ta strona umożliwia włączenie debugowania dla kodu zarządzanego, natywnego kodu i skryptów Just-In-Time. Aby uzyskać więcej informacji, zobacz [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md).

 Aby umożliwić debugowanie dla tych typów programów Just-In-Time:

- Zarządzane

- Natywne

- Skrypt

  Debugowanie Just In Time jest techniką debugowanie programu, który jest uruchamiany poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można uruchomić programu, który został utworzony w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska. Włączenie debugowania Just-in-time awarii wyświetli okno dialogowe z pytaniem, jeśli chcesz debugować.

## <a name="associated-warnings"></a>Skojarzone ostrzeżenia
 Podczas odwiedzania ta strona **opcje** okno dialogowe może pojawić się komunikat ostrzegawczy, następująco:

 **Inny debuger zarejestrował się jako Just-In-Time debugera. Aby naprawić, należy włączyć Just-In-Time debugging lub uruchomić naprawę programu Visual Studio.**

 Ten komunikat występuje, gdy inny debuger, prawdopodobnie starszą wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugera, Ustaw jako Just-In-Time debugera.

 Inny komunikat, który może zostać wyświetlony jest następująca:

 **Just In Time wykryto debugowania błędy rejestracji. Aby naprawić, należy włączyć Just-In-Time debugging lub uruchomić naprawę programu Visual Studio.**

 Jeśli zostanie wyświetlony jeden z tych ostrzeżeń debugowanie Just In Time [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] wymaga uprawnień administratora, dopóki problem został rozwiązany. Jeśli zostanie podjęta próba włączenia po prostu — jako bez uprawnień administratora w tych warunkach, zobaczą następujący komunikat o błędzie:

 **Odmowa dostępu. Ma administrator włączyć Just-In-Time debugowanie lub napraw instalację programu Visual Studio.**

## <a name="see-also"></a>Zobacz też
- [Debugowanie, Opcje, okno dialogowe](../debugger/debugging-options-dialog-box.md)
- [Instrukcje: Określanie ustawień debugera](../debugger/how-to-specify-debugger-settings.md)
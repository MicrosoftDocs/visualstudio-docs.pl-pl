---
title: Ważne polecenia dla filtrów usługi językowej | Microsoft Docs
description: Dowiedz się więcej na temat ważnych poleceń, które powinny być obsługiwane podczas tworzenia w pełni funkcjonalnego filtru usługi językowej w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4eaa85eab9d9691125afce28d51c61d464e56cb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839836"
---
# <a name="important-commands-for-language-service-filters"></a>Ważne polecenia dotyczące filtrów usługi językowej
Jeśli chcesz utworzyć w pełni proponowany filtr usługi językowej, rozważ obsługę następujących poleceń. Pełna lista identyfikatorów poleceń jest definiowana w <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wyliczeniu dla kodu zarządzanego i pliku nagłówkowego Stdidcmd. h dla niezarządzanego [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] kodu. Plik Stdidcmd. h można znaleźć w *ścieżce instalacji zestawu SDK programu Visual Studio*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Polecenia do obsłużenia

> [!NOTE]
> Filtrowanie dla każdego polecenia w poniższej tabeli nie jest obowiązkowe.

|Polecenie|Opis|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik kliknie prawym przyciskiem myszy. To polecenie wskazuje, że jest czas na podanie menu skrótów. Jeśli to polecenie nie jest obsługiwane, Edytor tekstu udostępnia domyślne menu skrótów bez żadnych poleceń specyficznych dla języka. Aby dołączyć własne polecenia do tego menu, należy obsłużyć polecenie i samodzielnie wyświetlić menu skrótów.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zwykle wysyłany, gdy użytkownik wpisze kombinację klawiszy CTRL + J. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> celu wyświetlenia pola uzupełniania instrukcji.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze znak. Monitoruj to polecenie, aby określić, kiedy znak wyzwalacza jest wpisany i aby zapewnić uzupełnianie instrukcji, podpowiedzi metod i znaczników tekstu, takich jak kolorowanie składni, dopasowanie nawiasów klamrowych i znaczniki błędów. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> potrzeby uzupełniania instrukcji i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodę na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> etykietach metod for. Aby można było obsługiwać znaczniki tekstu, Monitoruj to polecenie, aby określić, czy znakowanie jest wymagane, aby zaktualizować znaczniki.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze klawisz ENTER. Monitoruj to polecenie, aby określić, kiedy odrzucić okno etykietki metody przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Domyślnie widok tekstu obsługuje to polecenie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze klawisz Backspace. Monitoruj, aby określić, kiedy odrzucić okno wskazówki metody przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Domyślnie widok tekstu obsługuje to polecenie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany z menu lub klawisza skrótu. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodę w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> celu zaktualizowania okna TIP informacjami o parametrach.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik umieści wskaźnik myszy nad zmienną lub umieszcza kursor na zmiennej i wybiera **szybkie informacje** z **IntelliSense** w menu **Edycja** . Zwróć typ zmiennej w Porada przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Jeśli debugowanie jest aktywne, Wskazówka powinna również zawierać wartość zmiennej.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zwykle wysyłany, gdy użytkownik wpisze kombinację klawiszy CTRL + SPACJa. To polecenie informuje usługę języka o wywołaniu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany z menu, zazwyczaj **komentarz** zaznaczenia lub usuwania **komentarzy** z opcji **Zaawansowane** w menu **Edycja** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> oznacza, że użytkownik chce dodać komentarz do zaznaczonego tekstu; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> oznacza, że użytkownik chce usunąć komentarz do zaznaczonego tekstu. Te polecenia można zaimplementować tylko za pomocą usługi językowej.|

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)

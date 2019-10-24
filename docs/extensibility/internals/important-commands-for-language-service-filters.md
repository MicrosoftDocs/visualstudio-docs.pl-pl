---
title: Ważne polecenia dla filtrów usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0e2e605a0725c2f88922d3e3ce899263171bc4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726928"
---
# <a name="important-commands-for-language-service-filters"></a>Ważne polecenia dotyczące filtrów usługi językowej
Jeśli chcesz utworzyć w pełni proponowany filtr usługi językowej, rozważ obsługę następujących poleceń. Pełna lista identyfikatorów poleceń jest definiowana w <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wyliczenia dla kodu zarządzanego i pliku nagłówkowego Stdidcmd. h dla niezarządzanego kodu [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]. Plik Stdidcmd. h można znaleźć w *ścieżce instalacji zestawu SDK programu Visual Studio*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Polecenia do obsłużenia

> [!NOTE]
> Filtrowanie dla każdego polecenia w poniższej tabeli nie jest obowiązkowe.

|Polecenie|Opis|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik kliknie prawym przyciskiem myszy. To polecenie wskazuje, że jest czas na podanie menu skrótów. Jeśli to polecenie nie jest obsługiwane, Edytor tekstu udostępnia domyślne menu skrótów bez żadnych poleceń specyficznych dla języka. Aby dołączyć własne polecenia do tego menu, należy obsłużyć polecenie i samodzielnie wyświetlić menu skrótów.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zwykle wysyłany, gdy użytkownik wpisze kombinację klawiszy CTRL + J. Wywołaj metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, aby wyświetlić pole uzupełniania instrukcji.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze znak. Monitoruj to polecenie, aby określić, kiedy znak wyzwalacza jest wpisany i aby zapewnić uzupełnianie instrukcji, podpowiedzi metod i znaczników tekstu, takich jak kolorowanie składni, dopasowanie nawiasów klamrowych i znaczniki błędów. Wywołaj metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> uzupełniania instrukcji i metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> podpowiedzi metody. Aby można było obsługiwać znaczniki tekstu, Monitoruj to polecenie, aby określić, czy znakowanie jest wymagane, aby zaktualizować znaczniki.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze klawisz ENTER. Monitoruj to polecenie, aby określić, kiedy odrzucić okno wskazówki metody, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Domyślnie widok tekstu obsługuje to polecenie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze klawisz Backspace. Monitoruj, aby określić, kiedy odrzucić okno wskazówki metody, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Domyślnie widok tekstu obsługuje to polecenie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany z menu lub klawisza skrótu. Wywołaj metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, aby zaktualizować okno TIP informacjami o parametrach.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik umieści wskaźnik myszy nad zmienną lub umieszcza kursor na zmiennej i wybiera **szybkie informacje** z **IntelliSense** w menu **Edycja** . Zwróć typ zmiennej w Porada, wywołując metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> w <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Jeśli debugowanie jest aktywne, Wskazówka powinna również zawierać wartość zmiennej.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zwykle wysyłany, gdy użytkownik wpisze kombinację klawiszy CTRL + SPACJa. To polecenie instruuje usługę języka, aby wywoływać metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany z menu, zazwyczaj **komentarz** zaznaczenia lub usuwania **komentarzy** z opcji **Zaawansowane** w menu **Edycja** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wskazuje, że użytkownik chce dodać komentarz do zaznaczonego tekstu;  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wskazuje, że użytkownik chce usunąć komentarz do zaznaczonego tekstu. Te polecenia można zaimplementować tylko za pomocą usługi językowej.|

## <a name="see-also"></a>Zobacz także
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)
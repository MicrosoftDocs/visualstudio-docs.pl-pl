---
title: Ważne polecenia dotyczące filtrów usługi językowej | Microsoft Docs
description: Dowiedz się więcej o ważnych poleceniach, które należy obsługiwać podczas tworzenia w pełni funkcjonalnego filtru usługi językowej w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dd5f65248411a7ea6b892d5b4c800718456339f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899059"
---
# <a name="important-commands-for-language-service-filters"></a>Ważne polecenia dotyczące filtrów usługi językowej
Jeśli chcesz utworzyć w pełni funkcjonalny filtr usługi językowej, rozważ obsługę następujących poleceń. Pełna lista identyfikatorów poleceń jest zdefiniowana w wyliczeniu dla kodu zarządzanego i w pliku <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> nagłówka Stdidcmd.h dla kodu nieza [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] zarządzania. Plik Stdidcmd.h można znaleźć w *ścieżce* Visual Studio SDK \VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Polecenia do obsługi

> [!NOTE]
> Filtrowanie każdego polecenia w poniższej tabeli nie jest obowiązkowe.

|Polecenie|Opis|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik kliknie prawym przyciskiem myszy. To polecenie wskazuje, że na czas podać menu skrótów. Jeśli to polecenie nie jest obsługiwane, edytor tekstu udostępnia domyślne menu skrótów bez żadnych poleceń specyficznych dla języka. Aby dołączyć własne polecenia do tego menu, należy samodzielnie obsłużyć polecenie i wyświetlić menu skrótów.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zazwyczaj wysyłane, gdy użytkownik naciśnięty klawisz CTRL + J. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę w pliku , aby wyświetlić pole <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> uzupełniania instrukcji.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik w typie znaku. Monitoruj to polecenie, aby określić, kiedy jest wpisany znak wyzwalacza, oraz podać uzupełnianie instrukcji, porady dotyczące metod i znaczniki tekstu, takie jak kolorowanie składni, dopasowywanie nawiasów klamrowych i znaczniki błędów. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę na zakończenie instrukcji for i metodę w metodzie dla porad dotyczących <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> metody. Aby obsługiwać znaczniki tekstu, monitoruj to polecenie, aby określić, czy wpisywany znak wymaga zaktualizowania znaczników.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik wpisze klawisz Enter. Monitoruj to polecenie, aby określić, kiedy odrzucić okno porady metody, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> wywołując metodę w metodzie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Domyślnie widok tekstowy obsługuje to polecenie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik typi klawisz Backspace. Monitoruj, aby określić, kiedy odrzucić okno porady metody, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> wywołując metodę w metodzie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . Domyślnie widok tekstowy obsługuje to polecenie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane z menu lub klawisza skrótu. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodę w metodzie , aby <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> zaktualizować okno porad przy użyciu informacji o parametrach.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik najedzie kursorem na zmienną  lub ustawi kursor na zmiennej i wybierze pozycję Szybkie informacje z **funkcji IntelliSense** w menu **Edycja.** Zwróć typ zmiennej w wierzchołku, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodę dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Jeśli debugowanie jest aktywne, porada powinna również pokazywać wartość zmiennej.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zwykle wysyłane, gdy użytkownik naciśnięty klawisz CTRL + SPACJA. To polecenie nakazuje usłudze językowej wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody w metodzie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane z menu, zazwyczaj **zaznaczanie** komentarzy lub **zaznaczanie komentarza** **z** pozycji Zaawansowane w menu **Edycja.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wskazuje, że użytkownik chce oznaczać zaznaczony tekst jako komentarz; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wskazuje, że użytkownik chce odkomentować zaznaczony tekst. Te polecenia mogą być implementowane tylko przez usługę językową.|

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)

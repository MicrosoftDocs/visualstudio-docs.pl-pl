---
title: Ważne polecenia dla filtrów usług językowych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707614"
---
# <a name="important-commands-for-language-service-filters"></a>Ważne polecenia dotyczące filtrów usługi językowej
Jeśli chcesz utworzyć w pełni funkcjonalny filtr usługi języka, należy rozważyć obsługę następujących poleceń. Pełna lista identyfikatorów poleceń jest <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> zdefiniowana w wyliczeniu dla kodu zarządzanego i pliku [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] nagłówka Stdidcmd.h dla niezarządzanego kodu. Plik Stdidcmd.h można znaleźć w *ścieżce instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Polecenia do obsługi

> [!NOTE]
> Filtrowanie każdego polecenia w poniższej tabeli nie jest obowiązkowe.

|Polecenie|Opis|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane po kliknięciu prawym przyciskiem myszy użytkownika. To polecenie wskazuje, że nadszedł czas, aby udostępnić menu skrótów. Jeśli to polecenie nie jest obsługiwane, edytor tekstu udostępnia domyślne menu skrótów bez żadnych poleceń specyficznych dla języka. Aby dołączyć do tego menu własne polecenia, należy obsługiwać polecenie i samodzielnie wyświetlić menu skrótów.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zazwyczaj wysyłane, gdy użytkownik wpisuje CTRL + J. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> w polu, aby wyświetlić wypełnienie instrukcji.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik wpisuje znak. Monitoruj to polecenie, aby określić, kiedy znak wyzwalacza jest wpisywany i podać uzupełnianie instrukcji, porady dotyczące metod i znaczniki tekstu, takie jak kolorowanie składni, dopasowywanie nawiasów klamrowych i znaczniki błędów. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> na do uzupełnienia instrukcji i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metody na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> porady dotyczące metody. Aby obsługiwać znaczniki tekstu, należy monitorować to polecenie, aby ustalić, czy wpisany znak wymaga aktualizacji znaczników.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik wpisze klawisz Enter. Monitoruj to polecenie, aby określić, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> kiedy odrzucić okno końcówki metody, wywołując metodę w pliku <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Domyślnie widok tekstu obsługuje to polecenie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik wpisuje klawisz Backspace. Monitoruj, aby określić, kiedy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> odrzucić <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>okno końcówki metody, wywołując metodę w pliku . Domyślnie widok tekstu obsługuje to polecenie.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane z menu lub klawisza skrótu. Wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodę, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aby zaktualizować okno końcówki z informacjami o parametrach.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane, gdy użytkownik najedzie kursorem lub umieszcz kursor zmiennej i wybierze **polecenie Szybkie informacje** z polecenia **IntelliSense** w menu **Edycja.** Zwraca typ zmiennej w końcówce, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>metodę w pliku . Jeśli debugowanie jest aktywne, wskazówka powinna również pokazać wartość zmiennej.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Zazwyczaj wysyłane, gdy użytkownik wpisuje CTRL + spacja. To polecenie informuje usługę języka, aby wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodę na . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane z menu, zazwyczaj **wybór komentarza** lub **Odkomentowanie zaznaczenia** z **menu Edycja.** **Edit** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>wskazuje, że użytkownik chce skomentować zaznaczony tekst; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> oznacza, że użytkownik chce odkomentować zaznaczony tekst. Te polecenia mogą być implementowane tylko przez usługę języka.|

## <a name="see-also"></a>Zobacz też
- [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)

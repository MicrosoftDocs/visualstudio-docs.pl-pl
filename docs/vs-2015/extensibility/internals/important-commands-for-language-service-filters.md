---
title: Ważne polecenia dotyczące języka usługi filtry | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03bb20abf32f7c320ed56f4a649a9f43453e7694
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447258"
---
# <a name="important-commands-for-language-service-filters"></a>Ważne polecenia dotyczące filtrów usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jeśli chcesz utworzyć filtr usługi języka w pełni wyposażone, należy rozważyć obsługę następujących poleceń. Pełną listę identyfikatorów poleceń jest zdefiniowany w <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wyliczenie dla kodu zarządzanego i nagłówek Stdidcmd.h pliku niezarządzanych [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] kodu. Można znaleźć w pliku Stdidcmd.h *ścieżka instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Polecenia do uchwytu  
  
> [!NOTE]
> Nie jest wymagane, aby filtrować dla każdego polecenia w poniższej tabeli.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik kliknie prawym przyciskiem myszy. To polecenie wskazuje, że nadszedł czas na Zapewnij menu skrótów. Jeśli nie obsługuje tego polecenia, Edytor tekstu zawiera domyślne menu skrótów, bez żadnych poleceń specyficznych dla języka. Aby dołączyć poleceń w tym menu, obsługi polecenia i wyświetli menu skrótów, samodzielnie.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Typowo wysyłana, gdy użytkownik wpisuje CTRL + J. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aby pokazać pole uzupełniania instrukcji.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze jakiś znak. Monitorowanie to polecenie, aby określić po wpisaniu znaku wyzwalacza i zapewnienie instrukcji zakończenia, metoda porady i znaczników tekstu, takie jak kolorowanie składni, dopasowywanie nawiasów i znaczniki błędów. Wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> uzupełniania instrukcji i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> porady metody. Aby zapewnić obsługę znaczników tekstu, monitorowanie to polecenie, aby określić, czy jest wpisany znak wymaga aktualizacji usługi znaczników.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze klawisz Enter. Monitorowanie tego polecenia, aby określić, kiedy zamknąć okno porad metoda przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Domyślnie widok tekstu obsługuje tego polecenia.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik wpisze klawisz Backspace. Monitor do określenia, kiedy zamknąć okno porad metoda przez wywołanie metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Domyślnie widok tekstu obsługuje tego polecenia.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane z menu lub klawisza skrótu. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> można zaktualizować okno porad o informacje o parametrach.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłany, gdy użytkownik znajduje się nad zmienną lub z kursorem na zmienną i wybiera **Quick Info** z **IntelliSense** w **Edytuj** menu. Zwracany typ zmiennej w oknie z poradami, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Jeśli debugowanie jest aktywna, porady również powinny pokazywać wartość zmiennej.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Typowo wysyłana, gdy użytkownik wpisuje klawisze CTRL + SPACJA. To polecenie informuje usługa językowa do wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wysyłane z menu, zwykle **Dodaj komentarz do zaznaczenia** lub **Usuń komentarz zaznaczenia** z **zaawansowane** w **Edytuj** menu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Wskazuje, że użytkownik chce, aby przekształcić w komentarz zaznaczonego tekstu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> wskazuje, że użytkownik chce usuń znaczniki komentarza w zaznaczonym tekście. Te polecenia można zaimplementować tylko przez usługę języka.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)

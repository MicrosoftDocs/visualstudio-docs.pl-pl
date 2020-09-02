---
title: Dostosowywanie systemu Windows przy użyciu starszej wersji interfejsu API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556144"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Dostosowywanie okien kodu za pomocą starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno kodu jest obiektem okna dokumentu, który obsługuje co najmniej jeden widok tekstu. Dokładne funkcje okna kod zależą od powiązanej usługi językowej. W trybie interfejsu wielu dokumentów (MDI) okno kod jest ramką podrzędną MDI.  
  
 Okna kodu są kontrolowane przez usługi językowe, a każda usługa języka może zapewnić własny Menedżer okien kodu. Dzięki temu usługa języka może dodawać własne potrzeby definiowania układu do okna kodu, takie jak zygzaki, kolorowanie i inne. Aby uzyskać więcej informacji na temat tworzenia okna podstawowego, zobacz [Tworzenie wystąpienia podstawowego edytora przy użyciu starszego interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Okno kodu jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiektem, który ma widok tekstu i wszystkie zakończenia w obiekcie. Po utworzeniu okna kodu podczas tworzenia wystąpienia podstawowego edytora, usługa języka może dołączyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> do okna kodu, jak pokazano na poniższej ilustracji.  
  
 ![Grafika CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Okno kodu  
  
 Usługa językowa implementuje Menedżera okien kodu i odpowiada za zarządzanie zakończeniami, takimi jak pasek listy rozwijanej. Okno kodu wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metodę podczas inicjowania okna kodu. Po wykonaniu tego wywołania usługa języka może dodać do okna kod pasek listy rozwijanej lub pasek przycisku ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> ).  
  
## <a name="in-this-section"></a>W tej sekcji  
 `Customizing Code Windows by Using the Legacy API`  
 Wyjaśnia, jak dostosować okna kodu przy użyciu starszego interfejsu API.  
  
 [Instrukcje: hostowanie edytora w innym edytorze](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Wyjaśnia, jak hostować drugi Edytor wewnątrz okna edytora.  
  
 [Instrukcje: wyzwalanie zdarzeń po utracie fokusu przez edytor](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Wyjaśnia, jak dołączyć widok dokumentu do obiektu danych dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Tworzenie wystąpienia podstawowego edytora przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Uzyskiwanie dostępu do widoku tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)

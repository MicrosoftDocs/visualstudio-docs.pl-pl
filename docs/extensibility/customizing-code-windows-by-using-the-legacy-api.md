---
title: Dostosowywanie kodu Windows za pomocą starszej wersji interfejsu API | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0ea617a252d60d8e8d5810c42f7331508c28165
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62890997"
---
# <a name="customize-code-windows-by-using-the-legacy-api"></a>Dostosowywanie kodu systemu windows przy użyciu starszej wersji interfejsu API
Okno kodu jest obiekt okna dokumentu, który obsługuje jeden lub więcej widoków tekstu. Dokładne funkcje okna kodu, zależą od usługi skojarzone języka. W trybie interfejsu wielu dokumentów (MDI) w oknie Kod jest podrzędna ramka MDI.

 Kod systemu windows są kontrolowane przez usługi języka oraz każdej usługi w języka wprowadzić swój własny Menedżer okna kodu. Dzięki temu usługa językowa dodać własną zakończeń do okna kodu, takich jak faliste linie, kolorowanie i nie tylko. Aby uzyskać więcej informacji o tym, jak można utworzyć okna core, zobacz [wystąpienia podstawowy edytor przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).

 Okno kodu jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> obiekt widoku tekstu i wszelkie zakończeń ulokowany w obiekcie. Podczas tworzenia okna kodu podczas konkretyzacji, rdzenia edytora, można dołączyć usługi języka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> do okna kodu, tak jak przedstawiono na poniższej ilustracji.

 ![Grafika CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow") okno kodu

 Usługa językowa implementuje Menedżera okien kodu i jest odpowiedzialny za zarządzanie zakończeń, takie jak pasek listy rozwijanej. Kod wywołuje okno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metody podczas inicjowania okna kodu. Po wykonaniu tego wywołania usługi językowej można dodać pasek listy rozwijanej lub przycisku (<xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient>) do okna kodu.

## <a name="in-this-section"></a>W tej sekcji
 `Customizing Code Windows by Using the Legacy API` Opis sposobu dostosowywania kodu systemu windows za pomocą starszej wersji interfejsu API.

- [Instrukcje: Hostowanie redaktorem w innym edytorze](../extensibility/how-to-host-an-editor-in-another-editor.md) wyjaśnia, jak hostować drugi edytora w oknie edytora.

- [Instrukcje: Wyzwolenie zdarzenia po utracie fokusu przez edytor](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md) wyjaśnia, jak dołączyć widok dokumentu do obiektu danych dokumentu.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [Utwórz wystąpienie podstawowy edytor przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
- [Wyświetl theText dostępu przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
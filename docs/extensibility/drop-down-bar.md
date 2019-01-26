---
title: Listę rozwijaną paska | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3506ff05bf7551a66ea616ca4c49dbf6ea80f4a7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949288"
---
# <a name="drop-down-bar"></a>Listę rozwijaną paska
Pasek listy rozwijanej znajduje się w górnej części okna kodu i zawiera dwie listy rozwijanej.  
  
## <a name="drop-down-bar-interfaces"></a>Interfejsy listę rozwijaną paska  
 W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], na przykład pasek lista rozwijana zawiera listy dla [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] elementów i [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] elementy członkowskie funkcji, jak pokazano na poniższej ilustracji.  
  
 ![Drop&#45;down Bars](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Listę rozwijaną paska  
  
 Podczas implementowania pasek listy rozwijanej, dostępne są cztery interfejsy podstawowe znaczenie:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implementuje ten interfejs do wstawiania zawartości paska listy rozwijanej. Każda kombinacja listy rozwijanej może zawierać zwykły tekst lub ozdobnych tekst (pogrubienie, podkreślenie lub kursywa), może zawierać kolorowanie czcionki tekstu okna lub wygaszone się czcionki, kolorowanie, a opcjonalnie możesz podać małe mapy bitowe obok elementu listy rozwijanej. Podobnie jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejsu, obrazy bitmapowe znajdują się na listach obrazów. Każda kombinacja listy rozwijanej może się znajdować lista innego obrazu; Jednak każda lista obrazu musi zawierać obrazów sama wysokość. Ponadto za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> metoda, może dostarczyć etykietkę narzędzia dla każdej kombinacji.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Wywołanie tego interfejsu, aby utworzyć lub zniszczyć pasek listy rozwijanej w oknie kodu. Ten interfejs może również określić, czy pasek listy rozwijanej jest już dołączony do okna kodu, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metody. Wywołaj <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Wywołanie tego interfejsu, aby komunikować się bezpośrednio z paska listy rozwijanej. Można użyć tego interfejsu, aby wymusić odświeżenie listy rozwijanej paska zawartość lub aby zmienić wybór w jednym z pól listy.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Jeśli zarejestrowano `ShowDropdownBarOption` w ten sposób klucza rejestru usługi języka następnie Menedżera okna kodu należy monitorować to zdarzenie, aby zapewnić synchronizację z preferencje użytkownika dotyczące tego, czy powinien być wyświetlany pasek listy rozwijanej. Jeśli ta opcja nie zostanie zarejestrowany w ten sposób klucza usługi w języka, a następnie opcję, aby pokazać lub ukryć pasek listy rozwijanej jest wyłączona na **opcje** menu.  
  
## <a name="attach-a-drop-down-bar-to-a-code-window"></a>Dołącz pasek listy rozwijanej do okna kodu  
 Aby dołączyć listę rozwijaną paska do okna kodu podczas jego tworzenia, usługa języka należy dołączać do listy rozwijanej paska, kiedy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metoda jest wywoływana. Jeśli wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metoda wskazuje, że pasek listy rozwijanej jeszcze nie istnieje, a następnie wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Aby uzyskać dostęp do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interfejsu, zadzwoń <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> wskaźnik zwrócona do Ciebie, gdy usługi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementacja została dołączona.  
  
## <a name="see-also"></a>Zobacz także  
 [Dostosowywanie kodu systemu windows przy użyciu starszej wersji interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
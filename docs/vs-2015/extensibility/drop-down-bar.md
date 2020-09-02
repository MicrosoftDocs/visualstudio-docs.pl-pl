---
title: Pasek listy rozwijanej | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204650"
---
# <a name="drop-down-bar"></a>Pasek list rozwijanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pasek listy rozwijanej znajduje się u góry okna kod i zawiera dwie listy rozwijane.  
  
## <a name="drop-down-bar-interfaces"></a>Interfejsy słupków rozwijanych  
 Na [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] przykład na pasku listy rozwijanej znajdują się listy [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] elementów członkowskich elementy i [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] elementy, jak pokazano na poniższej ilustracji.  
  
 ![Upuść&#45;słupki w dół](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Pasek listy rozwijanej  
  
 Podczas implementowania paska rozwijanego istnieją cztery interfejsy podstawowej ważności:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Zaimplementuj ten interfejs, aby wstawić zawartość paska listy rozwijanej. Każda kombinacja rozwijana może zawierać zwykły tekst lub ozdobny tekst (pogrubiony, podkreślenie lub kursywa), może mieć kolorowanie czcionki okna lub wyszarzone, a opcjonalnie zapewnić małą mapę bitową obok elementu listy rozwijanej. Podobnie jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfejs, obrazy map bitowych są udostępniane na listach obrazów. Każda kombinacja rozwijana może mieć inną listę obrazów; jednak każda lista obrazów musi zawierać obrazy o tej samej wysokości. Ponadto za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> metody można podać etykietkę narzędzia dla każdej kombinacji.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Wywołaj ten interfejs, aby utworzyć lub zniszczyć pasek listy rozwijanej dla okna kodu. Tego interfejsu można także użyć do określenia, czy pasek listy rozwijanej jest już dołączony do okna kodu przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metody. Wywołaj <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> od <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Wywołaj ten interfejs, aby komunikować się bezpośrednio z paskiem listy rozwijanej. Możesz użyć tego interfejsu, aby wymusić odświeżenie zawartości paska rozwijanego lub zmianę zaznaczenia w jednym z pól listy.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Jeśli zarejestrowano `ShowDropdownBarOption` w kluczu rejestru usługi językowej, Menedżer okien kodu musi monitorować to zdarzenie, aby synchronizować się z preferencjami użytkownika dotyczącymi tego, czy ma być wyświetlany pasek listy rozwijanej. Jeśli nie zarejestrujesz tej opcji w kluczu usługi językowej, opcja pokazywania lub ukrywania paska rozwijanego jest wyłączona w menu **Opcje** .  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Dołączanie paska listy rozwijanej do okna kodu  
 Aby dołączyć pasek listy rozwijanej do okna kodu podczas jego tworzenia, usługa języka powinna dołączyć do paska listy rozwijanej, gdy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> wywoływana jest metoda. Jeśli wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> metody wskazuje, że pasek listy rozwijanej jeszcze nie istnieje, a następnie Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . Aby uzyskać dostęp do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interfejsu, wywołaj <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> od <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> wskaźnika zwróconego do Ciebie, gdy Twoja <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementacja została dołączona.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie systemu Windows przy użyciu starszego interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

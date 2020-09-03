---
title: Zmiana ustawień widoku przy użyciu starszego interfejsu API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184466"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Zmienianie ustawień widoku za pomocą starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ustawienia funkcji podstawowego edytora, takie jak Zawijanie wierszy, margines wyboru i wirtualne miejsce, mogą zostać zmienione przez użytkownika za pomocą okna dialogowego **Opcje** . Można jednak również programowo zmienić te ustawienia.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Zmienianie ustawień przy użyciu starszego interfejsu API  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>Interfejs uwidacznia zestaw właściwości edytora tekstu. Widok tekstu zawiera kategorię właściwości (GUID_EditPropCategory_View_MasterSettings), która reprezentuje grupę programowo zmienionych ustawień widoku tekstu. Po zmianie ustawień widoku w ten sposób nie można ich zmienić w oknie dialogowym **Opcje** , dopóki nie zostaną zresetowane.  
  
 Poniżej przedstawiono typowy proces zmiany ustawień widoku dla wystąpienia podstawowego edytora.  
  
1. Wywołaj metodę `QueryInterface` ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> ) dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfejsu.  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> metodę, określając wartość GUID_EditPropCategory_View_MasterSettings dla `rguidCategory` parametru.  
  
     Wykonanie tej operacji zwraca wskaźnik do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfejsu, który zawiera zestaw wymuszonych właściwości widoku. Wszystkie ustawienia w tej grupie są trwale wymuszane. Jeśli ustawienie nie znajduje się w tej grupie, będzie ono zgodne z opcjami określonymi w oknie dialogowym **Opcje** lub poleceniami użytkownika.  
  
3. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> metodę, określając odpowiednie wartości ustawień w `idprop` parametrze.  
  
     Na przykład aby wymusić zawijanie wierszy, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> i określić wartość VSEDITPROPID_ViewLangOpt_WordWrap, `vt` dla `idprop` parametru. W tym wywołaniu `vt` jest wariant typu VT_BOOL i `vt.boolVal` jest VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Resetowanie zmienionych ustawień widoku  
 Aby zresetować wszystkie zmiany ustawienia widoku dla wystąpienia edytora podstawowego, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> metodę i określić odpowiednią wartość ustawienia w `idprop` parametrze.  
  
 Na przykład, aby zezwolić na swobodne zawijanie wyrazów, należy usunąć je z kategorii właściwości przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> i określenie wartości VSEDITPROPID_ViewLangOpt_WordWrap dla `idprop` parametru.  
  
 Aby usunąć wszystkie zmienione ustawienia dla podstawowego edytora, określ wartość VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT dla `idprop` parametru. W przypadku tego wywołania VT jest WARIANTem typu VT_BOOL, a VT. boolVal jest VARIANT_TRUE.  
  
## <a name="see-also"></a>Zobacz też  
 [Wewnątrz edytora podstawowego](../extensibility/inside-the-core-editor.md)   
 [Uzyskiwanie dostępu do widoku theText przy użyciu starszego interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Opcje — okno dialogowe](../ide/reference/options-dialog-box-visual-studio.md)

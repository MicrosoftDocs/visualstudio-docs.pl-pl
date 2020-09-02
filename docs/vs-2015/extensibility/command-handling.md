---
title: Obsługa poleceń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184374"
---
# <a name="command-handling"></a>Obsługa poleceń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor może definiować nowe polecenia. Polecenia są zwykle wyświetlane w menu na pasku narzędzi lub w menu kontekstowym.  
  
 Aby uzyskać więcej informacji na temat definiowania poleceń i menu, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Usługa języka może kontrolować, jakie menu kontekstowe są wyświetlane w edytorze, przechwytując <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Wyliczenie. Alternatywnie można kontrolować menu kontekstowe dla poszczególnych znaczników. Aby uzyskać więcej informacji, zobacz [Ważne polecenia dla filtrów usługi językowej](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Dodawanie poleceń do menu kontekstowego edytora  
 Aby dodać polecenie do menu kontekstowego, należy najpierw zdefiniować zestaw poleceń menu należących do określonej grupy. Poniższy przykład jest pobierany z pliku. vsct wygenerowanego jako część [przewodnika instruktażowego: Dodawanie funkcji do edytora niestandardowego](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>Menu kontekstowe CustomEditor\</ButtonText>  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 Powyższy tekst dodaje polecenie menu kontekstowego z **menu kontekstowym CustomEditor**tekstu. Menu GUID jest zestawem poleceń utworzonym za pomocą tego edytora, a typem jest "context".  
  
 Można również użyć wstępnie zdefiniowanych poleceń, które nie muszą być zdefiniowane w pliku. vsct. Na przykład, jeśli sprawdzisz plik EditorPane.cs wygenerowany przez szablon pakietu programu Visual Studio, zobaczysz, że zestaw wstępnie zdefiniowanych poleceń, takich jak <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> zdefiniowane przez <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> , są obsługiwane w obsłudze poleceń, takich jak metoda onSelectAll.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)

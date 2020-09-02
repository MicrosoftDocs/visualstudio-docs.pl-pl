---
title: Obiekt VSCodeWindow | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690772"
---
# <a name="vscodewindow-object"></a>VSCodeWindow, obiekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno kodu to wyspecjalizowane okno dokumentu, które może zawierać co najmniej jeden widok tekstowy, zazwyczaj ten <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiekt.  
  
 W sposób architektoniczny okno kod jest oknem dokumentu, które znajduje się w obrębie ramki okna. Funkcjonalnie okno kod jest po prostu oknem dokumentu z dodatkowymi funkcjami. W trybie interfejsu wielu dokumentów (MDI) okno kod jest ramką podrzędną MDI. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodu w systemie Windows przy użyciu starszego interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Poniższa tabela zawiera interfejsy w <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> obiekcie.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Zapewnia ogólny mechanizm dostępu do lokalizowania usługi, która identyfikuje globalnie unikatowy identyfikator (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Reprezentuje element podrzędny interfejsu wielu dokumentów (MDI) zawierający co najmniej jeden widok kodu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Wypełnia ramkę okna.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Edycja ilustracji](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)

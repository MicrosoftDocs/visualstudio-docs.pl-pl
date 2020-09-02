---
title: 'Instrukcje: hostowanie edytora w innym edytorze | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204170"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Instrukcje: hostowanie edytora w innym edytorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można hostować jeden Edytor wewnątrz innego, określając okno hostingowe jako okno nadrzędne. Aby to zrobić, należy ustawić parametry <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> w ramce okna podrzędnego.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Aby skonfigurować ramkę okna do hostowania edytora  
  
1. Wyznaczanie edytora jako edytora hostowanego przez utworzenie okienka podrzędnego okna.  
  
     W tym okienku znajduje się tekst edytora.  
  
2. Utwórz Edytor hostingu przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
3. Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> właściwości i <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> w implementacji ramki okna dla edytora hostowanego, przekazując te właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> odpowiednio do metody.  
  
     Jeśli musisz pobrać te parametry, Przekaż te właściwości do <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody.  
  
4. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodę dla zawartego edytora.  
  
     Edytor pojawia się w hostowanym okienku zawierającego Edytor.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 **Projektant aplikacji** w Visual Studio Team Edition for Architects to przykład ramki okna edytora, która obsługuje inny edytor. **Projektant aplikacji** hostuje innych projektantów w okienku po prawej stronie. Panel projektanta (lub strona **Właściwości** ) dla każdego z zawartych projektantów jest dodawany do ramki okna zawierającego.

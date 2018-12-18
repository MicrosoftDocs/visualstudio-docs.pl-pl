---
title: Algorytm routingu poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44fc431f008c59a7d4ceff2d9b9ec14d85091daf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728003"
---
# <a name="command-routing-algorithm"></a>Algorytm routingu poleceń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W programie Visual Studio polecenia są obsługiwane przez szereg różnych składników. Polecenia są kierowane z najbardziej kontekst, który jest oparty na bieżącym zaznaczeniu, prowadzące kontekst (znany także jako globalna). Aby uzyskać więcej informacji, zobacz [dostępności](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Kolejność rozwiązywania polecenia  
 Polecenia są przekazywane za pośrednictwem następujących poziomów kontekst polecenia:  
  
1.  Dodatki: Środowiska oferuje najpierw polecenie, aby wszystkie dodatki, które są obecne.  
  
2.  Polecenia priorytet: te polecenia są zarejestrowane przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Są wywoływane dla każdego polecenia w programie Visual Studio i są wywoływane w kolejności, w którym zostały zarejestrowane.  
  
3.  Polecenia menu kontekstowego: polecenie znajdujące się w menu kontekstowym najpierw jest oferowana na elemencie docelowym polecenia, który został dostarczony do menu kontekstowe, a następnie do typowych routingu.  
  
4.  Pasek narzędzi ustawić obiekty docelowe poleceń: te obiekty docelowe poleceń są rejestrowane, gdy wywołujesz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. `pCmdTarget` Parametr może być `null`. Jeśli nie jest `null`, a następnie ten element docelowy polecenia służy do aktualizowania dowolne polecenia znajdujące się na pasku narzędzi, które konfigurujesz. Powłoka konfiguruje paska narzędzi, a następnie przekazuje ramki okna jako `pCmdTarget` tak, aby wszystkie aktualizacje poleceń na przepływu za pomocą ramki okna narzędzi, nawet gdy nie jest w trybie koncentracji uwagi.  
  
5.  Okno narzędzi: Narzędzi systemu windows, które zazwyczaj implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu, powinny również implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, tak aby program Visual Studio można uzyskać elemencie docelowym polecenia, gdy okno narzędzia jest aktywnym oknem. Jeśli jednak okno narzędzia ma fokus jest **projektu** okna, a następnie polecenie jest kierowany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu, który jest elementem nadrzędnym wspólnego z wybranych elementów. Jeśli to zaznaczenie obejmuje wiele projektów, polecenie jest kierowany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hierarchii. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Interfejs zawiera <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metody, które są analogiczne do odpowiednich poleceń w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu.  
  
6.  Okno dokumentu: Jeśli polecenie ma flagę RouteToDocs ustawiony w pliku vsct, Visual Studio szuka elementu docelowego polecenia dla obiektu widoku dokumentu, który może być wystąpieniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu lub wystąpienie obiektu dokumentu (zazwyczaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>interfejsu lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsu). Jeśli obiekt widoku dokumentu nie obsługuje polecenia, programu Visual Studio kieruje polecenia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, który jest zwracany. (Jest to opcjonalny interfejs dla obiektów danych dokumentu).  
  
7.  Bieżącą hierarchią: bieżącej hierarchii może być projektu, który jest właścicielem aktywnego okna dokumentu lub hierarchię, który wybrano w **Eksploratora rozwiązań**. Visual Studio szuka <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, który jest implementowany w bieżącej lub aktywnej hierarchii. Hierarchia powinien obsługiwać poleceń, które są prawidłowe, zawsze wtedy, gdy hierarchia jest aktywny, nawet wtedy, gdy okno dokumentu elementu projektu jest ustawiony fokus. Jednak polecenia, które są stosowane tylko wtedy, gdy **Eksploratora rozwiązań** ma fokus, muszą być obsługiwane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu i jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>metody.  
  
     **Wytnij**, **kopiowania**, **Wklej**, **Usuń**, **Zmień nazwę**, **wprowadź**i **DoubleClick** polecenia wymagają specjalnej obsługi. Aby uzyskać informacje dotyczące obsługi **Usuń** i **Usuń** poleceń w hierarchii, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfejsu.  
  
8.  Globalny: Jeśli polecenie nie został obsłużony przez kontekstów wspomniano wcześniej, Visual Studio podejmie próbę kierowania go do pakietu VSPackage, który jest właścicielem polecenia, który implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Jeśli nie został już załadowany pakietu VSPackage, nie jest ona załadowana gdy program Visual Studio wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Pakietu VSPackage są ładowane tylko wtedy, gdy <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metoda jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [Projektowanie poleceń](../../extensibility/internals/command-design.md)


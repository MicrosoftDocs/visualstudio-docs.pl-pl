---
title: Algorytm routingu poleceń | Microsoft Docs
description: Dowiedz się więcej o kolejności rozpoznawania poleceń w programie Visual Studio, ponieważ polecenia są obsługiwane przez różne składniki i przesyłane od najbardziej wewnętrznego do zewnętrznego kontekstu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0e02493cbb2f872806ade33d77609d45d1938ccd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057315"
---
# <a name="command-routing-algorithm"></a>Algorytm routingu poleceń
W poleceniach programu Visual Studio są obsługiwane przez wiele różnych składników. Polecenia są kierowane z wewnętrznego kontekstu, który jest oparty na bieżącym zaznaczeniu, do zewnętrznego (znanego również jako globalny) kontekstu. Aby uzyskać więcej informacji, zobacz [dostępność poleceń](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Kolejność rozpoznawania poleceń
 Polecenia są przesyłane przez następujące poziomy kontekstu poleceń:

1. Dodatki: środowisko najpierw oferuje polecenie do wszelkich dodatków, które są obecne.

2. Priorytet polecenia: te polecenia są rejestrowane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Są one wywoływane dla każdego polecenia w programie Visual Studio i są wywoływane w kolejności, w jakiej zostały zarejestrowane.

3. Polecenia menu kontekstowego: polecenie znajdujące się w menu kontekstowym jest najpierw oferowane dla elementu docelowego polecenia, który jest dostarczany do menu kontekstowego i po nim do typowego routingu.

4. Elementy docelowe poleceń Set Toolbar: te obiekty docelowe poleceń są rejestrowane podczas wywoływania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . `pCmdTarget`Parametr może być `null` . Jeśli tak nie jest `null` , to obiekt docelowy polecenia służy do aktualizowania wszelkich poleceń znajdujących się na pasku narzędzi, który jest konfigurowany. Jeśli powłoka konfiguruje pasek narzędzi, przenosi ramkę okna w taki sposób, aby `pCmdTarget` wszystkie aktualizacje poleceń na pasku narzędzi przepływają przez ramkę okna, nawet gdy nie jest ona skoncentrowana.

5. Okno narzędzi: okna narzędzi, które zazwyczaj implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejs, należy również zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, aby program Visual Studio mógł uzyskać obiekt docelowy polecenia, gdy okno narzędzia jest oknem aktywnym. Jeśli jednak okno narzędzia z fokusem jest oknem **projektu** , to polecenie jest kierowane do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu, który jest wspólnym elementem nadrzędnym wybranych elementów. Jeśli wybór obejmuje wiele projektów, polecenie jest kierowane do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hierarchii. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Interfejs zawiera <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metody i, które są analogiczne do odpowiednich poleceń w <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsie.

6. Okno dokumentu: Jeśli polecenie ma `RouteToDocs` ustawioną flagę w pliku *. vsct* , program Visual Studio szuka elementu docelowego polecenia w obiekcie widoku dokumentu, który jest wystąpieniem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu lub wystąpieniem obiektu dokumentu (zazwyczaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfejsem lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfejsem). Jeśli obiekt widoku dokumentu nie obsługuje polecenia, program Visual Studio kieruje polecenie do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zwracanego interfejsu. (Jest to opcjonalny interfejs dla obiektów danych dokumentów).

7. Bieżąca hierarchia: Bieżąca hierarchia może być projektem, który jest właścicielem okna aktywnego dokumentu lub hierarchią wybraną w **Eksplorator rozwiązań**. Program Visual Studio szuka <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu, który jest zaimplementowany w bieżącej lub aktywnej hierarchii. Hierarchia powinna obsługiwać polecenia, które są prawidłowe za każdym razem, gdy hierarchia jest aktywna, nawet jeśli okno dokumentu elementu projektu ma fokus. Jednak polecenia, które są stosowane tylko wtedy, gdy **Eksplorator rozwiązań** ma fokus, muszą być obsługiwane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu i jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metod.

     Polecenia **wycinanie**, **Kopiowanie**, **wklejanie**, **usuwanie**, **zmiana nazwy**, **wprowadzanie** i **kliknięcie** wymagają specjalnej obsługi. Informacje o sposobie obsługi poleceń **usuwania** i **usuwania** w hierarchiach znajdują się w <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfejsie.

8. Globalne: Jeśli polecenie nie zostało obsłużone przez poprzednio wymienione konteksty, program Visual Studio próbuje skierować go do pakietu VSPackage, który jest właścicielem polecenia, które implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs. Jeśli pakietu VSPackage nie został jeszcze załadowany, nie jest ładowany, gdy program Visual Studio wywołuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę. Pakietu VSPackage jest ładowany tylko wtedy, gdy <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Metoda jest wywoływana.

## <a name="see-also"></a>Zobacz też
- [Projekt polecenia](../../extensibility/internals/command-design.md)

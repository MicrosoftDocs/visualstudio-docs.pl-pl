---
title: Algorytm routingu poleceń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709535"
---
# <a name="command-routing-algorithm"></a>Algorytm routingu poleceń
W programie Visual Studio polecenia są obsługiwane przez wiele różnych składników. Polecenia są kierowane z kontekstu najbardziej wewnętrznego, który jest oparty na bieżącym zaznaczeniu, do najbardziej zewnętrznego (znanego również jako globalny) kontekstu. Aby uzyskać więcej informacji, zobacz [Dostępność polecenia](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Kolejność rozpoznawania poleceń
 Polecenia są przekazywane przez następujące poziomy kontekstu polecenia:

1. Dodatki: Środowisko najpierw oferuje polecenie do wszystkich dodatków, które są obecne.

2. Polecenia priorytetowe: Te polecenia są <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>rejestrowane za pomocą programu . Są one wywoływane dla każdego polecenia w programie Visual Studio i są wywoływane w kolejności, w jakiej zostały zarejestrowane.

3. Polecenia menu kontekstowego: Polecenie znajdujące się w menu kontekstowym jest najpierw oferowane do celu polecenia, które jest dostarczane do menu kontekstowego, a następnie do typowego routingu.

4. Cele docelowe polecenia zestawu na pasku <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>narzędzi: te obiekty docelowe poleceń są rejestrowane podczas wywoływania . Parametrem `pCmdTarget` może `null`być . Jeśli tak `null`nie jest , to ten cel polecenia jest używany do aktualizowania wszystkich poleceń znajdujących się na pasku narzędzi, który konfigurujesz. Jeśli powłoka konfiguruje pasek narzędzi, przekazuje ramkę `pCmdTarget` okna jako ramkę okna, aby wszystkie aktualizacje poleceń na pasku narzędzi przepływały przez ramkę okna, nawet jeśli nie jest ona skupina.

5. Okno narzędzia: Okna narzędzia, które <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> zazwyczaj implementują <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, należy również zaimplementować interfejs, tak aby visual studio można uzyskać miejsce docelowe polecenia, gdy okno narzędzia jest aktywne okno. Jeśli jednak oknem narzędzia, które ma fokus, jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> okno **Projektu,** polecenie jest kierowane do interfejsu, który jest wspólnym elementem nadrzędnym wybranych elementów. Jeśli to zaznaczenie obejmuje wiele projektów, polecenie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> jest kierowane do hierarchii. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> zawiera <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> i, które są analogiczne do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> odpowiednich poleceń w interfejsie.

6. Okno dokumentu: Jeśli polecenie `RouteToDocs` ma ustawioną flagę w pliku *vsct,* program Visual Studio wyszukuje obiekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> docelowy polecenia w obiekcie widoku <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> dokumentu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> który jest wystąpieniem interfejsu lub wystąpieniem obiektu dokumentu (zazwyczaj interfejsu lub interfejsu). Jeśli obiekt widoku dokumentu nie obsługuje polecenia, program Visual <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Studio kieruje polecenie do interfejsu, który jest zwracany. (Jest to opcjonalny interfejs dla obiektów danych dokumentu).

7. Bieżąca hierarchia: Bieżąca hierarchia może być projektem, który jest właścicielem aktywnego okna dokumentu lub hierarchią wybraną w **Eksploratorze rozwiązań**. Visual Studio wyszukuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs, który jest zaimplementowany w bieżącej lub aktywnej hierarchii. Hierarchia powinna obsługiwać polecenia, które są prawidłowe, gdy hierarchia jest aktywna, nawet jeśli okno dokumentu elementu projektu ma fokus. Jednak polecenia, które mają zastosowanie tylko wtedy, gdy **Eksplorator rozwiązań** ma fokus musi być obsługiwany przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfejsu i jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metod.

     **Polecenia Wytnij**, **Kopiuj,** **Wklej,** **Usuń,** **Zmień nazwę,** **Enter**i **DoubleClick** wymagają specjalnej obsługi. Aby uzyskać informacje dotyczące obsługi polecenia **Delete** i **Remove** w hierarchiach, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfejs.

8. Global: Jeśli polecenie nie zostało obsłużone przez wcześniej wymienionych kontekstów, Visual Studio próbuje przekierować go do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> VSPackage, który jest właścicielem polecenia, które implementuje interfejs. Jeśli vspackage nie został załadowany już, nie jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ładowany, gdy visual studio wywołuje metodę. VSPackage jest ładowany <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> tylko wtedy, gdy metoda jest wywoływana.

## <a name="see-also"></a>Zobacz też
- [Projekt polecenia](../../extensibility/internals/command-design.md)

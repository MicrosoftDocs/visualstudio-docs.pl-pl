---
title: Aktywacja w miejscu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
manager: douge
ms.openlocfilehash: 5ad55066eb3109d1a553d2496b522d0f18e4ba29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832492"
---
# <a name="in-place-activation"></a>Aktywacja w miejscu
Jeśli widok Edytor obsługuje ActiveX lub inne aktywne kontrolki, należy zaimplementować widoku edytora jako formant ActiveX, lub jako obiekt danych aktywnego dokumentu przy użyciu modelu aktywacji w miejscu.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Obsługa menu, paski narzędzi i poleceń  
 Program Visual Studio umożliwia widoku edytora do użycia, menu i paski narzędzi w IDE. Te rozszerzenia są określane jako *OLE w miejscu składniki*. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> i <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 W przypadku zaimplementowania formant ActiveX może obsługiwać inne obiekty osadzone. W przypadku zaimplementowania obiektu danych dokumentu ramki okna ogranicza możliwość korzystania z formantów ActiveX.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> interfejsy umożliwiają do oddzielania danych oraz widoku. Jednak program Visual Studio nie obsługuje tej funkcji, a te interfejsy są używane tylko do reprezentowania obiekt widoku dokumentu.  
  
 Edytory, które używają <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi może zapewnić menu, pasek narzędzi i integracja polecenia przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfejs implementowany przez <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi. Edytory również oferują inne funkcje programu Visual Studio, takie jak wybór śledzenia i Cofnij zarządzania. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Obiekty i interfejsy używane  
 Obiekty, które są używane do tworzenia aktywacji w miejscu są wyświetlane na poniższej ilustracji.  
  
 ![In&#45;place Activation Editor](../extensibility/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Edytor aktywacji w miejscu  
  
> [!NOTE]
>  Obiekty w tym rysowania, tylko `CYourEditorFactory` obiektu jest wymagana do utworzenia edytora standardowego. Jeśli tworzysz niestandardowy edytor, nie należy implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ponieważ edytor prawdopodobnie będzie mieć własny mechanizm prywatnej trwałości. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md).  
  
 Wszystkie interfejsy, które są wdrożone w celu tworzenia edytora Aktywacja w miejscu są wyświetlane w pojedynczej precyzji `CYourEditorDocument` obiekt, ale ta konfiguracja obsługuje tylko pojedynczy widok danych dokumentu. Aby uzyskać więcej informacji na temat obsługi wielu widoków danych dokumentu, zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).  
  
|Interface|Typ obiektu|Zastosowanie|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Widok|Włącza w miejscu pakietu VSPackage obiektów do działania jako składników w pełni zintegrowanego środowiska IDE, za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi. Ta usługa integruje się z menu, paski narzędzi i poleceń obiektu IDE i wysyła powiadomienia o zmianie stanu.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Widok|Główna oznacza, że za pomocą którego obiekt osadzony zapewnia podstawowe funkcje z jego kontenerem i komunikuje się z nim.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Widok|Zarządza Aktywacja i dezaktywacja obiekty w miejscu i określa, ile obiektu w miejscu powinny być widoczne.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Widok|Zapewnia bezpośredni kanał komunikacji między obiektu w miejscu, skojarzonej aplikacji peryferyjnych ramki okna i okna dokumentu w aplikacji, która zawiera osadzony obiekt.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Widok|Implementuje obiektu ActiveX. Należy pamiętać, że metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> że danych oddzielny dokument i widok nie są używane w środowisku IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Wyświetlanie i danych|Włącza obiekt danych dokumentów, obiekt widoku dokumentów lub obu tych do wzięcia udziału w obsłudze polecenia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Widok|Włącza aktualizacje paska stanu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Widok|Umożliwia dodawanie elementów do przybornika.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dane|Wysyła powiadomienia o zmianach edytowanego pliku. (Ten interfejs jest opcjonalny).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dane|Umożliwia włączenie funkcji Zapisz jako dla typu pliku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Dane|Umożliwia utrwalanie w dokumencie. Pliki tylko do odczytu, można wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> zapewnienie "Zablokuj" ikony, który wskazuje pliki tylko do odczytu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dane|Określa, czy mają być ignorowane zmiany danych dokumentu.|
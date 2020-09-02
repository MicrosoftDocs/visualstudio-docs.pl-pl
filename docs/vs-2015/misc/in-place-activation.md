---
title: Aktywacja w miejscu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 192274d087731f68cb7e01c1da20e80cbfef0360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802927"
---
# <a name="in-place-activation"></a>Aktywacja w miejscu
Jeśli widok edytora obsługuje kontrolki ActiveX lub inne aktywne formanty, należy zaimplementować widok edytora jako kontrolkę ActiveX lub obiekt danych aktywnego dokumentu przy użyciu modelu aktywacji w miejscu.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Obsługa menu, pasków narzędzi i poleceń  
 Program Visual Studio umożliwia widokowi edytora Używanie menu i pasków narzędzi IDE. Rozszerzenia te są określane jako *składniki w miejscu OLE*. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> i <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> .  
  
 W przypadku zaimplementowania kontrolki ActiveX można hostować inne osadzone obiekty. W przypadku zaimplementowania obiektu danych dokumentu, ramka okna ogranicza możliwość korzystania z formantów ActiveX.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>Interfejsy i <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> umożliwiają rozdzielenie danych i widoku. Jednak program Visual Studio nie obsługuje tej funkcji, a interfejsy te są używane tylko do reprezentowania obiektu widoku dokumentu.  
  
 Edytory korzystające z <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi mogą udostępniać menu, paski narzędzi i integrację poleceń, wywołując metody <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfejsu zaimplementowanego przez <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługę. Edytory mogą również oferować inne funkcje programu Visual Studio, takie jak śledzenie wyboru i zarządzanie cofaniem. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Używane obiekty i interfejsy  
 Obiekty, które są używane do tworzenia aktywacji w miejscu, przedstawiono na poniższej ilustracji.  
  
 ![W&#45;umieścić edytora aktywacji](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Edytor aktywacji w miejscu  
  
> [!NOTE]
> Obiektów na tym rysunku tylko `CYourEditorFactory` obiekt jest wymagany do utworzenia edytora standardowego. W przypadku tworzenia niestandardowego edytora nie trzeba implementować, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ponieważ Edytor prawdopodobnie będzie miał własny prywatny mechanizm trwałości. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md).  
  
 Wszystkie interfejsy, które są zaimplementowane do utworzenia edytora aktywacji w miejscu, są wyświetlane na pojedynczym `CYourEditorDocument` obiekcie, ale ta konfiguracja obsługuje tylko jeden widok danych dokumentu. Aby uzyskać więcej informacji na temat obsługi wielu widoków danych dokumentu, zobacz [Obsługa widoków wielu dokumentów](../extensibility/supporting-multiple-document-views.md).  
  
|Interfejs|Typ obiektu|Zastosowanie|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Widok|Umożliwia pakietu VSPackage obiektów do działania jako w pełni zintegrowanych składników IDE przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi. Ta usługa integruje menu, paski narzędzi i polecenia obiektu w IDE i wystawia powiadomienia o zmianach stanu.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Widok|Podmiot zabezpieczeń, za pomocą którego osadzony obiekt zapewnia podstawowe funkcje dla jego kontenera i komunikuje się z nim.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Widok|Zarządza aktywacją i dezaktywacją obiektów w miejscu oraz określa, jaka część obiektu w miejscu powinna być widoczna.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Widok|Zapewnia bezpośredni kanał komunikacji między obiektem umieszczonym w miejscu, niezależną ramką aplikacji i oknem dokumentu w aplikacji, która zawiera osadzony obiekt.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Widok|Implementuje obiekt ActiveX. Należy zauważyć, że metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> i `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` oddzielne dane i widok dokumentu nie są używane w środowisku IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Wyświetl/dane|Włącza obiekt danych dokumentu lub obiekt widoku dokumentu albo oba te elementy, aby uczestniczyły w obsłudze poleceń.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Widok|Włącza aktualizacje paska stanu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Widok|Włącza Dodawanie elementów do przybornika.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dane|Wysyła powiadomienie o zmianach edytowanego pliku. (Ten interfejs jest opcjonalny).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dane|Służy do włączania funkcji Zapisz jako dla typu pliku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Dane|Włącza trwałość dla dokumentu. W przypadku plików tylko do odczytu Połącz <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> się, aby podać ikonę "blokada" wskazującą pliki tylko do odczytu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dane|Określa, czy zmiany w danych dokumentu mają być ignorowane.|
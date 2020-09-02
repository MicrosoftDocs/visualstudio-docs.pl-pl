---
title: VisibilityItem — element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6f71e145282d1d6e340060b9798ca54c9af9f4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62584841"
---
# <a name="visibilityitem-element"></a>VisibilityItem, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`VisibilityItem`Element określa statyczną widoczność poleceń i pasków narzędzi. Każdy wpis identyfikuje polecenie lub menu, a także kontekst interfejsu użytkownika skojarzonego z poleceniem. Program Visual Studio wykrywa polecenia, menu i paski narzędzi oraz ich widoczność bez ładowania pakietów VSPackage, które je definiują. IDE używa metody, <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Aby określić, czy kontekst interfejsu użytkownika polecenia jest aktywny.  
  
 Po załadowaniu pakietu VSPackage program Visual Studio oczekuje, że widoczność poleceń ma być określona przez pakietu VSPackage, a nie `VisibilityItem` . Aby określić widoczność polecenia, można zaimplementować <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> procedurę obsługi zdarzeń lub <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę w zależności od sposobu implementacji polecenia.  
  
 Polecenie lub menu, które ma `VisibilityItem` element pojawia się tylko wtedy, gdy skojarzony kontekst jest aktywny. Można skojarzyć pojedyncze polecenie, menu lub pasek narzędzi z co najmniej jednym kontekstem interfejsu użytkownika poleceń, dołączając wpis dla każdej kombinacji kontekstu polecenia. Jeśli polecenie lub menu jest skojarzone z wieloma kontekstami interfejsu użytkownika poleceń, polecenie lub menu jest widoczne, gdy jeden ze skojarzonych kontekstów interfejsu użytkownika poleceń jest aktywny.  
  
 `VisibilityItem`Element ma zastosowanie tylko do poleceń, menu i pasków narzędzi, a nie do grup. Element, który nie ma powiązanego `VisibilityItem` elementu jest widoczny za każdym razem, gdy jego menu nadrzędne jest aktywne.  
  
## <a name="syntax"></a>Składnia  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|guid|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|  
|identyfikator|Wymagany. Identyfikator identyfikatora polecenia GUID/ID.|  
|kontekst|Wymagany. Kontekst interfejsu użytkownika, w którym polecenie jest widoczne.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`Element określa statyczną widoczność grup poleceń i pasków narzędzi.|  
  
## <a name="remarks"></a>Uwagi  
 Standardowe konteksty interfejsu użytkownika programu Visual Studio są zdefiniowane w pliku \VisualStudioIntegration\Common\Inc\vsshlids.h *ścieżki instalacji zestawu SDK programu Visual Studio*, a także w <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> klasach i. Bardziej kompletny zestaw kontekstów interfejsu użytkownika jest zdefiniowany w <xref:Microsoft.VisualStudio.VSConstants> klasie.  
  
## <a name="example"></a>Przykład  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

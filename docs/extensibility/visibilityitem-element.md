---
title: Element visibilityitem | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698149"
---
# <a name="visibilityitem-element"></a>Element VisibilityItem
Element `VisibilityItem` określa statyczną widoczność poleceń i pasków narzędzi. Każdy wpis identyfikuje polecenie lub menu, a także skojarzony kontekst interfejsu użytkownika polecenia. Visual Studio wykrywa polecenia, menu i paski narzędzi i ich widoczność, bez ładowania VSPackages, które je definiują. IDE używa metody, aby ustalić, <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> czy kontekst interfejsu użytkownika polecenia jest aktywny.

 Po załadowaniu vspackage visual studio oczekuje, że widoczność polecenia zostanie `VisibilityItem`określona przez VSPackage, a nie . Aby określić widoczność polecenia, można zaimplementować program obsługi <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> zdarzeń lub <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę, w zależności od sposobu zaimplementowania polecenia.

 Polecenie lub menu, `VisibilityItem` które ma element pojawia się tylko wtedy, gdy skojarzony kontekst jest aktywny. Jedno polecenie, menu lub pasek narzędzi można skojarzyć z co najmniej jednym kontekstem interfejsu użytkownika polecenia, dołączając wpis dla każdej kombinacji kontekstu polecenia. Jeśli polecenie lub menu jest skojarzone z kontekstami interfejsu użytkownika wielu poleceń, polecenie lub menu jest widoczne, gdy aktywny jest dowolny z skojarzonych kontekstów interfejsu użytkownika polecenia.

 Element `VisibilityItem` ma zastosowanie tylko do poleceń, menu i pasków narzędzi, a nie do grup. Element, który nie ma `VisibilityItem` powiązanego elementu jest widoczny, gdy jego menu nadrzędne jest aktywne.

## <a name="syntax"></a>Składnia

```xml
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
|Identyfikator GUID|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|
|id|Wymagany. Identyfikator identyfikatora polecenia GUID/ID.|
|kontekst|Wymagany. Kontekst interfejsu użytkownika, w którym polecenie jest widoczne.|
|Warunek|Element opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Element `VisibilityConstraints` określa statyczną widoczność grup poleceń i pasków narzędzi.|

## <a name="remarks"></a>Uwagi
 Standardowe konteksty interfejsu użytkownika programu Visual Studio są definiowane w *ścieżce instalacji zestawów SDK programu Visual Studio*\VisualStudioIntegration\Common\Inc\vsshlids.h, a także w <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> i <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> klasach. Bardziej kompletny zestaw kontekstów interfejsu użytkownika <xref:Microsoft.VisualStudio.VSConstants> jest zdefiniowany w klasie.

## <a name="example"></a>Przykład

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Element VisibilityConstraints](../extensibility/visibilityconstraints-element.md)
- [Tabela poleceń programu Visual Studio (. Vsct) Pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: VisibilityItem, element | Microsoft Docs
description: Element VisibilityItem określa statyczną widoczność poleceń i pasków narzędzi. Wpisy identyfikują polecenie lub menu oraz skojarzony kontekst interfejsu użytkownika polecenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 025e05dd0346c7da0a70985aa579d1673f2ffcaa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905439"
---
# <a name="visibilityitem-element"></a>VisibilityItem, element
Element `VisibilityItem` określa statyczną widoczność poleceń i pasków narzędzi. Każdy wpis identyfikuje polecenie lub menu, a także skojarzony kontekst interfejsu użytkownika polecenia. Visual Studio wykrywa polecenia, menu i paski narzędzi oraz ich widoczność bez ładowania pakietów VSPackage, które je definiują. Ide używa metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> , aby określić, czy kontekst interfejsu użytkownika polecenia jest aktywny.

 Po załadowaniu pakietów VSPackage program Visual Studio, że widoczność polecenia będzie określana przez pakiet VSPackage, a nie `VisibilityItem` przez . Aby określić widoczność polecenia, można zaimplementować program obsługi zdarzeń lub metodę , w zależności od sposobu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> implementacji polecenia.

 Polecenie lub menu, które ma `VisibilityItem` element pojawia się tylko wtedy, gdy skojarzony kontekst jest aktywny. Można skojarzyć jedno polecenie, menu lub pasek narzędzi z co najmniej jednym kontekstem interfejsu użytkownika polecenia, uwzględniając wpis dla każdej kombinacji kontekstu polecenia. Jeśli polecenie lub menu jest skojarzone z wieloma kontekstami interfejsu użytkownika polecenia, polecenie lub menu jest widoczne, gdy dowolny z powiązanych kontekstów interfejsu użytkownika polecenia jest aktywny.

 Element dotyczy tylko poleceń, menu i pasków narzędzi, a `VisibilityItem` nie grup. Element, który nie ma powiązanego `VisibilityItem` elementu, jest widoczny za każdym razem, gdy jego menu nadrzędne jest aktywne.

## <a name="syntax"></a>Składnia

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagane. Identyfikator GUID/ID identyfikatora polecenia.|
|identyfikator|Wymagane. Identyfikator identyfikatora GUID/ID polecenia.|
|kontekst|Wymagane. Kontekst interfejsu użytkownika, w którym polecenie jest widoczne.|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)|Element `VisibilityConstraints` określa statyczną widoczność grup poleceń i pasków narzędzi.|

## <a name="remarks"></a>Uwagi
 Standardowe konteksty Visual Studio użytkownika są zdefiniowane w ścieżce instalacji zestawu *Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h, a także w klasach <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> i <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> . Bardziej kompletny zestaw kontekstów interfejsu użytkownika jest zdefiniowany w <xref:Microsoft.VisualStudio.VSConstants> klasie .

## <a name="example"></a>Przykład

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md)
- [Visual Studio tabeli poleceń (. Vsct) Pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

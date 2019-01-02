---
title: Extern, Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dc48dc471dab06bf18c0edf622cfa18e7159eaab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895262"
---
# <a name="extern-element"></a>Extern, element
Extern, element odwołuje się do dowolnego nagłówka zewnętrznego (*.h*) pliki do scalania z *vsct* plik w czasie kompilacji. Pliki do scalenia muszą znajdować się w ścieżce Include podane do kompilatora VSCT lub jest przywoływany przez [Include element](../extensibility/include-element.md). Pliki mogą być inne *vsct* pliki lub pliki nagłówkowe C++.  
  
 Definicje w plikach nagłówkowych musi mieć postać "#define [Symbol] [wartość]" wartość może być inny symbol, jeśli został wcześniej zdefiniowany. Definicje mogą być używane w instrukcjach warunkowych elementów polecenia. Dowolny symbol nie rzeczywistej zostaną odrzucone.  
  
 CommandTable, element  
Extern, element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|href|Wymagana. Ścieżka do pliku nagłówka:<br /><br /> href="stdidcmd.h"|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|język|Opcjonalna. Domyślny język wszystkich [ \<ciągi >](../extensibility/strings-element.md) elementów w tabeli poleceń:<br /><br /> Language = "en-us"|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak.|Brak.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń — czyli elementy menu, menu, paski narzędzi i pola kombi — zapewniającej pakietu VSPackage IDE.|  
  
## <a name="example"></a>Przykład  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)